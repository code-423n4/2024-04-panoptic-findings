## 1. Define and use `constant` variables instead of using literals

use constant literal value instead of runtime calc

find in:

contracts/CollateralTracker.sol [Line: 204](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L201-L208)

suggestion:

```solidity
TICK_DEVIATION = uint256(
                2230 + (12500 * ratioTick) / 1e4 + (7812 * ratioTick ** 2) / 1e8 + (6510 * ratioTick ** 3) / 1e12
            );
```

find in:

contracts/PanopticPool.sol [Line:1348](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1348) | [Line:1353](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1353) | [Line:1552](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1552) | [Line:1561](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1561) | [Line:1635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1635) | [Line:1636](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1636) | [Line:1769](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1769) | [Line:1771](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1771) | [Line:1942](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1942) | [Line:1959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1959)

contracts/SemiFungiblePositionManager.sol [Line: 1352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1352) | [Line: 1357](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1357)

suggestion:

> use constant literal value `18446744073709552000` instead of calc 2**64 multi times
