



```
+------+------------------------------------------------------------------------------+----------+
| Q.A  | Issue                                                                        | Instances|
+------+------------------------------------------------------------------------------+----------+
| L-01 | Function Visibility marked as public for internal logic                      |    2     |
| L-02 | Implement Length Check in safeBatchTransferFrom and balanceOfBatch Functions |    2     |
| L-03 | Implement Address to Validation for ERC1155 token Receiver                   |    3     |
| L-04 | Unused variable MAX_UINT256 Constant in PanoticPool and Math Contracts       |    4     |
+------+------------------------------------------------------------------------------+----------+
```




## L-01  Function Visibility marked as public for internal logic 

#### Issue:

The `convertToShares` and `convertToAssets` functions are currently labeled as `public`, allowing external access. However, these functions are designed for internal calculations and logic within the contract and do not require external visibility or interaction.

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L379

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L386

Code Reference instances

convertToShares Use
1. https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L446
2.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L573
3.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L883
4.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L895
5.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L904
6.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L930
7.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L977
8.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L980
9.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1020
10.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1077

convertToAssets Use
1.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L511
2.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L582
3.https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1181

 
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

### L-03 Implement Address to Validation for ERC1155 token Receiver

#### Issue:

The `safeTransferFrom`, `safeBatchTransferFrom`, and `_mint` functions in the ERC1155 contract currently lack a check to ensure that the `address to` is a valid address capable of receiving the ERC1155 token. This omission can lead to unexpected behavior within the contract.

#### Recommendation:

To enhance the security and reliability of the ERC1155 contract, it is essential to implement a validation check to ensure that the `address to` parameter is a valid address before proceeding with the token transfer or minting operation. This check will help prevent potential issues and ensure that tokens are only transferred or minted to valid and intended addresses.

#### Relevant Code References:

- [ERC1155Minimal.sol - safeTransferFrom](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L112-L119)
- [ERC1155Minimal.sol - safeBatchTransferFrom](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L163-L170)
- [ERC1155Minimal.sol - _mint](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L222-L228)
- [Solmate ERC1155.sol - Address Validation](https://github.com/transmissions11/solmate/blob/e8f96f25d48fe702117ce76c79228ca4f20206cb/src/tokens/ERC1155.sol#L75)
- [Solmate ERC1155.sol - Address Validation](https://github.com/transmissions11/solmate/blob/e8f96f25d48fe702117ce76c79228ca4f20206cb/src/tokens/ERC1155.sol#L115)
- [Solmate ERC1155.sol - Address Validation](https://github.com/transmissions11/solmate/blob/e8f96f25d48fe702117ce76c79228ca4f20206cb/src/tokens/ERC1155.sol#L168)

#### Proposed Code Modification:

Implement Address Validation like it is in Solmate ERC1155.sol


## | L-04 | Unused variable MAX_UINT256 Constant in PanoticMath and Math Contracts

#### Issue:

The `uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;` constant is declared in both the PanoticMath and Math contracts. However, this constant is not being used, and the contracts continue to call `type(uint256).max` directly. 

#### Relevant Code:

```solidity
// In PanoticMath and Math contracts
uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```

Math.sol
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L15

PanopticMath.sol
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L23

Reference to instance

Line 176
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L176

Line 448 
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L448

Line 588

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L588

Line 665

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L665


#### Issue Analysis:

The declared `MAX_UINT256` constant is not being utilized in the code, and the contract continues to use `type(uint256).max` directly. This inconsistency may lead to confusion and could potentially cause issues if the `MAX_UINT256` constant is intended to be used for such purposes.

#### Recommendation:

To maintain consistency and clarity in the codebase, it is recommended to utilize the declared `MAX_UINT256` constant instead of calling `type(uint256).max` directly in the appropriate areas of the contracts.

#### Mitigation:

Replace `type(uint256).max` with `MAX_UINT256` in the appropriate areas of the contracts where the maximum uint256 value is required.



