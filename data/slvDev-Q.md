## Low Findings

|    | Issue | Instances |
|----|-------|:---------:|
| [L-01] | Centralization issue caused by admin privileges | 7 |
| [L-02] | Subtraction may underflow if multiplication is too large | 10 |
| [L-03] | `decimals()` is not part of the ERC20 standard | 1 |
| [L-04] | Code does not follow the best practice of check-effects-interaction | 7 |
| [L-05] | Initializers can be front-run | 2 |
| [L-06] | Prefer skip over `revert` model in loops | 12 |
| [L-07] | Unbounded loop may run out of gas | 8 |
| [L-08] | Lack of index element validation in external/public function | 37 |
| [L-09] | Consider checking that transfer to `address(this)` is disabled | 6 |
| [L-10] | Possible reentrancy with callback on transfer tokens | 7 |
| [L-11] | Prevent Division by Zero | 2 |
| [L-12] | Solidity version 0.8.20 may not work on other chains due to `PUSH0` | 11 |
| [L-13] | Ensure `payable` Functions Properly Handle Ether Transfers | 1 |
| [L-14] | Lack of Parameter Validation in Constructor/Initializer | 1 |
| [L-15] | Mint to zero address | 1 |
| [L-16] | External calls in an un-bounded `for-`loop may result in a DOS | 33 |
| [L-17] | Input Arrays Lengths Not Checked | 2 |
| [L-18] | Avoid Using `delegatecall` in Loops | 1 |
| [L-19] | Loss of precision | 3 |
| [L-20] | File allows a version of solidity that is susceptible to an assembly optimizer bug | 4 |
| [L-21] | Unsafe Conversion from Unsigned to Signed Integers | 4 |
| [L-22] | Unsafe downcast | 30 |
| [L-23] | Possible Revert ERC20 Transfers with Zero Value | 3 |
| [L-24] | Missing `address(0)` Check in Constructor/Initializer | 1 |
| [L-25] | Functions calling tokens with transfer hooks are missing reentrancy guards | 3 |

## NonCritical Findings

|    | Issue | Instances |
|----|-------|:---------:|
| [N-01] | Subtraction in `unchecked` block is unsafe | 119 |
| [N-02] | `internal/private` Function calls within for loops | 16 |
| [N-03] | Non-library/interface files should use fixed compiler versions, not floating ones | 7 |
| [N-04] | Array indices should be referenced via `enum`s rather than via numeric literals | 44 |
| [N-05] | Consider splitting long calculations | 35 |
| [N-06] | Use custom errors instead of `require()/assert()` | 9 |
| [N-07] | Missing Event Emission After Critical Initialize() Function | 1 |
| [N-08] | Variables need not be initialized to zero | 31 |
| [N-09] | Variables need not be initialized to false | 5 |
| [N-10] | `require()/revert()` statements without reason strings | 9 |
| [N-11] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability | 13 |
| [N-12] | Consider returning a `struct` rather than having multiple `return` values | 7 |
| [N-13] | Consider using a `struct` rather than having many function input parameters | 41 |
| [N-14] | Consider using descriptive `constant`s when passing zero as a function argument | 61 |
| [N-15] | Custom error has no error details | 34 |
| [N-16] | Consider using OpenZeppelin's SafeCast for any casting | 373 |
| [N-17] | Consider using `delete` rather than assigning `zero` to clear values | 3 |
| [N-18] | Consider emitting an event at the end of the constructor | 4 |
| [N-19] | Consider moving duplicated strings to constants | 3 |
| [N-20] | Consider using named returns | 104 |
| [N-21] | Expressions for constant values should use `immutable` rather than `constant` | 6 |
| [N-22] | Consider using named function arguments | 169 |
| [N-23] | Assembly block creates dirty bits | 1 |
| [N-24] | Events in public function missing sender information | 1 |
| [N-25] | Leverage Recent Solidity Features with `0.8.21` | 13 |
| [N-26] | Custom error has no error details | 16 |
| [N-27] | High Cyclomatic Complexity in Functions | 4 |
| [N-28] | Contract should expose an `interface` | 23 |
| [N-29] | Inconsistent spacing in comments | 19 |
| [N-30] | Unused Custom Errors | 15 |
| [N-31] | Outdated Solidity Version | 13 |
| [N-32] | Ensure Non-Empty Check for Bytes in Function Parameters | 3 |
| [N-33] | Adding a `return` statement when the function defines a named return variable, is redundant | 2 |
| [N-34] | Assembly blocks should have extensive comments | 1 |
| [N-35] | Use `bytes.concat()` instead of `abi.encodePacked()` | 7 |
| [N-36] | Function/Constructor Argument Names Not in mixedCase | 14 |
| [N-37] | Upgrade `openzeppelin` to the Latest Version - 5.0.0 | 1 |
| [N-38] | Duplicated require()/revert() Checks | 4 |
| [N-39] | Event is not properly `indexed` | 3 |
| [N-40] | Consider Adding Emergency-Stop Functionality | 1 |
| [N-41] | Consider adding a block/deny-list | 1 |
| [N-42] | Inconsistent Use of Named Return Variables | 12 |
| [N-43] | Function Names Not in mixedCase | 7 |
| [N-44] | Insufficient Comments in Complex Functions | 8 |
| [N-45] | Error Declarations Missing Descriptions | 2 |
| [N-46] | `constant`s should be defined rather than using magic numbers | 83 |
| [N-47] | Variable Names Not in mixedCase | 14 |
| [N-48] | Consider Avoid Loops in Public Functions | 4 |
| [N-49] | Consider moving `msg.sender` checks to a common authorization `modifier` | 8 |
| [N-50] | `Solidity Style Guide`: Internal/Private Function Names Without Leading Underscores | 74 |
| [N-51] | Invalid NatSpec Comment Style | 7 |
| [N-52] | Consider defining system-wide constants in a single file | 3 |
| [N-53] | Consider using `delete` rather than assigning `false` to clear values | 1 |
| [N-54] | State Parameter Change Events Should Contain Both Old and New Values | 1 |
| [N-55] | `Solidity Style Guide`: Non-public Variable Names Without Leading Underscores | 22 |
| [N-56] | Layout Order Does Not Comply with `Solidity Style Guide` | 3 |
| [N-57] | Control Structures Not Complying with Best Practices | 42 |
| [N-58] | Consider bounding input array length | 4 |
| [N-59] | Constants in comparisons should appear on the left side | 71 |
| [N-60] | Large Numeric Literals Lack Underscores | 8 |
| [N-61] | Replace `constant` with `immutable` for calculated values | 2 |
| [N-62] | Consider Refactoring Long Functions | 8 |
| [N-63] | `public` functions not called by the contract should be declared `external` instead | 3 |
| [N-64] | Complex casting | 24 |
| [N-65] | Double Type Casting | 22 |
| [N-66] | `else`-block not required | 4 |
| [N-67] | Function Name Duplication is Discouraged for Security Audits | 15 |
| [N-68] | `Solidity Style Guide`: Function order not compliant | 6 |
| [N-69] | `Solidity Style Guide`: Lines are too long | 162 |
| [N-70] | Function Parameters in Public Accessible Functions Need `address(0)` Check | 9 |
| [N-71] | Contract/Libraries Names Do Not Match Their Filenames | 1 |
| [N-72] | Presence of Unutilized Imports in the Contract | 1 |
| [N-73] | `if`-statement can be converted to a ternary | 2 |
| [N-74] | Consider using `delete` rather than assigning zero to clear values | 3 |
| [N-75] | Unnecessary Use of `override` Keyword | 2 |
| [N-76] | Implement Value Comparison Checks in Setter Functions to Prevent Redundant State Updates | 5 |
| [N-77] | Contracts should have full test coverage | 1 |
| [N-78] | Insufficient Invariant Tests for Contracts | 1 |
| [N-79] | Implement Formal Verification Proofs to Improve Security | 1 |

## Low Findings Details

### [L-01] Centralization issue caused by admin privileges

There are priviliged roles that are a single point of failure, who can use critical functions, posing a centralization issue.

<details>
<summary><i>7 issue instances in 1 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

864: function delegate(
        address delegator,
        address delegatee,
        uint256 assets
    ) external onlyPanopticPool
894: function delegate(address delegatee, uint256 assets) external onlyPanopticPool
903: function refund(address delegatee, uint256 assets) external onlyPanopticPool
911: function revoke(
        address delegator,
        address delegatee,
        uint256 assets
    ) external onlyPanopticPool
975: function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool
995: function takeCommissionAddData(
        address optionOwner,
        int128 longAmount,
        int128 shortAmount,
        int128 swappedAmount
    ) external onlyPanopticPool returns (int256 utilization)
1043: function exercise(
        address optionOwner,
        int128 longAmount,
        int128 shortAmount,
        int128 swappedAmount,
        int128 realizedPremium
    ) external onlyPanopticPool returns (int128)
```
[864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L864) | [894](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L894) | [903](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L903) | [911](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L911) | [975](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L975) | [995](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L995) | [1043](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043)
</details>

### [L-02] Subtraction may underflow if multiplication is too large

he following expressions may underflow, as the subtrahend could be greater than the minuend in case the former is multiplied by a large number.

<details>
<summary><i>10 issue instances in 4 files:</i></summary>

```solidity
File: contracts/PanopticPool.sol

1935: (int256(
                                                    grossPremiumLast.rightSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][0] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
1952: (int256(
                                                    grossPremiumLast.leftSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][1] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
```
[1935](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1935) | [1952](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1952)

```solidity
File: contracts/SemiFungiblePositionManager.sol

1388: uint256 numerator = totalLiquidity ** 2 -
                        totalLiquidity *
                        removedLiquidity +
```
[1388](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1388)

```solidity
File: contracts/libraries/Math.sol

418: inv *= 2 - denominator * inv; // inverse mod 2**8
419: inv *= 2 - denominator * inv; // inverse mod 2**16
420: inv *= 2 - denominator * inv; // inverse mod 2**32
421: inv *= 2 - denominator * inv; // inverse mod 2**64
422: inv *= 2 - denominator * inv; // inverse mod 2**128
423: inv *= 2 - denominator * inv; // inverse mod 2**256
```
[418](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L418) | [419](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L419) | [420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L420) | [421](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L421) | [422](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L422) | [423](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L423)

```solidity
File: contracts/libraries/PanopticMath.sol

140: (int256(observationIndex) - int256(i * period)) +
```
[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140)
</details>

### [L-03] `decimals()` is not part of the ERC20 standard

The `decimals` function is not part of the `ERC20` standard, and they may revert with some tokens if the don't also extend the `IERC20Metadata` interface.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/libraries/InteractionHelper.sol

110: try IERC20Metadata(token).decimals() returns (uint8 _decimals) {
```
[110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L110)
</details>

### [L-04] Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [CEI](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

<details>
<summary><i>7 issue instances in 2 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

/// @audit - State change after external call: `SafeTransferLib.safeTransferFrom(s_underlyingToken, msg.sender, address(s_panopticPool), assets)`
436: s_poolAssets += uint128(assets)
/// @audit - State change after external call: `SafeTransferLib.safeTransferFrom(s_underlyingToken, msg.sender, address(s_panopticPool), assets)`
496: s_poolAssets += uint128(assets)
```
[436](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L436) | [496](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L496)

```solidity
File: contracts/PanopticPool.sol

/// @audit - State change after external call: `IUniswapV3Pool(_univ3pool).slot0()`
308: s_miniMedian =
                (uint256(block.timestamp) << 216) +
                // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
                // see comment on s_miniMedian initialization for format of this magic number
                (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
                (uint256(uint24(currentTick)) << 24) + // add to slot 4
                (uint256(uint24(currentTick)))
/// @audit - State change after external call: `s_univ3pool.slot0()`
390: (LeftRightSigned premia, uint256[2][] memory balances) = _calculateAccumulatedPremia(
            user,
            positionIdList,
            COMPUTE_ALL_PREMIA,
            includePendingPremium,
            currentTick
        )
/// @audit - State change after external call: `s_univ3pool.slot0()`
533: s_miniMedian = medianData
/// @audit - State change after external call: `s_univ3pool.slot0()`
1206: (LeftRightSigned positionPremia, ) = _calculateAccumulatedPremia(
                account,
                touchedId,
                COMPUTE_LONG_PREMIA,
                ONLY_AVAILABLE_PREMIUM,
                currentTick
            )
/// @audit - State change after external call: `s_univ3pool.slot0()`
1622: s_options[owner][tokenId][legIndex] = accumulatedPremium
```
[308](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L308) | [390](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L390) | [533](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L533) | [1206](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1206) | [1622](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1622)
</details>

### [L-05] Initializers can be front-run

Initializers could be vulnerable to front-running attacks.
This might allow an attacker to set their own values, take ownership of the contract, or force a redeployment in the best-case scenario.
Be cautious of potential front-running risks in the following instances found in the code.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: contracts/PanopticFactory.sol

134: function initialize(address _owner) public
```
[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134)

```solidity
File: contracts/SemiFungiblePositionManager.sol

350: function initializeAMMPool(address token0, address token1, uint24 fee) external
```
[350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350)
</details>

### [L-06] Prefer skip over `revert` model in loops

When dealing with array operations in Solidity, it's often wiser to opt for skipping over reverting.
Instead of halting the entire transaction when a condition isn't met, suggests simply moving on to the next array index.
The reason behind this choice is to reduce the risk of malicious actors intentionally introducing array objects that fail conditional checks within loops, causing group operations to fail.
Unless there's a compelling security or logical justification for reverting, it's recommended to embrace the skip-over approach for a more robust codebase.

<details>
<summary><i>12 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

576: revert Errors.ReentrantCall()
634: revert Errors.TransferFailed()
639: revert Errors.TransferFailed()
```
[576](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L576) | [634](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L634) | [639](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L639)

```solidity
File: contracts/types/TokenId.sol

513: revert Errors.InvalidTokenIdParameter(1)
522: revert Errors.InvalidTokenIdParameter(6)
528: revert Errors.InvalidTokenIdParameter(5)
533: revert Errors.InvalidTokenIdParameter(4)
542: revert Errors.InvalidTokenIdParameter(3)
548: revert Errors.InvalidTokenIdParameter(3)
561: revert Errors.InvalidTokenIdParameter(4)
567: revert Errors.InvalidTokenIdParameter(5)
522: revert Errors.InvalidTokenIdParameter(6)
```
[513](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L513) | [522](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L522) | [528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L528) | [533](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L533) | [542](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L542) | [548](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L548) | [561](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L561) | [567](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L567) | [522](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L522)
</details>

### [L-07] Unbounded loop may run out of gas

Unbounded loops in smart contracts pose a risk because they iterate over an unknown number of elements, potentially consuming all available gas for a transaction.
This can result in unintended transaction failures. Gas consumption increases linearly with the number of iterations, and if it surpasses the gas limit, the transaction reverts, wasting the gas spent.
To mitigate this, developers should either set a maximum limit on loop iterations.

<details>
<summary><i>8 issue instances in 6 files:</i></summary>

```solidity
File: contracts/PanopticPool.sol

802: for (uint256 i = 0; i < positionIdList.length; )
```
[802](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L802)

```solidity
File: contracts/SemiFungiblePositionManager.sol

575: for (uint256 i = 0; i < ids.length; )
```
[575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L575)

```solidity
File: contracts/libraries/FeesCalc.sol

51: for (uint256 k = 0; k < positionIdList.length; )
```
[51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L51)

```solidity
File: contracts/libraries/PanopticMath.sol

781: for (uint256 i = 0; i < positionIdList.length; ++i)
860: for (uint256 i = 0; i < positionIdList.length; i++)
```
[781](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L781) | [860](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L860)

```solidity
File: contracts/multicall/Multicall.sol

14: for (uint256 i = 0; i < data.length; )
```
[14](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L14)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

143: for (uint256 i = 0; i < ids.length; )
187: for (uint256 i = 0; i < owners.length; ++i)
```
[143](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L143) | [187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L187)
</details>

### [L-08] Lack of index element validation in external/public function

There's no validation to check whether the index element provided as an argument actually exists in the call. This omission could lead to unintended behavior if an element that does not exist in the call is passed to the function.

The function should validate that the provided index element exists in the call before proceeding.

Without this validation, the function could cause unintended behaviour as it will call an non-existing index element. This could lead to inconsistencies in data and potentially affect the integrity of the call structure.

<details>
<summary><i>37 issue instances in 6 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

511: balanceOf[owner]
542: allowance[owner]
544: allowance[owner]
574: balanceOf[owner]
600: allowance[owner]
602: allowance[owner]
895: balanceOf[delegatee]
904: balanceOf[delegatee]
933: balanceOf[delegatee]
```
[511](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L511) | [542](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L542) | [544](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L544) | [574](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L574) | [600](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L600) | [602](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L602) | [895](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L895) | [904](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L904) | [933](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L933)

```solidity
File: contracts/PanopticFactory.sol

421: s_getPanopticPool[univ3pool]
```
[421](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L421)

```solidity
File: contracts/PanopticPool.sol

357: s_positionBalance[user][tokenId]
357: s_positionBalance[user]
417: s_positionBalance[user]
1193: s_positionBalance[account]
1445: s_positionsHash[user]
1621: s_options[owner][tokenId][legIndex]
1621: s_options[owner]
1622: s_options[owner][tokenId][legIndex]
1622: s_options[owner]
1628: s_positionBalance[owner]
```
[357](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L357) | [357](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L357) | [417](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L417) | [1193](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1193) | [1445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1445) | [1621](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1621) | [1621](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1621) | [1622](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1622) | [1622](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1622) | [1628](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1628)

```solidity
File: contracts/SemiFungiblePositionManager.sol

1558: s_poolContext[poolId]
1567: s_AddrToPoolIdData[univ3pool]
```
[1558](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1558) | [1567](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1567)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

82: isApprovedForAll[msg.sender][operator]
101: isApprovedForAll[from]
103: balanceOf[from][id]
103: balanceOf[from]
107: balanceOf[to][id]
107: balanceOf[to]
137: isApprovedForAll[from]
147: balanceOf[from]
151: balanceOf[to]
```
[82](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L82) | [101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L101) | [103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L103) | [103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L103) | [107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L107) | [107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L107) | [137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L137) | [147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L147) | [151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L151)

```solidity
File: contracts/tokens/ERC20Minimal.sol

50: allowance[msg.sender][spender]
67: balanceOf[to]
82: allowance[from]
84: allowance[from]
86: balanceOf[from]
91: balanceOf[to]
```
[50](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L50) | [67](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L67) | [82](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L82) | [84](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L84) | [86](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L86) | [91](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L91)
</details>

### [L-09] Consider checking that transfer to `address(this)` is disabled

Functions allowing users to specify the receiving address should check whether the referenced address is not `address(this)`.

This would prevent tokens to remain lock inside the contract due to an incorrect `transfer` or `mint`.

<details>
<summary><i>6 issue instances in 1 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

333: ERC20Minimal.transfer(recipient, amount)
432: _mint(receiver, shares)
492: _mint(receiver, shares)
954: _mint(
                delegator,
                Math.mulDiv(
                    assets,
                    totalSupply - delegateeBalance,
                    uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
                ) - delegateeBalance
            )
1021: _mint(optionOwner, sharesToMint)
1078: _mint(optionOwner, sharesToMint)
```
[333](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L333) | [432](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L432) | [492](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L492) | [954](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L954) | [1021](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1021) | [1078](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1078)
</details>

### [L-10] Possible reentrancy with callback on transfer tokens

The following functions don't apply the CEI pattern. It's possible to reenter after the transfer if the token has some kind of callback functionality (e.g. ERC777/ERC1155).

<details>
<summary><i>7 issue instances in 2 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

/// @audit - State change after transfer: `s_poolAssets += uint128(assets)`
424: SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        )
/// @audit - State change after transfer: `s_poolAssets += uint128(assets)`
484: SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        )
```
[424](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L424) | [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L484)

```solidity
File: contracts/PanopticPool.sol

/// @audit - State change after transfer: `s_miniMedian = (uint256(block.timestamp) << 216) + (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) + (uint256(uint24(currentTick)) << 24) + (uint256(uint24(currentTick)))`
304: IUniswapV3Pool(_univ3pool).slot0()
/// @audit - State change after transfer: `(LeftRightSigned premia, uint256[2][] memory balances) = _calculateAccumulatedPremia(user, positionIdList, COMPUTE_ALL_PREMIA, includePendingPremium, currentTick)`
387: s_univ3pool.slot0()
/// @audit - State change after transfer: `s_miniMedian = medianData`
523: s_univ3pool.slot0()
/// @audit - State change after transfer: `(LeftRightSigned positionPremia) = _calculateAccumulatedPremia(account, touchedId, COMPUTE_LONG_PREMIA, ONLY_AVAILABLE_PREMIUM, currentTick)`
1202: s_univ3pool.slot0()
/// @audit - State change after transfer: `s_options[owner][tokenId][legIndex] = accumulatedPremium`
1598: s_univ3pool.slot0()
```
[304](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L304) | [387](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L387) | [523](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L523) | [1202](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1202) | [1598](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1598)
</details>

### [L-11] Prevent Division by Zero

On several locations in the code, precautions are not being taken for not dividing by 0. This will revert the code.
These functions can be called with a 0 value in the input, this value is not checked for being bigger than 0,
that means in some scenarios this can potentially trigger a division by zero.

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: contracts/libraries/Math.sol

/// @audit sqrtR - can be zero
86: if (tick > 0) sqrtR = type(uint256).max / sqrtR;
/// @audit lowPriceX96 - can be zero
112: ) / lowPriceX96;
```
[86](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L86) | [112](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L112)
</details>

### [L-12] Solidity version 0.8.20 may not work on other chains due to `PUSH0`

Solidity 0.8.20, by default, targets the Shanghai version of the EVM, which includes the new `PUSH0` opcode.
However, this opcode may not yet be implemented on all Layer-2 chains.
For instance Arbitrum does not yet support `PUSH0`. See [Documentation](https://developer.arbitrum.io/solidity-support) for more information.
As such, deploying contracts compiled with Solidity 0.8.20 on these chains could lead to failures.

To avoid this, consider specifying an older EVM version as the target, or ensure that the Layer-2 chain used supports the Shanghai EVM.

<details>
<summary><i>11 issue instances in 11 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2)

```solidity
File: contracts/types/LeftRight.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L2)

```solidity
File: contracts/types/LiquidityChunk.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L2)

```solidity
File: contracts/types/TokenId.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L2)

```solidity
File: contracts/libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L2)

```solidity
File: contracts/libraries/Constants.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L2)

```solidity
File: contracts/libraries/Errors.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L2)

```solidity
File: contracts/libraries/FeesCalc.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L2)

```solidity
File: contracts/libraries/Math.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L2)

```solidity
File: contracts/libraries/PanopticMath.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L2)

```solidity
File: contracts/libraries/SafeTransferLib.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L2)
</details>

### [L-13] Ensure `payable` Functions Properly Handle Ether Transfers

A `payable` function that does not make use of `msg.value` can result in the loss of Ether sent with the function call. 
Make sure that if a function is marked as `payable`, it appropriately handles the transfer of Ether.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/multicall/Multicall.sol

12: function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
[12](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L12)
</details>

### [L-14] Lack of Parameter Validation in Constructor/Initializer

The constructor/initializer doesn't validate input parameters before assigning them to state variables.
It is crucial to ensure that input parameters meet certain conditions to avoid unexpected states or behaviors in the contract.
Consider adding appropriate checks or constraints.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit `_factory` is not validated before use
342: constructor(IUniswapV3Factory _factory) {
```
[342](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L342)
</details>

### [L-15] Mint to zero address

Minting tokens to the zero address should be avoided. In several locations in the code, precautions are not being taken to prevent minting to the zero address. This may lead to unintended consequences.
Consider applying checks in the minting functions to ensure tokens are not minted to the zero address.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

214: function _mint(address to, uint256 id, uint256 amount) internal {
```
[214](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L214)
</details>

### [L-16] External calls in an un-bounded `for-`loop may result in a DOS

Executing external calls within unbounded for-loops poses a significant risk of transaction revert.
A failure in one of the iterations can lead to the entire transaction being reverted.
Furthermore, excessive iterations may consume an exorbitant amount of gas, potentially reaching the block gas limit, causing the transaction to fail.
This can result in unintended outcomes, especially if a majority of the iterations would have otherwise succeeded without the problematic call.
To enhance contract reliability and manage gas consumption efficiently, consider limiting the number of iterations in such loops, and implement robust error-handling mechanisms for potential failures in the looped external calls.

<details>
<summary><i>33 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit 12 external calls in unbounded for-loop -> 583: for (uint256 leg = 0; leg < numLegs; ) {
586: uint256 liquidityChunk = PanopticMath.getLiquidityChunk(
590: univ3pool.tickSpacing()
598: id.tokenType(leg),
599: liquidityChunk.tickLower(),
600: liquidityChunk.tickUpper()
607: id.tokenType(leg),
608: liquidityChunk.tickLower(),
609: liquidityChunk.tickUpper()
617: ) revert Errors.TransferFailed();
621: if (fromLiq.rightSlot() != liquidityChunk.liquidity()) revert Errors.TransferFailed();
/// @audit 4 external calls in unbounded for-loop -> 860: for (uint256 leg = 0; leg < numLegs; ) {
882: uint256 liquidityChunk = PanopticMath.getLiquidityChunk(
886: _univ3pool.tickSpacing()
899: amount0 += Math.getAmount0ForLiquidity(liquidityChunk);
901: amount1 += Math.getAmount1ForLiquidity(liquidityChunk);
```
[586](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L586) | [590](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L590) | [598](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L598) | [599](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L599) | [600](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L600) | [607](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L607) | [608](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L608) | [609](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L609) | [617](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L617) | [621](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L621) | [882](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L882) | [886](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L886) | [899](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L899) | [901](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L901)

```solidity
File: contracts/types/TokenId.sol

/// @audit 21 external calls in unbounded for-loop -> 468: for (uint256 i = 0; i < 4; ++i) {
469: if (self.optionRatio(i) == 0) {
473: if ((self >> (64 + 48 * i)) != 0) revert Errors.InvalidTokenIdParameter(1);
480: if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);
483: (self.strike(i) == Constants.MIN_V3POOL_TICK) ||
484: (self.strike(i) == Constants.MAX_V3POOL_TICK)
485: ) revert Errors.InvalidTokenIdParameter(4);
490: uint256 riskPartnerIndex = self.riskPartner(i);
493: if (self.riskPartner(riskPartnerIndex) != i)
494: revert Errors.InvalidTokenIdParameter(3);
498: (self.asset(riskPartnerIndex) != self.asset(i)) ||
499: (self.optionRatio(riskPartnerIndex) != self.optionRatio(i))
500: ) revert Errors.InvalidTokenIdParameter(3);
503: uint256 isLong = self.isLong(i);
504: uint256 isLongP = self.isLong(riskPartnerIndex);
507: uint256 tokenType = self.tokenType(i);
508: uint256 tokenTypeP = self.tokenType(riskPartnerIndex);
513: revert Errors.InvalidTokenIdParameter(4);
518: revert Errors.InvalidTokenIdParameter(5);
```
[469](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L469) | [473](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L473) | [480](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L480) | [483](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L483) | [484](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L484) | [485](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L485) | [490](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L490) | [493](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L493) | [494](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L494) | [498](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L498) | [499](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L499) | [500](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L500) | [503](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L503) | [504](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L504) | [507](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L507) | [508](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L508) | [513](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L513) | [518](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L518)

```solidity
File: contracts/multicall/Multicall.sol

/// @audit 1 external calls in unbounded for-loop -> 14: for (uint256 i = 0; i < data.length; ) {
15: (bool success, bytes memory result) = address(this).delegatecall(data[i]);
```
[15](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L15)
</details>

### [L-17] Input Arrays Lengths Not Checked

When a function takes two or more arrays as arguments, it is important to ensure that their lengths are equal to prevent unexpected behavior.
Add a check to compare the lengths of the arrays in the function body.

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

128: function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public virtual {
178: function balanceOfBatch(
        address[] calldata owners,
        uint256[] calldata ids
    ) public view returns (uint256[] memory balances) {
```
[128](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L128) | [178](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L178)
</details>

### [L-18] Avoid Using `delegatecall` in Loops

Using `delegatecall` in a `for` loop can lead to high gas costs, as `delegatecall` is an expensive operation and its costs compound when used in a loop.
Additionally, it can pose security risks including reentrancy attacks, as it executes code in the calling contract's context.
The function selector collisions can also lead to unpredictable behaviour.
To mitigate these risks, control the loop's iterations, apply a reentrancy guard, strictly audit contracts called via `delegatecall`, and consider alternatives like `call` or proxy patterns if the use case allows.
Always thoroughly vet contracts involved in `delegatecall` operations.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/multicall/Multicall.sol

15: (bool success, bytes memory result) = address(this).delegatecall(data[i]);
```
[15](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L15)
</details>

### [L-19] Loss of precision

Division by large numbers may result in the result being zero, due to Solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator.

<details>
<summary><i>3 issue instances in 1 files:</i></summary>

```solidity
File: contracts/types/TokenId.sol

385: int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;
386: int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;
389: int24 oneSidedRange = (selfWidth * tickSpacing) / 2;
```
[385](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L385) | [386](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L386) | [389](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L389)
</details>

### [L-20] File allows a version of solidity that is susceptible to an assembly optimizer bug

Contracts in the project, written in a version of Solidity before 0.8.15, are at risk due to an optimization bug. This bug can mistakenly cause the removal of essential memory operations in inline assembly, leading to unexpected execution results.

The bug triggers when using the new YUL optimizer and legacy code generation. Under certain compiler settings, the optimizer removes memory operations it incorrectly deems irrelevant to the contract's final output. This faulty process can affect commands like `returndatacopy` and `mstore`, which can influence the execution output, rendering their removal unsafe.
Although the current contract might not exhibit this issue, it remains a risk for future code changes.

To avoid this issue, consider updating the contract Solidity version to 0.8.15 or later.
[More detailed information](https://medium.com/certora/overly-optimistic-optimizer-certora-bug-disclosure-2101e3f7994d)

<details>
<summary><i>4 issue instances in 1 files:</i></summary>

```solidity
File: contracts/libraries/SafeTransferLib.sol

24: mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)
25: mstore(add(4, p), from) // Append the "from" argument.
26: mstore(add(36, p), to) // Append the "to" argument.
27: mstore(add(68, p), amount) // Append the "amount" argument.
```
[24](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L24) | [25](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L25) | [26](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L26) | [27](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L27)
</details>

### [L-21] Unsafe Conversion from Unsigned to Signed Integers

Solidity follows two's complement rules for its integers.
Therefore, casting an unsigned integer to a signed one may result in an unexpected change of the sign or magnitude of the value.
For instance, `int8(type(uint8).max)` doesn't equal `type(int8).max` but is -1. [More information about Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement)

Additionally, if the value from the source type exceeds the maximum value of the target type, it gets truncated by the modulo operation, leading to unpredictable outcomes.
This might introduce unintended behaviors in the contract logic.

<details>
<summary><i>4 issue instances in 1 files:</i></summary>

```solidity
File: contracts/types/LeftRight.sol

/// @audit cast from `uint256 self` to `int128`
33: return int128(self);
/// @audit cast from `uint256 self >> 128` to `int128`
97: return int128(self >> 128);
/// @audit cast from `uint256 self` to `int128`
199: if (!((selfAsInt128 = int128(self)) == self)) revert Errors.CastingError();
/// @audit cast from `uint256 self` to `int256`
214: return int256(self);
```
[33](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L33) | [97](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L97) | [199](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L199) | [214](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L214)
</details>

### [L-22] Unsafe downcast

Casting from larger types to smaller ones can potentially lead to overflows and thus unexpected behavior.
For instance, when a `uint256` value gets cast to `uint8`, it could end up as an entirely different, much smaller number due to the reduction in bits. 

OpenZeppelin's `SafeCast` library provides functions for safe type conversions, throwing an error whenever an overflow would occur.
It is generally recommended to use `SafeCast` or similar protective measures when performing type conversions to ensure the accuracy of your computations and the security of your contracts.

<details>
<summary><i>30 issue instances in 9 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit casted from `int256` to `int128`
1120: .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))
/// @audit casted from `int256` to `int128`
1121: .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));
/// @audit casted from `int256` to `int128`
1159: movedAmounts = int256(0).toRightSlot(int128(int256(amount0))).toLeftSlot(
/// @audit casted from `int256` to `int128`
1160: int128(int256(amount1))
/// @audit casted from `int256` to `int128`
1186: movedAmounts = int256(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(
/// @audit casted from `int256` to `int128`
1187: -int128(int256(amount1))
/// @audit cast from `uint256 s_AddrToPoolIdData` to `uint64`
1469: poolId = uint64(s_AddrToPoolIdData[univ3pool]);
```
[1120](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1120) | [1121](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1121) | [1159](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1159) | [1160](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1160) | [1186](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1186) | [1187](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1187) | [1469](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1469)

```solidity
File: contracts/types/LeftRight.sol

/// @audit cast from `uint32 a` to `uint16`
12: /// @notice higher-order bits are cut off. For example: uint32 a = 0x12345678; uint16 b = uint16(a); // b will be 0x5678 now
/// @audit cast from `uint256 self` to `uint128`
26: return uint128(self);
/// @audit cast from `uint256 self >> 128` to `uint128`
90: return uint128(self >> 128);
/// @audit cast from `uint256 z` to `uint128`
151: if (z < x || (uint128(z) < uint128(x))) revert Errors.UnderOverFlow();
/// @audit cast from `uint256 x` to `uint128`
151: if (z < x || (uint128(z) < uint128(x))) revert Errors.UnderOverFlow();
/// @audit cast from `int256 left256` to `int128`
162: int128 left128 = int128(left256);
/// @audit cast from `int256 right256` to `int128`
165: int128 right128 = int128(right256);
/// @audit cast from `int256 left256` to `int128`
180: int128 left128 = int128(left256);
/// @audit cast from `int256 right256` to `int128`
183: int128 right128 = int128(right256);
/// @audit cast from `uint256 self` to `uint128`
206: if (!((selfAsUint128 = uint128(self)) == self)) revert Errors.CastingError();
```
[12](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L12) | [26](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L26) | [90](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L90) | [151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L151) | [151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L151) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L162) | [165](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L165) | [180](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L180) | [183](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L183) | [206](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L206)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit casted from `int256` to `int24`
114: return int24(int256(self >> 232));
/// @audit casted from `int256` to `int24`
123: return int24(int256(self >> 208));
/// @audit cast from `uint256 self` to `uint128`
132: return uint128(self);
```
[114](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L114) | [123](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L123) | [132](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L132)

```solidity
File: contracts/types/TokenId.sol

/// @audit cast from `uint256 self` to `uint64`
82: return uint64(self);
/// @audit casted from `int256` to `int24`
151: return int24(int256(self >> (64 + legIndex * 48 + 12)));
/// @audit casted from `int256` to `int24`
162: return int24(int256((self >> (64 + legIndex * 48 + 36)) % 4096));
```
[82](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L82) | [151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L151) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L162)

```solidity
File: contracts/libraries/CallbackLib.sol

/// @audit casted from `uint256` to `uint160`
37: uint160(
```
[37](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L37)

```solidity
File: contracts/libraries/Errors.sol

/// @audit casted from `uint256` to `uint128`
10: /// @dev e.g. uint128(uint256(a)) fails
```
[10](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L10)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit casted from `int256` to `int128`
76: .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, startingLiquidity))))
/// @audit casted from `int256` to `int128`
77: .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, startingLiquidity))));
```
[76](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L76) | [77](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L77)

```solidity
File: contracts/libraries/Math.sol

/// @audit cast from `uint256 toDowncast` to `uint128`
173: if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();
```
[173](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L173)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit casted from `uint160` to `uint64`
39: return uint64(uint160(univ3pool) >> 96);
/// @audit casted from `uint256` to `uint64`
57: (uint64(uint256(keccak256(abi.encodePacked(token0, token1, fee)))) >> 32);
```
[39](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L39) | [57](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L57)
</details>

### [L-23] Possible Revert ERC20 Transfers with Zero Value

Some ERC20 tokens (for example, LEND) revert on attempts to transfer a zero value.
This can become a problem in any contract that doesn't handle these cases correctly.

If a token transfer fails, any additional logic in a function might also be affected or even fail entirely.
Therefore, contracts interacting with ERC20 tokens should account for the possibility that a zero-value transfer might revert.

<details>
<summary><i>3 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit `msg.sender,
                amount0Owed` has not been checked for zero value before transfer
418: SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token0,
                decoded.payer,
                msg.sender,
                amount0Owed
            );
/// @audit `msg.sender,
                amount1Owed` has not been checked for zero value before transfer
425: SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token1,
                decoded.payer,
                msg.sender,
                amount1Owed
            );
/// @audit `msg.sender, amountToPay` has not been checked for zero value before transfer
460: SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);
```
[418](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L418) | [425](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L425) | [460](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L460)
</details>

### [L-24] Missing `address(0)` Check in Constructor/Initializer

The constructor/initializer does not include a check for `address(0)` when initializing state variables that hold addresses.
Initializing a state variable with `address(0)` can lead to unintended behavior and vulnerabilities in the contract, 
such as sending funds to an inaccessible address. 
It is recommended to include a validation step to ensure that address parameters are not set to `address(0)`.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit `_factory` has lack of `address(0)` check before use
342: constructor(IUniswapV3Factory _factory) {
```
[342](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L342)
</details>

### [L-25] Functions calling tokens with transfer hooks are missing reentrancy guards

Functions that call contracts or addresses with transfer hooks should use reentrancy guards for protection. 
Even if these functions adhere to the check-effects-interaction best practice, absence of reentrancy guards can expose the protocol users to read-only reentrancies.
Without the guards, the only protective measure is to block-list the entire protocol, which isn't an optimal solution.

<details>
<summary><i>3 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit function `uniswapV3MintCallback()` 
418: SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token0,
                decoded.payer,
                msg.sender,
                amount0Owed
            );
/// @audit function `uniswapV3MintCallback()` 
425: SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token1,
                decoded.payer,
                msg.sender,
                amount1Owed
            );
/// @audit function `uniswapV3SwapCallback()` 
460: SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);
```
[418](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L418) | [425](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L425) | [460](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L460)
</details>


## NonCritical Findings Details

### [N-01] Subtraction in `unchecked` block is unsafe

Performing subtraction within an unchecked block poses a risk of silent underflow, leading to unintended behavior or vulnerabilities. Without proper value checks, the subtraction could result in values that are lower than expected, potentially impacting the logic and security of the contract.

<details>
<summary><i>119 issue instances in 8 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

200: int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);
403: assets * (DECIMALS - COMMISSION_FEE),
465: totalSupply * (DECIMALS - COMMISSION_FEE)
677: uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
715: int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
718: int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
727: int256 fee = (FORCE_EXERCISE_COST >> (maxNumRangesFromStrike - 1)); // exponential decay of fee based on number of half ranges away from the price
797: ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
797: ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798: (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);
850: (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851: (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2
1003: int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
1029: s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));
1052: int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
1058: int256 intrinsicValue = swappedAmount - (longAmount - shortAmount);
1058: int256 intrinsicValue = swappedAmount - (longAmount - shortAmount);
1085: s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));
1085: s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));
1105: int256 intrinsicValue = swappedAmount - (shortAmount - longAmount);
1105: int256 intrinsicValue = swappedAmount - (shortAmount - longAmount);
1364: Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)
1367: Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)
1397: uint256 c2 = Constants.FP96 - ratio;
1409: (tickUpper - strike) + (strike - tickLower)
1409: (tickUpper - strike) + (strike - tickLower)
1413: scaleFactor - ratio,
1546: ? movedPartnerRight - movedRight
1547: : movedRight - movedPartnerRight;
1550: ? movedPartnerLeft - movedLeft
1551: : movedLeft - movedPartnerLeft;
1571: ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)
1572: : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);
```
[200](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L200) | [403](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L403) | [465](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L465) | [677](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L677) | [715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L715) | [718](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L718) | [727](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L727) | [797](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L797) | [797](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L797) | [798](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L798) | [850](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L850) | [851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L851) | [1003](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1003) | [1029](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1029) | [1052](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1052) | [1058](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1058) | [1058](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1058) | [1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085) | [1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085) | [1105](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1105) | [1105](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1105) | [1364](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1364) | [1367](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1367) | [1397](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1397) | [1409](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1409) | [1409](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1409) | [1413](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1413) | [1546](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1546) | [1547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1547) | [1550](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1550) | [1551](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1551) | [1571](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1571) | [1572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1572)

```solidity
File: contracts/PanopticPool.sol

624: tokenId = positionIdList[positionIdList.length - 1];
1255: refundAmounts.rightSlot() - delegatedAmounts.rightSlot()
1260: refundAmounts.leftSlot() - delegatedAmounts.leftSlot()
1376: pLength = positionIdList.length - offset;
1550: ((premiumAccumulatorsByLeg[leg][0] -
                                        premiumAccumulatorLast.rightSlot()) *
1559: ((premiumAccumulatorsByLeg[leg][1] -
                                        premiumAccumulatorLast.leftSlot()) *
1723: uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
1768: uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *
1770: uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *
1935: (int256(
                                                    grossPremiumLast.rightSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][0] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
1952: (int256(
                                                    grossPremiumLast.leftSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][1] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
```
[624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L624) | [1255](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1255) | [1260](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1260) | [1376](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1376) | [1550](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1550) | [1559](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1559) | [1723](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1723) | [1768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1768) | [1770](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1770) | [1935](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1935) | [1952](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1952)

```solidity
File: contracts/SemiFungiblePositionManager.sol

817: int256 net0 = itm0 - PanopticMath.convert1to0(itm1, sqrtPriceX96);
843: : Constants.MAX_V3POOL_SQRT_RATIO - 1,
899: _leg = _isBurn ? numLegs - leg - 1 : leg;
899: _leg = _isBurn ? numLegs - leg - 1 : leg;
1023: updatedLiquidity = startingLiquidity - chunkLiquidity;
1297: ? receivedAmount0 - uint128(-movedInLeg.rightSlot())
1300: ? receivedAmount1 - uint128(-movedInLeg.leftSlot())
1388: uint256 numerator = totalLiquidity ** 2 -
                        totalLiquidity *
                        removedLiquidity +
```
[817](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L817) | [843](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L843) | [899](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L899) | [899](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L899) | [1023](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1023) | [1297](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1297) | [1300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1300) | [1388](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1388)

```solidity
File: contracts/libraries/FeesCalc.sol

166: feeGrowthInside0X128 = lowerOut0 - upperOut0; // fee growth inside the chunk
167: feeGrowthInside1X128 = lowerOut1 - upperOut1;
183: feeGrowthInside0X128 = upperOut0 - lowerOut0;
184: feeGrowthInside1X128 = upperOut1 - lowerOut1;
204: feeGrowthInside0X128 = univ3pool.feeGrowthGlobal0X128() - lowerOut0 - upperOut0;
204: feeGrowthInside0X128 = univ3pool.feeGrowthGlobal0X128() - lowerOut0 - upperOut0;
205: feeGrowthInside1X128 = univ3pool.feeGrowthGlobal1X128() - lowerOut1 - upperOut1;
205: feeGrowthInside1X128 = univ3pool.feeGrowthGlobal1X128() - lowerOut1 - upperOut1;
```
[166](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L166) | [167](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L167) | [183](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L183) | [184](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L184) | [204](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L204) | [204](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L204) | [205](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L205) | [205](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L205)

```solidity
File: contracts/libraries/Math.sol

198: highPriceX96 - lowPriceX96,
212: return mulDiv96(liquidityChunk.liquidity(), highPriceX96 - lowPriceX96);
258: highPriceX96 - lowPriceX96
284: toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))
391: uint256 twos = (0 - denominator) & denominator;
418: inv *= 2 - denominator * inv; // inverse mod 2**8
419: inv *= 2 - denominator * inv; // inverse mod 2**16
420: inv *= 2 - denominator * inv; // inverse mod 2**32
421: inv *= 2 - denominator * inv; // inverse mod 2**64
422: inv *= 2 - denominator * inv; // inverse mod 2**128
423: inv *= 2 - denominator * inv; // inverse mod 2**256
758: int256 pivot = arr[uint256(left + (right - left) / 2)];
778: quickSort(data, int256(0), int256(data.length - 1));
```
[198](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L198) | [212](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L212) | [258](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L258) | [284](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L284) | [391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L391) | [418](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L418) | [419](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L419) | [420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L420) | [421](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L421) | [422](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L422) | [423](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L423) | [758](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L758) | [778](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L778)

```solidity
File: contracts/libraries/PanopticMath.sol

77: return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));
108: : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);
140: (int256(observationIndex) - int256(i * period)) +
150: (tickCumulatives[i] - tickCumulatives[i + 1]) /
151: int256(timestamps[i] - timestamps[i + 1]);
188: int256(observationIndex) - int256(1) + int256(observationCardinality)
195: (tickCumulative_last - tickCumulative_old) /
196: int256(timestamp_last - timestamp_old)
223: newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));
258: (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
351: (tickLower, tickUpper) = (strike - rangeDown, strike + rangeUp);
678: uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);
685: Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
693: int256 balance0 = int256(uint256(tokenData0.rightSlot())) -
                Math.max(premia.rightSlot(), 0);
695: int256 balance1 = int256(uint256(tokenData1.rightSlot())) -
                Math.max(premia.leftSlot(), 0);
716: balance1 - paid1,
717: PanopticMath.convert0to1(paid0 - balance0, sqrtPriceX96Final)
720: PanopticMath.convert1to0(balance1 - paid1, sqrtPriceX96Final),
721: paid0 - balance0
734: balance0 - paid0,
735: PanopticMath.convert1to0(paid1 - balance1, sqrtPriceX96Final)
738: PanopticMath.convert0to1(balance0 - paid0, sqrtPriceX96Final),
739: paid1 - balance1
749: LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(
750: int128(balance1 - paid1)
804: collateralDelta0 - longPremium.rightSlot(),
806: longPremium.leftSlot() - collateralDelta1,
811: longPremium.leftSlot() - collateralDelta1,
813: collateralDelta0 - longPremium.rightSlot(),
828: longPremium.rightSlot() - collateralDelta0,
830: collateralDelta1 - longPremium.leftSlot(),
835: collateralDelta1 - longPremium.leftSlot(),
837: longPremium.rightSlot() - collateralDelta0,
890: uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
894: uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
928: int256 balanceShortage = refundValues.rightSlot() -
                int256(collateral0.convertToAssets(collateral0.balanceOf(refunder)));
935: .toRightSlot(int128(refundValues.rightSlot() - balanceShortage))
946: refundValues.leftSlot() -
                int256(collateral1.convertToAssets(collateral1.balanceOf(refunder)));
953: .toLeftSlot(int128(refundValues.leftSlot() - balanceShortage))
```
[77](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L77) | [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L108) | [140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140) | [150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L150) | [151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L151) | [188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L188) | [195](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L195) | [196](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L196) | [223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223) | [258](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L258) | [351](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L351) | [678](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L678) | [685](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L685) | [693](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L693) | [695](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L695) | [716](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L716) | [717](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L717) | [720](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L720) | [721](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L721) | [734](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L734) | [735](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L735) | [738](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L738) | [739](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L739) | [749](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L749) | [750](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L750) | [804](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L804) | [806](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L806) | [811](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L811) | [813](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L813) | [828](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L828) | [830](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L830) | [835](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L835) | [837](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L837) | [890](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L890) | [894](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L894) | [928](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L928) | [935](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L935) | [946](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L946) | [953](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L953)

```solidity
File: contracts/types/LeftRight.sol

178: z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));
234: int256 left256 = int256(x.leftSlot()) - y.leftSlot();
237: int256 right256 = int256(x.rightSlot()) - y.rightSlot();
256: int256 left256 = int256(x.leftSlot()) - y.leftSlot();
259: int256 right256 = int256(x.rightSlot()) - y.rightSlot();
```
[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L178) | [234](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L234) | [237](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L237) | [256](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L256) | [259](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L259)

```solidity
File: contracts/types/TokenId.sol

395: ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)
589: if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {
```
[395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L395) | [589](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L589)
</details>

### [N-02] `internal/private` Function calls within for loops

Making function calls or external calls within loops in Solidity can lead to inefficient gas usage, potential bottlenecks, and increased vulnerability to attacks.
Each function call or external call consumes gas, and when executed within a loop, the gas cost multiplies, potentially causing the transaction to run out of gas or exceed block gas limits.
This can result in transaction failure or unpredictable behavior.

<details>
<summary><i>16 issue instances in 4 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

1219: _getRequiredCollateralAtTickSinglePosition(
                tokenId,
                positionSize,
                atTick,
                poolUtilization
            )
1259: _getRequiredCollateralSingleLeg(
                    tokenId,
                    index,
                    positionSize,
                    atTick,
                    poolUtilization
                )
```
[1219](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1219) | [1259](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1259)

```solidity
File: contracts/PanopticPool.sol

450: _getPremia(
                    tokenId,
                    LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
                    c_user,
                    computeAllPremia,
                    atTick
                )
469: _getAvailablePremium(
                        _getTotalLiquidity(tokenId, leg),
                        s_settledTokens[chunkKey],
                        s_grossPremiumLast[chunkKey],
                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
                        premiumAccumulatorsByLeg[leg]
                    )
470: _getTotalLiquidity(tokenId, leg)
469: _getAvailablePremium(
                        _getTotalLiquidity(tokenId, leg),
                        s_settledTokens[chunkKey],
                        s_grossPremiumLast[chunkKey],
                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
                        premiumAccumulatorsByLeg[leg]
                    )
470: _getTotalLiquidity(tokenId, leg)
770: _checkLiquiditySpread(
                    tokenId,
                    leg,
                    tickLower,
                    tickUpper,
                    uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))
                )
804: _burnOptions(
                commitLongSettled,
                positionIdList[i],
                owner,
                tickLimitLow,
                tickLimitHigh
            )
868: _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD)
1687: _getTotalLiquidity(tokenId, leg)
1882: _getTotalLiquidity(tokenId, leg)
1888: _getAvailablePremium(
                        totalLiquidity + positionLiquidity,
                        settledTokens,
                        grossPremiumLast,
                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
                        premiumAccumulatorsByLeg[leg]
                    )
```
[450](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L450) | [469](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L469) | [470](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L470) | [469](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L469) | [470](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L470) | [770](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L770) | [804](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L804) | [868](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L868) | [1687](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1687) | [1882](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1882) | [1888](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1888)

```solidity
File: contracts/SemiFungiblePositionManager.sol

577: registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i])
910: _createLegInAMM(
                    _univ3pool,
                    _tokenId,
                    _leg,
                    liquidityChunk,
                    _isBurn
                )
```
[577](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L577) | [910](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L910)

```solidity
File: contracts/libraries/PanopticMath.sol

397: _calculateIOAmounts(
                tokenId,
                positionSize,
                leg
            )
```
[397](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L397)
</details>

### [N-03] Non-library/interface files should use fixed compiler versions, not floating ones

Floating pragmas may lead to unintended vulnerabilities due to different compiler versions.
It is recommended to lock the Solidity version in pragma statements.

<details>
<summary><i>7 issue instances in 7 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

2: pragma solidity ^0.8.18
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L2)

```solidity
File: contracts/PanopticFactory.sol

2: pragma solidity ^0.8.18
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L2)

```solidity
File: contracts/PanopticPool.sol

2: pragma solidity ^0.8.18
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L2)

```solidity
File: contracts/SemiFungiblePositionManager.sol

2: pragma solidity ^0.8.18
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L2)

```solidity
File: contracts/multicall/Multicall.sol

2: pragma solidity ^0.8.18
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L2)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2)

```solidity
File: contracts/tokens/ERC20Minimal.sol

2: pragma solidity ^0.8.0
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L2)
</details>

### [N-04] Array indices should be referenced via `enum`s rather than via numeric literals

Using constant array indexes can make your Solidity code harder to read and maintain.
To improve clarity, consider using commented enum values in place of constant array indexes.

Enums provide a way to define a type that has a few pre-defined values, making your code more self-explanatory and easy to understand.
This can be particularly helpful in large codebases or when working with a team.

<details>
<summary><i>44 issue instances in 3 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

1210: positionBalanceArray[i][0]
1213: positionBalanceArray[i][1]
1216: positionBalanceArray[i][1]
```
[1210](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1210) | [1213](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1213) | [1216](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1216)

```solidity
File: contracts/PanopticPool.sol

390: uint256[2]
437: uint256[2]
444: balances[k][0]
445: balances[k][1]
448: LeftRightSigned[4]
449: uint256[2][4]
449: uint256[2]
452: balances[k][1]
685: LeftRightUnsigned[4]
801: LeftRightSigned[4]
970: LeftRightUnsigned[4]
1038: uint256[2]
1038: uint256[2]
1080: LeftRightSigned[4]
1193: touchedId[0]
1198: touchedId[0]
1219: touchedId[0]
1234: touchedId[0]
1277: touchedId[0]
1299: uint256[2]
1528: premiumAccumulatorsByLeg[leg][0]
1528: premiumAccumulatorsByLeg[leg][1]
1550: premiumAccumulatorsByLeg[leg][0]
1559: premiumAccumulatorsByLeg[leg][1]
1706: uint256[2]
1707: grossCurrent[0]
1707: grossCurrent[1]
1729: grossCurrent[0]
1737: grossCurrent[1]
1768: premiumAccumulators[0]
1770: premiumAccumulators[1]
1841: uint256[2][4]
1841: uint256[2]
1923: uint256[2][4]
1923: uint256[2]
1940: _premiumAccumulatorsByLeg[_leg][0]
1957: _premiumAccumulatorsByLeg[_leg][1]
1967: premiumAccumulatorsByLeg[_leg][0]
1968: premiumAccumulatorsByLeg[_leg][1]
```
[390](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L390) | [437](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L437) | [444](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L444) | [445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L445) | [448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L448) | [449](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L449) | [449](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L449) | [452](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L452) | [685](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L685) | [801](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L801) | [970](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L970) | [1038](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1038) | [1038](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1038) | [1080](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1080) | [1193](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1193) | [1198](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1198) | [1219](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1219) | [1234](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1234) | [1277](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1277) | [1299](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1299) | [1528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1528) | [1528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1528) | [1550](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1550) | [1559](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1559) | [1706](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1706) | [1707](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1707) | [1707](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1707) | [1729](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1729) | [1737](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1737) | [1768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1768) | [1770](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1770) | [1841](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1841) | [1841](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1841) | [1923](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1923) | [1923](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1923) | [1940](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1940) | [1957](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1957) | [1967](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1967) | [1968](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1968)

```solidity
File: contracts/libraries/PanopticMath.sol

266: sortedTicks[10]
862: LeftRightSigned[4]
```
[266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L266) | [862](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L862)
</details>

### [N-05] Consider splitting long calculations

For improved readability and maintainability, it's suggested to limit arithmetic operations to 3 per expression.
Excessive operations can convolute the code, making it more prone to errors and more difficult to debug or review.
Splitting operations across multiple lines is often a good approach.
Special care should be taken with division operations. The number of arithmetic operations per line ideally shouldn't exceed three.

<details>
<summary><i>35 issue instances in 6 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

201: uint256(
                2230 +
                    (12500 * ratioTick) /
                    10_000 +
                    (7812 * ratioTick ** 2) /
                    10_000 ** 2 +
                    (6510 * ratioTick ** 3) /
                    10_000 ** 3
            )
730: exerciseFees
                .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))
                .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128))
796: min_sell_ratio +
                ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
                (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)
849: (BUYER_COLLATERAL_RATIO +
                    (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2
1570: (notional < notionalP)
                    ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)
                    : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP)
```
[201](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L201) | [730](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L730) | [796](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L796) | [849](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L849) | [1570](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1570)

```solidity
File: contracts/PanopticPool.sol

309: (uint256(block.timestamp) << 216) +
                // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
                // see comment on s_miniMedian initialization for format of this magic number
                (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
                (uint256(uint24(currentTick)) << 24) + // add to slot 4
                (uint256(uint24(currentTick)))
1545: LeftRightSigned
                        .wrap(0)
                        .toRightSlot(
                            int128(
                                int256(
                                    ((premiumAccumulatorsByLeg[leg][0] -
                                        premiumAccumulatorLast.rightSlot()) *
                                        (liquidityChunk.liquidity())) / 2 ** 64
                                )
                            )
                        )
                        .toLeftSlot(
                            int128(
                                int256(
                                    ((premiumAccumulatorsByLeg[leg][1] -
                                        premiumAccumulatorLast.leftSlot()) *
                                        (liquidityChunk.liquidity())) / 2 ** 64
                                )
                            )
                        )
1725: LeftRightUnsigned
                        .wrap(0)
                        .toRightSlot(
                            uint128(
                                (grossCurrent[0] *
                                    positionLiquidity +
                                    grossPremiumLast.rightSlot() *
                                    totalLiquidityBefore) / (totalLiquidity)
                            )
                        )
                        .toLeftSlot(
                            uint128(
                                (grossCurrent[1] *
                                    positionLiquidity +
                                    grossPremiumLast.leftSlot() *
                                    totalLiquidityBefore) / (totalLiquidity)
                            )
                        )
1774: LeftRightUnsigned
                    .wrap(0)
                    .toRightSlot(
                        uint128(
                            Math.min(
                                (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /
                                    (accumulated0 == 0 ? type(uint256).max : accumulated0),
                                premiumOwed.rightSlot()
                            )
                        )
                    )
                    .toLeftSlot(
                        uint128(
                            Math.min(
                                (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /
                                    (accumulated1 == 0 ? type(uint256).max : accumulated1),
                                premiumOwed.leftSlot()
                            )
                        )
                    )
1928: totalLiquidity != 0
                            ? LeftRightUnsigned
                                .wrap(0)
                                .toRightSlot(
                                    uint128(
                                        uint256(
                                            Math.max(
                                                (int256(
                                                    grossPremiumLast.rightSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][0] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
                                                0
                                            )
                                        ) / totalLiquidity
                                    )
                                )
                                .toLeftSlot(
                                    uint128(
                                        uint256(
                                            Math.max(
                                                (int256(
                                                    grossPremiumLast.leftSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][1] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
                                                0
                                            )
                                        ) / totalLiquidity
                                    )
                                )
                            : LeftRightUnsigned
                                .wrap(0)
                                .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
                                .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]))
```
[309](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L309) | [1545](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1545) | [1725](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1725) | [1774](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1774) | [1928](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1928)

```solidity
File: contracts/libraries/Math.sol

179: uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1))
```
[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L179)

```solidity
File: contracts/libraries/PanopticMath.sol

106: addFlag
                    ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)
                    : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248)
138: univ3pool.observations(
                    uint256(
                        (int256(observationIndex) - int256(i * period)) +
                            int256(observationCardinality)
                    ) % observationCardinality
                )
150: (tickCumulatives[i] - tickCumulatives[i + 1]) /
                    int256(timestamps[i] - timestamps[i + 1])
178: (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
                2
223: newOrderMap + ((rank + 1) << (3 * (i + shift - 1)))
227: (block.timestamp << 216) +
                    (uint256(newOrderMap) << 192) +
                    uint256(uint192(medianData << 24)) +
                    uint256(uint24(lastObservedTick))
257: int24(
                    (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
                )
802: (
                    -Math.min(
                        collateralDelta0 - longPremium.rightSlot(),
                        PanopticMath.convert1to0(
                            longPremium.leftSlot() - collateralDelta1,
                            sqrtPriceX96Final
                        )
                    ),
                    Math.min(
                        longPremium.leftSlot() - collateralDelta1,
                        PanopticMath.convert0to1(
                            collateralDelta0 - longPremium.rightSlot(),
                            sqrtPriceX96Final
                        )
                    )
                )
826: (
                    Math.min(
                        longPremium.rightSlot() - collateralDelta0,
                        PanopticMath.convert1to0(
                            collateralDelta1 - longPremium.leftSlot(),
                            sqrtPriceX96Final
                        )
                    ),
                    -Math.min(
                        collateralDelta1 - longPremium.leftSlot(),
                        PanopticMath.convert0to1(
                            longPremium.rightSlot() - collateralDelta0,
                            sqrtPriceX96Final
                        )
                    )
                )
```
[106](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L106) | [138](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L138) | [150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L150) | [178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178) | [223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223) | [227](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L227) | [257](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L257) | [802](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L802) | [826](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L826)

```solidity
File: contracts/types/LiquidityChunk.sol

77: LiquidityChunk.wrap(
                    (uint256(uint24(_tickLower)) << 232) +
                        (uint256(uint24(_tickUpper)) << 208) +
                        uint256(amount)
                )
```
[77](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L77)

```solidity
File: contracts/types/TokenId.sol

110: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2)
120: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128)
130: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2)
140: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2)
150: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4)
160: int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)))
171: int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096))
212: TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)))
228: TokenId.wrap(
                    TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))
                )
246: TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)))
262: TokenId.wrap(
                    TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))
                )
280: TokenId.wrap(
                    TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))
                )
298: TokenId.wrap(
                    TokenId.unwrap(self) +
                        uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))
                )
318: TokenId.wrap(
                    TokenId.unwrap(self) +
                        (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))
                )
```
[110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L110) | [120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120) | [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130) | [140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140) | [150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150) | [160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L160) | [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171) | [212](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L212) | [228](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L228) | [246](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L246) | [262](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L262) | [280](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L280) | [298](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L298) | [318](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L318)
</details>

### [N-06] Use custom errors instead of `require()/assert()`

Starting from Solidity 0.8.4, custom errors have been introduced to improve readability and clarity in your code. Instead of using `require()/assert()` with strings, custom errors can provide more expressive and understandable error conditions.

This change not only reduces unnecessary clutter in your codebase but also promotes a more streamlined contract structure, ultimately improving the quality of your Solidity code.

<details>
<summary><i>9 issue instances in 1 files:</i></summary>

```solidity
File: contracts/libraries/Math.sol

361: require(denominator > 0)
370: require(denominator > prod1)
448: require(result < type(uint256).max)
484: require(2 ** 64 > prod1)
547: require(2 ** 96 > prod1)
588: require(result < type(uint256).max)
624: require(2 ** 128 > prod1)
665: require(result < type(uint256).max)
701: require(2 ** 192 > prod1)
```
[361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L361) | [370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L370) | [448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448) | [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L484) | [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L547) | [588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588) | [624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L624) | [665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665) | [701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L701)
</details>

### [N-07] Missing Event Emission After Critical Initialize() Function

Emitting an initialization event offers clear, on-chain evidence of the contract's initialization state, enhancing transparency and auditability.
This practice aids users and developers in accurately tracking the contract's lifecycle, pinpointing the precise moment of its initialization.
Moreover, it aligns with best practices for event logging in smart contracts, ensuring that significant state changes are both observable and verifiable through emitted events.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/PanopticFactory.sol

134: function initialize(address _owner) public
```
[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134)
</details>

### [N-08] Variables need not be initialized to zero

By default, `int/uint` variables in Solidity are initialized to `zero`.
Explicitly setting variables to zero during their declaration is redundant and might cause confusion.
Removing the explicit zero initialization can improve code readability and understanding.

<details>
<summary><i>31 issue instances in 8 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

662: for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {
1208: for (uint256 i = 0; i < totalIterations; ) {
1255: for (uint256 index = 0; index < numLegs; ++index) {
```
[662](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L662) | [1208](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1208) | [1255](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1255)

```solidity
File: contracts/PanopticPool.sol

441: for (uint256 k = 0; k < pLength; ) {
459: for (uint256 leg = 0; leg < numLegs; ) {
745: for (uint256 leg = 0; leg < numLegs; ) {
802: for (uint256 i = 0; i < positionIdList.length; ) {
864: for (uint256 leg = 0; leg < numLegs; ) {
1382: for (uint256 i = 0; i < pLength; ) {
1518: for (uint256 leg = 0; leg < numLegs; ) {
1672: for (uint256 leg = 0; leg < numLegs; ++leg) {
1852: for (uint256 leg = 0; leg < numLegs; ) {
```
[441](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L441) | [459](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L459) | [745](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L745) | [802](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L802) | [864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L864) | [1382](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1382) | [1518](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1518) | [1672](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1672) | [1852](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1852)

```solidity
File: contracts/SemiFungiblePositionManager.sol

575: for (uint256 i = 0; i < ids.length; ) {
601: for (uint256 leg = 0; leg < numLegs; ) {
882: for (uint256 leg = 0; leg < numLegs; ) {
```
[575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L575) | [601](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L601) | [882](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L882)

```solidity
File: contracts/libraries/FeesCalc.sol

51: for (uint256 k = 0; k < positionIdList.length; ) {
55: for (uint256 leg = 0; leg < numLegs; ) {
```
[51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L51) | [55](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L55)

```solidity
File: contracts/libraries/PanopticMath.sol

137: for (uint256 i = 0; i < cardinality + 1; ++i) {
148: for (uint256 i = 0; i < cardinality; ++i) {
248: for (uint256 i = 0; i < 20; ++i) {
256: for (uint256 i = 0; i < 19; ++i) {
395: for (uint256 leg = 0; leg < numLegs; ) {
781: for (uint256 i = 0; i < positionIdList.length; ++i) {
784: for (uint256 leg = 0; leg < numLegs; ++leg) {
860: for (uint256 i = 0; i < positionIdList.length; i++) {
863: for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
```
[137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L137) | [148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L148) | [248](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L248) | [256](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L256) | [395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L395) | [781](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L781) | [784](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L784) | [860](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L860) | [863](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L863)

```solidity
File: contracts/multicall/Multicall.sol

14: for (uint256 i = 0; i < data.length; ) {
```
[14](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L14)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

143: for (uint256 i = 0; i < ids.length; ) {
187: for (uint256 i = 0; i < owners.length; ++i) {
```
[143](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L143) | [187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L187)

```solidity
File: contracts/types/TokenId.sol

507: for (uint256 i = 0; i < 4; ++i) {
581: for (uint256 i = 0; i < numLegs; ++i) {
```
[507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L507) | [581](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L581)
</details>

### [N-09] Variables need not be initialized to false

By default, boolean variables in Solidity are initialized to `false`.
Explicitly setting variables to `false` during their declaration is redundant and might cause confusion.
Removing the explicit zero initialization can improve code readability and understanding.

<details>
<summary><i>5 issue instances in 2 files:</i></summary>

```solidity
File: contracts/PanopticPool.sol

111: bool internal constant COMPUTE_LONG_PREMIA = false;
114: bool internal constant ONLY_AVAILABLE_PREMIUM = false;
120: bool internal constant DONOT_COMMIT_LONG_SETTLED = false;
133: bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;
```
[111](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L111) | [114](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L114) | [120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L120) | [133](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L133)

```solidity
File: contracts/SemiFungiblePositionManager.sol

125: bool internal constant MINT = false;
```
[125](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L125)
</details>

### [N-10] `require()/revert()` statements without reason strings

In Solidity, require() and revert() functions can include an optional 'reason' string that describes what caused the function to fail. This string can be incredibly helpful during testing and debugging, as it provides more context for what went wrong.

Some `require()/revert()` statements do not have these descriptive reason strings. For better error handling and debugging, it is strongly recommended to add descriptive reason strings to all `require()/revert()` statements.

<details>
<summary><i>9 issue instances in 1 files:</i></summary>

```solidity
File: contracts/libraries/Math.sol

361: require(denominator > 0)
370: require(denominator > prod1)
448: require(result < type(uint256).max)
484: require(2 ** 64 > prod1)
547: require(2 ** 96 > prod1)
588: require(result < type(uint256).max)
624: require(2 ** 128 > prod1)
665: require(result < type(uint256).max)
701: require(2 ** 192 > prod1)
```
[361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L361) | [370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L370) | [448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448) | [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L484) | [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L547) | [588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588) | [624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L624) | [665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665) | [701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L701)
</details>

### [N-11] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability

Combining multiple address/ID mappings into a single mapping to a struct can enhance code clarity and maintainability. 
Consider refactoring multiple mappings into a single mapping with a struct for cleaner code structure.
This arrangement also promotes a more organized contract structure, making it easier for developers to navigate and understand.

<details>
<summary><i>13 issue instances in 4 files:</i></summary>

```solidity
File: contracts/PanopticPool.sol

238: mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))
        internal s_options
258: mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
        internal s_positionBalance
272: mapping(address account => uint256 positionsHash) internal s_positionsHash
245: mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast
251: mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens
```
[238](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L238) | [258](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L258) | [272](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L272) | [245](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L245) | [251](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L251)

```solidity
File: contracts/SemiFungiblePositionManager.sol

177: mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
        internal s_accountLiquidity
287: mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed
289: mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross
295: mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase
```
[177](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L177) | [287](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L287) | [289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L289) | [295](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L295)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

66: mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf
71: mapping(address owner => mapping(address operator => bool approvedForAll))
        public isApprovedForAll
```
[66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L66) | [71](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L71)

```solidity
File: contracts/tokens/ERC20Minimal.sol

35: mapping(address account => uint256 balance) public balanceOf
39: mapping(address owner => mapping(address spender => uint256 allowance)) public allowance
```
[35](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L35) | [39](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L39)
</details>

### [N-12] Consider returning a `struct` rather than having multiple `return` values

Functions that return many variables can become difficult to read and maintain.
Using a struct to encapsulate these return values can improve code readability, increase reusability, and reduce the likelihood of errors.
Consider refactoring functions that return more than three variables to use a struct instead.

<details>
<summary><i>7 issue instances in 4 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

277: function getPoolData()
        external
        view
        returns (uint256 poolAssets, uint256 insideAMM, int256 currentPoolUtilization)
```
[277](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L277)

```solidity
File: contracts/PanopticPool.sol

352: function optionPositionBalance(
        address user,
        TokenId tokenId
    ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1)
381: function calculateAccumulatedFeesBatch(
        address user,
        bool includePendingPremium,
        TokenId[] calldata positionIdList
    ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory)
955: function _burnAndHandleExercise(
        bool commitLongSettled,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        TokenId tokenId,
        uint128 positionSize,
        address owner
    )
        internal
        returns (
            LeftRightSigned realizedPremia,
            LeftRightSigned[4] memory premiaByLeg,
            LeftRightSigned paidAmounts
        )
```
[352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L352) | [381](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L381) | [955](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L955)

```solidity
File: contracts/SemiFungiblePositionManager.sol

863: function _createPositionInAMM(
        IUniswapV3Pool univ3pool,
        TokenId tokenId,
        uint128 positionSize,
        bool isBurn
    )
        internal
        returns (
            LeftRightSigned totalMoved,
            LeftRightUnsigned[4] memory collectedByLeg,
            LeftRightSigned itmAmounts
        )
958: function _createLegInAMM(
        IUniswapV3Pool univ3pool,
        TokenId tokenId,
        uint256 leg,
        LiquidityChunk liquidityChunk,
        bool isBurn
    )
        internal
        returns (
            LeftRightSigned moved,
            LeftRightSigned itmAmounts,
            LeftRightUnsigned collectedSingleLeg
        )
```
[863](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L863) | [958](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L958)

```solidity
File: contracts/libraries/PanopticMath.sol

651: function getLiquidationBonus(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint160 sqrtPriceX96Twap,
        uint160 sqrtPriceX96Final,
        LeftRightSigned netExchanged,
        LeftRightSigned premia
    ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned)
```
[651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L651)
</details>

### [N-13] Consider using a `struct` rather than having many function input parameters

Functions with many parameters can become difficult to read and maintain. 
Using a struct to encapsulate these parameters can improve code readability, increase reusability, and reduce the likelihood of errors.
Consider refactoring functions that take more than three parameters to use a struct instead.

<details>
<summary><i>41 issue instances in 9 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

178: constructor(
        uint256 _commissionFee,
        uint256 _sellerCollateralRatio,
        uint256 _buyerCollateralRatio,
        int256 _forceExerciseCost,
        uint256 _targetPoolUtilization,
        uint256 _saturatedPoolUtilization,
        uint256 _ITMSpreadMultiplier
    )
221: function startToken(
        bool underlyingIsToken0,
        address token0,
        address token1,
        uint24 fee,
        PanopticPool panopticPool
    ) external
650: function exerciseCost(
        int24 currentTick,
        int24 oracleTick,
        TokenId positionId,
        uint128 positionBalance,
        LeftRightSigned longAmounts
    ) external view returns (LeftRightSigned exerciseFees)
1043: function exercise(
        address optionOwner,
        int128 longAmount,
        int128 shortAmount,
        int128 swappedAmount,
        int128 realizedPremium
    ) external onlyPanopticPool returns (int128)
1278: function _getRequiredCollateralSingleLeg(
        TokenId tokenId,
        uint256 index,
        uint128 positionSize,
        int24 atTick,
        uint128 poolUtilization
    ) internal view returns (uint256 required)
1311: function _getRequiredCollateralSingleLegNoPartner(
        TokenId tokenId,
        uint256 index,
        uint128 positionSize,
        int24 atTick,
        uint128 poolUtilization
    ) internal view returns (uint256 required)
1439: function _getRequiredCollateralSingleLegPartner(
        TokenId tokenId,
        uint256 index,
        uint128 positionSize,
        int24 atTick,
        uint128 poolUtilization
    ) internal view returns (uint256 required)
1510: function _computeSpread(
        TokenId tokenId,
        uint128 positionSize,
        uint256 index,
        uint256 partnerIndex,
        uint128 poolUtilization
    ) internal view returns (uint256 spreadRequirement)
1600: function _computeStrangle(
        TokenId tokenId,
        uint256 index,
        uint128 positionSize,
        int24 atTick,
        uint128 poolUtilization
    ) internal view returns (uint256 strangleRequired)
```
[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L178) | [221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221) | [650](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L650) | [1043](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043) | [1278](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1278) | [1311](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1311) | [1439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1439) | [1510](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1510) | [1600](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1600)

```solidity
File: contracts/PanopticFactory.sol

115: constructor(
        address _WETH9,
        SemiFungiblePositionManager _SFPM,
        IUniswapV3Factory _univ3Factory,
        IDonorNFT _donorNFT,
        address _poolReference,
        address _collateralReference
    )
```
[115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L115)

```solidity
File: contracts/PanopticPool.sol

291: function startPool(
        IUniswapV3Pool _univ3pool,
        address token0,
        address token1,
        CollateralTracker collateralTracker0,
        CollateralTracker collateralTracker1
    ) external
429: function _calculateAccumulatedPremia(
        address user,
        TokenId[] calldata positionIdList,
        bool computeAllPremia,
        bool includePendingPremium,
        int24 atTick
    ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances)
547: function mintOptions(
        TokenId[] calldata positionIdList,
        uint128 positionSize,
        uint64 effectiveLiquidityLimitX32,
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) external
614: function _mintOptions(
        TokenId[] calldata positionIdList,
        uint128 positionSize,
        uint64 effectiveLiquidityLimitX32,
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) internal
794: function _burnAllOptionsFrom(
        address owner,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        bool commitLongSettled,
        TokenId[] calldata positionIdList
    ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg)
826: function _burnOptions(
        bool commitLongSettled,
        TokenId tokenId,
        address owner,
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg)
955: function _burnAndHandleExercise(
        bool commitLongSettled,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        TokenId tokenId,
        uint128 positionSize,
        address owner
    )
        internal
        returns (
            LeftRightSigned realizedPremia,
            LeftRightSigned[4] memory premiaByLeg,
            LeftRightSigned paidAmounts
        )
1290: function _checkSolvencyAtTick(
        address account,
        TokenId[] calldata positionIdList,
        int24 currentTick,
        int24 atTick,
        uint256 buffer
    ) internal view returns (bool)
1465: function _checkLiquiditySpread(
        TokenId tokenId,
        uint256 leg,
        int24 tickLower,
        int24 tickUpper,
        uint64 effectiveLiquidityLimitX32
    ) internal view
1503: function _getPremia(
        TokenId tokenId,
        uint128 positionSize,
        address owner,
        bool computeAllPremia,
        int24 atTick
    )
        internal
        view
        returns (
            LeftRightSigned[4] memory premiaByLeg,
            uint256[2][4] memory premiumAccumulatorsByLeg
        )
1757: function _getAvailablePremium(
        uint256 totalLiquidity,
        LeftRightUnsigned settledTokens,
        LeftRightUnsigned grossPremiumLast,
        LeftRightUnsigned premiumOwed,
        uint256[2] memory premiumAccumulators
    ) internal pure returns (LeftRightUnsigned)
1833: function _updateSettlementPostBurn(
        address owner,
        TokenId tokenId,
        LeftRightUnsigned[4] memory collectedByLeg,
        uint128 positionSize,
        bool commitLongSettled
    ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg)
```
[291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291) | [429](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L429) | [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L547) | [614](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L614) | [794](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L794) | [826](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L826) | [955](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L955) | [1290](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1290) | [1465](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1465) | [1503](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1503) | [1757](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1757) | [1833](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833)

```solidity
File: contracts/SemiFungiblePositionManager.sol

540: function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public override
566: function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public override
680: function _validateAndForwardToAMM(
        TokenId tokenId,
        uint128 positionSize,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        bool isBurn
    ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved)
958: function _createLegInAMM(
        IUniswapV3Pool univ3pool,
        TokenId tokenId,
        uint256 leg,
        LiquidityChunk liquidityChunk,
        bool isBurn
    )
        internal
        returns (
            LeftRightSigned moved,
            LeftRightSigned itmAmounts,
            LeftRightUnsigned collectedSingleLeg
        )
1255: function _collectAndWritePositionData(
        LiquidityChunk liquidityChunk,
        IUniswapV3Pool univ3pool,
        LeftRightUnsigned currentLiquidity,
        bytes32 positionKey,
        LeftRightSigned movedInLeg,
        uint256 isLong
    ) internal returns (LeftRightUnsigned collectedChunk)
1421: function getAccountLiquidity(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper
    ) external view returns (LeftRightUnsigned accountLiquidities)
1449: function getAccountPremium(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper,
        int24 atTick,
        uint256 isLong
    ) external view returns (uint128, uint128)
1535: function getAccountFeesBase(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper
    ) external view returns (int128 feesBase0, int128 feesBase1)
```
[540](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L540) | [566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566) | [680](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L680) | [958](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L958) | [1255](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255) | [1421](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1421) | [1449](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1449) | [1535](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1535)

```solidity
File: contracts/libraries/FeesCalc.sol

97: function calculateAMMSwapFees(
        IUniswapV3Pool univ3pool,
        int24 currentTick,
        int24 tickLower,
        int24 tickUpper,
        uint128 liquidity
    ) public view returns (LeftRightSigned)
```
[97](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L97)

```solidity
File: contracts/libraries/InteractionHelper.sol

24: function doApprovals(
        SemiFungiblePositionManager sfpm,
        CollateralTracker ct0,
        CollateralTracker ct1,
        address token0,
        address token1
    ) external
48: function computeName(
        address token0,
        address token1,
        bool isToken0,
        uint24 fee,
        string memory prefix
    ) external view returns (string memory)
```
[24](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L24) | [48](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L48)

```solidity
File: contracts/libraries/PanopticMath.sol

125: function computeMedianObservedPrice(
        IUniswapV3Pool univ3pool,
        uint256 observationIndex,
        uint256 observationCardinality,
        uint256 cardinality,
        uint256 period
    ) external view returns (int24)
168: function computeInternalMedian(
        uint256 observationIndex,
        uint256 observationCardinality,
        uint256 period,
        uint256 medianData,
        IUniswapV3Pool univ3pool
    ) external view returns (int24 medianTick, uint256 updatedMedianData)
651: function getLiquidationBonus(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint160 sqrtPriceX96Twap,
        uint160 sqrtPriceX96Final,
        LeftRightSigned netExchanged,
        LeftRightSigned premia
    ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned)
768: function haircutPremia(
        address liquidatee,
        TokenId[] memory positionIdList,
        LeftRightSigned[4][] memory premiasByLeg,
        LeftRightSigned collateralRemaining,
        CollateralTracker collateral0,
        CollateralTracker collateral1,
        uint160 sqrtPriceX96Final,
        mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
    ) external returns (int256, int256)
917: function getRefundAmounts(
        address refunder,
        LeftRightSigned refundValues,
        int24 atTick,
        CollateralTracker collateral0,
        CollateralTracker collateral1
    ) external view returns (LeftRightSigned)
```
[125](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L125) | [168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L168) | [651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L651) | [768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768) | [917](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L917)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

94: function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public virtual
130: function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public virtual
```
[94](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L94) | [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L130)

```solidity
File: contracts/types/TokenId.sol

336: function addLeg(
        TokenId self,
        uint256 legIndex,
        uint256 _optionRatio,
        uint256 _asset,
        uint256 _isLong,
        uint256 _tokenType,
        uint256 _riskPartner,
        int24 _strike,
        int24 _width
    ) internal pure returns (TokenId tokenId)
```
[336](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L336)
</details>

### [N-14] Consider using descriptive `constant`s when passing zero as a function argument

In instances where utilizing a zero parameter is essential, it is recommended to employ descriptive constants or an enum instead of directly integrating zero within function calls.
This strategy aids in clearly articulating the caller's intention and minimizes the risk of errors.
Emitting zero also not recomended, as it is not clear what the intention is.

<details>
<summary><i>61 issue instances in 7 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

712: LeftRightSigned
                            .wrap(0)
```
[712](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L712)

```solidity
File: contracts/PanopticPool.sol

654: LeftRightUnsigned
            .wrap(0)
762: LeftRightUnsigned
                    .wrap(0)
861: LeftRightUnsigned.wrap(0)
870: LeftRightUnsigned.wrap(0)
893: _validatePositionList(user, positionIdList, 0)
1023: _validatePositionList(liquidatee, positionIdList, 0)
1153: _validatePositionList(msg.sender, positionIdListLiquidator, 0)
1165: LeftRightSigned
            .wrap(0)
1191: _validatePositionList(msg.sender, positionIdListExercisor, 0)
1227: _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId)
1545: LeftRightSigned
                        .wrap(0)
1567: LeftRightSigned.wrap(0)
1592: _validatePositionList(owner, positionIdList, 0)
1614: LeftRightUnsigned
                .wrap(0)
1633: LeftRightSigned
                .wrap(0)
1639: s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot())
1640: s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot())
1707: SFPM.getAccountPremium(
                    address(s_univ3pool),
                    address(this),
                    tokenId.tokenType(leg),
                    liquidityChunk.tickLower(),
                    liquidityChunk.tickUpper(),
                    type(int24).max,
                    0
                )
1725: LeftRightUnsigned
                        .wrap(0)
1774: LeftRightUnsigned
                    .wrap(0)
1929: LeftRightUnsigned
                                .wrap(0)
1934: Math.max(
                                                (int256(
                                                    grossPremiumLast.rightSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][0] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
                                                0
                                            )
1951: Math.max(
                                                (int256(
                                                    grossPremiumLast.leftSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][1] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
                                                0
                                            )
1965: LeftRightUnsigned
                                .wrap(0)
```
[654](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L654) | [762](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L762) | [861](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L861) | [870](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L870) | [893](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L893) | [1023](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1023) | [1153](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1153) | [1165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1165) | [1191](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1191) | [1227](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1227) | [1545](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1545) | [1567](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1567) | [1592](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1592) | [1614](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1614) | [1633](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1633) | [1639](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1639) | [1640](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1640) | [1707](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1707) | [1725](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1725) | [1774](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1774) | [1929](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1929) | [1934](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1934) | [1951](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1951) | [1965](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1965)

```solidity
File: contracts/SemiFungiblePositionManager.sol

645: LeftRightUnsigned.wrap(0)
648: LeftRightSigned.wrap(0)
833: LeftRightSigned.wrap(0)
848: LeftRightSigned.wrap(0)
1038: LeftRightUnsigned
                .wrap(0)
1166: LeftRightSigned
                .wrap(0)
1174: LeftRightSigned
                .wrap(0)
1214: LeftRightSigned.wrap(0)
1241: LeftRightSigned.wrap(0)
1306: LeftRightUnsigned.wrap(0)
1376: LeftRightUnsigned
                        .wrap(0)
1400: LeftRightUnsigned
                        .wrap(0)
```
[645](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L645) | [648](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L648) | [833](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L833) | [848](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L848) | [1038](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1038) | [1166](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1166) | [1174](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1174) | [1214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1214) | [1241](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1241) | [1306](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1306) | [1376](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1376) | [1400](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1400)

```solidity
File: contracts/libraries/FeesCalc.sol

115: LeftRightSigned
                .wrap(0)
```
[115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L115)

```solidity
File: contracts/libraries/PanopticMath.sol

598: LeftRightUnsigned.wrap(0)
671: PanopticMath.convertCollateralData(
                    tokenData0,
                    tokenData1,
                    0,
                    sqrtPriceX96Twap
                )
694: Math.max(premia.rightSlot(), 0)
696: Math.max(premia.leftSlot(), 0)
749: LeftRightSigned.wrap(0)
791: Math.min(collateralRemaining.rightSlot(), 0)
792: Math.min(collateralRemaining.leftSlot(), 0)
856: collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0))
857: collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1))
880: tokenId.strike(0)
881: tokenId.width(0)
882: tokenId.tokenType(0)
888: Math.max(
                            0,
                            uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
                        )
892: Math.max(
                            0,
                            uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
                        )
898: LeftRightUnsigned.wrap(0)
933: LeftRightSigned
                        .wrap(0)
951: LeftRightSigned
                        .wrap(0)
```
[598](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L598) | [671](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L671) | [694](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L694) | [696](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L696) | [749](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L749) | [791](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L791) | [792](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L792) | [856](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L856) | [857](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L857) | [880](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L880) | [881](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L881) | [882](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L882) | [888](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L888) | [892](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L892) | [898](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L898) | [933](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L933) | [951](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L951)

```solidity
File: contracts/types/LeftRight.sol

265: Math.max(right128, 0)
266: Math.max(left128, 0)
294: LeftRightUnsigned.wrap(0)
297: LeftRightUnsigned.wrap(0)
```
[265](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L265) | [266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L266) | [294](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L294) | [297](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L297)

```solidity
File: contracts/types/TokenId.sol

406: self.isLong(0)
501: self.optionRatio(0)
```
[406](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L406) | [501](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L501)
</details>

### [N-15] Custom error has no error details

Take advantage of custom error's return value property. 

An important feature of Custom Error is that values such as address, tokenID, msg.value can be written inside the () sign, providing a serious advantage in debugging and examining the revert details of dapps such as Tenderly.

<details>
<summary><i>34 issue instances in 2 files:</i></summary>

```solidity
File: contracts/libraries/Errors.sol

10: error CastingError()
13: error CollateralTokenAlreadyInitialized()
16: error DepositTooLarge()
20: error EffectiveLiquidityAboveThreshold()
23: error ExceedsMaximumRedemption()
26: error ExerciseeNotSolvent()
29: error InputListFail()
32: error InvalidSalt()
35: error InvalidTick()
38: error InvalidNotionalValue()
45: error InvalidUniswapCallback()
48: error LeftRightInputError()
51: error NoLegsExercisable()
54: error NotEnoughCollateral()
57: error PositionTooLarge()
60: error NotALongLeg()
63: error NotEnoughLiquidity()
66: error NotMarginCalled()
70: error NotOwner()
73: error NotPanopticPool()
76: error OptionsBalanceZero()
79: error PoolAlreadyInitialized()
82: error PositionAlreadyMinted()
85: error PositionCountNotZero()
88: error PriceBoundFail()
91: error ReentrantCall()
95: error StaleTWAP()
98: error TooManyPositionsOpen()
101: error TransferFailed()
105: error TicksNotInitializable()
108: error UnderOverFlow()
111: error UniswapPoolNotInitialized()
```
[10](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L10) | [13](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L13) | [16](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L16) | [20](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L20) | [23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L23) | [26](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L26) | [29](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L29) | [32](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L32) | [35](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L35) | [38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L38) | [45](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L45) | [48](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L48) | [51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L51) | [54](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L54) | [57](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L57) | [60](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L60) | [63](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L63) | [66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L66) | [70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L70) | [73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L73) | [76](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L76) | [79](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L79) | [82](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L82) | [85](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L85) | [88](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L88) | [91](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L91) | [95](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L95) | [98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L98) | [101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L101) | [105](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L105) | [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L108) | [111](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L111)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

55: error NotAuthorized()
58: error UnsafeRecipient()
```
[55](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L55) | [58](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L58)
</details>

### [N-16] Consider using OpenZeppelin's SafeCast for any casting

OpenZeppelin's has `SafeCast` library that provides functions to safely cast. Recommended to use it instead of casting directly in any case.

<details>
<summary><i>373 issue instances in 10 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

200: int256(_sellerCollateralRatio)
201: uint256(
                2230 +
                    (12500 * ratioTick) /
                    10_000 +
                    (7812 * ratioTick ** 2) /
                    10_000 ** 2 +
                    (6510 * ratioTick ** 3) /
                    10_000 ** 3
            )
262: uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS)
436: uint128(assets)
496: uint128(assets)
552: uint128(assets)
612: uint128(assets)
667: int24(
                        int256(
                            Math.unsafeDivRoundingUp(
                                uint24(positionId.width(leg) * positionId.tickSpacing()),
                                2
                            )
                        )
                    )
668: int256(
                            Math.unsafeDivRoundingUp(
                                uint24(positionId.width(leg) * positionId.tickSpacing()),
                                2
                            )
                        )
670: uint24(positionId.width(leg) * positionId.tickSpacing())
677: uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
715: int128(uint128(oracleValue0))
715: uint128(oracleValue0)
715: int128(uint128(currentValue0))
715: uint128(currentValue0)
718: int128(uint128(oracleValue1))
718: uint128(oracleValue1)
718: int128(uint128(currentValue1))
718: uint128(currentValue1)
731: int128((longAmounts.rightSlot() * fee) / DECIMALS_128)
732: int128((longAmounts.leftSlot() * fee) / DECIMALS_128)
743: int256((s_inAMM * DECIMALS) / totalAssets())
784: uint256(utilization)
790: uint256(utilization)
797: uint256(utilization)
959: uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
959: int256(totalAssets())
959: int256(assets)
977: uint256(assets)
980: uint256(-assets)
1003: int256(uint256(s_poolAssets))
1003: uint256(s_poolAssets)
1013: uint256(tokenToPay)
1020: uint256(-tokenToPay)
1028: uint128(uint256(updatedAssets))
1028: uint256(updatedAssets)
1029: uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)))
1029: uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount))
1029: int256(uint256(s_inAMM))
1029: uint256(s_inAMM)
1052: int256(uint256(s_poolAssets))
1052: uint256(s_poolAssets)
1070: uint256(tokenToPay)
1077: uint256(-tokenToPay)
1084: uint128(uint256(updatedAssets + realizedPremium))
1084: uint256(updatedAssets + realizedPremium)
1085: uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)))
1085: uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount))
1085: int256(uint256(s_inAMM))
1085: uint256(s_inAMM)
1087: int128(tokenToPay)
1110: uint256(Math.abs(intrinsicValue))
1115: int256(swapCommission)
1119: int256(
                Math.unsafeDivRoundingUp(
                    uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
                    DECIMALS
                )
            )
1121: uint256(uint128(shortAmount + longAmount))
1121: uint128(shortAmount + longAmount)
1175: uint128(-premiumAllPositions)
1184: uint256(uint128(premiumAllPositions))
1184: uint128(premiumAllPositions)
1329: int64(uint64(poolUtilization))
1329: uint64(poolUtilization)
1330: int64(uint64(poolUtilization >> 64))
1330: uint64(poolUtilization >> 64)
1491: uint256(utilization)
1585: int64(uint64(poolUtilization))
1585: uint64(poolUtilization)
1586: int64(uint64(poolUtilization >> 64))
1586: uint64(poolUtilization >> 64)
1631: uint64(poolUtilization)
1632: uint64(poolUtilization >> 64)
1637: uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0)))
1637: uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))
1637: int64(poolUtilization0 == 0 ? 1 : poolUtilization0)
1638: uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1)))
1638: uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))
1638: int64(poolUtilization1 == 0 ? 1 : poolUtilization1)
```
[200](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L200) | [201](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L201) | [262](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L262) | [436](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L436) | [496](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L496) | [552](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L552) | [612](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L612) | [667](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L667) | [668](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L668) | [670](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L670) | [677](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L677) | [715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L715) | [715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L715) | [715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L715) | [715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L715) | [718](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L718) | [718](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L718) | [718](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L718) | [718](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L718) | [731](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L731) | [732](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L732) | [743](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L743) | [784](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L784) | [790](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L790) | [797](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L797) | [959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L959) | [959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L959) | [959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L959) | [977](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L977) | [980](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L980) | [1003](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1003) | [1003](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1003) | [1013](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1013) | [1020](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1020) | [1028](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1028) | [1028](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1028) | [1029](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1029) | [1029](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1029) | [1029](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1029) | [1029](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1029) | [1052](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1052) | [1052](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1052) | [1070](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1070) | [1077](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1077) | [1084](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1084) | [1084](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1084) | [1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085) | [1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085) | [1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085) | [1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085) | [1087](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1087) | [1110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1110) | [1115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1115) | [1119](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1119) | [1121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1121) | [1121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1121) | [1175](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1175) | [1184](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1184) | [1184](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1184) | [1329](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1329) | [1329](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1329) | [1330](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1330) | [1330](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1330) | [1491](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1491) | [1585](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1585) | [1585](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1585) | [1586](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1586) | [1586](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1586) | [1631](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1631) | [1632](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1632) | [1637](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1637) | [1637](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1637) | [1637](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1637) | [1638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1638) | [1638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1638) | [1638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1638)

```solidity
File: contracts/PanopticFactory.sol

300: uint256(salt)
303: uint256(salt)
323: uint256(salt)
352: uint128(
                    Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)
                )
356: uint128(
                    Math.mulDivRoundingUp(
                        FULL_RANGE_LIQUIDITY_AMOUNT_WETH,
                        Constants.FP96,
                        currentSqrtPriceX96
                    )
                )
365: uint128(
                    Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)
                )
368: uint128(
                    Math.mulDivRoundingUp(
                        FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,
                        Constants.FP96,
                        currentSqrtPriceX96
                    )
                )
```
[300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L300) | [303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L303) | [323](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L323) | [352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L352) | [356](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L356) | [365](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L365) | [368](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L368)

```solidity
File: contracts/PanopticPool.sol

309: uint256(block.timestamp)
312: uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)
313: uint256(uint24(currentTick))
313: uint24(currentTick)
314: uint256(uint24(currentTick))
314: uint24(currentTick)
366: uint64(balanceData.leftSlot())
370: uint64(balanceData.leftSlot() >> 64)
473: uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))
477: int256(LeftRightUnsigned.unwrap(availablePremium))
730: uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64))
730: uint256(utilization0)
730: uint128(uint256(utilization1) << 64)
730: uint256(utilization1)
775: uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))
943: int256(fastOracleTick)
1144: uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)
1144: int256(uint256(_delegations.rightSlot()))
1144: uint256(_delegations.rightSlot())
1149: uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)
1149: int256(uint256(_delegations.leftSlot()))
1149: uint256(_delegations.leftSlot())
1167: int128(liquidationBonus0)
1168: int128(liquidationBonus1)
1222: uint128(delegatedAmounts.rightSlot())
1223: uint128(delegatedAmounts.leftSlot())
1265: uint128(delegatedAmounts.rightSlot())
1266: uint128(delegatedAmounts.leftSlot())
1348: uint256(tokenData1.rightSlot())
1353: uint256(tokenData1.leftSlot())
1487: uint256(totalLiquidity)
1492: uint256(effectiveLiquidityLimitX32)
1548: int128(
                                int256(
                                    ((premiumAccumulatorsByLeg[leg][0] -
                                        premiumAccumulatorLast.rightSlot()) *
                                        (liquidityChunk.liquidity())) / 2 ** 64
                                )
                            )
1549: int256(
                                    ((premiumAccumulatorsByLeg[leg][0] -
                                        premiumAccumulatorLast.rightSlot()) *
                                        (liquidityChunk.liquidity())) / 2 ** 64
                                )
1557: int128(
                                int256(
                                    ((premiumAccumulatorsByLeg[leg][1] -
                                        premiumAccumulatorLast.leftSlot()) *
                                        (liquidityChunk.liquidity())) / 2 ** 64
                                )
                            )
1558: int256(
                                    ((premiumAccumulatorsByLeg[leg][1] -
                                        premiumAccumulatorLast.leftSlot()) *
                                        (liquidityChunk.liquidity())) / 2 ** 64
                                )
1635: int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64))
1635: int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)
1636: int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64))
1636: int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)
1651: uint256(LeftRightSigned.unwrap(realizedPremia))
1728: uint128(
                                (grossCurrent[0] *
                                    positionLiquidity +
                                    grossPremiumLast.rightSlot() *
                                    totalLiquidityBefore) / (totalLiquidity)
                            )
1736: uint128(
                                (grossCurrent[1] *
                                    positionLiquidity +
                                    grossPremiumLast.leftSlot() *
                                    totalLiquidityBefore) / (totalLiquidity)
                            )
1777: uint128(
                            Math.min(
                                (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /
                                    (accumulated0 == 0 ? type(uint256).max : accumulated0),
                                premiumOwed.rightSlot()
                            )
                        )
1779: uint256(premiumOwed.rightSlot())
1786: uint128(
                            Math.min(
                                (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /
                                    (accumulated1 == 0 ? type(uint256).max : accumulated1),
                                premiumOwed.leftSlot()
                            )
                        )
1788: uint256(premiumOwed.leftSlot())
1867: uint256(
                                LeftRightSigned.unwrap(
                                    LeftRightSigned
                                        .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
                                        .sub(legPremia)
                                )
                            )
1870: int256(LeftRightUnsigned.unwrap(settledTokens))
1892: uint256(LeftRightSigned.unwrap(legPremia))
1901: int256(LeftRightUnsigned.unwrap(availablePremium))
1932: uint128(
                                        uint256(
                                            Math.max(
                                                (int256(
                                                    grossPremiumLast.rightSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][0] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
                                                0
                                            )
                                        ) / totalLiquidity
                                    )
1933: uint256(
                                            Math.max(
                                                (int256(
                                                    grossPremiumLast.rightSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][0] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
                                                0
                                            )
                                        )
1935: int256(
                                                    grossPremiumLast.rightSlot() *
                                                        totalLiquidityBefore
                                                )
1939: int256(
                                                        _premiumAccumulatorsByLeg[_leg][0] *
                                                            positionLiquidity
                                                    )
1942: int256(legPremia.rightSlot() * 2 ** 64)
1949: uint128(
                                        uint256(
                                            Math.max(
                                                (int256(
                                                    grossPremiumLast.leftSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][1] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
                                                0
                                            )
                                        ) / totalLiquidity
                                    )
1950: uint256(
                                            Math.max(
                                                (int256(
                                                    grossPremiumLast.leftSlot() *
                                                        totalLiquidityBefore
                                                ) -
                                                    int256(
                                                        _premiumAccumulatorsByLeg[_leg][1] *
                                                            positionLiquidity
                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
                                                0
                                            )
                                        )
1952: int256(
                                                    grossPremiumLast.leftSlot() *
                                                        totalLiquidityBefore
                                                )
1956: int256(
                                                        _premiumAccumulatorsByLeg[_leg][1] *
                                                            positionLiquidity
                                                    )
1959: int256(legPremia.leftSlot())
1967: uint128(premiumAccumulatorsByLeg[_leg][0])
1968: uint128(premiumAccumulatorsByLeg[_leg][1])
```
[309](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L309) | [312](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L312) | [313](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L313) | [313](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L313) | [314](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L314) | [314](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L314) | [366](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L366) | [370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L370) | [473](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L473) | [477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L477) | [730](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L730) | [730](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L730) | [730](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L730) | [730](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L730) | [775](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L775) | [943](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L943) | [1144](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1144) | [1144](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1144) | [1144](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1144) | [1149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1149) | [1149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1149) | [1149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1149) | [1167](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1167) | [1168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1168) | [1222](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1222) | [1223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1223) | [1265](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1265) | [1266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1266) | [1348](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1348) | [1353](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1353) | [1487](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1487) | [1492](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1492) | [1548](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1548) | [1549](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1549) | [1557](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1557) | [1558](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1558) | [1635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1635) | [1635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1635) | [1636](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1636) | [1636](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1636) | [1651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1651) | [1728](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1728) | [1736](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1736) | [1777](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1777) | [1779](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1779) | [1786](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1786) | [1788](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1788) | [1867](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1867) | [1870](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1870) | [1892](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1892) | [1901](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1901) | [1932](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1932) | [1933](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1933) | [1935](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1935) | [1939](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1939) | [1942](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1942) | [1949](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1949) | [1950](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1950) | [1952](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1952) | [1956](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1956) | [1959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1959) | [1967](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1967) | [1968](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1968)

```solidity
File: contracts/SemiFungiblePositionManager.sol

388: uint256(poolId)
453: uint256(amount0Delta)
453: uint256(amount1Delta)
607: uint128(amount)
939: uint128(type(int128).max)
939: uint128(type(int128).max)
1169: int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))
1169: int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity))
1172: int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))
1172: int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity))
1176: int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity)))
1176: int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))
1177: int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity)))
1177: int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))
1214: int128(int256(amount0))
1214: int256(amount0)
1215: int128(int256(amount1))
1215: int256(amount1)
1241: int128(int256(amount0))
1241: int256(amount0)
1242: int128(int256(amount1))
1242: int256(amount1)
1288: uint128(amountToCollect.rightSlot())
1289: uint128(amountToCollect.leftSlot())
1297: uint128(-movedInLeg.rightSlot())
1300: uint128(-movedInLeg.leftSlot())
1493: uint256(
                            LeftRightSigned.unwrap(feesBase.subRect(s_accountFeesBase[positionKey]))
                        )
1567: uint64(s_AddrToPoolIdData[univ3pool])
```
[388](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L388) | [453](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L453) | [453](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L453) | [607](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L607) | [939](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L939) | [939](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L939) | [1169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1169) | [1169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1169) | [1172](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1172) | [1172](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1172) | [1176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1176) | [1176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1176) | [1177](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1177) | [1177](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1177) | [1214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1214) | [1214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1214) | [1215](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1215) | [1215](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1215) | [1241](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1241) | [1241](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1241) | [1242](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1242) | [1242](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1242) | [1288](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1288) | [1289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1289) | [1297](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1297) | [1300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1300) | [1493](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1493) | [1567](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1567)

```solidity
File: contracts/libraries/FeesCalc.sol

69: int256(amount0)
70: int256(amount1)
74: int256(amount0)
75: int256(amount1)
117: int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity)))
117: int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))
118: int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity)))
118: int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))
```
[69](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L69) | [70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L70) | [74](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L74) | [75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L75) | [117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L117) | [117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L117) | [118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L118) | [118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L118)

```solidity
File: contracts/libraries/Math.sol

83: uint256(x)
83: uint256(-x)
130: uint256(-int256(tick))
130: int256(tick)
130: uint256(int256(tick))
130: int256(tick)
131: uint256(int256(Constants.MAX_V3POOL_TICK))
131: int256(Constants.MAX_V3POOL_TICK)
179: uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1))
197: uint256(liquidityChunk.liquidity())
297: uint128(toDowncast)
303: uint128(toDowncast)
312: int128(toCast)
319: int128(toCast)
326: uint256(type(int256).max)
327: int256(toCast)
758: uint256(left + (right - left) / 2)
760: uint256(i)
761: uint256(j)
763: uint256(i)
763: uint256(j)
763: uint256(j)
763: uint256(i)
778: int256(0)
778: int256(data.length - 1)
```
[83](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L83) | [83](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L83) | [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L130) | [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L130) | [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L130) | [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L130) | [131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L131) | [131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L131) | [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L179) | [197](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L197) | [297](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L297) | [303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L303) | [312](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L312) | [319](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L319) | [326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L326) | [327](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L327) | [758](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L758) | [760](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L760) | [761](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L761) | [763](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L763) | [763](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L763) | [763](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L763) | [763](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L763) | [778](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L778) | [778](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L778)

```solidity
File: contracts/libraries/PanopticMath.sol

50: uint64(uint160(univ3pool) >> 112)
50: uint160(univ3pool)
51: uint64(uint24(tickSpacing))
51: uint24(tickSpacing)
62: uint48(poolId)
77: uint160(addr)
102: uint248(existingHash)
103: uint248(uint256(keccak256(abi.encode(tokenId))))
103: uint256(keccak256(abi.encode(tokenId)))
107: uint256(updatedHash)
108: uint256(updatedHash)
139: uint256(
                        (int256(observationIndex) - int256(i * period)) +
                            int256(observationCardinality)
                    )
140: int256(observationIndex)
140: int256(i * period)
141: int256(observationCardinality)
151: int256(timestamps[i] - timestamps[i + 1])
155: int24(Math.sort(ticks)[cardinality / 2])
178: int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24)))
178: uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))
178: uint24(medianData >> (192 + 3 * 3))
179: int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))
179: uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24))
179: uint24(medianData >> (192 + 3 * 4))
183: uint256(uint40(medianData >> 216))
183: uint40(medianData >> 216)
187: uint256(
                            int256(observationIndex) - int256(1) + int256(observationCardinality)
                        )
188: int256(observationIndex)
188: int256(1)
188: int256(observationCardinality)
194: int24(
                        (tickCumulative_last - tickCumulative_old) /
                            int256(timestamp_last - timestamp_old)
                    )
196: int256(timestamp_last - timestamp_old)
200: uint24(medianData >> 192)
217: int24(uint24(medianData >> (rank * 24)))
217: uint24(medianData >> (rank * 24))
228: uint256(newOrderMap)
229: uint256(uint192(medianData << 24))
229: uint192(medianData << 24)
230: uint256(uint24(lastObservedTick))
230: uint24(lastObservedTick)
249: uint32(((i + 1) * twapWindow) / 20)
257: int24(
                    (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
                )
258: int56(uint56(twapWindow / 20))
258: uint56(twapWindow / 20)
266: int24(sortedTicks[10])
324: uint256(positionSize)
377: int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))
377: int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2))
377: uint24(width)
377: uint24(tickSpacing)
481: uint128(notional)
495: uint256(sqrtPriceX96)
512: uint256(sqrtPriceX96)
530: uint256(sqrtPriceX96)
553: uint256(sqrtPriceX96)
585: uint128(tokenId.optionRatio(legIndex))
591: uint128(tokenId.optionRatio(legIndex))
681: int256(Math.mulDiv128(bonusCross, requiredRatioX128))
683: int256(
                    PanopticMath.convert0to1(
                        Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
                        sqrtPriceX96Final
                    )
                )
693: int256(uint256(tokenData0.rightSlot()))
693: uint256(tokenData0.rightSlot())
695: int256(uint256(tokenData1.rightSlot()))
695: uint256(tokenData1.rightSlot())
698: int256(netExchanged.rightSlot())
699: int256(netExchanged.leftSlot())
744: int256(netExchanged.rightSlot())
745: int256(netExchanged.leftSlot())
749: int128(balance0 - paid0)
750: int128(balance1 - paid1)
856: int128(haircut0)
857: int128(haircut1)
870: uint128(-_premiasByLeg[i][leg].rightSlot())
870: uint256(haircut0)
871: uint128(longPremium.rightSlot())
874: uint128(-_premiasByLeg[i][leg].leftSlot())
874: uint256(haircut1)
875: uint128(longPremium.leftSlot())
890: uint128(-_premiasByLeg[i][leg].rightSlot())
894: uint128(-_premiasByLeg[i][leg].leftSlot())
898: uint128(settled0)
899: uint128(settled1)
929: int256(collateral0.convertToAssets(collateral0.balanceOf(refunder)))
935: int128(refundValues.rightSlot() - balanceShortage)
937: int128(
                                int256(
                                    PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
                                ) + refundValues.leftSlot()
                            )
938: int256(
                                    PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
                                )
939: uint256(balanceShortage)
947: int256(collateral1.convertToAssets(collateral1.balanceOf(refunder)))
953: int128(refundValues.leftSlot() - balanceShortage)
955: int128(
                                int256(
                                    PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
                                ) + refundValues.rightSlot()
                            )
956: int256(
                                    PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
                                )
957: uint256(balanceShortage)
```
[50](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L50) | [50](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L50) | [51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L51) | [51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L51) | [62](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L62) | [77](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L77) | [102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L102) | [103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L103) | [103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L103) | [107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L107) | [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L108) | [139](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L139) | [140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140) | [140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140) | [141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L141) | [151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L151) | [155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L155) | [178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178) | [178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178) | [178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178) | [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179) | [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179) | [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179) | [183](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L183) | [183](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L183) | [187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L187) | [188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L188) | [188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L188) | [188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L188) | [194](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L194) | [196](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L196) | [200](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L200) | [217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L217) | [217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L217) | [228](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L228) | [229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L229) | [229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L229) | [230](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L230) | [230](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L230) | [249](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L249) | [257](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L257) | [258](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L258) | [258](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L258) | [266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L266) | [324](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L324) | [377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L377) | [377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L377) | [377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L377) | [377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L377) | [481](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L481) | [495](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L495) | [512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L512) | [530](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L530) | [553](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L553) | [585](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L585) | [591](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L591) | [681](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L681) | [683](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L683) | [693](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L693) | [693](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L693) | [695](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L695) | [695](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L695) | [698](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L698) | [699](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L699) | [744](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L744) | [745](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L745) | [749](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L749) | [750](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L750) | [856](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L856) | [857](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L857) | [870](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L870) | [870](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L870) | [871](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L871) | [874](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L874) | [874](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L874) | [875](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L875) | [890](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L890) | [894](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L894) | [898](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L898) | [899](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L899) | [929](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L929) | [935](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L935) | [937](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L937) | [938](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L938) | [939](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L939) | [947](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L947) | [953](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L953) | [955](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L955) | [956](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L956) | [957](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L957)

```solidity
File: contracts/types/LeftRight.sol

40: uint128(LeftRightUnsigned.unwrap(self))
47: int128(LeftRightSigned.unwrap(self))
69: uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)
69: uint128(LeftRightUnsigned.unwrap(self))
89: int256(int128(LeftRightSigned.unwrap(self)) + right)
89: int128(LeftRightSigned.unwrap(self))
102: uint128(LeftRightUnsigned.unwrap(self) >> 128)
109: int128(LeftRightSigned.unwrap(self) >> 128)
126: uint256(left)
136: int256(left)
162: uint128(LeftRightUnsigned.unwrap(z))
162: uint128(LeftRightUnsigned.unwrap(x))
185: uint128(LeftRightUnsigned.unwrap(z))
185: uint128(LeftRightUnsigned.unwrap(x))
196: int256(uint256(x.leftSlot()))
196: uint256(x.leftSlot())
197: int128(left)
201: int256(uint256(x.rightSlot()))
201: uint256(x.rightSlot())
202: int128(right)
216: int256(x.leftSlot())
217: int128(left256)
219: int256(x.rightSlot())
220: int128(right256)
234: int256(x.leftSlot())
235: int128(left256)
237: int256(x.rightSlot())
238: int128(right256)
256: int256(x.leftSlot())
257: int128(left256)
259: int256(x.rightSlot())
260: int128(right256)
265: int128(Math.max(right128, 0))
266: int128(Math.max(left128, 0))
285: uint256(x.rightSlot())
286: uint256(x.leftSlot())
287: uint256(y.rightSlot())
288: uint256(y.leftSlot())
```
[40](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L40) | [47](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L47) | [69](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L69) | [69](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L69) | [89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L89) | [89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L89) | [102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L102) | [109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L109) | [126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L126) | [136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L136) | [162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L162) | [162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L162) | [185](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L185) | [185](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L185) | [196](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L196) | [196](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L196) | [197](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L197) | [201](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L201) | [201](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L201) | [202](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L202) | [216](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L216) | [217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L217) | [219](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L219) | [220](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L220) | [234](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L234) | [235](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L235) | [237](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L237) | [238](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L238) | [256](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L256) | [257](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L257) | [259](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L259) | [260](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L260) | [265](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L265) | [266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L266) | [285](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L285) | [286](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L286) | [287](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L287) | [288](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L288)

```solidity
File: contracts/types/LiquidityChunk.sol

78: uint256(uint24(_tickLower))
78: uint24(_tickLower)
79: uint256(uint24(_tickUpper))
79: uint24(_tickUpper)
80: uint256(amount)
109: uint256(uint24(_tickLower))
109: uint24(_tickLower)
126: uint256(uint24(_tickUpper))
126: uint24(_tickUpper)
173: int24(int256(LiquidityChunk.unwrap(self) >> 232))
173: int256(LiquidityChunk.unwrap(self) >> 232)
182: int24(int256(LiquidityChunk.unwrap(self) >> 208))
182: int256(LiquidityChunk.unwrap(self) >> 208)
191: uint128(LiquidityChunk.unwrap(self))
```
[78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L78) | [78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L78) | [79](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L79) | [79](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L79) | [80](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L80) | [109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L109) | [109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L109) | [126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L126) | [126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L126) | [173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L173) | [173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L173) | [182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L182) | [182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L182) | [191](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L191)

```solidity
File: contracts/types/TokenId.sol

89: uint64(TokenId.unwrap(self))
98: int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16))
98: uint24((TokenId.unwrap(self) >> 48) % 2 ** 16)
110: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2)
120: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128)
130: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2)
140: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2)
150: uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4)
160: int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)))
160: int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12))
171: int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096))
171: int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096)
195: uint256(uint24(_tickSpacing))
195: uint24(_tickSpacing)
212: uint256(_asset % 2)
229: uint256(_optionRatio % 128)
263: uint256(_tokenType % 2)
281: uint256(_riskPartner % 4)
300: uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))
300: int256(_strike)
320: uint256(uint24(_width) % 4096)
320: uint24(_width)
521: uint48(chunkData >> (48 * i))
521: uint48(chunkData >> (48 * j))
```
[89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L89) | [98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L98) | [98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L98) | [110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L110) | [120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120) | [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130) | [140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140) | [150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150) | [160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L160) | [160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L160) | [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171) | [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171) | [195](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L195) | [195](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L195) | [212](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L212) | [229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L229) | [263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L263) | [281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L281) | [300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L300) | [300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L300) | [320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L320) | [320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L320) | [521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L521) | [521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L521)
</details>

### [N-17] Consider using `delete` rather than assigning `zero` to clear values

Rather than merely setting a variable to zero, you can use the `delete` keyword to reset it to its default value.
This action is especially relevant for complex data types like arrays or mappings where the default is not necessarily zero.
Using `delete` not only provides explicit clarity that you intend to reset a variable, but it can also result in more concise and intuitive code.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: contracts/libraries/PanopticMath.sol

850: collateralDelta0 = 0
851: collateralDelta1 = 0
```
[850](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L850) | [851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L851)

```solidity
File: contracts/types/TokenId.sol

377: optionRatios = 0
```
[377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L377)
</details>

### [N-18] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

<details>
<summary><i>4 issue instances in 4 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

178: constructor(
        uint256 _commissionFee,
        uint256 _sellerCollateralRatio,
        uint256 _buyerCollateralRatio,
        int256 _forceExerciseCost,
        uint256 _targetPoolUtilization,
        uint256 _saturatedPoolUtilization,
        uint256 _ITMSpreadMultiplier
    )
```
[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L178)

```solidity
File: contracts/PanopticFactory.sol

115: constructor(
        address _WETH9,
        SemiFungiblePositionManager _SFPM,
        IUniswapV3Factory _univ3Factory,
        IDonorNFT _donorNFT,
        address _poolReference,
        address _collateralReference
    )
```
[115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L115)

```solidity
File: contracts/PanopticPool.sol

280: constructor(SemiFungiblePositionManager _sfpm)
```
[280](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L280)

```solidity
File: contracts/SemiFungiblePositionManager.sol

341: constructor(IUniswapV3Factory _factory)
```
[341](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L341)
</details>

### [N-19] Consider moving duplicated strings to constants

Reusing string literals in this manner can lead to inconsistencies and makes the code harder to maintain.
It's recommended to define such strings as constants, which promotes easier updates and ensures uniformity across the codebase.

<details>
<summary><i>3 issue instances in 1 files:</i></summary>

```solidity
File: contracts/libraries/InteractionHelper.sol

63: "???"
68: "???"
100: "???"
```
[63](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L63) | [68](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L68) | [100](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L100)
</details>

### [N-20] Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas.
The cases below are where there currently is at most one return statement, which is ideal for named returns.

<details>
<summary><i>104 issue instances in 13 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

289: function name() external view returns (string memory)
303: function symbol() external view returns (string memory)
310: function decimals() external view returns (uint8)
323: function transfer(
        address recipient,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool)
341: function transferFrom(
        address from,
        address to,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool)
1043: function exercise(
        address optionOwner,
        int128 longAmount,
        int128 shortAmount,
        int128 swappedAmount,
        int128 realizedPremium
    ) external onlyPanopticPool returns (int128)
```
[289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L289) | [303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L303) | [310](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L310) | [323](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L323) | [341](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L341) | [1043](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043)

```solidity
File: contracts/PanopticFactory.sol

159: function owner() external view returns (address)
335: function _mintFullRange(
        IUniswapV3Pool v3Pool,
        address token0,
        address token1,
        uint24 fee
    ) internal returns (uint256, uint256)
420: function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool)
```
[159](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L159) | [335](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L335) | [420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L420)

```solidity
File: contracts/PanopticPool.sol

381: function calculateAccumulatedFeesBatch(
        address user,
        bool includePendingPremium,
        TokenId[] calldata positionIdList
    ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory)
499: function _getSlippageLimits(
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) internal pure returns (int24, int24)
677: function _mintInSFPMAndUpdateCollateral(
        TokenId tokenId,
        uint128 positionSize,
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) internal returns (uint128)
706: function _payCommissionAndWriteData(
        TokenId tokenId,
        uint128 positionSize,
        LeftRightSigned totalSwapped
    ) internal returns (uint128)
1290: function _checkSolvencyAtTick(
        address account,
        TokenId[] calldata positionIdList,
        int24 currentTick,
        int24 atTick,
        uint256 buffer
    ) internal view returns (bool)
1425: function univ3pool() external view returns (IUniswapV3Pool)
1437: function collateralToken1() external view returns (CollateralTracker)
1757: function _getAvailablePremium(
        uint256 totalLiquidity,
        LeftRightUnsigned settledTokens,
        LeftRightUnsigned grossPremiumLast,
        LeftRightUnsigned premiumOwed,
        uint256[2] memory premiumAccumulators
    ) internal pure returns (LeftRightUnsigned)
```
[381](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L381) | [499](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L499) | [677](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L677) | [706](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L706) | [1290](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1290) | [1425](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1425) | [1437](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1437) | [1757](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1757)

```solidity
File: contracts/SemiFungiblePositionManager.sol

1449: function getAccountPremium(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper,
        int24 atTick,
        uint256 isLong
    ) external view returns (uint128, uint128)
```
[1449](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1449)

```solidity
File: contracts/libraries/FeesCalc.sol

97: function calculateAMMSwapFees(
        IUniswapV3Pool univ3pool,
        int24 currentTick,
        int24 tickLower,
        int24 tickUpper,
        uint128 liquidity
    ) public view returns (LeftRightSigned)
```
[97](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L97)

```solidity
File: contracts/libraries/InteractionHelper.sol

48: function computeName(
        address token0,
        address token1,
        bool isToken0,
        uint24 fee,
        string memory prefix
    ) external view returns (string memory)
91: function computeSymbol(
        address token,
        string memory prefix
    ) external view returns (string memory)
107: function computeDecimals(address token) external view returns (uint8)
```
[48](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L48) | [91](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L91) | [107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L107)

```solidity
File: contracts/libraries/Math.sol

25: function min24(int24 a, int24 b) internal pure returns (int24)
33: function max24(int24 a, int24 b) internal pure returns (int24)
41: function min(uint256 a, uint256 b) internal pure returns (uint256)
49: function min(int256 a, int256 b) internal pure returns (int256)
57: function max(uint256 a, uint256 b) internal pure returns (uint256)
65: function max(int256 a, int256 b) internal pure returns (int256)
73: function abs(int256 x) internal pure returns (int256)
81: function absUint(int256 x) internal pure returns (uint256)
128: function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160)
191: function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256)
207: function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256)
241: function getLiquidityForAmount0(
        int24 tickLower,
        int24 tickUpper,
        uint256 amount0
    ) internal pure returns (LiquidityChunk)
271: function getLiquidityForAmount1(
        int24 tickLower,
        int24 tickUpper,
        uint256 amount1
    ) internal pure returns (LiquidityChunk)
325: function toInt256(uint256 toCast) internal pure returns (int256)
458: function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256)
521: function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256)
598: function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256)
675: function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256)
776: function sort(int256[] memory data) internal pure returns (int256[] memory)
```
[25](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L25) | [33](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L33) | [41](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L41) | [49](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L49) | [57](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L57) | [65](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L65) | [73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L73) | [81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L81) | [128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L128) | [191](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L191) | [207](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L207) | [241](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L241) | [271](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L271) | [325](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L325) | [458](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L458) | [521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L521) | [598](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L598) | [675](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L675) | [776](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L776)

```solidity
File: contracts/libraries/PanopticMath.sol

47: function getPoolId(address univ3pool) internal view returns (uint64)
59: function incrementPoolPattern(uint64 poolId) internal pure returns (uint64)
75: function numberOfLeadingHexZeros(address addr) external pure returns (uint256)
92: function updatePositionsHash(
        uint256 existingHash,
        TokenId tokenId,
        bool addFlag
    ) internal pure returns (uint256)
125: function computeMedianObservedPrice(
        IUniswapV3Pool univ3pool,
        uint256 observationIndex,
        uint256 observationCardinality,
        uint256 cardinality,
        uint256 period
    ) external view returns (int24)
241: function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24)
289: function getLiquidityChunk(
        TokenId tokenId,
        uint256 legIndex,
        uint128 positionSize
    ) internal pure returns (LiquidityChunk)
371: function getRangesFromStrike(
        int24 width,
        int24 tickSpacing
    ) internal pure returns (int24, int24)
419: function convertCollateralData(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint256 tokenType,
        uint160 sqrtPriceX96
    ) internal pure returns (uint256, uint256)
445: function convertCollateralData(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint256 tokenType,
        int24 tick
    ) internal pure returns (uint256, uint256)
468: function convertNotional(
        uint128 contractSize,
        int24 tickLower,
        int24 tickUpper,
        uint256 asset
    ) internal pure returns (uint128)
490: function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256)
507: function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256)
524: function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256)
547: function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256)
574: function getAmountsMoved(
        TokenId tokenId,
        uint128 positionSize,
        uint256 legIndex
    ) internal pure returns (LeftRightUnsigned)
651: function getLiquidationBonus(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint160 sqrtPriceX96Twap,
        uint160 sqrtPriceX96Final,
        LeftRightSigned netExchanged,
        LeftRightSigned premia
    ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned)
768: function haircutPremia(
        address liquidatee,
        TokenId[] memory positionIdList,
        LeftRightSigned[4][] memory premiasByLeg,
        LeftRightSigned collateralRemaining,
        CollateralTracker collateral0,
        CollateralTracker collateral1,
        uint160 sqrtPriceX96Final,
        mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
    ) external returns (int256, int256)
917: function getRefundAmounts(
        address refunder,
        LeftRightSigned refundValues,
        int24 atTick,
        CollateralTracker collateral0,
        CollateralTracker collateral1
    ) external view returns (LeftRightSigned)
```
[47](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L47) | [59](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L59) | [75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L75) | [92](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L92) | [125](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L125) | [241](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L241) | [289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L289) | [371](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L371) | [419](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L419) | [445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L445) | [468](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L468) | [490](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L490) | [507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L507) | [524](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L524) | [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L547) | [574](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L574) | [651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L651) | [768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768) | [917](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L917)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

200: function supportsInterface(bytes4 interfaceId) public pure returns (bool)
```
[200](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L200)

```solidity
File: contracts/tokens/ERC20Minimal.sol

49: function approve(address spender, uint256 amount) public returns (bool)
61: function transfer(address to, uint256 amount) public virtual returns (bool)
81: function transferFrom(address from, address to, uint256 amount) public virtual returns (bool)
```
[49](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L49) | [61](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L61) | [81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L81)

```solidity
File: contracts/types/LeftRight.sol

39: function rightSlot(LeftRightUnsigned self) internal pure returns (uint128)
46: function rightSlot(LeftRightSigned self) internal pure returns (int128)
59: function toRightSlot(
        LeftRightUnsigned self,
        uint128 right
    ) internal pure returns (LeftRightUnsigned)
78: function toRightSlot(
        LeftRightSigned self,
        int128 right
    ) internal pure returns (LeftRightSigned)
101: function leftSlot(LeftRightUnsigned self) internal pure returns (uint128)
108: function leftSlot(LeftRightSigned self) internal pure returns (int128)
121: function toLeftSlot(
        LeftRightUnsigned self,
        uint128 left
    ) internal pure returns (LeftRightUnsigned)
134: function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned)
279: function addCapped(
        LeftRightUnsigned x,
        LeftRightUnsigned dx,
        LeftRightUnsigned y,
        LeftRightUnsigned dy
    ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned)
```
[39](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L39) | [46](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L46) | [59](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L59) | [78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L78) | [101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L101) | [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L108) | [121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L121) | [134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L134) | [279](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L279)

```solidity
File: contracts/types/LiquidityChunk.sol

70: function createChunk(
        int24 _tickLower,
        int24 _tickUpper,
        uint128 amount
    ) internal pure returns (LiquidityChunk)
89: function addLiquidity(
        LiquidityChunk self,
        uint128 amount
    ) internal pure returns (LiquidityChunk)
102: function addTickLower(
        LiquidityChunk self,
        int24 _tickLower
    ) internal pure returns (LiquidityChunk)
118: function addTickUpper(
        LiquidityChunk self,
        int24 _tickUpper
    ) internal pure returns (LiquidityChunk)
135: function updateTickLower(
        LiquidityChunk self,
        int24 _tickLower
    ) internal pure returns (LiquidityChunk)
151: function updateTickUpper(
        LiquidityChunk self,
        int24 _tickUpper
    ) internal pure returns (LiquidityChunk)
171: function tickLower(LiquidityChunk self) internal pure returns (int24)
180: function tickUpper(LiquidityChunk self) internal pure returns (int24)
189: function liquidity(LiquidityChunk self) internal pure returns (uint128)
```
[70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L70) | [89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L89) | [102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L102) | [118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L118) | [135](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L135) | [151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L151) | [171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L171) | [180](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L180) | [189](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L189)

```solidity
File: contracts/types/TokenId.sol

87: function poolId(TokenId self) internal pure returns (uint64)
96: function tickSpacing(TokenId self) internal pure returns (int24)
108: function asset(TokenId self, uint256 legIndex) internal pure returns (uint256)
118: function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256)
128: function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256)
138: function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256)
148: function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256)
158: function strike(TokenId self, uint256 legIndex) internal pure returns (int24)
169: function width(TokenId self, uint256 legIndex) internal pure returns (int24)
183: function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId)
193: function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId)
205: function addAsset(
        TokenId self,
        uint256 _asset,
        uint256 legIndex
    ) internal pure returns (TokenId)
221: function addOptionRatio(
        TokenId self,
        uint256 _optionRatio,
        uint256 legIndex
    ) internal pure returns (TokenId)
240: function addIsLong(
        TokenId self,
        uint256 _isLong,
        uint256 legIndex
    ) internal pure returns (TokenId)
255: function addTokenType(
        TokenId self,
        uint256 _tokenType,
        uint256 legIndex
    ) internal pure returns (TokenId)
273: function addRiskPartner(
        TokenId self,
        uint256 _riskPartner,
        uint256 legIndex
    ) internal pure returns (TokenId)
291: function addStrike(
        TokenId self,
        int24 _strike,
        uint256 legIndex
    ) internal pure returns (TokenId)
310: function addWidth(
        TokenId self,
        int24 _width,
        uint256 legIndex
    ) internal pure returns (TokenId)
366: function flipToBurnToken(TokenId self) internal pure returns (TokenId)
404: function countLongs(TokenId self) internal pure returns (uint256)
432: function countLegs(TokenId self) internal pure returns (uint256)
464: function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId)
```
[87](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L87) | [96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L96) | [108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L108) | [118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L118) | [128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L128) | [138](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L138) | [148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L148) | [158](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L158) | [169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L169) | [183](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L183) | [193](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L193) | [205](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L205) | [221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L221) | [240](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L240) | [255](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L255) | [273](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L273) | [291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L291) | [310](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L310) | [366](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L366) | [404](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L404) | [432](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L432) | [464](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L464)
</details>

### [N-21] Expressions for constant values should use `immutable` rather than `constant`

While it does not save gas for some simple binary expressions because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and immutable variables, and they should each be used in their appropriate contexts.
`constant`s should be used for literal values written into the code, and immutable variables should be used for expressions, or values calculated in, or passed into the constructor.

<details>
<summary><i>6 issue instances in 4 files:</i></summary>

```solidity
File: contracts/PanopticPool.sol

103: int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1
105: int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1
165: uint64 internal constant MAX_SPREAD = 9 * (2 ** 32)
```
[103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L103) | [105](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L105) | [165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L165)

```solidity
File: contracts/libraries/Math.sol

15: uint256 internal constant MAX_UINT256 = 2 ** 256 - 1
```
[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L15)

```solidity
File: contracts/libraries/PanopticMath.sol

23: uint256 internal constant MAX_UINT256 = 2 ** 256 - 1
```
[23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L23)

```solidity
File: contracts/types/LeftRight.sol

26: int256 internal constant LEFT_HALF_BIT_MASK_INT =
        int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000))
```
[26](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L26)
</details>

### [N-22] Consider using named function arguments

When calling functions in external contracts with multiple arguments, consider using named function parameters, rather than positional ones.

<details>
<summary><i>169 issue instances in 11 files:</i></summary>

```solidity
File: contracts/CollateralTracker.sol

292: InteractionHelper.computeName(
                s_univ3token0,
                s_univ3token1,
                s_underlyingIsToken0,
                s_poolFee,
                NAME_PREFIX
            )
305: InteractionHelper.computeSymbol(s_underlyingToken, TICKER_PREFIX)
380: Math.mulDiv(assets, totalSupply, totalAssets())
387: Math.mulDiv(shares, totalAssets(), totalSupply)
402: Math.mulDiv(
                assets * (DECIMALS - COMMISSION_FEE),
                totalSupply,
                totalAssets() * DECIMALS
            )
424: SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        )
462: Math.mulDivRoundingUp(
                shares * DECIMALS,
                totalAssets(),
                totalSupply * (DECIMALS - COMMISSION_FEE)
            )
484: SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        )
521: Math.mulDivRoundingUp(assets, supply, totalAssets())
556: SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        )
616: SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        )
669: Math.unsafeDivRoundingUp(
                                uint24(positionId.width(leg) * positionId.tickSpacing()),
                                2
                            )
687: PanopticMath.getLiquidityChunk(
                        positionId,
                        leg,
                        positionBalance
                    )
693: Math.getAmountsForLiquidity(
                        currentTick,
                        liquidityChunk
                    )
698: Math.getAmountsForLiquidity(
                        oracleTick,
                        liquidityChunk
                    )
956: Math.mulDiv(
                    assets,
                    totalSupply - delegateeBalance,
                    uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
                )
1012: Math.mulDivRoundingUp(
                    uint256(tokenToPay),
                    totalSupply,
                    totalAssets()
                )
1069: Math.mulDivRoundingUp(
                    uint256(tokenToPay),
                    totalSupply,
                    totalAssets()
                )
1109: Math.unsafeDivRoundingUp(
                    s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),
                    DECIMALS
                )
1120: Math.unsafeDivRoundingUp(
                    uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
                    DECIMALS
                )
1322: PanopticMath.getAmountsMoved(tokenId, positionSize, index)
1401: Math.mulDiv96RoundingUp(amountMoved, c2)
1411: Math.mulDivRoundingUp(
                            amountMoved,
                            scaleFactor - ratio,
                            scaleFactor + Constants.FP96
                        )
1486: Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS)
1496: Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS)
1518: PanopticMath.getAmountsMoved(tokenId, positionSize, index)
1521: PanopticMath.getAmountsMoved(
            tokenId,
            positionSize,
            partnerIndex
        )
1571: Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)
1572: Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP)
```
[292](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L292) | [305](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L305) | [380](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L380) | [387](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L387) | [402](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L402) | [424](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L424) | [462](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L462) | [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L484) | [521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L521) | [556](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L556) | [616](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L616) | [669](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L669) | [687](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L687) | [693](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L693) | [698](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L698) | [956](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L956) | [1012](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1012) | [1069](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1069) | [1109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1109) | [1120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1120) | [1322](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1322) | [1401](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1401) | [1411](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1411) | [1486](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1486) | [1496](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1496) | [1518](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1518) | [1521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1521) | [1571](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1571) | [1572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1572)

```solidity
File: contracts/PanopticFactory.sol

179: CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures)
182: SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token0,
                decoded.payer,
                msg.sender,
                amount0Owed
            )
189: SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token1,
                decoded.payer,
                msg.sender,
                amount1Owed
            )
226: UNIV3_FACTORY.getPool(token0, token1, fee)
233: SFPM.initializeAMMPool(token0, token1, fee)
248: collateralTracker0.startToken(true, token0, token1, fee, newPoolContract)
249: collateralTracker1.startToken(false, token0, token1, fee, newPoolContract)
251: newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1)
266: DONOR_NFT.issueNFT(msg.sender, newPoolContract, token0, token1, fee)
353: Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)
357: Math.mulDivRoundingUp(
                        FULL_RANGE_LIQUIDITY_AMOUNT_WETH,
                        Constants.FP96,
                        currentSqrtPriceX96
                    )
366: Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)
369: Math.mulDivRoundingUp(
                        FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,
                        Constants.FP96,
                        currentSqrtPriceX96
                    )
```
[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L179) | [182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L182) | [189](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L189) | [226](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L226) | [233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L233) | [248](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L248) | [249](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L249) | [251](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L251) | [266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L266) | [353](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L353) | [357](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L357) | [366](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L366) | [369](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L369)

```solidity
File: contracts/PanopticPool.sol

326: InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1)
415: FeesCalc.getPortfolioValue(
            atTick,
            s_positionBalance[user],
            positionIdList
        )
525: PanopticMath.computeInternalMedian(
            observationIndex,
            observationCardinality,
            MEDIAN_PERIOD,
            s_miniMedian,
            s_univ3pool
        )
712: PanopticMath
            .computeExercisedAmounts(tokenId, positionSize)
715: s_collateralToken0.takeCommissionAddData(
            msg.sender,
            longAmounts.rightSlot(),
            shortAmounts.rightSlot(),
            totalSwapped.rightSlot()
        )
721: s_collateralToken1.takeCommissionAddData(
            msg.sender,
            longAmounts.leftSlot(),
            shortAmounts.leftSlot(),
            totalSwapped.leftSlot()
        )
751: SFPM.getAccountPremium(
                    address(s_univ3pool),
                    address(this),
                    tokenId.tokenType(leg),
                    tickLower,
                    tickUpper,
                    type(int24).max,
                    isLong
                )
905: PanopticMath.computeMedianObservedPrice(
            _univ3pool,
            observationIndex,
            observationCardinality,
            FAST_ORACLE_CARDINALITY,
            FAST_ORACLE_PERIOD
        )
915: PanopticMath.computeMedianObservedPrice(
                _univ3pool,
                observationIndex,
                observationCardinality,
                SLOW_ORACLE_CARDINALITY,
                SLOW_ORACLE_PERIOD
            )
923: PanopticMath.computeInternalMedian(
                observationIndex,
                observationCardinality,
                MEDIAN_PERIOD,
                s_miniMedian,
                _univ3pool
            )
981: PanopticMath
            .computeExercisedAmounts(tokenId, positionSize)
985: s_collateralToken0.exercise(
                owner,
                longAmounts.rightSlot(),
                shortAmounts.rightSlot(),
                totalSwapped.rightSlot(),
                realizedPremia.rightSlot()
            )
996: s_collateralToken1.exercise(
                owner,
                longAmounts.leftSlot(),
                shortAmounts.leftSlot(),
                totalSwapped.leftSlot(),
                realizedPremia.leftSlot()
            )
1046: s_collateralToken0.getAccountMarginDetails(
                liquidatee,
                twapTick,
                positionBalanceArray,
                premia.rightSlot()
            )
1053: s_collateralToken1.getAccountMarginDetails(
                liquidatee,
                twapTick,
                positionBalanceArray,
                premia.leftSlot()
            )
1072: s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot())
1073: s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot())
1098: PanopticMath
                .getLiquidationBonus(
                    tokenData0,
                    tokenData1,
                    Math.getSqrtRatioAtTick(twapTick),
                    Math.getSqrtRatioAtTick(finalTick),
                    netExchanged,
                    premia
                )
1122: PanopticMath.haircutPremia(
                _liquidatee,
                _positionIdList,
                premiasByLeg,
                collateralRemaining,
                s_collateralToken0,
                s_collateralToken1,
                Math.getSqrtRatioAtTick(_finalTick),
                s_settledTokens
            )
1141: s_collateralToken0.revoke(
            msg.sender,
            liquidatee,
            uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)
        )
1146: s_collateralToken1.revoke(
            msg.sender,
            liquidatee,
            uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)
        )
1197: PanopticMath
            .computeExercisedAmounts(touchedId[0], positionBalance)
1222: s_collateralToken0.delegate(account, uint128(delegatedAmounts.rightSlot()))
1223: s_collateralToken1.delegate(account, uint128(delegatedAmounts.leftSlot()))
1231: s_collateralToken0.exerciseCost(
            currentTick,
            twapTick,
            touchedId[0],
            positionBalance,
            longAmounts
        )
1242: PanopticMath.getRefundAmounts(
            account,
            refundAmounts,
            twapTick,
            s_collateralToken0,
            s_collateralToken1
        )
1252: s_collateralToken0.refund(
                account,
                msg.sender,
                refundAmounts.rightSlot() - delegatedAmounts.rightSlot()
            )
1257: s_collateralToken1.refund(
                account,
                msg.sender,
                refundAmounts.leftSlot() - delegatedAmounts.leftSlot()
            )
1265: s_collateralToken0.refund(account, uint128(delegatedAmounts.rightSlot()))
1266: s_collateralToken1.refund(account, uint128(delegatedAmounts.leftSlot()))
1308: s_collateralToken0.getAccountMarginDetails(
            account,
            atTick,
            positionBalanceArray,
            portfolioPremium.rightSlot()
        )
1314: s_collateralToken1.getAccountMarginDetails(
            account,
            atTick,
            positionBalanceArray,
            portfolioPremium.leftSlot()
        )
1329: Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000)
1348: Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96)
1349: Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96)
1353: Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96)
1354: Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96)
1383: PanopticMath.updatePositionsHash(
                fingerprintIncomingList,
                positionIdList[i],
                ADD
            )
1410: PanopticMath.updatePositionsHash(
            s_positionsHash[account],
            tokenId,
            addFlag
        )
1451: PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW)
1472: SFPM.getAccountLiquidity(
            address(s_univ3pool),
            address(this),
            tokenId.tokenType(leg),
            tickLower,
            tickUpper
        )
1521: PanopticMath.getLiquidityChunk(
                    tokenId,
                    leg,
                    positionSize
                )
1528: SFPM
                    .getAccountPremium(
                        address(s_univ3pool),
                        address(this),
                        tokenType,
                        liquidityChunk.tickLower(),
                        liquidityChunk.tickUpper(),
                        atTick,
                        isLong
                    )
1605: SFPM.getAccountPremium(
                address(s_univ3pool),
                address(this),
                tokenType,
                tickLower,
                tickUpper,
                currentTick,
                1
            )
1627: PanopticMath
            .getLiquidityChunk(tokenId, legIndex, s_positionBalance[owner][tokenId].rightSlot())
1639: s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot())
1640: s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot())
1680: PanopticMath.getLiquidityChunk(
                    tokenId,
                    leg,
                    positionSize
                )
1707: SFPM.getAccountPremium(
                    address(s_univ3pool),
                    address(this),
                    tokenId.tokenType(leg),
                    liquidityChunk.tickLower(),
                    liquidityChunk.tickUpper(),
                    type(int24).max,
                    0
                )
1811: SFPM.getAccountLiquidity(
                address(s_univ3pool),
                address(this),
                tokenType,
                tickLower,
                tickUpper
            )
1877: PanopticMath
                        .getLiquidityChunk(tokenId, leg, positionSize)
```
[326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L326) | [415](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L415) | [525](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L525) | [712](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L712) | [715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L715) | [721](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L721) | [751](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L751) | [905](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L905) | [915](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L915) | [923](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L923) | [981](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L981) | [985](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L985) | [996](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L996) | [1046](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1046) | [1053](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1053) | [1072](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1072) | [1073](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1073) | [1098](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1098) | [1122](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1122) | [1141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1141) | [1146](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1146) | [1197](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1197) | [1222](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1222) | [1223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1223) | [1231](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1231) | [1242](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1242) | [1252](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1252) | [1257](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1257) | [1265](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1265) | [1266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1266) | [1308](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1308) | [1314](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1314) | [1329](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1329) | [1348](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1348) | [1349](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1349) | [1353](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1353) | [1354](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1354) | [1383](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1383) | [1410](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1410) | [1451](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1451) | [1472](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1472) | [1521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1521) | [1528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1528) | [1605](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1605) | [1627](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1627) | [1639](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1639) | [1640](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1640) | [1680](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1680) | [1707](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1707) | [1811](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1811) | [1877](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1877)

```solidity
File: contracts/SemiFungiblePositionManager.sol

352: FACTORY.getPool(token0, token1, fee)
410: CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures)
413: SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token0,
                decoded.payer,
                msg.sender,
                amount0Owed
            )
420: SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token1,
                decoded.payer,
                msg.sender,
                amount1Owed
            )
443: CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures)
456: SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay)
604: PanopticMath.getLiquidityChunk(
                id,
                leg,
                uint128(amount)
            )
817: PanopticMath.convert1to0(itm1, sqrtPriceX96)
837: _univ3pool.swap(
                msg.sender,
                zeroForOne,
                swapAmount,
                zeroForOne
                    ? Constants.MIN_V3POOL_SQRT_RATIO + 1
                    : Constants.MAX_V3POOL_SQRT_RATIO - 1,
                data
            )
904: PanopticMath.getLiquidityChunk(
                    _tokenId,
                    _leg,
                    _positionSize
                )
1123: LeftRightLibrary
            .addCapped(
                s_accountPremiumOwed[positionKey],
                deltaPremiumOwed,
                s_accountPremiumGross[positionKey],
                deltaPremiumGross
            )
1169: Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)
1172: Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)
1176: Math.mulDiv128(feeGrowthInside0LastX128, liquidity)
1177: Math.mulDiv128(feeGrowthInside1LastX128, liquidity)
1284: univ3pool.collect(
                msg.sender,
                liquidityChunk.tickLower(),
                liquidityChunk.tickUpper(),
                uint128(amountToCollect.rightSlot()),
                uint128(amountToCollect.leftSlot())
            )
1350: Math.mulDiv(
                    collected0,
                    totalLiquidity * 2 ** 64,
                    netLiquidity ** 2
                )
1355: Math.mulDiv(
                    collected1,
                    totalLiquidity * 2 ** 64,
                    netLiquidity ** 2
                )
1369: Math
                        .mulDiv(premium0X64_base, numerator, totalLiquidity)
1372: Math
                        .mulDiv(premium1X64_base, numerator, totalLiquidity)
1393: Math
                        .mulDiv(premium0X64_base, numerator, totalLiquidity ** 2)
1396: Math
                        .mulDiv(premium1X64_base, numerator, totalLiquidity ** 2)
1480: FeesCalc.calculateAMMSwapFees(
                        _univ3pool,
                        atTick,
                        _tickLower,
                        _tickUpper,
                        netLiquidity
                    )
1507: LeftRightLibrary.addCapped(
                    s_accountPremiumOwed[positionKey],
                    premiumOwed,
                    s_accountPremiumGross[positionKey],
                    premiumGross
                )
```
[352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L352) | [410](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L410) | [413](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L413) | [420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L420) | [443](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L443) | [456](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L456) | [604](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L604) | [817](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L817) | [837](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L837) | [904](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L904) | [1123](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1123) | [1169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1169) | [1172](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1172) | [1176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1176) | [1177](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1177) | [1284](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1284) | [1350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1350) | [1355](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1355) | [1369](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1369) | [1372](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1372) | [1393](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1393) | [1396](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1396) | [1480](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1480) | [1507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1507)

```solidity
File: contracts/libraries/CallbackLib.sol

36: factory.getPool(features.token0, features.token1, features.fee)
```
[36](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L36)

```solidity
File: contracts/libraries/FeesCalc.sol

56: PanopticMath.getLiquidityChunk(
                    tokenId,
                    leg,
                    positionSize
                )
62: Math.getAmountsForLiquidity(
                    atTick,
                    liquidityChunk
                )
117: Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity)
118: Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity)
```
[56](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L56) | [62](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L62) | [117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L117) | [118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L118)

```solidity
File: contracts/libraries/InteractionHelper.sol

72: string.concat(
                    prefix,
                    " ",
                    isToken0 ? symbol0 : symbol1,
                    " LP on ",
                    symbol0,
                    "/",
                    symbol1,
                    " ",
                    Strings.toString(fee),
                    "bps"
                )
98: string.concat(prefix, tokenSymbol)
100: string.concat(prefix, "???")
```
[72](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L72) | [98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L98) | [100](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L100)

```solidity
File: contracts/libraries/Math.sol

251: LiquidityChunkLibrary.createChunk(
                    tickLower,
                    tickUpper,
                    toUint128(
                        mulDiv(
                            amount0,
                            mulDiv96(highPriceX96, lowPriceX96),
                            highPriceX96 - lowPriceX96
                        )
                    )
                )
281: LiquidityChunkLibrary.createChunk(
                    tickLower,
                    tickUpper,
                    toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))
                )
```
[251](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L251) | [281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L281)

```solidity
File: contracts/libraries/PanopticMath.sol

326: Math.getLiquidityForAmount0(tickLower, tickUpper, amount)
328: Math.getLiquidityForAmount1(tickLower, tickUpper, amount)
349: PanopticMath.getRangesFromStrike(width, tickSpacing)
377: Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)
495: Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2)
497: Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
497: Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
512: Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2)
514: Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
514: Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
529: Math
                    .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
534: Math
                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
535: Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
552: Math
                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
557: Math
                    .mulDiv(
                        Math.absUint(amount),
                        2 ** 128,
                        Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
                    )
561: Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
588: Math.getLiquidityForAmount0(tickLower, tickUpper, amount0)
594: Math.getLiquidityForAmount1(tickLower, tickUpper, amount1)
664: PanopticMath.convert0to1(
                    tokenData0.leftSlot(),
                    sqrtPriceX96Twap
                )
671: PanopticMath.convertCollateralData(
                    tokenData0,
                    tokenData1,
                    0,
                    sqrtPriceX96Twap
                )
681: Math.mulDiv128(bonusCross, requiredRatioX128)
684: PanopticMath.convert0to1(
                        Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
                        sqrtPriceX96Final
                    )
685: Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128)
717: PanopticMath.convert0to1(paid0 - balance0, sqrtPriceX96Final)
720: PanopticMath.convert1to0(balance1 - paid1, sqrtPriceX96Final)
735: PanopticMath.convert1to0(paid1 - balance1, sqrtPriceX96Final)
738: PanopticMath.convert0to1(balance0 - paid0, sqrtPriceX96Final)
805: PanopticMath.convert1to0(
                            longPremium.leftSlot() - collateralDelta1,
                            sqrtPriceX96Final
                        )
812: PanopticMath.convert0to1(
                            collateralDelta0 - longPremium.rightSlot(),
                            sqrtPriceX96Final
                        )
829: PanopticMath.convert1to0(
                            collateralDelta1 - longPremium.leftSlot(),
                            sqrtPriceX96Final
                        )
836: PanopticMath.convert0to1(
                            longPremium.rightSlot() - collateralDelta0,
                            sqrtPriceX96Final
                        )
856: collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0))
857: collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1))
869: Math.unsafeDivRoundingUp(
                            uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
                            uint128(longPremium.rightSlot())
                        )
873: Math.unsafeDivRoundingUp(
                            uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
                            uint128(longPremium.leftSlot())
                        )
939: PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
957: PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
```
[326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L326) | [328](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L328) | [349](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L349) | [377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L377) | [495](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L495) | [497](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L497) | [497](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L497) | [512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L512) | [514](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L514) | [514](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L514) | [529](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L529) | [534](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L534) | [535](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L535) | [552](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L552) | [557](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L557) | [561](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L561) | [588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L588) | [594](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L594) | [664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L664) | [671](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L671) | [681](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L681) | [684](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L684) | [685](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L685) | [717](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L717) | [720](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L720) | [735](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L735) | [738](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L738) | [805](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L805) | [812](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L812) | [829](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L829) | [836](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L836) | [856](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L856) | [857](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L857) | [869](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L869) | [873](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L873) | [939](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L939) | [957](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L957)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

114: ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data)
165: ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data)
224: ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "")
```
[114](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L114) | [165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L165) | [224](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L224)

```solidity
File: contracts/types/TokenId.sol

420: PanopticMath.getTicks(
            self.strike(legIndex),
            self.width(legIndex),
            self.tickSpacing()
        )
582: PanopticMath.getRangesFromStrike(
                    self.width(i),
                    self.tickSpacing()
                )
```
[420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L420) | [582](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L582)
</details>

### [N-23] Assembly block creates dirty bits

Writing data to the free memory pointer without later updating the free memory pointer will cause dirty bits at that memory location.
This makes it harder for the optimizer to determine whether the memory needs to be cleaned before use, leading to suboptimal optimizations.
It is recommended to update the free memory pointer and annotate the assembly block with `memory-safe` to avoid this issue.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit - Assembly block has `mstore` without `memory-safe` annotation
393: assembly {
```
[393](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L393)
</details>

### [N-24] Events in public function missing sender information

Events should include the sender information when emitted in `public` or `external` functions for better traceability.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit external function `initializeAMMPool()` emits an event without sender information
386: emit PoolInitialized(univ3pool);
```
[386](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L386)
</details>

### [N-25] Leverage Recent Solidity Features with `0.8.21`

The recent updates in Solidity provide several features and optimizations that, when leveraged appropriately, can significantly improve your contract's code clarity and maintainability.
Key enhancements include the use of push0 for placing 0 on the stack for EVM versions starting from "Shanghai", making your code simpler and more straightforward.
Moreover, Solidity has extended NatSpec documentation support to enum and struct definitions, facilitating more comprehensive and insightful code documentation.

Additionally, the re-implementation of the UnusedAssignEliminator and UnusedStoreEliminator in the Solidity optimizer provides the ability to remove unused assignments in deeply nested loops.
This results in a cleaner, more efficient contract code, reducing clutter and potential points of confusion during code review or debugging.
It's recommended to make full use of these features and optimizations to enhance the robustness and readability of your smart contracts.

<details>
<summary><i>13 issue instances in 13 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

2: pragma solidity =0.8.18;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L2)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2)

```solidity
File: contracts/types/LeftRight.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L2)

```solidity
File: contracts/types/LiquidityChunk.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L2)

```solidity
File: contracts/types/TokenId.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L2)

```solidity
File: contracts/libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L2)

```solidity
File: contracts/libraries/Constants.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L2)

```solidity
File: contracts/libraries/Errors.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L2)

```solidity
File: contracts/libraries/FeesCalc.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L2)

```solidity
File: contracts/libraries/Math.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L2)

```solidity
File: contracts/libraries/PanopticMath.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L2)

```solidity
File: contracts/libraries/SafeTransferLib.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L2)

```solidity
File: contracts/multicall/Multicall.sol

2: pragma solidity =0.8.18;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L2)
</details>

### [N-26] Custom error has no error details

Take advantage of custom error's return value property. 

An important feature of Custom Error is that values such as address, tokenID, msg.value can be written inside the () sign, providing a serious advantage in debugging and examining the revert details of dapps such as Tenderly.

<details>
<summary><i>16 issue instances in 2 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

51: error NotAuthorized();
54: error UnsafeRecipient();
```
[51](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L51) | [54](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L54)

```solidity
File: contracts/libraries/Errors.sol

11: error CastingError();
14: error InvalidTick();
17: error InvalidUniswapCallback();
24: error LeftRightInputError();
27: error NoLegsExercisable();
30: error PositionTooLarge();
33: error NotEnoughLiquidity();
36: error OptionsBalanceZero();
39: error PriceBoundFail();
42: error ReentrantCall();
45: error TransferFailed();
49: error TicksNotInitializable();
52: error UnderOverFlow();
55: error UniswapPoolNotInitialized();
```
[11](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L11) | [14](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L14) | [17](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L17) | [24](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L24) | [27](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L27) | [30](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L30) | [33](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L33) | [36](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L36) | [39](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L39) | [42](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L42) | [45](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L45) | [49](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L49) | [52](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L52) | [55](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L55)
</details>

### [N-27] High Cyclomatic Complexity in Functions

Functions with high cyclomatic complexity are harder to understand, test, and maintain.
Consider breaking down these blocks into more manageable units, by splitting things into utility functions,
by reducing nesting, and by using early returns.

[Learn More About Cyclomatic Complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity)

<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit function `_validateAndForwardToAMM` has a cyclomatic complexity of 6
663: function _validateAndForwardToAMM(
        uint256 tokenId,
        uint128 positionSize,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        bool isBurn
    ) internal returns (int256 totalCollectedFromAMM, int256 totalMoved, int24 newTick) {
/// @audit function `_createLegInAMM` has a cyclomatic complexity of 9
936: function _createLegInAMM(
        IUniswapV3Pool _univ3pool,
        uint256 _tokenId,
        uint256 _leg,
        uint256 _liquidityChunk,
        bool _isBurn
    ) internal returns (int256 _moved, int256 _itmAmounts, int256 _totalCollected) {
```
[663](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L663) | [936](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L936)

```solidity
File: contracts/types/TokenId.sol

/// @audit function `validate` has a cyclomatic complexity of 11
463: function validate(uint256 self) internal pure returns (uint64) {
```
[463](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L463)

```solidity
File: contracts/libraries/Math.sol

/// @audit function `getSqrtRatioAtTick` has a cyclomatic complexity of 21
38: function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160 sqrtPriceX96) {
```
[38](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L38)
</details>

### [N-28] Contract should expose an `interface`

Exposing an interface in a smart contract allows for easier integration by other projects and developers.
Without an interface, there's a risk that other projects will have to develop non-standard variants to interact with your contract.
It's highly recommended to define an interface for clearer and more robust collaboration.

<details>
<summary><i>23 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

321: function beginReentrancyLock(uint64 poolId) internal {
331: function endReentrancyLock(uint64 poolId) internal {
351: function initializeAMMPool(address token0, address token1, uint24 fee) external {
407: function uniswapV3MintCallback(
        uint256 amount0Owed,
        uint256 amount1Owed,
        bytes calldata data
    ) external {
441: function uniswapV3SwapCallback(
        int256 amount0Delta,
        int256 amount1Delta,
        bytes calldata data
    ) external {
476: function burnTokenizedPosition(
        uint256 tokenId,
        uint128 positionSize,
        int24 slippageTickLimitLow,
        int24 slippageTickLimitHigh
    )
        external
        ReentrancyLock(tokenId.univ3pool())
        returns (int256 totalCollected, int256 totalSwapped, int24 newTick)
    {
510: function mintTokenizedPosition(
        uint256 tokenId,
        uint128 positionSize,
        int24 slippageTickLimitLow,
        int24 slippageTickLimitHigh
    )
        external
        ReentrancyLock(tokenId.univ3pool())
        returns (int256 totalCollected, int256 totalSwapped, int24 newTick)
    {
578: function registerTokenTransfer(address from, address to, uint256 id, uint256 amount) internal {
663: function _validateAndForwardToAMM(
        uint256 tokenId,
        uint128 positionSize,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        bool isBurn
    ) internal returns (int256 totalCollectedFromAMM, int256 totalMoved, int24 newTick) {
743: function swapInAMM(
        IUniswapV3Pool univ3pool,
        int256 itmAmounts
    ) internal returns (int256 totalSwapped) {
848: function _createPositionInAMM(
        IUniswapV3Pool univ3pool,
        uint256 tokenId,
        uint128 positionSize,
        bool isBurn
    ) internal returns (int256 totalMoved, int256 totalCollected, int256 itmAmounts) {
936: function _createLegInAMM(
        IUniswapV3Pool _univ3pool,
        uint256 _tokenId,
        uint256 _leg,
        uint256 _liquidityChunk,
        bool _isBurn
    ) internal returns (int256 _moved, int256 _itmAmounts, int256 _totalCollected) {
1073: function _updateStoredPremia(
        bytes32 positionKey,
        uint256 currentLiquidity,
        int256 collectedAmounts
    ) private {
1093: function _getFeesBase(
        IUniswapV3Pool univ3pool,
        uint128 liquidity,
        uint256 liquidityChunk
    ) private view returns (int256 feesBase) {
1129: function _mintLiquidity(
        uint256 liquidityChunk,
        IUniswapV3Pool univ3pool
    ) internal returns (int256 movedAmounts) {
1169: function _burnLiquidity(
        uint256 liquidityChunk,
        IUniswapV3Pool univ3pool
    ) internal returns (int256 movedAmounts) {
1200: function _collectAndWritePositionData(
        uint256 liquidityChunk,
        IUniswapV3Pool univ3pool,
        uint256 currentLiquidity,
        bytes32 positionKey,
        int256 movedInLeg,
        uint256 isLong
    ) internal returns (int256 collectedOut) {
1255: function _getPremiaDeltas(
        uint256 currentLiquidity,
        int256 collectedAmounts
    ) private pure returns (uint256 deltaPremiumOwed, uint256 deltaPremiumGross) {
1343: function getAccountLiquidity(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper
    ) external view returns (uint256 accountLiquidities) {
1371: function getAccountPremium(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper,
        int24 atTick,
        uint256 isLong
    ) external view returns (uint128 premiumToken0, uint128 premiumToken1) {
1437: function getAccountFeesBase(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper
    ) external view returns (int128 feesBase0, int128 feesBase1) {
1457: function getUniswapV3PoolFromId(
        uint64 poolId
    ) external view returns (IUniswapV3Pool UniswapV3Pool) {
1468: function getPoolId(address univ3pool) external view returns (uint64 poolId) {
```
[321](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L321) | [331](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L331) | [351](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L351) | [407](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L407) | [441](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L441) | [476](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L476) | [510](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L510) | [578](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L578) | [663](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L663) | [743](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L743) | [848](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L848) | [936](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L936) | [1073](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1073) | [1093](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1093) | [1129](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1129) | [1169](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1169) | [1200](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1200) | [1255](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255) | [1343](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1343) | [1371](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1371) | [1437](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1437) | [1457](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1457) | [1468](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1468)
</details>

### [N-29] Inconsistent spacing in comments

Some lines use // x and some use //x. The instances below point out the usages that don't follow the majority, within each file:

<details>
<summary><i>19 issue instances in 1 files:</i></summary>

```solidity
File: contracts/types/LiquidityChunk.sol

11: ///   A liquidity chunk is an amount of `liquidity` (an amount of WETH, e.g.) deployed between two ticks: `tickLower` and `tickUpper`
12: ///   into a concentrated liquidity AMM (Shown as "Other AMM liquidity" in the diagram below):
14: ///                liquidity
15: ///                    ▲      liquidity chunk
16: ///                    │        │
17: ///                    │    ┌───▼────┐   ▲
18: ///                    │    │        │   │ liquidity/size
19: ///      Other AMM     │  ┌─┴────────┴─┐ ▼ of chunk
20: ///      liquidity  ───┼──┼─►          │
21: ///                    │  │            │
22: ///                    └──┴─▲────────▲─┴──► price ticks
23: ///                         │        │
24: ///                         │        │
25: ///                    tickLower     │
26: ///                              tickUpper
44: ///           (3)             (2)             ( )                (1)
45: ///    <-- 24 bits -->  <-- 24 bits -->  <-- 80 bits -->   <-- 128 bits -->
46: ///        tickLower       tickUpper         Zeros             Liquidity
48: ///        <--- most significant bit        least significant bit --->
```
[11](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L11) | [12](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L12) | [14](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L14) | [15](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L15) | [16](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L16) | [17](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L17) | [18](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L18) | [19](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L19) | [20](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L20) | [21](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L21) | [22](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L22) | [23](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L23) | [24](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L24) | [25](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L25) | [26](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L26) | [44](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L44) | [45](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L45) | [46](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L46) | [48](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L48)
</details>

### [N-30] Unused Custom Errors

Custom errors that aren't utilized within the contract add unnecessary complexity to the codebase. 
Cleaning up and removing these unused custom errors can enhance the readability and maintainability of the contract.

<details>
<summary><i>15 issue instances in 1 files:</i></summary>

```solidity
File: contracts/libraries/Errors.sol

/// @audit Custom Error `CastingError` declared but never used
11: error CastingError();
/// @audit Custom Error `InvalidTick` declared but never used
14: error InvalidTick();
/// @audit Custom Error `InvalidUniswapCallback` declared but never used
17: error InvalidUniswapCallback();
/// @audit Custom Error `InvalidTokenIdParameter` declared but never used
21: error InvalidTokenIdParameter(uint256 parameterType);
/// @audit Custom Error `LeftRightInputError` declared but never used
24: error LeftRightInputError();
/// @audit Custom Error `NoLegsExercisable` declared but never used
27: error NoLegsExercisable();
/// @audit Custom Error `PositionTooLarge` declared but never used
30: error PositionTooLarge();
/// @audit Custom Error `NotEnoughLiquidity` declared but never used
33: error NotEnoughLiquidity();
/// @audit Custom Error `OptionsBalanceZero` declared but never used
36: error OptionsBalanceZero();
/// @audit Custom Error `PriceBoundFail` declared but never used
39: error PriceBoundFail();
/// @audit Custom Error `ReentrantCall` declared but never used
42: error ReentrantCall();
/// @audit Custom Error `TransferFailed` declared but never used
45: error TransferFailed();
/// @audit Custom Error `TicksNotInitializable` declared but never used
49: error TicksNotInitializable();
/// @audit Custom Error `UnderOverFlow` declared but never used
52: error UnderOverFlow();
/// @audit Custom Error `UniswapPoolNotInitialized` declared but never used
55: error UniswapPoolNotInitialized();
```
[11](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L11) | [14](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L14) | [17](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L17) | [21](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L21) | [24](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L24) | [27](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L27) | [30](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L30) | [33](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L33) | [36](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L36) | [39](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L39) | [42](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L42) | [45](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L45) | [49](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L49) | [52](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L52) | [55](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L55)
</details>

### [N-31] Outdated Solidity Version

The current Solidity version used in the contract is outdated.
Consider using a more recent version for improved features and security.

0.8.4: bytes.concat() instead of abi.encodePacked(,)

0.8.12: string.concat() instead of abi.encodePacked(,)

0.8.13: Ability to use using for with a list of free functions

0.8.14:
    ABI Encoder: When ABI-encoding values from calldata that contain nested arrays, correctly validate the nested array length against calldatasize() in all cases. Override Checker: Allow changing data location for parameters only when overriding external functions.

0.8.15:
    Code Generation: Avoid writing dirty bytes to storage when copying bytes arrays. Yul Optimizer: Keep all memory side-effects of inline assembly blocks.

0.8.16:
    Code Generation: Fix data corruption that affected ABI-encoding of calldata values represented by tuples: structs at any nesting level; argument lists of external functions, events and errors; return value lists of external functions. The 32 leading bytes of the first dynamically-encoded value in the tuple would get zeroed when the last component contained a statically-encoded array.

0.8.17:
    Yul Optimizer: Prevent the incorrect removal of storage writes before calls to Yul functions that conditionally terminate the external EVM call.

<details>
<summary><i>13 issue instances in 13 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

2: pragma solidity =0.8.18;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L2)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2)

```solidity
File: contracts/types/LeftRight.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L2)

```solidity
File: contracts/types/LiquidityChunk.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L2)

```solidity
File: contracts/types/TokenId.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L2)

```solidity
File: contracts/libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L2)

```solidity
File: contracts/libraries/Constants.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L2)

```solidity
File: contracts/libraries/Errors.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L2)

```solidity
File: contracts/libraries/FeesCalc.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L2)

```solidity
File: contracts/libraries/Math.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L2)

```solidity
File: contracts/libraries/PanopticMath.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L2)

```solidity
File: contracts/libraries/SafeTransferLib.sol

2: pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L2)

```solidity
File: contracts/multicall/Multicall.sol

2: pragma solidity =0.8.18;
```
[2](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L2)
</details>

### [N-32] Ensure Non-Empty Check for Bytes in Function Parameters

To avoid mistakenly accepting empty bytes as valid parameters, it is advisable to implement checks for non-empty bytes within functions.
This ensures that empty bytes are not treated as valid inputs, preventing potential issues.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

407: function uniswapV3MintCallback(
        uint256 amount0Owed,
        uint256 amount1Owed,
        bytes calldata data
    ) external {
441: function uniswapV3SwapCallback(
        int256 amount0Delta,
        int256 amount1Delta,
        bytes calldata data
    ) external {
```
[407](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L407) | [441](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L441)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

200: function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
```
[200](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L200)
</details>

### [N-33] Adding a `return` statement when the function defines a named return variable, is redundant

Functions in Solidity can use named return variables which can enhance readability and reduce the complexity of the code. When using named return variables, a return statement without any parameters is implicitly added to the end of the function.
This means that explicitly writing return in a function that uses named return variables is redundant.
This redundancy could lead to confusion and misinterpretation of the function's behavior, particularly for developers who are new to the Solidity language or to the codebase.

Moreover, explicitly stating the return statement with the named variables might give the impression that the function could have different exit points or that it might return different values, which is not the case here.
Therefore, removing these redundant return statements can lead to cleaner, more maintainable code with reduced cognitive load for developers.
This helps in understanding the flow and the logic of the function at a quick glance and aids in faster debugging and fewer mistakes.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit - Redundant `return (totalCollectedFromAMM, totalMoved, newTick);` when function has named return variables
663: function _validateAndForwardToAMM(
        uint256 tokenId,
        uint128 positionSize,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        bool isBurn
    ) internal returns (int256 totalCollectedFromAMM, int256 totalMoved, int24 newTick) {
```
[663](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L663)

```solidity
File: contracts/libraries/Math.sol

/// @audit - Redundant `return result;` when function has named return variables
/// @audit - Redundant `return result;` when function has named return variables
186: function mulDiv(
        uint256 a,
        uint256 b,
        uint256 denominator
    ) internal pure returns (uint256 result) {
/// @audit - Redundant `return result;` when function has named return variables
/// @audit - Redundant `return result;` when function has named return variables
/// @audit - Redundant `return result;` when function has named return variables
/// @audit - Redundant `return result;` when function has named return variables
```
[186](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L186)
</details>

### [N-34] Assembly blocks should have extensive comments

Large assembly blocks require extensive comments to aid understanding and code auditing. Assembly code takes more time to audit than normal Solidity code and often contains intricate details that aren't as apparent as in higher-level languages.

The identified assembly blocks in your contract appear to lack sufficient comments. Consider adding more comments explaining what each step of the assembly code does.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

393: assembly {
            mstore(0, 0xFA20F71C)
        }
```
[393](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L393)
</details>

### [N-35] Use `bytes.concat()` instead of `abi.encodePacked()`

Solidity version 0.8.4 introduces `bytes.concat()` for concatenating byte arrays, which is more efficient than using `abi.encodePacked()`.
It is recommended to use `bytes.concat()` instead of `abi.encodePacked()` and upgrade to at least Solidity version 0.8.4 if required.

<details>
<summary><i>7 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

604: abi.encodePacked(
946: abi.encodePacked(
1105: abi.encodePacked(
1353: keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))
1381: abi.encodePacked(address(univ3pool), owner, tokenType, tickLower, tickUpper)
1446: keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))
```
[604](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L604) | [946](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L946) | [1105](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1105) | [1353](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1353) | [1381](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1381) | [1446](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1446)

```solidity
File: contracts/libraries/CallbackLib.sol

40: abi.encodePacked(
```
[40](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L40)
</details>

### [N-36] Function/Constructor Argument Names Not in mixedCase

Underscore before of after function argument names is a common convention in Solidity NOT a documentation requirement.

Function arguments should use mixedCase for better readability and consistency with Solidity style guidelines. 
Examples of good practice include: initialSupply, account, recipientAddress, senderAddress, newOwner. 
[More information in Documentation](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#function-argument-names)

Rule exceptions
- Allow constant variable name/symbol/decimals to be lowercase (ERC20).
- Allow `_` at the beginning of the mixedCase match for `private variables` and `unused parameters`.

<details>
<summary><i>14 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

936: function _createLegInAMM(
        IUniswapV3Pool _univ3pool,
        uint256 _tokenId,
        uint256 _leg,
        uint256 _liquidityChunk,
        bool _isBurn
    ) internal returns (int256 _moved, int256 _itmAmounts, int256 _totalCollected) {
342: constructor(IUniswapV3Factory _factory) {
```
[936](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L936) | [342](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L342)

```solidity
File: contracts/types/LiquidityChunk.sol

63: function createChunk(
        uint256 self,
        int24 _tickLower,
        int24 _tickUpper,
        uint128 amount
    ) internal pure returns (uint256) {
88: function addTickLower(uint256 self, int24 _tickLower) internal pure returns (uint256) {
98: function addTickUpper(uint256 self, int24 _tickUpper) internal pure returns (uint256) {
```
[63](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L63) | [88](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L88) | [98](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L98)

```solidity
File: contracts/types/TokenId.sol

173: function addUniv3pool(uint256 self, uint64 _poolId) internal pure returns (uint256) {
189: function addAsset(
        uint256 self,
        uint256 _asset,
        uint256 legIndex
    ) internal pure returns (uint256) {
204: function addOptionRatio(
        uint256 self,
        uint256 _optionRatio,
        uint256 legIndex
    ) internal pure returns (uint256) {
220: function addIsLong(
        uint256 self,
        uint256 _isLong,
        uint256 legIndex
    ) internal pure returns (uint256) {
234: function addTokenType(
        uint256 self,
        uint256 _tokenType,
        uint256 legIndex
    ) internal pure returns (uint256) {
248: function addRiskPartner(
        uint256 self,
        uint256 _riskPartner,
        uint256 legIndex
    ) internal pure returns (uint256) {
262: function addStrike(
        uint256 self,
        int24 _strike,
        uint256 legIndex
    ) internal pure returns (uint256) {
276: function addWidth(
        uint256 self,
        int24 _width,
        uint256 legIndex
    ) internal pure returns (uint256) {
298: function addLeg(
        uint256 self,
        uint256 legIndex,
        uint256 _optionRatio,
        uint256 _asset,
        uint256 _isLong,
        uint256 _tokenType,
        uint256 _riskPartner,
        int24 _strike,
        int24 _width
    ) internal pure returns (uint256 tokenId) {
```
[173](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L173) | [189](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L189) | [204](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L204) | [220](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L220) | [234](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L234) | [248](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L248) | [262](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L262) | [276](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L276) | [298](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L298)
</details>

### [N-37] Upgrade `openzeppelin` to the Latest Version - 5.0.0

These contracts import contracts from @openzeppelin/contracts but they are not using the latest version.
For more information, please visit: [OpenZeppelin GitHub Releases](https://github.com/OpenZeppelin/openzeppelin-contracts/releases)
It is recommended to always use the latest version to take advantage of updates and security fixes.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

5: import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```
[5](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L5)
</details>

### [N-38] Duplicated require()/revert() Checks

Duplicated require() or revert() checks should be refactored to a modifier or function.
This helps in maintaining a clean and organized codebase and saves deployment costs.

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

97: if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
135: if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
```
[97](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L97) | [135](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L135)

```solidity
File: contracts/types/LeftRight.sol

167: if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
185: if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
```
[167](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L167) | [185](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L185)
</details>

### [N-39] Event is not properly `indexed`

Index event fields make the field more quickly accessible to off-chain tools that parse events.
This is especially useful when it comes to filtering based on an address. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields).
Where applicable, each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question.
If there are fewer than three applicable fields, all of the applicable fields should be indexed.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

86: event TokenizedPositionBurnt(
        address indexed recipient,
        uint256 indexed tokenId,
        uint128 positionSize
    );
97: event TokenizedPositionMinted(
        address indexed caller,
        uint256 indexed tokenId,
        uint128 positionSize
    );
```
[86](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L86) | [97](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L97)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

44: event ApprovalForAll(address indexed owner, address indexed operator, bool approved);
```
[44](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L44)
</details>

### [N-40] Consider Adding Emergency-Stop Functionality

Smart contracts that hold significant value, interact with external contracts, or have complex logic should include an emergency-stop mechanism for added security. This allows pausing certain contract functionalities in case of emergencies, mitigating potential damages.

This contract seems to lack such a mechanism. Implementing an emergency stop can enhance contract security and reliability.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

1: No emergency stop pattern found
```
[1](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1)
</details>

### [N-41] Consider adding a block/deny-list

While adding a block or deny-list may increase the level of centralization in the contract, it provides an additional layer of security by preventing hackers from using stolen tokens or carrying out other malicious activities.

Although it's a trade-off, a block or deny-list can help improve the overall security posture of the contract.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

72: contract SemiFungiblePositionManager is ERC1155, Multicall {
```
[72](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L72)
</details>

### [N-42] Inconsistent Use of Named Return Variables

Declaring a named return variable but returning a different value within the function is an inconsistent use of named return variables.
This practice can lead to confusion and misinterpretation of the function's intended behavior, as it contradicts the purpose of declaring named return variables, which is to enhance readability and reduce complexity in the code.

This inconsistency might signal an error in the function logic where the declared return variable is not being used as intended.
It is recommended to revisit the function's logic to ensure that the named return variables are being utilized correctly, or to adjust the return statements to reflect the actual values being returned, fostering better clarity and coherence in the code.

<details>
<summary><i>12 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit - `if (swapAmount == 0) return int256(0);` statement in functions but `totalSwapped` are declared
743: function swapInAMM(
        IUniswapV3Pool univ3pool,
        int256 itmAmounts
    ) internal returns (int256 totalSwapped) {
/// @audit - `return s_poolContext[poolId].pool;` statement in functions but `UniswapV3Pool` are declared
1457: function getUniswapV3PoolFromId(
        uint64 poolId
    ) external view returns (IUniswapV3Pool UniswapV3Pool) {
```
[743](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L743) | [1457](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1457)

```solidity
File: contracts/types/LeftRight.sol

/// @audit - `return z.toRightSlot(right128).toLeftSlot(left128);` statement in functions but `z` are declared
159: function add(int256 x, int256 y) internal pure returns (int256 z) {
/// @audit - `return z.toRightSlot(right128).toLeftSlot(left128);` statement in functions but `z` are declared
177: function sub(int256 x, int256 y) internal pure returns (int256 z) {
```
[159](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L159) | [177](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L177)

```solidity
File: contracts/libraries/Math.sol

/// @audit - `return
                mulDiv(
                    uint256(liquidityChunk.liquidity()) << 96,
                    highPriceX96 - lowPriceX96,
                    highPriceX96
                ) / lowPriceX96;` statement in functions but `amount0` are declared
101: function getAmount0ForLiquidity(
        uint256 liquidityChunk
    ) internal pure returns (uint256 amount0) {
/// @audit - `return mulDiv96(liquidityChunk.liquidity(), highPriceX96 - lowPriceX96);` statement in functions but `amount1` are declared
119: function getAmount1ForLiquidity(
        uint256 liquidityChunk
    ) internal pure returns (uint256 amount1) {
/// @audit - `return
                toUint128(
                    mulDiv(amount0, mulDiv96(highPriceX96, lowPriceX96), highPriceX96 - lowPriceX96)
                );` statement in functions but `liquidity` are declared
135: function getLiquidityForAmount0(
        uint256 liquidityChunk,
        uint256 amount0
    ) internal pure returns (uint128 liquidity) {
/// @audit - `return toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96));` statement in functions but `liquidity` are declared
154: function getLiquidityForAmount1(
        uint256 liquidityChunk,
        uint256 amount1
    ) internal pure returns (uint128 liquidity) {
/// @audit - `return prod0;` statement in functions but `result` are declared
286: function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256 result) {
/// @audit - `return prod0;` statement in functions but `result` are declared
348: function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256 result) {
/// @audit - `return prod0;` statement in functions but `result` are declared
410: function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256 result) {
/// @audit - `return prod0;` statement in functions but `result` are declared
472: function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256 result) {
```
[101](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L101) | [119](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L119) | [135](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L135) | [154](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L154) | [286](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L286) | [348](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L348) | [410](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L410) | [472](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L472)
</details>

### [N-43] Function Names Not in mixedCase

Function names should use mixedCase for better readability and consistency with Solidity style guidelines. 
Examples of good practice include: getBalance, transfer, verifyOwner, addMember, changeOwner. 
[More information in Documentation](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#function-names)

<details>
<summary><i>7 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

351: function initializeAMMPool(address token0, address token1, uint24 fee) external {
663: function _validateAndForwardToAMM(
743: function swapInAMM(
848: function _createPositionInAMM(
936: function _createLegInAMM(
```
[351](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L351) | [663](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L663) | [743](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L743) | [848](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L848) | [936](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L936)

```solidity
File: contracts/libraries/FeesCalc.sol

54: function calculateAMMSwapFeesLiquidityChunk(
89: function _getAMMSwapFeesPerLiquidityCollected(
```
[54](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L54) | [89](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L89)
</details>

### [N-44] Insufficient Comments in Complex Functions

Complex functions spanning multiple lines should have more comments to better explain the purpose of each logic step.
Proper commenting can greatly improve the readability and maintainability of the codebase. Consider adding explicit comments
to provide insights into the function's operation.

<details>
<summary><i>8 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit function with 42 lines has only 7 comment lines
578: function registerTokenTransfer(address from, address to, uint256 id, uint256 amount) internal {
/// @audit function with 41 lines has only 41 comment lines
743: function swapInAMM(
        IUniswapV3Pool univ3pool,
        int256 itmAmounts
    ) internal returns (int256 totalSwapped) {
/// @audit function with 43 lines has only 12 comment lines
848: function _createPositionInAMM(
        IUniswapV3Pool univ3pool,
        uint256 tokenId,
        uint128 positionSize,
        bool isBurn
    ) internal returns (int256 totalMoved, int256 totalCollected, int256 itmAmounts) {
/// @audit function with 62 lines has only 35 comment lines
936: function _createLegInAMM(
        IUniswapV3Pool _univ3pool,
        uint256 _tokenId,
        uint256 _leg,
        uint256 _liquidityChunk,
        bool _isBurn
    ) internal returns (int256 _moved, int256 _itmAmounts, int256 _totalCollected) {
/// @audit function with 52 lines has only 11 comment lines
1255: function _getPremiaDeltas(
        uint256 currentLiquidity,
        int256 collectedAmounts
    ) private pure returns (uint256 deltaPremiumOwed, uint256 deltaPremiumGross) {
/// @audit function with 33 lines has only 8 comment lines
1371: function getAccountPremium(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper,
        int24 atTick,
        uint256 isLong
    ) external view returns (uint128 premiumToken0, uint128 premiumToken1) {
```
[578](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L578) | [743](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L743) | [848](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L848) | [936](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L936) | [1255](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255) | [1371](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1371)

```solidity
File: contracts/types/TokenId.sol

/// @audit function with 32 lines has only 20 comment lines
463: function validate(uint256 self) internal pure returns (uint64) {
```
[463](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L463)

```solidity
File: contracts/libraries/Math.sol

/// @audit function with 45 lines has only 88 comment lines
186: function mulDiv(
        uint256 a,
        uint256 b,
        uint256 denominator
    ) internal pure returns (uint256 result) {
```
[186](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L186)
</details>

### [N-45] Error Declarations Missing Descriptions

NatSpec comments are essential for understanding the purpose and functionality of error declarations. 
Adding descriptive comments improves readability and can aid in debugging.
It's a best practice to provide NatSpec comments for all error declarations in your Solidity contract.

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

51: error NotAuthorized();
54: error UnsafeRecipient();
```
[51](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L51) | [54](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L54)
</details>

### [N-46] `constant`s should be defined rather than using magic numbers

Magic numbers are hardcoded numerical values used directly in the code, making it harder to read and maintain.
Consider using constants instead of magic numbers.

<details>
<summary><i>83 issue instances in 8 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit 2 ** 255
384: s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;
/// @audit 2 ** 64
1281: .mulDiv(collected0, totalLiquidity * 2 ** 64, netLiquidity ** 2)
/// @audit 2 ** 64
1284: .mulDiv(collected1, totalLiquidity * 2 ** 64, netLiquidity ** 2)
```
[384](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L384) | [1281](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1281) | [1284](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1284)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit 0x01ffc9a7
202: interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165
/// @audit 0xd9b67a26
203: interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155
```
[202](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L202) | [203](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L203)

```solidity
File: contracts/types/LeftRight.sol

/// @audit 128
90: return uint128(self >> 128);
/// @audit 128
97: return int128(self >> 128);
/// @audit 128
110: return self + (uint256(left) << 128);
/// @audit 128
120: return self + (int256(int128(left)) << 128);
/// @audit 128
130: return self + (int256(left) << 128);
```
[90](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L90) | [97](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L97) | [110](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L110) | [120](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L120) | [130](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L130)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit 232
90: return self + (uint256(uint24(_tickLower)) << 232);
/// @audit 208
101: return self + ((uint256(uint24(_tickUpper))) << 208);
/// @audit 232
114: return int24(int256(self >> 232));
/// @audit 208
123: return int24(int256(self >> 208));
```
[90](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L90) | [101](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L101) | [114](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L114) | [123](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L123)

```solidity
File: contracts/types/TokenId.sol

/// @audit 0x100_000000000100_000000000100_000000000100_0000000000000000
61: 0x100_000000000100_000000000100_000000000100_0000000000000000;
/// @audit 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF_0000000000000000
64: 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF_0000000000000000;
/// @audit 0x0000000000FE_0000000000FE_0000000000FE_0000000000FE_0000000000000000
67: 0x0000000000FE_0000000000FE_0000000000FE_0000000000FE_0000000000000000;
/// @audit 64
95: return uint256((self >> (64 + legIndex * 48)) % 2);
/// @audit 48
95: return uint256((self >> (64 + legIndex * 48)) % 2);
/// @audit 64
105: return uint256((self >> (64 + legIndex * 48 + 1)) % 128);
/// @audit 48
105: return uint256((self >> (64 + legIndex * 48 + 1)) % 128);
/// @audit 128
105: return uint256((self >> (64 + legIndex * 48 + 1)) % 128);
/// @audit 64
115: return uint256((self >> (64 + legIndex * 48 + 8)) % 2);
/// @audit 48
115: return uint256((self >> (64 + legIndex * 48 + 8)) % 2);
/// @audit 64
125: return uint256((self >> (64 + legIndex * 48 + 9)) % 2);
/// @audit 48
125: return uint256((self >> (64 + legIndex * 48 + 9)) % 2);
/// @audit 64
141: return uint256((self >> (64 + legIndex * 48 + 10)) % 4);
/// @audit 48
141: return uint256((self >> (64 + legIndex * 48 + 10)) % 4);
/// @audit 10
141: return uint256((self >> (64 + legIndex * 48 + 10)) % 4);
/// @audit 64
151: return int24(int256(self >> (64 + legIndex * 48 + 12)));
/// @audit 48
151: return int24(int256(self >> (64 + legIndex * 48 + 12)));
/// @audit 12
151: return int24(int256(self >> (64 + legIndex * 48 + 12)));
/// @audit 64
162: return int24(int256((self >> (64 + legIndex * 48 + 36)) % 4096));
/// @audit 48
162: return int24(int256((self >> (64 + legIndex * 48 + 36)) % 4096));
/// @audit 36
162: return int24(int256((self >> (64 + legIndex * 48 + 36)) % 4096));
/// @audit 4096
162: return int24(int256((self >> (64 + legIndex * 48 + 36)) % 4096));
/// @audit 64
195: return self + (uint256(_asset % 2) << (64 + legIndex * 48));
/// @audit 48
195: return self + (uint256(_asset % 2) << (64 + legIndex * 48));
/// @audit 128
210: return self + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1));
/// @audit 64
210: return self + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1));
/// @audit 48
210: return self + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1));
/// @audit 64
226: return self + ((_isLong % 2) << (64 + legIndex * 48 + 8));
/// @audit 48
226: return self + ((_isLong % 2) << (64 + legIndex * 48 + 8));
/// @audit 64
240: return self + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9));
/// @audit 48
240: return self + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9));
/// @audit 64
254: return self + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10));
/// @audit 48
254: return self + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10));
/// @audit 10
254: return self + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10));
/// @audit 64
268: return self + uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12));
/// @audit 48
268: return self + uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12));
/// @audit 12
268: return self + uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12));
/// @audit 4096
283: return self + (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36));
/// @audit 64
283: return self + (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36));
/// @audit 48
283: return self + (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36));
/// @audit 36
283: return self + (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36));
/// @audit 2 ** 64
337: if (optionRatios < 2 ** 64) {
/// @audit 2 ** 112
339: } else if (optionRatios < 2 ** 112) {
/// @audit 2 ** 160
341: } else if (optionRatios < 2 ** 160) {
/// @audit 2 ** 208
343: } else if (optionRatios < 2 ** 208) {
/// @audit 48
353: return self ^ ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK);
/// @audit 2 ** 64
417: if (optionRatios < 2 ** 64) {
/// @audit 2 ** 112
419: } else if (optionRatios < 2 ** 112) {
/// @audit 2 ** 160
421: } else if (optionRatios < 2 ** 160) {
/// @audit 2 ** 208
423: } else if (optionRatios < 2 ** 208) {
/// @audit 0xFFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFFFFFF
444: return self & 0xFFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFFFFFF;
/// @audit 0xFFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
446: return self & 0xFFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF;
/// @audit 0xFFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
448: return self & 0xFFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF;
/// @audit 0x000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
450: return self & 0x000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF;
/// @audit 64
473: if ((self >> (64 + 48 * i)) != 0) revert Errors.InvalidTokenIdParameter(1);
/// @audit 48
473: if ((self >> (64 + 48 * i)) != 0) revert Errors.InvalidTokenIdParameter(1);
```
[61](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L61) | [64](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L64) | [67](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L67) | [95](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L95) | [95](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L95) | [105](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L105) | [105](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L105) | [105](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L105) | [115](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L115) | [115](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L115) | [125](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L125) | [125](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L125) | [141](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L141) | [141](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L141) | [141](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L141) | [151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L151) | [151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L151) | [151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L151) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L162) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L162) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L162) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L162) | [195](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L195) | [195](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L195) | [210](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L210) | [210](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L210) | [210](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L210) | [226](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L226) | [226](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L226) | [240](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L240) | [240](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L240) | [254](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L254) | [254](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L254) | [254](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L254) | [268](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L268) | [268](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L268) | [268](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L268) | [283](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L283) | [283](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L283) | [283](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L283) | [283](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L283) | [337](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L337) | [339](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L339) | [341](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L341) | [343](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L343) | [353](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L353) | [417](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L417) | [419](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L419) | [421](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L421) | [423](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L423) | [444](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L444) | [446](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L446) | [448](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L448) | [450](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L450) | [473](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L473) | [473](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L473)

```solidity
File: contracts/libraries/Constants.sol

/// @audit 1461446703485210103287273052203988822378723970342
21: 1461446703485210103287273052203988822378723970342;
```
[21](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L21)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit 96
39: return uint64(uint160(univ3pool) >> 96);
/// @audit 32
57: (uint64(uint256(keccak256(abi.encodePacked(token0, token1, fee)))) >> 32);
/// @audit 340275971719517849884101479065584693834
149: if (sqrtPriceX96 < 340275971719517849884101479065584693834) {
/// @audit 340275971719517849884101479065584693834
172: if (sqrtPriceX96 < 340275971719517849884101479065584693834) {
/// @audit 2 ** 192
174: .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
/// @audit 2 ** 128
181: 2 ** 128,
```
[39](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L39) | [57](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L57) | [149](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L149) | [172](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L172) | [174](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L174) | [181](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L181)

```solidity
File: contracts/libraries/SafeTransferLib.sol

/// @audit 0x23b872dd00000000000000000000000000000000000000000000000000000000
24: mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)
/// @audit 36
26: mstore(add(36, p), to) // Append the "to" argument.
/// @audit 68
27: mstore(add(68, p), amount) // Append the "amount" argument.
/// @audit 31
32: or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
/// @audit 100
36: call(gas(), token, 0, p, 100, 0, 32)
/// @audit 32
36: call(gas(), token, 0, p, 100, 0, 32)
```
[24](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L24) | [26](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L26) | [27](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L27) | [32](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L32) | [36](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L36) | [36](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L36)
</details>

### [N-47] Variable Names Not in mixedCase

State or Local Variable names in your contract don't align with the Solidity naming convention.
For clarity and code consistency, it's recommended to use mixedCase for local and state variables that are not constants, and add a trailing underscore for internal variables.
Adhering to this convention helps in improving code readability and maintenance.
[More information in Documentation](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#function-names)

<details>
<summary><i>14 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit - Variable name `s_AddrToPoolIdData` should be in mixedCase
147: mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;
/// @audit - Variable name `s_poolContext` should be in mixedCase
152: mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;
/// @audit - Variable name `s_accountLiquidity` should be in mixedCase
179: mapping(bytes32 positionKey => uint256 removedAndNetLiquidity) internal s_accountLiquidity;
/// @audit - Variable name `s_accountPremiumOwed` should be in mixedCase
288: mapping(bytes32 positionKey => uint256 accountPremium) private s_accountPremiumOwed;
/// @audit - Variable name `s_accountPremiumGross` should be in mixedCase
290: mapping(bytes32 positionKey => uint256 accountPremium) private s_accountPremiumGross;
/// @audit - Variable name `s_accountFeesBase` should be in mixedCase
296: mapping(bytes32 positionKey => int256 baseFees0And1) internal s_accountFeesBase;
/// @audit - Variable name `positionKey_from` should be in mixedCase
594: bytes32 positionKey_from = keccak256(
/// @audit - Variable name `positionKey_to` should be in mixedCase
603: bytes32 positionKey_to = keccak256(
/// @audit - Variable name `premium0X64_base` should be in mixedCase
1272: uint128 premium0X64_base;
/// @audit - Variable name `premium1X64_base` should be in mixedCase
1273: uint128 premium1X64_base;
/// @audit - Variable name `premium0X64_owed` should be in mixedCase
1289: uint128 premium0X64_owed;
/// @audit - Variable name `premium1X64_owed` should be in mixedCase
1290: uint128 premium1X64_owed;
/// @audit - Variable name `premium0X64_gross` should be in mixedCase
1309: uint128 premium0X64_gross;
/// @audit - Variable name `premium1X64_gross` should be in mixedCase
1310: uint128 premium1X64_gross;
```
[147](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L147) | [152](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L152) | [179](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L179) | [288](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L288) | [290](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L290) | [296](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L296) | [594](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L594) | [603](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L603) | [1272](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1272) | [1273](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1273) | [1289](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1289) | [1290](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1290) | [1309](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1309) | [1310](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1310)
</details>

### [N-48] Consider Avoid Loops in Public Functions

Using loops within `public` or `external` functions can pose risks and inefficiencies.
Unpredictable gas consumption due to loop iterations can hinder a function's usability and cost-effectiveness. 
Furthermore, if the loop's logic can be externally influenced or altered, it might be exploited to intentionally drain gas, making the function impractical or uneconomical to call.
To ensure consistent performance and avoid potential vulnerabilities, it's advisable to avoid or limit loops in public functions, especially if their logic can change.

<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

370: while (address(s_poolContext[poolId].pool) != address(0)) {
```
[370](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L370)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

141: for (uint256 i = 0; i < ids.length; ) {
187: for (uint256 i = 0; i < owners.length; ++i) {
```
[141](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L141) | [187](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L187)

```solidity
File: contracts/multicall/Multicall.sol

14: for (uint256 i = 0; i < data.length; ) {
```
[14](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L14)
</details>

### [N-49] Consider moving `msg.sender` checks to a common authorization `modifier`

Functions that are only allowed to be called by a specific actor should use a modifier to check if the caller is the specified actor (e.g., owner, specific role, etc.).
Using `require` to check `msg.sender` in the function body is less efficient and less clear.

Consider refactoring these `require` statements into a modifier for better readability, organization, and gas efficiency.

<details>
<summary><i>8 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

417: if (amount0Owed > 0)
            SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token0,
                decoded.payer,
                msg.sender,
                amount0Owed
            );
424: if (amount1Owed > 0)
            SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token1,
                decoded.payer,
                msg.sender,
                amount1Owed
            );
1216: if (amountToCollect != 0) {
            // first collect amounts from Uniswap corresponding to this position
            // Collect only if there was existing startingLiquidity=liquidities.rightSlot() at that position: collect all fees

            // Collects tokens owed to a liquidity chunk
            (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(
                msg.sender,
                liquidityChunk.tickLower(),
```
[417](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L417) | [424](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L424) | [1216](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1216)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

97: if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
109: if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=
135: if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
162: if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
221: if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
```
[97](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L97) | [109](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L109) | [135](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L135) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L162) | [221](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L221)
</details>

### [N-50] `Solidity Style Guide`: Internal/Private Function Names Without Leading Underscores

In Solidity, it is suggested to use a leading underscore for non-public (private and internal) function names.
This convention helps to distinguish clearly between public/external and non-public functions, improving code clarity.
By adhering to this convention, developers can mitigate potential misinterpretation or errors, thus making the code more comprehensible and easier to maintain.

<details>
<summary><i>74 issue instances in 9 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

321: function beginReentrancyLock(uint64 poolId) internal {
331: function endReentrancyLock(uint64 poolId) internal {
544: function afterTokenTransfer(
        address from,
        address to,
        uint256[] memory ids,
        uint256[] memory amounts
    ) internal override {
563: function afterTokenTransfer(
        address from,
        address to,
        uint256 id,
        uint256 amount
    ) internal override {
578: function registerTokenTransfer(address from, address to, uint256 id, uint256 amount) internal {
743: function swapInAMM(
        IUniswapV3Pool univ3pool,
        int256 itmAmounts
    ) internal returns (int256 totalSwapped) {
```
[321](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L321) | [331](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L331) | [544](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L544) | [563](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L563) | [578](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L578) | [743](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L743)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

252: function afterTokenTransfer(
        address from,
        address to,
        uint256[] memory ids,
        uint256[] memory amounts
    ) internal virtual;
265: function afterTokenTransfer(
        address from,
        address to,
        uint256 id,
        uint256 amount
    ) internal virtual;
```
[252](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L252) | [265](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L265)

```solidity
File: contracts/types/LeftRight.sol

25: function rightSlot(uint256 self) internal pure returns (uint128) {
32: function rightSlot(int256 self) internal pure returns (int128) {
44: function toRightSlot(uint256 self, uint128 right) internal pure returns (uint256) {
54: function toRightSlot(uint256 self, int128 right) internal pure returns (uint256) {
65: function toRightSlot(int256 self, uint128 right) internal pure returns (int256) {
75: function toRightSlot(int256 self, int128 right) internal pure returns (int256) {
89: function leftSlot(uint256 self) internal pure returns (uint128) {
96: function leftSlot(int256 self) internal pure returns (int128) {
108: function toLeftSlot(uint256 self, uint128 left) internal pure returns (uint256) {
118: function toLeftSlot(int256 self, uint128 left) internal pure returns (int256) {
128: function toLeftSlot(int256 self, int128 left) internal pure returns (int256) {
142: function add(uint256 x, uint256 y) internal pure returns (uint256 z) {
159: function add(int256 x, int256 y) internal pure returns (int256 z) {
177: function sub(int256 x, int256 y) internal pure returns (int256 z) {
198: function toInt128(int256 self) internal pure returns (int128 selfAsInt128) {
205: function toUint128(uint256 self) internal pure returns (uint128 selfAsUint128) {
212: function toInt256(uint256 self) internal pure returns (int256) {
```
[25](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L25) | [32](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L32) | [44](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L44) | [54](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L54) | [65](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L65) | [75](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L75) | [89](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L89) | [96](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L96) | [108](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L108) | [118](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L118) | [128](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L128) | [142](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L142) | [159](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L159) | [177](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L177) | [198](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L198) | [205](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L205) | [212](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L212)

```solidity
File: contracts/types/LiquidityChunk.sol

63: function createChunk(
        uint256 self,
        int24 _tickLower,
        int24 _tickUpper,
        uint128 amount
    ) internal pure returns (uint256) {
78: function addLiquidity(uint256 self, uint128 amount) internal pure returns (uint256) {
88: function addTickLower(uint256 self, int24 _tickLower) internal pure returns (uint256) {
98: function addTickUpper(uint256 self, int24 _tickUpper) internal pure returns (uint256) {
112: function tickLower(uint256 self) internal pure returns (int24) {
121: function tickUpper(uint256 self) internal pure returns (int24) {
130: function liquidity(uint256 self) internal pure returns (uint128) {
```
[63](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L63) | [78](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L78) | [88](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L88) | [98](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L98) | [112](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L112) | [121](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L121) | [130](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L130)

```solidity
File: contracts/types/TokenId.sol

80: function univ3pool(uint256 self) internal pure returns (uint64) {
93: function asset(uint256 self, uint256 legIndex) internal pure returns (uint256) {
103: function optionRatio(uint256 self, uint256 legIndex) internal pure returns (uint256) {
113: function isLong(uint256 self, uint256 legIndex) internal pure returns (uint256) {
123: function tokenType(uint256 self, uint256 legIndex) internal pure returns (uint256) {
139: function riskPartner(uint256 self, uint256 legIndex) internal pure returns (uint256) {
149: function strike(uint256 self, uint256 legIndex) internal pure returns (int24) {
160: function width(uint256 self, uint256 legIndex) internal pure returns (int24) {
173: function addUniv3pool(uint256 self, uint64 _poolId) internal pure returns (uint256) {
189: function addAsset(
        uint256 self,
        uint256 _asset,
        uint256 legIndex
    ) internal pure returns (uint256) {
204: function addOptionRatio(
        uint256 self,
        uint256 _optionRatio,
        uint256 legIndex
    ) internal pure returns (uint256) {
220: function addIsLong(
        uint256 self,
        uint256 _isLong,
        uint256 legIndex
    ) internal pure returns (uint256) {
234: function addTokenType(
        uint256 self,
        uint256 _tokenType,
        uint256 legIndex
    ) internal pure returns (uint256) {
248: function addRiskPartner(
        uint256 self,
        uint256 _riskPartner,
        uint256 legIndex
    ) internal pure returns (uint256) {
262: function addStrike(
        uint256 self,
        int24 _strike,
        uint256 legIndex
    ) internal pure returns (uint256) {
276: function addWidth(
        uint256 self,
        int24 _width,
        uint256 legIndex
    ) internal pure returns (uint256) {
298: function addLeg(
        uint256 self,
        uint256 legIndex,
        uint256 _optionRatio,
        uint256 _asset,
        uint256 _isLong,
        uint256 _tokenType,
        uint256 _riskPartner,
        int24 _strike,
        int24 _width
    ) internal pure returns (uint256 tokenId) {
327: function flipToBurnToken(uint256 self) internal pure returns (uint256) {
361: function countLongs(uint256 self) internal pure returns (uint256) {
374: function asTicks(
        uint256 self,
        uint256 legIndex,
        int24 tickSpacing
    ) internal pure returns (int24 legLowerTick, int24 legUpperTick) {
410: function countLegs(uint256 self) internal pure returns (uint256) {
442: function clearLeg(uint256 self, uint256 i) internal pure returns (uint256) {
463: function validate(uint256 self) internal pure returns (uint64) {
```
[80](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L80) | [93](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L93) | [103](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L103) | [113](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L113) | [123](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L123) | [139](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L139) | [149](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L149) | [160](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L160) | [173](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L173) | [189](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L189) | [204](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L204) | [220](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L220) | [234](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L234) | [248](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L248) | [262](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L262) | [276](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L276) | [298](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L298) | [327](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L327) | [361](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L361) | [374](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L374) | [410](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L410) | [442](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L442) | [463](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L463)

```solidity
File: contracts/libraries/CallbackLib.sol

28: function validateCallback(
        address sender,
        address factory,
        PoolFeatures memory features
    ) internal pure {
```
[28](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L28)

```solidity
File: contracts/libraries/Math.sol

23: function absUint(int256 x) internal pure returns (uint256) {
38: function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160 sqrtPriceX96) {
101: function getAmount0ForLiquidity(
        uint256 liquidityChunk
    ) internal pure returns (uint256 amount0) {
119: function getAmount1ForLiquidity(
        uint256 liquidityChunk
    ) internal pure returns (uint256 amount1) {
135: function getLiquidityForAmount0(
        uint256 liquidityChunk,
        uint256 amount0
    ) internal pure returns (uint128 liquidity) {
154: function getLiquidityForAmount1(
        uint256 liquidityChunk,
        uint256 amount1
    ) internal pure returns (uint128 liquidity) {
172: function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {
186: function mulDiv(
        uint256 a,
        uint256 b,
        uint256 denominator
    ) internal pure returns (uint256 result) {
286: function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256 result) {
348: function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256 result) {
410: function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256 result) {
472: function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256 result) {
```
[23](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L23) | [38](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L38) | [101](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L101) | [119](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L119) | [135](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L135) | [154](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L154) | [172](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L172) | [186](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L186) | [286](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L286) | [348](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L348) | [410](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L410) | [472](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L472)

```solidity
File: contracts/libraries/PanopticMath.sol

38: function getPoolId(address univ3pool) internal pure returns (uint64) {
48: function getFinalPoolId(
        uint64 basePoolId,
        address token0,
        address token1,
        uint24 fee
    ) internal pure returns (uint64) {
82: function getLiquidityChunk(
        uint256 tokenId,
        uint256 legIndex,
        uint128 positionSize,
        int24 tickSpacing
    ) internal pure returns (uint256 liquidityChunk) {
145: function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
168: function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
```
[38](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L38) | [48](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L48) | [82](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L82) | [145](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L145) | [168](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L168)

```solidity
File: contracts/libraries/SafeTransferLib.sol

15: function safeTransferFrom(address token, address from, address to, uint256 amount) internal {
```
[15](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L15)
</details>

### [N-51] Invalid NatSpec Comment Style

NatSpec comments in Solidity are meant to be recognized by tools for a variety of purposes such as documentation generation.
The correct style is to use `///` for single-line comments and `/* ... */` for multi-line comments.
Incorrect styles can cause tools to not recognize the comments as intended.

<details>
<summary><i>7 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

359: // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting
361: // @dev some pools may not be deployable if the poolId has a collision (since we take only 8 bytes)
366: // @dev in the unlikely case that there is a collision between the first 8 bytes of two different Uni v3 pools
367: // @dev increase the poolId by a pseudo-random number
585: // @dev see `contracts/types/LiquidityChunk.sol`
823: // @dev note this triggers our swap callback function
881: // @dev see `contracts/types/LiquidityChunk.sol`
```
[359](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L359) | [361](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L361) | [366](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L366) | [367](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L367) | [585](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L585) | [823](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L823) | [881](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L881)
</details>

### [N-52] Consider defining system-wide constants in a single file

System-wide constants should be declared in a single file for better maintainability and readability.
This contract seems to contain constants which could potentially be system-wide and could be better managed if they were centralized in a single location.

<details>
<summary><i>3 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

127: bool internal constant MINT = false;
128: bool internal constant BURN = true;
135: uint128 private constant VEGOID = 2;
```
[127](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L127) | [128](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L128) | [135](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L135)
</details>

### [N-53] Consider using `delete` rather than assigning `false` to clear values

The use of the delete keyword is recommended over simply assigning values to false when you intend to reset the state of a variable.
The delete keyword more closely aligns with the semantic intent of clearing or resetting a variable.
This practice also makes the code more readable and highlights the change in state, which may encourage a more thorough audit of the surrounding logic.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

333: s_poolContext[poolId].locked = false;
```
[333](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L333)
</details>

### [N-54] State Parameter Change Events Should Contain Both Old and New Values

When emitting events that signify critical changes in parameters, it's important to include both the old and new values. 

This aids in auditability, providing more complete information about the state change. It's especially necessary when the new value isn't required to be different from the old one, as this prevents ambiguity in event logs.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

386: emit PoolInitialized(univ3pool);
```
[386](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L386)
</details>

### [N-55] `Solidity Style Guide`: Non-public Variable Names Without Leading Underscores

The naming convention for non-public (private and internal) variables in Solidity recommends the use of a leading underscore.

Since `constants` can be public, to avoid confusion, they should also be prefixed with an underscore.

This practice clearly differentiates between public/external and non-public variables, enhancing code clarity and reducing the likelihood of misinterpretation or errors.
Following this convention improves code readability and maintainability.

<details>
<summary><i>22 issue instances in 4 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

127: bool internal constant MINT = false;
128: bool internal constant BURN = true;
135: uint128 private constant VEGOID = 2;
139: IUniswapV3Factory internal immutable FACTORY;
147: mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;
152: mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;
179: mapping(bytes32 positionKey => uint256 removedAndNetLiquidity) internal s_accountLiquidity;
288: mapping(bytes32 positionKey => uint256 accountPremium) private s_accountPremiumOwed;
290: mapping(bytes32 positionKey => uint256 accountPremium) private s_accountPremiumGross;
296: mapping(bytes32 positionKey => int256 baseFees0And1) internal s_accountFeesBase;
```
[127](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L127) | [128](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L128) | [135](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L135) | [139](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L139) | [147](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L147) | [152](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L152) | [179](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L179) | [288](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L288) | [290](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L290) | [296](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L296)

```solidity
File: contracts/types/LeftRight.sol

16: int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;
```
[16](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L16)

```solidity
File: contracts/types/TokenId.sol

60: uint256 internal constant LONG_MASK =
        0x100_000000000100_000000000100_000000000100_0000000000000000;
63: uint256 internal constant CLEAR_POOLID_MASK =
        0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF_0000000000000000;
66: uint256 internal constant OPTION_RATIO_MASK =
        0x0000000000FE_0000000000FE_0000000000FE_0000000000FE_0000000000000000;
68: int256 internal constant BITMASK_INT24 = 0xFFFFFF;
71: uint256 internal constant RISK_PARTNER_MASK = 0xFFFFFFFFF3FF;
```
[60](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L60) | [63](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L63) | [66](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L66) | [68](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L68) | [71](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L71)

```solidity
File: contracts/libraries/Constants.sol

8: uint256 internal constant FP96 = 0x1000000000000000000000000;
11: int24 internal constant MIN_V3POOL_TICK = -887272;
14: int24 internal constant MAX_V3POOL_TICK = 887272;
17: uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;
20: uint160 internal constant MAX_V3POOL_SQRT_RATIO =
        1461446703485210103287273052203988822378723970342;
25: bytes32 internal constant V3POOL_INIT_CODE_HASH =
        keccak256(
            hex"6101606040523480156200001257600080fd5b503060601b60805260408051630890357360e41b81529051600091339163890357309160048082019260a092909190829003018186803b1580156200005657600080fd5b505afa1580156200006b573d6000803e3d6000fd5b505050506040513d60a08110156200008257600080fd5b508051602080830151604084015160608086015160809096015160e896871b6001600160e81b0319166101005291811b6001600160601b031990811660e05292811b831660c0529390931b1660a052600282810b900b90921b610120529150620000f79082906200010f811b62002b8417901c565b60801b6001600160801b03191661014052506200017d565b60008082600281900b620d89e719816200012557fe5b05029050600083600281900b620d89e8816200013d57fe5b0502905060008460020b83830360020b816200015557fe5b0560010190508062ffffff166001600160801b038016816200017357fe5b0495945050505050565b60805160601c60a05160601c60c05160601c60e05160601c6101005160e81c6101205160e81c6101405160801c61567e6200024a60003980611fee5280614b5f5280614b96525080610c0052806128fd5280614bca5280614bfc525080610cef52806119cb5280611a0252806129455250806111c75280611a855280611ef4528061244452806129215280613e6b5250806108d252806112f55280611a545280611e8e52806123be5280613d2252508061207b528061227d52806128d9525080612bfb525061567e6000f3fe608060405234801561001057600080fd5b50600436106101ae5760003560e01c806370cf754a116100ee578063c45a015511610097578063ddca3f4311610071578063ddca3f4314610800578063f305839914610820578063f30dba9314610828578063f637731d146108aa576101ae565b8063c45a0155146107d1578063d0c93a7c146107d9578063d21220a7146107f8576101ae565b8063883bdbfd116100c8578063883bdbfd14610633578063a34123a71461073c578063a38807f214610776576101ae565b806370cf754a146105c65780638206a4d1146105ce57806385b66729146105f6576101ae565b80633850c7bd1161015b578063490e6cbc11610135578063490e6cbc146104705780634f1eb3d8146104fc578063514ea4bf1461054d5780635339c296146105a6576101ae565b80633850c7bd1461035b5780633c8a7d8d146103b45780634614131914610456576101ae565b80631ad8b03b1161018c5780631ad8b03b146102aa578063252c09d7146102e157806332148f6714610338576101ae565b80630dfe1681146101b3578063128acb08146101d75780631a68650214610286575b600080fd5b6101bb6108d0565b604080516001600160a01b039092168252519081900360200190f35b61026d600480360360a08110156101ed57600080fd5b6001600160a01b0382358116926020810135151592604082013592606083013516919081019060a08101608082013564010000000081111561022e57600080fd5b82018360208201111561024057600080fd5b8035906020019184600183028401116401000000008311171561026257600080fd5b5090925090506108f4565b6040805192835260208301919091528051918290030190f35b61028e6114ad565b604080516001600160801b039092168252519081900360200190f35b6102b26114bc565b60405180836001600160801b03168152602001826001600160801b031681526020019250505060405180910390f35b6102fe600480360360208110156102f757600080fd5b50356114d6565b6040805163ffffffff909516855260069390930b60208501526001600160a01b039091168383015215156060830152519081900360800190f35b6103596004803603602081101561034e57600080fd5b503561ffff1661151c565b005b610363611616565b604080516001600160a01b03909816885260029690960b602088015261ffff9485168787015292841660608701529216608085015260ff90911660a0840152151560c0830152519081900360e00190f35b61026d600480360360a08110156103ca57600080fd5b6001600160a01b03823516916020810135600290810b92604083013590910b916001600160801b036060820135169181019060a08101608082013564010000000081111561041757600080fd5b82018360208201111561042957600080fd5b8035906020019184600183028401116401000000008311171561044b57600080fd5b509092509050611666565b61045e611922565b60408051918252519081900360200190f35b6103596004803603608081101561048657600080fd5b6001600160a01b0382351691602081013591604082013591908101906080810160608201356401000000008111156104bd57600080fd5b8201836020820111156104cf57600080fd5b803590602001918460018302840111640100000000831117156104f157600080fd5b509092509050611928565b6102b2600480360360a081101561051257600080fd5b506001600160a01b03813516906020810135600290810b91604081013590910b906001600160801b0360608201358116916080013516611d83565b61056a6004803603602081101561056357600080fd5b5035611f9d565b604080516001600160801b0396871681526020810195909552848101939093529084166060840152909216608082015290519081900360a00190f35b61045e600480360360208110156105bc57600080fd5b503560010b611fda565b61028e611fec565b610359600480360360408110156105e457600080fd5b5060ff81358116916020013516612010565b6102b26004803603606081101561060c57600080fd5b506001600160a01b03813516906001600160801b036020820135811691604001351661220f565b6106a36004803603602081101561064957600080fd5b81019060208101813564010000000081111561066457600080fd5b82018360208201111561067657600080fd5b8035906020019184602083028401116401000000008311171561069857600080fd5b5090925090506124dc565b604051808060200180602001838103835285818151815260200191508051906020019060200280838360005b838110156106e75781810151838201526020016106cf565b50505050905001838103825284818151815260200191508051906020019060200280838360005b8381101561072657818101518382015260200161070e565b5050505090500194505050505060405180910390f35b61026d6004803603606081101561075257600080fd5b508035600290810b91602081013590910b90604001356001600160801b0316612569565b6107a06004803603604081101561078c57600080fd5b508035600290810b9160200135900b6126e0565b6040805160069490940b84526001600160a01b03909216602084015263ffffffff1682820152519081900360600190f35b6101bb6128d7565b6107e16128fb565b6040805160029290920b8252519081900360200190f35b6101bb61291f565b610808612943565b6040805162ffffff9092168252519081900360200190f35b61045e612967565b6108486004803603602081101561083e57600080fd5b503560020b61296d565b604080516001600160801b039099168952600f9790970b602089015287870195909552606087019390935260069190910b60808601526001600160a01b031660a085015263ffffffff1660c0840152151560e083015251908190036101000190f35b610359600480360360208110156108c057600080fd5b50356001600160a01b03166129db565b7f000000000000000000000000000000000000000000000000000000000000000081565b6000806108ff612bf0565b85610936576040805162461bcd60e51b8152602060048201526002602482015261415360f01b604482015290519081900360640190fd5b6040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b900b602083015261ffff600160b81b8204811693830193909352600160c81b810483166060830152600160d81b8104909216608082015260ff600160e81b8304811660a0830152600160f01b909204909116151560c082018190526109ef576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b87610a3a5780600001516001600160a01b0316866001600160a01b0316118015610a35575073fffd8963efd1fc6a506488495d951d5263988d266001600160a01b038716105b610a6c565b80600001516001600160a01b0316866001600160a01b0316108015610a6c57506401000276a36001600160a01b038716115b610aa3576040805162461bcd60e51b815260206004820152600360248201526214d41360ea1b604482015290519081900360640190fd5b6000805460ff60f01b191681556040805160c08101909152808a610ad25760048460a0015160ff16901c610ae5565b60108460a0015160ff1681610ae357fe5b065b60ff1681526004546001600160801b03166020820152604001610b06612c27565b63ffffffff168152602001600060060b815260200160006001600160a01b031681526020016000151581525090506000808913905060006040518060e001604052808b81526020016000815260200185600001516001600160a01b03168152602001856020015160020b81526020018c610b8257600254610b86565b6001545b815260200160006001600160801b0316815260200184602001516001600160801b031681525090505b805115801590610bd55750886001600160a01b031681604001516001600160a01b031614155b15610f9f57610be261560e565b60408201516001600160a01b031681526060820151610c25906006907f00000000000000000000000000000000000000000000000000000000000000008f612c2b565b15156040830152600290810b810b60208301819052620d89e719910b1215610c5657620d89e7196020820152610c75565b6020810151620d89e860029190910b1315610c7557620d89e860208201525b610c828160200151612d6d565b6001600160a01b031660608201526040820151610d13908d610cbc578b6001600160a01b031683606001516001600160a01b031611610cd6565b8b6001600160a01b031683606001516001600160a01b0316105b610ce4578260600151610ce6565b8b5b60c085015185517f000000000000000000000000000000000000000000000000000000000000000061309f565b60c085015260a084015260808301526001600160a01b031660408301528215610d7557610d498160c00151826080015101613291565b825103825260a0810151610d6b90610d6090613291565b6020840151906132a7565b6020830152610db0565b610d828160a00151613291565b825101825260c08101516080820151610daa91610d9f9101613291565b6020840151906132c3565b60208301525b835160ff1615610df6576000846000015160ff168260c0015181610dd057fe5b60c0840180519290910491829003905260a0840180519091016001600160801b03169052505b60c08201516001600160801b031615610e3557610e298160c00151600160801b8460c001516001600160801b03166132d9565b60808301805190910190525b80606001516001600160a01b031682604001516001600160a01b03161415610f5e57806040015115610f35578360a00151610ebf57610e9d846040015160008760200151886040015188602001518a606001516008613389909695949392919063ffffffff16565b6001600160a01b03166080860152600690810b900b6060850152600160a08501525b6000610f0b82602001518e610ed657600154610edc565b84608001515b8f610eeb578560800151610eef565b6002545b608089015160608a015160408b0151600595949392919061351c565b90508c15610f17576000035b610f258360c00151826135ef565b6001600160801b031660c0840152505b8b610f44578060200151610f4d565b60018160200151035b600290810b900b6060830152610f99565b80600001516001600160a01b031682604001516001600160a01b031614610f9957610f8c82604001516136a5565b600290810b900b60608301525b50610baf565b836020015160020b816060015160020b1461107a57600080610fed86604001518660400151886020015188602001518a606001518b6080015160086139d1909695949392919063ffffffff16565b604085015160608601516000805461ffff60c81b1916600160c81b61ffff958616021761ffff60b81b1916600160b81b95909416949094029290921762ffffff60a01b1916600160a01b62ffffff60029490940b93909316929092029190911773ffffffffffffffffffffffffffffffffffffffff19166001600160a01b03909116179055506110ac9050565b60408101516000805473ffffffffffffffffffffffffffffffffffffffff19166001600160a01b039092169190911790555b8060c001516001600160801b031683602001516001600160801b0316146110f25760c0810151600480546001600160801b0319166001600160801b039092169190911790555b8a1561114257608081015160015560a08101516001600160801b03161561113d5760a0810151600380546001600160801b031981166001600160801b03918216909301169190911790555b611188565b608081015160025560a08101516001600160801b0316156111885760a0810151600380546001600160801b03808216600160801b92839004821690940116029190911790555b8115158b1515146111a157602081015181518b036111ae565b80600001518a0381602001515b90965094508a156112e75760008512156111f0576111f07f00000000000000000000000000000000000000000000000000000000000000008d87600003613b86565b60006111fa613cd4565b9050336001600160a01b031663fa461e3388888c8c6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b15801561127e57600080fd5b505af1158015611292573d6000803e3d6000fd5b5050505061129e613cd4565b6112a88289613e0d565b11156112e1576040805162461bcd60e51b815260206004820152600360248201526249494160e81b604482015290519081900360640190fd5b50611411565b600086121561131e5761131e7f00000000000000000000000000000000000000000000000000000000000000008d88600003613b86565b6000611328613e1d565b9050336001600160a01b031663fa461e3388888c8c6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b1580156113ac57600080fd5b505af11580156113c0573d6000803e3d6000fd5b505050506113cc613e1d565b6113d68288613e0d565b111561140f576040805162461bcd60e51b815260206004820152600360248201526249494160e81b604482015290519081900360640190fd5b505b60408082015160c083015160608085015184518b8152602081018b90526001600160a01b03948516818701526001600160801b039093169183019190915260020b60808201529151908e169133917fc42079f94a6350d7e6235f29174924f928cc2ac818eb64fed8004e115fbcca679181900360a00190a350506000805460ff60f01b1916600160f01b17905550919890975095505050505050565b6004546001600160801b031681565b6003546001600160801b0380821691600160801b90041682565b60088161ffff81106114e757600080fd5b015463ffffffff81169150640100000000810460060b90600160581b81046001600160a01b031690600160f81b900460ff1684565b600054600160f01b900460ff16611560576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19169055611575612bf0565b60008054600160d81b900461ffff169061159160088385613eb5565b6000805461ffff808416600160d81b810261ffff60d81b19909316929092179092559192508316146115fe576040805161ffff80851682528316602082015281517fac49e518f90a358f652e4400164f05a5d8f7e35e7747279bc3a93dbf584e125a929181900390910190a15b50506000805460ff60f01b1916600160f01b17905550565b6000546001600160a01b03811690600160a01b810460020b9061ffff600160b81b8204811691600160c81b8104821691600160d81b8204169060ff600160e81b8204811691600160f01b90041687565b600080548190600160f01b900460ff166116ad576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b191690556001600160801b0385166116cd57600080fd5b60008061171b60405180608001604052808c6001600160a01b031681526020018b60020b81526020018a60020b81526020016117118a6001600160801b0316613f58565b600f0b9052613f69565b9250925050819350809250600080600086111561173d5761173a613cd4565b91505b841561174e5761174b613e1d565b90505b336001600160a01b031663d348799787878b8b6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b1580156117d057600080fd5b505af11580156117e4573d6000803e3d6000fd5b50505050600086111561183b576117f9613cd4565b6118038388613e0d565b111561183b576040805162461bcd60e51b815260206004820152600260248201526104d360f41b604482015290519081900360640190fd5b841561188b57611849613e1d565b6118538287613e0d565b111561188b576040805162461bcd60e51b81526020600482015260026024820152614d3160f01b604482015290519081900360640190fd5b8960020b8b60020b8d6001600160a01b03167f7a53080ba414158be7ec69b987b5fb7d07dee101fe85488f0853ae16239d0bde338d8b8b60405180856001600160a01b03168152602001846001600160801b0316815260200183815260200182815260200194505050505060405180910390a450506000805460ff60f01b1916600160f01b17905550919890975095505050505050565b60025481565b600054600160f01b900460ff1661196c576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19169055611981612bf0565b6004546001600160801b0316806119c3576040805162461bcd60e51b81526020600482015260016024820152601360fa1b604482015290519081900360640190fd5b60006119f8867f000000000000000000000000000000000000000000000000000000000000000062ffffff16620f42406141a9565b90506000611a2f867f000000000000000000000000000000000000000000000000000000000000000062ffffff16620f42406141a9565b90506000611a3b613cd4565b90506000611a47613e1d565b90508815611a7a57611a7a7f00000000000000000000000000000000000000000000000000000000000000008b8b613b86565b8715611aab57611aab7f00000000000000000000000000000000000000000000000000000000000000008b8a613b86565b336001600160a01b031663e9cbafb085858a8a6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b158015611b2d57600080fd5b505af1158015611b41573d6000803e3d6000fd5b505050506000611b4f613cd4565b90506000611b5b613e1d565b905081611b688588613e0d565b1115611ba0576040805162461bcd60e51b8152602060048201526002602482015261046360f41b604482015290519081900360640190fd5b80611bab8487613e0d565b1115611be3576040805162461bcd60e51b8152602060048201526002602482015261463160f01b604482015290519081900360640190fd5b8382038382038115611c725760008054600160e81b9004600f16908115611c16578160ff168481611c1057fe5b04611c19565b60005b90506001600160801b03811615611c4c57600380546001600160801b038082168401166001600160801b03199091161790555b611c66818503600160801b8d6001600160801b03166132d9565b60018054909101905550505b8015611cfd5760008054600160e81b900460041c600f16908115611ca2578160ff168381611c9c57fe5b04611ca5565b60005b90506001600160801b03811615611cd757600380546001600160801b03600160801b8083048216850182160291161790555b611cf1818403600160801b8d6001600160801b03166132d9565b60028054909101905550505b8d6001600160a01b0316336001600160a01b03167fbdbdb71d7860376ba52b25a5028beea23581364a40522f6bcfb86bb1f2dca6338f8f86866040518085815260200184815260200183815260200182815260200194505050505060405180910390a350506000805460ff60f01b1916600160f01b179055505050505050505050505050565b600080548190600160f01b900460ff16611dca576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19168155611de460073389896141e3565b60038101549091506001600160801b0390811690861611611e055784611e14565b60038101546001600160801b03165b60038201549093506001600160801b03600160801b909104811690851611611e3c5783611e52565b6003810154600160801b90046001600160801b03165b91506001600160801b03831615611eb7576003810180546001600160801b031981166001600160801b03918216869003821617909155611eb7907f0000000000000000000000000000000000000000000000000000000000000000908a908616613b86565b6001600160801b03821615611f1d576003810180546001600160801b03600160801b808304821686900382160291811691909117909155611f1d907f0000000000000000000000000000000000000000000000000000000000000000908a908516613b86565b604080516001600160a01b038a1681526001600160801b0380861660208301528416818301529051600288810b92908a900b9133917f70935338e69775456a85ddef226c395fb668b63fa0115f5f20610b388e6ca9c0919081900360600190a4506000805460ff60f01b1916600160f01b17905590969095509350505050565b60076020526000908152604090208054600182015460028301546003909301546001600160801b0392831693919281811691600160801b90041685565b60066020526000908152604090205481565b7f000000000000000000000000000000000000000000000000000000000000000081565b600054600160f01b900460ff16612054576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916905560408051638da5cb5b60e01b815290516001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001691638da5cb5b916004808301926020929190829003018186803b1580156120c157600080fd5b505afa1580156120d5573d6000803e3d6000fd5b505050506040513d60208110156120eb57600080fd5b50516001600160a01b0316331461210157600080fd5b60ff82161580612124575060048260ff16101580156121245750600a8260ff1611155b801561214e575060ff8116158061214e575060048160ff161015801561214e5750600a8160ff1611155b61215757600080fd5b60008054610ff0600484901b16840160ff908116600160e81b9081027fffff00ffffffffffffffffffffffffffffffffffffffffffffffffffffffffff841617909355919004167f973d8d92bb299f4af6ce49b52a8adb85ae46b9f214c4c4fc06ac77401237b1336010826040805160ff9390920683168252600f600486901c16602083015286831682820152918516606082015290519081900360800190a150506000805460ff60f01b1916600160f01b17905550565b600080548190600160f01b900460ff16612256576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916905560408051638da5cb5b60e01b815290516001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001691638da5cb5b916004808301926020929190829003018186803b1580156122c357600080fd5b505afa1580156122d7573d6000803e3d6000fd5b505050506040513d60208110156122ed57600080fd5b50516001600160a01b0316331461230357600080fd5b6003546001600160801b039081169085161161231f578361232c565b6003546001600160801b03165b6003549092506001600160801b03600160801b9091048116908416116123525782612366565b600354600160801b90046001600160801b03165b90506001600160801b038216156123e7576003546001600160801b038381169116141561239557600019909101905b600380546001600160801b031981166001600160801b039182168590038216179091556123e7907f00000000000000000000000000000000000000000000000000000000000000009087908516613b86565b6001600160801b0381161561246d576003546001600160801b03828116600160801b90920416141561241857600019015b600380546001600160801b03600160801b80830482168590038216029181169190911790915561246d907f00000000000000000000000000000000000000000000000000000000000000009087908416613b86565b604080516001600160801b0380851682528316602082015281516001600160a01b0388169233927f596b573906218d3411850b26a6b437d6c4522fdb43d2d2386263f86d50b8b151929081900390910190a36000805460ff60f01b1916600160f01b1790559094909350915050565b6060806124e7612bf0565b61255e6124f2612c27565b858580806020026020016040519081016040528093929190818152602001838360200280828437600092018290525054600454600896959450600160a01b820460020b935061ffff600160b81b8304811693506001600160801b0390911691600160c81b900416614247565b915091509250929050565b600080548190600160f01b900460ff166125b0576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916815560408051608081018252338152600288810b602083015287900b918101919091528190819061260990606081016125fc6001600160801b038a16613f58565b600003600f0b9052613f69565b925092509250816000039450806000039350600085118061262a5750600084115b15612669576003830180546001600160801b038082168089018216600160801b93849004831689019092169092029091176001600160801b0319161790555b604080516001600160801b0388168152602081018790528082018690529051600289810b92908b900b9133917f0c396cd989a39f4459b5fa1aed6a9a8dcdbc45908acfd67e028cd568da98982c919081900360600190a450506000805460ff60f01b1916600160f01b179055509094909350915050565b60008060006126ed612bf0565b6126f785856143a1565b600285810b810b60009081526005602052604080822087840b90930b825281206003830154600681900b9367010000000000000082046001600160a01b0316928492600160d81b810463ffffffff169284929091600160f81b900460ff168061275f57600080fd5b6003820154600681900b985067010000000000000081046001600160a01b03169650600160d81b810463ffffffff169450600160f81b900460ff16806127a457600080fd5b50506040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b810b6020840181905261ffff600160b81b8404811695850195909552600160c81b830485166060850152600160d81b8304909416608084015260ff600160e81b8304811660a0850152600160f01b909204909116151560c08301529093508e810b91900b1215905061284d575093909403965090039350900390506128d0565b8a60020b816020015160020b12156128c1576000612869612c27565b602083015160408401516004546060860151939450600093849361289f936008938893879392916001600160801b031690613389565b9a9003989098039b5050949096039290920396509091030392506128d0915050565b50949093039650039350900390505b9250925092565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b60015481565b60056020526000908152604090208054600182015460028301546003909301546001600160801b03831693600160801b909304600f0b9290600681900b9067010000000000000081046001600160a01b031690600160d81b810463ffffffff1690600160f81b900460ff1688565b6000546001600160a01b031615612a1e576040805162461bcd60e51b8152602060048201526002602482015261414960f01b604482015290519081900360640190fd5b6000612a29826136a5565b9050600080612a41612a39612c27565b60089061446a565b6040805160e0810182526001600160a01b038816808252600288810b6020808501829052600085870181905261ffff898116606088018190529089166080880181905260a08801839052600160c0909801979097528154600160f01b73ffffffffffffffffffffffffffffffffffffffff19909116871762ffffff60a01b1916600160a01b62ffffff9787900b9790971696909602959095177fffffffffff00000000ffffffffffffffffffffffffffffffffffffffffffffff16600160c81b9091021761ffff60d81b1916600160d81b909602959095177fff0000ffffffffffffffffffffffffffffffffffffffffffffffffffffffffff1692909217909355835191825281019190915281519395509193507f98636036cb66a9c19a37435efc1e90142190214e8abeb821bdba3f2990dd4c9592918290030190a150505050565b60008082600281900b620d89e71981612b9957fe5b05029050600083600281900b620d89e881612bb057fe5b0502905060008460020b83830360020b81612bc757fe5b0560010190508062ffffff166001600160801b03801681612be457fe5b0493505050505b919050565b306001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001614612c2557600080fd5b565b4290565b60008060008460020b8660020b81612c3f57fe5b05905060008660020b128015612c6657508460020b8660020b81612c5f57fe5b0760020b15155b15612c7057600019015b8315612ce557600080612c82836144b6565b600182810b810b600090815260208d9052604090205460ff83169190911b80016000190190811680151597509294509092509085612cc757888360ff16860302612cda565b88612cd1826144c8565b840360ff168603025b965050505050612d63565b600080612cf4836001016144b6565b91509150600060018260ff166001901b031990506000818b60008660010b60010b8152602001908152602001600020541690508060001415955085612d4657888360ff0360ff16866001010102612d5c565b8883612d5183614568565b0360ff168660010101025b9650505050505b5094509492505050565b60008060008360020b12612d84578260020b612d8c565b8260020b6000035b9050620d89e8811115612dca576040805162461bcd60e51b81526020600482015260016024820152601560fa1b604482015290519081900360640190fd5b600060018216612dde57600160801b612df0565b6ffffcb933bd6fad37aa2d162d1a5940015b70ffffffffffffffffffffffffffffffffff1690506002821615612e24576ffff97272373d413259a46990580e213a0260801c5b6004821615612e43576ffff2e50f5f656932ef12357cf3c7fdcc0260801c5b6008821615612e62576fffe5caca7e10e4e61c3624eaa0941cd00260801c5b6010821615612e81576fffcb9843d60f6159c9db58835c9266440260801c5b6020821615612ea0576fff973b41fa98c081472e6896dfb254c00260801c5b6040821615612ebf576fff2ea16466c96a3843ec78b326b528610260801c5b6080821615612ede576ffe5dee046a99a2a811c461f1969c30530260801c5b610100821615612efe576ffcbe86c7900a88aedcffc83b479aa3a40260801c5b610200821615612f1e576ff987a7253ac413176f2b074cf7815e540260801c5b610400821615612f3e576ff3392b0822b70005940c7a398e4b70f30260801c5b610800821615612f5e576fe7159475a2c29b7443b29c7fa6e889d90260801c5b611000821615612f7e576fd097f3bdfd2022b8845ad8f792aa58250260801c5b612000821615612f9e576fa9f746462d870fdf8a65dc1f90e061e50260801c5b614000821615612fbe576f70d869a156d2a1b890bb3df62baf32f70260801c5b618000821615612fde576f31be135f97d08fd981231505542fcfa60260801c5b62010000821615612fff576f09aa508b5b7a84e1c677de54f3e99bc90260801c5b6202000082161561301f576e5d6af8dedb81196699c329225ee6040260801c5b6204000082161561303e576d2216e584f5fa1ea926041bedfe980260801c5b6208000082161561305b576b048a170391f7dc42444e8fa20260801c5b60008460020b131561307657806000198161307257fe5b0490505b64010000000081061561308a57600161308d565b60005b60ff16602082901c0192505050919050565b60008080806001600160a01b03808916908a1610158187128015906131245760006130d88989620f42400362ffffff16620f42406132d9565b9050826130f1576130ec8c8c8c6001614652565b6130fe565b6130fe8b8d8c60016146cd565b955085811061310f578a965061311e565b61311b8c8b838661478a565b96505b5061316e565b8161313b576131368b8b8b60006146cd565b613148565b6131488a8c8b6000614652565b935083886000031061315c5789955061316e565b61316b8b8a8a600003856147d6565b95505b6001600160a01b038a81169087161482156131d15780801561318d5750815b6131a35761319e878d8c60016146cd565b6131a5565b855b95508080156131b2575081155b6131c8576131c3878d8c6000614652565b6131ca565b845b945061321b565b8080156131db5750815b6131f1576131ec8c888c6001614652565b6131f3565b855b9550808015613200575081155b613216576132118c888c60006146cd565b613218565b845b94505b8115801561322b57508860000385115b15613237578860000394505b81801561325657508a6001600160a01b0316876001600160a01b031614155b15613265578589039350613282565b61327f868962ffffff168a620f42400362ffffff166141a9565b93505b50505095509550955095915050565b6000600160ff1b82106132a357600080fd5b5090565b808203828113156000831215146132bd57600080fd5b92915050565b818101828112156000831215146132bd57600080fd5b600080806000198587098686029250828110908390030390508061330f576000841161330457600080fd5b508290049050613382565b80841161331b57600080fd5b6000848688096000868103871696879004966002600389028118808a02820302808a02820302808a02820302808a02820302808a02820302808a02909103029181900381900460010186841190950394909402919094039290920491909117919091029150505b9392505050565b60008063ffffffff8716613430576000898661ffff1661ffff81106133aa57fe5b60408051608081018252919092015463ffffffff8082168084526401000000008304600690810b810b900b6020850152600160581b83046001600160a01b031694840194909452600160f81b90910460ff16151560608301529092508a161461341c57613419818a8988614822565b90505b806020015181604001519250925050613510565b8688036000806134458c8c858c8c8c8c6148d2565b91509150816000015163ffffffff168363ffffffff161415613477578160200151826040015194509450505050613510565b805163ffffffff8481169116141561349f578060200151816040015194509450505050613510565b8151815160208085015190840151918390039286039163ffffffff80841692908516910360060b816134cd57fe5b05028460200151018263ffffffff168263ffffffff1686604001518660400151036001600160a01b031602816134ff57fe5b048560400151019650965050505050505b97509795505050505050565b600295860b860b60009081526020979097526040909620600181018054909503909455938301805490920390915560038201805463ffffffff600160d81b6001600160a01b036701000000000000008085048216909603169094027fffffffffff0000000000000000000000000000000000000000ffffffffffffff90921691909117600681810b90960390950b66ffffffffffffff1666ffffffffffffff199095169490941782810485169095039093160263ffffffff60d81b1990931692909217905554600160801b9004600f0b90565b60008082600f0b121561365457826001600160801b03168260000384039150816001600160801b03161061364f576040805162461bcd60e51b81526020600482015260026024820152614c5360f01b604482015290519081900360640190fd5b6132bd565b826001600160801b03168284019150816001600160801b031610156132bd576040805162461bcd60e51b81526020600482015260026024820152614c4160f01b604482015290519081900360640190fd5b60006401000276a36001600160a01b038316108015906136e1575073fffd8963efd1fc6a506488495d951d5263988d266001600160a01b038316105b613716576040805162461bcd60e51b81526020600482015260016024820152602960f91b604482015290519081900360640190fd5b77ffffffffffffffffffffffffffffffffffffffff00000000602083901b166001600160801b03811160071b81811c67ffffffffffffffff811160061b90811c63ffffffff811160051b90811c61ffff811160041b90811c60ff8111600390811b91821c600f811160021b90811c918211600190811b92831c979088119617909417909217179091171717608081106137b757607f810383901c91506137c1565b80607f0383901b91505b908002607f81811c60ff83811c9190911c800280831c81831c1c800280841c81841c1c800280851c81851c1c800280861c81861c1c800280871c81871c1c800280881c81881c1c800280891c81891c1c8002808a1c818a1c1c8002808b1c818b1c1c8002808c1c818c1c1c8002808d1c818d1c1c8002808e1c9c81901c9c909c1c80029c8d901c9e9d607f198f0160401b60c09190911c678000000000000000161760c19b909b1c674000000000000000169a909a1760c29990991c672000000000000000169890981760c39790971c671000000000000000169690961760c49590951c670800000000000000169490941760c59390931c670400000000000000169290921760c69190911c670200000000000000161760c79190911c670100000000000000161760c89190911c6680000000000000161760c99190911c6640000000000000161760ca9190911c6620000000000000161760cb9190911c6610000000000000161760cc9190911c6608000000000000161760cd9190911c66040000000000001617693627a301d71055774c8581026f028f6481ab7f045a5af012a19d003aa9198101608090811d906fdb2df09e81959a81455e260799a0632f8301901d600281810b9083900b146139c257886001600160a01b03166139a682612d6d565b6001600160a01b031611156139bb57816139bd565b805b6139c4565b815b9998505050505050505050565b6000806000898961ffff1661ffff81106139e757fe5b60408051608081018252919092015463ffffffff8082168084526401000000008304600690810b810b900b6020850152600160581b83046001600160a01b031694840194909452600160f81b90910460ff161515606083015290925089161415613a575788859250925050613510565b8461ffff168461ffff16118015613a7857506001850361ffff168961ffff16145b15613a8557839150613a89565b8491505b8161ffff168960010161ffff1681613a9d57fe5b069250613aac81898989614822565b8a8461ffff1661ffff8110613abd57fe5b825191018054602084015160408501516060909501511515600160f81b027effffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff6001600160a01b03909616600160581b027fff0000000000000000000000000000000000000000ffffffffffffffffffffff60069390930b66ffffffffffffff16640100000000026affffffffffffff000000001963ffffffff90971663ffffffff199095169490941795909516929092171692909217929092161790555097509795505050505050565b604080516001600160a01b038481166024830152604480830185905283518084039091018152606490920183526020820180516001600160e01b031663a9059cbb60e01b1781529251825160009485949389169392918291908083835b60208310613c025780518252601f199092019160209182019101613be3565b6001836020036101000a0380198251168184511680821785525050505050509050019150506000604051808303816000865af19150503d8060008114613c64576040519150601f19603f3d011682016040523d82523d6000602084013e613c69565b606091505b5091509150818015613c97575080511580613c975750808060200190516020811015613c9457600080fd5b50515b613ccd576040805162461bcd60e51b81526020600482015260026024820152612a2360f11b604482015290519081900360640190fd5b5050505050565b604080513060248083019190915282518083039091018152604490910182526020810180516001600160e01b03166370a0823160e01b17815291518151600093849384936001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001693919290918291908083835b60208310613d6d5780518252601f199092019160209182019101613d4e565b6001836020036101000a038019825116818451168082178552505050505050905001915050600060405180830381855afa9150503d8060008114613dcd576040519150601f19603f3d011682016040523d82523d6000602084013e613dd2565b606091505b5091509150818015613de657506020815110155b613def57600080fd5b808060200190516020811015613e0457600080fd5b50519250505090565b808201828110156132bd57600080fd5b604080513060248083019190915282518083039091018152604490910182526020810180516001600160e01b03166370a0823160e01b17815291518151600093849384936001600160a01b037f000000000000000000000000000000000000000000000000000000000000000016939192909182919080838360208310613d6d5780518252601f199092019160209182019101613d4e565b6000808361ffff1611613ef3576040805162461bcd60e51b81526020600482015260016024820152604960f81b604482015290519081900360640190fd5b8261ffff168261ffff1611613f09575081613382565b825b8261ffff168161ffff161015613f4f576001858261ffff1661ffff8110613f2e57fe5b01805463ffffffff191663ffffffff92909216919091179055600101613f0b565b50909392505050565b80600f81900b8114612beb57600080fd5b6000806000613f76612bf0565b613f88846020015185604001516143a1565b6040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b900b602080840182905261ffff600160b81b8404811685870152600160c81b84048116606080870191909152600160d81b8504909116608086015260ff600160e81b8504811660a0870152600160f01b909404909316151560c08501528851908901519489015192890151939461402c9491939092909190614acf565b93508460600151600f0b6000146141a157846020015160020b816020015160020b12156140815761407a6140638660200151612d6d565b6140708760400151612d6d565b8760600151614c84565b92506141a1565b846040015160020b816020015160020b12156141775760045460408201516001600160801b03909116906140d3906140b7612c27565b60208501516060860151608087015160089493929187916139d1565b6000805461ffff60c81b1916600160c81b61ffff938416021761ffff60b81b1916600160b81b939092169290920217905581516040870151614123919061411990612d6d565b8860600151614c84565b93506141416141358760200151612d6d565b83516060890151614cc8565b92506141518187606001516135ef565b600480546001600160801b0319166001600160801b0392909216919091179055506141a1565b61419e6141878660200151612d6d565b6141948760400151612d6d565b8760600151614cc8565b91505b509193909250565b60006141b68484846132d9565b9050600082806141c257fe5b84860911156133825760001981106141d957600080fd5b6001019392505050565b6040805160609490941b6bffffffffffffffffffffffff1916602080860191909152600293840b60e890811b60348701529290930b90911b60378401528051808403601a018152603a90930181528251928201929092206000908152929052902090565b60608060008361ffff1611614287576040805162461bcd60e51b81526020600482015260016024820152604960f81b604482015290519081900360640190fd5b865167ffffffffffffffff8111801561429f57600080fd5b506040519080825280602002602001820160405280156142c9578160200160208202803683370190505b509150865167ffffffffffffffff811180156142e457600080fd5b5060405190808252806020026020018201604052801561430e578160200160208202803683370190505b50905060005b87518110156143945761433f8a8a8a848151811061432e57fe5b60200260200101518a8a8a8a613389565b84838151811061434b57fe5b6020026020010184848151811061435e57fe5b60200260200101826001600160a01b03166001600160a01b03168152508260060b60060b81525050508080600101915050614314565b5097509795505050505050565b8060020b8260020b126143e1576040805162461bcd60e51b8152602060048201526003602482015262544c5560e81b604482015290519081900360640190fd5b620d89e719600283900b1215614424576040805162461bcd60e51b8152602060048201526003602482015262544c4d60e81b604482015290519081900360640190fd5b620d89e8600282900b1315614466576040805162461bcd60e51b815260206004820152600360248201526254554d60e81b604482015290519081900360640190fd5b5050565b6040805160808101825263ffffffff9283168082526000602083018190529282019290925260016060909101819052835463ffffffff1916909117909116600160f81b17909155908190565b60020b600881901d9161010090910790565b60008082116144d657600080fd5b600160801b82106144e957608091821c91015b68010000000000000000821061450157604091821c91015b640100000000821061451557602091821c91015b62010000821061452757601091821c91015b610100821061453857600891821c91015b6010821061454857600491821c91015b6004821061455857600291821c91015b60028210612beb57600101919050565b600080821161457657600080fd5b5060ff6001600160801b0382161561459157607f1901614599565b608082901c91505b67ffffffffffffffff8216156145b257603f19016145ba565b604082901c91505b63ffffffff8216156145cf57601f19016145d7565b602082901c91505b61ffff8216156145ea57600f19016145f2565b601082901c91505b60ff821615614604576007190161460c565b600882901c91505b600f82161561461e5760031901614626565b600482901c91505b60038216156146385760011901614640565b600282901c91505b6001821615612beb5760001901919050565b6000836001600160a01b0316856001600160a01b03161115614672579293925b8161469f5761469a836001600160801b03168686036001600160a01b0316600160601b6132d9565b6146c2565b6146c2836001600160801b03168686036001600160a01b0316600160601b6141a9565b90505b949350505050565b6000836001600160a01b0316856001600160a01b031611156146ed579293925b7bffffffffffffffffffffffffffffffff000000000000000000000000606084901b166001600160a01b03868603811690871661472957600080fd5b8361475957866001600160a01b031661474c8383896001600160a01b03166132d9565b8161475357fe5b0461477f565b61477f6147708383896001600160a01b03166141a9565b886001600160a01b0316614cf7565b979650505050505050565b600080856001600160a01b0316116147a157600080fd5b6000846001600160801b0316116147b757600080fd5b816147c95761469a8585856001614d02565b6146c28585856001614de3565b600080856001600160a01b0316116147ed57600080fd5b6000846001600160801b03161161480357600080fd5b816148155761469a8585856000614de3565b6146c28585856000614d02565b61482a61564a565b600085600001518503905060405180608001604052808663ffffffff1681526020018263ffffffff168660020b0288602001510160060b81526020016000856001600160801b03161161487e576001614880565b845b6001600160801b031673ffffffff00000000000000000000000000000000608085901b16816148ab57fe5b048860400151016001600160a01b0316815260200160011515815250915050949350505050565b6148da61564a565b6148e261564a565b888561ffff1661ffff81106148f357fe5b60408051608081018252919092015463ffffffff81168083526401000000008204600690810b810b900b6020840152600160581b82046001600160a01b031693830193909352600160f81b900460ff1615156060820152925061495890899089614ed8565b15614990578663ffffffff16826000015163ffffffff16141561497a57613510565b8161498783898988614822565b91509150613510565b888361ffff168660010161ffff16816149a557fe5b0661ffff1661ffff81106149b557fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b90910416151560608201819052909250614a6c57604080516080810182528a5463ffffffff811682526401000000008104600690810b810b900b6020830152600160581b81046001600160a01b031692820192909252600160f81b90910460ff161515606082015291505b614a7b88836000015189614ed8565b614ab2576040805162461bcd60e51b815260206004820152600360248201526213d31160ea1b604482015290519081900360640190fd5b614abf8989898887614f9b565b9150915097509795505050505050565b6000614ade60078787876141e3565b60015460025491925090600080600f87900b15614c24576000614aff612c27565b6000805460045492935090918291614b499160089186918591600160a01b810460020b9161ffff600160b81b83048116926001600160801b0390921691600160c81b900416613389565b9092509050614b8360058d8b8d8b8b87898b60007f000000000000000000000000000000000000000000000000000000000000000061513b565b9450614bba60058c8b8d8b8b87898b60017f000000000000000000000000000000000000000000000000000000000000000061513b565b93508415614bee57614bee60068d7f0000000000000000000000000000000000000000000000000000000000000000615325565b8315614c2057614c2060068c7f0000000000000000000000000000000000000000000000000000000000000000615325565b5050505b600080614c3660058c8c8b8a8a61538b565b9092509050614c47878a8484615437565b600089600f0b1215614c75578315614c6457614c6460058c6155cc565b8215614c7557614c7560058b6155cc565b50505050505095945050505050565b60008082600f0b12614caa57614ca5614ca085858560016146cd565b613291565b6146c5565b614cbd614ca085858560000360006146cd565b600003949350505050565b60008082600f0b12614ce457614ca5614ca08585856001614652565b614cbd614ca08585856000036000614652565b808204910615150190565b60008115614d755760006001600160a01b03841115614d3857614d3384600160601b876001600160801b03166132d9565b614d50565b6001600160801b038516606085901b81614d4e57fe5b045b9050614d6d614d686001600160a01b03881683613e0d565b6155f8565b9150506146c5565b60006001600160a01b03841115614da357614d9e84600160601b876001600160801b03166141a9565b614dba565b614dba606085901b6001600160801b038716614cf7565b905080866001600160a01b031611614dd157600080fd5b6001600160a01b0386160390506146c5565b600082614df15750836146c5565b7bffffffffffffffffffffffffffffffff000000000000000000000000606085901b168215614e91576001600160a01b03861684810290858281614e3157fe5b041415614e6257818101828110614e6057614e5683896001600160a01b0316836141a9565b93505050506146c5565b505b614e8882614e83878a6001600160a01b03168681614e7c57fe5b0490613e0d565b614cf7565b925050506146c5565b6001600160a01b03861684810290858281614ea857fe5b04148015614eb557508082115b614ebe57600080fd5b808203614e56614d68846001600160a01b038b16846141a9565b60008363ffffffff168363ffffffff1611158015614f0257508363ffffffff168263ffffffff1611155b15614f1e578163ffffffff168363ffffffff1611159050613382565b60008463ffffffff168463ffffffff1611614f46578363ffffffff1664010000000001614f4e565b8363ffffffff165b64ffffffffff16905060008563ffffffff168463ffffffff1611614f7f578363ffffffff1664010000000001614f87565b8363ffffffff165b64ffffffffff169091111595945050505050565b614fa361564a565b614fab61564a565b60008361ffff168560010161ffff1681614fc157fe5b0661ffff169050600060018561ffff16830103905060005b506002818301048961ffff87168281614fee57fe5b0661ffff8110614ffa57fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b9091041615156060820181905290955061506557806001019250614fd9565b898661ffff16826001018161507657fe5b0661ffff811061508257fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b909104161515606082015285519094506000906150ed908b908b614ed8565b905080801561510657506151068a8a8760000151614ed8565b15615111575061512e565b8061512157600182039250615128565b8160010193505b50614fd9565b5050509550959350505050565b60028a810b900b600090815260208c90526040812080546001600160801b031682615166828d6135ef565b9050846001600160801b0316816001600160801b031611156151b4576040805162461bcd60e51b81526020600482015260026024820152614c4f60f01b604482015290519081900360640190fd5b6001600160801b03828116159082161581141594501561528a578c60020b8e60020b1361525a57600183018b9055600283018a90556003830180547fffffffffff0000000000000000000000000000000000000000ffffffffffffff166701000000000000006001600160a01b038c16021766ffffffffffffff191666ffffffffffffff60068b900b161763ffffffff60d81b1916600160d81b63ffffffff8a16021790555b6003830180547effffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff16600160f81b1790555b82546001600160801b0319166001600160801b038216178355856152d35782546152ce906152c990600160801b9004600f90810b810b908f900b6132c3565b613f58565b6152f4565b82546152f4906152c990600160801b9004600f90810b810b908f900b6132a7565b8354600f9190910b6001600160801b03908116600160801b0291161790925550909c9b505050505050505050505050565b8060020b8260020b8161533457fe5b0760020b1561534257600080fd5b60008061535d8360020b8560020b8161535757fe5b056144b6565b600191820b820b60009081526020979097526040909620805460ff9097169190911b90951890945550505050565b600285810b80820b60009081526020899052604080822088850b850b83529082209193849391929184918291908a900b126153d1575050600182015460028301546153e4565b8360010154880391508360020154870390505b6000808b60020b8b60020b121561540657505060018301546002840154615419565b84600101548a0391508460020154890390505b92909803979097039b96909503949094039850939650505050505050565b6040805160a08101825285546001600160801b0390811682526001870154602083015260028701549282019290925260038601548083166060830152600160801b900490911660808201526000600f85900b6154d65781516001600160801b03166154ce576040805162461bcd60e51b815260206004820152600260248201526104e560f41b604482015290519081900360640190fd5b5080516154e5565b81516154e290866135ef565b90505b60006155098360200151860384600001516001600160801b0316600160801b6132d9565b9050600061552f8460400151860385600001516001600160801b0316600160801b6132d9565b905086600f0b6000146155565787546001600160801b0319166001600160801b0384161788555b60018801869055600288018590556001600160801b03821615158061558457506000816001600160801b0316115b156155c2576003880180546001600160801b031981166001600160801b039182168501821617808216600160801b9182900483168501909216021790555b5050505050505050565b600290810b810b6000908152602092909252604082208281556001810183905590810182905560030155565b806001600160a01b0381168114612beb57600080fd5b6040805160e081018252600080825260208201819052918101829052606081018290526080810182905260a0810182905260c081019190915290565b6040805160808101825260008082526020820181905291810182905260608101919091529056fea164736f6c6343000706000a"
        );
```
[8](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L8) | [11](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L11) | [14](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L14) | [17](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L17) | [20](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L20) | [25](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L25)
</details>

### [N-56] Layout Order Does Not Comply with `Solidity Style Guide`

Adhering to a recommended order in Solidity contracts enhances code readability and maintenance.
[More information in Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#order-of-layout)
It's recommended to use the following order:
1. Type declarations
2. State variables
3. Events
4. Errors
5. Modifiers
6. Functions

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit `type` declared after `event`
117: struct PoolAddressAndLock {
        IUniswapV3Pool pool;
        bool locked;
    }
/// @audit `constructor` declared after `function`
342: constructor(IUniswapV3Factory _factory) {
```
[117](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L117) | [342](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L342)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit `state variable` declared after `error`
62: mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;
```
[62](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L62)
</details>

### [N-57] Control Structures Not Complying with Best Practices

Following best practices for control structures in solidity code is vital for readability and maintainability. The control structures in contracts, libraries, functions, and structs should adhere to the following standards:

- Braces denoting the body should open on the same line as the declaration and close on their own line at the same indentation level as the beginning of the declaration. 
- A single space should precede the opening brace. 
- Control structures such as 'if', 'else', 'while', and 'for' should also follow these spacing and brace placement recommendations.

It is advised to revisit the [control structures](https://docs.soliditylang.org/en/latest/style-guide.html#control-structures) sections in documentation to ensure conformity with these best practices, fostering cleaner and more maintainable code.

<details>
<summary><i>42 issue instances in 8 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit `Space between condition and closing brace.`
417: if (amount0Owed > 0)
            SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token0,
                decoded.payer,
                msg.sender,
                amount0Owed
            );
/// @audit `Space between condition and closing brace.`
424: if (amount1Owed > 0)
            SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token1,
                decoded.payer,
                msg.sender,
                amount1Owed
            );
/// @audit `Space between condition and closing brace.`
1050: if (currentLiquidity.rightSlot() > 0) {
            _totalCollected = _collectAndWritePositionData(
                _liquidityChunk,
                _univ3pool,
                currentLiquidity,
                positionKey,
                _moved,
                isLong
            );
/// @audit `Return or revert statement should be on new line.`
323: if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();
/// @audit `Return or revert statement should be on new line.`
356: if (address(univ3pool) == address(0)) revert Errors.UniswapPoolNotInitialized();
/// @audit `Return or revert statement should be on new line.`
363: if (s_AddrToPoolIdData[univ3pool] != 0) return;
/// @audit `Return or revert statement should be on new line.`
614: if (
                (s_accountLiquidity[positionKey_to] != 0) ||
                (s_accountFeesBase[positionKey_to] != 0)
            ) revert Errors.TransferFailed();
/// @audit `Return or revert statement should be on new line.`
621: if (fromLiq.rightSlot() != liquidityChunk.liquidity()) revert Errors.TransferFailed();
/// @audit `Return or revert statement should be on new line.`
671: if (positionSize == 0) revert Errors.OptionsBalanceZero();
/// @audit `Return or revert statement should be on new line.`
683: if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();
/// @audit `Return or revert statement should be on new line.`
712: if ((newTick >= tickLimitHigh) || (newTick <= tickLimitLow)) revert Errors.PriceBoundFail();
/// @audit `Return or revert statement should be on new line.`
820: if (swapAmount == 0) return int256(0);
```
[417](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L417) | [424](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L424) | [1050](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1050) | [323](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L323) | [356](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L356) | [363](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L363) | [614](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L614) | [621](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L621) | [671](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L671) | [683](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L683) | [712](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L712) | [820](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L820)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit `Space between opening brace and condition.`
111: if (
                ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=
/// @audit `Space between opening brace and condition.`
164: if (
                ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
/// @audit `Space between opening brace and condition.`
223: if (
                ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
/// @audit `Space between condition and closing brace.`
109: if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=
                ERC1155Holder.onERC1155Received.selector
            ) {
/// @audit `Space between condition and closing brace.`
162: if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
                ERC1155Holder.onERC1155BatchReceived.selector
            ) {
/// @audit `Space between condition and closing brace.`
221: if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
                ERC1155Holder.onERC1155Received.selector
            ) {
/// @audit `Return or revert statement should be on new line.`
97: if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
/// @audit `Return or revert statement should be on new line.`
135: if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
```
[111](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L111) | [164](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L164) | [223](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L223) | [109](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L109) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L162) | [221](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L221) | [97](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L97) | [135](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L135)

```solidity
File: contracts/types/LeftRight.sol

/// @audit `Return or revert statement should be on new line.`
55: if (right < 0) revert Errors.LeftRightInputError();
/// @audit `Return or revert statement should be on new line.`
151: if (z < x || (uint128(z) < uint128(x))) revert Errors.UnderOverFlow();
/// @audit `Return or revert statement should be on new line.`
166: if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
/// @audit `Return or revert statement should be on new line.`
184: if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
/// @audit `Return or revert statement should be on new line.`
199: if (!((selfAsInt128 = int128(self)) == self)) revert Errors.CastingError();
/// @audit `Return or revert statement should be on new line.`
206: if (!((selfAsUint128 = uint128(self)) == self)) revert Errors.CastingError();
/// @audit `Return or revert statement should be on new line.`
213: if (self > uint256(type(int256).max)) revert Errors.CastingError();
```
[55](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L55) | [151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L151) | [166](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L166) | [184](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L184) | [199](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L199) | [206](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L206) | [213](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L213)

```solidity
File: contracts/types/TokenId.sol

/// @audit `Space between opening brace and condition.`
396: if (
                legLowerTick % tickSpacing != 0 ||
/// @audit `Space between condition and closing brace.`
396: if (
                legLowerTick % tickSpacing != 0 ||
                legUpperTick % tickSpacing != 0 ||
                legLowerTick < minTick ||
                legUpperTick > maxTick
            ) revert Errors.TicksNotInitializable();
/// @audit `Return or revert statement should be on new line.`
396: if (
                legLowerTick % tickSpacing != 0 ||
                legUpperTick % tickSpacing != 0 ||
                legLowerTick < minTick ||
                legUpperTick > maxTick
            ) revert Errors.TicksNotInitializable();
/// @audit `Return or revert statement should be on new line.`
464: if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);
/// @audit `Return or revert statement should be on new line.`
473: if ((self >> (64 + 48 * i)) != 0) revert Errors.InvalidTokenIdParameter(1);
/// @audit `Return or revert statement should be on new line.`
480: if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);
/// @audit `Return or revert statement should be on new line.`
482: if (
                    (self.strike(i) == Constants.MIN_V3POOL_TICK) ||
                    (self.strike(i) == Constants.MAX_V3POOL_TICK)
                ) revert Errors.InvalidTokenIdParameter(4);
/// @audit `Return or revert statement should be on new line.`
497: if (
                        (self.asset(riskPartnerIndex) != self.asset(i)) ||
                        (self.optionRatio(riskPartnerIndex) != self.optionRatio(i))
                    ) revert Errors.InvalidTokenIdParameter(3);
```
[396](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L396) | [396](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L396) | [396](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L396) | [464](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L464) | [473](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L473) | [480](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L480) | [482](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L482) | [497](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L497)

```solidity
File: contracts/libraries/CallbackLib.sol

/// @audit `Space between opening brace and condition.`
35: if (
            address(
/// @audit `Space between condition and closing brace.`
35: if (
            address(
                uint160(
                    uint256(
                        keccak256(
                            abi.encodePacked(
                                bytes1(0xff),
                                factory,
                                keccak256(abi.encode(features)),
                                Constants.V3POOL_INIT_CODE_HASH
                            )
/// @audit `Return or revert statement should be on new line.`
35: if (
            address(
                uint160(
                    uint256(
                        keccak256(
                            abi.encodePacked(
                                bytes1(0xff),
                                factory,
                                keccak256(abi.encode(features)),
                                Constants.V3POOL_INIT_CODE_HASH
                            )
                        )
                    )
                )
            ) != sender
        ) revert Errors.InvalidUniswapCallback();
```
[35](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L35) | [35](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L35) | [35](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L35)

```solidity
File: contracts/libraries/Math.sol

/// @audit `Return or revert statement should be on new line.`
41: if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();
/// @audit `Return or revert statement should be on new line.`
173: if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();
```
[41](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L41) | [173](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L173)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit `Space between condition and closing brace.`
120: if (tokenId.asset(legIndex) == 0) {
            legLiquidity = Math.getLiquidityForAmount0(
                uint256(0).addTickLower(tickLower).addTickUpper(tickUpper),
                amount
            );
```
[120](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L120)

```solidity
File: contracts/libraries/SafeTransferLib.sol

/// @audit `Return or revert statement should be on new line.`
38: }

        if (!success) revert Errors.TransferFailed();
```
[38](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L38)
</details>

### [N-58] Consider bounding input array length

The functions in question operate on arrays without established boundaries, executing function calls for each of their entries.
If these arrays become excessively long, a function might revert due to gas constraints.
To enhance user experience, consider incorporating a `require()` statement that enforces a sensible maximum array length.
This approach can avoid unnecessary computational work and ensure smoother transactions.

<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit `ids` is a function array parameter and `ids.length` is not bounded
550: for (uint256 i = 0; i < ids.length; ) {
```
[550](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L550)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit `ids` is a function array parameter and `ids.length` is not bounded
141: for (uint256 i = 0; i < ids.length; ) {
/// @audit `owners` is a function array parameter and `owners.length` is not bounded
187: for (uint256 i = 0; i < owners.length; ++i) {
```
[141](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L141) | [187](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L187)

```solidity
File: contracts/multicall/Multicall.sol

/// @audit `data` is a function array parameter and `data.length` is not bounded
14: for (uint256 i = 0; i < data.length; ) {
```
[14](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L14)
</details>

### [N-59] Constants in comparisons should appear on the left side

Placing constants on the left side of comparison statements can help prevent accidental assignments and improve code readability.
In languages like C, placing constants on the left can protect against unintended assignments that would be treated as true conditions, leading to bugs.
Although Solidity does not have this specific issue, using the same practice can still be beneficial for code readability and consistency.

Consider placing constants on the left side of comparison operators like `==`, `!=`, `<`, `>`, `<=`, and `>=`."

<details>
<summary><i>71 issue instances in 7 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

363: if (s_AddrToPoolIdData[univ3pool] != 0) return;
417: if (amount0Owed > 0)
424: if (amount1Owed > 0)
614: if (
                (s_accountLiquidity[positionKey_to] != 0) ||
616: (s_accountFeesBase[positionKey_to] != 0)
671: if (positionSize == 0) revert Errors.OptionsBalanceZero();
706: if ((itmAmounts != 0) && (swapAtMint)) {
774: if ((itm0 != 0) && (itm1 != 0)) {
774: if ((itm0 != 0) && (itm1 != 0)) {
810: } else if (itm0 != 0) {
820: if (swapAmount == 0) return int256(0);
971: if (isLong == 0) {
1014: Selling(isLong=0): Mint chunk of liquidity in Uniswap (defined by upper tick, lower tick, and amount)
1023: Buying(isLong=1): Burn in Uniswap
1038: if (_tokenType == 1) {
1043: if (_tokenType == 0) {
1213: if (isLong == 1) {
1217: if (amountToCollect != 0) {
1394: if (netLiquidity != 0) {
```
[363](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L363) | [417](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L417) | [424](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L424) | [614](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L614) | [616](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L616) | [671](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L671) | [706](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L706) | [774](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L774) | [774](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L774) | [810](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L810) | [820](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L820) | [971](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L971) | [1014](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1014) | [1023](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1023) | [1038](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1038) | [1043](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1043) | [1213](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1213) | [1217](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1217) | [1394](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1394)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

110: if (to.code.length != 0) {
163: if (to.code.length != 0) {
222: if (to.code.length != 0) {
```
[110](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L110) | [163](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L163) | [222](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L222)

```solidity
File: contracts/types/LeftRight.sol

55: if (right < 0) revert Errors.LeftRightInputError();
90: return uint128(self >> 128);
97: return int128(self >> 128);
```
[55](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L55) | [90](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L90) | [97](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L97)

```solidity
File: contracts/types/LiquidityChunk.sol

114: return int24(int256(self >> 232));
123: return int24(int256(self >> 208));
```
[114](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L114) | [123](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L123)

```solidity
File: contracts/types/TokenId.sol

163: } // "% 4096" = take last (2 ** 12 = 4096) 12 bits
337: if (optionRatios < 2 ** 64) {
339: } else if (optionRatios < 2 ** 112) {
341: } else if (optionRatios < 2 ** 160) {
343: } else if (optionRatios < 2 ** 208) {
396: if (
                legLowerTick % tickSpacing != 0 ||
                legUpperTick % tickSpacing != 0 ||
                legLowerTick < minTick ||
                legUpperTick > maxTick
            ) revert Errors.TicksNotInitializable();
417: if (optionRatios < 2 ** 64) {
419: } else if (optionRatios < 2 ** 112) {
421: } else if (optionRatios < 2 ** 160) {
423: } else if (optionRatios < 2 ** 208) {
443: if (i == 0)
445: if (i == 1)
447: if (i == 2)
449: if (i == 3)
```
[163](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L163) | [337](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L337) | [339](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L339) | [341](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L341) | [343](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L343) | [396](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L396) | [417](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L417) | [419](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L419) | [421](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L421) | [423](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L423) | [443](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L443) | [445](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L445) | [447](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L447) | [449](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L449)

```solidity
File: contracts/libraries/Math.sol

47: if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;
49: if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;
51: if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;
53: if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;
55: if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;
57: if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;
59: if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;
61: if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;
63: if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;
65: if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;
67: if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;
69: if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;
71: if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;
73: if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;
75: if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;
77: if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;
79: if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;
81: if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;
83: if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;
86: if (tick > 0) sqrtR = type(uint256).max / sqrtR;
89: sqrtPriceX96 = uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));
89: sqrtPriceX96 = uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));
206: if (prod1 == 0) {
207: require(denominator > 0);
302: if (prod1 == 0) {
364: if (prod1 == 0) {
426: if (prod1 == 0) {
488: if (prod1 == 0) {
```
[47](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L47) | [49](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L49) | [51](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L51) | [53](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L53) | [55](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L55) | [57](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L57) | [59](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L59) | [61](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L61) | [63](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L63) | [65](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L65) | [67](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L67) | [69](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L69) | [71](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L71) | [73](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L73) | [75](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L75) | [77](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L77) | [79](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L79) | [81](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L81) | [83](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L83) | [86](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L86) | [89](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L89) | [89](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L89) | [206](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L206) | [207](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L207) | [302](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L302) | [364](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L364) | [426](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L426) | [488](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L488)

```solidity
File: contracts/libraries/PanopticMath.sol

149: if (sqrtPriceX96 < 340275971719517849884101479065584693834) {
172: if (sqrtPriceX96 < 340275971719517849884101479065584693834) {
```
[149](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L149) | [172](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L172)
</details>

### [N-60] Large Numeric Literals Lack Underscores

Large numeric literals are often hard to read and prone to mistakes.
To improve readability and reduce the likelihood of errors, it is recommended to separate the digits of large numeric literals using underscores.
For example, instead of '1000000', use '1_000_000'.

<details>
<summary><i>8 issue instances in 3 files:</i></summary>

```solidity
File: contracts/types/TokenId.sol

162: return int24(int256((self >> (64 + legIndex * 48 + 36)) % 4096));
283: return self + (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36));
```
[162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L162) | [283](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L283)

```solidity
File: contracts/libraries/Constants.sol

11: int24 internal constant MIN_V3POOL_TICK = -887272;
14: int24 internal constant MAX_V3POOL_TICK = 887272;
17: uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;
21: 1461446703485210103287273052203988822378723970342;
```
[11](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L11) | [14](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L14) | [17](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L17) | [21](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L21)

```solidity
File: contracts/libraries/PanopticMath.sol

149: if (sqrtPriceX96 < 340275971719517849884101479065584693834) {
172: if (sqrtPriceX96 < 340275971719517849884101479065584693834) {
```
[149](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L149) | [172](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L172)
</details>

### [N-61] Replace `constant` with `immutable` for calculated values

Using `constant` with expressions like `keccak256()` or any calculations can be misleading. 

In Solidity, the `constant` modifier should be reserved for values that are truly constant and hardcoded into the contract. For values that are calculated or derived during the contract's creation, consider using the `immutable` modifier instead.

Shifting to `immutable` in such instances provides better clarity about the nature of the value, indicating that it's set once during contract initialization and remains unchanged afterward.

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: contracts/libraries/Constants.sol

11: int24 internal constant MIN_V3POOL_TICK = -887272;
25: bytes32 internal constant V3POOL_INIT_CODE_HASH =
        keccak256(
            hex"6101606040523480156200001257600080fd5b503060601b60805260408051630890357360e41b81529051600091339163890357309160048082019260a092909190829003018186803b1580156200005657600080fd5b505afa1580156200006b573d6000803e3d6000fd5b505050506040513d60a08110156200008257600080fd5b508051602080830151604084015160608086015160809096015160e896871b6001600160e81b0319166101005291811b6001600160601b031990811660e05292811b831660c0529390931b1660a052600282810b900b90921b610120529150620000f79082906200010f811b62002b8417901c565b60801b6001600160801b03191661014052506200017d565b60008082600281900b620d89e719816200012557fe5b05029050600083600281900b620d89e8816200013d57fe5b0502905060008460020b83830360020b816200015557fe5b0560010190508062ffffff166001600160801b038016816200017357fe5b0495945050505050565b60805160601c60a05160601c60c05160601c60e05160601c6101005160e81c6101205160e81c6101405160801c61567e6200024a60003980611fee5280614b5f5280614b96525080610c0052806128fd5280614bca5280614bfc525080610cef52806119cb5280611a0252806129455250806111c75280611a855280611ef4528061244452806129215280613e6b5250806108d252806112f55280611a545280611e8e52806123be5280613d2252508061207b528061227d52806128d9525080612bfb525061567e6000f3fe608060405234801561001057600080fd5b50600436106101ae5760003560e01c806370cf754a116100ee578063c45a015511610097578063ddca3f4311610071578063ddca3f4314610800578063f305839914610820578063f30dba9314610828578063f637731d146108aa576101ae565b8063c45a0155146107d1578063d0c93a7c146107d9578063d21220a7146107f8576101ae565b8063883bdbfd116100c8578063883bdbfd14610633578063a34123a71461073c578063a38807f214610776576101ae565b806370cf754a146105c65780638206a4d1146105ce57806385b66729146105f6576101ae565b80633850c7bd1161015b578063490e6cbc11610135578063490e6cbc146104705780634f1eb3d8146104fc578063514ea4bf1461054d5780635339c296146105a6576101ae565b80633850c7bd1461035b5780633c8a7d8d146103b45780634614131914610456576101ae565b80631ad8b03b1161018c5780631ad8b03b146102aa578063252c09d7146102e157806332148f6714610338576101ae565b80630dfe1681146101b3578063128acb08146101d75780631a68650214610286575b600080fd5b6101bb6108d0565b604080516001600160a01b039092168252519081900360200190f35b61026d600480360360a08110156101ed57600080fd5b6001600160a01b0382358116926020810135151592604082013592606083013516919081019060a08101608082013564010000000081111561022e57600080fd5b82018360208201111561024057600080fd5b8035906020019184600183028401116401000000008311171561026257600080fd5b5090925090506108f4565b6040805192835260208301919091528051918290030190f35b61028e6114ad565b604080516001600160801b039092168252519081900360200190f35b6102b26114bc565b60405180836001600160801b03168152602001826001600160801b031681526020019250505060405180910390f35b6102fe600480360360208110156102f757600080fd5b50356114d6565b6040805163ffffffff909516855260069390930b60208501526001600160a01b039091168383015215156060830152519081900360800190f35b6103596004803603602081101561034e57600080fd5b503561ffff1661151c565b005b610363611616565b604080516001600160a01b03909816885260029690960b602088015261ffff9485168787015292841660608701529216608085015260ff90911660a0840152151560c0830152519081900360e00190f35b61026d600480360360a08110156103ca57600080fd5b6001600160a01b03823516916020810135600290810b92604083013590910b916001600160801b036060820135169181019060a08101608082013564010000000081111561041757600080fd5b82018360208201111561042957600080fd5b8035906020019184600183028401116401000000008311171561044b57600080fd5b509092509050611666565b61045e611922565b60408051918252519081900360200190f35b6103596004803603608081101561048657600080fd5b6001600160a01b0382351691602081013591604082013591908101906080810160608201356401000000008111156104bd57600080fd5b8201836020820111156104cf57600080fd5b803590602001918460018302840111640100000000831117156104f157600080fd5b509092509050611928565b6102b2600480360360a081101561051257600080fd5b506001600160a01b03813516906020810135600290810b91604081013590910b906001600160801b0360608201358116916080013516611d83565b61056a6004803603602081101561056357600080fd5b5035611f9d565b604080516001600160801b0396871681526020810195909552848101939093529084166060840152909216608082015290519081900360a00190f35b61045e600480360360208110156105bc57600080fd5b503560010b611fda565b61028e611fec565b610359600480360360408110156105e457600080fd5b5060ff81358116916020013516612010565b6102b26004803603606081101561060c57600080fd5b506001600160a01b03813516906001600160801b036020820135811691604001351661220f565b6106a36004803603602081101561064957600080fd5b81019060208101813564010000000081111561066457600080fd5b82018360208201111561067657600080fd5b8035906020019184602083028401116401000000008311171561069857600080fd5b5090925090506124dc565b604051808060200180602001838103835285818151815260200191508051906020019060200280838360005b838110156106e75781810151838201526020016106cf565b50505050905001838103825284818151815260200191508051906020019060200280838360005b8381101561072657818101518382015260200161070e565b5050505090500194505050505060405180910390f35b61026d6004803603606081101561075257600080fd5b508035600290810b91602081013590910b90604001356001600160801b0316612569565b6107a06004803603604081101561078c57600080fd5b508035600290810b9160200135900b6126e0565b6040805160069490940b84526001600160a01b03909216602084015263ffffffff1682820152519081900360600190f35b6101bb6128d7565b6107e16128fb565b6040805160029290920b8252519081900360200190f35b6101bb61291f565b610808612943565b6040805162ffffff9092168252519081900360200190f35b61045e612967565b6108486004803603602081101561083e57600080fd5b503560020b61296d565b604080516001600160801b039099168952600f9790970b602089015287870195909552606087019390935260069190910b60808601526001600160a01b031660a085015263ffffffff1660c0840152151560e083015251908190036101000190f35b610359600480360360208110156108c057600080fd5b50356001600160a01b03166129db565b7f000000000000000000000000000000000000000000000000000000000000000081565b6000806108ff612bf0565b85610936576040805162461bcd60e51b8152602060048201526002602482015261415360f01b604482015290519081900360640190fd5b6040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b900b602083015261ffff600160b81b8204811693830193909352600160c81b810483166060830152600160d81b8104909216608082015260ff600160e81b8304811660a0830152600160f01b909204909116151560c082018190526109ef576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b87610a3a5780600001516001600160a01b0316866001600160a01b0316118015610a35575073fffd8963efd1fc6a506488495d951d5263988d266001600160a01b038716105b610a6c565b80600001516001600160a01b0316866001600160a01b0316108015610a6c57506401000276a36001600160a01b038716115b610aa3576040805162461bcd60e51b815260206004820152600360248201526214d41360ea1b604482015290519081900360640190fd5b6000805460ff60f01b191681556040805160c08101909152808a610ad25760048460a0015160ff16901c610ae5565b60108460a0015160ff1681610ae357fe5b065b60ff1681526004546001600160801b03166020820152604001610b06612c27565b63ffffffff168152602001600060060b815260200160006001600160a01b031681526020016000151581525090506000808913905060006040518060e001604052808b81526020016000815260200185600001516001600160a01b03168152602001856020015160020b81526020018c610b8257600254610b86565b6001545b815260200160006001600160801b0316815260200184602001516001600160801b031681525090505b805115801590610bd55750886001600160a01b031681604001516001600160a01b031614155b15610f9f57610be261560e565b60408201516001600160a01b031681526060820151610c25906006907f00000000000000000000000000000000000000000000000000000000000000008f612c2b565b15156040830152600290810b810b60208301819052620d89e719910b1215610c5657620d89e7196020820152610c75565b6020810151620d89e860029190910b1315610c7557620d89e860208201525b610c828160200151612d6d565b6001600160a01b031660608201526040820151610d13908d610cbc578b6001600160a01b031683606001516001600160a01b031611610cd6565b8b6001600160a01b031683606001516001600160a01b0316105b610ce4578260600151610ce6565b8b5b60c085015185517f000000000000000000000000000000000000000000000000000000000000000061309f565b60c085015260a084015260808301526001600160a01b031660408301528215610d7557610d498160c00151826080015101613291565b825103825260a0810151610d6b90610d6090613291565b6020840151906132a7565b6020830152610db0565b610d828160a00151613291565b825101825260c08101516080820151610daa91610d9f9101613291565b6020840151906132c3565b60208301525b835160ff1615610df6576000846000015160ff168260c0015181610dd057fe5b60c0840180519290910491829003905260a0840180519091016001600160801b03169052505b60c08201516001600160801b031615610e3557610e298160c00151600160801b8460c001516001600160801b03166132d9565b60808301805190910190525b80606001516001600160a01b031682604001516001600160a01b03161415610f5e57806040015115610f35578360a00151610ebf57610e9d846040015160008760200151886040015188602001518a606001516008613389909695949392919063ffffffff16565b6001600160a01b03166080860152600690810b900b6060850152600160a08501525b6000610f0b82602001518e610ed657600154610edc565b84608001515b8f610eeb578560800151610eef565b6002545b608089015160608a015160408b0151600595949392919061351c565b90508c15610f17576000035b610f258360c00151826135ef565b6001600160801b031660c0840152505b8b610f44578060200151610f4d565b60018160200151035b600290810b900b6060830152610f99565b80600001516001600160a01b031682604001516001600160a01b031614610f9957610f8c82604001516136a5565b600290810b900b60608301525b50610baf565b836020015160020b816060015160020b1461107a57600080610fed86604001518660400151886020015188602001518a606001518b6080015160086139d1909695949392919063ffffffff16565b604085015160608601516000805461ffff60c81b1916600160c81b61ffff958616021761ffff60b81b1916600160b81b95909416949094029290921762ffffff60a01b1916600160a01b62ffffff60029490940b93909316929092029190911773ffffffffffffffffffffffffffffffffffffffff19166001600160a01b03909116179055506110ac9050565b60408101516000805473ffffffffffffffffffffffffffffffffffffffff19166001600160a01b039092169190911790555b8060c001516001600160801b031683602001516001600160801b0316146110f25760c0810151600480546001600160801b0319166001600160801b039092169190911790555b8a1561114257608081015160015560a08101516001600160801b03161561113d5760a0810151600380546001600160801b031981166001600160801b03918216909301169190911790555b611188565b608081015160025560a08101516001600160801b0316156111885760a0810151600380546001600160801b03808216600160801b92839004821690940116029190911790555b8115158b1515146111a157602081015181518b036111ae565b80600001518a0381602001515b90965094508a156112e75760008512156111f0576111f07f00000000000000000000000000000000000000000000000000000000000000008d87600003613b86565b60006111fa613cd4565b9050336001600160a01b031663fa461e3388888c8c6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b15801561127e57600080fd5b505af1158015611292573d6000803e3d6000fd5b5050505061129e613cd4565b6112a88289613e0d565b11156112e1576040805162461bcd60e51b815260206004820152600360248201526249494160e81b604482015290519081900360640190fd5b50611411565b600086121561131e5761131e7f00000000000000000000000000000000000000000000000000000000000000008d88600003613b86565b6000611328613e1d565b9050336001600160a01b031663fa461e3388888c8c6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b1580156113ac57600080fd5b505af11580156113c0573d6000803e3d6000fd5b505050506113cc613e1d565b6113d68288613e0d565b111561140f576040805162461bcd60e51b815260206004820152600360248201526249494160e81b604482015290519081900360640190fd5b505b60408082015160c083015160608085015184518b8152602081018b90526001600160a01b03948516818701526001600160801b039093169183019190915260020b60808201529151908e169133917fc42079f94a6350d7e6235f29174924f928cc2ac818eb64fed8004e115fbcca679181900360a00190a350506000805460ff60f01b1916600160f01b17905550919890975095505050505050565b6004546001600160801b031681565b6003546001600160801b0380821691600160801b90041682565b60088161ffff81106114e757600080fd5b015463ffffffff81169150640100000000810460060b90600160581b81046001600160a01b031690600160f81b900460ff1684565b600054600160f01b900460ff16611560576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19169055611575612bf0565b60008054600160d81b900461ffff169061159160088385613eb5565b6000805461ffff808416600160d81b810261ffff60d81b19909316929092179092559192508316146115fe576040805161ffff80851682528316602082015281517fac49e518f90a358f652e4400164f05a5d8f7e35e7747279bc3a93dbf584e125a929181900390910190a15b50506000805460ff60f01b1916600160f01b17905550565b6000546001600160a01b03811690600160a01b810460020b9061ffff600160b81b8204811691600160c81b8104821691600160d81b8204169060ff600160e81b8204811691600160f01b90041687565b600080548190600160f01b900460ff166116ad576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b191690556001600160801b0385166116cd57600080fd5b60008061171b60405180608001604052808c6001600160a01b031681526020018b60020b81526020018a60020b81526020016117118a6001600160801b0316613f58565b600f0b9052613f69565b9250925050819350809250600080600086111561173d5761173a613cd4565b91505b841561174e5761174b613e1d565b90505b336001600160a01b031663d348799787878b8b6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b1580156117d057600080fd5b505af11580156117e4573d6000803e3d6000fd5b50505050600086111561183b576117f9613cd4565b6118038388613e0d565b111561183b576040805162461bcd60e51b815260206004820152600260248201526104d360f41b604482015290519081900360640190fd5b841561188b57611849613e1d565b6118538287613e0d565b111561188b576040805162461bcd60e51b81526020600482015260026024820152614d3160f01b604482015290519081900360640190fd5b8960020b8b60020b8d6001600160a01b03167f7a53080ba414158be7ec69b987b5fb7d07dee101fe85488f0853ae16239d0bde338d8b8b60405180856001600160a01b03168152602001846001600160801b0316815260200183815260200182815260200194505050505060405180910390a450506000805460ff60f01b1916600160f01b17905550919890975095505050505050565b60025481565b600054600160f01b900460ff1661196c576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19169055611981612bf0565b6004546001600160801b0316806119c3576040805162461bcd60e51b81526020600482015260016024820152601360fa1b604482015290519081900360640190fd5b60006119f8867f000000000000000000000000000000000000000000000000000000000000000062ffffff16620f42406141a9565b90506000611a2f867f000000000000000000000000000000000000000000000000000000000000000062ffffff16620f42406141a9565b90506000611a3b613cd4565b90506000611a47613e1d565b90508815611a7a57611a7a7f00000000000000000000000000000000000000000000000000000000000000008b8b613b86565b8715611aab57611aab7f00000000000000000000000000000000000000000000000000000000000000008b8a613b86565b336001600160a01b031663e9cbafb085858a8a6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b158015611b2d57600080fd5b505af1158015611b41573d6000803e3d6000fd5b505050506000611b4f613cd4565b90506000611b5b613e1d565b905081611b688588613e0d565b1115611ba0576040805162461bcd60e51b8152602060048201526002602482015261046360f41b604482015290519081900360640190fd5b80611bab8487613e0d565b1115611be3576040805162461bcd60e51b8152602060048201526002602482015261463160f01b604482015290519081900360640190fd5b8382038382038115611c725760008054600160e81b9004600f16908115611c16578160ff168481611c1057fe5b04611c19565b60005b90506001600160801b03811615611c4c57600380546001600160801b038082168401166001600160801b03199091161790555b611c66818503600160801b8d6001600160801b03166132d9565b60018054909101905550505b8015611cfd5760008054600160e81b900460041c600f16908115611ca2578160ff168381611c9c57fe5b04611ca5565b60005b90506001600160801b03811615611cd757600380546001600160801b03600160801b8083048216850182160291161790555b611cf1818403600160801b8d6001600160801b03166132d9565b60028054909101905550505b8d6001600160a01b0316336001600160a01b03167fbdbdb71d7860376ba52b25a5028beea23581364a40522f6bcfb86bb1f2dca6338f8f86866040518085815260200184815260200183815260200182815260200194505050505060405180910390a350506000805460ff60f01b1916600160f01b179055505050505050505050505050565b600080548190600160f01b900460ff16611dca576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19168155611de460073389896141e3565b60038101549091506001600160801b0390811690861611611e055784611e14565b60038101546001600160801b03165b60038201549093506001600160801b03600160801b909104811690851611611e3c5783611e52565b6003810154600160801b90046001600160801b03165b91506001600160801b03831615611eb7576003810180546001600160801b031981166001600160801b03918216869003821617909155611eb7907f0000000000000000000000000000000000000000000000000000000000000000908a908616613b86565b6001600160801b03821615611f1d576003810180546001600160801b03600160801b808304821686900382160291811691909117909155611f1d907f0000000000000000000000000000000000000000000000000000000000000000908a908516613b86565b604080516001600160a01b038a1681526001600160801b0380861660208301528416818301529051600288810b92908a900b9133917f70935338e69775456a85ddef226c395fb668b63fa0115f5f20610b388e6ca9c0919081900360600190a4506000805460ff60f01b1916600160f01b17905590969095509350505050565b60076020526000908152604090208054600182015460028301546003909301546001600160801b0392831693919281811691600160801b90041685565b60066020526000908152604090205481565b7f000000000000000000000000000000000000000000000000000000000000000081565b600054600160f01b900460ff16612054576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916905560408051638da5cb5b60e01b815290516001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001691638da5cb5b916004808301926020929190829003018186803b1580156120c157600080fd5b505afa1580156120d5573d6000803e3d6000fd5b505050506040513d60208110156120eb57600080fd5b50516001600160a01b0316331461210157600080fd5b60ff82161580612124575060048260ff16101580156121245750600a8260ff1611155b801561214e575060ff8116158061214e575060048160ff161015801561214e5750600a8160ff1611155b61215757600080fd5b60008054610ff0600484901b16840160ff908116600160e81b9081027fffff00ffffffffffffffffffffffffffffffffffffffffffffffffffffffffff841617909355919004167f973d8d92bb299f4af6ce49b52a8adb85ae46b9f214c4c4fc06ac77401237b1336010826040805160ff9390920683168252600f600486901c16602083015286831682820152918516606082015290519081900360800190a150506000805460ff60f01b1916600160f01b17905550565b600080548190600160f01b900460ff16612256576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916905560408051638da5cb5b60e01b815290516001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001691638da5cb5b916004808301926020929190829003018186803b1580156122c357600080fd5b505afa1580156122d7573d6000803e3d6000fd5b505050506040513d60208110156122ed57600080fd5b50516001600160a01b0316331461230357600080fd5b6003546001600160801b039081169085161161231f578361232c565b6003546001600160801b03165b6003549092506001600160801b03600160801b9091048116908416116123525782612366565b600354600160801b90046001600160801b03165b90506001600160801b038216156123e7576003546001600160801b038381169116141561239557600019909101905b600380546001600160801b031981166001600160801b039182168590038216179091556123e7907f00000000000000000000000000000000000000000000000000000000000000009087908516613b86565b6001600160801b0381161561246d576003546001600160801b03828116600160801b90920416141561241857600019015b600380546001600160801b03600160801b80830482168590038216029181169190911790915561246d907f00000000000000000000000000000000000000000000000000000000000000009087908416613b86565b604080516001600160801b0380851682528316602082015281516001600160a01b0388169233927f596b573906218d3411850b26a6b437d6c4522fdb43d2d2386263f86d50b8b151929081900390910190a36000805460ff60f01b1916600160f01b1790559094909350915050565b6060806124e7612bf0565b61255e6124f2612c27565b858580806020026020016040519081016040528093929190818152602001838360200280828437600092018290525054600454600896959450600160a01b820460020b935061ffff600160b81b8304811693506001600160801b0390911691600160c81b900416614247565b915091509250929050565b600080548190600160f01b900460ff166125b0576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916815560408051608081018252338152600288810b602083015287900b918101919091528190819061260990606081016125fc6001600160801b038a16613f58565b600003600f0b9052613f69565b925092509250816000039450806000039350600085118061262a5750600084115b15612669576003830180546001600160801b038082168089018216600160801b93849004831689019092169092029091176001600160801b0319161790555b604080516001600160801b0388168152602081018790528082018690529051600289810b92908b900b9133917f0c396cd989a39f4459b5fa1aed6a9a8dcdbc45908acfd67e028cd568da98982c919081900360600190a450506000805460ff60f01b1916600160f01b179055509094909350915050565b60008060006126ed612bf0565b6126f785856143a1565b600285810b810b60009081526005602052604080822087840b90930b825281206003830154600681900b9367010000000000000082046001600160a01b0316928492600160d81b810463ffffffff169284929091600160f81b900460ff168061275f57600080fd5b6003820154600681900b985067010000000000000081046001600160a01b03169650600160d81b810463ffffffff169450600160f81b900460ff16806127a457600080fd5b50506040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b810b6020840181905261ffff600160b81b8404811695850195909552600160c81b830485166060850152600160d81b8304909416608084015260ff600160e81b8304811660a0850152600160f01b909204909116151560c08301529093508e810b91900b1215905061284d575093909403965090039350900390506128d0565b8a60020b816020015160020b12156128c1576000612869612c27565b602083015160408401516004546060860151939450600093849361289f936008938893879392916001600160801b031690613389565b9a9003989098039b5050949096039290920396509091030392506128d0915050565b50949093039650039350900390505b9250925092565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b60015481565b60056020526000908152604090208054600182015460028301546003909301546001600160801b03831693600160801b909304600f0b9290600681900b9067010000000000000081046001600160a01b031690600160d81b810463ffffffff1690600160f81b900460ff1688565b6000546001600160a01b031615612a1e576040805162461bcd60e51b8152602060048201526002602482015261414960f01b604482015290519081900360640190fd5b6000612a29826136a5565b9050600080612a41612a39612c27565b60089061446a565b6040805160e0810182526001600160a01b038816808252600288810b6020808501829052600085870181905261ffff898116606088018190529089166080880181905260a08801839052600160c0909801979097528154600160f01b73ffffffffffffffffffffffffffffffffffffffff19909116871762ffffff60a01b1916600160a01b62ffffff9787900b9790971696909602959095177fffffffffff00000000ffffffffffffffffffffffffffffffffffffffffffffff16600160c81b9091021761ffff60d81b1916600160d81b909602959095177fff0000ffffffffffffffffffffffffffffffffffffffffffffffffffffffffff1692909217909355835191825281019190915281519395509193507f98636036cb66a9c19a37435efc1e90142190214e8abeb821bdba3f2990dd4c9592918290030190a150505050565b60008082600281900b620d89e71981612b9957fe5b05029050600083600281900b620d89e881612bb057fe5b0502905060008460020b83830360020b81612bc757fe5b0560010190508062ffffff166001600160801b03801681612be457fe5b0493505050505b919050565b306001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001614612c2557600080fd5b565b4290565b60008060008460020b8660020b81612c3f57fe5b05905060008660020b128015612c6657508460020b8660020b81612c5f57fe5b0760020b15155b15612c7057600019015b8315612ce557600080612c82836144b6565b600182810b810b600090815260208d9052604090205460ff83169190911b80016000190190811680151597509294509092509085612cc757888360ff16860302612cda565b88612cd1826144c8565b840360ff168603025b965050505050612d63565b600080612cf4836001016144b6565b91509150600060018260ff166001901b031990506000818b60008660010b60010b8152602001908152602001600020541690508060001415955085612d4657888360ff0360ff16866001010102612d5c565b8883612d5183614568565b0360ff168660010101025b9650505050505b5094509492505050565b60008060008360020b12612d84578260020b612d8c565b8260020b6000035b9050620d89e8811115612dca576040805162461bcd60e51b81526020600482015260016024820152601560fa1b604482015290519081900360640190fd5b600060018216612dde57600160801b612df0565b6ffffcb933bd6fad37aa2d162d1a5940015b70ffffffffffffffffffffffffffffffffff1690506002821615612e24576ffff97272373d413259a46990580e213a0260801c5b6004821615612e43576ffff2e50f5f656932ef12357cf3c7fdcc0260801c5b6008821615612e62576fffe5caca7e10e4e61c3624eaa0941cd00260801c5b6010821615612e81576fffcb9843d60f6159c9db58835c9266440260801c5b6020821615612ea0576fff973b41fa98c081472e6896dfb254c00260801c5b6040821615612ebf576fff2ea16466c96a3843ec78b326b528610260801c5b6080821615612ede576ffe5dee046a99a2a811c461f1969c30530260801c5b610100821615612efe576ffcbe86c7900a88aedcffc83b479aa3a40260801c5b610200821615612f1e576ff987a7253ac413176f2b074cf7815e540260801c5b610400821615612f3e576ff3392b0822b70005940c7a398e4b70f30260801c5b610800821615612f5e576fe7159475a2c29b7443b29c7fa6e889d90260801c5b611000821615612f7e576fd097f3bdfd2022b8845ad8f792aa58250260801c5b612000821615612f9e576fa9f746462d870fdf8a65dc1f90e061e50260801c5b614000821615612fbe576f70d869a156d2a1b890bb3df62baf32f70260801c5b618000821615612fde576f31be135f97d08fd981231505542fcfa60260801c5b62010000821615612fff576f09aa508b5b7a84e1c677de54f3e99bc90260801c5b6202000082161561301f576e5d6af8dedb81196699c329225ee6040260801c5b6204000082161561303e576d2216e584f5fa1ea926041bedfe980260801c5b6208000082161561305b576b048a170391f7dc42444e8fa20260801c5b60008460020b131561307657806000198161307257fe5b0490505b64010000000081061561308a57600161308d565b60005b60ff16602082901c0192505050919050565b60008080806001600160a01b03808916908a1610158187128015906131245760006130d88989620f42400362ffffff16620f42406132d9565b9050826130f1576130ec8c8c8c6001614652565b6130fe565b6130fe8b8d8c60016146cd565b955085811061310f578a965061311e565b61311b8c8b838661478a565b96505b5061316e565b8161313b576131368b8b8b60006146cd565b613148565b6131488a8c8b6000614652565b935083886000031061315c5789955061316e565b61316b8b8a8a600003856147d6565b95505b6001600160a01b038a81169087161482156131d15780801561318d5750815b6131a35761319e878d8c60016146cd565b6131a5565b855b95508080156131b2575081155b6131c8576131c3878d8c6000614652565b6131ca565b845b945061321b565b8080156131db5750815b6131f1576131ec8c888c6001614652565b6131f3565b855b9550808015613200575081155b613216576132118c888c60006146cd565b613218565b845b94505b8115801561322b57508860000385115b15613237578860000394505b81801561325657508a6001600160a01b0316876001600160a01b031614155b15613265578589039350613282565b61327f868962ffffff168a620f42400362ffffff166141a9565b93505b50505095509550955095915050565b6000600160ff1b82106132a357600080fd5b5090565b808203828113156000831215146132bd57600080fd5b92915050565b818101828112156000831215146132bd57600080fd5b600080806000198587098686029250828110908390030390508061330f576000841161330457600080fd5b508290049050613382565b80841161331b57600080fd5b6000848688096000868103871696879004966002600389028118808a02820302808a02820302808a02820302808a02820302808a02820302808a02909103029181900381900460010186841190950394909402919094039290920491909117919091029150505b9392505050565b60008063ffffffff8716613430576000898661ffff1661ffff81106133aa57fe5b60408051608081018252919092015463ffffffff8082168084526401000000008304600690810b810b900b6020850152600160581b83046001600160a01b031694840194909452600160f81b90910460ff16151560608301529092508a161461341c57613419818a8988614822565b90505b806020015181604001519250925050613510565b8688036000806134458c8c858c8c8c8c6148d2565b91509150816000015163ffffffff168363ffffffff161415613477578160200151826040015194509450505050613510565b805163ffffffff8481169116141561349f578060200151816040015194509450505050613510565b8151815160208085015190840151918390039286039163ffffffff80841692908516910360060b816134cd57fe5b05028460200151018263ffffffff168263ffffffff1686604001518660400151036001600160a01b031602816134ff57fe5b048560400151019650965050505050505b97509795505050505050565b600295860b860b60009081526020979097526040909620600181018054909503909455938301805490920390915560038201805463ffffffff600160d81b6001600160a01b036701000000000000008085048216909603169094027fffffffffff0000000000000000000000000000000000000000ffffffffffffff90921691909117600681810b90960390950b66ffffffffffffff1666ffffffffffffff199095169490941782810485169095039093160263ffffffff60d81b1990931692909217905554600160801b9004600f0b90565b60008082600f0b121561365457826001600160801b03168260000384039150816001600160801b03161061364f576040805162461bcd60e51b81526020600482015260026024820152614c5360f01b604482015290519081900360640190fd5b6132bd565b826001600160801b03168284019150816001600160801b031610156132bd576040805162461bcd60e51b81526020600482015260026024820152614c4160f01b604482015290519081900360640190fd5b60006401000276a36001600160a01b038316108015906136e1575073fffd8963efd1fc6a506488495d951d5263988d266001600160a01b038316105b613716576040805162461bcd60e51b81526020600482015260016024820152602960f91b604482015290519081900360640190fd5b77ffffffffffffffffffffffffffffffffffffffff00000000602083901b166001600160801b03811160071b81811c67ffffffffffffffff811160061b90811c63ffffffff811160051b90811c61ffff811160041b90811c60ff8111600390811b91821c600f811160021b90811c918211600190811b92831c979088119617909417909217179091171717608081106137b757607f810383901c91506137c1565b80607f0383901b91505b908002607f81811c60ff83811c9190911c800280831c81831c1c800280841c81841c1c800280851c81851c1c800280861c81861c1c800280871c81871c1c800280881c81881c1c800280891c81891c1c8002808a1c818a1c1c8002808b1c818b1c1c8002808c1c818c1c1c8002808d1c818d1c1c8002808e1c9c81901c9c909c1c80029c8d901c9e9d607f198f0160401b60c09190911c678000000000000000161760c19b909b1c674000000000000000169a909a1760c29990991c672000000000000000169890981760c39790971c671000000000000000169690961760c49590951c670800000000000000169490941760c59390931c670400000000000000169290921760c69190911c670200000000000000161760c79190911c670100000000000000161760c89190911c6680000000000000161760c99190911c6640000000000000161760ca9190911c6620000000000000161760cb9190911c6610000000000000161760cc9190911c6608000000000000161760cd9190911c66040000000000001617693627a301d71055774c8581026f028f6481ab7f045a5af012a19d003aa9198101608090811d906fdb2df09e81959a81455e260799a0632f8301901d600281810b9083900b146139c257886001600160a01b03166139a682612d6d565b6001600160a01b031611156139bb57816139bd565b805b6139c4565b815b9998505050505050505050565b6000806000898961ffff1661ffff81106139e757fe5b60408051608081018252919092015463ffffffff8082168084526401000000008304600690810b810b900b6020850152600160581b83046001600160a01b031694840194909452600160f81b90910460ff161515606083015290925089161415613a575788859250925050613510565b8461ffff168461ffff16118015613a7857506001850361ffff168961ffff16145b15613a8557839150613a89565b8491505b8161ffff168960010161ffff1681613a9d57fe5b069250613aac81898989614822565b8a8461ffff1661ffff8110613abd57fe5b825191018054602084015160408501516060909501511515600160f81b027effffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff6001600160a01b03909616600160581b027fff0000000000000000000000000000000000000000ffffffffffffffffffffff60069390930b66ffffffffffffff16640100000000026affffffffffffff000000001963ffffffff90971663ffffffff199095169490941795909516929092171692909217929092161790555097509795505050505050565b604080516001600160a01b038481166024830152604480830185905283518084039091018152606490920183526020820180516001600160e01b031663a9059cbb60e01b1781529251825160009485949389169392918291908083835b60208310613c025780518252601f199092019160209182019101613be3565b6001836020036101000a0380198251168184511680821785525050505050509050019150506000604051808303816000865af19150503d8060008114613c64576040519150601f19603f3d011682016040523d82523d6000602084013e613c69565b606091505b5091509150818015613c97575080511580613c975750808060200190516020811015613c9457600080fd5b50515b613ccd576040805162461bcd60e51b81526020600482015260026024820152612a2360f11b604482015290519081900360640190fd5b5050505050565b604080513060248083019190915282518083039091018152604490910182526020810180516001600160e01b03166370a0823160e01b17815291518151600093849384936001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001693919290918291908083835b60208310613d6d5780518252601f199092019160209182019101613d4e565b6001836020036101000a038019825116818451168082178552505050505050905001915050600060405180830381855afa9150503d8060008114613dcd576040519150601f19603f3d011682016040523d82523d6000602084013e613dd2565b606091505b5091509150818015613de657506020815110155b613def57600080fd5b808060200190516020811015613e0457600080fd5b50519250505090565b808201828110156132bd57600080fd5b604080513060248083019190915282518083039091018152604490910182526020810180516001600160e01b03166370a0823160e01b17815291518151600093849384936001600160a01b037f000000000000000000000000000000000000000000000000000000000000000016939192909182919080838360208310613d6d5780518252601f199092019160209182019101613d4e565b6000808361ffff1611613ef3576040805162461bcd60e51b81526020600482015260016024820152604960f81b604482015290519081900360640190fd5b8261ffff168261ffff1611613f09575081613382565b825b8261ffff168161ffff161015613f4f576001858261ffff1661ffff8110613f2e57fe5b01805463ffffffff191663ffffffff92909216919091179055600101613f0b565b50909392505050565b80600f81900b8114612beb57600080fd5b6000806000613f76612bf0565b613f88846020015185604001516143a1565b6040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b900b602080840182905261ffff600160b81b8404811685870152600160c81b84048116606080870191909152600160d81b8504909116608086015260ff600160e81b8504811660a0870152600160f01b909404909316151560c08501528851908901519489015192890151939461402c9491939092909190614acf565b93508460600151600f0b6000146141a157846020015160020b816020015160020b12156140815761407a6140638660200151612d6d565b6140708760400151612d6d565b8760600151614c84565b92506141a1565b846040015160020b816020015160020b12156141775760045460408201516001600160801b03909116906140d3906140b7612c27565b60208501516060860151608087015160089493929187916139d1565b6000805461ffff60c81b1916600160c81b61ffff938416021761ffff60b81b1916600160b81b939092169290920217905581516040870151614123919061411990612d6d565b8860600151614c84565b93506141416141358760200151612d6d565b83516060890151614cc8565b92506141518187606001516135ef565b600480546001600160801b0319166001600160801b0392909216919091179055506141a1565b61419e6141878660200151612d6d565b6141948760400151612d6d565b8760600151614cc8565b91505b509193909250565b60006141b68484846132d9565b9050600082806141c257fe5b84860911156133825760001981106141d957600080fd5b6001019392505050565b6040805160609490941b6bffffffffffffffffffffffff1916602080860191909152600293840b60e890811b60348701529290930b90911b60378401528051808403601a018152603a90930181528251928201929092206000908152929052902090565b60608060008361ffff1611614287576040805162461bcd60e51b81526020600482015260016024820152604960f81b604482015290519081900360640190fd5b865167ffffffffffffffff8111801561429f57600080fd5b506040519080825280602002602001820160405280156142c9578160200160208202803683370190505b509150865167ffffffffffffffff811180156142e457600080fd5b5060405190808252806020026020018201604052801561430e578160200160208202803683370190505b50905060005b87518110156143945761433f8a8a8a848151811061432e57fe5b60200260200101518a8a8a8a613389565b84838151811061434b57fe5b6020026020010184848151811061435e57fe5b60200260200101826001600160a01b03166001600160a01b03168152508260060b60060b81525050508080600101915050614314565b5097509795505050505050565b8060020b8260020b126143e1576040805162461bcd60e51b8152602060048201526003602482015262544c5560e81b604482015290519081900360640190fd5b620d89e719600283900b1215614424576040805162461bcd60e51b8152602060048201526003602482015262544c4d60e81b604482015290519081900360640190fd5b620d89e8600282900b1315614466576040805162461bcd60e51b815260206004820152600360248201526254554d60e81b604482015290519081900360640190fd5b5050565b6040805160808101825263ffffffff9283168082526000602083018190529282019290925260016060909101819052835463ffffffff1916909117909116600160f81b17909155908190565b60020b600881901d9161010090910790565b60008082116144d657600080fd5b600160801b82106144e957608091821c91015b68010000000000000000821061450157604091821c91015b640100000000821061451557602091821c91015b62010000821061452757601091821c91015b610100821061453857600891821c91015b6010821061454857600491821c91015b6004821061455857600291821c91015b60028210612beb57600101919050565b600080821161457657600080fd5b5060ff6001600160801b0382161561459157607f1901614599565b608082901c91505b67ffffffffffffffff8216156145b257603f19016145ba565b604082901c91505b63ffffffff8216156145cf57601f19016145d7565b602082901c91505b61ffff8216156145ea57600f19016145f2565b601082901c91505b60ff821615614604576007190161460c565b600882901c91505b600f82161561461e5760031901614626565b600482901c91505b60038216156146385760011901614640565b600282901c91505b6001821615612beb5760001901919050565b6000836001600160a01b0316856001600160a01b03161115614672579293925b8161469f5761469a836001600160801b03168686036001600160a01b0316600160601b6132d9565b6146c2565b6146c2836001600160801b03168686036001600160a01b0316600160601b6141a9565b90505b949350505050565b6000836001600160a01b0316856001600160a01b031611156146ed579293925b7bffffffffffffffffffffffffffffffff000000000000000000000000606084901b166001600160a01b03868603811690871661472957600080fd5b8361475957866001600160a01b031661474c8383896001600160a01b03166132d9565b8161475357fe5b0461477f565b61477f6147708383896001600160a01b03166141a9565b886001600160a01b0316614cf7565b979650505050505050565b600080856001600160a01b0316116147a157600080fd5b6000846001600160801b0316116147b757600080fd5b816147c95761469a8585856001614d02565b6146c28585856001614de3565b600080856001600160a01b0316116147ed57600080fd5b6000846001600160801b03161161480357600080fd5b816148155761469a8585856000614de3565b6146c28585856000614d02565b61482a61564a565b600085600001518503905060405180608001604052808663ffffffff1681526020018263ffffffff168660020b0288602001510160060b81526020016000856001600160801b03161161487e576001614880565b845b6001600160801b031673ffffffff00000000000000000000000000000000608085901b16816148ab57fe5b048860400151016001600160a01b0316815260200160011515815250915050949350505050565b6148da61564a565b6148e261564a565b888561ffff1661ffff81106148f357fe5b60408051608081018252919092015463ffffffff81168083526401000000008204600690810b810b900b6020840152600160581b82046001600160a01b031693830193909352600160f81b900460ff1615156060820152925061495890899089614ed8565b15614990578663ffffffff16826000015163ffffffff16141561497a57613510565b8161498783898988614822565b91509150613510565b888361ffff168660010161ffff16816149a557fe5b0661ffff1661ffff81106149b557fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b90910416151560608201819052909250614a6c57604080516080810182528a5463ffffffff811682526401000000008104600690810b810b900b6020830152600160581b81046001600160a01b031692820192909252600160f81b90910460ff161515606082015291505b614a7b88836000015189614ed8565b614ab2576040805162461bcd60e51b815260206004820152600360248201526213d31160ea1b604482015290519081900360640190fd5b614abf8989898887614f9b565b9150915097509795505050505050565b6000614ade60078787876141e3565b60015460025491925090600080600f87900b15614c24576000614aff612c27565b6000805460045492935090918291614b499160089186918591600160a01b810460020b9161ffff600160b81b83048116926001600160801b0390921691600160c81b900416613389565b9092509050614b8360058d8b8d8b8b87898b60007f000000000000000000000000000000000000000000000000000000000000000061513b565b9450614bba60058c8b8d8b8b87898b60017f000000000000000000000000000000000000000000000000000000000000000061513b565b93508415614bee57614bee60068d7f0000000000000000000000000000000000000000000000000000000000000000615325565b8315614c2057614c2060068c7f0000000000000000000000000000000000000000000000000000000000000000615325565b5050505b600080614c3660058c8c8b8a8a61538b565b9092509050614c47878a8484615437565b600089600f0b1215614c75578315614c6457614c6460058c6155cc565b8215614c7557614c7560058b6155cc565b50505050505095945050505050565b60008082600f0b12614caa57614ca5614ca085858560016146cd565b613291565b6146c5565b614cbd614ca085858560000360006146cd565b600003949350505050565b60008082600f0b12614ce457614ca5614ca08585856001614652565b614cbd614ca08585856000036000614652565b808204910615150190565b60008115614d755760006001600160a01b03841115614d3857614d3384600160601b876001600160801b03166132d9565b614d50565b6001600160801b038516606085901b81614d4e57fe5b045b9050614d6d614d686001600160a01b03881683613e0d565b6155f8565b9150506146c5565b60006001600160a01b03841115614da357614d9e84600160601b876001600160801b03166141a9565b614dba565b614dba606085901b6001600160801b038716614cf7565b905080866001600160a01b031611614dd157600080fd5b6001600160a01b0386160390506146c5565b600082614df15750836146c5565b7bffffffffffffffffffffffffffffffff000000000000000000000000606085901b168215614e91576001600160a01b03861684810290858281614e3157fe5b041415614e6257818101828110614e6057614e5683896001600160a01b0316836141a9565b93505050506146c5565b505b614e8882614e83878a6001600160a01b03168681614e7c57fe5b0490613e0d565b614cf7565b925050506146c5565b6001600160a01b03861684810290858281614ea857fe5b04148015614eb557508082115b614ebe57600080fd5b808203614e56614d68846001600160a01b038b16846141a9565b60008363ffffffff168363ffffffff1611158015614f0257508363ffffffff168263ffffffff1611155b15614f1e578163ffffffff168363ffffffff1611159050613382565b60008463ffffffff168463ffffffff1611614f46578363ffffffff1664010000000001614f4e565b8363ffffffff165b64ffffffffff16905060008563ffffffff168463ffffffff1611614f7f578363ffffffff1664010000000001614f87565b8363ffffffff165b64ffffffffff169091111595945050505050565b614fa361564a565b614fab61564a565b60008361ffff168560010161ffff1681614fc157fe5b0661ffff169050600060018561ffff16830103905060005b506002818301048961ffff87168281614fee57fe5b0661ffff8110614ffa57fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b9091041615156060820181905290955061506557806001019250614fd9565b898661ffff16826001018161507657fe5b0661ffff811061508257fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b909104161515606082015285519094506000906150ed908b908b614ed8565b905080801561510657506151068a8a8760000151614ed8565b15615111575061512e565b8061512157600182039250615128565b8160010193505b50614fd9565b5050509550959350505050565b60028a810b900b600090815260208c90526040812080546001600160801b031682615166828d6135ef565b9050846001600160801b0316816001600160801b031611156151b4576040805162461bcd60e51b81526020600482015260026024820152614c4f60f01b604482015290519081900360640190fd5b6001600160801b03828116159082161581141594501561528a578c60020b8e60020b1361525a57600183018b9055600283018a90556003830180547fffffffffff0000000000000000000000000000000000000000ffffffffffffff166701000000000000006001600160a01b038c16021766ffffffffffffff191666ffffffffffffff60068b900b161763ffffffff60d81b1916600160d81b63ffffffff8a16021790555b6003830180547effffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff16600160f81b1790555b82546001600160801b0319166001600160801b038216178355856152d35782546152ce906152c990600160801b9004600f90810b810b908f900b6132c3565b613f58565b6152f4565b82546152f4906152c990600160801b9004600f90810b810b908f900b6132a7565b8354600f9190910b6001600160801b03908116600160801b0291161790925550909c9b505050505050505050505050565b8060020b8260020b8161533457fe5b0760020b1561534257600080fd5b60008061535d8360020b8560020b8161535757fe5b056144b6565b600191820b820b60009081526020979097526040909620805460ff9097169190911b90951890945550505050565b600285810b80820b60009081526020899052604080822088850b850b83529082209193849391929184918291908a900b126153d1575050600182015460028301546153e4565b8360010154880391508360020154870390505b6000808b60020b8b60020b121561540657505060018301546002840154615419565b84600101548a0391508460020154890390505b92909803979097039b96909503949094039850939650505050505050565b6040805160a08101825285546001600160801b0390811682526001870154602083015260028701549282019290925260038601548083166060830152600160801b900490911660808201526000600f85900b6154d65781516001600160801b03166154ce576040805162461bcd60e51b815260206004820152600260248201526104e560f41b604482015290519081900360640190fd5b5080516154e5565b81516154e290866135ef565b90505b60006155098360200151860384600001516001600160801b0316600160801b6132d9565b9050600061552f8460400151860385600001516001600160801b0316600160801b6132d9565b905086600f0b6000146155565787546001600160801b0319166001600160801b0384161788555b60018801869055600288018590556001600160801b03821615158061558457506000816001600160801b0316115b156155c2576003880180546001600160801b031981166001600160801b039182168501821617808216600160801b9182900483168501909216021790555b5050505050505050565b600290810b810b6000908152602092909252604082208281556001810183905590810182905560030155565b806001600160a01b0381168114612beb57600080fd5b6040805160e081018252600080825260208201819052918101829052606081018290526080810182905260a0810182905260c081019190915290565b6040805160808101825260008082526020820181905291810182905260608101919091529056fea164736f6c6343000706000a"
        );
```
[11](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L11) | [25](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L25)
</details>

### [N-62] Consider Refactoring Long Functions

Functions that span many lines can be hard to understand and maintain.
It is often beneficial to refactor long functions into multiple smaller functions.
This improves readability, makes testing easier, and can even lead to gas optimization if it eliminates the need for variables that would otherwise have to be stored in memory.

<details>
<summary><i>8 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

 /// @audit 42 lines (excluding comments)
578: function registerTokenTransfer(address from, address to, uint256 id, uint256 amount) internal {
 /// @audit 41 lines (excluding comments)
743: function swapInAMM(
        IUniswapV3Pool univ3pool,
        int256 itmAmounts
    ) internal returns (int256 totalSwapped) {
 /// @audit 43 lines (excluding comments)
848: function _createPositionInAMM(
        IUniswapV3Pool univ3pool,
        uint256 tokenId,
        uint128 positionSize,
        bool isBurn
    ) internal returns (int256 totalMoved, int256 totalCollected, int256 itmAmounts) {
 /// @audit 62 lines (excluding comments)
936: function _createLegInAMM(
        IUniswapV3Pool _univ3pool,
        uint256 _tokenId,
        uint256 _leg,
        uint256 _liquidityChunk,
        bool _isBurn
    ) internal returns (int256 _moved, int256 _itmAmounts, int256 _totalCollected) {
 /// @audit 52 lines (excluding comments)
1255: function _getPremiaDeltas(
        uint256 currentLiquidity,
        int256 collectedAmounts
    ) private pure returns (uint256 deltaPremiumOwed, uint256 deltaPremiumGross) {
 /// @audit 33 lines (excluding comments)
1371: function getAccountPremium(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper,
        int24 atTick,
        uint256 isLong
    ) external view returns (uint128 premiumToken0, uint128 premiumToken1) {
```
[578](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L578) | [743](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L743) | [848](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L848) | [936](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L936) | [1255](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255) | [1371](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1371)

```solidity
File: contracts/types/TokenId.sol

 /// @audit 32 lines (excluding comments)
463: function validate(uint256 self) internal pure returns (uint64) {
```
[463](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L463)

```solidity
File: contracts/libraries/Math.sol

 /// @audit 45 lines (excluding comments)
186: function mulDiv(
        uint256 a,
        uint256 b,
        uint256 denominator
    ) internal pure returns (uint256 result) {
```
[186](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L186)
</details>

### [N-63] `public` functions not called by the contract should be declared `external` instead

Contracts are allowed to override their parents' functions and change the visibility from `external` to `public`.
If a `public` function is not called internally within the contract, it should be declared as `external` to save gas.

<details>
<summary><i>3 issue instances in 3 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

178: function balanceOfBatch(
        address[] calldata owners,
        uint256[] calldata ids
    ) public view returns (uint256[] memory balances) {
```
[178](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L178)

```solidity
File: contracts/libraries/FeesCalc.sol

54: function calculateAMMSwapFeesLiquidityChunk(
        IUniswapV3Pool univ3pool,
        int24 currentTick,
        uint128 startingLiquidity,
        uint256 liquidityChunk
    ) public view returns (int256 feesEachToken) {
```
[54](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L54)

```solidity
File: contracts/multicall/Multicall.sol

12: function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
[12](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L12)
</details>

### [N-64] Complex casting

Complex casting in Solidity contracts can introduce both readability issues and potential for overflows. 
Whenever multiple casts are found, consider whether the complexity is necessary.
If so, it is strongly recommended to add inline comments to explain why these casts are needed and to assure that no overflows are introduced.

<details>
<summary><i>24 issue instances in 8 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

1120: .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))
1121: .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));
1159: movedAmounts = int256(0).toRightSlot(int128(int256(amount0))).toLeftSlot(
1160: int128(int256(amount1))
1186: movedAmounts = int256(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(
1187: -int128(int256(amount1))
```
[1120](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1120) | [1121](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1121) | [1159](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1159) | [1160](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1160) | [1186](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1186) | [1187](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1187)

```solidity
File: contracts/types/LeftRight.sol

57: return self + uint256(int256(right));
67: return self + int256(uint256(right));
120: return self + (int256(int128(left)) << 128);
```
[57](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L57) | [67](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L67) | [120](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L120)

```solidity
File: contracts/types/LiquidityChunk.sol

90: return self + (uint256(uint24(_tickLower)) << 232);
101: return self + ((uint256(uint24(_tickUpper))) << 208);
114: return int24(int256(self >> 232));
123: return int24(int256(self >> 208));
```
[90](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L90) | [101](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L101) | [114](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L114) | [123](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L123)

```solidity
File: contracts/types/TokenId.sol

151: return int24(int256(self >> (64 + legIndex * 48 + 12)));
162: return int24(int256((self >> (64 + legIndex * 48 + 36)) % 4096));
283: return self + (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36));
```
[151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L151) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L162) | [283](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L283)

```solidity
File: contracts/libraries/Errors.sol

10: /// @dev e.g. uint128(uint256(a)) fails
```
[10](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L10)

```solidity
File: contracts/libraries/FeesCalc.sol

76: .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, startingLiquidity))))
77: .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, startingLiquidity))));
```
[76](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L76) | [77](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L77)

```solidity
File: contracts/libraries/Math.sol

40: uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));
41: if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();
171: /// @return downcastedInt the downcasted uint (uint128 now)
```
[40](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L40) | [41](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L41) | [171](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L171)

```solidity
File: contracts/libraries/PanopticMath.sol

39: return uint64(uint160(univ3pool) >> 96);
57: (uint64(uint256(keccak256(abi.encodePacked(token0, token1, fee)))) >> 32);
```
[39](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L39) | [57](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L57)
</details>

### [N-65] Double Type Casting

Double type casting should be avoided in Solidity contracts to prevent unintended consequences and ensure accurate data representation.
Performing multiple type casts in succession can lead to unexpected truncation, rounding errors, or loss of precision, potentially compromising the contract's functionality and reliability.
Furthermore, double type casting can make the code less readable and harder to maintain, increasing the likelihood of errors and misunderstandings during development and debugging.
To ensure precise and consistent data handling, developers should use appropriate data types and avoid unnecessary or excessive type casting, promoting a more robust and dependable contract execution.

<details>
<summary><i>22 issue instances in 7 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

1120: .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))
1121: .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));
1159: movedAmounts = int256(0).toRightSlot(int128(int256(amount0))).toLeftSlot(
1160: int128(int256(amount1))
1186: movedAmounts = int256(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(
1187: -int128(int256(amount1))
```
[1120](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1120) | [1121](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1121) | [1159](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1159) | [1160](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1160) | [1186](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1186) | [1187](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1187)

```solidity
File: contracts/types/LeftRight.sol

57: return self + uint256(int256(right));
67: return self + int256(uint256(right));
120: return self + (int256(int128(left)) << 128);
```
[57](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L57) | [67](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L67) | [120](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L120)

```solidity
File: contracts/types/LiquidityChunk.sol

90: return self + (uint256(uint24(_tickLower)) << 232);
101: return self + ((uint256(uint24(_tickUpper))) << 208);
114: return int24(int256(self >> 232));
123: return int24(int256(self >> 208));
```
[90](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L90) | [101](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L101) | [114](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L114) | [123](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L123)

```solidity
File: contracts/types/TokenId.sol

151: return int24(int256(self >> (64 + legIndex * 48 + 12)));
162: return int24(int256((self >> (64 + legIndex * 48 + 36)) % 4096));
283: return self + (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36));
```
[151](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L151) | [162](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L162) | [283](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L283)

```solidity
File: contracts/libraries/FeesCalc.sol

76: .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, startingLiquidity))))
77: .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, startingLiquidity))));
```
[76](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L76) | [77](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L77)

```solidity
File: contracts/libraries/Math.sol

40: uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));
41: if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();
```
[40](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L40) | [41](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L41)

```solidity
File: contracts/libraries/PanopticMath.sol

39: return uint64(uint160(univ3pool) >> 96);
57: (uint64(uint256(keccak256(abi.encodePacked(token0, token1, fee)))) >> 32);
```
[39](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L39) | [57](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L57)
</details>

### [N-66] `else`-block not required

In Solidity, if an `if` block contains a `return` statement, subsequent `else` blocks become unnecessary.
This is because the `return` statement halts the execution of the function at that point, making any `else` conditions redundant.
Therefore, omitting `else` after such `if` blocks can lead to cleaner and more readable code without any change in the functionality.

<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

985: if (startingLiquidity < chunkLiquidity) {
                    // the amount we want to move (liquidityChunk.legLiquidity()) out of uniswap is greater than
                    // what the account that owns the liquidity in uniswap has (startingLiquidity)
                    // we must ensure that an account can only move its own liquidity out of uniswap
                    // so we revert in this case
                    revert Errors.NotEnoughLiquidity();
                } else {
                    // we want to move less than what already sits in uniswap, no problem:
                    updatedLiquidity = startingLiquidity - chunkLiquidity;
                }
```
[985](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L985)

```solidity
File: contracts/types/TokenId.sol

417: if (optionRatios < 2 ** 64) {
            return 0;
        } else if (optionRatios < 2 ** 112) {
            return 1;
        } else if (optionRatios < 2 ** 160) {
```
[417](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L417)

```solidity
File: contracts/libraries/PanopticMath.sol

149: if (sqrtPriceX96 < 340275971719517849884101479065584693834) {
                int256 absResult = Math
                    .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }
172: if (sqrtPriceX96 < 340275971719517849884101479065584693834) {
                int256 absResult = Math
                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv(
                        Math.absUint(amount),
                        2 ** 128,
                        Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
                    )
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }
```
[149](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L149) | [172](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L172)
</details>

### [N-67] Function Name Duplication is Discouraged for Security Audits

While function overriding allows for functions with the same name to coexist, it's advisable to avoid this practice for the sake of readability and maintainability. 

Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the chance of errors during development, testing, and debugging.
Using distinct and descriptive function names not only clarifies the purpose and behavior of each function but also helps prevent unintended function calls or incorrect overriding.

<details>
<summary><i>15 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

544: function afterTokenTransfer(
        address from,
        address to,
        uint256[] memory ids,
        uint256[] memory amounts
    ) internal override {
563: function afterTokenTransfer(
        address from,
        address to,
        uint256 id,
        uint256 amount
    ) internal override {
```
[544](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L544) | [563](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L563)

```solidity
File: contracts/types/LeftRight.sol

25: function rightSlot(uint256 self) internal pure returns (uint128) {
32: function rightSlot(int256 self) internal pure returns (int128) {
44: function toRightSlot(uint256 self, uint128 right) internal pure returns (uint256) {
54: function toRightSlot(uint256 self, int128 right) internal pure returns (uint256) {
65: function toRightSlot(int256 self, uint128 right) internal pure returns (int256) {
75: function toRightSlot(int256 self, int128 right) internal pure returns (int256) {
89: function leftSlot(uint256 self) internal pure returns (uint128) {
96: function leftSlot(int256 self) internal pure returns (int128) {
108: function toLeftSlot(uint256 self, uint128 left) internal pure returns (uint256) {
118: function toLeftSlot(int256 self, uint128 left) internal pure returns (int256) {
128: function toLeftSlot(int256 self, int128 left) internal pure returns (int256) {
142: function add(uint256 x, uint256 y) internal pure returns (uint256 z) {
159: function add(int256 x, int256 y) internal pure returns (int256 z) {
```
[25](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L25) | [32](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L32) | [44](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L44) | [54](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L54) | [65](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L65) | [75](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L75) | [89](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L89) | [96](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L96) | [108](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L108) | [118](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L118) | [128](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L128) | [142](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L142) | [159](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L159)
</details>

### [N-68] `Solidity Style Guide`: Function order not compliant

Ordering helps readers identify which functions they can call and to find the constructor and fallback definitions easier.
But there are contracts in the project that do not comply with this.
Functions should be grouped according to their visibility and ordered:
- constructor 
- receive function (if exists)
- fallback function (if exists)
- external
- public
- internal
- private.

<details>
<summary><i>6 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit `function` declared before `constructor`
331: function endReentrancyLock(uint64 poolId) internal {
342: constructor(IUniswapV3Factory _factory) {
/// @audit `private` function `_getFeesBase()` declared before `internal` function `_mintLiquidity()`
1093: function _getFeesBase(
        IUniswapV3Pool univ3pool,
        uint128 liquidity,
        uint256 liquidityChunk
    ) private view returns (int256 feesBase) {
1129: function _mintLiquidity(
        uint256 liquidityChunk,
        IUniswapV3Pool univ3pool
    ) internal returns (int256 movedAmounts) {
/// @audit `private` function `_getPremiaDeltas()` declared before `external` function `getAccountLiquidity()`
1255: function _getPremiaDeltas(
        uint256 currentLiquidity,
        int256 collectedAmounts
    ) private pure returns (uint256 deltaPremiumOwed, uint256 deltaPremiumGross) {
1343: function getAccountLiquidity(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper
    ) external view returns (uint256 accountLiquidities) {
```
[331](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L331) | [342](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L342) | [1093](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1093) | [1129](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1129) | [1255](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255) | [1343](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1343)
</details>

### [N-69] `Solidity Style Guide`: Lines are too long

It is generally recommended that lines in the source code should not exceed 80-120 characters.
Multiline output parameters and return statements should follow the same style recommended for wrapping long lines found in the Maximum Line Length section.

<details>
<summary><i>162 issue instances in 11 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

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
131: // Similar to vega in options because the liquidity utilization is somewhat reflective of the implied volatility (IV),
134: // The effect of vegoid on the long premium multiplier can be explored here: https://www.desmos.com/calculator/mdeqob2m04
175: /// @dev mapping that stores the liquidity data of keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))
176: // liquidityData is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user
177: // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller
178: // the reason why it is called "removedLiquidity" is because long options are created by removed liquidity -ie. short selling LP positions
292: /// @dev mapping that stores a LeftRight packing of feesBase of  keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))
293: /// @dev Base fees is stored as int128((feeGrowthInside0LastX128 * liquidity) / 2**128), which allows us to store the accumulated fees as int128 instead of uint256
295: /// feesBase represents the baseline fees collected by the position last time it was updated - this is recalculated every time the position is collected from with the new value
392: // we need this because enabling `memoryguard` and therefore StackLimitEvader increases the size of the contract significantly beyond the size limit
471: /// @param slippageTickLimitLow The lower price slippage limit when minting an ITM position (set to larger than slippageTickLimitHigh for swapping when minting)
472: /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)
473: /// @return totalCollected A LeftRight encoded word containing the total amount of token0 and token1 collected as fees
474: /// @return totalSwapped A LeftRight encoded word containing the total amount of token0 and token1 swapped if minting ITM
505: /// @param slippageTickLimitLow The lower price slippage limit when minting an ITM position (set to larger than slippageTickLimitHigh for swapping when minting)
506: /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)
507: /// @return totalCollected A LeftRight encoded word containing the total amount of token0 and token1 collected as fees
508: /// @return totalSwapped A LeftRight encoded word containing the total amount of token0 and token1 swapped if minting ITM
573: /// @dev token transfers are only allowed if you transfer your entire balance of a given tokenId and the recipient has none
584: // for this leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
641: /// @notice Helper that checks the proposed option position and size and forwards the minting and potential swapping tasks.
646: /// @notice and then forwards the minting/burning/swapping to another internal helper functions which perform the AMM pool actions.
705: // if the in-the-money amount is not zero (i.e. positions were minted ITM) and the user did provide tick limits LOW > HIGH, then swap necessary amounts
718: /// @notice When a position is minted or burnt in-the-money (ITM) we are *not* 100% token0 or 100% token1: we have a mix of both tokens.
719: /// @notice The swapping for ITM options is needed because only one of the tokens are "borrowed" by a user to create the position.
737: ///   If we take token0 as an example, we deploy it to the AMM pool and *then* swap to get the right mix of token0 and token1
739: ///   It that position is burnt, then we remove a mix of the two tokens and swap one of them so that the user receives only one.
771: // note: upstream users of this function such as the Panoptic Pool should ensure users always compensate for the ITM amount delta
772: // the netting swap is not perfectly accurate, and it is possible for swaps to run out of liquidity, so we do not want to rely on it
778: // note: negative ITM amounts denote a surplus of tokens (burning liquidity), while positive amounts denote a shortage of tokens (minting liquidity)
780: // we do this by flipping the signs on the token1 ITM amount converting+deducting it against the token0 ITM amount
875: // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,
880: // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
898: // increment accumulators of the upper bound on tokens contained across all legs of the position at any given tick
914: // Ensure upper bound on amount of tokens contained across all legs of the position on any given tick does not exceed a maximum of (2**127-1).
915: // This is the maximum value of the `int128` type we frequently use to hold token amounts, so a given position's size should be guaranteed to
964: // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user
965: // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller
966: // the reason why it is called "removedLiquidity" is because long options are created by removing -ie.short selling LP positions
973: // we're minting more liquidity in uniswap: so add the incoming liquidity chunk to the existing liquidity chunk
983: // so we seek to move the incoming liquidity chunk *out* of uniswap - but was there sufficient liquidity sitting in uniswap
1089: /// @notice Compute the feesGrowth * liquidity / 2**128 by reading feeGrowthInside0LastX128 and feeGrowthInside1LastX128 from univ3pool.positions.
1114: /// @dev here we're converting the value to an int128 even though all values (feeGrowth, liquidity, Q128) are strictly positive.
1115: /// That's because of the way feeGrowthInside works in Uniswap v3, where it can underflow when stored for the first time.
1116: /// This is not a problem in Uniswap v3 because the fees are always calculated by taking the difference of the feeGrowths,
1118: /// So by using int128 instead of uint128, we remove the need to handle extremely large underflows and simply allow it to be negative
1164: /// @notice Burn a chunk of liquidity (`liquidityChunk`) in the Uniswap v3 pool and send to msg.sender; return the amount moved.
1192: /// @notice Helper to collect amounts between msg.sender and Uniswap and also to update the Uniswap fees collected to date from the AMM.
1195: /// @param currentLiquidity the existing liquidity msg.sender owns in the AMM for this chunk before the SFPM was called
1199: /// @return collectedOut the incoming totalCollected with potentially whatever is collected in this function added to it
1219: // Collect only if there was existing startingLiquidity=liquidities.rightSlot() at that position: collect all fees
1253: /// @return deltaPremiumOwed The extra premium (per liquidity X64) to be added to the owed accumulator for token0 (right) and token1 (right)
1254: /// @return deltaPremiumGross The extra premium (per liquidity X64) to be added to the gross accumulator for token0 (right) and token1 (right)
1264: // explains how we get from the premium per liquidity (calculated here) to the total premia collected and the multiplier
1342: /// @return accountLiquidities The amount of liquidity that has been shorted/added to the Uniswap contract (removedLiquidity:netLiquidity -> rightSlot:leftSlot)
1351: /// @dev tokenType input here is the asset of the positions minted, this avoids put liquidity to be used for call, and vice-versa
1357: /// @notice Return the premium associated with a given position, where Premium is an accumulator of feeGrowth for the touched position.
1358: /// @dev Computes s_accountPremium{isLong ? Owed : Gross}[keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))]
1359: /// @dev if an atTick parameter is provided that is different from type(int24).max, then it will update the premium up to the current
1360: /// @dev block at the provided atTick value. We do this because this may be called immediately after the Uni v3 pool has been touched
1367: /// @param atTick The current tick. Set atTick < type(int24).max = 8388608 to get latest premium up to the current block
1369: /// @return premiumToken0 The amount of premium (per liquidity X64) for token0 = sum (feeGrowthLast0X128) over every block where the position has been touched
1370: /// @return premiumToken1 The amount of premium (per liquidity X64) for token1 = sum (feeGrowthLast0X128) over every block where the position has been touched
1389: // Compute the premium up to the current block (ie. after last touch until now). Do not proceed if atTick == type(int24).max = 8388608
1399: // how much fees have been accumulated within the liquidity chunk since last time we updated this chunk?
1401: // currentFeesGrowth (calculated from FeesCalc.calculateAMMSwapFeesLiquidityChunk) is (ammFeesCollectedPerLiquidity * liquidityChunk.liquidity())
1402: // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])
```
[24](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L24) | [25](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L25) | [26](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L26) | [27](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L27) | [28](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L28) | [29](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L29) | [30](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L30) | [31](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L31) | [32](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L32) | [33](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L33) | [34](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L34) | [35](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L35) | [36](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L36) | [37](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L37) | [38](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L38) | [39](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L39) | [40](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L40) | [41](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L41) | [42](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L42) | [43](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L43) | [44](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L44) | [45](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L45) | [46](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L46) | [47](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L47) | [48](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L48) | [49](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L49) | [50](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L50) | [51](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L51) | [52](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L52) | [53](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L53) | [54](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L54) | [55](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L55) | [56](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L56) | [57](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L57) | [58](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L58) | [59](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L59) | [60](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L60) | [61](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L61) | [62](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L62) | [63](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L63) | [64](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L64) | [65](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L65) | [131](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L131) | [134](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L134) | [175](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L175) | [176](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L176) | [177](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L177) | [178](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L178) | [292](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L292) | [293](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L293) | [295](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L295) | [392](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L392) | [471](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L471) | [472](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L472) | [473](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L473) | [474](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L474) | [505](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L505) | [506](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L506) | [507](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L507) | [508](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L508) | [573](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L573) | [584](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L584) | [641](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L641) | [646](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L646) | [705](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L705) | [718](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L718) | [719](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L719) | [737](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L737) | [739](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L739) | [771](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L771) | [772](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L772) | [778](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L778) | [780](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L780) | [875](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L875) | [880](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L880) | [898](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L898) | [914](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L914) | [915](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L915) | [964](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L964) | [965](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L965) | [966](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L966) | [973](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L973) | [983](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L983) | [1089](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1089) | [1114](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1114) | [1115](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1115) | [1116](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1116) | [1118](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1118) | [1164](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1164) | [1192](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1192) | [1195](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1195) | [1199](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1199) | [1219](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1219) | [1253](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1253) | [1254](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1254) | [1264](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1264) | [1342](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1342) | [1351](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1351) | [1357](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1357) | [1358](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1358) | [1359](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1359) | [1360](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1360) | [1367](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1367) | [1369](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1369) | [1370](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1370) | [1389](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1389) | [1399](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1399) | [1401](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1401) | [1402](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1402)

```solidity
File: contracts/types/LeftRight.sol

12: /// @notice higher-order bits are cut off. For example: uint32 a = 0x12345678; uint16 b = uint16(a); // b will be 0x5678 now
37: /// @dev Typically, the slot is already clear when writing to it, but if it is not, the bits will be added to the existing bits
101: /// @dev Typically, the slot is already clear when writing to it, but if it is not, the bits will be added to the existing bits
```
[12](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L12) | [37](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L37) | [101](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LeftRight.sol#L101)

```solidity
File: contracts/types/LiquidityChunk.sol

7: /// @title A Panoptic Liquidity Chunk. Tracks Tick Range and Liquidity Information for a "chunk." Used to track movement of chunks.
11: ///   A liquidity chunk is an amount of `liquidity` (an amount of WETH, e.g.) deployed between two ticks: `tickLower` and `tickUpper`
```
[7](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L7) | [11](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L11)

```solidity
File: contracts/types/TokenId.sol

13: /// @notice our terminology: "leg n" or "nth leg" (in {1,2,3,4}) corresponds to "leg index n-1" or `legIndex` (in {0,1,2,3})
21: /// (1) univ3pool        64bits     0bits      : first 8 bytes of the Uniswap v3 pool address (first 64 bits; little-endian), plus a pseudorandom number in the event of a collision
47: ///   - if a leg is active (e.g. leg 1) there can be no gaps in other legs meaning: if leg 1 is active then leg 3 cannot be active if leg 2 is inactive.
51: ///  We also refer to the legs via their index, so leg number 2 has leg index 1 (legIndex) (counting from zero), and in general leg number N has leg index N-1.
52: ///  - the underlying strike price of the 2nd leg (leg index = 1) in this option position starts at bit index  (64 + 12 + 48 * (leg index=1))=123
62: // This mask contains zero bits where the poolId is. It is used via & to strip the poolId section from a number, leaving the rest.
130: /// @notice that returning the riskPartner for any leg is 0 by default, this does not necessarily imply that token 1 (index 0)
131: /// @notice is the risk partner of that leg. We are assuming here that the position has been validated before this and that
132: /// @notice the risk partner of any leg always makes sense in this way. A leg btw. does not need to have a risk partner.
133: /// @notice the point here is that this function is very low level and must be used with utmost care because it comes down
155: /// @notice Get the width of the nth leg (index `legIndex`). This is half the tick-range covered by the leg (tickUpper - tickLower)/2.
272: /// @notice Add the width of the nth leg (index `legIndex`). This is half the tick-range covered by the leg (tickUpper - tickLower)/2.
330: // We copy the logic from the countLegs function, using it here adds 5K to the contract size with IR for some reason
336: // Since only the option ratios remain, we can be sure that no bits above the start of the inactive legs will be 1
351: // i.e the whole mask is used to flip all legs with 4 legs, but only the first leg is flipped with 1 leg so we shift by 3 legs
352: // We also clear the poolId area of the mask to ensure the bits that are shifted right into the area don't flip and cause issues
383: // The max/min ticks that can be initialized are the closest multiple of tickSpacing to the actual max/min tick abs()=887272
408: /// @dev ASSUMPTION: For any leg, the option ratio is always > 0 (the leg always has a number of contracts associated with it).
416: // Since only the option ratios remain, we can be sure that no bits above the start of the inactive legs will be 1
515: // if the two token long-types and the tokenTypes are both different (one is a short call, the other a long put, e.g.), this is a synthetic position
516: // A synthetic long or short is more capital efficient than each leg separated because the long+short premia accumulate proportionally
```
[13](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L13) | [21](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L21) | [47](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L47) | [51](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L51) | [52](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L52) | [62](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L62) | [130](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L130) | [131](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L131) | [132](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L132) | [133](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L133) | [155](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L155) | [272](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L272) | [330](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L330) | [336](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L336) | [351](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L351) | [352](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L352) | [383](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L383) | [408](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L408) | [416](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L416) | [515](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L515) | [516](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L516)

```solidity
File: contracts/libraries/Constants.sol

27: hex"6101606040523480156200001257600080fd5b503060601b60805260408051630890357360e41b81529051600091339163890357309160048082019260a092909190829003018186803b1580156200005657600080fd5b505afa1580156200006b573d6000803e3d6000fd5b505050506040513d60a08110156200008257600080fd5b508051602080830151604084015160608086015160809096015160e896871b6001600160e81b0319166101005291811b6001600160601b031990811660e05292811b831660c0529390931b1660a052600282810b900b90921b610120529150620000f79082906200010f811b62002b8417901c565b60801b6001600160801b03191661014052506200017d565b60008082600281900b620d89e719816200012557fe5b05029050600083600281900b620d89e8816200013d57fe5b0502905060008460020b83830360020b816200015557fe5b0560010190508062ffffff166001600160801b038016816200017357fe5b0495945050505050565b60805160601c60a05160601c60c05160601c60e05160601c6101005160e81c6101205160e81c6101405160801c61567e6200024a60003980611fee5280614b5f5280614b96525080610c0052806128fd5280614bca5280614bfc525080610cef52806119cb5280611a0252806129455250806111c75280611a855280611ef4528061244452806129215280613e6b5250806108d252806112f55280611a545280611e8e52806123be5280613d2252508061207b528061227d52806128d9525080612bfb525061567e6000f3fe608060405234801561001057600080fd5b50600436106101ae5760003560e01c806370cf754a116100ee578063c45a015511610097578063ddca3f4311610071578063ddca3f4314610800578063f305839914610820578063f30dba9314610828578063f637731d146108aa576101ae565b8063c45a0155146107d1578063d0c93a7c146107d9578063d21220a7146107f8576101ae565b8063883bdbfd116100c8578063883bdbfd14610633578063a34123a71461073c578063a38807f214610776576101ae565b806370cf754a146105c65780638206a4d1146105ce57806385b66729146105f6576101ae565b80633850c7bd1161015b578063490e6cbc11610135578063490e6cbc146104705780634f1eb3d8146104fc578063514ea4bf1461054d5780635339c296146105a6576101ae565b80633850c7bd1461035b5780633c8a7d8d146103b45780634614131914610456576101ae565b80631ad8b03b1161018c5780631ad8b03b146102aa578063252c09d7146102e157806332148f6714610338576101ae565b80630dfe1681146101b3578063128acb08146101d75780631a68650214610286575b600080fd5b6101bb6108d0565b604080516001600160a01b039092168252519081900360200190f35b61026d600480360360a08110156101ed57600080fd5b6001600160a01b0382358116926020810135151592604082013592606083013516919081019060a08101608082013564010000000081111561022e57600080fd5b82018360208201111561024057600080fd5b8035906020019184600183028401116401000000008311171561026257600080fd5b5090925090506108f4565b6040805192835260208301919091528051918290030190f35b61028e6114ad565b604080516001600160801b039092168252519081900360200190f35b6102b26114bc565b60405180836001600160801b03168152602001826001600160801b031681526020019250505060405180910390f35b6102fe600480360360208110156102f757600080fd5b50356114d6565b6040805163ffffffff909516855260069390930b60208501526001600160a01b039091168383015215156060830152519081900360800190f35b6103596004803603602081101561034e57600080fd5b503561ffff1661151c565b005b610363611616565b604080516001600160a01b03909816885260029690960b602088015261ffff9485168787015292841660608701529216608085015260ff90911660a0840152151560c0830152519081900360e00190f35b61026d600480360360a08110156103ca57600080fd5b6001600160a01b03823516916020810135600290810b92604083013590910b916001600160801b036060820135169181019060a08101608082013564010000000081111561041757600080fd5b82018360208201111561042957600080fd5b8035906020019184600183028401116401000000008311171561044b57600080fd5b509092509050611666565b61045e611922565b60408051918252519081900360200190f35b6103596004803603608081101561048657600080fd5b6001600160a01b0382351691602081013591604082013591908101906080810160608201356401000000008111156104bd57600080fd5b8201836020820111156104cf57600080fd5b803590602001918460018302840111640100000000831117156104f157600080fd5b509092509050611928565b6102b2600480360360a081101561051257600080fd5b506001600160a01b03813516906020810135600290810b91604081013590910b906001600160801b0360608201358116916080013516611d83565b61056a6004803603602081101561056357600080fd5b5035611f9d565b604080516001600160801b0396871681526020810195909552848101939093529084166060840152909216608082015290519081900360a00190f35b61045e600480360360208110156105bc57600080fd5b503560010b611fda565b61028e611fec565b610359600480360360408110156105e457600080fd5b5060ff81358116916020013516612010565b6102b26004803603606081101561060c57600080fd5b506001600160a01b03813516906001600160801b036020820135811691604001351661220f565b6106a36004803603602081101561064957600080fd5b81019060208101813564010000000081111561066457600080fd5b82018360208201111561067657600080fd5b8035906020019184602083028401116401000000008311171561069857600080fd5b5090925090506124dc565b604051808060200180602001838103835285818151815260200191508051906020019060200280838360005b838110156106e75781810151838201526020016106cf565b50505050905001838103825284818151815260200191508051906020019060200280838360005b8381101561072657818101518382015260200161070e565b5050505090500194505050505060405180910390f35b61026d6004803603606081101561075257600080fd5b508035600290810b91602081013590910b90604001356001600160801b0316612569565b6107a06004803603604081101561078c57600080fd5b508035600290810b9160200135900b6126e0565b6040805160069490940b84526001600160a01b03909216602084015263ffffffff1682820152519081900360600190f35b6101bb6128d7565b6107e16128fb565b6040805160029290920b8252519081900360200190f35b6101bb61291f565b610808612943565b6040805162ffffff9092168252519081900360200190f35b61045e612967565b6108486004803603602081101561083e57600080fd5b503560020b61296d565b604080516001600160801b039099168952600f9790970b602089015287870195909552606087019390935260069190910b60808601526001600160a01b031660a085015263ffffffff1660c0840152151560e083015251908190036101000190f35b610359600480360360208110156108c057600080fd5b50356001600160a01b03166129db565b7f000000000000000000000000000000000000000000000000000000000000000081565b6000806108ff612bf0565b85610936576040805162461bcd60e51b8152602060048201526002602482015261415360f01b604482015290519081900360640190fd5b6040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b900b602083015261ffff600160b81b8204811693830193909352600160c81b810483166060830152600160d81b8104909216608082015260ff600160e81b8304811660a0830152600160f01b909204909116151560c082018190526109ef576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b87610a3a5780600001516001600160a01b0316866001600160a01b0316118015610a35575073fffd8963efd1fc6a506488495d951d5263988d266001600160a01b038716105b610a6c565b80600001516001600160a01b0316866001600160a01b0316108015610a6c57506401000276a36001600160a01b038716115b610aa3576040805162461bcd60e51b815260206004820152600360248201526214d41360ea1b604482015290519081900360640190fd5b6000805460ff60f01b191681556040805160c08101909152808a610ad25760048460a0015160ff16901c610ae5565b60108460a0015160ff1681610ae357fe5b065b60ff1681526004546001600160801b03166020820152604001610b06612c27565b63ffffffff168152602001600060060b815260200160006001600160a01b031681526020016000151581525090506000808913905060006040518060e001604052808b81526020016000815260200185600001516001600160a01b03168152602001856020015160020b81526020018c610b8257600254610b86565b6001545b815260200160006001600160801b0316815260200184602001516001600160801b031681525090505b805115801590610bd55750886001600160a01b031681604001516001600160a01b031614155b15610f9f57610be261560e565b60408201516001600160a01b031681526060820151610c25906006907f00000000000000000000000000000000000000000000000000000000000000008f612c2b565b15156040830152600290810b810b60208301819052620d89e719910b1215610c5657620d89e7196020820152610c75565b6020810151620d89e860029190910b1315610c7557620d89e860208201525b610c828160200151612d6d565b6001600160a01b031660608201526040820151610d13908d610cbc578b6001600160a01b031683606001516001600160a01b031611610cd6565b8b6001600160a01b031683606001516001600160a01b0316105b610ce4578260600151610ce6565b8b5b60c085015185517f000000000000000000000000000000000000000000000000000000000000000061309f565b60c085015260a084015260808301526001600160a01b031660408301528215610d7557610d498160c00151826080015101613291565b825103825260a0810151610d6b90610d6090613291565b6020840151906132a7565b6020830152610db0565b610d828160a00151613291565b825101825260c08101516080820151610daa91610d9f9101613291565b6020840151906132c3565b60208301525b835160ff1615610df6576000846000015160ff168260c0015181610dd057fe5b60c0840180519290910491829003905260a0840180519091016001600160801b03169052505b60c08201516001600160801b031615610e3557610e298160c00151600160801b8460c001516001600160801b03166132d9565b60808301805190910190525b80606001516001600160a01b031682604001516001600160a01b03161415610f5e57806040015115610f35578360a00151610ebf57610e9d846040015160008760200151886040015188602001518a606001516008613389909695949392919063ffffffff16565b6001600160a01b03166080860152600690810b900b6060850152600160a08501525b6000610f0b82602001518e610ed657600154610edc565b84608001515b8f610eeb578560800151610eef565b6002545b608089015160608a015160408b0151600595949392919061351c565b90508c15610f17576000035b610f258360c00151826135ef565b6001600160801b031660c0840152505b8b610f44578060200151610f4d565b60018160200151035b600290810b900b6060830152610f99565b80600001516001600160a01b031682604001516001600160a01b031614610f9957610f8c82604001516136a5565b600290810b900b60608301525b50610baf565b836020015160020b816060015160020b1461107a57600080610fed86604001518660400151886020015188602001518a606001518b6080015160086139d1909695949392919063ffffffff16565b604085015160608601516000805461ffff60c81b1916600160c81b61ffff958616021761ffff60b81b1916600160b81b95909416949094029290921762ffffff60a01b1916600160a01b62ffffff60029490940b93909316929092029190911773ffffffffffffffffffffffffffffffffffffffff19166001600160a01b03909116179055506110ac9050565b60408101516000805473ffffffffffffffffffffffffffffffffffffffff19166001600160a01b039092169190911790555b8060c001516001600160801b031683602001516001600160801b0316146110f25760c0810151600480546001600160801b0319166001600160801b039092169190911790555b8a1561114257608081015160015560a08101516001600160801b03161561113d5760a0810151600380546001600160801b031981166001600160801b03918216909301169190911790555b611188565b608081015160025560a08101516001600160801b0316156111885760a0810151600380546001600160801b03808216600160801b92839004821690940116029190911790555b8115158b1515146111a157602081015181518b036111ae565b80600001518a0381602001515b90965094508a156112e75760008512156111f0576111f07f00000000000000000000000000000000000000000000000000000000000000008d87600003613b86565b60006111fa613cd4565b9050336001600160a01b031663fa461e3388888c8c6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b15801561127e57600080fd5b505af1158015611292573d6000803e3d6000fd5b5050505061129e613cd4565b6112a88289613e0d565b11156112e1576040805162461bcd60e51b815260206004820152600360248201526249494160e81b604482015290519081900360640190fd5b50611411565b600086121561131e5761131e7f00000000000000000000000000000000000000000000000000000000000000008d88600003613b86565b6000611328613e1d565b9050336001600160a01b031663fa461e3388888c8c6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b1580156113ac57600080fd5b505af11580156113c0573d6000803e3d6000fd5b505050506113cc613e1d565b6113d68288613e0d565b111561140f576040805162461bcd60e51b815260206004820152600360248201526249494160e81b604482015290519081900360640190fd5b505b60408082015160c083015160608085015184518b8152602081018b90526001600160a01b03948516818701526001600160801b039093169183019190915260020b60808201529151908e169133917fc42079f94a6350d7e6235f29174924f928cc2ac818eb64fed8004e115fbcca679181900360a00190a350506000805460ff60f01b1916600160f01b17905550919890975095505050505050565b6004546001600160801b031681565b6003546001600160801b0380821691600160801b90041682565b60088161ffff81106114e757600080fd5b015463ffffffff81169150640100000000810460060b90600160581b81046001600160a01b031690600160f81b900460ff1684565b600054600160f01b900460ff16611560576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19169055611575612bf0565b60008054600160d81b900461ffff169061159160088385613eb5565b6000805461ffff808416600160d81b810261ffff60d81b19909316929092179092559192508316146115fe576040805161ffff80851682528316602082015281517fac49e518f90a358f652e4400164f05a5d8f7e35e7747279bc3a93dbf584e125a929181900390910190a15b50506000805460ff60f01b1916600160f01b17905550565b6000546001600160a01b03811690600160a01b810460020b9061ffff600160b81b8204811691600160c81b8104821691600160d81b8204169060ff600160e81b8204811691600160f01b90041687565b600080548190600160f01b900460ff166116ad576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b191690556001600160801b0385166116cd57600080fd5b60008061171b60405180608001604052808c6001600160a01b031681526020018b60020b81526020018a60020b81526020016117118a6001600160801b0316613f58565b600f0b9052613f69565b9250925050819350809250600080600086111561173d5761173a613cd4565b91505b841561174e5761174b613e1d565b90505b336001600160a01b031663d348799787878b8b6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b1580156117d057600080fd5b505af11580156117e4573d6000803e3d6000fd5b50505050600086111561183b576117f9613cd4565b6118038388613e0d565b111561183b576040805162461bcd60e51b815260206004820152600260248201526104d360f41b604482015290519081900360640190fd5b841561188b57611849613e1d565b6118538287613e0d565b111561188b576040805162461bcd60e51b81526020600482015260026024820152614d3160f01b604482015290519081900360640190fd5b8960020b8b60020b8d6001600160a01b03167f7a53080ba414158be7ec69b987b5fb7d07dee101fe85488f0853ae16239d0bde338d8b8b60405180856001600160a01b03168152602001846001600160801b0316815260200183815260200182815260200194505050505060405180910390a450506000805460ff60f01b1916600160f01b17905550919890975095505050505050565b60025481565b600054600160f01b900460ff1661196c576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19169055611981612bf0565b6004546001600160801b0316806119c3576040805162461bcd60e51b81526020600482015260016024820152601360fa1b604482015290519081900360640190fd5b60006119f8867f000000000000000000000000000000000000000000000000000000000000000062ffffff16620f42406141a9565b90506000611a2f867f000000000000000000000000000000000000000000000000000000000000000062ffffff16620f42406141a9565b90506000611a3b613cd4565b90506000611a47613e1d565b90508815611a7a57611a7a7f00000000000000000000000000000000000000000000000000000000000000008b8b613b86565b8715611aab57611aab7f00000000000000000000000000000000000000000000000000000000000000008b8a613b86565b336001600160a01b031663e9cbafb085858a8a6040518563ffffffff1660e01b815260040180858152602001848152602001806020018281038252848482818152602001925080828437600081840152601f19601f82011690508083019250505095505050505050600060405180830381600087803b158015611b2d57600080fd5b505af1158015611b41573d6000803e3d6000fd5b505050506000611b4f613cd4565b90506000611b5b613e1d565b905081611b688588613e0d565b1115611ba0576040805162461bcd60e51b8152602060048201526002602482015261046360f41b604482015290519081900360640190fd5b80611bab8487613e0d565b1115611be3576040805162461bcd60e51b8152602060048201526002602482015261463160f01b604482015290519081900360640190fd5b8382038382038115611c725760008054600160e81b9004600f16908115611c16578160ff168481611c1057fe5b04611c19565b60005b90506001600160801b03811615611c4c57600380546001600160801b038082168401166001600160801b03199091161790555b611c66818503600160801b8d6001600160801b03166132d9565b60018054909101905550505b8015611cfd5760008054600160e81b900460041c600f16908115611ca2578160ff168381611c9c57fe5b04611ca5565b60005b90506001600160801b03811615611cd757600380546001600160801b03600160801b8083048216850182160291161790555b611cf1818403600160801b8d6001600160801b03166132d9565b60028054909101905550505b8d6001600160a01b0316336001600160a01b03167fbdbdb71d7860376ba52b25a5028beea23581364a40522f6bcfb86bb1f2dca6338f8f86866040518085815260200184815260200183815260200182815260200194505050505060405180910390a350506000805460ff60f01b1916600160f01b179055505050505050505050505050565b600080548190600160f01b900460ff16611dca576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b19168155611de460073389896141e3565b60038101549091506001600160801b0390811690861611611e055784611e14565b60038101546001600160801b03165b60038201549093506001600160801b03600160801b909104811690851611611e3c5783611e52565b6003810154600160801b90046001600160801b03165b91506001600160801b03831615611eb7576003810180546001600160801b031981166001600160801b03918216869003821617909155611eb7907f0000000000000000000000000000000000000000000000000000000000000000908a908616613b86565b6001600160801b03821615611f1d576003810180546001600160801b03600160801b808304821686900382160291811691909117909155611f1d907f0000000000000000000000000000000000000000000000000000000000000000908a908516613b86565b604080516001600160a01b038a1681526001600160801b0380861660208301528416818301529051600288810b92908a900b9133917f70935338e69775456a85ddef226c395fb668b63fa0115f5f20610b388e6ca9c0919081900360600190a4506000805460ff60f01b1916600160f01b17905590969095509350505050565b60076020526000908152604090208054600182015460028301546003909301546001600160801b0392831693919281811691600160801b90041685565b60066020526000908152604090205481565b7f000000000000000000000000000000000000000000000000000000000000000081565b600054600160f01b900460ff16612054576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916905560408051638da5cb5b60e01b815290516001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001691638da5cb5b916004808301926020929190829003018186803b1580156120c157600080fd5b505afa1580156120d5573d6000803e3d6000fd5b505050506040513d60208110156120eb57600080fd5b50516001600160a01b0316331461210157600080fd5b60ff82161580612124575060048260ff16101580156121245750600a8260ff1611155b801561214e575060ff8116158061214e575060048160ff161015801561214e5750600a8160ff1611155b61215757600080fd5b60008054610ff0600484901b16840160ff908116600160e81b9081027fffff00ffffffffffffffffffffffffffffffffffffffffffffffffffffffffff841617909355919004167f973d8d92bb299f4af6ce49b52a8adb85ae46b9f214c4c4fc06ac77401237b1336010826040805160ff9390920683168252600f600486901c16602083015286831682820152918516606082015290519081900360800190a150506000805460ff60f01b1916600160f01b17905550565b600080548190600160f01b900460ff16612256576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916905560408051638da5cb5b60e01b815290516001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001691638da5cb5b916004808301926020929190829003018186803b1580156122c357600080fd5b505afa1580156122d7573d6000803e3d6000fd5b505050506040513d60208110156122ed57600080fd5b50516001600160a01b0316331461230357600080fd5b6003546001600160801b039081169085161161231f578361232c565b6003546001600160801b03165b6003549092506001600160801b03600160801b9091048116908416116123525782612366565b600354600160801b90046001600160801b03165b90506001600160801b038216156123e7576003546001600160801b038381169116141561239557600019909101905b600380546001600160801b031981166001600160801b039182168590038216179091556123e7907f00000000000000000000000000000000000000000000000000000000000000009087908516613b86565b6001600160801b0381161561246d576003546001600160801b03828116600160801b90920416141561241857600019015b600380546001600160801b03600160801b80830482168590038216029181169190911790915561246d907f00000000000000000000000000000000000000000000000000000000000000009087908416613b86565b604080516001600160801b0380851682528316602082015281516001600160a01b0388169233927f596b573906218d3411850b26a6b437d6c4522fdb43d2d2386263f86d50b8b151929081900390910190a36000805460ff60f01b1916600160f01b1790559094909350915050565b6060806124e7612bf0565b61255e6124f2612c27565b858580806020026020016040519081016040528093929190818152602001838360200280828437600092018290525054600454600896959450600160a01b820460020b935061ffff600160b81b8304811693506001600160801b0390911691600160c81b900416614247565b915091509250929050565b600080548190600160f01b900460ff166125b0576040805162461bcd60e51b81526020600482015260036024820152624c4f4b60e81b604482015290519081900360640190fd5b6000805460ff60f01b1916815560408051608081018252338152600288810b602083015287900b918101919091528190819061260990606081016125fc6001600160801b038a16613f58565b600003600f0b9052613f69565b925092509250816000039450806000039350600085118061262a5750600084115b15612669576003830180546001600160801b038082168089018216600160801b93849004831689019092169092029091176001600160801b0319161790555b604080516001600160801b0388168152602081018790528082018690529051600289810b92908b900b9133917f0c396cd989a39f4459b5fa1aed6a9a8dcdbc45908acfd67e028cd568da98982c919081900360600190a450506000805460ff60f01b1916600160f01b179055509094909350915050565b60008060006126ed612bf0565b6126f785856143a1565b600285810b810b60009081526005602052604080822087840b90930b825281206003830154600681900b9367010000000000000082046001600160a01b0316928492600160d81b810463ffffffff169284929091600160f81b900460ff168061275f57600080fd5b6003820154600681900b985067010000000000000081046001600160a01b03169650600160d81b810463ffffffff169450600160f81b900460ff16806127a457600080fd5b50506040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b810b6020840181905261ffff600160b81b8404811695850195909552600160c81b830485166060850152600160d81b8304909416608084015260ff600160e81b8304811660a0850152600160f01b909204909116151560c08301529093508e810b91900b1215905061284d575093909403965090039350900390506128d0565b8a60020b816020015160020b12156128c1576000612869612c27565b602083015160408401516004546060860151939450600093849361289f936008938893879392916001600160801b031690613389565b9a9003989098039b5050949096039290920396509091030392506128d0915050565b50949093039650039350900390505b9250925092565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b7f000000000000000000000000000000000000000000000000000000000000000081565b60015481565b60056020526000908152604090208054600182015460028301546003909301546001600160801b03831693600160801b909304600f0b9290600681900b9067010000000000000081046001600160a01b031690600160d81b810463ffffffff1690600160f81b900460ff1688565b6000546001600160a01b031615612a1e576040805162461bcd60e51b8152602060048201526002602482015261414960f01b604482015290519081900360640190fd5b6000612a29826136a5565b9050600080612a41612a39612c27565b60089061446a565b6040805160e0810182526001600160a01b038816808252600288810b6020808501829052600085870181905261ffff898116606088018190529089166080880181905260a08801839052600160c0909801979097528154600160f01b73ffffffffffffffffffffffffffffffffffffffff19909116871762ffffff60a01b1916600160a01b62ffffff9787900b9790971696909602959095177fffffffffff00000000ffffffffffffffffffffffffffffffffffffffffffffff16600160c81b9091021761ffff60d81b1916600160d81b909602959095177fff0000ffffffffffffffffffffffffffffffffffffffffffffffffffffffffff1692909217909355835191825281019190915281519395509193507f98636036cb66a9c19a37435efc1e90142190214e8abeb821bdba3f2990dd4c9592918290030190a150505050565b60008082600281900b620d89e71981612b9957fe5b05029050600083600281900b620d89e881612bb057fe5b0502905060008460020b83830360020b81612bc757fe5b0560010190508062ffffff166001600160801b03801681612be457fe5b0493505050505b919050565b306001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001614612c2557600080fd5b565b4290565b60008060008460020b8660020b81612c3f57fe5b05905060008660020b128015612c6657508460020b8660020b81612c5f57fe5b0760020b15155b15612c7057600019015b8315612ce557600080612c82836144b6565b600182810b810b600090815260208d9052604090205460ff83169190911b80016000190190811680151597509294509092509085612cc757888360ff16860302612cda565b88612cd1826144c8565b840360ff168603025b965050505050612d63565b600080612cf4836001016144b6565b91509150600060018260ff166001901b031990506000818b60008660010b60010b8152602001908152602001600020541690508060001415955085612d4657888360ff0360ff16866001010102612d5c565b8883612d5183614568565b0360ff168660010101025b9650505050505b5094509492505050565b60008060008360020b12612d84578260020b612d8c565b8260020b6000035b9050620d89e8811115612dca576040805162461bcd60e51b81526020600482015260016024820152601560fa1b604482015290519081900360640190fd5b600060018216612dde57600160801b612df0565b6ffffcb933bd6fad37aa2d162d1a5940015b70ffffffffffffffffffffffffffffffffff1690506002821615612e24576ffff97272373d413259a46990580e213a0260801c5b6004821615612e43576ffff2e50f5f656932ef12357cf3c7fdcc0260801c5b6008821615612e62576fffe5caca7e10e4e61c3624eaa0941cd00260801c5b6010821615612e81576fffcb9843d60f6159c9db58835c9266440260801c5b6020821615612ea0576fff973b41fa98c081472e6896dfb254c00260801c5b6040821615612ebf576fff2ea16466c96a3843ec78b326b528610260801c5b6080821615612ede576ffe5dee046a99a2a811c461f1969c30530260801c5b610100821615612efe576ffcbe86c7900a88aedcffc83b479aa3a40260801c5b610200821615612f1e576ff987a7253ac413176f2b074cf7815e540260801c5b610400821615612f3e576ff3392b0822b70005940c7a398e4b70f30260801c5b610800821615612f5e576fe7159475a2c29b7443b29c7fa6e889d90260801c5b611000821615612f7e576fd097f3bdfd2022b8845ad8f792aa58250260801c5b612000821615612f9e576fa9f746462d870fdf8a65dc1f90e061e50260801c5b614000821615612fbe576f70d869a156d2a1b890bb3df62baf32f70260801c5b618000821615612fde576f31be135f97d08fd981231505542fcfa60260801c5b62010000821615612fff576f09aa508b5b7a84e1c677de54f3e99bc90260801c5b6202000082161561301f576e5d6af8dedb81196699c329225ee6040260801c5b6204000082161561303e576d2216e584f5fa1ea926041bedfe980260801c5b6208000082161561305b576b048a170391f7dc42444e8fa20260801c5b60008460020b131561307657806000198161307257fe5b0490505b64010000000081061561308a57600161308d565b60005b60ff16602082901c0192505050919050565b60008080806001600160a01b03808916908a1610158187128015906131245760006130d88989620f42400362ffffff16620f42406132d9565b9050826130f1576130ec8c8c8c6001614652565b6130fe565b6130fe8b8d8c60016146cd565b955085811061310f578a965061311e565b61311b8c8b838661478a565b96505b5061316e565b8161313b576131368b8b8b60006146cd565b613148565b6131488a8c8b6000614652565b935083886000031061315c5789955061316e565b61316b8b8a8a600003856147d6565b95505b6001600160a01b038a81169087161482156131d15780801561318d5750815b6131a35761319e878d8c60016146cd565b6131a5565b855b95508080156131b2575081155b6131c8576131c3878d8c6000614652565b6131ca565b845b945061321b565b8080156131db5750815b6131f1576131ec8c888c6001614652565b6131f3565b855b9550808015613200575081155b613216576132118c888c60006146cd565b613218565b845b94505b8115801561322b57508860000385115b15613237578860000394505b81801561325657508a6001600160a01b0316876001600160a01b031614155b15613265578589039350613282565b61327f868962ffffff168a620f42400362ffffff166141a9565b93505b50505095509550955095915050565b6000600160ff1b82106132a357600080fd5b5090565b808203828113156000831215146132bd57600080fd5b92915050565b818101828112156000831215146132bd57600080fd5b600080806000198587098686029250828110908390030390508061330f576000841161330457600080fd5b508290049050613382565b80841161331b57600080fd5b6000848688096000868103871696879004966002600389028118808a02820302808a02820302808a02820302808a02820302808a02820302808a02909103029181900381900460010186841190950394909402919094039290920491909117919091029150505b9392505050565b60008063ffffffff8716613430576000898661ffff1661ffff81106133aa57fe5b60408051608081018252919092015463ffffffff8082168084526401000000008304600690810b810b900b6020850152600160581b83046001600160a01b031694840194909452600160f81b90910460ff16151560608301529092508a161461341c57613419818a8988614822565b90505b806020015181604001519250925050613510565b8688036000806134458c8c858c8c8c8c6148d2565b91509150816000015163ffffffff168363ffffffff161415613477578160200151826040015194509450505050613510565b805163ffffffff8481169116141561349f578060200151816040015194509450505050613510565b8151815160208085015190840151918390039286039163ffffffff80841692908516910360060b816134cd57fe5b05028460200151018263ffffffff168263ffffffff1686604001518660400151036001600160a01b031602816134ff57fe5b048560400151019650965050505050505b97509795505050505050565b600295860b860b60009081526020979097526040909620600181018054909503909455938301805490920390915560038201805463ffffffff600160d81b6001600160a01b036701000000000000008085048216909603169094027fffffffffff0000000000000000000000000000000000000000ffffffffffffff90921691909117600681810b90960390950b66ffffffffffffff1666ffffffffffffff199095169490941782810485169095039093160263ffffffff60d81b1990931692909217905554600160801b9004600f0b90565b60008082600f0b121561365457826001600160801b03168260000384039150816001600160801b03161061364f576040805162461bcd60e51b81526020600482015260026024820152614c5360f01b604482015290519081900360640190fd5b6132bd565b826001600160801b03168284019150816001600160801b031610156132bd576040805162461bcd60e51b81526020600482015260026024820152614c4160f01b604482015290519081900360640190fd5b60006401000276a36001600160a01b038316108015906136e1575073fffd8963efd1fc6a506488495d951d5263988d266001600160a01b038316105b613716576040805162461bcd60e51b81526020600482015260016024820152602960f91b604482015290519081900360640190fd5b77ffffffffffffffffffffffffffffffffffffffff00000000602083901b166001600160801b03811160071b81811c67ffffffffffffffff811160061b90811c63ffffffff811160051b90811c61ffff811160041b90811c60ff8111600390811b91821c600f811160021b90811c918211600190811b92831c979088119617909417909217179091171717608081106137b757607f810383901c91506137c1565b80607f0383901b91505b908002607f81811c60ff83811c9190911c800280831c81831c1c800280841c81841c1c800280851c81851c1c800280861c81861c1c800280871c81871c1c800280881c81881c1c800280891c81891c1c8002808a1c818a1c1c8002808b1c818b1c1c8002808c1c818c1c1c8002808d1c818d1c1c8002808e1c9c81901c9c909c1c80029c8d901c9e9d607f198f0160401b60c09190911c678000000000000000161760c19b909b1c674000000000000000169a909a1760c29990991c672000000000000000169890981760c39790971c671000000000000000169690961760c49590951c670800000000000000169490941760c59390931c670400000000000000169290921760c69190911c670200000000000000161760c79190911c670100000000000000161760c89190911c6680000000000000161760c99190911c6640000000000000161760ca9190911c6620000000000000161760cb9190911c6610000000000000161760cc9190911c6608000000000000161760cd9190911c66040000000000001617693627a301d71055774c8581026f028f6481ab7f045a5af012a19d003aa9198101608090811d906fdb2df09e81959a81455e260799a0632f8301901d600281810b9083900b146139c257886001600160a01b03166139a682612d6d565b6001600160a01b031611156139bb57816139bd565b805b6139c4565b815b9998505050505050505050565b6000806000898961ffff1661ffff81106139e757fe5b60408051608081018252919092015463ffffffff8082168084526401000000008304600690810b810b900b6020850152600160581b83046001600160a01b031694840194909452600160f81b90910460ff161515606083015290925089161415613a575788859250925050613510565b8461ffff168461ffff16118015613a7857506001850361ffff168961ffff16145b15613a8557839150613a89565b8491505b8161ffff168960010161ffff1681613a9d57fe5b069250613aac81898989614822565b8a8461ffff1661ffff8110613abd57fe5b825191018054602084015160408501516060909501511515600160f81b027effffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff6001600160a01b03909616600160581b027fff0000000000000000000000000000000000000000ffffffffffffffffffffff60069390930b66ffffffffffffff16640100000000026affffffffffffff000000001963ffffffff90971663ffffffff199095169490941795909516929092171692909217929092161790555097509795505050505050565b604080516001600160a01b038481166024830152604480830185905283518084039091018152606490920183526020820180516001600160e01b031663a9059cbb60e01b1781529251825160009485949389169392918291908083835b60208310613c025780518252601f199092019160209182019101613be3565b6001836020036101000a0380198251168184511680821785525050505050509050019150506000604051808303816000865af19150503d8060008114613c64576040519150601f19603f3d011682016040523d82523d6000602084013e613c69565b606091505b5091509150818015613c97575080511580613c975750808060200190516020811015613c9457600080fd5b50515b613ccd576040805162461bcd60e51b81526020600482015260026024820152612a2360f11b604482015290519081900360640190fd5b5050505050565b604080513060248083019190915282518083039091018152604490910182526020810180516001600160e01b03166370a0823160e01b17815291518151600093849384936001600160a01b037f00000000000000000000000000000000000000000000000000000000000000001693919290918291908083835b60208310613d6d5780518252601f199092019160209182019101613d4e565b6001836020036101000a038019825116818451168082178552505050505050905001915050600060405180830381855afa9150503d8060008114613dcd576040519150601f19603f3d011682016040523d82523d6000602084013e613dd2565b606091505b5091509150818015613de657506020815110155b613def57600080fd5b808060200190516020811015613e0457600080fd5b50519250505090565b808201828110156132bd57600080fd5b604080513060248083019190915282518083039091018152604490910182526020810180516001600160e01b03166370a0823160e01b17815291518151600093849384936001600160a01b037f000000000000000000000000000000000000000000000000000000000000000016939192909182919080838360208310613d6d5780518252601f199092019160209182019101613d4e565b6000808361ffff1611613ef3576040805162461bcd60e51b81526020600482015260016024820152604960f81b604482015290519081900360640190fd5b8261ffff168261ffff1611613f09575081613382565b825b8261ffff168161ffff161015613f4f576001858261ffff1661ffff8110613f2e57fe5b01805463ffffffff191663ffffffff92909216919091179055600101613f0b565b50909392505050565b80600f81900b8114612beb57600080fd5b6000806000613f76612bf0565b613f88846020015185604001516143a1565b6040805160e0810182526000546001600160a01b0381168252600160a01b8104600290810b810b900b602080840182905261ffff600160b81b8404811685870152600160c81b84048116606080870191909152600160d81b8504909116608086015260ff600160e81b8504811660a0870152600160f01b909404909316151560c08501528851908901519489015192890151939461402c9491939092909190614acf565b93508460600151600f0b6000146141a157846020015160020b816020015160020b12156140815761407a6140638660200151612d6d565b6140708760400151612d6d565b8760600151614c84565b92506141a1565b846040015160020b816020015160020b12156141775760045460408201516001600160801b03909116906140d3906140b7612c27565b60208501516060860151608087015160089493929187916139d1565b6000805461ffff60c81b1916600160c81b61ffff938416021761ffff60b81b1916600160b81b939092169290920217905581516040870151614123919061411990612d6d565b8860600151614c84565b93506141416141358760200151612d6d565b83516060890151614cc8565b92506141518187606001516135ef565b600480546001600160801b0319166001600160801b0392909216919091179055506141a1565b61419e6141878660200151612d6d565b6141948760400151612d6d565b8760600151614cc8565b91505b509193909250565b60006141b68484846132d9565b9050600082806141c257fe5b84860911156133825760001981106141d957600080fd5b6001019392505050565b6040805160609490941b6bffffffffffffffffffffffff1916602080860191909152600293840b60e890811b60348701529290930b90911b60378401528051808403601a018152603a90930181528251928201929092206000908152929052902090565b60608060008361ffff1611614287576040805162461bcd60e51b81526020600482015260016024820152604960f81b604482015290519081900360640190fd5b865167ffffffffffffffff8111801561429f57600080fd5b506040519080825280602002602001820160405280156142c9578160200160208202803683370190505b509150865167ffffffffffffffff811180156142e457600080fd5b5060405190808252806020026020018201604052801561430e578160200160208202803683370190505b50905060005b87518110156143945761433f8a8a8a848151811061432e57fe5b60200260200101518a8a8a8a613389565b84838151811061434b57fe5b6020026020010184848151811061435e57fe5b60200260200101826001600160a01b03166001600160a01b03168152508260060b60060b81525050508080600101915050614314565b5097509795505050505050565b8060020b8260020b126143e1576040805162461bcd60e51b8152602060048201526003602482015262544c5560e81b604482015290519081900360640190fd5b620d89e719600283900b1215614424576040805162461bcd60e51b8152602060048201526003602482015262544c4d60e81b604482015290519081900360640190fd5b620d89e8600282900b1315614466576040805162461bcd60e51b815260206004820152600360248201526254554d60e81b604482015290519081900360640190fd5b5050565b6040805160808101825263ffffffff9283168082526000602083018190529282019290925260016060909101819052835463ffffffff1916909117909116600160f81b17909155908190565b60020b600881901d9161010090910790565b60008082116144d657600080fd5b600160801b82106144e957608091821c91015b68010000000000000000821061450157604091821c91015b640100000000821061451557602091821c91015b62010000821061452757601091821c91015b610100821061453857600891821c91015b6010821061454857600491821c91015b6004821061455857600291821c91015b60028210612beb57600101919050565b600080821161457657600080fd5b5060ff6001600160801b0382161561459157607f1901614599565b608082901c91505b67ffffffffffffffff8216156145b257603f19016145ba565b604082901c91505b63ffffffff8216156145cf57601f19016145d7565b602082901c91505b61ffff8216156145ea57600f19016145f2565b601082901c91505b60ff821615614604576007190161460c565b600882901c91505b600f82161561461e5760031901614626565b600482901c91505b60038216156146385760011901614640565b600282901c91505b6001821615612beb5760001901919050565b6000836001600160a01b0316856001600160a01b03161115614672579293925b8161469f5761469a836001600160801b03168686036001600160a01b0316600160601b6132d9565b6146c2565b6146c2836001600160801b03168686036001600160a01b0316600160601b6141a9565b90505b949350505050565b6000836001600160a01b0316856001600160a01b031611156146ed579293925b7bffffffffffffffffffffffffffffffff000000000000000000000000606084901b166001600160a01b03868603811690871661472957600080fd5b8361475957866001600160a01b031661474c8383896001600160a01b03166132d9565b8161475357fe5b0461477f565b61477f6147708383896001600160a01b03166141a9565b886001600160a01b0316614cf7565b979650505050505050565b600080856001600160a01b0316116147a157600080fd5b6000846001600160801b0316116147b757600080fd5b816147c95761469a8585856001614d02565b6146c28585856001614de3565b600080856001600160a01b0316116147ed57600080fd5b6000846001600160801b03161161480357600080fd5b816148155761469a8585856000614de3565b6146c28585856000614d02565b61482a61564a565b600085600001518503905060405180608001604052808663ffffffff1681526020018263ffffffff168660020b0288602001510160060b81526020016000856001600160801b03161161487e576001614880565b845b6001600160801b031673ffffffff00000000000000000000000000000000608085901b16816148ab57fe5b048860400151016001600160a01b0316815260200160011515815250915050949350505050565b6148da61564a565b6148e261564a565b888561ffff1661ffff81106148f357fe5b60408051608081018252919092015463ffffffff81168083526401000000008204600690810b810b900b6020840152600160581b82046001600160a01b031693830193909352600160f81b900460ff1615156060820152925061495890899089614ed8565b15614990578663ffffffff16826000015163ffffffff16141561497a57613510565b8161498783898988614822565b91509150613510565b888361ffff168660010161ffff16816149a557fe5b0661ffff1661ffff81106149b557fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b90910416151560608201819052909250614a6c57604080516080810182528a5463ffffffff811682526401000000008104600690810b810b900b6020830152600160581b81046001600160a01b031692820192909252600160f81b90910460ff161515606082015291505b614a7b88836000015189614ed8565b614ab2576040805162461bcd60e51b815260206004820152600360248201526213d31160ea1b604482015290519081900360640190fd5b614abf8989898887614f9b565b9150915097509795505050505050565b6000614ade60078787876141e3565b60015460025491925090600080600f87900b15614c24576000614aff612c27565b6000805460045492935090918291614b499160089186918591600160a01b810460020b9161ffff600160b81b83048116926001600160801b0390921691600160c81b900416613389565b9092509050614b8360058d8b8d8b8b87898b60007f000000000000000000000000000000000000000000000000000000000000000061513b565b9450614bba60058c8b8d8b8b87898b60017f000000000000000000000000000000000000000000000000000000000000000061513b565b93508415614bee57614bee60068d7f0000000000000000000000000000000000000000000000000000000000000000615325565b8315614c2057614c2060068c7f0000000000000000000000000000000000000000000000000000000000000000615325565b5050505b600080614c3660058c8c8b8a8a61538b565b9092509050614c47878a8484615437565b600089600f0b1215614c75578315614c6457614c6460058c6155cc565b8215614c7557614c7560058b6155cc565b50505050505095945050505050565b60008082600f0b12614caa57614ca5614ca085858560016146cd565b613291565b6146c5565b614cbd614ca085858560000360006146cd565b600003949350505050565b60008082600f0b12614ce457614ca5614ca08585856001614652565b614cbd614ca08585856000036000614652565b808204910615150190565b60008115614d755760006001600160a01b03841115614d3857614d3384600160601b876001600160801b03166132d9565b614d50565b6001600160801b038516606085901b81614d4e57fe5b045b9050614d6d614d686001600160a01b03881683613e0d565b6155f8565b9150506146c5565b60006001600160a01b03841115614da357614d9e84600160601b876001600160801b03166141a9565b614dba565b614dba606085901b6001600160801b038716614cf7565b905080866001600160a01b031611614dd157600080fd5b6001600160a01b0386160390506146c5565b600082614df15750836146c5565b7bffffffffffffffffffffffffffffffff000000000000000000000000606085901b168215614e91576001600160a01b03861684810290858281614e3157fe5b041415614e6257818101828110614e6057614e5683896001600160a01b0316836141a9565b93505050506146c5565b505b614e8882614e83878a6001600160a01b03168681614e7c57fe5b0490613e0d565b614cf7565b925050506146c5565b6001600160a01b03861684810290858281614ea857fe5b04148015614eb557508082115b614ebe57600080fd5b808203614e56614d68846001600160a01b038b16846141a9565b60008363ffffffff168363ffffffff1611158015614f0257508363ffffffff168263ffffffff1611155b15614f1e578163ffffffff168363ffffffff1611159050613382565b60008463ffffffff168463ffffffff1611614f46578363ffffffff1664010000000001614f4e565b8363ffffffff165b64ffffffffff16905060008563ffffffff168463ffffffff1611614f7f578363ffffffff1664010000000001614f87565b8363ffffffff165b64ffffffffff169091111595945050505050565b614fa361564a565b614fab61564a565b60008361ffff168560010161ffff1681614fc157fe5b0661ffff169050600060018561ffff16830103905060005b506002818301048961ffff87168281614fee57fe5b0661ffff8110614ffa57fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b9091041615156060820181905290955061506557806001019250614fd9565b898661ffff16826001018161507657fe5b0661ffff811061508257fe5b60408051608081018252929091015463ffffffff811683526401000000008104600690810b810b900b60208401526001600160a01b03600160581b8204169183019190915260ff600160f81b909104161515606082015285519094506000906150ed908b908b614ed8565b905080801561510657506151068a8a8760000151614ed8565b15615111575061512e565b8061512157600182039250615128565b8160010193505b50614fd9565b5050509550959350505050565b60028a810b900b600090815260208c90526040812080546001600160801b031682615166828d6135ef565b9050846001600160801b0316816001600160801b031611156151b4576040805162461bcd60e51b81526020600482015260026024820152614c4f60f01b604482015290519081900360640190fd5b6001600160801b03828116159082161581141594501561528a578c60020b8e60020b1361525a57600183018b9055600283018a90556003830180547fffffffffff0000000000000000000000000000000000000000ffffffffffffff166701000000000000006001600160a01b038c16021766ffffffffffffff191666ffffffffffffff60068b900b161763ffffffff60d81b1916600160d81b63ffffffff8a16021790555b6003830180547effffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff16600160f81b1790555b82546001600160801b0319166001600160801b038216178355856152d35782546152ce906152c990600160801b9004600f90810b810b908f900b6132c3565b613f58565b6152f4565b82546152f4906152c990600160801b9004600f90810b810b908f900b6132a7565b8354600f9190910b6001600160801b03908116600160801b0291161790925550909c9b505050505050505050505050565b8060020b8260020b8161533457fe5b0760020b1561534257600080fd5b60008061535d8360020b8560020b8161535757fe5b056144b6565b600191820b820b60009081526020979097526040909620805460ff9097169190911b90951890945550505050565b600285810b80820b60009081526020899052604080822088850b850b83529082209193849391929184918291908a900b126153d1575050600182015460028301546153e4565b8360010154880391508360020154870390505b6000808b60020b8b60020b121561540657505060018301546002840154615419565b84600101548a0391508460020154890390505b92909803979097039b96909503949094039850939650505050505050565b6040805160a08101825285546001600160801b0390811682526001870154602083015260028701549282019290925260038601548083166060830152600160801b900490911660808201526000600f85900b6154d65781516001600160801b03166154ce576040805162461bcd60e51b815260206004820152600260248201526104e560f41b604482015290519081900360640190fd5b5080516154e5565b81516154e290866135ef565b90505b60006155098360200151860384600001516001600160801b0316600160801b6132d9565b9050600061552f8460400151860385600001516001600160801b0316600160801b6132d9565b905086600f0b6000146155565787546001600160801b0319166001600160801b0384161788555b60018801869055600288018590556001600160801b03821615158061558457506000816001600160801b0316115b156155c2576003880180546001600160801b031981166001600160801b039182168501821617808216600160801b9182900483168501909216021790555b5050505050505050565b600290810b810b6000908152602092909252604082208281556001810183905590810182905560030155565b806001600160a01b0381168114612beb57600080fd5b6040805160e081018252600080825260208201819052918101829052606081018290526080810182905260a0810182905260c081019190915290565b6040805160808101825260008082526020820181905291810182905260608101919091529056fea164736f6c6343000706000a"
```
[27](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Constants.sol#L27)

```solidity
File: contracts/libraries/Errors.sol

16: /// @notice A mint or swap callback was attempted from an address that did not match the canonical Uniswap V3 pool with the claimed features
```
[16](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Errors.sol#L16)

```solidity
File: contracts/libraries/FeesCalc.sol

14: /// @notice Some options positions involve moving liquidity chunks to the AMM/Uniswap. Those chunks can then earn AMM swap fees.
53: /// @return feesEachToken the fees collected from the AMM for each token (LeftRight-packed) with token0 in the right slot and token1 in the left slot
96: // lowerOut0: For token0: fee growth per unit of liquidity on the _other_ side of tickLower (relative to currentTick)
```
[14](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L14) | [53](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L53) | [96](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L96)

```solidity
File: contracts/libraries/Math.sol

34: /// @dev Implemented using Uniswap's "incorrect" constants. Supplying commented-out real values for an accurate calculation
180: /// @notice Calculates floor(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0.
282: /// @notice Calculates floor(a×b÷2^64) with full precision. Throws if result overflows a uint256 or denominator == 0.
329: // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)
344: /// @notice Calculates floor(a×b÷2^96) with full precision. Throws if result overflows a uint256 or denominator == 0.
391: // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)
406: /// @notice Calculates floor(a×b÷2^128) with full precision. Throws if result overflows a uint256 or denominator == 0.
453: // Divide [prod1 prod0] by the factors of two (note that this is just 2**128 since the denominator is a power of 2 itself)
468: /// @notice Calculates floor(a×b÷2^192) with full precision. Throws if result overflows a uint256 or denominator == 0.
515: // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)
```
[34](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L34) | [180](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L180) | [282](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L282) | [329](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L329) | [344](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L344) | [391](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L391) | [406](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L406) | [453](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L453) | [468](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L468) | [515](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/Math.sol#L515)

```solidity
File: contracts/libraries/PanopticMath.sol

28: ///      the 64 bits are the 64 *last* (most significant) bits - and thus corresponds to the *first* 16 hex characters (reading left to right)
47: /// @return finalPoolId the final 64-bit pool id as encoded in the `TokenId` type - composed of the last 64 bits of the address and a hash of the parameters
65: /// @notice For a given option position (`tokenId`), leg index within that position (`legIndex`), and `positionSize` get the tick range spanned and its
81: /// @return liquidityChunk a uint256 bit-packed (see `LiquidityChunk.sol`) with `tickLower`, `tickUpper`, and `liquidity`
104: //  Because Uni v3 chooses token0 and token1 from the alphanumeric order, there is no consistency as to whether token0 is
105: //  stablecoin, ETH, or an ERC20. Some pools may want ETH to be the asset (e.g. ETH-DAI) and some may wish the stablecoin to
109: //  To solve this, we encode the asset value in tokenId. This parameter specifies which of token0 or token1 is the
140: /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.
163: /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.
```
[28](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L28) | [47](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L47) | [65](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L65) | [81](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L81) | [104](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L104) | [105](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L105) | [109](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L109) | [140](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140) | [163](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L163)

```solidity
File: contracts/libraries/SafeTransferLib.sol

20: // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
```
[20](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L20)

```solidity
File: contracts/multicall/Multicall.sol

22: // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
24: // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
```
[22](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L22) | [24](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L24)
</details>

### [N-70] Function Parameters in Public Accessible Functions Need `address(0)` Check

Parameters of type `address` in your functions should be checked to ensure that they are not assigned the null address (`address(0x0)`). 
Failure to validate these parameters can lead to transaction reverts, wasted gas, the need for transaction resubmission, and may even require redeployment of contracts within the protocol in certain situations.
Implement checks for `address(0x0)` to avoid these potential issues.

<details>
<summary><i>9 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit `token0` parameter without address(0) check
/// @audit `token1` parameter without address(0) check
351: function initializeAMMPool(address token0, address token1, uint24 fee) external {
/// @audit `univ3pool` parameter without address(0) check
/// @audit `owner` parameter without address(0) check
1343: function getAccountLiquidity(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper
    ) external view returns (uint256 accountLiquidities) {
/// @audit `univ3pool` parameter without address(0) check
/// @audit `owner` parameter without address(0) check
1371: function getAccountPremium(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper,
        int24 atTick,
        uint256 isLong
    ) external view returns (uint128 premiumToken0, uint128 premiumToken1) {
/// @audit `univ3pool` parameter without address(0) check
/// @audit `owner` parameter without address(0) check
1437: function getAccountFeesBase(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper
    ) external view returns (int128 feesBase0, int128 feesBase1) {
/// @audit `univ3pool` parameter without address(0) check
1468: function getPoolId(address univ3pool) external view returns (uint64 poolId) {
```
[351](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L351) | [1343](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1343) | [1371](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1371) | [1437](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1437) | [1468](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1468)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit `operator` parameter without address(0) check
77: function setApprovalForAll(address operator, bool approved) public {
/// @audit `from` parameter without address(0) check
/// @audit `to` parameter without address(0) check
90: function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public {
/// @audit `from` parameter without address(0) check
/// @audit `to` parameter without address(0) check
128: function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public virtual {
/// @audit `owners` parameter without address(0) check
178: function balanceOfBatch(
        address[] calldata owners,
        uint256[] calldata ids
    ) public view returns (uint256[] memory balances) {
```
[77](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L77) | [90](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L90) | [128](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L128) | [178](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L178)
</details>

### [N-71] Contract/Libraries Names Do Not Match Their Filenames

According to the Solidity Style Guide, contract names should match their filenames. 
Mismatching contract names and filenames can lead to confusion and make the code harder to maintain and review.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/tokens/ERC1155Minimal.sol

10: abstract contract ERC1155 {
```
[10](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L10)
</details>

### [N-72] Presence of Unutilized Imports in the Contract

The contract contains import statements for libraries or other contracts that are not utilized within the code.
Excessive or unused imports can clutter the codebase, leading to inefficiency and potential confusion.
Consider removing any imports that are not essential to the contract's functionality.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit imported `TokenId` not used)
5: import {TokenId} from "@types/TokenId.sol";
```
[5](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L5)
</details>

### [N-73] `if`-statement can be converted to a ternary

The ternary operator provides a shorthand way to write if / else statements.
It can improve readability and reduce the number of lines of code.
Traditional `if / else` statements, particularly those spanning only a one lines, could potentially be refactored using the ternary operator.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: contracts/types/TokenId.sol

343: } else if (optionRatios < 2 ** 208) {
                optionRatios = 3;
            } else {
                optionRatios = 4;
            }
```
[343](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L343)

```solidity
File: contracts/libraries/PanopticMath.sol

120: if (tokenId.asset(legIndex) == 0) {
            legLiquidity = Math.getLiquidityForAmount0(
                uint256(0).addTickLower(tickLower).addTickUpper(tickUpper),
                amount
            );
        } else {
            legLiquidity = Math.getLiquidityForAmount1(
                uint256(0).addTickLower(tickLower).addTickUpper(tickUpper),
                amount
            );
        }
```
[120](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L120)
</details>

### [N-74] Consider using `delete` rather than assigning zero to clear values

Rather than merely setting a variable to zero, you can use the `delete` keyword to reset it to its default value.
This action is especially relevant for complex data types like arrays or mappings where the default is not necessarily zero.
Using `delete` not only provides explicit clarity that you intend to reset a variable, but it can also result in more concise and intuitive code.

Moreover, in certain contexts, delete might help save gas if optimizer off.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

627: s_accountLiquidity[positionKey_from] = 0;
630: s_accountFeesBase[positionKey_from] = 0;
```
[627](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L627) | [630](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L630)

```solidity
File: contracts/types/TokenId.sol

338: optionRatios = 0;
```
[338](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/types/TokenId.sol#L338)
</details>

### [N-75] Unnecessary Use of `override` Keyword

In Solidity version 0.8.8 and later, the use of the `override` keyword becomes superfluous when a function is overriding solely from an interface and the function isn't present in multiple base contracts.
Previously, the `override` keyword was required as an explicit indication to the compiler. However, this is no longer the case, and the extraneous use of the keyword can make the code less clean and more verbose.

Solidity documentation on [Function Overriding](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding).

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

544: function afterTokenTransfer(
        address from,
        address to,
        uint256[] memory ids,
        uint256[] memory amounts
    ) internal override {
563: function afterTokenTransfer(
        address from,
        address to,
        uint256 id,
        uint256 amount
    ) internal override {
```
[544](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L544) | [563](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L563)
</details>

### [N-76] Implement Value Comparison Checks in Setter Functions to Prevent Redundant State Updates

Setter functions should include a condition to check if the new value being assigned is different from the current value. This practice prevents redundant state changes and the emission of unnecessary events, ensuring that changes only occur when actual updates to the values are made.

This not only helps to maintain the integrity of the contract's state but also keeps the event logs cleaner and more meaningful by avoiding the recording of identical consecutive values. Such an approach can improve the clarity and efficiency of debugging and data tracking processes.

<details>
<summary><i>5 issue instances in 2 files:</i></summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit Missing `isLong` check before state change
1417: acctPremia = isLong == 1
```
[1417](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1417)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit Missing `amount` check before state change
98: balanceOf[from][id] -= amount;
/// @audit Missing `amount` check before state change
103: balanceOf[to][id] += amount;
/// @audit Missing `ids` check before state change
142: id = ids[i];
/// @audit Missing `amounts` check before state change
143: amount = amounts[i];
```
[98](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L98) | [103](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L103) | [142](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L142) | [143](https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L143)
</details>

### [N-77] Contracts should have full test coverage

It's recommended to have full test coverage for all contracts.
While 100% code coverage does not guarantee absence of bugs, it can catch simple bugs and reduce regressions during code modifications.
Moreover, to achieve full coverage, authors often have to refactor their code into more modular components, each testable separately.
This leads to lower interdependencies, and results in code that is easier to understand and audit.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: app/2023-11-panoptic

1: All files
```
[1](https://github.com/code-423n4/2023-11-panoptic/blob/main/app/2023-11-panoptic#L1)
</details>

### [N-78] Insufficient Invariant Tests for Contracts

Large or complex code bases should include invariant fuzzing tests, such as those provided by Echidna.
These tests require the identification of invariants that should not be violated under any circumstances, with the fuzzer testing various inputs and function calls to ensure these invariants always hold.
This is especially important for code with a lot of inline-assembly, complicated math, or complex interactions between contracts. Despite having 100% code coverage, bugs can still occur due to the order of operations a user performs.
Extensive and well-written invariant tests can significantly reduce this testing gap.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: app/2023-11-panoptic

1: All files
```
[1](https://github.com/code-423n4/2023-11-panoptic/blob/main/app/2023-11-panoptic#L1)
</details>

### [N-79] Implement Formal Verification Proofs to Improve Security

Formal verification offers a mathematical proof confirming that your code operates as intended and is devoid of edge cases 
that may lead to unintended behavior. By leveraging this rigorous audit technique, you not only enhance the robustness 
of your code but also strengthen the trust of stakeholders in the safety of your contract.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: app/2023-11-panoptic

1: All files
```
[1](https://github.com/code-423n4/2023-11-panoptic/blob/main/app/2023-11-panoptic#L1)
</details>

