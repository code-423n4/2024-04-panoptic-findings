# Panoptic QA report by Timenov

## Summary

|               | Issue                                | Instances |
| ------------- | :----------------------------------- | :-------: |
| [I-01] | Typo. |     1     |
| [I-02] | Constants style not followed. |    4     |
| [I-03] | ERC20Minimal can support interface. |     1     |
| [L-01] | `initialize` function will not revert. |     1     |
| [L-02] | `maxMint` return value will never be used. |     1     |
| [L-03] | `DONOR_NFT` can get stuck. |     1     |
| [L-04] | No validation of equal length. |     1     |

### [I-01] Typo.
In `CollateralTracker.sol` the `previewRedeem` function Natpec @notice says `returns the amount of assets resulting from a given amount of shares being redeemed`. However `returns` must be `Returns`. 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L578

### [I-02] Constants style not followed.
The dev team has added another file called `Constants.sol` only to hold constant variables. However `CollateralTracker`, `PanopticFactory`, `PanopticPool` and `SemiFungiblePositionManager` have constant variables defined within them. Consider storing constants only in `Constants.sol`, the same `Errors.sol` is done.

### [I-03] ERC20Minimal can support interface.
The `ERC1155Minimal` contract has `supportsInterface` function.

```solidity
    function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
        return
            interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165
            interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155
    }
```

However `ERC20Minimal` does not have it. Consider adding `supportsInterface` function and add the ERC20 interface id.

### [L-01] `initialize` function will not revert.
A `PanopticFactory` is initialized from the `initialize` function.

```solidity
    function initialize(address _owner) public {
        if (!s_initialized) {
            s_owner = _owner;
            s_initialized = true;
        }
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134-L139

However this function will never revert as there is no `require` or `revert` statement. This means that even if the check is not satisfied, the tx will go through. Consider reverting if `s_initialized == true`.

### [L-02] `maxMint` return value will never be used.
The `CollateralTracker` is used as ERC4626 vault and has `maxDeposit` and `maxMint` view functions.

```solidity
    function maxDeposit(address) external pure returns (uint256 maxAssets) {
        return type(uint104).max;
    }
```

```solidity
    function maxMint(address) external view returns (uint256 maxShares) {
        unchecked {
            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
        }
    }
```

However in `deposit()` and `mint()` only `type(uint104).max` is used for validation which is the same as the `maxDeposit` return value. Therefore the `maxMint` return value is never used and can be misleading to user.

### [L-03] `DONOR_NFT` can get stuck.
When deploying a `PanopticPool` through `PanopticFactory`, the deployer will get NFT as a reward. `DonorNFT` is out of scope, but with it's current implementation, if the deployer does not implement `onERC721Received`, the NFT will be minted to him, but he will never be able to use it. Consider using `_safeMint` instead of `_mint` when deploying the `DonorNFT.sol`. This issue is also tied with `PanopticFactory` as it will affect the deployer of the pool.

### [L-04] No validation of equal length.
In `SemiFungiblePositionManager::safeBatchTransferFrom`, the @dev Natspec states `@dev ids and amounts must be of equal length`, but there is no such validation. Consider adding a check at the beginning of the function to validate `ids.length == amounts.length`.