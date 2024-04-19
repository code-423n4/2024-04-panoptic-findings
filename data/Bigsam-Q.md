



```
+------+------------------------------------------------------------------------------+----------+
| Q.A  | Issue                                                                        | Instances|
+------+------------------------------------------------------------------------------+----------+
| L-01 | Function Visibility marked as public for internal logic                      |    2     |
| L-02 | Implement Length Check in safeBatchTransferFrom and balanceOfBatch Functions |    2     |
| L-03 | Implement Address to Validation for ERC1155 token Receiver                   |    3     |
+------+------------------------------------------------------------------------------+----------+
```




## L-01  Function Visibility marked as public for internal logic 

#### Issue:

The `convertToShares` and `convertToAssets` functions are currently labeled as `public`, allowing external access. However, these functions are designed for internal calculations and logic within the contract and do not require external visibility or interaction.

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L379

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L386

#### Recommendation:

To enhance the security and integrity of the smart contract, it is advisable to change the visibility of these functions from `public` to `internal`.

#### Proposed Code Modification:

```solidity
/// @notice Returns the amount of shares that can be minted for the given amount of assets.
/// @param assets The amount of assets to be deposited.
/// @return shares The amount of shares that can be minted.
function convertToShares(uint256 assets) internal view returns (uint256 shares) {
    return Math.mulDiv(assets, totalSupply, totalAssets());
}

/// @notice Returns the amount of assets that can be redeemed for the given amount of shares.
/// @param shares The amount of shares to be redeemed.
/// @return assets The amount of assets that can be redeemed.
function convertToAssets(uint256 shares) internal view returns (uint256 assets) {
    return Math.mulDiv(shares, totalAssets(), totalSupply);
}
```


## L-02  Implement Length Check in safeBatchTransferFrom and balanceOfBatch Functions

#### Issue:

The `safeBatchTransferFrom` and `balanceOfBatch` functions currently lack a check to ensure that the `owners` and `ids` arrays are of equal length. This oversight can lead to unexpected behavior within the contract.

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L124-L143

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L174-L187

## Code to check reference in  Openzeppelin ERC115

https://github.com/OpenZeppelin/openzeppelin-contracts/blob/0a25c1940ca220686588c4af3ec526f725fe2582/contracts/token/ERC1155/ERC1155.sol#L206

https://github.com/OpenZeppelin/openzeppelin-contracts/blob/0a25c1940ca220686588c4af3ec526f725fe2582/contracts/token/ERC1155/ERC1155.sol#L89



#### Recommendation:

To prevent potential issues and ensure consistent and expected behavior, it is crucial to implement a check to verify that the `owners` and `ids` arrays are of equal length in both the `safeBatchTransferFrom` and `balanceOfBatch` functions.

#### Proposed Code Modification:

```solidity
 function balanceOfBatch(
        address[] calldata owners,
        uint256[] calldata ids
    ) public view returns (uint256[] memory balances)  {
    require(ids.length == owners.length, "Length mismatch between ids and owners");
    // Existing implementation
}

 function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public virtual  {
    require(amounts.length == ids.length, "Length mismatch between owners and ids");
    // Existing implementation
}
```

---