## Low & NC Report For Panoptics

### [L-1] No token extract method presents in `CollateralTracker` contract

`CollateralTracker` is a token vault contract.
It possible that some token could remain in that contract at the, due to some precision loss or rounding down/up opration as Dusts

So developer should implemnt some token extract method so that those Dust amount could pulled out of collateralTracker contracts.


Or in most hazardious situation let say in some attack case, it could stop attacker from daring fund.

Protocol should implement some sort of `pause / upgradable` methods. I mention those in Non-critical section.

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol



### [L-2] Possible precision loss in `maxMint` function

In Solidity division can result in rounding down errors, hence to minimize any rounding errors we always want to perform multiplication before division.

```solidity
    function maxMint(address) external view returns (uint256 maxShares) { 
        unchecked {
            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
        }
    }

    function convertToShares(uint256 assets) public view returns (uint256 shares) {
        return Math.mulDiv(assets, totalSupply, totalAssets()); 
    }
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444-L448

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L379-L381




### [L-3] Multiple Wrong cases provided in contest Docs

#### Wrong Equation used in `Net, Gross, and Owed fees (with spread)` section

`gross_feesCollectedX128 = feesGrowthX128 * N + feesGrowthX128*ν*S*(1 + S/N)` --Eq-1

According to Docs we get following equation(Eq-2) by solving above(Eq-1)

`gross_feesCollectedX128 = feesGrowthX128 * T * (1 + ν*S^2/(N*T))` -- Eq-2

which is not true

To get Eq-2 from above we have to assume that ` T = N + VS `
which is not right

Actually `T = N + S`

That shows that above equation(Eq-1) was wrong

https://panoptic.xyz/docs/panoptic-protocol/streamia#net-gross-and-owed-fees-with-spread



### [L-4] `maxDeposit` is incompatible with some ERC20 tokens

maxDeposit() returns that maximum amount asset that can be deposited to `collateralTracker` contract. it returns `type(uint104).max`

But problem is that some tokens like `COMP` `UNI` ony support maxTransfer or maxAllowance till `type(uint96).max`.
https://www.youtube.com/watch?v=Tx0f8A2Yd3k&t=2090s

So for those type of Assets here `maxDeposit()` retuning wrong values.

```solidity
    /// @notice returns The maximum deposit amount.
    /// @return maxAssets The maximum amount of assets that can be deposited.
    function maxDeposit(address) external pure returns (uint256 maxAssets) {
        return type(uint104).max;
    }
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L392-L394



### [L-5] `maxMint` calculation is wrong

In ERC4626 standard's word maxMint() `MUST return the maximum amount of shares mint would allow to be deposited to receiver and not cause a revert, `

```solidity
    function maxMint(address) external view returns (uint256 maxShares) { 
        unchecked {
            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
        }
    }



    function convertToShares(uint256 assets) public view returns (uint256 shares) {
        return Math.mulDiv(assets, totalSupply, totalAssets());
```

But in above implementation we see so many rounding downs

- 1st rounding down in `convertToShares`
- 2nd in `maxShares` calculation

As a result `maxMint()` not returning maximum possible shares

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444-L448

### [L-6] Before setting Crucial address state variable make sure to check address(0)

```solidity
    constructor(
        address _WETH9,
        SemiFungiblePositionManager _SFPM,
        IUniswapV3Factory _univ3Factory,
        IDonorNFT _donorNFT,
        address _poolReference,
        address _collateralReference
    ) {
        WETH = _WETH9; // @audit L :: address check in constructor
        SFPM = _SFPM;
        DONOR_NFT = _donorNFT;
        // We store the Uniswap Factory contract - later we can use this to verify uniswap pools
        UNIV3_FACTORY = _univ3Factory;
        POOL_REFERENCE = _poolReference;
        COLLATERAL_REFERENCE = _collateralReference;
    }
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L115-L130





### [L-7] `deposit()` doesn't fully followed `ERC4626` standard
according to EIP-4626 standard following s the required condition for deposit()

MUST support EIP-20 approve / transferFrom on asset as a deposit flow. MAY support an additional flow in which the underlying tokens are owned by the Vault contract before the deposit execution, and are accounted for during deposit.

This EIP-20 approve support feature already implemented in case of CallateralTracker.sol's withdraw() & redeem(). So its recommened to follow same feature in case of deposit as well.
```solidity
    function deposit(uint256 assets, address receiver) external returns (uint256 shares) { // @audit-issue incompatible with erc4626 as EIP-20 approve
        if (assets > type(uint104).max) revert Errors.DepositTooLarge();

        shares = previewDeposit(assets); 

        
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        );
        
        _mint(receiver, shares);

        // update tracked asset balance
        unchecked {
            s_poolAssets += uint128(assets); 
        }

        emit Deposit(msg.sender, receiver, assets, shares);
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L417-L440





### [N-01] Low Level Calls to Custom Addresses

Contracts should avoid making low-level calls to custom addresses, especially if these calls are based on address parameters in the function. 
Such behavior can lead to unexpected execution of untrusted code. Instead, consider using Solidity's high-level function calls or contract interactions.

```solidity
        return ERC20Minimal.transfer(recipient, amount);


       return ERC20Minimal.transferFrom(from, to, amount);
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L333
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L352



### [N-02] Missing Event Emission After Critical Initialize() Function

Emitting an initialization event offers clear, on-chain evidence of the contract's initialization state, enhancing transparency and auditability. This practice aids users and developers in accurately tracking the contract's lifecycle, pinpointing the precise moment of its initialization. Moreover, it aligns with best practices for event logging in smart contracts, ensuring that significant state changes are both observable and verifiable through emitted events.
```solidity
        totalSupply = 10 ** 6;

        s_poolAssets = 1;


        s_underlyingToken = underlyingIsToken0 ? token0 : token1;


        s_panopticPool = panopticPool;


        COMMISSION_FEE = _commissionFee;
        SELLER_COLLATERAL_RATIO = _sellerCollateralRatio;
        BUYER_COLLATERAL_RATIO = _buyerCollateralRatio;
        FORCE_EXERCISE_COST = _forceExerciseCost;
        TARGET_POOL_UTIL = _targetPoolUtilization;
        SATURATED_POOL_UTIL = _saturatedPoolUtilization;
        ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L187-L193
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L238
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L234
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L244


### [N-03] Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct, for readability

Combining multiple address/ID mappings into a single mapping to a struct can enhance code clarity and maintainability. Consider refactoring multiple mappings into a single mapping with a struct for cleaner code structure. This arrangement also promotes a more organized contract structure, making it easier for developers to navigate and understand.

*Instances(2)*
```solidity
mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))
        internal s_options;


mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
        internal s_positionBalance;
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L238

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L258



### [N-04] Expressions for constant values should use immutable rather than constant
While it does not save gas for some simple binary expressions because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between constant variables and immutable variables, and they should each be used in their appropriate contexts. constants should be used for literal values written into the code, and immutable variables should be used for expressions, or values calculated in, or passed into the constructor.

*Instances(3)*
```solidity
    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;
    
    int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

    uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L103
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L105
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L165



### [N-5] Consider making contracts Upgradeable

Contract uses a non-upgradeable design. Transitioning to an upgradeable contract structure is more aligned with contemporary smart contract practices. This approach not only enhances flexibility but also allows for continuous improvement and adaptation, ensuring the contract stays relevant and robust in an ever-evolving ecosystem.

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol


### [N-6] Consider Adding Emergency-Stop Functionality

Smart contracts that hold significant value, interact with external contracts, or have complex logic should include an emergency-stop mechanism for added security. This allows pausing certain contract functionalities in case of emergencies, mitigating potential damages.

This contract seems to lack such a mechanism. Implementing an emergency stop can enhance contract security and reliability.
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol



### [N-7] Consider adding a block/deny-list

While adding a block or deny-list may increase the level of centralization in the contract, it provides an additional layer of security by preventing hackers from using stolen tokens or carrying out other malicious activities.

Although it's a trade-off, a block or deny-list can help improve the overall security posture of the contract.

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol




### [N-8] Consider bounding input array length

The functions in question operate on arrays without established boundaries, executing function calls for each of their entries. If these arrays become excessively long, a function might revert due to gas constraints. To enhance user experience, consider incorporating a require() statement that enforces a sensible maximum array length. This approach can avoid unnecessary computational work and ensure smoother transactions.

*Instances()*
```solidity
        uint256 pLength = positionIdList.length;
        balances = new uint256[2][](pLength);

        for (uint256 k = 0; k < pLength; ) {



        for (uint256 i = 0; i < positionIdList.length; ) {



        for (uint256 i = 0; i < pLength; ) {
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L441
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L802
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1382

### [N-9] Complex casting

Complex casting in Solidity contracts can introduce both readability issues and potential for overflows. Whenever multiple casts are found, consider whether the complexity is necessary. If so, it is strongly recommended to add inline comments to explain why these casts are needed and to assure that no overflows are introduced.

*Instances(Multiple instances in following contracts)*

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol

### [N-10] Constants in comparisons should appear on the left side

Placing constants on the left side of comparison statements can help prevent accidental assignments and improve code readability. In languages like C, placing constants on the left can protect against unintended assignments that would be treated as true conditions, leading to bugs. Although Solidity does not have this specific issue, using the same practice can still be beneficial for code readability and consistency.

Consider placing constants on the left side of comparison operators like ==, !=, <, >, <=, and >=."

*Instances()*
```solidity
if (currentSqrtPriceX96 <= sqrtLowerBound || currentSqrtPriceX96 >= sqrtUpperBound) {

if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)


if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L341
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L943
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1035




### [N-12] Consider using delete rather than assigning false to clear values

The use of the delete keyword is recommended over simply assigning values to false when you intend to reset the state of a variable. The delete keyword more closely aligns with the semantic intent of clearing or resetting a variable. This practice also makes the code more readable and highlights the change in state, which may encourage a more thorough audit of the surrounding logic.

*Instances()*
```solidity
        for (uint256 leg = 0; leg < numLegs; ) {
...
...
            s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
...
        }
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L870



### [N-13] No need toassign default values to state variables

*Instances(4)*
```solidity
    bool internal constant COMPUTE_LONG_PREMIA = false;

    bool internal constant ONLY_AVAILABLE_PREMIUM = false;

    bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

    bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L111
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L114
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L120
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L133

### [N-14] Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is ideal for named returns.

*Instances()*
```solidity
    function _getSlippageLimits(
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) internal pure returns (int24, int24) {




    function _mintInSFPMAndUpdateCollateral(
        TokenId tokenId,
        uint128 positionSize,
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) internal returns (uint128) {



    function _payCommissionAndWriteData(
        TokenId tokenId,
        uint128 positionSize,
        LeftRightSigned totalSwapped
    ) internal returns (uint128) {
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L502
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L682
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L710



### [N-16] Leverage Recent Solidity Features with 0.8.23

The recent updates in Solidity provide several features and optimizations that, when leveraged appropriately, can significantly improve your contract's code clarity and maintainability. Key enhancements include the use of push0 for placing 0 on the stack for EVM versions starting from "Shanghai", making your code simpler and more straightforward. Moreover, Solidity has extended NatSpec documentation support to enum and struct definitions, facilitating more comprehensive and insightful code documentation.

Additionally, the re-implementation of the UnusedAssignEliminator and UnusedStoreEliminator in the Solidity optimizer provides the ability to remove unused assignments in deeply nested loops. This results in a cleaner, more efficient contract code, reducing clutter and potential points of confusion during code review or debugging. It's recommended to make full use of these features and optimizations to enhance the robustness and readability of your smart contracts.

* Should implemented in all contract files *

### [N-17] Use of magic numbers in code's mathematical calculations

```solidity
            TICK_DEVIATION = uint256(
                2230 +
                    (12500 * ratioTick) /
                    10_000 +
                    (7812 * ratioTick ** 2) /
                    10_000 ** 2 +
                    (6510 * ratioTick ** 3) /
                    10_000 ** 3
            );
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L200-L209

### [N-18] `constant` should be value rather than expression

*Instances(3)*
```solidity
    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;
    
    int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

    uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L103
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L105
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L165




### [N-19] Code base using hard-coded address

```solidity
             s_miniMedian =
                (uint256(block.timestamp) << 216) 
+ (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
                            
```
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L312






























