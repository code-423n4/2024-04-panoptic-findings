# [1] Utilize `maxDeposit()` directly in `deposit()` function

**File:** `CollateralTracker.sol`


[File: CollateralTracker.sol](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L392-L394)
```
    function maxDeposit(address) external pure returns (uint256 maxAssets) {
        return type(uint104).max;
    }
```


[File: CollateralTracker.sol](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L417-L418)
```
    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
        if (assets > type(uint104).max) revert Errors.DepositTooLarge();
```

Function `maxDeposit()` hardcodes the maximum amount of the underlying asset that can be deposited into the Vault to `type(uint104).max`.
The very same value is used in function `deposit()`. To improve the code readability, it would be better to use `maxDeposit()` directly in the `deposit()` function:

```
    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
        if (assets > maxDeposit(receiver)) revert Errors.DepositTooLarge();
```

This will stick to the convection of other EIP-4626 related functions. E.g., function `redeem()` straightforwardly checks if `shares > maxRedeem(owner)`; function `withdraw()` straightforwardly checks if `assets > maxWithdraw(owner)`:

```
function withdraw(
        uint256 assets,
        address receiver,
        address owner
    ) external returns (uint256 shares) {
        if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();
```


```
function redeem(
        uint256 shares,
        address receiver,
        address owner
    ) external returns (uint256 assets) {
        if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption(); 
```

This implies, that function `deposit()` should also straightforwardly check if `assets > maxDeposit(receiver)`


# [2] `balanceOfBatch()` breaks the composability with EIP-1155

**File:** `ERC1155Minimal.sol`

According to provided documentation, `ERC1155Minimal.sol` is `A minimalist implementation of the ERC1155 token standard without metadata`. 


According to [EIP-1155](https://eips.ethereum.org/EIPS/eip-1155): `The balanceOfBatch function allows clients to retrieve balances of multiple owners and token IDs with a single call.`

However, the current implementation is incorrect, because it does not provide any verification if `owners.length == ids.length`.

* when `owners.length > ids.length`
Function will simply revert, because there will be no enough elements in `ids` array:
```
balances[i] = balanceOf[owners[i]][ids[i]];
```

E.g., calling `balanceOfBatch([0xAAA, 0xBBB, 0xCCC], [1, 2])` will simply revert on accessing non-existing `ids[3]` element.

* when `owners.length < ids.length`

Function will return incorrect results, because it will only iterate from 0 to `owners.length`
```
for (uint256 i = 0; i < owners.length; ++i)
```

Function will update `balances` at indexes from 0 to  `owners.length`. When `owners.length < ids.length`, the remaining `ids` values will be omitted.

E.g., calling `balanceOfBatch([0xAAA, 0xBBB], [1, 2, 3])` will omit `3`. Other protocols which integrates with `ERC1155Minimal.sol` might be mislead by this behavior.


Please notice, that the protocol straightforwardly states that its implementation is a modified version from Solmate

[File: ERC1155Minimal.sol](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L9)
```
/// @author Modified from Solmate (https://github.com/transmissions11/solmate/blob/v7/src/tokens/ERC1155.sol)
```

Examining Solmate's implementation shows the extra check:
```
require(owners.length == ids.length, "LENGTH_MISMATCH");
```

This check should also be implemented in `ERC1155Minimal.sol`.


# [3] `ERC1155Minimal.sol` misses batch minting and batch burning

**File:** `ERC1155Minimal.sol`

The protocol straightforwardly states that its implementation is a modified version from Solmate

[File: ERC1155Minimal.sol](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L9)
```
/// @author Modified from Solmate (https://github.com/transmissions11/solmate/blob/v7/src/tokens/ERC1155.sol)
```

The Solmate's code implements two additional functions: `_batchMint()` and `_batchBurn()` which allow to perform batch minting and batch burnings. Those functions are, however missed in the `ERC1155Minimal.sol`. While this does not pose any security risk - consider extending the `ERC1155Minimal.sol` abilities of burning and minting in batches.


# [4] Lack of validation of `COMMISSION_FEE`

**File:** `CollateralTracker.sol`

[File: CollateralTracker.sol](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L187)
```
COMMISSION_FEE = _commissionFee;
```

Immutable variable `COMMISSION_FEE` is set in the constructor, however, its value is nowhere check.
If, during the deployment, this variable would be set to value greater than `DECIMALS` constant (`> 10_000`) - some functions in `CollateralTracker.sol` will overflow and the contract will be needed to be redeployed with proper `COMMISSION_FEE` value.


[File: CollateralTracker.sol](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L399)
```
 function previewDeposit(uint256 assets) public view returns (uint256 shares) {
        // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid
        unchecked {
            shares = Math.mulDiv(
                assets * (DECIMALS - COMMISSION_FEE),
```

[File: CollateralTracker.sol](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L399)
```
function previewMint(uint256 shares) public view returns (uint256 assets) {
[...]
        unchecked {
            assets = Math.mulDivRoundingUp(
                shares * DECIMALS,
                totalAssets(),
                totalSupply * (DECIMALS - COMMISSION_FEE)
```

When contract will be deployed with `COMMISSION_FEE > DECIMALS`, `DECIMALS - COMMISSION_FEE` in functions `previewDeposit()` and `previewMint()` will overflow (please notice that this calculation is in the `unchecked` block) - leading to incorrect calculations.

# [5] Format math operations in comments for better code readability

**File:** `CollateralTracker.sol`

Better formatting the math operations in the comments sections increases the code readability, thus it's highly recommended.

E.g., in `CollateralTracker.sol` at lines 457-460, math operations are properly formatted:

```
        // finalAssets - convertedAssets = commissionRate * finalAssets
        // finalAssets - commissionRate * finalAssets = convertedAssets
        // finalAssets * (1 - commissionRate) = convertedAssets
        // finalAssets = convertedAssets / (1 - commissionRate)
```

However, line 198 misses the proper format:

[File: CollateralTracker.sol](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L198)
```
 // taylor expand log(1-sellCollateralRatio)/log(1.0001) around sellCollateralRatio=2000 up to 3rd order
```

Use whitespaces, to properly format math operations - so it will be easier to read them and understand them:

```
// taylor expand log(1 - sellCollateralRatio) / log(1.0001) around sellCollateralRatio = 2000 up to 3rd order
```