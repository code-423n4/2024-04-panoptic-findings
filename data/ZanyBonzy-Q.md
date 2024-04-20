# 1. Lack of access control in major functions can be misused

startPool(

Lines of code* 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L210
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L221
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L291

## Impact
While the `deployNewPool` function allows for users and owners alike to be able to deploy a panoptic pool based on a univ3 pool.

```solidity
function deployNewPool(
        address token0,
        address token1,
        uint24 fee,
        bytes32 salt
    ) external returns (PanopticPool newPoolContract) {
        // initialize pool in SFPM if it has not already been initialized
        SFPM.initializeAMMPool(token0, token1, fee);
...
        // Run state initialization sequence for pool and collateral tokens
        collateralTracker0.startToken(true, token0, token1, fee, newPoolContract);
        collateralTracker1.startToken(false, token0, token1, fee, newPoolContract);
        newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);
...
    }
```
The issue is that, the external functions called in the function, the `initializeAMMPool`, `startToken`, `startPool` lack a form of access control. Users having access to these functions can maliciously use it to DOS pool creations, register malicious pools, causing a host of problems in the protocol and to its users.

SFPM
```solidity
    function initializeAMMPool(address token0, address token1, uint24 fee) external {
```
PanopticPool
```solidity
    function startPool(
        IUniswapV3Pool _univ3pool,
        address token0,
        address token1,
        CollateralTracker collateralTracker0,
        CollateralTracker collateralTracker1
    ) external {
```

CollateralTracker
```solidity
    function startToken(
        bool underlyingIsToken0,
        address token0,
        address token1,
        uint24 fee,
        PanopticPool panopticPool
    ) external {
```

## Recommended Mitigation Steps
Add a form of access control, `onlyPanopticFactory`, `onlyPanopticPool` that will prevent these functions from being misused.


# 3. Pools can be deployed without factory state initialization

Lines of code*

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L210

## Impact

Panoptic factory allows for panoptic pool deployment before its intitialization which can be used by users to unfairly mint DonorNFTs by frontrunning calls to factory initializations to deploy panoptic pool. After `PanopticFactory` deployment, the initialize function allows the deployers set the owner address and initialize the contract state.

```solidity
    function initialize(address _owner) public {
        if (!s_initialized) {
            s_owner = _owner;
            s_initialized = true;
        }
    }
```
But by frontrunning the call to the initialize function, users can call the `deployNewPool` function to deploy a new pool and mint themselves NFTs due to the lack of check for contract initialization in the function. Note the lack of check of initialized state in the `deployNewPool` function, and that pools can be deployed when there's no owner.

```solidity
function deployNewPool(
        address token0,
        address token1,
        uint24 fee,
        bytes32 salt
    ) external returns (PanopticPool newPoolContract) {
        // sort the tokens, if necessary:
        (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);

        // frontrunning protection for mined pool addresses
        if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

        // restrict pool deployment to owner if contract has not been made permissionless
        address _owner = s_owner;
        if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner(); //@note

        IUniswapV3Pool v3Pool = IUniswapV3Pool(UNIV3_FACTORY.getPool(token0, token1, fee));
        if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

        if (address(s_getPanopticPool[v3Pool]) != address(0))
            revert Errors.PoolAlreadyInitialized();

        // initialize pool in SFPM if it has not already been initialized
        SFPM.initializeAMMPool(token0, token1, fee);

        // This creates a new Panoptic Pool (proxy to the PanopticPool implementation)
        // Users can specify a salt, the aim is to incentivize the mining of addresses with leading zeros
        newPoolContract = PanopticPool(POOL_REFERENCE.cloneDeterministic(salt));

        // Deploy collateral token proxies
        CollateralTracker collateralTracker0 = CollateralTracker(
            Clones.clone(COLLATERAL_REFERENCE)
        );
        CollateralTracker collateralTracker1 = CollateralTracker(
            Clones.clone(COLLATERAL_REFERENCE)
        );

        // Run state initialization sequence for pool and collateral tokens
        collateralTracker0.startToken(true, token0, token1, fee, newPoolContract);
        collateralTracker1.startToken(false, token0, token1, fee, newPoolContract);

        newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);

        s_getPanopticPool[v3Pool] = newPoolContract;

        // The Panoptic pool won't be safe to use until the observation cardinality is at least CARDINALITY_INCREASE
        // If this is not the case, we increase the next cardinality during deployment so the cardinality can catch up over time
        // When that happens, there will be a period of time where the PanopticPool is deployed, but not (safely) usable
        v3Pool.increaseObservationCardinalityNext(CARDINALITY_INCREASE);

        // Mints the full-range initial deposit
        // which is why the deployer becomes also a "donor" of full-range liquidity
        // The SFPM will `safeTransferFrom` tokens from the donor during the mint callback
        (uint256 amount0, uint256 amount1) = _mintFullRange(v3Pool, token0, token1, fee);

        // Issue reward NFT to donor
        DONOR_NFT.issueNFT(msg.sender, newPoolContract, token0, token1, fee);

        emit PoolDeployed(
            newPoolContract,
            v3Pool,
            collateralTracker0,
            collateralTracker1,
            amount0,
            amount1
        );
    }
```
## Recommended Mitigation Steps

Include a check in the `deployNewPool` function.
```solidity
require ((s_initialized),  "Factory Not Yet Initialized");
```
***

***


# 4. Shares can be burned by transferring to zero address 

Lines of code* 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L323
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L341
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L61
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L81

## Impact
The `transfer` and `transferFrom` functions in CollateralTracker allows for shares transfer to zero address which is effectively burning. The only caveat here is that `totalSupply` parameter is not updated, causing the shares in circulation to differ from actual supply of shares, resulting in a host of accounting issues and unexpected behaviours, especially if the CollateralTracker (as its an ERC4626 vault) is integrated with other protocols.

## Recommended Mitigation Steps
Introduce zero address checks in the `transfer` and `transferFrom` functions.

***

***

# 5. Lack of deadline check for protocol operations

Lines of code* 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L547
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L504
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L569
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L471

## Impact

The interactions with the univ3 pool are all missing a "deadline" parameter. AMMs provide their users with an option to limit the execution of their pending actions, such as swaps or adding and removing liquidity. The most common solution is to include this deadline parameter. It protects users from bad trades and ensures that user's transactions cannot be "saved for later". The lack of deadline means that the can be withheld indefinitely at the advantage of a malicious miner. Consider updating functions below to include a user-input deadline parameter that should be passed along to univ3call

## Recommended Mitigation Steps
Consider introducing a deadline parameter 
***

***

# 6. Consider checking for active L2 sequencer

Lines of code* 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L547
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L504
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L569
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L471

## Impact
The protocol aims to deploy on various chains including Arbitrum, Optimism etc. In case of sequencer being down, token prices will be outdated which will result it incorrect premia calculations and exercising options that unexpectedly becomes out of the money.

## Recommended Mitigation Steps
Consider introducing a chainlink sequencer integration to check for sequencer uptime.
***

***

# 7. Excess `ETH` sent during Multicall will not be retrievable

Lines of code*

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L12

## Impact

The Multicall contract, through which the multicalls are made, is payable, meaning it can receive ETH.
```solidity
    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
Consequently, any excess ETH sent during a multicall, will be locked in the contract with no way to retrieve it. 

## Recommended Mitigation Steps
Introduce a sweep function to retrieve excess ETH
***

***

# 8. Check for zero denominator in `mulDiv` not very effective

Lines of code* 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L370C1-L371C1

## Impact

The mulDiv function is designed to perform a multiplication and division operation at once. It holds a check to prevent the denominator being 0.This check is not fully effective if both prod1 and denominator are zero. In such a case, the function might exhibit undefined behavior or cause a revert without a clear explanation.

```solidity
   function mulDiv(
        uint256 a,
        uint256 b,
        uint256 denominator
    ) internal pure returns (uint256 result) {
        unchecked {
...

            // Make sure the result is less than 2**256.
            // Also prevents denominator == 0
            require(denominator > prod1);

```
## Recommended Mitigation Steps

Include an explicit check that requires that denominator != 0

***

***

# 9. Check for array lengths in ERC1155Minimal.sol

Lines of code* 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L130

## Impact

`safeBatchTransferFrom` should employ checks, to ensure that ids and amounts arrays have the same length, making it more EIP1155 compliant. According to ERC1155 Multi token standard,

MUST revert if length of _ids is not the same as length of _values. This can help prevent any unexpected behaviour.
```solidity
          if (ids.length != amounts.length) revert NotEnoughTokenBalance();
```
This check can also be included in the balanceOfBatch function too, to ensure the owners and the ids are of the same length.
```solidity
                  address[] calldata owners,
                  uint256[] calldata ids
```
Also, the amount being transferred should also be checked to make sure it's <= balanceOf, e.g, also from EIP1155 standard,

MUST revert if any of the balance(s) of the holder(s) for token(s) in _ids is lower than the respective amount(s) in _values sent to the recipient.
```solidity
          if (amount > balanceOf) revert NotEnoughTokenBalance();
```

## Recommended Mitigation Steps
Add the needed checks

***

# 10. `transferFrom` and `_transferFrom` can be refactored

Lines of code* 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L81
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L103

## Impact

COnsider refactoring the `transferFrom` to call the internal `_transferFrom` function instead.

```solidity
    function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
        uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.

        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;

        _transferFrom(address from, address to, uint256 amount);

        return true;
    }
```

# 11. TWAP prices on L2 can easily be manipulated

Lines of code*
 
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L253

## Impact

The protocol aims to deploy on major L2s including Arbitrum, and Optimism. The problem is that the cost of manipulating TWAP on Optimism L2 networks so low and with the lack of abundance of MEVs, little arbitrage risk from manipulating prices. From [Uniswap docs](https://docs.uniswap.org/concepts/protocol/oracle#oracles-integrations-on-layer-2-rollups), 
> Uniswap pools on Optimism are not suitable for providing oracle prices, as this high-latency block.timestamp update process makes the oracle much less costly to manipulate
But since protocol uses TWAP prices when performing major functions including liquidations and forceful excercising, prices can easily and cheaply be manipulated to gain unfair advantages over other users.

## Recommended Mitigation Steps
Recommend integrating chainlink or a different oracle support system when dealing with L2s.


# 12. CollateralTracker is not fully compliant ERC4626

Links to affected code *

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L365-L374

## Impact

`totalAssets` doesn't include fees

```solidity
    /// @dev - EXCLUDING the amount of collected fees (because they are reserved for short options)
    /// @dev - EXCLUDING any donations that have been made to the pool
    /// @return totalManagedAssets The total amount of assets managed.
    function totalAssets() public view returns (uint256 totalManagedAssets) {
        unchecked {
            return s_poolAssets + s_inAMM;
        }
    }
```
But according to the [standard](https://eips.ethereum.org/EIPS/eip-4626#totalassets)

> MUST be inclusive of any fees that are charged against assets in the Vault.


