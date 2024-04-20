### [L-1] `CollateralTracker::maxDeposit` amount should be a constant

## Description
`CollateralTracker::maxDeposit` should be a constant

## Impact
The maximum allowed deposit value is type(uint104).max, but it is not a constant variable. It is hardcoded in functions `CollateralTracker::maxDeposit`, `CollateralTracker::deposit` and `CollateralTracker::maxMint`. The developer/engineer could make a mistake, update the maximum allowed deposit value in function deposit but forget to update the value in maxDeposit/maxMint and cause a big discrepancy.

## Proof of Concept

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L392-L394

```javascript
    function maxDeposit(address) external pure returns (uint256 maxAssets) {
    @>    return type(uint104).max;
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L417-L418

```javascript
    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
    @>    if (assets > type(uint104).max) revert Errors.DepositTooLarge();

```

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444-L448

```javascript
    function maxMint(address) external view returns (uint256 maxShares) {
        unchecked {
    @>        return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
        }
    }
```

**Recommended Mitigation:**

```diff
    // CONSTANTS
+    uint104 internal constant MAX_DEPOSIT = type(uint104).max;

    function maxDeposit(address) external pure returns (uint256 maxAssets) {
-        return type(uint104).max;
+        return MAX_DEPOSIT;
    }

    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
-       if (assets > type(uint104).max) revert Errors.DepositTooLarge();
+       if (assets > MAX_DEPOSIT) revert Errors.DepositTooLarge();


    function maxMint(address) external view returns (uint256 maxShares) {
        unchecked {
-            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
+            return (convertToShares(MAX_DEPOSIT) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
        }
    }

```
