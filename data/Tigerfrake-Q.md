### [L-1] Using `delegatecall` inside a loop may cause issues with `payable` functions
##### Description:
If one of the delegatecall consumes part of the `msg.value`, other calls might fail, if they expect the full `msg.value`.

##### Instances:

- https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L12-L36

```solidity
    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
        results = new bytes[](data.length);
        for (uint256 i = 0; i < data.length; ) {
            (bool success, bytes memory result) = address(this).delegatecall(data[i]); // @audit delegatecall in a loop


            if (!success) {
                // Bubble up the revert reason
                // The bytes type is ABI encoded as a length-prefixed byte array
                // So we simply need to add 32 to the pointer to get the start of the data
                // And then revert with the size loaded from the first 32 bytes
                // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
                // However, we have chosen to simply replicate the the normal behavior of the call
                // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
                assembly ("memory-safe") {
                    revert(add(result, 32), mload(result))
                }
            }


            results[i] = result;


            unchecked {
                ++i;
            }
        }
    }
```

##### Recommendation:
Consider using a different design, or fully document this decision to avoid potential issues.

### [L-2] Precision Loss When Dividing Odd Integers by Two
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

### [L-3] Missing array length check
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

### [L-4] Floating pragma
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