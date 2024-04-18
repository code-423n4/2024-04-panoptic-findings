### [L-1] Precision Loss When Dividing Odd Integers by Two
##### Description:
The contract has a flaw where it may lose precision when dividing odd integers by two. This
is because in Solidity, integer division is floor division, meaning that the result of the division operation will be the largest integer less than or equal to the exact result. Therefore,
when an odd integer is divided by two, the result will be rounded down, leading to a loss of precision.

##### Instances:
- https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L778
```solidity
min_sell_ratio /= 2;
```

- https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L843
```solidity
return BUYER_COLLATERAL_RATIO / 2;
```


##### Recommendation:
When dividing an amount by two, consider taking the first amount as the division result by
two, and the second one to be the total amount minus the first one.

### [L-2] Missing array length check
##### Description:
The `balanceOfBatch()` function in `ERC1155Minimal` is used to Query balances for multiple users and tokens at once. According to comments:
```solidity
    /// @dev `owners` and `ids` should be of equal length
```
However, there is no check to verify this.

##### Instance:
- https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L178-L191
```solidity
    function balanceOfBatch(
        address[] calldata owners,
        uint256[] calldata ids
    ) public view returns (uint256[] memory balances) {
        balances = new uint256[](owners.length);


        // Unchecked because the only math done is incrementing
        // the array index counter which cannot possibly overflow.
        unchecked {
            for (uint256 i = 0; i < owners.length; ++i) {
                balances[i] = balanceOf[owners[i]][ids[i]];
            }
        }
    }
```

##### Impact
This can result in a revert of the function if the `owners` and `ids` are not of equal length.

##### Recommendation:
Add a check at the beginning of this function to ensure that the `owners` and `ids` are of equal length.

### [L-3] Floating pragma
##### Description:
The disadvantage of using a floating pragma is that it can lead to inconsistencies and potential bugs. When a contract is compiled with a different compiler version, it might produce different bytecode due to changes in the compiler, even if the source code looks the same. This can lead to unexpected behavior if the contract is deployed on a network with a different compiler version than the one it was tested with.

##### Instance:
- https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L2
```solidity
pragma solidity ^0.8.0;
```
##### Recommendation:
It's generally recommended to lock the compiler version to avoid these issues.
```solidity
pragma solidity 0.8.0;
```

### [L-4] Missing Value verification
##### Description:
Certain functions lack value safety check. The values of the arguments should be verified to allow only the ones that comply with the contract's logic.

##### Instance:
In the constructor of `CollateralTracker`, values such as `_sellerCollateralRatio, _buyerCollateralRatio` are not sanitized to meet the specs as highlighted in the comments:

> [constructor()](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L178-L211)
```solidity
    constructor(
        uint256 _commissionFee,
        uint256 _sellerCollateralRatio,
        uint256 _buyerCollateralRatio,
        int256 _forceExerciseCost,
        uint256 _targetPoolUtilization,
        uint256 _saturatedPoolUtilization,
        uint256 _ITMSpreadMultiplier
    ) {
        COMMISSION_FEE = _commissionFee;
        SELLER_COLLATERAL_RATIO = _sellerCollateralRatio;
        BUYER_COLLATERAL_RATIO = _buyerCollateralRatio;
        FORCE_EXERCISE_COST = _forceExerciseCost;
        TARGET_POOL_UTIL = _targetPoolUtilization;
        SATURATED_POOL_UTIL = _saturatedPoolUtilization;
        ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;

         ---- ---------more code----------
}
```
> [Comments on the variables](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L139-L145)
```solidity
    /// @notice Required collateral ratios for buying, represented as percentage * 10_000.
    /// i.e 20% -> 0.2 * 10_000 = 2_000.
    uint256 immutable SELLER_COLLATERAL_RATIO;


    /// @notice Required collateral ratios for selling, represented as percentage * 10_000.
    /// i.e 10% -> 0.1 * 10_000 = 1_000.
    uint256 immutable BUYER_COLLATERAL_RATIO;
```
##### Recommendation:
Verify the values provided in the arguments. This issue can be addressed by utilizing a `require` statement.

### [L-5] For same condition checks, use modifiers
##### Description:
The main advantage of using modifiers for the same condition checks in different functions is code reusability and readability. Instead of repeating the same condition check in every function that requires it, you can define a modifier once and then apply it to any function that needs it. This makes your code cleaner and easier to maintain.

##### Instances:
The following check has been used in multiple instances to put a limit to the amount of `assets deposited`

> [CollateralTracker.deposit()](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L418)
```solidity
        if (assets > type(uint104).max) revert Errors.DepositTooLarge();
```

> [CollateralTracker.mint()](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L480)
```solidity
        if (assets > type(uint104).max) revert Errors.DepositTooLarge();
```
This loos redundant and should be replaced with a modifier.

## [L-6] Unnecessary solvency checks
In `PanopticPool.mintOptions()`, we need to perform solvency check on user's account to ensure they had enough buying power to mint the option. 
However, the solvency validation would occur for every invocation of the `mintOptions()` function, irrespective of whether the user has open positions or not.

- https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L659-L661

```solidity
        // Perform solvency check on user's account to ensure they had enough buying power to mint the option
        // Add an initial buffer to the collateral requirement to prevent users from minting their account close to insolvency
        uint256 medianData = _validateSolvency(msg.sender, positionIdList, BP_DECREASE_BUFFER);
```
## Impact
Potential Overhead: Executing the solvency validation unconditionally might introduce additional overhead, especially in situations where the user frequently interacts with the contract but rarely has open positions.

## Mitigation
Add a conditional check for solvency validation i.e only if the user has open positions.

```solidity
if (positionIdList.length > 0){
    uint256 medianData = _validateSolvency(msg.sender, positionIdList, BP_DECREASE_BUFFER);
    if (medianData != 0) s_miniMedian = medianData;
}
```
