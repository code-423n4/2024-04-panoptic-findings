### Report 1:
#### Overflow or Underflow Error in LeftRight.sol Contract
As noted from the pointer in the comment description in the subRect(...) function, implementation is expected to ensure there is no over flow since the operations are performed inside the unchecked area, However this implementation was only done for type conversion from int256 to int128 but it was not done for the subtraction operations before the conversion which will lead to overflow or underflow breaking protocol functionality.
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L256
```solidity
>>>    /// @notice Subtract two LeftRight-encoded words; revert on overflow or underflow.
    /// @notice FOr each slot, rectify difference `x - y` to 0 if negative.
    /// @param x The minuend
    /// @param y The subtrahend
    /// @return z The difference `x - y`
    function subRect(
        LeftRightSigned x,
        LeftRightSigned y
    ) internal pure returns (LeftRightSigned z) {
        unchecked {
>>>            int256 left256 = int256(x.leftSlot()) - y.leftSlot();
            int128 left128 = int128(left256);

>>>            int256 right256 = int256(x.rightSlot()) - y.rightSlot();
            int128 right128 = int128(right256);

            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

            return
                z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(
                    int128(Math.max(left128, 0))
                );
        }
    }
```
Other similar Overflow and underflow instances are present protocol contract and should be corrected e.g [L1340](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1340) of SemiFungiblePositionManager.sol contract etc
###  Report 2:
#### Denial of Service
Denial of Service when the number Of Leading Hex Zeros in address is exactly 39.
The function in the code snippet shows how numberOfLeadingHexZeros(...) function is implemented, when all the address is zero, 40 is returned, but when it is not, a call is made to Math.mostSignificantNibble(...) function, expansion of the function at [L91](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L91) shows that the lowest amount it can return for a non zero address is 1 meaning when one is returned for an address that should have 39 zero address the 1 is instead subtracted from 39 instead of 40 which would return to 38. basically the code does not include implementation to handle address with 39 Leading Hex zeros
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L77
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L91
```solidity
    function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {
        unchecked {
---            return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr)); ❌
+++            return addr == address(0) ? 40 : 40 - Math.mostSignificantNibble(uint160(addr));
        }
    }
```