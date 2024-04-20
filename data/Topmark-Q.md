### Report 1:
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
###  Report 2:
