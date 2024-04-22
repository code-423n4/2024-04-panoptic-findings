## QA Report


| |Issue|Instances|
|-|-|-|
| [[L-01](#l-01)] | Using `delegatecall` inside a loop may cause issues with `payable` functions| 1|
| [[L-02](#l-02)] | Unprotected initializer | 2|
| [[L-03](#l-03)] | Missing Slippage Parameters| 1|
| [[L-04](#l-04)] | Potential manipulation of the `balanceOf` mapping without adjusting the total supply of the token| 1| 
| [[L-05](#l-05)] |  Incorrect adjustment of Pool's Assets | 1|
| [[L-06](#l-06)] | Handling Edge Cases in Median Calculation and Buffer Update | 1| 
| [[L-07](#l-07)] | Incorrect Collateral Requirement Calculation for Short Positions Out of Range| 1|
| [[L-08](#l-08)] | Unsafe ERC20 Operations should not be used | 6| 
| [[L-09](#l-09)] | Missing checks for `address(0)` when assigning values to address state variables | 25| 
| [[L-10](#l-10)] | `public` functions not used internally could be marked `external` | 17| 
| [[L-11](#l-11)] | Event is missing `indexed` fields | 12| 
| [[L-12](#l-12)] | Empty `require()` / `revert()` statements | 9| 
| [[L-13](#l-13)] | PUSH0 is not supported by all chains | 17| 
| [[L-14](#l-14)] | Large literal values multiples of 10000 can be replaced with scientific notation | 7| 
| [[L-15](#l-15)] | Internal functions called only once can be inlined | 2| 
| [[L-16](#l-16)] | Contract still has TODOs | 1| 
| [[L-17](#l-17)] | Insufficient Comments | 1|



### L-01: Using `delegatecall` inside a loop may cause issues with `payable` functions

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L12-L37

When calling `delegatecall` the same `msg.value` amount will be accredited multiple times. If one of the `delegatecall` consumes part of the msg.value, other calls might fail, if they expect the full msg.value. Consider using a different design, or fully document this decision to avoid potential issues.

```solidity
  function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
        results = new bytes[](data.length);
        for (uint256 i = 0; i < data.length; ) {
            (bool success, bytes memory result) = address(this).delegatecall(data[i]);

            if (!success) {
```


### L-02: Unprotected initializers
Without the modifier, the function may be called multiple times, overwriting prior initializations. Consider protecting the initializer functions with modifiers.


PanopticFactory.sol [Line: 134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134)

	```solidity
	    function initialize(address _owner) public {
	```

- SemiFungiblePositionManager.sol [Line: 350](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350)

	```solidity
	    function initializeAMMPool(address token0, address token1, uint24 fee) external {
	```



### L-03: Missing Slippage Parameters
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol

The contract does include mechanisms for calculating assets and shares, adjusting for the pool's current state, and managing collateral in relation to option positions. For example, the withdraw and redeem functions calculate the amount of assets or shares based on the current total assets and supply of shares. However, without explicit slippage protection parameters that users can set (like minimum assets out for redeem or maximum shares in for withdraw), users might still be exposed to the risk of receiving less than expected if the pool's state changes unfavorably between the transaction's initiation and execution. 

The CollateralTracker.sol contract could benefit from implementing slippage protection features. This could involve allowing users to specify minimum amounts of assets they are willing to accept when withdrawing or redeeming shares, thus providing a safeguard against unfavorable changes in the pool's state during the transaction's pending period.

[Here is a similar situation from a previous audit](https://solodit.xyz/issues/m-04-lack-of-slippage-protection-in-withdrawredeem-functions-of-the-vault-code4rena-pooltogether-pooltogether-git)






### L-04: Potential manipulation of the `balanceOf` mapping without adjusting the total supply of the token

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L903-L905

The issue in the `refund` function and is related to the direct manipulation of the `balanceOf` mapping without adjusting the total supply of the token. By directly adjusting `balanceOf[delegatee]` without corresponding adjustments to the total supply, the contract's internal accounting can become inconsistent.

This can lead to scenarios where the total supply reported by the contract does not match the sum of all individual balances, breaking the invariant that should always hold for ERC20 tokens.

### Recommended Mitigation:

A potential fix could involve tracking delegated shares separately from the actual shares that contribute to the total supply. This way, operations on delegated shares do not affect the total supply directly but still allow for accurate accounting of user balances and delegated amounts.

```solidity
// Example of a potential fix, assuming a new mapping to track delegated (ghost) shares
mapping(address => uint256) private delegatedShares;

// Adjust the delegate function to track delegated shares separately
function delegate(address delegatee, uint256 assets) external onlyPanopticPool {
    uint256 shares = convertToShares(assets);
    delegatedShares[delegatee] += shares; // Track delegated shares separately
    // No change to totalSupply since these are "ghost" shares
}

// Adjust the refund function to correctly handle the removal of delegated shares
function refund(address delegatee, uint256 assets) external onlyPanopticPool {
    uint256 shares = convertToShares(assets);
    require(delegatedShares[delegatee] >= shares, "Insufficient delegated shares");
    delegatedShares[delegatee] -= shares; // Correctly remove the delegated shares
    // No change to totalSupply since these were "ghost" shares
}

// Ensure that any function that reads balances or total supply correctly accounts for the presence of delegated shares where appropriate.
```




### L-05: Incorrect adjustment of Pool's Assets

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L995-L1033

The `takeCommissionAddData` function is designed to handle the commission on option creation/opening. It updates the pool's assets and in-AMM (Automated Market Maker) balances based on the option transaction details. 

But there is a potential issue in the calculation and application of `updatedAssets` and the subsequent update to `s_poolAsset` and `s_inAMM`. The logic does not fully account for scenarios where the `swappedAmount`  might lead to an incorrect adjustment of the pool's assets, especially when `swappedAmount`  is negative (indicating that the pool owes tokens to the option owner) or when the calculation of `tokenToPay`  results in a need to mint new shares or burn existing shares.

### Specific Concerns:
1. The calculation of `updatedAssets` subtracts `swappedAmount` directly from `(s_poolAssets)`, which could lead to an incorrect pool asset value if `swappedAmount` does not accurately reflect changes in pool assets due to option creation/opening.
2. If `swappedAmount`  is negative, indicating the pool should receive tokens, the logic does not explicitly handle this scenario, potentially leading to incorrect pool asset balances.
3. The function mints or burns shares based on `tokenToPay` without validating if the resulting total supply and pool assets would remain consistent and accurate.

### Recommended Steps:
1. **Validate `swappedAmount`**: Ensure that `swappedAmount` accurately reflects the net change in pool assets due to the transaction. This might involve more detailed tracking of asset flows during option creation/opening.
2. **Explicit Handling of Negative Values**: Add explicit checks and logic to handle scenarios where `swappedAmount` or `tokenToPay` is negative, ensuring that asset and share adjustments are made correctly.
3. **Recompute `s_poolAssets` Accurately**: Instead of directly subtracting `swappedAmount` , recompute `s_poolAssets`  based on actual asset flows into and out of the pool, considering both the creation of new options and the settlement of existing ones.


### Code Adjustment Example:
Consider revising the asset and share adjustment logic to more accurately reflect the actual changes in pool assets and shares. This might involve adding checks for the sign of `swappedAmount` and `tokenToPay`, as well as recalculating `s_poolAssets`  based on actual asset flows.

```solidity
// Example adjustment for handling swappedAmount and tokenToPay
if (swappedAmount > 0) {
    // Logic for handling positive swappedAmount
} else if (swappedAmount < 0) {
    // Adjust pool assets correctly for negative swappedAmount
}

// Recalculate s_poolAssets after adjusting for tokenToPay
if (tokenToPay > 0) {
    // Burn shares logic
} else if (tokenToPay < 0) {
    // Mint shares logic
}

// Ensure s_poolAssets and s_inAMM are recalculated to reflect the true state of the pool
```




### L-06: Handling Edge Cases in Median Calculation and Buffer Update

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L168-L233

There are 2 potential scenarios described here:
### 1. Empty Buffer

If the buffer is empty, it means there are no observations to calculate the median from. In the `computeInternalMedian` function, there's no explicit check for an empty buffer before attempting to calculate the median. This could lead to unexpected behavior, as the code assumes there are at least two observations (at ranks 3 and 4) to calculate the median. If the buffer is empty, attempting to access these ranks would likely result in incorrect calculations or even runtime errors as the case may be.
If the buffer is empty and the function is called, it would attempt to calculate the median using non-existent data, potentially leading to incorrect results or errors.

### 2. Latest Observation is the Same as an Existing Observation

The code updates the buffer with the latest observation from the Uniswap V3 pool. If the latest observation is the same as an existing observation in the buffer, it might not correctly update the buffer's order map. This is because the code logic for updating the buffer and the order map assumes that the latest observation is different from the existing ones.

**Example**: Suppose the buffer contains observations `[1, 2, 3, 4, 5, 6, 7]` and the latest observation is `3`. The code logic for updating the buffer and the order map might not correctly handle this case, potentially leading to incorrect buffer updates or even skipping the update altogether, which could affect the median calculation.


Recommended steps:

- For an Empty Buffer, Before attempting to calculate the median, check if the buffer is empty. If it is, the function could return a default value (e.g., `0` for the median tick) and an unchanged `medianData`. This would signal to the caller that the median could not be calculated due to the lack of observations.

- For Duplicate Observations, When updating the buffer with the latest observation, include logic to handle the case where the observation is the same as an existing one. This could involve skipping the update if the observation is a duplicate or adjusting the logic to correctly update the buffer and the order map in such cases.

Here's a conceptual example of how an empty buffer can be handled:

```solidity
if (bufferIsEmpty) {
    // Handle the case where the buffer is empty
    return (0, medianData); // Return a default median tick and unchanged medianData
}
```

And for handling duplicate observations, you might need to adjust the logic within the loop that updates the buffer and the order map to correctly handle cases where the latest observation is a duplicate.






### L-07: Incorrect Collateral Requirement Calculation for Short Positions Out of Range
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1350

In the `_getRequiredCollateralSingleLegNoPartner` function, there is an issue with the calculation of the collateral requirement for a short position that is in-the-money (ITM) or at-the-money (ATM) but out of range. Specifically, the line `required;` on its own does not perform any operation or assignment, which is likely a mistake. This line should either be removed if it's not needed or corrected to perform the intended calculation. The correct calculation should involve adding the product of `amountMoved` and `c2` to `required`, as indicated by the comment above it. However, the line is incorrectly written and does not perform the intended operation.

Recommended step:
Correct the line to perform the intended calculation by adding the product of `amountMoved` and `c2` to `required`. The corrected line should be:

```solidity
required += Math.mulDiv96RoundingUp(amountMoved, c2);
```




### L-08: Unsafe ERC20 Operations should not be used

ERC20 functions may not behave as expected. For example: return values are not always meaningful. It is recommended to use OpenZeppelin's SafeERC20 library.

- CollateralTracker.sol [Line: 333](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L333)

	```solidity
	        return ERC20Minimal.transfer(recipient, amount);
	```

- CollateralTracker.sol [Line: 352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L352)

	```solidity
	        return ERC20Minimal.transferFrom(from, to, amount);
	```

- InteractionHelper.sol [Line: 32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L32)

	```solidity
	        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
	```

- InteractionHelper.sol [Line: 33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L33)

	```solidity
	        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
	```

- InteractionHelper.sol [Line: 36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L36)

	```solidity
	        IERC20Partial(token0).approve(address(ct0), type(uint256).max);
	```

- InteractionHelper.sol [Line: 37](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L37)

	```solidity
	        IERC20Partial(token1).approve(address(ct1), type(uint256).max);
	```



### L-09: Missing checks for `address(0)` when assigning values to address state variables

Check for `address(0)` when assigning values to address state variables.

- CollateralTracker.sol [Line: 241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L241)

	```solidity
	        s_underlyingToken = underlyingIsToken0 ? token0 : token1;
	```

- CollateralTracker.sol [Line: 244](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L244)

	```solidity
	        s_panopticPool = panopticPool;
	```

- CollateralTracker.sol [Line: 254](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L254)

	```solidity
	        s_univ3token0 = token0;
	```

- CollateralTracker.sol [Line: 255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L255)

	```solidity
	        s_univ3token1 = token1;
	```

- CollateralTracker.sol [Line: 602](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L602)

	```solidity
	            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
	```

- CollateralTracker.sol [Line: 895](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L895)

	```solidity
	        balanceOf[delegatee] += convertToShares(assets);
	```

- CollateralTracker.sol [Line: 904](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L904)

	```solidity
	        balanceOf[delegatee] -= convertToShares(assets);
	```

- PanopticFactory.sol [Line: 136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L136)

	```solidity
	            s_owner = _owner;
	```

- PanopticFactory.sol [Line: 152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L152)

	```solidity
	        s_owner = newOwner;
	```

- PanopticPool.sol [Line: 302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L302)

	```solidity
	        s_univ3pool = IUniswapV3Pool(_univ3pool);
	```

- PanopticPool.sol [Line: 318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L318)

	```solidity
	        s_collateralToken0 = collateralTracker0;
	```

- PanopticPool.sol [Line: 319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L319)

	```solidity
	        s_collateralToken1 = collateralTracker1;
	```

- PanopticPool.sol [Line: 654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L654)

	```solidity
	        s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
	```

- ERC1155Minimal.sol [Line: 82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L82)

	```solidity
	        isApprovedForAll[msg.sender][operator] = approved;
	```

- ERC1155Minimal.sol [Line: 237](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L237)

	```solidity
	        balanceOf[from][id] -= amount;
	```

- ERC20Minimal.sol [Line: 50](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L50)

	```solidity
	        allowance[msg.sender][spender] = amount;
	```

- ERC20Minimal.sol [Line: 62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L62)

	```solidity
	        balanceOf[msg.sender] -= amount;
	```

- ERC20Minimal.sol [Line: 67](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L67)

	```solidity
	            balanceOf[to] += amount;
	```

- ERC20Minimal.sol [Line: 84](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L84)

	```solidity
	        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
	```

- ERC20Minimal.sol [Line: 86](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L86)

	```solidity
	        balanceOf[from] -= amount;
	```

- ERC20Minimal.sol [Line: 91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L91)

	```solidity
	            balanceOf[to] += amount;
	```

- ERC20Minimal.sol [Line: 104](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L104)

	```solidity
	        balanceOf[from] -= amount;
	```

- ERC20Minimal.sol [Line: 109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L109)

	```solidity
	            balanceOf[to] += amount;
	```

- ERC20Minimal.sol [Line: 126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L126)

	```solidity
	            balanceOf[to] += amount;
	```

- ERC20Minimal.sol [Line: 137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L137)

	```solidity
	        balanceOf[from] -= amount;
	```



### L-10: `public` functions not used internally could be marked `external`

Instead of marking a function as `public`, consider marking it as `external` if it is not used internally.

- CollateralTracker.sol [Line: 323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L323)

	```solidity
	    function transfer(
	```

  - CollateralTracker.sol [Line: 341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L341)

	```solidity
	    function transferFrom(
	```

- CollateralTracker.sol [Line: 1141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1141)

	```solidity
	    function getAccountMarginDetails(
	```

- PanopticFactory.sol [Line: 134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134)

	```solidity
	    function initialize(address _owner) public {
	```

- PanopticPool.sol [Line: 1444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1444)

	```solidity
	    function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {
	```

- SemiFungiblePositionManager.sol [Line: 540](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L540)

	```solidity
	    function safeTransferFrom(
	```

- SemiFungiblePositionManager.sol [Line: 566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L566)

	```solidity
	    function safeBatchTransferFrom(
	```

- FeesCalc.sol [Line: 97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L97)

	```solidity
	    function calculateAMMSwapFees(
	```

- Multicall.sol [Line: 12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L12)

	```solidity
	    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
	```

- ERC1155Minimal.sol [Line: 81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L81)

	```solidity
	    function setApprovalForAll(address operator, bool approved) public {
	```

- ERC1155Minimal.sol [Line: 94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L94)

	```solidity
	    function safeTransferFrom(
	```

- ERC1155Minimal.sol [Line: 130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L130)

	```solidity
	    function safeBatchTransferFrom(
	```

- ERC1155Minimal.sol [Line: 178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L178)

	```solidity
	    function balanceOfBatch(
	```

- ERC1155Minimal.sol [Line: 200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L200)

	```solidity
	    function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
	```

- ERC20Minimal.sol [Line: 49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L49)

	```solidity
	    function approve(address spender, uint256 amount) public returns (bool) {
	```

- ERC20Minimal.sol [Line: 61](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L61)

	```solidity
	    function transfer(address to, uint256 amount) public virtual returns (bool) {
	```

- ERC20Minimal.sol [Line: 81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L81)

	```solidity
	    function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
	```


### L-11:  Event is missing `indexed` fields

Index event fields make the field more quickly accessible to off-chain tools that parse events. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

- CollateralTracker.sol [Line: 49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L49)

	```solidity
	    event Deposit(address indexed sender, address indexed owner, uint256 assets, uint256 shares);
	```

- PanopticFactory.sol [Line: 43](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L43)

	```solidity
	    event PoolDeployed(
	```

- PanopticPool.sol [Line: 38](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L38)

	```solidity
	    event AccountLiquidated(
	```

- PanopticPool.sol [Line: 62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L62)

	```solidity
	    event PremiumSettled(
	```

- PanopticPool.sol [Line: 75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L75)

	```solidity
	    event OptionBurnt(
	```

- PanopticPool.sol [Line: 90](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L90)

	```solidity
	    event OptionMinted(
	```

- SemiFungiblePositionManager.sol [Line: 80](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L80)

	```solidity
	    event PoolInitialized(address indexed uniswapPool, uint64 poolId);
	```

- SemiFungiblePositionManager.sol [Line: 87](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L87)

	```solidity
	    event TokenizedPositionBurnt(
	```

- SemiFungiblePositionManager.sol [Line: 98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L98)

	```solidity
	    event TokenizedPositionMinted(
	```

- ERC1155Minimal.sol [Line: 48](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L48)

	```solidity
	    event ApprovalForAll(address indexed owner, address indexed operator, bool approved);
	```

- ERC20Minimal.sol [Line: 18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L18)

	```solidity
	    event Transfer(address indexed from, address indexed to, uint256 amount);
	```

- ERC20Minimal.sol [Line: 24](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L24)

	```solidity
	    event Approval(address indexed owner, address indexed spender, uint256 amount);
	```



### L-12: Empty `require()` / `revert()` statements


Use descriptive reason strings or custom errors for revert paths.

- Math.sol [Line: 361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L361)

	```solidity
	                require(denominator > 0);
	```

- Math.sol [Line: 370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L370)

	```solidity
	            require(denominator > prod1);
	```

- Math.sol [Line: 448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L448)

	```solidity
	                require(result < type(uint256).max);
	```

- Math.sol [Line: 484](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L484)

	```solidity
	            require(2 ** 64 > prod1);
	```

- Math.sol [Line: 547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L547)

	```solidity
	            require(2 ** 96 > prod1);
	```

- Math.sol [Line: 588](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L588)

	```solidity
	                require(result < type(uint256).max);
	```

- Math.sol [Line: 624](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L624)

	```solidity
	            require(2 ** 128 > prod1);
	```

- Math.sol [Line: 665](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L665)

	```solidity
	                require(result < type(uint256).max);
	```

- Math.sol [Line: 701](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L701)

	```solidity
	            require(2 ** 192 > prod1);
	```



### L-13: PUSH0 is not supported by all chains

Solc compiler version 0.8.20 switches the default target EVM version to Shanghai, which means that the generated bytecode will include PUSH0 opcodes. Be sure to select the appropriate EVM version in case you intend to deploy on a chain other than mainnet like L2 chains that may not support PUSH0, otherwise deployment of your contracts will fail.

- CollateralTracker.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- PanopticFactory.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- PanopticPool.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- SemiFungiblePositionManager.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- CallbackLib.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Constants.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Errors.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- FeesCalc.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- InteractionHelper.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Math.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- PanopticMath.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- SafeTransferLib.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Multicall.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- ERC1155Minimal.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- ERC20Minimal.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- IDonorNFT.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- IERC20Partial.sol [Line: 2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```



### L-14: Large literal values multiples of 10000 can be replaced with scientific notation

Use `e` notation, for example: `1e18`, instead of its full numeric value.


- Constants.sol [Line: 9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L9)

	```solidity
	    uint256 internal constant FP96 = 0x1000000000000000000000000;
	```

- Math.sol [Line: 93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L93)

	```solidity
	            if (x >= 0x100000000000000000000000000000000) {
	```

- Math.sol [Line: 97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L97)

	```solidity
	            if (x >= 0x10000000000000000) {
	```

- Math.sol [Line: 101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L101)

	```solidity
	            if (x >= 0x100000000) {
	```

- Math.sol [Line: 105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L105)

	```solidity
	            if (x >= 0x10000) {
	```

- Math.sol [Line: 135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L135)

	```solidity
	                : 0x100000000000000000000000000000000;
	```

- Math.sol [Line: 167](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L167)

	```solidity
	            if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;
	```



### L-15: Internal functions called only once can be inlined

Instead of separating the logic into a separate function, consider inlining the logic into the calling function. This can reduce the number of function calls and improve readability.

- SemiFungiblePositionManager.sol [Line: 320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L320)

	```solidity
	    function beginReentrancyLock(uint64 poolId) internal {
	```

- SemiFungiblePositionManager.sol [Line: 330](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L330)

	```solidity
	    function endReentrancyLock(uint64 poolId) internal {
	```


### L-16: Contract still has TODOs

Contract contains comments with TODOS

- Found in contracts/libraries/Math.sol [Line: 13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L13)

	```solidity
	library Math {
	```




### L-17: Insufficient Comments

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1600

The `_computeStrangle` function attempts to handle a zero pool utilization by negating it and adding 1. This approach, while clever, could lead to  misinterpretation of the pool utilization value, especially if the negation and addition are not clearly documented or understood by other developers working with this contract.
The primary concern is that the negation and addition of 1 to the pool utilization might not be immediately clear to someone reading the code. 

This could potentially lead to confusion or errors in the future, especially if the pool utilization is used in further calculations or logic that assumes it's a positive value. The negation and addition are used to encode information about the position type (strangle), but this encoding might not be immediately obvious to someone not familiar with the specific logic of the contract.
To mitigate this issue, it would be beneficial to add comments explaining why the pool utilization is manipulated in this way and how this manipulation affects the calculation of the required collateral.























