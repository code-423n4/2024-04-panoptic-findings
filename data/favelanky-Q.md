
## Low Risk Issues

| Number | Issues | Instances |
|:------:|:--------------|:-------:|
| [L-01](#l-01-solidity-0820-may-not-work-on-other-chains)  | Solidity 0.8.20 may not work on other chains | 20 |
| [L-02](#l-02-solmates-safetransferlib-doesnt-check-whether-the-erc20-contract-exists)  | Solmate's SafeTransferLib doesn't check whether the ERC20 contract exists | 14 |
| [L-03](#l-03-loss-of-precision)  | Loss of precision | 35 |
| [L-04](#l-04-division-before-multiplication-can-lead-to-precision-errors)  | Division before multiplication can lead to precision errors | 2 |
| [L-05](#l-05-initializer-can-be-frontrun)  | Initializer can be frontrun | 2 |
| [L-06](#l-06-zero-address-check-is-missing-is-setter-functions)  | Zero address check is missing is setter functions | 4 |
| [L-07](#l-07-approve-typeuint256max-not-work-with-some-tokens)  | Approve `type(uint256).max` not work with some tokens | 4 |
| [L-08](#l-08-use-safeapprove-instead-of-approve)  | Use `safeApprove` instead of `approve` | 4 |
| [L-09](#l-09-symbol-is-not-a-part-of-the-erc20-standard)  | `symbol()` is not a part of the ERC-20 standard | 6 |
| [L-10](#l-10-decimals-is-not-a-part-of-the-erc20-standard)  | `decimals()` is not a part of the ERC-20 standard | 2 |

Total: 93 over 10 issues

## Non-Critical Issues

| Number | Issues | Instances |
|:------:|:--------------|:-------:|
| [N-01](#n-01-modifier-name-should-be-in-mixedcase)  | Modifier name should be in mixedCase | 1 |
| [N-02](#n-02-it-is-standard-for-all-external-and-public-functions-to-be-overridden-from-an-interface)  | It is standard for all external and public functions to be overridden from an interface | 63 |
| [N-03](#n-03-function-must-not-be-longer-than-50-lines)  | Function must not be longer than 50 lines | 33 |
| [N-04](#n-04-function-parameter-name-must-be-in-mixedcase)  | Function parameter name must be in mixedCase | 3 |
| [N-05](#n-05-cyclomatic-complexity-of-the-function-is-too-high)  | Cyclomatic complexity of the function is too high | 3 |
| [N-06](#n-06-lines-are-too-long)  | Lines are too long | 407 |
| [N-07](#n-07-visibility-should-be-set-explicitly-rather-than-defaulting-to-internal)  | Visibility should be set explicitly rather than defaulting to `internal` | 8 |
| [N-08](#n-08-constructor-missing-variable-check)  | Constructor missing variable check | 4 |
| [N-09](#n-09-constants-should-be-defined-rather-than-using-magic-numbers)  | `constants` should be defined rather than using magic numbers | 209 |
| [N-10](#n-10-missing-event-for-critical-parameters-change)  | Missing event for critical parameters change | 7 |
| [N-11](#n-11-functions-that-alter-state-should-emit-events)  | Functions that alter state should emit events | 6 |
| [N-12](#n-12-zero-address-check-is-missing-in-nonsetter-functions)  | Zero address check is missing in non-setter functions | 37 |
| [N-13](#n-13-use-inheritdoc-rather-than-using-a-nonstandard-annotation)  | Use `@inheritdoc` rather than using a non-standard annotation | 2 |
| [N-14](#n-14-change-public-to-external-for-functions-that-are-not-called-internally)  | Change `public` to `external` for functions that are not called internally | 14 |
| [N-15](#n-15-constants-in-comparisons-should-appear-on-the-left-side)  | Constants in comparisons should appear on the left side | 97 |
| [N-16](#n-16-redundant-return-statement-with-named-return-variable)  | Redundant return statement with named return variable | 30 |
| [N-17](#n-17-unsafe-conversion-from-unsigned-to-signed-values)  | Unsafe conversion from unsigned to signed values | 25 |
| [N-18](#n-18-remove-unnecessary-brackets)  | Remove unnecessary brackets | 46 |
| [N-19](#n-19-avoid-mutating-function-parameters)  | Avoid mutating function parameters | 6 |
| [N-20](#n-20-local-variables-should-be-named-using-mixedcase)  | Local variables should be named using mixedCase | 12 |
| [N-21](#n-21-overridden-function-names-should-differ)  | Overridden function names should differ | 6 |
| [N-22](#n-22-use--0-instead-of--0-for-unsigned-integer-comparison)  | Use != 0 instead of > 0 for unsigned integer comparison | 4 |
| [N-23](#n-23-inconsistent-spacing-in-comments)  | Inconsistent spacing in comments | 9 |
| [N-24](#n-24-use-modifier-for-special-msgsender)  | Use modifier for special msg.sender | 3 |
| [N-25](#n-25-2n--1-should-be-rewritten-as-typeuintnmax)  | `2**<n> - 1` should be re-written as `type(uint<n>).max` | 41 |
| [N-26](#n-26-complex-casting)  | Complex casting | 6 |
| [N-27](#n-27-unbounded-loop-may-run-out-of-gas)  | Unbounded loop may run out of gas | 8 |
| [N-28](#n-28-private-and-internal-functions-should-start-with-an-underscore)  | Private and internal functions should start with an underscore | 104 |
| [N-29](#n-29-consider-using-delete-rather-than-assigning-zero-to-clear-values)  | Consider using `delete` rather than assigning zero to clear values | 1 |
| [N-30](#n-30-incorrect-natspec-comment-style)  | Incorrect NatSpec comment style | 6 |
| [N-31](#n-31-inline-private-functions-that-are-only-used-once)  | Inline private functions that are only used once | 1 |
| [N-32](#n-32-typetmax-is-inclusive)  | `type(T).max` is inclusive | 7 |
| [N-33](#n-33-custom-error-has-no-error-information)  | Custom error has no error information | 34 |
| [N-34](#n-34-unsigned-divisions-can-be-marked-as-unchecked)  | Unsigned divisions can be marked as unchecked | 1 |
| [N-35](#n-35-requirerevert-statements-should-have-descriptive-reason-strings)  | `require()`/`revert()` statements should have descriptive reason strings | 9 |
| [N-36](#n-36-else-block-not-required)  | `else` block not required | 6 |
| [N-37](#n-37-setters-should-have-initial-value-check)  | Setters should have initial value check | 1 |
| [N-38](#n-38-setters-should-prevent-resetting-of-the-same-value)  | Setters should prevent re-setting of the same value | 1 |
| [N-39](#n-39-event-missing-msgsender-information)  | Event missing `msg.sender` information | 4 |
| [N-40](#n-40-typos-in-the-code)  | Typos in the code | 17 |
| [N-41](#n-41-function-ordering-does-not-follow-the-solidity-style-guide)  | Function ordering does not follow the Solidity style guide | 2 |
| [N-42](#n-42-contract-does-not-follow-the-solidity-style-guides-suggested-layout-ordering)  | Contract does not follow the Solidity style guide's suggested layout ordering | 6 |
| [N-43](#n-43-private-and-internal-variables-should-start-with-an-underscore)  | Private and internal variables should start with an underscore | 93 |
| [N-44](#n-44-imports-could-be-organized-more-systematically)  | Imports could be organized more systematically | 5 |
| [N-45](#n-45-contract-name-should-match-filename)  | Contract name should match filename | 1 |
| [N-46](#n-46-constant-redefined-elsewhere)  | Constant redefined elsewhere | 2 |
| [N-47](#n-47-duplicated-requireif-checks-should-be-refactored-to-a-modifier-or-function)  | Duplicated `require`/`if` checks should be refactored to a modifier or function | 15 |
| [N-48](#n-48-nonlibraryinterface-files-should-use-fixed-compiler-versions-not-floating-ones)  | Non-library/interface files should use fixed compiler versions, not floating ones | 7 |
| [N-49](#n-49-use-a-more-recent-version-of-solidity)  | Use a more recent version of Solidity | 7 |

Total: 1420 over 49 issues



## [L-01] Solidity 0.8.20 may not work on other chains

Solidity 0.8.20 introduces the `PUSH0(0x5f)` opcode which is only supported on ETH mainnet and not on any other chains.

<details>
<summary><i>There are 20 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L2). 

```solidity
File: PanopticFactory.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L2). 

```solidity
File: PanopticPool.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L2). 

```solidity
File: SemiFungiblePositionManager.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L2). 

```solidity
File: libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L2). 

```solidity
File: libraries/Constants.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L2). 

```solidity
File: libraries/Errors.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L2). 

```solidity
File: libraries/FeesCalc.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L2). 

```solidity
File: libraries/InteractionHelper.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L2). 

```solidity
File: libraries/Math.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L2). 

```solidity
File: libraries/PanopticMath.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L2). 

```solidity
File: libraries/SafeTransferLib.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L2). 

```solidity
File: multicall/Multicall.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L2). 

```solidity
File: tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2). 

```solidity
File: tokens/ERC20Minimal.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L2). 

```solidity
File: tokens/interfaces/IDonorNFT.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IDonorNFT.sol#L2). 

```solidity
File: tokens/interfaces/IERC20Partial.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IERC20Partial.sol#L2). 

```solidity
File: types/LeftRight.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L2). 

```solidity
File: types/LiquidityChunk.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L2). 

```solidity
File: types/TokenId.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L2). 

</details>

## [L-02] Solmate's SafeTransferLib doesn't check whether the ERC20 contract exists

Solmate's SafeTransferLib, which is often used to interact with non-compliant/unsafe ERC20 tokens, does not check whether the ERC20 contract exists. The following code will not revert in case the token doesn't exist (yet).

This is stated in the Solmate library: https://github.com/transmissions11/solmate/blob/main/src/utils/SafeTransferLib.sol#L9

Consider using OpenZeppelin's SafeERC20 library instead.

<details>
<summary><i>There are 14 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

15: import {SafeTransferLib} from "@libraries/SafeTransferLib.sol";

424:         SafeTransferLib.safeTransferFrom(

484:         SafeTransferLib.safeTransferFrom(

556:         SafeTransferLib.safeTransferFrom(

616:         SafeTransferLib.safeTransferFrom(

```

[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L15), [424](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L424), [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L484), [556](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L556), [616](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L616). 

```solidity
File: PanopticFactory.sol

21: import {SafeTransferLib} from "@libraries/SafeTransferLib.sol";

182:             SafeTransferLib.safeTransferFrom(

189:             SafeTransferLib.safeTransferFrom(

```

[21](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L21), [182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L182), [189](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L189). 

```solidity
File: SemiFungiblePositionManager.sol

17: import {SafeTransferLib} from "@libraries/SafeTransferLib.sol";

413:             SafeTransferLib.safeTransferFrom(

420:             SafeTransferLib.safeTransferFrom(

456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

```

[17](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L17), [413](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L413), [420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L420), [456](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L456). 

```solidity
File: libraries/SafeTransferLib.sol

9: /// @author Modified from Solmate (https://github.com/Rari-Capital/solmate/blob/main/src/utils/SafeTransferLib.sol)

11: library SafeTransferLib {

```

[9](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L9), [11](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L11). 

</details>

## [L-03] Loss of precision

Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator

<details>
<summary><i>There are 35 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

201:             TICK_DEVIATION = uint256(
202:                 2230 +
203:                     (12500 * ratioTick) /
204:                     10_000 +
205:                     (7812 * ratioTick ** 2) /
206:                     10_000 ** 2 +
207:                     (6510 * ratioTick ** 3) /
208:                     10_000 ** 3
209:             );

249:             _poolFee = fee / 100;

262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

675:                     maxNumRangesFromStrike = Math.max(
676:                         maxNumRangesFromStrike,
677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
678:                     );

730:             exerciseFees = exerciseFees
731:                 .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))
732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

743:             return int256((s_inAMM * DECIMALS) / totalAssets());

795:             return
796:                 min_sell_ratio +
797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798:                 (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);

843:                 return BUYER_COLLATERAL_RATIO / 2;

848:             return
849:                 (BUYER_COLLATERAL_RATIO +
850:                     (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851:                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

```

[201](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L201-L209), [249](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L249), [262](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L262), [446](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L446), [675](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L675-L678), [730](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L730-L732), [743](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L743), [795](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L795-L798), [843](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L843), [848](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L848-L851). 

```solidity
File: PanopticFactory.sol

392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```

[392](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L392). 

```solidity
File: PanopticPool.sol

1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

1545:                     premiaByLeg[leg] = LeftRightSigned
1546:                         .wrap(0)
1547:                         .toRightSlot(
1548:                             int128(
1549:                                 int256(
1550:                                     ((premiumAccumulatorsByLeg[leg][0] -
1551:                                         premiumAccumulatorLast.rightSlot()) *
1552:                                         (liquidityChunk.liquidity())) / 2 ** 64
1553:                                 )
1554:                             )
1555:                         )
1556:                         .toLeftSlot(
1557:                             int128(
1558:                                 int256(
1559:                                     ((premiumAccumulatorsByLeg[leg][1] -
1560:                                         premiumAccumulatorLast.leftSlot()) *
1561:                                         (liquidityChunk.liquidity())) / 2 ** 64
1562:                                 )
1563:                             )
1564:                         );

1633:             LeftRightSigned realizedPremia = LeftRightSigned
1634:                 .wrap(0)
1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))
1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1726:                         .wrap(0)
1727:                         .toRightSlot(
1728:                             uint128(
1729:                                 (grossCurrent[0] *
1730:                                     positionLiquidity +
1731:                                     grossPremiumLast.rightSlot() *
1732:                                     totalLiquidityBefore) / (totalLiquidity)
1733:                             )
1734:                         )
1735:                         .toLeftSlot(
1736:                             uint128(
1737:                                 (grossCurrent[1] *
1738:                                     positionLiquidity +
1739:                                     grossPremiumLast.leftSlot() *
1740:                                     totalLiquidityBefore) / (totalLiquidity)
1741:                             )
1742:                         );

1768:             uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *
1769:                 totalLiquidity) / 2 ** 64;

1770:             uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *
1771:                 totalLiquidity) / 2 ** 64;

1773:             return (
1774:                 LeftRightUnsigned
1775:                     .wrap(0)
1776:                     .toRightSlot(
1777:                         uint128(
1778:                             Math.min(
1779:                                 (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /
1780:                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),
1781:                                 premiumOwed.rightSlot()
1782:                             )
1783:                         )
1784:                     )
1785:                     .toLeftSlot(
1786:                         uint128(
1787:                             Math.min(
1788:                                 (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /
1789:                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),
1790:                                 premiumOwed.leftSlot()
1791:                             )
1792:                         )
1793:                     )
1794:             );

```

[1487](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1487), [1545](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1545-L1564), [1633](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1633-L1636), [1725](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1725-L1742), [1768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1768-L1769), [1770](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1770-L1771), [1773](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1773-L1794). 

```solidity
File: SemiFungiblePositionManager.sol

1367:                     uint256 numerator = netLiquidity + (removedLiquidity / 2 ** VEGOID);

1388:                     uint256 numerator = totalLiquidity ** 2 -
1389:                         totalLiquidity *
1390:                         removedLiquidity +
1391:                         ((removedLiquidity ** 2) / 2 ** (VEGOID));

```

[1367](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1367), [1388](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1388-L1391). 

```solidity
File: libraries/Math.sol

176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

195:             return
196:                 mulDiv(
197:                     uint256(liquidityChunk.liquidity()) << 96,
198:                     highPriceX96 - lowPriceX96,
199:                     highPriceX96
200:                 ) / lowPriceX96;

758:             int256 pivot = arr[uint256(left + (right - left) / 2)];

```

[176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L176), [195](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L195-L200), [758](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L758). 

```solidity
File: libraries/PanopticMath.sol

149:                 ticks[i] =
150:                     (tickCumulatives[i] - tickCumulatives[i + 1]) /
151:                     int256(timestamps[i] - timestamps[i + 1]);

155:             return int24(Math.sort(ticks)[cardinality / 2]);

177:             medianTick =
178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
180:                 2;

194:                     lastObservedTick = int24(
195:                         (tickCumulative_last - tickCumulative_old) /
196:                             int256(timestamp_last - timestamp_old)
197:                     );

249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);

257:                 twapMeasurement[i] = int24(
258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
259:                 );

346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

375:         return (
376:             (width * tickSpacing) / 2,
377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))
378:         );

475:             uint256 notional = asset == 0
476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))
477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

669:                 uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);

678:                 uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

```

[149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L149-L151), [155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L155), [177](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L177-L180), [194](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L194-L197), [249](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L249), [257](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L257-L259), [346](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L346), [347](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L347), [375](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L375-L378), [475](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L475-L477), [669](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L669), [678](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L678). 

</details>

## [L-04] Division before multiplication can lead to precision errors

Because Solidity integer division may truncate, it is often preferable to do multiplication before division to prevent precision loss.

<details>
<summary><i>There are 2 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

249:             _poolFee = fee / 100;

262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

```

[249](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L249), [262](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L262). 

</details>

## [L-05] Initializer can be frontrun

As per [OpenZeppelin’s (OZ) recommendation](https://forum.openzeppelin.com/t/uupsupgradeable-vulnerability-post-mortem/15680/6), “The guidelines are now to make it impossible for anyone to run initialize on an implementation contract, by adding an empty constructor with the initializer modifier. So the implementation contract gets initialized automatically upon deployment.”

<details>
<summary><i>There are 2 instance of this issue:</i></summary>

```solidity
File: PanopticFactory.sol

134:     function initialize(address _owner) public {

```

[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134). 

```solidity
File: SemiFungiblePositionManager.sol

350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

```

[350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350). 

</details>

## [L-06] Zero address check is missing is setter functions

Zero-address checks are a best-practise for input validation of critical address parameters. While the codebase applies this to most addresses in setters, there are many places where this is missing in constructors and setters.

<details>
<summary><i>There are 4 instance of this issue:</i></summary>

```solidity
File: PanopticFactory.sol

134:     function initialize(address _owner) public {

```

[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134). 

```solidity
File: PanopticPool.sol

1833:     function _updateSettlementPostBurn(

```

[1833](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833). 

```solidity
File: SemiFungiblePositionManager.sol

350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

```

[350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350). 

```solidity
File: tokens/ERC1155Minimal.sol

81:     function setApprovalForAll(address operator, bool approved) public {

```

[81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L81). 

</details>

## [L-07] Approve `type(uint256).max` not work with some tokens

Some tokens (e.g. `UNI`, `COMP`) revert if the value passed to approve or transfer is larger than uint96.

Both of the above tokens have special case logic in `approve` that sets `allowance` to `type(uint96).max` if the approval amount is `uint256(-1)`, which may cause issues with systems that expect the value passed to `approve` to be reflected in the `allowances` mapping.

Source: https://github.com/d-xo/weird-erc20#revert-on-large-approvals--transfers

<details>
<summary><i>There are 4 instance of this issue:</i></summary>

```solidity
File: libraries/InteractionHelper.sol

32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```

[32](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L33), [36](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L37). 

</details>

## [L-08] Use `safeApprove` instead of `approve`

The `approve` function in ERC20 tokens is not safe to use. It is possible for an attacker to front-run the transaction and steal the tokens. Use `safeApprove` instead.

<details>
<summary><i>There are 4 instance of this issue:</i></summary>

```solidity
File: libraries/InteractionHelper.sol

32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```

[32](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L33), [36](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L37). 

</details>

## [L-09] `symbol()` is not a part of the ERC-20 standard

The inclusion of the symbol() function in the ERC-20 standard is not mandatory; it was introduced later as an optional extension. Consequently, certain legitimate ERC20 tokens may not provide support for this particular interface. Therefore, it is risky to indiscriminately assume that all tokens conform to this interface and proceed to invoke the symbol() function.

<details>
<summary><i>There are 6 instance of this issue:</i></summary>

```solidity
File: libraries/InteractionHelper.sol

60:         try IERC20Metadata(token0).symbol() returns (string memory _symbol) {
61:             symbol0 = _symbol;
62:         } catch {

60:         try IERC20Metadata(token0).symbol() returns (string memory _symbol) {

65:         try IERC20Metadata(token1).symbol() returns (string memory _symbol) {
66:             symbol1 = _symbol;
67:         } catch {

65:         try IERC20Metadata(token1).symbol() returns (string memory _symbol) {

97:         try IERC20Metadata(token).symbol() returns (string memory tokenSymbol) {
98:             return string.concat(prefix, tokenSymbol);
99:         } catch {

97:         try IERC20Metadata(token).symbol() returns (string memory tokenSymbol) {

```

[60](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L60-L62), [60](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L60), [65](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L65-L67), [65](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L65), [97](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L97-L99), [97](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L97). 

</details>

## [L-10] `decimals()` is not a part of the ERC-20 standard

The inclusion of the decimals() function in the ERC-20 standard is not mandatory; it was introduced later as an optional extension. Consequently, certain legitimate ERC20 tokens may not provide support for this particular interface. Therefore, it is risky to indiscriminately assume that all tokens conform to this interface and proceed to invoke the decimals() function.

<details>
<summary><i>There are 2 instance of this issue:</i></summary>

```solidity
File: libraries/InteractionHelper.sol

110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {
111:             return _decimals;
112:         } catch {

110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {

```

[110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L110-L112), [110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L110). 

</details>

## [N-01] Modifier name should be in mixedCase

<details>
<summary><i>There is 1 instance of this issue:</i></summary>

```solidity
File: SemiFungiblePositionManager.sol

305:     modifier ReentrancyLock(uint64 poolId) {

```

[305](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L305). 

</details>

## [N-02] It is standard for all external and public functions to be overridden from an interface

Check that all public or external functions are override. This is iseful to make sure that the whole API is extracted in an interface.

<details>
<summary><i>There are 63 instance of this issue:</i></summary>

```solidity
File: SemiFungiblePositionManager.sol

350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

402:     function uniswapV3MintCallback(

435:     function uniswapV3SwapCallback(

471:     function burnTokenizedPosition(

504:     function mintTokenizedPosition(

1421:     function getAccountLiquidity(

1449:     function getAccountPremium(

1535:     function getAccountFeesBase(

1555:     function getUniswapV3PoolFromId(

1566:     function getPoolId(address univ3pool) external view returns (uint64 poolId) {

```

[350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350), [402](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L402), [435](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L435), [471](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L471), [504](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L504), [1421](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1421), [1449](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1449), [1535](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1535), [1555](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1555), [1566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1566). 

```solidity
File: CollateralTracker.sol

221:     function startToken(

277:     function getPoolData()

289:     function name() external view returns (string memory) {

303:     function symbol() external view returns (string memory) {

310:     function decimals() external view returns (uint8) {

361:     function asset() external view returns (address assetTokenAddress) {

370:     function totalAssets() public view returns (uint256 totalManagedAssets) {

379:     function convertToShares(uint256 assets) public view returns (uint256 shares) {

386:     function convertToAssets(uint256 shares) public view returns (uint256 assets) {

392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

399:     function previewDeposit(uint256 assets) public view returns (uint256 shares) {

417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {

444:     function maxMint(address) external view returns (uint256 maxShares) {

453:     function previewMint(uint256 shares) public view returns (uint256 assets) {

477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {

507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

518:     function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

531:     function withdraw(

572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {

581:     function previewRedeem(uint256 shares) public view returns (uint256 assets) {

591:     function redeem(

650:     function exerciseCost(

864:     function delegate(

894:     function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

903:     function refund(address delegatee, uint256 assets) external onlyPanopticPool {

911:     function revoke(

975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

995:     function takeCommissionAddData(

1043:     function exercise(

1141:     function getAccountMarginDetails(

```

[221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221), [277](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L277), [289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L310), [361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L370), [379](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L392), [399](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L399), [417](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L417), [444](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444), [453](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L453), [477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L477), [507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L507), [518](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L518), [531](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L531), [572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L581), [591](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L591), [650](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L650), [864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L864), [894](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L894), [903](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L903), [911](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L911), [975](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L975), [995](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L995), [1043](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043), [1141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1141). 

```solidity
File: PanopticPool.sol

291:     function startPool(

338:     function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {

352:     function optionPositionBalance(

381:     function calculateAccumulatedFeesBatch(

410:     function calculatePortfolioValue(

522:     function pokeMedian() external {

547:     function mintOptions(

569:     function burnOptions(

586:     function burnOptions(

1017:     function liquidate(

1179:     function forceExercise(

1425:     function univ3pool() external view returns (IUniswapV3Pool) {

1431:     function collateralToken0() external view returns (CollateralTracker collateralToken) {

1437:     function collateralToken1() external view returns (CollateralTracker) {

1444:     function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

1587:     function settleLongPremium(

```

[291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291), [338](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L338), [352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L352), [381](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L381), [410](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L410), [522](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L522), [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L547), [569](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L569), [586](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L586), [1017](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017), [1179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1179), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1425), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1437), [1444](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1444), [1587](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587). 

```solidity
File: PanopticFactory.sol

134:     function initialize(address _owner) public {

147:     function transferOwnership(address newOwner) external {

159:     function owner() external view returns (address) {

172:     function uniswapV3MintCallback(

210:     function deployNewPool(

290:     function minePoolAddress(

420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {

```

[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134), [147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147), [159](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L159), [172](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L172), [210](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210), [290](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L290), [420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L420). 

</details>

## [N-03] Function must not be longer than 50 lines

<details>
<summary><i>There are 33 instance of this issue:</i></summary>

```solidity
File: SemiFungiblePositionManager.sol

593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

756:     function swapInAMM(

863:     function _createPositionInAMM(

958:     function _createLegInAMM(

1255:     function _collectAndWritePositionData(

1321:     function _getPremiaDeltas(

1449:     function getAccountPremium(

```

[593](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593), [756](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L756), [863](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L863), [958](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L958), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255), [1321](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1321), [1449](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1449). 

```solidity
File: CollateralTracker.sol

650:     function exerciseCost(

911:     function revoke(

1311:     function _getRequiredCollateralSingleLegNoPartner(

1510:     function _computeSpread(

```

[650](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L650), [911](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L911), [1311](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1311), [1510](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1510). 

```solidity
File: PanopticPool.sol

429:     function _calculateAccumulatedPremia(

614:     function _mintOptions(

887:     function _validateSolvency(

1017:     function liquidate(

1179:     function forceExercise(

1503:     function _getPremia(

1587:     function settleLongPremium(

1666:     function _updateSettlementPostMint(

1833:     function _updateSettlementPostBurn(

```

[429](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L429), [614](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L614), [887](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L887), [1017](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017), [1179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1179), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1503), [1587](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587), [1666](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1666), [1833](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833). 

```solidity
File: PanopticFactory.sol

210:     function deployNewPool(

335:     function _mintFullRange(

```

[210](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210), [335](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L335). 

```solidity
File: libraries/PanopticMath.sol

168:     function computeInternalMedian(

651:     function getLiquidationBonus(

768:     function haircutPremia(

```

[168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L168), [651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L651), [768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768). 

```solidity
File: libraries/Math.sol

128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {

340:     function mulDiv(

458:     function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521:     function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

598:     function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

675:     function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

```

[128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L128), [340](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L340), [458](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L521), [598](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L598), [675](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L675). 

```solidity
File: libraries/FeesCalc.sol

130:     function _getAMMSwapFeesPerLiquidityCollected(

```

[130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L130). 

```solidity
File: types/TokenId.sol

500:     function validate(TokenId self) internal pure {

```

[500](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L500). 

</details>

## [N-04] Function parameter name must be in mixedCase

<details>
<summary><i>There are 3 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

185:         uint256 _ITMSpreadMultiplier

```

[185](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L185). 

```solidity
File: PanopticFactory.sol

116:         address _WETH9,

117:         SemiFungiblePositionManager _SFPM,

```

[116](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L116), [117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L117). 

</details>

## [N-05] Cyclomatic complexity of the function is too high

Consider dividing this function into smaller ones.

<details>
<summary><i>There are 3 instance of this issue:</i></summary>

```solidity
File: libraries/PanopticMath.sol

768:     function haircutPremia(

```

[768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768). 

```solidity
File: libraries/Math.sol

128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {

```

[128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L128). 

```solidity
File: types/TokenId.sol

500:     function validate(TokenId self) internal pure {

```

[500](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L500). 

</details>

## [N-06] Lines are too long

The solidity style guide [recommends](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#maximum-line-length) a maximumum line length of 120 characters, so the lines below should be split when they reach that length.ODO

<details>
<summary><i>There are 407 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

25: /// This is represented as an ERC20 share token. A Panoptic pool has 2 tokens, each issued by its own instance of a CollateralTracker.

28: /// @notice This contract uses the ERC4626 standard allowing the minting and burning of "shares" (represented using ERC20 inheritance) in exchange for underlying "assets".

88:     /// @dev Whether this is token0 or token1 depends on which collateral token is being tracked in this CollateralTracker instance.

92:     /// @dev As each instance is deployed via proxy clone, initial parameters must only be initalized once via startToken().

111:     /// @dev Cached amount of assets accounted to be held by the Panoptic Pool — ignores donations, pending fee payouts, and other untracked balance changes.

135:     /// We believe that this will eliminate the impact of the commission fee on the user's decision-making process when closing a position.

195:         // calculate amount of ticks required for upwards and downwards moves, used to check if current and mini-median tick

199:             /// since we're dropping the higher order terms, which are all negative, this will underestimate the number of ticks for a 20% move

213:     /// @notice Initialize a new collateral tracker for a specific token corresponding to the Panoptic Pool being created by the factory that called it.

214:     /// @dev The factory calls this function to start a new collateral tracking system for the incoming token at 'underlyingToken'.

215:     /// The factory will do this for each of the two tokens being tracked. Thus, the collateral tracking system does not track *both* tokens at once.

257:         // store whether the current collateral token is token0 (true) or token1 (false; since there's always exactly two tokens it could be)

272:     /// @return poolAssets cached amount of assets accounted to be held by the Panoptic Pool - ignores donations, pending fee payouts, and other untracked balance changes.

274:     /// @return currentPoolUtilization Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),

276:     /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.

290:         // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size

304:         // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size

311:         // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size

400:         // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid

410:     /// @notice Deposit underlying tokens (assets) to the Panoptic pool from the LP and mint corresponding amount of shares.

456:         // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid

635:     /// - The cost must be larger when the position is close to being in-range, and should be minimal when it is far from being in range. eg. Exercising a (1000, 1050)

637:     /// - The cost is an exponentially decaying function of the distance between the position's strike and the current price

706:                 // note: the delta for one token will be positive and the other will be negative. This cancels out any moves in their positions

723:             // note: we HAVE to start with a negative number as the base exercise cost because when shifting a negative number right by n bits,

725:             // this divergence is observed when n (the number of half ranges) is > 10 (ensuring the floor is not zero, but -1 = 1bps at that point)

727:             int256 fee = (FORCE_EXERCISE_COST >> (maxNumRangesFromStrike - 1)); // exponential decay of fee based on number of half ranges away from the price

736:     /// @notice Get the pool utilization; it is a measure of the ratio of assets in the AMM vs the total assets managed by the pool.

747:     /// @notice Get the (sell) collateral ratio that is paid when a short option is minted at a specific pool utilization.

774:         /// if utilization is less than zero, this is the calculation for a strangle, which gets 2x the capital efficiency at low pool utilization

789:         // this means all new positions are fully collateralized, which reduces risks of insolvency at high pool utilization

814:         // aka the buy ratio starts high and drops to a lower value with increased utilization; the sell ratio does the opposite (slope is positive)

820:         // this denotes a situation where the median is too far away from the current price, so we need to require fully collateralized positions for safety

851:                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

946:             // T: transferred shares from liquidatee which are a component of N but do not contribute toward protocol loss

974:     /// @param assets The amount of assets to refund. Positive means a transfer from refunder to refundee, vice versa for negative.

993:     /// @param swappedAmount The amount of tokens swapped during creation of the option position (non-zero for options minted ITM).

1005:             // constrict premium to only assets not belonging to PLPs (i.e premium paid by sellers or collected from the pool earlier)

1025:             // the inflow or outflow of pool assets is defined by the swappedAmount: it includes both the ITM swap amounts and the short/long amounts used to create the position

1026:             // however, any intrinsic value is paid for by the users, so we only add the portion that comes from PLPs: the short/long amounts

1095:     /// @return exchangedAmount The amount of funds to be exchanged for minting an option (includes commission, swapFee, and intrinsic value).

1137:     /// @param positionBalanceArray The list of all historical positions held by the 'optionOwner', stored as [[tokenId, balance/poolUtilizationAtMint], ...].

1155:     /// @param positionBalanceArray the list of all historical positions held by the 'optionOwner', stored as [[tokenId, balance/poolUtilizationAtMint], ...].

1172:             // If premium is negative (ie. user has to pay for their purchased options), add this long premium to the token requirement

1180:         // if premium is positive (ie. user will receive funds due to selling options), add this premum to the user's balance

1195:     /// @notice Get the total required amount of collateral tokens of a user/account across all active positions to stay above the margin requirement.

1196:     /// @dev Returns the token amounts required for the entire account with active positions in 'positionIdList' (list of tokenIds).

1198:     /// @param positionBalanceArray The list of all historical positions held by the 'optionOwner', stored as [[tokenId, balance/poolUtilizationAtMint], ...].

1199:     /// @return tokenRequired The amount of tokens required to stay above the margin threshold for all active positions of user.

1238:     /// @notice Get the required amount of collateral tokens corresponding to a specific single position 'tokenId' at a price 'tick'.

1239:     /// The required collateral of an account depends on the price ('tick') in the AMM pool: if in the position's favor less collateral needed, etc.

1270:     /// @notice Calculate the required amount of collateral for a single leg 'index' of position 'tokenId' when the leg does not have a risk partner.

1303:     /// @notice Calculate the required amount of collateral for leg 'index' of position 'tokenId' when the leg does not have a risk partner.

1309:     /// @param poolUtilization The pool utilization: ratio of how much funds are in the Panoptic pool versus the AMM pool.

1356:                     // (- and * 2 in tick space are / and ^ 2 in price space so sqrtRatioAtTick(2 *(a - b)) = a/b (*2^96)

1370:                     // compute the collateral requirement depending on whether the position is ITM & out-of-range or ITM and in-range:

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1403:                         // position is in-range (ie. current tick is between upper+lower tick): we draw a line between the

1404:                         // collateral requirement at the lowerTick and the one at the upperTick. We use that interpolation as

1405:                         // the collateral requirement when in-range, which always over-estimates the amount of token required

1407:                         //  required = amountMoved * (scaleFactor - ratio) / (scaleFactor + 1) + sellCollateralRatio*amountMoved

1416:                         // position is in-the-money, collateral requirement = amountMoved*(1-SRC)*(scaleFactor-ratio)/(scaleFactor+1) + SCR*amountMoved

1424:     /// @notice Calculate the required amount of collateral for leg 'index' for position 'tokenId' accounting for its partner leg.

1425:     /// @notice If the two token long-types are different (one is a long, the other a short, e.g.) but the tokenTypes are the same, this is a spread

1427:     /// @notice If the two token long-types are the same but the tokenTypes are different (one is a call, the other a put, e.g.), this is a strangle -

1430:     ///   1) The difference in notional value at both strikes: abs(strikeLong - strikeShort) or abs(strikeShort - strikeLong)

1432:     /// @dev If a position is a strangle, only one leg can be tested at a time which allows us to increase the capital efficiency.

1438:     /// @return required the required amount collateral needed for this leg 'index', accounting for what the leg's risk partner is.

1467:     /// @notice For a given incoming 'amount' - which is the size of a user position (e.g. opening a position), what is the corresponding required collateral to have.

1468:     /// @dev NOTE this does not depend on the price of the AMM pool. This only computes what is needed in response to the current utilization.

1568:                 // the required amount is the amount of contracts multiplied by (notional1 - notional2)/min(notional1, notional2)

1593:     /// @dev A strangle can only have only one of its leg tested at the same time, so this reduces the total risk and collateral requirement.

```

[25](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L25), [28](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L28), [88](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L88), [92](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L92), [111](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L111), [135](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L135), [195](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L195), [199](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L199), [213](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L213), [214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L214), [215](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L215), [257](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L257), [272](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L272), [274](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L274), [276](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L276), [290](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L290), [304](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L304), [311](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L311), [400](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L400), [410](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L410), [456](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L456), [635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L635), [637](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L637), [706](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L706), [723](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L723), [725](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L725), [727](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L727), [736](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L736), [747](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L747), [774](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L774), [789](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L789), [814](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L814), [820](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L820), [851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L851), [946](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L946), [974](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L974), [993](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L993), [1005](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1005), [1025](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1025), [1026](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1026), [1095](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1095), [1137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1137), [1155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1155), [1172](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1172), [1180](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1180), [1195](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1195), [1196](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1196), [1198](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1198), [1199](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1199), [1238](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1238), [1239](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1239), [1270](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1270), [1303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1303), [1309](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1309), [1356](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1356), [1370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1370), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1374), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1375), [1403](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1403), [1404](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1404), [1405](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1405), [1407](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1407), [1416](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1416), [1424](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1424), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1425), [1427](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1427), [1430](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1430), [1432](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1432), [1438](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1438), [1467](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1467), [1468](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1468), [1568](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1568), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1593). 

```solidity
File: PanopticFactory.sol

101:     /// @notice Mapping from address(UniswapV3Pool) to address(PanopticPool) that stores the address of all deployed Panoptic Pools

201:     /// @notice Create a new Panoptic Pool linked to the given Uniswap pool identified uniquely by the incoming parameters.

256:         // If this is not the case, we increase the next cardinality during deployment so the cardinality can catch up over time

285:     /// @param salt Salt value ([160-bit deployer address][96-bit nonce]) to start from, useful as a checkpoint across multiple calls

287:     /// @param minTargetRarity The minimum target rarity to mine for. The internal loop stops when this is reached *or* when no more iterations

347:         // In this case, the `fullRangeLiquidity` will always be an underestimate in respect to the token amounts required to mint.

```

[101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L101), [201](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L201), [256](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L256), [285](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L285), [287](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L287), [347](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L347). 

```solidity
File: PanopticPool.sol

36:     /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.

61:     /// @param settledAmounts LeftRight encoding for the amount of premium settled for token0 (right slot) and token1 (left slot).

87:     /// @param poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),

89:     /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.

113:     /// @dev Only include the share of (settled) premium that is available to collect when calling `_calculateAccumulatedPremia`

131:     // This oracle is updated with the last Uniswap observation during `mintOptions` if MEDIAN_PERIOD has elapsed past the last observation

132:     // If true, the "slow" oracle price is instead computed on-the-fly from 7 Uniswap observations (spaced 5 observations apart) irrespective of the frequency of `mintOptions` calls

142:     /// Note that the *minimum* total observation time is determined by the blocktime and may need to be adjusted by chain

144:     /// In this case, if there is an interaction every block, the "fast" oracle can consider 3 consecutive block end prices (min=36 seconds on Ethereum)

151:     /// @dev Structured such that the minimum total observation time is 7 minutes on Ethereum (similar to internal median mode)

154:     // The maximum allowed delta between the currentTick and the Uniswap TWAP tick during a liquidation (~5% down, ~5.26% up)

159:     /// Falls back on the more conservative (less solvent) tick during times of extreme volatility (to ensure the account is always solvent)

170:     // multiplier (x10k) for the collateral requirement in the event of a buying power decrease, such as minting or force exercising

237:     // collected for every chunk per unit of liquidity (net or short, depending on the isLong value of the specific leg index)

241:     /// @dev Per-chunk `last` value that gives the aggregate amount of premium owed to all sellers when multiplied by the total amount of liquidity `totalLiquidity`

253:     /// @dev Tracks the amount of liquidity for a user+tokenId (right slot) and the initial pool utilizations when that position was minted (left slot)

267:     /// The accumulator also tracks the total number of positions (ie. makes sure the length of the provided positionIdList matches);

270:     /// this hash can be cheaply verified on every operation with a user provided positionIdList - and we can use that for operations

278:     /// @notice During construction: sets the address of the panoptic factory smart contract and the SemiFungiblePositionMananger (SFPM).

310:                 // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2

368:         // the 64 most significant bits are the utilization of token1, so we can shift the number to the right by 64 to extract it

377:     /// @param includePendingPremium true = include premium that is owed to the user but has not yet settled, false = only include premium that is available to collect.

380:     /// @return balances A list of balances and pool utilization for each position, of the form [[tokenId0, balances0], [tokenId1, balances1], ...].

425:     /// @param computeAllPremia Whether to compute accumulated premia for all legs held by the user (true), or just owed premia for long legs (false).

426:     /// @param includePendingPremium true = include premium that is owed to the user but has not yet settled, false = only include premium that is available to collect.

427:     /// @return portfolioPremium The computed premia of the user's positions, where premia contains the accumulated premia for token0 in the right slot and for token1 in the left slot.

428:     /// @return balances A list of balances and pool utilization for each position, of the form [[tokenId0, balances0], [tokenId1, balances1], ...].

494:     /// @notice Disable slippage checks if tickLimitLow == tickLimitHigh and reverses ticks if given in correct order to enable ITM swaps

541:     /// @param positionIdList the list of currently held positions by the user, where the newly minted position(token) will be the last element in 'positionIdList'.

543:     /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position.

608:     /// @param positionIdList the list of currently held positions by the user, where the newly minted position(token) will be the last element in 'positionIdList'.

610:     /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position.

660:         // Add an initial buffer to the collateral requirement to prevent users from minting their account close to insolvency

663:         // Update `s_miniMedian` with a new observation if the last observation is old enough (returned medianData is nonzero)

675:     /// @return poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool) at the time of minting,

703:     /// @return poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),

705:     /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.

737:     /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position

881:     /// @notice Falls back to the more conservative tick if the delta between the fast and slow oracle exceeds `MAX_SLOW_FAST_DELTA`.

882:     /// @dev Effectively, this means that the users must be solvent at both the fast and slow oracle ticks if one of them is stale to mint or burn options.

886:     /// @return medianData If nonzero (enough time has passed since last observation), the updated value for `s_miniMedian` with a new observation

942:         // If one of the ticks is too stale, we fall back to the more conservative tick, i.e, the user must be solvent at both the fast and slow oracle ticks.

1012:     /// @dev Will revert if liquidated account is solvent at the TWAP tick or if TWAP tick is too far away from the current tick.

1015:     /// @param delegations LeftRight amounts of token0 and token1 (token0:token1 right:left) delegated to the liquidatee by the liquidator so the option can be smoothly exercised.

1070:         // Works like a transfer, so the liquidator must possess all the tokens they are delegating, resulting in no net supply change

1083:             // Do not commit any settled long premium to storage - we will do this after we determine if any long premium must be revoked

1084:             // This is to prevent any short positions the liquidatee has being settled with tokens that will later be revoked

1112:             // thus, we haircut any premium paid by the liquidatee (converting tokens as necessary) until the protocol loss is covered or the premium is exhausted

1113:             // note that the haircutPremia function also commits the settled amounts (adjusted for the haircut) to storage, so it will be called even if there is no haircut

1115:             // if premium is haircut from a token that is not in protocol loss, some of the liquidation bonus will be converted into that token

1187:         // '_calculateAccumulatedPremia' expects a list of positions to be touched, and this is the only way to pass a single position

1190:         // validate the exercisor's position list (the exercisee's list will be evaluated after their position is force exercised)

1284:     /// @notice check whether an account is solvent at a given `atTick` with a collateral requirement of `buffer`/10_000 multiplied by the requirement of `positionIdList`.

1334:     /// @param tokenData0 Leftright encoded word with balance of token0 in the right slot, and required balance in left slot.

1335:     /// @param tokenData1 Leftright encoded word with balance of token1 in the right slot, and required balance in left slot.

1350:             // the amount of cross-collateral balance needed for the account to be solvent, computed in terms of liquidity

1363:     /// @dev Check whether the list of positionId 1) has duplicates and 2) matches the length stored in the positionsHash.

1366:     /// @param offset Changes depending on whether this is a new mint or a liquidation (=1 if new mint, 0 if liquidation).

1378:         // note that if pLength == 0 even if a user has existing position(s) the below will fail b/c the fingerprints will mismatch

1397:     /// @notice Updates the hash for all positions owned by an account. This fingerprints the list of all incoming options with a single hash.

1400:     /// @dev The positions hash is stored as the XOR of the keccak256 of each tokenId. Updating will XOR the existing hash with the new tokenId.

1401:     /// The same update can either add a new tokenId (when minting an option), or remove an existing one (when burning it) - this happens through the XOR.

1404:     /// @param addFlag Pass addFlag=true when this is adding a position, needed to ensure the number of positions increases or decreases.

1463:     /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position

1491:         // the effective liquidity measures how many times more the newly added liquidity is compared to the existing/base liquidity

1500:     /// @param computeAllPremia Whether to compute accumulated premia for all legs held by the user (true), or just owed premia for long legs (false).

1542:                     // if the premium accumulatorLast is higher than current, it means the premium accumulator has overflowed and rolled over at least once

1544:                     // if there are multiple rollovers or the rollover goes past the last accumulator, rolled over fees will just remain unclaimed

1582:     /// @dev Called by sellers on buyers of their chunk to increase the available premium for withdrawal (before closing their position).

1584:     /// @param positionIdList Exhaustive list of open positions for the `owners` used for solvency checks where the tokenId to be settled is the last element.

1638:             // deduct the paid premium tokens from the owner's balance and add them to the cumulative settled token delta

1649:             // commit the delta in settled tokens (all of the premium paid by long chunks in the tokenIds list) to storage

1657:         // ensure the owner is solvent (insolvent accounts are not permitted to pay premium unless they are being liquidated)

1676:             // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers

1690:                 // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64

1753:     /// @param grossPremiumLast The `last` values used with `premiumAccumulators` to compute the total premium owed to sellers

```

[36](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L36), [61](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L61), [87](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L87), [89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L89), [113](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L113), [131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L131), [132](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L132), [142](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L142), [144](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L144), [151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L151), [154](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L154), [159](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L159), [170](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L170), [237](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L237), [241](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L241), [253](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L253), [267](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L267), [270](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L270), [278](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L278), [310](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L310), [368](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L368), [377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L377), [380](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L380), [425](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L425), [426](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L426), [427](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L427), [428](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L428), [494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L494), [541](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L541), [543](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L543), [608](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L608), [610](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L610), [660](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L660), [663](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L663), [675](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L675), [703](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L703), [705](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L705), [737](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L737), [881](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L881), [882](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L882), [886](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L886), [942](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L942), [1012](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1012), [1015](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1015), [1070](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1070), [1083](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1083), [1084](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1084), [1112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1112), [1113](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1113), [1115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1115), [1187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1187), [1190](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1190), [1284](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1284), [1334](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1334), [1335](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1335), [1350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1350), [1363](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1363), [1366](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1366), [1378](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1378), [1397](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1397), [1400](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1400), [1401](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1401), [1404](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1404), [1463](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1463), [1491](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1491), [1500](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1500), [1542](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1542), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1544), [1582](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1582), [1584](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1584), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1638), [1649](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1649), [1657](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1657), [1676](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1676), [1690](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1690), [1753](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1753). 

```solidity
File: SemiFungiblePositionManager.sol

24: //                       ,.                                   .,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.                                    ,,

25: //                    ,,,,,,,                           ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                            ,,,,,,

26: //                  .,,,,,,,,,,.                   ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                     ,,,,,,,,,,,

27: //                .,,,,,,,,,,,,,,,             ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.              ,,,,,,,,,,,,,,,

28: //               ,,,,,,,,,,,,,,.            ,,,,,,,,,,,,,,,,,,,,,,,,,,,                ,,,,,,,,,,,,,,,,,,,,,,,,,,.             ,,,,,,,,,,,,,,,

29: //             ,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,,,,,,                                ,,,,,,,,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,,

30: //            ,,,,,,,,,,,,,.           ,,,,,,,,,,,,,,,,,,                                           .,,,,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,

31: //          ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,,,.                                                  ,,,,,,,,,,,,,,,,,           .,,,,,,,,,,,,,

32: //         ,,,,,,,,,,,,,.         .,,,,,,,,,,,,,,,.                                                        ,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,.

33: //        ,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,                                                              ,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

34: //       ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,.                                                                  ,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

35: //      ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,                                                                      ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,

36: //     ,,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                         ,,,,,,,,,,,,,,          ,,,,,,,,,,,,.

37: //    .,,,,,,,,,,,,        .,,,,,,,,,,,,,                                                                            ,,,,,,,,,,,,,          ,,,,,,,,,,,,

38: //    ,,,,,,,,,,,,         ,,,,,,,,,,,,                                                                               ,,,,,,,,,,,,,         .,,,,,,,,,,,,

39: //   ,,,,,,,,,,,,         ,,,,,,,,,,,,                                                                                 ,,,,,,,,,,,,.         ,,,,,,,,,,,,

40: //   ,,,,,,,,,,,,        ,,,,,,,,,,,,.                █████████  ███████████ ███████████  ██████   ██████               ,,,,,,,,,,,,          ,,,,,,,,,,,,

41: //  .,,,,,,,,,,,,        ,,,,,,,,,,,,                ███░░░░░███░░███░░░░░░█░░███░░░░░███░░██████ ██████                .,,,,,,,,,,,,         ,,,,,,,,,,,,

42: //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░███    ░░░  ░███   █ ░  ░███    ░███ ░███░█████░███                 ,,,,,,,,,,,,         ,,,,,,,,,,,,.

43: //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░░█████████  ░███████    ░██████████  ░███░░███ ░███                 .,,,,,,,,,,,          ,,,,,,,,,,,.

44: //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ░░░░░░░░███ ░███░░░█    ░███░░░░░░   ░███ ░░░  ░███                  ,,,,,,,,,,,.         ,,,,,,,,,,,,

45: //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ███    ░███ ░███  ░     ░███         ░███      ░███                  ,,,,,,,,,,,,         ,,,,,,,,,,,,

46: //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░░█████████  █████       █████        █████     █████                 ,,,,,,,,,,,          ,,,,,,,,,,,,

47: //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ░░░░░░░░░  ░░░░░       ░░░░░        ░░░░░     ░░░░░                 ,,,,,,,,,,,,          ,,,,,,,,,,,.

48: //  ,,,,,,,,,,,,        .,,,,,,,,,,,.                                                                                    ,,,,,,,,,,,,         ,,,,,,,,,,,,

49: //  .,,,,,,,,,,,,        ,,,,,,,,,,,,                                                                                   .,,,,,,,,,,,,         ,,,,,,,,,,,,

50: //   ,,,,,,,,,,,,        ,,,,,,,,,,,,,                                                                                  ,,,,,,,,,,,,          ,,,,,,,,,,,,

51: //   ,,,,,,,,,,,,.        ,,,,,,,,,,,,.                                                                                ,,,,,,,,,,,,.         ,,,,,,,,,,,,

52: //    ,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                              ,,,,,,,,,,,,,         .,,,,,,,,,,,,

53: //     ,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                            ,,,,,,,,,,,,,         .,,,,,,,,,,,,

54: //     .,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                         ,,,,,,,,,,,,,.          ,,,,,,,,,,,,

55: //      ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,                                                                     .,,,,,,,,,,,,,.          ,,,,,,,,,,,,

56: //       ,,,,,,,,,,,,,         .,,,,,,,,,,,,,,                                                                 .,,,,,,,,,,,,,,          .,,,,,,,,,,,,

57: //        ,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,                                                             ,,,,,,,,,,,,,,,.          ,,,,,,,,,,,,,.

58: //         ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,,                                                       .,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

59: //          .,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,                                                 .,,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,

60: //            ,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,,,.                                        ,,,,,,,,,,,,,,,,,,,.            ,,,,,,,,,,,,,,

61: //             ,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,,,,,,,,,                             .,,,,,,,,,,,,,,,,,,,,,,             ,,,,,,,,,,,,,,

62: //               ,,,,,,,,,,,,,,,            .,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.        ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,             .,,,,,,,,,,,,,,.

63: //                 ,,,,,,,,,,,,,,.              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,               ,,,,,,,,,,,,,,,

64: //                   ,,,,,,,,,,                     ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                     .,,,,,,,,,,

65: //                     ,,,,,.                            ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                             ,,,,,,

129:     // Similar to vega in options because the liquidity utilization is somewhat reflective of the implied volatility (IV),

132:     // The effect of vegoid on the long premium multiplier can be explored here: https://www.desmos.com/calculator/mdeqob2m04

173:     /// @dev mapping that stores the liquidity data of keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))

174:     // liquidityData is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user

175:     // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller

176:     // the reason why it is called "removedLiquidity" is because long options are created by removed liquidity -ie. short selling LP positions

219:         For an arbitrary parameter 0 <= ν <= 1 (ν = 1/2^VEGOID). This way, the gross_feesCollectedX128 will be given by:

291:     /// @dev mapping that stores a LeftRight packing of feesBase of  keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))

292:     /// @dev Base fees is stored as int128((feeGrowthInside0LastX128 * liquidity) / 2**128), which allows us to store the accumulated fees as int128 instead of uint256

294:     /// feesBase represents the baseline fees collected by the position last time it was updated - this is recalculated every time the position is collected from with the new value

378:         // note: we preserve the state of `locked` to prevent reentering a pool by initializing it during the reentrant call

467:     /// @param slippageTickLimitLow The lower price slippage limit when minting an ITM position (set to larger than slippageTickLimitHigh for swapping when minting)

468:     /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)

469:     /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

470:     /// @return totalSwapped A LeftRight encoded word containing the total amount of token0 and token1 swapped if minting ITM

500:     /// @param slippageTickLimitLow The lower price slippage limit when minting an ITM position (set to larger than slippageTickLimitHigh for swapping when minting)

501:     /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)

502:     /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

503:     /// @return totalSwapped A LeftRight encoded word containing the total amount of token0 and token1 swapped if minting ITM

547:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call

554:         // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)

573:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call

588:     /// @dev token transfers are only allowed if you transfer your entire liquidity of a given chunk and the recipient has none

602:             // for this leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick

659:     /// @notice Helper that checks the proposed option position and size and forwards the minting and potential swapping tasks.

664:     /// @notice and then forwards the minting/burning/swapping to another internal helper functions which perform the AMM pool actions.

678:     /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

716:             // if the in-the-money amount is not zero (i.e. positions were minted ITM) and the user did provide tick limits LOW > HIGH, then swap necessary amounts

731:     /// @notice When a position is minted or burnt in-the-money (ITM) we are *not* 100% token0 or 100% token1: we have a mix of both tokens.

732:     /// @notice The swapping for ITM options is needed because only one of the tokens are "borrowed" by a user to create the position.

750:     ///   If we take token0 as an example, we deploy it to the AMM pool and *then* swap to get the right mix of token0 and token1

752:     ///   It that position is burnt, then we remove a mix of the two tokens and swap one of them so that the user receives only one.

784:             // note: upstream users of this function such as the Panoptic Pool should ensure users always compensate for the ITM amount delta

785:             // the netting swap is not perfectly accurate, and it is possible for swaps to run out of liquidity, so we do not want to rely on it

791:                 // note: negative ITM amounts denote a surplus of tokens (burning liquidity), while positive amounts denote a shortage of tokens (minting liquidity)

793:                 // we do this by flipping the signs on the token1 ITM amount converting+deducting it against the token0 ITM amount

861:     /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

897:                     // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,

902:                 // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick

921:                     // increment accumulators of the upper bound on tokens contained across all legs of the position at any given tick

936:         // Ensure upper bound on amount of tokens contained across all legs of the position on any given tick does not exceed a maximum of (2**127-1).

937:         // This is the maximum value of the `int128` type we frequently use to hold token amounts, so a given position's size should be guaranteed to

992:             // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user

993:             // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller

994:             // the reason why it is called "removedLiquidity" is because long options are created by removing -ie.short selling LP positions

1001:                 // we're minting more liquidity in uniswap: so add the incoming liquidity chunk to the existing liquidity chunk

1011:                 // so we seek to move the incoming liquidity chunk *out* of uniswap - but was there sufficient liquidity sitting in uniswap

1121:         // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)

1122:         // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing

1132:     /// @notice Compute the feesGrowth * liquidity / 2**128 by reading feeGrowthInside0LastX128 and feeGrowthInside1LastX128 from univ3pool.positions.

1137:     /// @dev stored fees base is rounded up and the current fees base is rounded down to minimize the amount of fees collected (Δfeesbase) in favor of the protocol

1160:         /// @dev here we're converting the value to an int128 even though all values (feeGrowth, liquidity, Q128) are strictly positive.

1161:         /// That's because of the way feeGrowthInside works in Uniswap v3, where it can underflow when stored for the first time.

1162:         /// This is not a problem in Uniswap v3 because the fees are always calculated by taking the difference of the feeGrowths,

1164:         /// So by using int128 instead of uint128, we remove the need to handle extremely large underflows and simply allow it to be negative

1219:     /// @notice Burn a chunk of liquidity (`liquidityChunk`) in the Uniswap v3 pool and send to msg.sender; return the amount moved.

1247:     /// @notice Helper to collect amounts between msg.sender and Uniswap and also to update the Uniswap fees collected to date from the AMM.

1250:     /// @param currentLiquidity the existing liquidity msg.sender owns in the AMM for this chunk before the SFPM was called

1254:     /// @return collectedChunk the incoming amount collected with potentially whatever is collected in this function added to it

1281:             // Collect only if there was existing startingLiquidity=liquidities.rightSlot() at that position: collect all fees

1319:     /// @return deltaPremiumOwed The extra premium (per liquidity X64) to be added to the owed accumulator for token0 (right) and token1 (left)

1320:     /// @return deltaPremiumGross The extra premium (per liquidity X64) to be added to the gross accumulator for token0 (right) and token1 (left)

1334:         // explains how we get from the premium per liquidity (calculated here) to the total premia collected and the multiplier

1420:     /// @return accountLiquidities The amount of liquidity that has been shorted/added to the Uniswap contract (netLiquidity:removedLiquidity -> rightSlot:leftSlot)

1429:         /// @dev tokenType input here is the asset of the positions minted, this avoids put liquidity to be used for call, and vice-versa

1435:     /// @notice Return the premium associated with a given position, where Premium is an accumulator of feeGrowth for the touched position.

1436:     /// @dev Computes s_accountPremium{isLong ? Owed : Gross}[keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))]

1437:     /// @dev if an atTick parameter is provided that is different from type(int24).max, then it will update the premium up to the current

1438:     /// @dev block at the provided atTick value. We do this because this may be called immediately after the Uni v3 pool has been touched

1445:     /// @param atTick The current tick. Set atTick < type(int24).max = 8388608 to get latest premium up to the current block

1447:     /// @return premiumToken0 The amount of premium (per liquidity X64) for token0 = sum (feeGrowthLast0X128) over every block where the position has been touched

1448:     /// @return premiumToken1 The amount of premium (per liquidity X64) for token1 = sum (feeGrowthLast0X128) over every block where the position has been touched

1464:         // Compute the premium up to the current block (ie. after last touch until now). Do not proceed if atTick == type(int24).max = 8388608

1476:                     // how much fees have been accumulated within the liquidity chunk since last time we updated this chunk?

1478:                     // currentFeesGrowth (calculated from FeesCalc.calculateAMMSwapFeesLiquidityChunk) is (ammFeesCollectedPerLiquidity * liquidityChunk.liquidity())

1479:                     // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])

1488:                     // If the current feesBase is close or identical to the stored one, the amountToCollect can be negative.

1505:                 // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)

1506:                 // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing

```

[24](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L24), [25](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L25), [26](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L26), [27](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L27), [28](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L28), [29](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L29), [30](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L30), [31](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L31), [32](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L34), [35](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L35), [36](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L38), [39](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L39), [40](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L40), [41](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L41), [42](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L42), [43](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L43), [44](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L44), [45](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L45), [46](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L46), [47](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L47), [48](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L48), [49](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L49), [50](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L50), [51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L51), [52](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L52), [53](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L53), [54](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L54), [55](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L55), [56](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L56), [57](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L57), [58](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L58), [59](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L59), [60](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L60), [61](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L61), [62](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L62), [63](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L63), [64](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L64), [65](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L65), [129](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L129), [132](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L132), [173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L173), [174](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L174), [175](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L175), [176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L176), [219](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L219), [291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L291), [292](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L292), [294](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L294), [378](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L378), [467](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L467), [468](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L468), [469](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L469), [470](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L470), [500](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L500), [501](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L501), [502](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L502), [503](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L503), [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L547), [554](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L554), [573](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L573), [588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L588), [602](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L602), [659](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L659), [664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L664), [678](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L678), [716](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L716), [731](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L731), [732](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L732), [750](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L750), [752](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L752), [784](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L784), [785](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L785), [791](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L791), [793](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L793), [861](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L861), [897](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L897), [902](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L902), [921](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L921), [936](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L936), [937](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L937), [992](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L992), [993](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L993), [994](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L994), [1001](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1001), [1011](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1011), [1121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1121), [1122](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1122), [1132](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1132), [1137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1137), [1160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1160), [1161](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1161), [1162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1162), [1164](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1164), [1219](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1219), [1247](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1247), [1250](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1250), [1254](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1254), [1281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1281), [1319](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1319), [1320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1320), [1334](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1334), [1420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1420), [1429](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1429), [1435](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1435), [1436](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1436), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1437), [1438](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1438), [1445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1445), [1447](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1447), [1448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1448), [1464](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1464), [1476](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1476), [1478](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1478), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1479), [1488](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1488), [1505](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1505), [1506](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1506). 

```solidity
File: libraries/CallbackLib.sol

11: /// @notice This library provides functions to verify that a callback came from a canonical Uniswap V3 pool with a claimed set of features.

35:         // Call getPool on the factory to verify that the sender corresponds to the canonical pool with the claimed features

```

[11](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L11), [35](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L35). 

```solidity
File: libraries/Errors.sol

18:     /// @notice PanopticPool: the effective liquidity (X32) is greater than min(`MAX_SPREAD`, `USER_PROVIDED_THRESHOLD`) during a long mint or short burn

22:     /// @notice CollateralTracker: attempted to withdraw/redeem more than available liquidity, owned shares, or open positions would allow for

25:     /// @notice PanopticPool: force exercisee is insolvent - liquidatable accounts are not permitted to open or close positions outside of a liquidation

41:     /// @param parameterType poolId=0, ratio=1, tokenType=2, risk_partner=3 , strike=4, width=5, two identical strike/width/tokenType chunks=6

44:     /// @notice A mint or swap callback was attempted from an address that did not match the canonical Uniswap V3 pool with the claimed features

50:     /// @notice PanopticPool: one of the legs in a position are force-exercisable (they are all either short or ITM long)

```

[18](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L18), [22](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L22), [25](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L25), [41](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L41), [44](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L44), [50](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L50). 

```solidity
File: libraries/FeesCalc.sol

17: /// @dev Some options positions involve moving liquidity chunks to the AMM/Uniswap. Those chunks can then earn AMM swap fees.

96:     /// @return The fees collected from the AMM for each token (LeftRight-packed) with token0 in the right slot and token1 in the left slot

137:         // lowerOut0: For token0: fee growth per unit of liquidity on the _other_ side of tickLower (relative to currentTick)

```

[17](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L17), [96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L96), [137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L137). 

```solidity
File: libraries/InteractionHelper.sol

18:     /// @notice Function that performs approvals on behalf of the PanopticPool for CollateralTracker and SemiFungiblePositionManager.

40:     /// @notice Computes the name of a CollateralTracker based on the token composition and fee of the underlying Uniswap Pool.

41:     /// @dev Some tokens do not have proper symbols so error handling is required - this logic takes up significant bytecode size, which is why it is in a library.

```

[18](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L18), [40](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L40), [41](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L41). 

```solidity
File: libraries/Math.sol

124:     /// @dev Implemented using Uniswap's "incorrect" constants. Supplying commented-out real values for an accurate calculation.

216:     /// @notice Calculates the amount of token0 and token1 received for a given LiquidityChunk at the provided currentTick.

334:     /// @notice Calculates floor(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0.

435:     /// @notice Calculates ceil(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0.

502:             // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

565:             // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

642:             // Divide [prod1 prod0] by the factors of two (note that this is just 2**128 since the denominator is a power of 2 itself)

719:             // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

748:     /// @notice QuickSort is a sorting algorithm that employs the Divide and Conquer strategy. It selects a pivot element and arranges the given array around

```

[124](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L124), [216](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L216), [334](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L334), [435](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L435), [502](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L502), [565](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L565), [642](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L642), [719](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L719), [748](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L748). 

```solidity
File: libraries/PanopticMath.sol

34:     ///      the 64 bits are the 48 *last* (most significant) bits - and thus corresponds to the *first* 12 hex characters (reading left to right)

35:     ///      of the Uniswap v3 pool address, with the tickSpacing written in the highest 16 bits (i.e, max tickSpacing is 32768)

86:     /// @notice The positions hash contains a single fingerprint of all positions created by an account/user as well as a tally of the positions.

88:     /// @param existingHash The existing position hash containing all historical N positions created and the count of the positions

89:     /// @param tokenId The new position to add to the existing hash: existingHash = uint248(existingHash) ^ hashOf(tokenId)

90:     /// @param addFlag Whether to mint (add) the tokenId to the count of positions or burn (subtract) it from the count (existingHash >> 248) +/- 1

114:     /// @dev Uniswap observations snapshot the closing price of the last block before the first interaction of a given block.

115:     /// @dev The maximum frequency of observations is 1 per block, but there is no guarantee that the pool will be observed at every block.

116:     /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.

117:     /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).

136:             // get the last 4 timestamps/tickCumulatives (if observationIndex < cardinality, the index will wrap back from observationCardinality)

147:             // use cardinality periods given by cardinality + 1 accumulator observations to compute the last cardinality observed ticks spaced by period

159:     /// @notice Takes a packed structure representing a sorted 7-slot ring buffer of ticks and returns the median of those values.

160:     /// @dev Also inserts the latest Uniswap observation into the buffer, resorts, and returns if the last entry is at least `period` seconds old.

163:     /// @param period The minimum time in seconds that must have passed since the last observation was inserted into the buffer

167:     /// @return updatedMedianData The updated 7-slot ring buffer of ticks with the latest observation inserted if the last entry is at least `period` seconds old (returns 0 otherwise)

237:     /// @dev We instead observe the average price over a series of time intervals, and define the TWAP as the median of those averages.

274:     /// @notice For a given option position (`tokenId`), leg index within that position (`legIndex`), and `positionSize` get the tick range spanned and its

310:         //  Because Uni v3 chooses token0 and token1 from the alphanumeric order, there is no consistency as to whether token0 is

311:         //  stablecoin, ETH, or an ERC20. Some pools may want ETH to be the asset (e.g. ETH-DAI) and some may wish the stablecoin to

315:         //  To solve this, we encode the asset value in tokenId. This parameter specifies which of token0 or token1 is the

344:             // The max/min ticks that can be initialized are the closest multiple of tickSpacing to the actual max/min tick abs()=887272

365:     /// @notice Returns the distances of the upper and lower ticks from the strike for a position with the given width and tickSpacing.

385:     /// @notice Compute the amount of funds that are underlying this option position. This is useful when exercising a position.

388:     /// @return longAmounts Left-right packed word where the right contains the total contract size and the left total notional

389:     /// @return shortAmounts Left-right packed word where the right contains the total contract size and the left total notional

412:     /// @notice Adds required collateral and collateral balance from collateralTracker0 and collateralTracker1 and converts to single values in terms of `tokenType`.

413:     /// @param tokenData0 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token0)

414:     /// @param tokenData1 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token1)

438:     /// @notice Adds required collateral and collateral balance from collateralTracker0 and collateralTracker1 and converts to single values in terms of `tokenType`.

439:     /// @param tokenData0 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token0)

440:     /// @param tokenData1 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token1)

455:     /// @notice Compute the notional amount given an incoming total number of `contracts` deployed between `tickLower` and `tickUpper`.

456:     /// @dev The notional value of an option is the value of the crypto assets that are controlled (rather than the cost of the transaction).

461:     /// @dev Thus, `contracts` refer to "100" in this example. The $20 is the strike price. We get the strike price from `tickLower` and `tickUpper`.

462:     /// @dev From TradFi: [https://www.investopedia.com/terms/n/notionalvalue.asp](https://www.investopedia.com/terms/n/notionalvalue.asp).

485:     /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

502:     /// @notice Convert an amount of token1 into an amount of token0 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

519:     /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

542:     /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

569:     /// @notice Compute the amount of token0 and token1 moved. Given an option position `tokenId`, leg index `legIndex`, and how many contracts are in the leg `positionSize`.

571:     /// @param positionSize The number of option contracts held in this position (each contract can control multiple tokens)

573:     /// @return A LeftRight encoded variable containing the amount0 and the amount1 value controlled by this option position's leg

642:     /// @param tokenData0 Leftright encoded word with balance of token0 in the right slot, and required balance in left slot

643:     /// @param tokenData1 Leftright encoded word with balance of token1 in the right slot, and required balance in left slot

650:     /// @return The LeftRight-packed protocol loss for both tokens, i.e., the delta between the user's balance and expended tokens

692:             // this is already present in the netExchanged amount, so to avoid double-counting we remove it from the balance

701:             // note that "balance0" and "balance1" are the liquidatee's original balances before token delegation by a liquidator

702:             // their actual balances at the time of computation may be higher, but these are a buffer representing the amount of tokens we

707:                     // liquidatee has insufficient token0 but some token1 left over, so we use what they have left to mitigate token0 losses

708:                     // we do this by substituting an equivalent value of token1 in our refund to the liquidator, plus a bonus, for the token0 we convert

709:                     // we want to convert the minimum amount of tokens required to achieve the lowest possible protocol loss (to avoid overpaying on the conversion bonus)

710:                     // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token1 balance: balance1 - paid1

711:                     // and paid0 - balance0 is the amount of token0 that the liquidatee is missing, i.e the protocol loss

712:                     // if the protocol loss is lower than the excess token1 balance, then we can fully mitigate the loss and we should only convert the loss amount

713:                     // if the protocol loss is higher than the excess token1 balance, we can only mitigate part of the loss, so we should convert only the excess token1 balance

725:                     // liquidatee has insufficient token1 but some token0 left over, so we use what they have left to mitigate token1 losses

726:                     // we do this by substituting an equivalent value of token0 in our refund to the liquidator, plus a bonus, for the token1 we convert

727:                     // we want to convert the minimum amount of tokens required to achieve the lowest possible protocol loss (to avoid overpaying on the conversion bonus)

728:                     // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token0 balance: balance0 - paid0

729:                     // and paid1 - balance1 is the amount of token1 that the liquidatee is missing, i.e the protocol loss

730:                     // if the protocol loss is lower than the excess token0 balance, then we can fully mitigate the loss and we should only convert the loss amount

731:                     // if the protocol loss is higher than the excess token0 balance, we can only mitigate part of the loss, so we should convert only the excess token0 balance

756:     /// @notice Haircut/clawback any premium paid by `liquidatee` on `positionIdList` over the protocol loss threshold during a liquidation.

757:     /// @dev Note that the storage mapping provided as the `settledTokens` parameter WILL be modified on the caller by this function.

765:     /// @param settledTokens The per-chunk accumulator of settled tokens in storage from which to subtract the haircut premium

790:             // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token

795:             // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,

796:             // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token

886:                         // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount

910:     /// @notice Returns the original delegated value to a user at a certain tick based on the available collateral from the exercised user.

926:             // if the refunder lacks sufficient token0 to pay back the refundee, have them pay back the equivalent value in token1

927:             // note: it is possible for refunds to be negative when the exercise fee is higher than the delegated amounts. This is expected behavior

```

[34](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L34), [35](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L35), [86](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L86), [88](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L88), [89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L89), [90](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L90), [114](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L114), [115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L115), [116](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L116), [117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L117), [136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L136), [147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L147), [159](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L159), [160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L160), [163](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L163), [167](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L167), [237](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L237), [274](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L274), [310](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L310), [311](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L311), [315](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L315), [344](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L344), [365](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L365), [385](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L385), [388](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L388), [389](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L389), [412](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L412), [413](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L413), [414](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L414), [438](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L438), [439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L439), [440](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L440), [455](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L455), [456](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L456), [461](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L461), [462](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L462), [485](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L485), [502](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L502), [519](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L519), [542](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L542), [569](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L569), [571](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L571), [573](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L573), [642](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L642), [643](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L643), [650](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L650), [692](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L692), [701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L701), [702](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L702), [707](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L707), [708](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L708), [709](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L709), [710](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L710), [711](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L711), [712](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L712), [713](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L713), [725](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L725), [726](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L726), [727](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L727), [728](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L728), [729](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L729), [730](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L730), [731](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L731), [756](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L756), [757](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L757), [765](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L765), [790](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L790), [795](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L795), [796](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L796), [886](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L886), [910](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L910), [926](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L926), [927](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L927). 

```solidity
File: libraries/SafeTransferLib.sol

25:             // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.

56:             // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.

```

[25](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L25), [56](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L56). 

```solidity
File: multicall/Multicall.sol

22:                 // Other solutions will do work to differentiate the revert reasons and provide paranthetical information

24:                 // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)

```

[22](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L22), [24](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L24). 

```solidity
File: tokens/ERC1155Minimal.sol

57:     /// @notice Emitted when an attempt is made to initiate a transfer to a contract recipient that fails to signal support for ERC1155.

```

[57](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L57). 

```solidity
File: tokens/interfaces/IERC20Partial.sol

8: /// @dev However, we cannot productively handle a failed approval and such a situation would surely cause a revert later in execution.

9: /// @dev In addition, no notable instances exist of tokens that both i) contain a failure case for `approve` and ii) return `false` instead of reverting.

```

[8](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IERC20Partial.sol#L8), [9](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IERC20Partial.sol#L9). 

```solidity
File: types/LeftRight.sol

51:     // Typically, the slot is already clear when writing to it, but if it is not, the bits will be added to the existing bits

53:     // Note that the values *within* the slots are allowed to overflow, but overflows are contained and will not leak into the other slot

113:     // Typically, the slot is already clear when writing to it, but if it is not, the bits will be added to the existing bits

115:     // Note that the values *within* the slots are allowed to overflow, but overflows are contained and will not leak into the other slot

181:             // type cast z to uint128 to isolate the right slot and if it's higher than a value that was subtracted from (x)

272:     /// @dev Used for linked accumulators, so if the accumulator for one side overflows for a token, both cease to accumulate.

```

[51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L51), [53](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L53), [113](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L113), [115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L115), [181](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L181), [272](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L272). 

```solidity
File: types/LiquidityChunk.sol

10: /// @title A Panoptic Liquidity Chunk. Tracks Tick Range and Liquidity Information for a "chunk." Used to track movement of chunks.

13: /// @notice A liquidity chunk is an amount of `liquidity` (an amount of WETH, e.g.) deployed between two ticks: `tickLower` and `tickUpper`

```

[10](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L10), [13](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L13). 

```solidity
File: types/TokenId.sol

24: // (0) univ3pool        48bits     0bits      : first 6 bytes of the Uniswap v3 pool address (first 48 bits; little-endian), plus a pseudorandom number in the event of a collision

43: //  <---- 48 bits ---->    <---- 48 bits ---->    <---- 48 bits ---->     <---- 48 bits ---->   <- 16 bits ->   <- 48 bits ->

44: //         Leg 4                  Leg 3                  Leg 2                   Leg 1          tickSpacing    Univ3 Pool Address

46: //  <--- most significant bit                                                                             least significant bit --->

51: //   - if a leg is active (e.g. leg 1) there can be no gaps in other legs meaning: if leg 1 is active then leg 3 cannot be active if leg 2 is inactive.

55: //  We also refer to the legs via their index, so leg number 2 has leg index 1 (legIndex) (counting from zero), and in general leg number N has leg index N-1.

56: //  - the underlying strike price of the 2nd leg (leg index = 1) in this option position starts at bit index  (64 + 12 + 48 * (leg index=1))=123

73:     /// @notice AND mask to clear all bits except for the components of the chunk key (strike, width, tokenType) for each leg

86:     /// @return The `poolId` (Panoptic's pool fingerprint, contains the whole 64 bit sequence with the tickSpacing) of the Uniswap V3 pool

144:     /// @notice Get the associated risk partner of the leg index (generally another leg index in the position if enabled or the same leg index if no partner).

164:     /// @notice Get the width of the nth leg (index `legIndex`). This is half the tick-range covered by the leg (tickUpper - tickLower)/2.

369:             // We copy the logic from the countLegs function, using it here adds 5K to the contract size with IR for some reason

375:             // Since only the option ratios remain, we can be sure that no bits above the start of the inactive legs will be 1

390:             // i.e the whole mask is used to flip all legs with 4 legs, but only the first leg is flipped with 1 leg so we shift by 3 legs

391:             // We also clear the poolId area of the mask to ensure the bits that are shifted right into the area don't flip and cause issues

430:     /// @dev ASSUMPTION: For any leg, the option ratio is always > 0 (the leg always has a number of contracts associated with it).

438:         // Since only the option ratios remain, we can be sure that no bits above the start of the inactive legs will be 1

563:                     // if the two token long-types and the tokenTypes are both different (one is a short call, the other a long put, e.g.), this is a synthetic position

564:                     // A synthetic long or short is more capital efficient than each leg separated because the long+short premia accumulate proportionally

565:                     // unlike short stranlges, long strangles also cannot be partnered, because there is no reduction in risk (both legs can earn premia simultaneously)

```

[24](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L24), [43](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L43), [44](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L44), [46](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L46), [51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L51), [55](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L55), [56](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L56), [73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L73), [86](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L86), [144](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L144), [164](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L164), [369](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L369), [375](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L375), [390](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L390), [391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L391), [430](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L430), [438](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L438), [563](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L563), [564](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L564), [565](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L565). 

</details>

## [N-07] Visibility should be set explicitly rather than defaulting to `internal`

<details>
<summary><i>There are 8 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

131:     uint256 immutable TICK_DEVIATION;

136:     uint256 immutable COMMISSION_FEE;

141:     uint256 immutable SELLER_COLLATERAL_RATIO;

145:     uint256 immutable BUYER_COLLATERAL_RATIO;

149:     int256 immutable FORCE_EXERCISE_COST;

154:     uint256 immutable TARGET_POOL_UTIL;

158:     uint256 immutable SATURATED_POOL_UTIL;

162:     uint256 immutable ITM_SPREAD_MULTIPLIER;

```

[131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L131), [136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L136), [141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L141), [145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L145), [149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L149), [154](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L154), [158](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L158), [162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L162). 

</details>

## [N-08] Constructor missing variable check

Variable checks in the `constructor` are important to ensure that the contract is initialized correctly.

<details>
<summary><i>There are 4 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

178:     constructor(
179:         uint256 _commissionFee,
180:         uint256 _sellerCollateralRatio,
181:         uint256 _buyerCollateralRatio,
182:         int256 _forceExerciseCost,
183:         uint256 _targetPoolUtilization,
184:         uint256 _saturatedPoolUtilization,
185:         uint256 _ITMSpreadMultiplier
186:     ) {
187:         COMMISSION_FEE = _commissionFee;
188:         SELLER_COLLATERAL_RATIO = _sellerCollateralRatio;
189:         BUYER_COLLATERAL_RATIO = _buyerCollateralRatio;
190:         FORCE_EXERCISE_COST = _forceExerciseCost;
191:         TARGET_POOL_UTIL = _targetPoolUtilization;
192:         SATURATED_POOL_UTIL = _saturatedPoolUtilization;
193:         ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;
194: 
195:         // calculate amount of ticks required for upwards and downwards moves, used to check if current and mini-median tick
196:         // are out of sync (then apply a 100% collateral requirement)
197:         unchecked {
198:             // taylor expand log(1-sellCollateralRatio)/log(1.0001) around sellCollateralRatio=2000 up to 3rd order
199:             /// since we're dropping the higher order terms, which are all negative, this will underestimate the number of ticks for a 20% move
200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);
201:             TICK_DEVIATION = uint256(
202:                 2230 +
203:                     (12500 * ratioTick) /
204:                     10_000 +
205:                     (7812 * ratioTick ** 2) /
206:                     10_000 ** 2 +
207:                     (6510 * ratioTick ** 3) /
208:                     10_000 ** 3
209:             );
210:         }
211:     }

```

[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L178-L211). 

```solidity
File: PanopticFactory.sol

115:     constructor(
116:         address _WETH9,
117:         SemiFungiblePositionManager _SFPM,
118:         IUniswapV3Factory _univ3Factory,
119:         IDonorNFT _donorNFT,
120:         address _poolReference,
121:         address _collateralReference
122:     ) {
123:         WETH = _WETH9;
124:         SFPM = _SFPM;
125:         DONOR_NFT = _donorNFT;
126:         // We store the Uniswap Factory contract - later we can use this to verify uniswap pools
127:         UNIV3_FACTORY = _univ3Factory;
128:         POOL_REFERENCE = _poolReference;
129:         COLLATERAL_REFERENCE = _collateralReference;
130:     }

```

[115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L115-L130). 

```solidity
File: PanopticPool.sol

280:     constructor(SemiFungiblePositionManager _sfpm) {
281:         SFPM = _sfpm;
282:     }

```

[280](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L280-L282). 

```solidity
File: SemiFungiblePositionManager.sol

341:     constructor(IUniswapV3Factory _factory) {
342:         FACTORY = _factory;
343:     }

```

[341](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L341-L343). 

</details>

## [N-09] `constants` should be defined rather than using magic numbers

Magic numbers are numbers that appear without explanation in the code. They should be replaced with named constants.

<details>
<summary><i>There are 209 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

202:                 2230 +

203:                     (12500 * ratioTick) /

205:                     (7812 * ratioTick ** 2) /

206:                     10_000 ** 2 +

207:                     (6510 * ratioTick ** 3) /

208:                     10_000 ** 3

234:         totalSupply = 10 ** 6;

249:             _poolFee = fee / 100;

671:                                 2

778:                 min_sell_ratio /= 2;

843:                 return BUYER_COLLATERAL_RATIO / 2;

851:                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

1144:         uint256[2][] memory positionBalanceArray,

1162:         uint256[2][] memory positionBalanceArray,

1202:         uint256[2][] memory positionBalanceArray

1330:             : int64(uint64(poolUtilization >> 64));

1364:                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

1586:                     : int64(uint64(poolUtilization >> 64))

1632:             uint64 poolUtilization1 = uint64(poolUtilization >> 64);

1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```

[200](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L200), [202](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L203), [205](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L205), [206](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L206), [207](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L207), [208](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L208), [234](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L234), [249](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L249), [671](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L671), [778](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L778), [843](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L843), [851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L851), [1144](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1144), [1162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1162), [1202](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1202), [1330](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1330), [1364](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1364), [1367](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1367), [1586](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1586), [1632](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1632), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1638). 

```solidity
File: PanopticPool.sol

309:                 (uint256(block.timestamp) << 216) +

313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

370:         poolUtilization1 = uint64(balanceData.leftSlot() >> 64);

448:                 LeftRightSigned[4] memory premiaByLeg,

449:                 uint256[2][4] memory premiumAccumulatorsByLeg

685:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM

730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

801:         premiasByLeg = new LeftRightSigned[4][](positionIdList.length);

970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM

1080:             LeftRightSigned[4][] memory premiasByLeg;

1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

1445:         _numberOfPositions = (s_positionsHash[user] >> 248);

1552:                                         (liquidityChunk.liquidity())) / 2 ** 64

1561:                                         (liquidityChunk.liquidity())) / 2 ** 64

1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1668:         LeftRightUnsigned[4] memory collectedByLeg,

1769:                 totalLiquidity) / 2 ** 64;

1771:                 totalLiquidity) / 2 ** 64;

1836:         LeftRightUnsigned[4] memory collectedByLeg,

1841:         uint256[2][4] memory premiumAccumulatorsByLeg;

1923:                         uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;

1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),

1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,

```

[309](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L309), [313](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L313), [370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L370), [448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L448), [449](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L449), [685](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L685), [730](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L730), [801](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L801), [970](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L970), [1080](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1080), [1348](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1348), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1353), [1415](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1415), [1445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1445), [1552](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1552), [1561](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1561), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1636), [1668](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1668), [1769](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1769), [1771](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1771), [1836](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1836), [1841](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1841), [1923](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1923), [1942](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1942), [1959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1959). 

```solidity
File: SemiFungiblePositionManager.sol

388:             s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;

1352:                     totalLiquidity * 2 ** 64,

1357:                     totalLiquidity * 2 ** 64,

```

[388](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L388), [1352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1352), [1357](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1357). 

```solidity
File: libraries/Math.sol

94:                 x >>= 128;

95:                 r += 32;

98:                 x >>= 64;

99:                 r += 16;

102:                 x >>= 32;

103:                 r += 8;

106:                 x >>= 16;

107:                 r += 4;

110:                 x >>= 8;

111:                 r += 2;

137:             if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

139:             if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

141:             if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

143:             if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;

145:             if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

147:             if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;

149:             if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;

151:             if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;

153:             if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

155:             if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

157:             if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

159:             if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;

161:             if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

163:             if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;

165:             if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;

167:             if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

169:             if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;

171:             if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

173:             if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

197:                     uint256(liquidityChunk.liquidity()) << 96,

414:             uint256 inv = (3 * denominator) ^ 2;

418:             inv *= 2 - denominator * inv; // inverse mod 2**8

419:             inv *= 2 - denominator * inv; // inverse mod 2**16

420:             inv *= 2 - denominator * inv; // inverse mod 2**32

421:             inv *= 2 - denominator * inv; // inverse mod 2**64

422:             inv *= 2 - denominator * inv; // inverse mod 2**128

423:             inv *= 2 - denominator * inv; // inverse mod 2**256

484:             require(2 ** 64 > prod1);

505:                 prod0 := shr(64, prod0)

511:             prod0 |= prod1 * 2 ** 192;

547:             require(2 ** 96 > prod1);

568:                 prod0 := shr(96, prod0)

574:             prod0 |= prod1 * 2 ** 160;

587:             if (mulmod(a, b, 2 ** 96) > 0) {

624:             require(2 ** 128 > prod1);

645:                 prod0 := shr(128, prod0)

651:             prod0 |= prod1 * 2 ** 128;

664:             if (mulmod(a, b, 2 ** 128) > 0) {

701:             require(2 ** 192 > prod1);

722:                 prod0 := shr(192, prod0)

728:             prod0 |= prod1 * 2 ** 64;

758:             int256 pivot = arr[uint256(left + (right - left) / 2)];

```

[94](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L94), [95](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L95), [98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L98), [99](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L102), [103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L103), [106](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L106), [107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L107), [110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L110), [111](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L111), [137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L137), [139](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L139), [141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L141), [143](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L143), [145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L145), [147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L147), [149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L149), [151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L151), [153](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L153), [155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L155), [157](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L157), [159](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L159), [161](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L161), [163](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L163), [165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L165), [167](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L167), [169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L169), [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L171), [173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L173), [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L179), [197](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L197), [414](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L414), [418](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L418), [419](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L419), [420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L420), [421](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L421), [422](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L422), [423](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L423), [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L484), [505](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L505), [511](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L511), [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L547), [568](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L568), [574](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L574), [587](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L587), [624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L624), [645](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L645), [651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L651), [664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L664), [701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L701), [722](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L722), [728](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L728), [758](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L758). 

```solidity
File: libraries/PanopticMath.sol

50:             uint64 poolId = uint64(uint160(univ3pool) >> 112);

51:             poolId += uint64(uint24(tickSpacing)) << 48;

77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

107:                     ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)

108:                     : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);

155:             return int24(Math.sort(ticks)[cardinality / 2]);

178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

180:                 2;

183:             if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

200:                 uint24 orderMap = uint24(medianData >> 192);

207:                 for (uint8 i; i < 8; ++i) {

209:                     rank = (orderMap >> (3 * i)) % 8;

211:                     if (rank == 7) {

217:                     entry = int24(uint24(medianData >> (rank * 24)));

223:                     newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));

227:                     (block.timestamp << 216) +

228:                     (uint256(newOrderMap) << 192) +

229:                     uint256(uint192(medianData << 24)) +

242:         uint32[] memory secondsAgos = new uint32[](20);

244:         int256[] memory twapMeasurement = new int256[](19);

248:             for (uint256 i = 0; i < 20; ++i) {

249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);

256:             for (uint256 i = 0; i < 19; ++i) {

258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

266:             return int24(sortedTicks[10]);

376:             (width * tickSpacing) / 2,

377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);

512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)

553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

560:                         2 ** 128,

669:                 uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);

678:                 uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

771:         LeftRightSigned[4][] memory premiasByLeg,

862:                 LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;

```

[50](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L50), [51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L51), [77](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L77), [107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L107), [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L108), [155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L155), [178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178), [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179), [180](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L180), [183](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L183), [200](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L200), [207](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L207), [209](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L209), [211](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L211), [217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L217), [223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223), [227](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L227), [228](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L228), [229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L229), [242](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L242), [244](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L244), [248](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L248), [249](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L249), [256](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L256), [258](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L258), [266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L266), [376](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L376), [377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L377), [476](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L476), [477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L477), [495](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L495), [512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L512), [514](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L514), [530](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L530), [553](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L553), [560](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L560), [669](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L669), [678](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L678), [685](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L685), [771](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L771), [862](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L862). 

```solidity
File: libraries/SafeTransferLib.sol

30:             mstore(add(4, p), from) // Append the "from" argument.

31:             mstore(add(36, p), to) // Append the "to" argument.

32:             mstore(add(68, p), amount) // Append the "amount" argument.

37:                 or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),

41:                 call(gas(), token, 0, p, 100, 0, 32)

61:             mstore(add(4, p), to) // Append the "to" argument.

62:             mstore(add(36, p), amount) // Append the "amount" argument.

67:                 or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),

71:                 call(gas(), token, 0, p, 68, 0, 32)

```

[30](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L30), [31](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L31), [32](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L32), [37](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L37), [41](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L41), [61](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L61), [62](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L62), [67](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L67), [71](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L71). 

```solidity
File: types/LeftRight.sol

102:         return uint128(LeftRightUnsigned.unwrap(self) >> 128);

109:         return int128(LeftRightSigned.unwrap(self) >> 128);

126:             return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));

136:             return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));

```

[102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L109), [126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L126), [136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L136). 

```solidity
File: types/LiquidityChunk.sol

78:                     (uint256(uint24(_tickLower)) << 232) +

79:                         (uint256(uint24(_tickUpper)) << 208) +

109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));

182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));

```

[78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L78), [79](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L79), [109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L109), [126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L126), [173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L173), [182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L182). 

```solidity
File: types/TokenId.sol

98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

110:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

120:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

130:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

140:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

150:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

195:             return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

300:                         uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))

320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

376:             if (optionRatios < 2 ** 64) {

378:             } else if (optionRatios < 2 ** 112) {

380:             } else if (optionRatios < 2 ** 160) {

381:                 optionRatios = 2;

382:             } else if (optionRatios < 2 ** 208) {

383:                 optionRatios = 3;

385:                 optionRatios = 4;

395:                         ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)

406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

439:         if (optionRatios < 2 ** 64) {

441:         } else if (optionRatios < 2 ** 112) {

443:         } else if (optionRatios < 2 ** 160) {

444:             return 2;

445:         } else if (optionRatios < 2 ** 208) {

446:             return 3;

448:         return 4;

477:         if (i == 2)

483:         if (i == 3)

506:             uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;

507:             for (uint256 i = 0; i < 4; ++i) {

512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

521:                     if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {

522:                         revert Errors.InvalidTokenIdParameter(6);

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

533:                 ) revert Errors.InvalidTokenIdParameter(4);

542:                         revert Errors.InvalidTokenIdParameter(3);

548:                     ) revert Errors.InvalidTokenIdParameter(3);

561:                         revert Errors.InvalidTokenIdParameter(4);

567:                         revert Errors.InvalidTokenIdParameter(5);

```

[98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L98), [110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L110), [120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120), [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130), [140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140), [150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150), [160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171), [195](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L195), [212](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L212), [229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L229), [246](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L246), [263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L263), [281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L281), [300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L300), [320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L320), [376](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L376), [378](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L378), [380](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L380), [381](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L381), [382](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L382), [383](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L383), [385](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L385), [395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L395), [406](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L406), [439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L439), [441](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L441), [443](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L443), [444](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L444), [445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L445), [446](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L446), [448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L448), [477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L477), [483](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L483), [506](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L506), [507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L507), [512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L512), [521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L521), [522](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L522), [528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L528), [533](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L533), [542](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L542), [548](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L548), [561](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L561), [567](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L567). 

</details>

## [N-10] Missing event for critical parameters change

It is important to log critical parameters change to be able to track the state of the contract.

<details>
<summary><i>There are 7 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

221:     function startToken(
222:         bool underlyingIsToken0,
223:         address token0,
224:         address token1,
225:         uint24 fee,
226:         PanopticPool panopticPool
227:     ) external {
228:         // fails if already initialized
229:         if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();
230:         s_initialized = true;
231: 
232:         // these virtual shares function as a multiplier for the capital requirement to manipulate the pool price
233:         // e.g if the virtual shares are 10**6, then the capital requirement to manipulate the price to 10**12 is 10**18
234:         totalSupply = 10 ** 6;
235: 
236:         // set total assets to 1
237:         // the initial share price is defined by 1/virtualShares
238:         s_poolAssets = 1;
239: 
240:         // store the address of the underlying ERC20 token
241:         s_underlyingToken = underlyingIsToken0 ? token0 : token1;
242: 
243:         // store the Panoptic pool for this collateral token
244:         s_panopticPool = panopticPool;
245: 
246:         // cache the pool fee in basis points
247:         uint24 _poolFee;
248:         unchecked {
249:             _poolFee = fee / 100;
250:         }
251:         s_poolFee = _poolFee;
252: 
253:         // Stores the addresses of the underlying tracked tokens.
254:         s_univ3token0 = token0;
255:         s_univ3token1 = token1;
256: 
257:         // store whether the current collateral token is token0 (true) or token1 (false; since there's always exactly two tokens it could be)
258:         s_underlyingIsToken0 = underlyingIsToken0;
259: 
260:         // Additional risk premium charged on intrinsic value of ITM positions
261:         unchecked {
262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);
263:         }
264:     }

995:     function takeCommissionAddData(
996:         address optionOwner,
997:         int128 longAmount,
998:         int128 shortAmount,
999:         int128 swappedAmount
1000:     ) external onlyPanopticPool returns (int256 utilization) {
1001:         unchecked {
1002:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
1003:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
1004: 
1005:             // constrict premium to only assets not belonging to PLPs (i.e premium paid by sellers or collected from the pool earlier)
1006:             int256 tokenToPay = _getExchangedAmount(longAmount, shortAmount, swappedAmount);
1007: 
1008:             // compute tokens to be paid due to swap
1009:             // mint or burn tokens due to minting in-the-money
1010:             if (tokenToPay > 0) {
1011:                 // if user must pay tokens, burn them from user balance
1012:                 uint256 sharesToBurn = Math.mulDivRoundingUp(
1013:                     uint256(tokenToPay),
1014:                     totalSupply,
1015:                     totalAssets()
1016:                 );
1017:                 _burn(optionOwner, sharesToBurn);
1018:             } else if (tokenToPay < 0) {
1019:                 // if user must receive tokens, mint them
1020:                 uint256 sharesToMint = convertToShares(uint256(-tokenToPay));
1021:                 _mint(optionOwner, sharesToMint);
1022:             }
1023: 
1024:             // update stored asset balances with net moved amounts
1025:             // the inflow or outflow of pool assets is defined by the swappedAmount: it includes both the ITM swap amounts and the short/long amounts used to create the position
1026:             // however, any intrinsic value is paid for by the users, so we only add the portion that comes from PLPs: the short/long amounts
1027:             // premia is not included in the balance since it is the property of options buyers and sellers, not PLPs
1028:             s_poolAssets = uint128(uint256(updatedAssets));
1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));
1030: 
1031:             utilization = _poolUtilization();
1032:         }
1033:     }

1043:     function exercise(
1044:         address optionOwner,
1045:         int128 longAmount,
1046:         int128 shortAmount,
1047:         int128 swappedAmount,
1048:         int128 realizedPremium
1049:     ) external onlyPanopticPool returns (int128) {
1050:         unchecked {
1051:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
1052:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
1053: 
1054:             // add premium to be paid/collected on position close
1055:             int256 tokenToPay = -realizedPremium;
1056: 
1057:             // if burning ITM and swap occurred, compute tokens to be paid through exercise and add swap fees
1058:             int256 intrinsicValue = swappedAmount - (longAmount - shortAmount);
1059: 
1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {
1061:                 // intrinsic value is the amount that need to be exchanged due to burning in-the-money
1062: 
1063:                 // add the intrinsic value to the tokenToPay
1064:                 tokenToPay += intrinsicValue;
1065:             }
1066: 
1067:             if (tokenToPay > 0) {
1068:                 // if user must pay tokens, burn them from user balance (revert if balance too small)
1069:                 uint256 sharesToBurn = Math.mulDivRoundingUp(
1070:                     uint256(tokenToPay),
1071:                     totalSupply,
1072:                     totalAssets()
1073:                 );
1074:                 _burn(optionOwner, sharesToBurn);
1075:             } else if (tokenToPay < 0) {
1076:                 // if user must receive tokens, mint them
1077:                 uint256 sharesToMint = convertToShares(uint256(-tokenToPay));
1078:                 _mint(optionOwner, sharesToMint);
1079:             }
1080: 
1081:             // update stored asset balances with net moved amounts
1082:             // any intrinsic value is paid for by the users, so we do not add it to s_inAMM
1083:             // premia is not included in the balance since it is the property of options buyers and sellers, not PLPs
1084:             s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));
1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));
1086: 
1087:             return (int128(tokenToPay));
1088:         }
1089:     }

```

[221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221-L264), [995](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L995-L1033), [1043](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043-L1089). 

```solidity
File: PanopticFactory.sol

147:     function transferOwnership(address newOwner) external {
148:         address currentOwner = s_owner;
149: 
150:         if (msg.sender != currentOwner) revert Errors.NotOwner();
151: 
152:         s_owner = newOwner;
153: 
154:         emit OwnershipTransferred(currentOwner, newOwner);
155:     }

```

[147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147-L155). 

```solidity
File: PanopticPool.sol

291:     function startPool(
292:         IUniswapV3Pool _univ3pool,
293:         address token0,
294:         address token1,
295:         CollateralTracker collateralTracker0,
296:         CollateralTracker collateralTracker1
297:     ) external {
298:         // reverts if the Uniswap pool has already been initialized
299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();
300: 
301:         // Store the univ3Pool variable
302:         s_univ3pool = IUniswapV3Pool(_univ3pool);
303: 
304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();
305: 
306:         // Store the median data
307:         unchecked {
308:             s_miniMedian =
309:                 (uint256(block.timestamp) << 216) +
310:                 // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
311:                 // see comment on s_miniMedian initialization for format of this magic number
312:                 (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4
314:                 (uint256(uint24(currentTick))); // add to slot 3
315:         }
316: 
317:         // Store the collateral token0
318:         s_collateralToken0 = collateralTracker0;
319:         s_collateralToken1 = collateralTracker1;
320: 
321:         // consolidate all 4 approval calls to one library delegatecall in order to reduce bytecode size
322:         // approves:
323:         // SFPM: token0, token1
324:         // CollateralTracker0 - token0
325:         // CollateralTracker1 - token1
326:         InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);
327:     }

522:     function pokeMedian() external {
523:         (, , uint16 observationIndex, uint16 observationCardinality, , , ) = s_univ3pool.slot0();
524: 
525:         (, uint256 medianData) = PanopticMath.computeInternalMedian(
526:             observationIndex,
527:             observationCardinality,
528:             MEDIAN_PERIOD,
529:             s_miniMedian,
530:             s_univ3pool
531:         );
532: 
533:         if (medianData != 0) s_miniMedian = medianData;
534:     }

614:     function _mintOptions(
615:         TokenId[] calldata positionIdList,
616:         uint128 positionSize,
617:         uint64 effectiveLiquidityLimitX32,
618:         int24 tickLimitLow,
619:         int24 tickLimitHigh
620:     ) internal {
621:         // the new tokenId will be the last element in 'positionIdList'
622:         TokenId tokenId;
623:         unchecked {
624:             tokenId = positionIdList[positionIdList.length - 1];
625:         }
626: 
627:         // do duplicate checks and the checks related to minting and positions
628:         _validatePositionList(msg.sender, positionIdList, 1);
629: 
630:         (tickLimitLow, tickLimitHigh) = _getSlippageLimits(tickLimitLow, tickLimitHigh);
631: 
632:         // make sure the tokenId is for this Panoptic pool
633:         if (tokenId.poolId() != SFPM.getPoolId(address(s_univ3pool)))
634:             revert Errors.InvalidTokenIdParameter(0);
635: 
636:         // disallow user to mint exact same position
637:         // in order to do it, user should burn it first and then mint
638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)
639:             revert Errors.PositionAlreadyMinted();
640: 
641:         // Mint in the SFPM and update state of collateral
642:         uint128 poolUtilizations = _mintInSFPMAndUpdateCollateral(
643:             tokenId,
644:             positionSize,
645:             tickLimitLow,
646:             tickLimitHigh
647:         );
648: 
649:         // calculate and write position data
650:         _addUserOption(tokenId, effectiveLiquidityLimitX32);
651: 
652:         // update the users options balance of position 'tokenId'
653:         // note: user can't mint same position multiple times, so set the positionSize instead of adding
654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
655:             .wrap(0)
656:             .toLeftSlot(poolUtilizations)
657:             .toRightSlot(positionSize);
658: 
659:         // Perform solvency check on user's account to ensure they had enough buying power to mint the option
660:         // Add an initial buffer to the collateral requirement to prevent users from minting their account close to insolvency
661:         uint256 medianData = _validateSolvency(msg.sender, positionIdList, BP_DECREASE_BUFFER);
662: 
663:         // Update `s_miniMedian` with a new observation if the last observation is old enough (returned medianData is nonzero)
664:         if (medianData != 0) s_miniMedian = medianData;
665: 
666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);
667:     }

```

[291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L327), [522](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L522-L534), [614](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L614-L667). 

</details>

## [N-11] Functions that alter state should emit events

Functions that alter state should emit events to notify users of the state change. This is especially important for functions that alter state and do not return a value.

<details>
<summary><i>There are 6 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

221:     function startToken(

995:     function takeCommissionAddData(

1043:     function exercise(

```

[221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221), [995](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L995), [1043](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043). 

```solidity
File: PanopticFactory.sol

134:     function initialize(address _owner) public {

```

[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134). 

```solidity
File: PanopticPool.sol

291:     function startPool(

522:     function pokeMedian() external {

```

[291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291), [522](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L522). 

</details>

## [N-12] Zero address check is missing in non-setter functions

<details>
<summary><i>There are 37 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

221:     function startToken(

323:     function transfer(

341:     function transferFrom(

417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {

477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {

531:     function withdraw(

591:     function redeem(

864:     function delegate(

894:     function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

903:     function refund(address delegatee, uint256 assets) external onlyPanopticPool {

911:     function revoke(

975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

995:     function takeCommissionAddData(

1043:     function exercise(

```

[221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221), [323](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L341), [417](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L417), [477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L477), [531](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L531), [591](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L591), [864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L864), [894](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L894), [903](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L903), [911](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L911), [975](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L975), [995](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L995), [1043](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043). 

```solidity
File: PanopticFactory.sol

147:     function transferOwnership(address newOwner) external {

335:     function _mintFullRange(

```

[147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147), [335](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L335). 

```solidity
File: PanopticPool.sol

291:     function startPool(

794:     function _burnAllOptionsFrom(

826:     function _burnOptions(

859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

955:     function _burnAndHandleExercise(

1017:     function liquidate(

1405:     function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {

1833:     function _updateSettlementPostBurn(

```

[291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291), [794](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L794), [826](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L826), [859](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L859), [955](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L955), [1017](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017), [1405](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1405), [1833](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833). 

```solidity
File: SemiFungiblePositionManager.sol

540:     function safeTransferFrom(

566:     function safeBatchTransferFrom(

593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

```

[540](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L540), [566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566), [593](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593). 

```solidity
File: libraries/InteractionHelper.sol

24:     function doApprovals(

```

[24](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L24). 

```solidity
File: libraries/PanopticMath.sol

768:     function haircutPremia(

```

[768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768). 

```solidity
File: libraries/SafeTransferLib.sol

21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:     function safeTransfer(address token, address to, uint256 amount) internal {

```

[21](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L21), [52](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L52). 

```solidity
File: tokens/ERC1155Minimal.sol

214:     function _mint(address to, uint256 id, uint256 amount) internal {

236:     function _burn(address from, uint256 id, uint256 amount) internal {

```

[214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L214), [236](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L236). 

```solidity
File: tokens/ERC20Minimal.sol

49:     function approve(address spender, uint256 amount) public returns (bool) {

103:     function _transferFrom(address from, address to, uint256 amount) internal {

122:     function _mint(address to, uint256 amount) internal {

136:     function _burn(address from, uint256 amount) internal {

```

[49](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L49), [103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L103), [122](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L122), [136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L136). 

</details>

## [N-13] Use `@inheritdoc` rather than using a non-standard annotation

<details>
<summary><i>There are 2 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

319:     /// @dev See {IERC20-transfer}.

336:     /// @dev See {IERC20-transferFrom}.

```

[319](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L319), [336](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L336). 

</details>

## [N-14] Change `public` to `external` for functions that are not called internally

Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`.

<details>
<summary><i>There are 14 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

323:     function transfer(

341:     function transferFrom(

507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {

1141:     function getAccountMarginDetails(

```

[323](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L341), [507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L507), [572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L572), [1141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1141). 

```solidity
File: PanopticFactory.sol

134:     function initialize(address _owner) public {

```

[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134). 

```solidity
File: PanopticPool.sol

1444:     function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

```

[1444](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1444). 

```solidity
File: SemiFungiblePositionManager.sol

540:     function safeTransferFrom(

566:     function safeBatchTransferFrom(

```

[540](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L540), [566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566). 

```solidity
File: multicall/Multicall.sol

12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {

```

[12](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L12). 

```solidity
File: tokens/ERC1155Minimal.sol

81:     function setApprovalForAll(address operator, bool approved) public {

178:     function balanceOfBatch(

200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

```

[81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L81), [178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L178), [200](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L200). 

```solidity
File: tokens/ERC20Minimal.sol

49:     function approve(address spender, uint256 amount) public returns (bool) {

```

[49](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L49). 

</details>

## [N-15] Constants in comparisons should appear on the left side

Doing so will prevent [typo bugs](https://www.moserware.com/2008/01/constants-on-left-are-better-but-this.html)

<details>
<summary><i>There are 97 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

664:                 if (positionId.isLong(leg) == 0) continue;

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

709:                     (tokenType == 1 && currentValue0 < oracleValue0)

1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1107:             if (intrinsicValue != 0) {

1339:             if (isLong == 0) {

1346:                     ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1

1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1451:             if (isLong == 1) {

1479:         if (isLong == 0) {

1488:         } else if (isLong == 1) {

1544:                 if (tokenType == 0) {

1559:                 if (tokenType == 1) {

```

[331](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L331), [350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L350), [664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L664), [708](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L708), [709](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L709), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1060), [1107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1107), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1339), [1346](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1346), [1347](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1347), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1374), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1375), [1451](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1451), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1479), [1488](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1488), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1544), [1559](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1559). 

```solidity
File: PanopticFactory.sol

224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

229:         if (address(s_getPanopticPool[v3Pool]) != address(0))

```

[224](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L224), [227](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L227), [229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L229). 

```solidity
File: PanopticPool.sol

299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

533:         if (medianData != 0) s_miniMedian = medianData;

638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

664:         if (medianData != 0) s_miniMedian = medianData;

768:             if (isLong == 1) {

865:             if (tokenId.isLong(leg) == 0) {

1188:         if (touchedId.length != 1) revert Errors.InputListFail();

1483:         if (netLiquidity == 0) return;

1520:             if ((isLong == 1) || computeAllPremia) {

1566:                     if (isLong == 1) {

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1679:             if (tokenId.isLong(leg) == 0) {

1862:             if (LeftRightSigned.unwrap(legPremia) != 0) {

1864:                 if (tokenId.isLong(leg) == 1) {

```

[299](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L299), [460](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L460), [533](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L533), [638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L638), [664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L664), [768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L768), [865](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L865), [1188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1188), [1483](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1483), [1520](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1520), [1566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1566), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1596), [1679](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1679), [1862](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1862), [1864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1864). 

```solidity
File: SemiFungiblePositionManager.sol

355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

362:         if (s_AddrToPoolIdData[univ3pool] != 0) return;

632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

787:             if ((itm0 != 0) && (itm1 != 0)) {

823:             } else if (itm0 != 0) {

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

999:             if (isLong == 0) {

1073:             if (tokenType == 1) {

1078:             if (tokenType == 0) {

1275:         if (isLong == 1) {

1279:         if (LeftRightSigned.unwrap(amountToCollect) != 0) {

1469:             if (netLiquidity != 0) {

```

[355](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L355), [362](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L362), [632](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L632), [633](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L633), [688](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L688), [717](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L717), [787](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L787), [823](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L823), [833](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L833), [999](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L999), [1073](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1073), [1078](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1078), [1275](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1275), [1279](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1279), [1469](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1469). 

```solidity
File: libraries/FeesCalc.sol

67:                 if (tokenId.isLong(leg) == 0) {

```

[67](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L67). 

```solidity
File: libraries/Math.sol

137:             if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

139:             if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

141:             if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

143:             if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;

145:             if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

147:             if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;

149:             if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;

151:             if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;

153:             if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

155:             if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

157:             if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

159:             if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;

161:             if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

163:             if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;

165:             if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;

167:             if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

169:             if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;

171:             if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

173:             if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

360:             if (prod1 == 0) {

474:             if (prod1 == 0) {

537:             if (prod1 == 0) {

614:             if (prod1 == 0) {

691:             if (prod1 == 0) {

```

[137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L137), [139](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L139), [141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L141), [143](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L143), [145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L145), [147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L147), [149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L149), [151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L151), [153](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L153), [155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L155), [157](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L157), [159](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L159), [161](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L161), [163](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L163), [165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L165), [167](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L167), [169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L169), [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L171), [173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L173), [360](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L360), [474](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L474), [537](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L537), [614](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L614), [691](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L691). 

```solidity
File: libraries/PanopticMath.sol

211:                     if (rank == 7) {

325:         if (tokenId.asset(legIndex) == 0) {

425:         if (tokenType == 0) {

479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

584:         if (tokenId.asset(legIndex) == 0) {

618:         if (tokenId.tokenType(legIndex) == 0) {

785:                     if (tokenId.isLong(leg) == 1) {

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

864:                     if (tokenId.isLong(leg) == 1) {

```

[211](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L211), [325](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L325), [425](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L425), [479](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L479), [584](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L584), [618](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L618), [785](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L785), [856](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L857), [864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L864). 

```solidity
File: tokens/ERC1155Minimal.sol

112:         if (to.code.length != 0) {

163:         if (to.code.length != 0) {

222:         if (to.code.length != 0) {

```

[112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L112), [163](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L163), [222](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L222). 

```solidity
File: types/TokenId.sol

465:         if (i == 0)

471:         if (i == 1)

477:         if (i == 2)

483:         if (i == 3)

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

508:                 if (self.optionRatio(i) == 0) {

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

592:                     if (self.isLong(i) == 1) return; // validated

```

[465](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L465), [471](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L471), [477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L477), [483](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L483), [501](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L501), [508](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L508), [528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L528), [566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L566), [592](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L592). 

</details>

## [N-16] Redundant return statement with named return variable

Adding a return statement when the function defines a named return variable is redundant.

<details>
<summary><i>There are 30 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

361:     function asset() external view returns (address assetTokenAddress) {

370:     function totalAssets() public view returns (uint256 totalManagedAssets) {

379:     function convertToShares(uint256 assets) public view returns (uint256 shares) {

386:     function convertToAssets(uint256 shares) public view returns (uint256 assets) {

392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

444:     function maxMint(address) external view returns (uint256 maxShares) {

507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

518:     function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

535:     ) external returns (uint256 shares) {

572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {

581:     function previewRedeem(uint256 shares) public view returns (uint256 assets) {

595:     ) external returns (uint256 assets) {

741:     function _poolUtilization() internal view returns (int256 poolUtilization) {

753:     ) internal view returns (uint256 sellCollateralRatio) {

808:     ) internal view returns (uint256 buyCollateralRatio) {

1164:     ) internal view returns (LeftRightUnsigned tokenData) {

1203:     ) internal view returns (uint256 tokenRequired) {

1284:     ) internal view returns (uint256 required) {

1606:     ) internal view returns (uint256 strangleRequired) {

```

[361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L370), [379](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444), [507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L507), [518](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L518), [535](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L535), [572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L581), [595](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L595), [741](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L741), [753](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L753), [808](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L808), [1164](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1164), [1203](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1203), [1284](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1284), [1606](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1606). 

```solidity
File: PanopticPool.sol

385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

435:     ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

1431:     function collateralToken0() external view returns (CollateralTracker collateralToken) {

```

[385](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L385), [435](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L435), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1431). 

```solidity
File: SemiFungiblePositionManager.sol

759:     ) internal returns (LeftRightSigned totalSwapped) {

1557:     ) external view returns (IUniswapV3Pool UniswapV3Pool) {

```

[759](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L759), [1557](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1557). 

```solidity
File: libraries/InteractionHelper.sol

110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {

```

[110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L110). 

```solidity
File: libraries/PanopticMath.sol

658:     ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

```

[658](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L658). 

```solidity
File: types/LeftRight.sol

194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

214:     function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

254:     ) internal pure returns (LeftRightSigned z) {

```

[194](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L194), [214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L232), [254](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L254). 

</details>

## [N-17] Unsafe conversion from unsigned to signed values

Solidity follows [two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) rules for its integers, meaning that the most significant bit for signed integers is used to denote the sign, and converting between the two requires inverting all of the bits and adding one. Because of this, casting an unsigned integer to a signed one may result in a change of the sign and or magnitude of the value. For example, `int8(type(uint8).max)` is not equal to `type(int8).max`, but is equal to `-1`. `type(uint8).max` in binary is `11111111`, which if cast to a signed value, means the first binary `1` indicates a negative value, and the binary `1`s, invert to all zeroes, and when one is added, it becomes one, but negative, and therefore the decimal value of binary `11111111` is `-1`.

<details>
<summary><i>There are 25 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

743:             return int256((s_inAMM * DECIMALS) / totalAssets());

1003:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

1052:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

1115:                 exchangedAmount = intrinsicValue + int256(swapCommission);

1119:             exchangedAmount += int256(
1120:                 Math.unsafeDivRoundingUp(
1121:                     uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
1122:                     DECIMALS
1123:                 )

1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```

[715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L715), [718](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L718), [743](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L743), [1003](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1003), [1029](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1029), [1052](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1052), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085), [1115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1115), [1119](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1119-L1123), [1637](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1638). 

```solidity
File: PanopticPool.sol

1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1935:                                                 (int256(
1936:                                                     grossPremiumLast.rightSlot() *
1937:                                                         totalLiquidityBefore

1939:                                                     int256(
1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941:                                                             positionLiquidity

1952:                                                 (int256(
1953:                                                     grossPremiumLast.leftSlot() *
1954:                                                         totalLiquidityBefore

1956:                                                     int256(
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958:                                                             positionLiquidity

```

[1635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1636), [1935](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1935-L1937), [1939](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1939-L1941), [1952](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1952-L1954), [1956](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1956-L1958). 

```solidity
File: libraries/PanopticMath.sol

151:                     int256(timestamps[i] - timestamps[i + 1]);

217:                     entry = int24(uint24(medianData >> (rank * 24)));

681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));

683:                 bonus1 = int256(
684:                     PanopticMath.convert0to1(
685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
686:                         sqrtPriceX96Final
687:                     )

937:                             int128(
938:                                 int256(
939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
940:                                 ) + refundValues.leftSlot()

938:                                 int256(
939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)

955:                             int128(
956:                                 int256(
957:                                     PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
958:                                 ) + refundValues.rightSlot()

956:                                 int256(
957:                                     PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)

```

[151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L151), [217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L217), [681](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L681), [683](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L683-L687), [937](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L937-L940), [938](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L938-L939), [955](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L955-L958), [956](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L956-L957). 

</details>

## [N-18] Remove unnecessary brackets

Change `((x))` to `(x)`.

<details>
<summary><i>There are 46 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

731:                 .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))

732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

743:             return int256((s_inAMM * DECIMALS) / totalAssets());

797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1346:                     ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1

1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

```

[731](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L731), [732](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L732), [743](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L743), [797](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L797), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1060), [1346](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1346), [1347](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1347), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1374), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1375). 

```solidity
File: PanopticPool.sol

1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1768:             uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *

1770:             uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *

```

[1635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1636), [1768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1768), [1770](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1770). 

```solidity
File: SemiFungiblePositionManager.sol

717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

727:         if ((currentTick >= tickLimitHigh) || (currentTick <= tickLimitLow))

787:             if ((itm0 != 0) && (itm1 != 0)) {

1391:                         ((removedLiquidity ** 2) / 2 ** (VEGOID));

```

[717](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L717), [727](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L727), [787](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L787), [1391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1391). 

```solidity
File: libraries/Math.sol

179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

297:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

303:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) {

312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

```

[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L179), [297](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L297), [303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L303), [312](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L312), [319](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L319). 

```solidity
File: libraries/PanopticMath.sol

178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

218:                     if ((below) && (lastObservedTick > entry)) {

223:                     newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));

476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

706:                 if ((paid0 > balance0)) {

724:                 if ((paid1 > balance1)) {

```

[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178), [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179), [218](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L218), [223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223), [476](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L476), [477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L477), [706](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L706), [724](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L724). 

```solidity
File: types/LiquidityChunk.sol

126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

```

[126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L126). 

```solidity
File: types/TokenId.sol

98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

110:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

120:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

130:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

140:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

150:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

300:                         uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))

395:                         ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)

512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

560:                     if ((_isLong == isLongP) && (_tokenType == tokenTypeP))

566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {

```

[98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L98), [110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L110), [120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120), [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130), [140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140), [150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150), [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171), [246](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L246), [300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L300), [395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L395), [512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L512), [528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L528), [560](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L560), [566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L566), [589](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L589). 

</details>

## [N-19] Avoid mutating function parameters

Function parameters in Solidity are passed by value, meaning they are essentially local copies. Mutating them can lead to confusion and errors because the changes don't persist outside the function. By keeping function parameters immutable, you ensure clarity in code behavior, preventing unintended side-effects. If you need to modify a value based on a parameter, use a local variable inside the function, leaving the original parameter unaltered. By adhering to this practice, you maintain a clear distinction between input data and the internal processing logic, improving code readability and reducing the potential for bugs.

<details>
<summary><i>There are 6 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

752:         int256 utilization

1605:         uint128 poolUtilization

```

[752](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L752), [1605](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1605). 

```solidity
File: PanopticFactory.sol

291:         bytes32 salt,

```

[291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L291). 

```solidity
File: SemiFungiblePositionManager.sol

681:         TokenId tokenId,

683:         int24 tickLimitLow,

684:         int24 tickLimitHigh,

```

[681](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L681), [683](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L683), [684](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L684). 

</details>

## [N-20] Local variables should be named using mixedCase

<details>
<summary><i>There are 12 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

773:         uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;

```

[773](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L773). 

```solidity
File: PanopticFactory.sol

223:         address _owner = s_owner;

```

[223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L223). 

```solidity
File: PanopticPool.sol

439:         address c_user = user;

1117:             address _liquidatee = liquidatee;

1139:         LeftRightUnsigned _delegations = delegations;

1924:                         uint256 _leg = leg;

```

[439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L439), [1117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1117), [1139](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1139), [1924](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1924). 

```solidity
File: SemiFungiblePositionManager.sol

883:             LeftRightSigned _moved;

893:                 uint256 _leg;

```

[883](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L883), [893](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L893). 

```solidity
File: libraries/PanopticMath.sol

855:                 address _liquidatee = liquidatee;

```

[855](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L855). 

```solidity
File: types/LeftRight.sol

290:         bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);

291:         bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);

```

[290](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L290), [291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L291). 

```solidity
File: types/TokenId.sol

587:                 int24 _strike = self.strike(i);

```

[587](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L587). 

</details>

## [N-21] Overridden function names should differ

In Solidity, while function overriding allows for functions with the same name to coexist, it is advisable to avoid this practice to enhance code readability and maintainability. Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the likelihood of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function, but also helps prevent unintended function calls or incorrect overriding. By adopting a clear and consistent naming convention, developers can create more comprehensible and maintainable smart contracts.

<details>
<summary><i>There are 6 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

864:     function delegate(

894:     function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

903:     function refund(address delegatee, uint256 assets) external onlyPanopticPool {

975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

```

[864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L864), [894](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L894), [903](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L903), [975](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L975). 

```solidity
File: PanopticPool.sol

569:     function burnOptions(

586:     function burnOptions(

```

[569](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L569), [586](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L586). 

</details>

## [N-22] Use != 0 instead of > 0 for unsigned integer comparison

<details>
<summary><i>There are 4 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

1010:             if (tokenToPay > 0) {

1067:             if (tokenToPay > 0) {

```

[1010](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1010), [1067](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1067). 

```solidity
File: libraries/PanopticMath.sol

931:             if (balanceShortage > 0) {

949:             if (balanceShortage > 0) {

```

[931](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L931), [949](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L949). 

</details>

## [N-23] Inconsistent spacing in comments

Using `// x` is more preferable than `//x`. It is easier to read and also easier to search for.

<details>
<summary><i>There are 9 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

1117: 
1118:             //compute total commission amount = commission rate + spread fee

1118:             //compute total commission amount = commission rate + spread fee

```

[1117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1117-L1118), [1118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1118). 

```solidity
File: SemiFungiblePositionManager.sol

609: 
610:             //construct the positionKey for the from and to addresses

610:             //construct the positionKey for the from and to addresses

642: 
643:             //update+store liquidity and fee values between accounts

643:             //update+store liquidity and fee values between accounts

820: 
821:                 //compute the swap amount, set as positive (exact input)

821:                 //compute the swap amount, set as positive (exact input)

988:         LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache

```

[609](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L609-L610), [610](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L610), [642](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L642-L643), [643](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L643), [820](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L820-L821), [821](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L821), [988](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L988). 

</details>

## [N-24] Use modifier for special msg.sender

If functions are only allowed to be called by the special actor, modifier should be used to make the code more readable.

<details>
<summary><i>There are 3 instance of this issue:</i></summary>

```solidity
File: PanopticFactory.sol

147:     function transferOwnership(address newOwner) external {
148:         address currentOwner = s_owner;
149: 
150:         if (msg.sender != currentOwner) revert Errors.NotOwner();
151: 
152:         s_owner = newOwner;
153: 
154:         emit OwnershipTransferred(currentOwner, newOwner);
155:     }

```

[147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147-L155). 

```solidity
File: tokens/ERC1155Minimal.sol

94:     function safeTransferFrom(
95:         address from,
96:         address to,
97:         uint256 id,
98:         uint256 amount,
99:         bytes calldata data
100:     ) public virtual {
101:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
102: 
103:         balanceOf[from][id] -= amount;
104: 
105:         // balance will never overflow
106:         unchecked {
107:             balanceOf[to][id] += amount;
108:         }
109: 
110:         emit TransferSingle(msg.sender, from, to, id, amount);
111: 
112:         if (to.code.length != 0) {
113:             if (
114:                 ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=
115:                 ERC1155Holder.onERC1155Received.selector
116:             ) {
117:                 revert UnsafeRecipient();
118:             }
119:         }
120:     }

130:     function safeBatchTransferFrom(
131:         address from,
132:         address to,
133:         uint256[] calldata ids,
134:         uint256[] calldata amounts,
135:         bytes calldata data
136:     ) public virtual {
137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
138: 
139:         // Storing these outside the loop saves ~15 gas per iteration.
140:         uint256 id;
141:         uint256 amount;
142: 
143:         for (uint256 i = 0; i < ids.length; ) {
144:             id = ids[i];
145:             amount = amounts[i];
146: 
147:             balanceOf[from][id] -= amount;
148: 
149:             // balance will never overflow
150:             unchecked {
151:                 balanceOf[to][id] += amount;
152:             }
153: 
154:             // An array can't have a total length
155:             // larger than the max uint256 value.
156:             unchecked {
157:                 ++i;
158:             }
159:         }
160: 
161:         emit TransferBatch(msg.sender, from, to, ids, amounts);
162: 
163:         if (to.code.length != 0) {
164:             if (
165:                 ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
166:                 ERC1155Holder.onERC1155BatchReceived.selector
167:             ) {
168:                 revert UnsafeRecipient();
169:             }
170:         }
171:     }

```

[94](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L94-L120), [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L130-L171). 

</details>

## [N-25] `2**<n> - 1` should be re-written as `type(uint<n>).max`

Earlier versions of solidity can use uint<n>(-1) instead. Expressions not including the - 1 can often be re-written to accommodate the change (e.g. by using a > rather than a >=, which will also save some gas)

<details>
<summary><i>There are 41 instance of this issue:</i></summary>

```solidity
File: PanopticPool.sol

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

1552:                                         (liquidityChunk.liquidity())) / 2 ** 64

1561:                                         (liquidityChunk.liquidity())) / 2 ** 64

1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1769:                 totalLiquidity) / 2 ** 64;

1771:                 totalLiquidity) / 2 ** 64;

1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),

1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,

```

[165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L165), [1348](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1348), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1353), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1487), [1552](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1552), [1561](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1561), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1636), [1769](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1769), [1771](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1771), [1942](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1942), [1959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1959). 

```solidity
File: SemiFungiblePositionManager.sol

388:             s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;

1352:                     totalLiquidity * 2 ** 64,

1357:                     totalLiquidity * 2 ** 64,

```

[388](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L388), [1352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1352), [1357](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1357). 

```solidity
File: libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

484:             require(2 ** 64 > prod1);

511:             prod0 |= prod1 * 2 ** 192;

547:             require(2 ** 96 > prod1);

574:             prod0 |= prod1 * 2 ** 160;

587:             if (mulmod(a, b, 2 ** 96) > 0) {

624:             require(2 ** 128 > prod1);

651:             prod0 |= prod1 * 2 ** 128;

664:             if (mulmod(a, b, 2 ** 128) > 0) {

701:             require(2 ** 192 > prod1);

728:             prod0 |= prod1 * 2 ** 64;

```

[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L15), [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L484), [511](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L511), [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L547), [574](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L574), [587](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L587), [624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L624), [651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L651), [664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L664), [701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L701), [728](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L728). 

```solidity
File: libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

560:                         2 ** 128,

685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

```

[23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L23), [512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L512), [514](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L514), [553](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L553), [560](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L560), [685](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L685). 

```solidity
File: types/TokenId.sol

98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

376:             if (optionRatios < 2 ** 64) {

378:             } else if (optionRatios < 2 ** 112) {

380:             } else if (optionRatios < 2 ** 160) {

382:             } else if (optionRatios < 2 ** 208) {

439:         if (optionRatios < 2 ** 64) {

441:         } else if (optionRatios < 2 ** 112) {

443:         } else if (optionRatios < 2 ** 160) {

445:         } else if (optionRatios < 2 ** 208) {

```

[98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L98), [376](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L376), [378](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L378), [380](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L380), [382](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L382), [439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L439), [441](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L441), [443](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L443), [445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L445). 

</details>

## [N-26] Complex casting

Consider whether the number of casts is really necessary, or whether using a different type would be more appropriate. Alternatively, add comments to explain in detail why the casts are necessary.

<details>
<summary><i>There are 6 instance of this issue:</i></summary>

```solidity
File: PanopticPool.sol

476:                     portfolioPremium = portfolioPremium.add(
477:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478:                     );

1650:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(
1651:                 LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))
1652:             );

1866:                         settledTokens = LeftRightUnsigned.wrap(
1867:                             uint256(
1868:                                 LeftRightSigned.unwrap(
1869:                                     LeftRightSigned
1870:                                         .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1871:                                         .sub(legPremia)
1872:                                 )
1873:                             )
1874:                         );

1900:                     realizedPremia = realizedPremia.add(
1901:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1902:                     );

```

[476](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L476-L478), [1650](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1650-L1652), [1866](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1866-L1874), [1900](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1900-L1902). 

```solidity
File: SemiFungiblePositionManager.sol

1148:         (, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, , ) = univ3pool
1149:             .positions(
1150:                 keccak256(
1151:                     abi.encodePacked(
1152:                         address(this),
1153:                         liquidityChunk.tickLower(),
1154:                         liquidityChunk.tickUpper()
1155:                     )
1156:                 )
1157:             );

1492:                     amountToCollect = LeftRightUnsigned.wrap(
1493:                         uint256(
1494:                             LeftRightSigned.unwrap(feesBase.subRect(s_accountFeesBase[positionKey]))
1495:                         )
1496:                     );

```

[1148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1148-L1157), [1492](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1492-L1496). 

</details>

## [N-27] Unbounded loop may run out of gas

Consider limiting the number of iterations in loops with an explicit revert reason to improve the user experience.

The function would eventually revert if out of gas anyway, but by limiting it the user avoids wasting too much gas, as the loop doesn't execute if an excessive value is provided.

<details>
<summary><i>There are 8 instance of this issue:</i></summary>

```solidity
File: PanopticPool.sol

802:         for (uint256 i = 0; i < positionIdList.length; ) {

```

[802](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L802). 

```solidity
File: SemiFungiblePositionManager.sol

575:         for (uint256 i = 0; i < ids.length; ) {

```

[575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L575). 

```solidity
File: libraries/FeesCalc.sol

51:         for (uint256 k = 0; k < positionIdList.length; ) {

```

[51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L51). 

```solidity
File: libraries/PanopticMath.sol

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

```

[781](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L781), [860](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L860). 

```solidity
File: multicall/Multicall.sol

14:         for (uint256 i = 0; i < data.length; ) {

```

[14](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L14). 

```solidity
File: tokens/ERC1155Minimal.sol

143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {

```

[143](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L143), [187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L187). 

</details>

## [N-28] Private and internal functions should start with an underscore

Underscore shows that the variable is private or internal. Remove the underscore prefix to make the code more readable.

<details>
<summary><i>There are 104 instance of this issue:</i></summary>

```solidity
File: PanopticPool.sol

1450:     function getUniV3TWAP() internal view returns (int24 twapTick) {

```

[1450](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1450). 

```solidity
File: SemiFungiblePositionManager.sol

320:     function beginReentrancyLock(uint64 poolId) internal {

330:     function endReentrancyLock(uint64 poolId) internal {

593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

756:     function swapInAMM(

```

[320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L320), [330](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L330), [593](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593), [756](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L756). 

```solidity
File: libraries/CallbackLib.sol

30:     function validateCallback(

```

[30](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L30). 

```solidity
File: libraries/Math.sol

25:     function min24(int24 a, int24 b) internal pure returns (int24) {

33:     function max24(int24 a, int24 b) internal pure returns (int24) {

41:     function min(uint256 a, uint256 b) internal pure returns (uint256) {

49:     function min(int256 a, int256 b) internal pure returns (int256) {

57:     function max(uint256 a, uint256 b) internal pure returns (uint256) {

65:     function max(int256 a, int256 b) internal pure returns (int256) {

73:     function abs(int256 x) internal pure returns (int256) {

81:     function absUint(int256 x) internal pure returns (uint256) {

91:     function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {

128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {

191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

221:     function getAmountsForLiquidity(

241:     function getLiquidityForAmount0(

271:     function getLiquidityForAmount1(

296:     function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

340:     function mulDiv(

440:     function mulDivRoundingUp(

458:     function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521:     function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

584:     function mulDiv96RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

598:     function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

661:     function mulDiv128RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

675:     function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

738:     function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

753:     function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {

776:     function sort(int256[] memory data) internal pure returns (int256[] memory) {

```

[25](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L33), [41](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L41), [49](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L57), [65](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L65), [73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L73), [81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L81), [91](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L91), [128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L128), [191](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L191), [207](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L207), [221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L221), [241](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L241), [271](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L271), [296](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L296), [302](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L302), [311](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L311), [318](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L318), [325](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L325), [340](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L340), [440](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L440), [458](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L521), [584](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L584), [598](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L598), [661](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L661), [675](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L675), [738](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L738), [753](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L753), [776](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L776). 

```solidity
File: libraries/PanopticMath.sol

47:     function getPoolId(address univ3pool) internal view returns (uint64) {

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

92:     function updatePositionsHash(

289:     function getLiquidityChunk(

338:     function getTicks(

371:     function getRangesFromStrike(

390:     function computeExercisedAmounts(

419:     function convertCollateralData(

445:     function convertCollateralData(

468:     function convertNotional(

490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

574:     function getAmountsMoved(

```

[47](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L47), [59](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L59), [92](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L92), [289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L289), [338](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L338), [371](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L371), [390](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L390), [419](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L419), [445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L445), [468](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L468), [490](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L490), [507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L507), [524](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L524), [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L547), [574](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L574). 

```solidity
File: libraries/SafeTransferLib.sol

21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:     function safeTransfer(address token, address to, uint256 amount) internal {

```

[21](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L21), [52](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L52). 

```solidity
File: types/LeftRight.sol

39:     function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46:     function rightSlot(LeftRightSigned self) internal pure returns (int128) {

59:     function toRightSlot(

78:     function toRightSlot(

101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

121:     function toLeftSlot(

134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

148:     function add(

171:     function sub(

194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

214:     function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

251:     function subRect(

279:     function addCapped(

```

[39](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L39), [46](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L46), [59](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L59), [78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L78), [101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L101), [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L108), [121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L121), [134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L134), [148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L148), [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L171), [194](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L194), [214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L232), [251](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L251), [279](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L279). 

```solidity
File: types/LiquidityChunk.sol

70:     function createChunk(

89:     function addLiquidity(

102:     function addTickLower(

118:     function addTickUpper(

135:     function updateTickLower(

151:     function updateTickUpper(

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```

[70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L70), [89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L89), [102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L102), [118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L118), [135](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L135), [151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L151), [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L171), [180](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L180), [189](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L189). 

```solidity
File: types/TokenId.sol

87:     function poolId(TokenId self) internal pure returns (uint64) {

96:     function tickSpacing(TokenId self) internal pure returns (int24) {

108:     function asset(TokenId self, uint256 legIndex) internal pure returns (uint256) {

118:     function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {

128:     function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {

138:     function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {

148:     function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {

158:     function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

169:     function width(TokenId self, uint256 legIndex) internal pure returns (int24) {

183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

205:     function addAsset(

221:     function addOptionRatio(

240:     function addIsLong(

255:     function addTokenType(

273:     function addRiskPartner(

291:     function addStrike(

310:     function addWidth(

336:     function addLeg(

366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

404:     function countLongs(TokenId self) internal pure returns (uint256) {

416:     function asTicks(

432:     function countLegs(TokenId self) internal pure returns (uint256) {

464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

500:     function validate(TokenId self) internal pure {

578:     function validateIsExercisable(TokenId self, int24 currentTick) internal pure {

```

[87](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L87), [96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L96), [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L108), [118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L118), [128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L128), [138](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L138), [148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L148), [158](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L158), [169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L169), [183](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L183), [193](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L193), [205](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L205), [221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L221), [240](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L240), [255](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L255), [273](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L273), [291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L291), [310](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L310), [336](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L336), [366](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L366), [404](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L404), [416](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L416), [432](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L432), [464](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L464), [500](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L500), [578](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L578). 

</details>

## [N-29] Consider using `delete` rather than assigning zero to clear values

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

<details>
<summary><i>There is 1 instance of this issue:</i></summary>

```solidity
File: SemiFungiblePositionManager.sol

332:         s_poolContext[poolId].locked = false;

```

[332](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L332). 

</details>

## [N-30] Incorrect NatSpec comment style

NatSpec must begin with `///`, or use `/* ... */` syntax

<details>
<summary><i>There are 6 instance of this issue:</i></summary>

```solidity
File: SemiFungiblePositionManager.sol

358:         // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting

360:         // @dev some pools may not be deployable if the poolId has a collision (since we take only 8 bytes)

603:             // @dev see `contracts/types/LiquidityChunk.sol`

836:             // @dev note this triggers our swap callback function

903:                 // @dev see `contracts/types/LiquidityChunk.sol`

```

[358](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L358), [360](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L360), [603](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L603), [836](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L836), [903](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L903). 

```solidity
File: libraries/PanopticMath.sol

98:         // @dev 0 ^ x = x

```

[98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L98). 

</details>

## [N-31] Inline private functions that are only used once

Private functions that are only used once should be inlined to save gas.

<details>
<summary><i>There is 1 instance of this issue:</i></summary>

```solidity
File: SemiFungiblePositionManager.sol

1110:     function _updateStoredPremia(

```

[1110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1110). 

</details>

## [N-32] `type(T).max` is inclusive

`type(T).max` is inclusive, i.e., it is the greatest number that can be represented with type `T`. Strictly speaking, it can and should therefore be used consistently with `<=` instead of `<`.

<details>
<summary><i>There are 7 instance of this issue:</i></summary>

```solidity
File: libraries/Math.sol

448:                 require(result < type(uint256).max);

588:                 require(result < type(uint256).max);

665:                 require(result < type(uint256).max);

```

[448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448), [588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588), [665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665). 

```solidity
File: libraries/PanopticMath.sol

494:             if (sqrtPriceX96 < type(uint128).max) {
495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
496:             } else {
497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
498:             }

511:             if (sqrtPriceX96 < type(uint128).max) {
512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
513:             } else {
514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
515:             }

528:             if (sqrtPriceX96 < type(uint128).max) {
529:                 int256 absResult = Math
530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
531:                     .toInt256();
532:                 return amount < 0 ? -absResult : absResult;
533:             } else {
534:                 int256 absResult = Math
535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
536:                     .toInt256();
537:                 return amount < 0 ? -absResult : absResult;
538:             }

551:             if (sqrtPriceX96 < type(uint128).max) {
552:                 int256 absResult = Math
553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
554:                     .toInt256();
555:                 return amount < 0 ? -absResult : absResult;
556:             } else {
557:                 int256 absResult = Math
558:                     .mulDiv(
559:                         Math.absUint(amount),
560:                         2 ** 128,
561:                         Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
562:                     )
563:                     .toInt256();
564:                 return amount < 0 ? -absResult : absResult;
565:             }

```

[494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L494-L498), [511](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L511-L515), [528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L528-L538), [551](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L551-L565). 

</details>

## [N-33] Custom error has no error information

<details>
<summary><i>There are 34 instance of this issue:</i></summary>

```solidity
File: libraries/Errors.sol

10:     error CastingError();

13:     error CollateralTokenAlreadyInitialized();

16:     error DepositTooLarge();

20:     error EffectiveLiquidityAboveThreshold();

23:     error ExceedsMaximumRedemption();

26:     error ExerciseeNotSolvent();

29:     error InputListFail();

32:     error InvalidSalt();

35:     error InvalidTick();

38:     error InvalidNotionalValue();

45:     error InvalidUniswapCallback();

48:     error LeftRightInputError();

51:     error NoLegsExercisable();

54:     error NotEnoughCollateral();

57:     error PositionTooLarge();

60:     error NotALongLeg();

63:     error NotEnoughLiquidity();

66:     error NotMarginCalled();

70:     error NotOwner();

73:     error NotPanopticPool();

76:     error OptionsBalanceZero();

79:     error PoolAlreadyInitialized();

82:     error PositionAlreadyMinted();

85:     error PositionCountNotZero();

88:     error PriceBoundFail();

91:     error ReentrantCall();

95:     error StaleTWAP();

98:     error TooManyPositionsOpen();

101:     error TransferFailed();

105:     error TicksNotInitializable();

108:     error UnderOverFlow();

111:     error UniswapPoolNotInitialized();

```

[10](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L10), [13](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L13), [16](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L16), [20](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L20), [23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L26), [29](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L29), [32](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L32), [35](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L35), [38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L38), [45](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L45), [48](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L48), [51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L51), [54](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L54), [57](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L57), [60](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L60), [63](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L73), [76](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L76), [79](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L79), [82](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L82), [85](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L85), [88](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L88), [91](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L91), [95](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L95), [98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L98), [101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L105), [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L108), [111](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L111). 

```solidity
File: tokens/ERC1155Minimal.sol

55:     error NotAuthorized();

58:     error UnsafeRecipient();

```

[55](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L55), [58](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L58). 

</details>

## [N-34] Unsigned divisions can be marked as unchecked

Divisions which do not divide by -1 cannot overflow or overflow so such operations can be unchecked to save gas

<details>
<summary><i>There is 1 instance of this issue:</i></summary>

```solidity
File: libraries/Math.sol

176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

[176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L176). 

</details>

## [N-35] `require()`/`revert()` statements should have descriptive reason strings

<details>
<summary><i>There are 9 instance of this issue:</i></summary>

```solidity
File: libraries/Math.sol

361:                 require(denominator > 0);

370:             require(denominator > prod1);

448:                 require(result < type(uint256).max);

484:             require(2 ** 64 > prod1);

547:             require(2 ** 96 > prod1);

588:                 require(result < type(uint256).max);

624:             require(2 ** 128 > prod1);

665:                 require(result < type(uint256).max);

701:             require(2 ** 192 > prod1);

```

[361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L370), [448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448), [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L484), [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L547), [588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588), [624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L624), [665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665), [701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L701). 

</details>

## [N-36] `else` block not required

One level of nesting can be removed by not having an else block when the if-block returns:

<details>
<summary><i>There are 6 instance of this issue:</i></summary>

```solidity
File: libraries/PanopticMath.sol

325:         if (tokenId.asset(legIndex) == 0) {
326:             return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
327:         } else {
328:             return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
329:         }

425:         if (tokenType == 0) {
426:             return (
427:                 tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
428:                 tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
429:             );
430:         } else {
431:             return (
432:                 tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
433:                 tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
434:             );
435:         }

494:             if (sqrtPriceX96 < type(uint128).max) {
495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
496:             } else {
497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
498:             }

511:             if (sqrtPriceX96 < type(uint128).max) {
512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
513:             } else {
514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
515:             }

528:             if (sqrtPriceX96 < type(uint128).max) {
529:                 int256 absResult = Math
530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
531:                     .toInt256();
532:                 return amount < 0 ? -absResult : absResult;
533:             } else {
534:                 int256 absResult = Math
535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
536:                     .toInt256();
537:                 return amount < 0 ? -absResult : absResult;
538:             }

551:             if (sqrtPriceX96 < type(uint128).max) {
552:                 int256 absResult = Math
553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
554:                     .toInt256();
555:                 return amount < 0 ? -absResult : absResult;
556:             } else {
557:                 int256 absResult = Math
558:                     .mulDiv(
559:                         Math.absUint(amount),
560:                         2 ** 128,
561:                         Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
562:                     )
563:                     .toInt256();
564:                 return amount < 0 ? -absResult : absResult;
565:             }

```

[325](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L325-L329), [425](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L425-L435), [494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L494-L498), [511](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L511-L515), [528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L528-L538), [551](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L551-L565). 

</details>

## [N-37] Setters should have initial value check

Setters should have initial value check to prevent assigning wrong value to the variable. Assignment of wrong value can lead to unexpected behavior of the contract.

<details>
<summary><i>There is 1 instance of this issue:</i></summary>

```solidity
File: tokens/ERC1155Minimal.sol

80:     /// @audit Not validated: operator

81:     function setApprovalForAll(address operator, bool approved) public {
82:         isApprovedForAll[msg.sender][operator] = approved;
83: 
84:         emit ApprovalForAll(msg.sender, operator, approved);
85:     }

```

[81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L81-L85). 

</details>

## [N-38] Setters should prevent re-setting of the same value

This especially problematic when the setter also emits the same value, which may be confusing to offline parsers

<details>
<summary><i>There is 1 instance of this issue:</i></summary>

```solidity
File: tokens/ERC1155Minimal.sol

81:     function setApprovalForAll(address operator, bool approved) public {
82:         isApprovedForAll[msg.sender][operator] = approved;
83: 
84:         emit ApprovalForAll(msg.sender, operator, approved);
85:     }

```

[81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L81-L85). 

</details>

## [N-39] Event missing `msg.sender` information

In scenarios where actions are initiated by users, the absence of the ability to filter events based on the initiator of the action can significantly complicate event processing. By including the `msg.sender` in events associated with such actions, events become considerably more valuable for end users, particularly when `msg.sender` differs from `tx.origin`.

<details>
<summary><i>There are 4 instance of this issue:</i></summary>

```solidity
File: tokens/ERC20Minimal.sol

94:         emit Transfer(from, to, amount);

112:         emit Transfer(from, to, amount);

130:         emit Transfer(address(0), to, amount);

145:         emit Transfer(from, address(0), amount);

```

[94](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L94), [112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L112), [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L130), [145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L145). 

</details>

## [N-40] Typos in the code

<details>
<summary><i>There are 17 instance of this issue:</i></summary>

```solidity
File: types/LeftRight.sol

152:             /// @audit explicitly
153:             // adding leftRight packed uint128's is same as just adding the values explictily

158:             /// @audit occurred
159:             // then an overflow has occured

175:             /// @audit explicitly
176:             // subtracting leftRight packed uint128's is same as just subtracting the values explictily

181:             /// @audit occurred
182:             // then an underflow has occured

```

[153](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L153), [159](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L159), [176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L176), [182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L182). 

```solidity
File: PanopticPool.sol

106:     /// @audit calculation
107:     // Flags used as arguments to premia caluculation functions

121:     /// @audit weather
122:     /// @dev Boolean flag to determine wether a position is added (true) or not (!ADD = false)

277:     /// @audit Manager
278:     /// @notice During construction: sets the address of the panoptic factory smart contract and the SemiFungiblePositionMananger (SFPM).

```

[107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L107), [122](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L122), [278](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L278). 

```solidity
File: CollateralTracker.sol

91:     /// @audit initialized
92:     /// @dev As each instance is deployed via proxy clone, initial parameters must only be initalized once via startToken().

```

[92](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L92). 

```solidity
File: libraries/Errors.sol

61:     /// @audit available
62:     /// @notice PanopticPool: there is not enough avaiable liquidity to buy an option

```

[62](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L62). 

```solidity
File: SemiFungiblePositionManager.sol

1105:     /// @audit position
1106:     /// @notice caches/stores the accumulated premia values for the specified postion.

1336:         /// @audit separated
1337:         // premia, and is only seperated to simplify the calculation

```

[1106](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1106), [1337](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1337). 

```solidity
File: libraries/PanopticMath.sol

485:     /// @audit accommodate
486:     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of tick.s

502:     /// @audit accommodate
503:     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.

519:     /// @audit accommodate
520:     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.

542:     /// @audit accommodate
543:     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.

662:                 /// @audit consistently
663:                 // evaluate at TWAP price to keep consistentcy with solvency calculations

885:                         /// @audit committed
886:                         // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount

```

[486](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L486), [503](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L503), [520](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L520), [543](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L543), [663](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L663), [886](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L886). 

</details>

## [N-41] Function ordering does not follow the Solidity style guide

Source: https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-layout

<details>
<summary><i>There are 2 instance of this issue:</i></summary>

```solidity
File: libraries/PanopticMath.sol

74:     /// @audit External pure function can not go after internal pure function 
75:     function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

```

[75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L75). 

```solidity
File: tokens/interfaces/IERC20Partial.sol

21:     /// @audit External function can not go after external view function 
22:     function approve(address spender, uint256 amount) external;

```

[22](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IERC20Partial.sol#L22). 

</details>

## [N-42] Contract does not follow the Solidity style guide's suggested layout ordering

Inside each contract, library or interface, use the following order:

1. Type declarations
2. State variables
3. Events
4. Errors
5. Modifiers
6. Functions

Source: https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-layout

<details>
<summary><i>There are 6 instance of this issue:</i></summary>

```solidity
File: SemiFungiblePositionManager.sol

108:     /// @audit Using for declaration can not go after event definition 
109:     using Math for uint256;

```

[109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L109). 

```solidity
File: CollateralTracker.sol

69:     /// @audit State variable declaration can not go after event definition 
70:     string internal constant TICKER_PREFIX = "po";

```

[70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L70). 

```solidity
File: PanopticPool.sol

102:     /// @audit State variable declaration can not go after event definition 
103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

```

[103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L103). 

```solidity
File: PanopticFactory.sol

55:     /// @audit Using for declaration can not go after event definition 
56:     using Clones for address;

```

[56](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L56). 

```solidity
File: tokens/ERC20Minimal.sol

31:     /// @audit State variable declaration can not go after event definition 
32:     uint256 public totalSupply;

```

[32](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L32). 

```solidity
File: tokens/ERC1155Minimal.sol

65:     /// @audit State variable declaration can not go after custom error definition 
66:     mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;

```

[66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L66). 

</details>

## [N-43] Private and internal variables should start with an underscore

Source: https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables.

<details>
<summary><i>There are 93 instance of this issue:</i></summary>

```solidity
File: SemiFungiblePositionManager.sol

125:     bool internal constant MINT = false;

126:     bool internal constant BURN = true;

133:     uint128 private constant VEGOID = 2;

137:     IUniswapV3Factory internal immutable FACTORY;

145:     mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;

150:     mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;

177:     mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)

287:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

295:     mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;

```

[125](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L125), [126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L126), [133](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L133), [137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L137), [145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L145), [150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L150), [177](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L177), [287](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L287), [289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L289), [295](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L295). 

```solidity
File: CollateralTracker.sol

70:     string internal constant TICKER_PREFIX = "po";

73:     string internal constant NAME_PREFIX = "POPT-V1";

77:     uint256 internal constant DECIMALS = 10_000;

81:     int128 internal constant DECIMALS_128 = 10_000;

89:     address internal s_underlyingToken;

93:     bool internal s_initialized;

96:     address internal s_univ3token0;

99:     address internal s_univ3token1;

102:     bool internal s_underlyingIsToken0;

109:     PanopticPool internal s_panopticPool;

112:     uint128 internal s_poolAssets;

115:     uint128 internal s_inAMM;

121:     uint128 internal s_ITMSpreadFee;

124:     uint24 internal s_poolFee;

131:     uint256 immutable TICK_DEVIATION;

136:     uint256 immutable COMMISSION_FEE;

141:     uint256 immutable SELLER_COLLATERAL_RATIO;

145:     uint256 immutable BUYER_COLLATERAL_RATIO;

149:     int256 immutable FORCE_EXERCISE_COST;

154:     uint256 immutable TARGET_POOL_UTIL;

158:     uint256 immutable SATURATED_POOL_UTIL;

162:     uint256 immutable ITM_SPREAD_MULTIPLIER;

```

[70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L73), [77](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L81), [89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L89), [93](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L93), [96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L109), [112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L112), [115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L115), [121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L121), [124](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L124), [131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L131), [136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L136), [141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L141), [145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L145), [149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L149), [154](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L154), [158](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L158), [162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L162). 

```solidity
File: PanopticPool.sol

103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

109:     bool internal constant COMPUTE_ALL_PREMIA = true;

111:     bool internal constant COMPUTE_LONG_PREMIA = false;

114:     bool internal constant ONLY_AVAILABLE_PREMIUM = false;

119:     bool internal constant COMMIT_LONG_SETTLED = true;

120:     bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

123:     bool internal constant ADD = true;

128:     uint32 internal constant TWAP_WINDOW = 600;

133:     bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;

136:     uint256 internal constant MEDIAN_PERIOD = 60;

139:     uint256 internal constant FAST_ORACLE_CARDINALITY = 3;

145:     uint256 internal constant FAST_ORACLE_PERIOD = 1;

148:     uint256 internal constant SLOW_ORACLE_CARDINALITY = 7;

152:     uint256 internal constant SLOW_ORACLE_PERIOD = 5;

156:     int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;

160:     int256 internal constant MAX_SLOW_FAST_DELTA = 1800;

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

168:     uint64 internal constant MAX_POSITIONS = 32;

171:     uint256 internal constant BP_DECREASE_BUFFER = 13_333;

174:     uint256 internal constant NO_BUFFER = 10_000;

179:     SemiFungiblePositionManager internal immutable SFPM;

186:     IUniswapV3Pool internal s_univ3pool;

225:     uint256 internal s_miniMedian;

231:     CollateralTracker internal s_collateralToken0;

233:     CollateralTracker internal s_collateralToken1;

238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

245:     mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

251:     mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;

258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))

272:     mapping(address account => uint256 positionsHash) internal s_positionsHash;

```

[103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L109), [111](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L111), [114](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L114), [119](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L119), [120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L120), [123](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L123), [128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L128), [133](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L133), [136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L136), [139](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L139), [145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L145), [148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L148), [152](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L152), [156](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L156), [160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L160), [165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L165), [168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L168), [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L171), [174](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L174), [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L179), [186](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L186), [225](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L225), [231](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L231), [233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L233), [238](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L238), [245](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L245), [251](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L251), [258](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L258), [272](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L272). 

```solidity
File: PanopticFactory.sol

63:     IUniswapV3Factory internal immutable UNIV3_FACTORY;

66:     SemiFungiblePositionManager internal immutable SFPM;

69:     IDonorNFT internal immutable DONOR_NFT;

72:     address internal immutable POOL_REFERENCE;

75:     address internal immutable COLLATERAL_REFERENCE;

78:     address internal immutable WETH;

82:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;

86:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

89:     uint16 internal constant CARDINALITY_INCREASE = 100;

96:     address internal s_owner;

99:     bool internal s_initialized;

102:     mapping(IUniswapV3Pool univ3pool => PanopticPool panopticPool) internal s_getPanopticPool;

```

[63](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L66), [69](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L69), [72](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L72), [75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L75), [78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L78), [82](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L82), [86](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L86), [89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L89), [96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L102). 

```solidity
File: libraries/Constants.sol

9:     uint256 internal constant FP96 = 0x1000000000000000000000000;

12:     int24 internal constant MIN_V3POOL_TICK = -887272;

15:     int24 internal constant MAX_V3POOL_TICK = 887272;

18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

21:     uint160 internal constant MAX_V3POOL_SQRT_RATIO =

```

[9](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L9), [12](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L12), [15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L15), [18](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L18), [21](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L21). 

```solidity
File: libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

26:     uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

```

[23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L26). 

```solidity
File: libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```

[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L15). 

```solidity
File: types/LeftRight.sol

22:     uint256 internal constant LEFT_HALF_BIT_MASK =

26:     int256 internal constant LEFT_HALF_BIT_MASK_INT =

30:     int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```

[22](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L22), [26](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L26), [30](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L30). 

```solidity
File: types/TokenId.sol

62:     uint256 internal constant LONG_MASK =

66:     uint256 internal constant CLEAR_POOLID_MASK =

70:     uint256 internal constant OPTION_RATIO_MASK =

74:     uint256 internal constant CHUNK_MASK =

78:     int256 internal constant BITMASK_INT24 = 0xFFFFFF;

```

[62](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L62), [66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L70), [74](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L74), [78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L78). 

```solidity
File: types/LiquidityChunk.sol

54:     uint256 internal constant CLEAR_TL_MASK =

58:     uint256 internal constant CLEAR_TU_MASK =

```

[54](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L54), [58](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L58). 

</details>

## [N-44] Imports could be organized more systematically

The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

<details>
<summary><i>There are 5 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

5: import {PanopticPool} from "./PanopticPool.sol";

```

[5](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L5). 

```solidity
File: PanopticFactory.sol

5: import {CollateralTracker} from "@contracts/CollateralTracker.sol";

```

[5](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L5). 

```solidity
File: PanopticPool.sol

5: import {CollateralTracker} from "@contracts/CollateralTracker.sol";

```

[5](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L5). 

```solidity
File: SemiFungiblePositionManager.sol

5: import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

```

[5](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L5). 

```solidity
File: tokens/ERC1155Minimal.sol

5: import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";

```

[5](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L5). 

</details>

## [N-45] Contract name should match filename

The name of the contract [should](https://docs.soliditylang.org/en/latest/style-guide.html#contract-and-library-names) match the filename.

<details>
<summary><i>There is 1 instance of this issue:</i></summary>

```solidity
File: tokens/ERC1155Minimal.sol

11: abstract contract ERC1155 {

```

[11](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L11). 

</details>

## [N-46] Constant redefined elsewhere

Consider defining in only one contract so that values cannot become out of sync when only one location is updated. A [cheap way](https://medium.com/coinmonks/gas-cost-of-solidity-library-functions-dbe0cedd4678) to store constants in a single location is to create an `internal constant` in a `library`. If the variable is a local cache of another contract’s value, consider making the cache variable internal or private, which will require external users to query the contract with the source of truth, so that callers don’t get out of sync.

<details>
<summary><i>There are 2 instance of this issue:</i></summary>

```solidity
File: libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```

[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L15). 

```solidity
File: libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```

[23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L23). 

</details>

## [N-47] Duplicated `require`/`if` checks should be refactored to a modifier or function

This saves deployment gas cost.

<details>
<summary><i>There are 15 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

```

[418](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L418), [480](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L480). 

```solidity
File: libraries/Math.sol

448:                 require(result < type(uint256).max);

588:                 require(result < type(uint256).max);

665:                 require(result < type(uint256).max);

```

[448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448), [588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588), [665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665). 

```solidity
File: tokens/ERC1155Minimal.sol

101:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

117:                 revert UnsafeRecipient();

168:                 revert UnsafeRecipient();

227:                 revert UnsafeRecipient();

```

[101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L101), [137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L137), [117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L117), [168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L168), [227](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L227). 

```solidity
File: types/LeftRight.sol

163:             ) revert Errors.UnderOverFlow();

186:             ) revert Errors.UnderOverFlow();

222:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

240:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

262:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

```

[163](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L163), [186](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L186), [222](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L222), [240](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L240), [262](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L262). 

</details>

## [N-48] Non-library/interface files should use fixed compiler versions, not floating ones

Contracts should be deployed with the same compiler version and flags that have been thoroughly tested. Specifying and locking the pragma directive helps ensure that contracts are not accidentally deployed using an outdated compiler version, which could introduce bugs that negatively impact the contract system.

Source: https://swcregistry.io/docs/SWC-103

<details>
<summary><i>There are 7 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L2). 

```solidity
File: PanopticFactory.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L2). 

```solidity
File: PanopticPool.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L2). 

```solidity
File: SemiFungiblePositionManager.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L2). 

```solidity
File: multicall/Multicall.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L2). 

```solidity
File: tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2). 

```solidity
File: tokens/ERC20Minimal.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L2). 

</details>

## [N-49] Use a more recent version of Solidity

Use a solidity version of at least 0.8.2 to get simple compiler automatic inlining.

Use a solidity version of at least 0.8.3 to get better struct packing and cheaper multiple storage reads.

Use a solidity version of at least 0.8.4 to get custom errors, which are cheaper at deployment than revert()/require() strings.

Use a solidity version of at least 0.8.10 to have external calls skip contract existence checks if the external call has a return value

Use a solidity version of at least 0.8.12 to get string.concat() instead of abi.encodePacked(<str>,<str>).

<details>
<summary><i>There are 7 instance of this issue:</i></summary>

```solidity
File: CollateralTracker.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L2). 

```solidity
File: PanopticFactory.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L2). 

```solidity
File: PanopticPool.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L2). 

```solidity
File: SemiFungiblePositionManager.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L2). 

```solidity
File: multicall/Multicall.sol

2: pragma solidity ^0.8.18;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L2). 

```solidity
File: tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2). 

```solidity
File: tokens/ERC20Minimal.sol

2: pragma solidity ^0.8.0;

```

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L2). 

</details>
