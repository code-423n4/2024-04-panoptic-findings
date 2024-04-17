## Medium Issues


*Total <b>19</b> instances over <b>4</b> issues:*

|ID|Issue|Instances|
|-|:-|:-:|
| [M-2](#M-2) | Return values of `approve()` not checked | 4 |
| [M-3](#M-3) | Return values of `transfer()`/`transferFrom()` not checked | 2 |
| [M-4](#M-4) | Usage of `slot0` is extremely easy to manipulate | 12 |

## Low Issues


*Total <b>569</b> instances over <b>36</b> issues:*

|ID|Issue|Instances|
|-|:-|:-:|
| [L-1](#L-1) | Missing zero address check in functions with address parameters | 80 |
| [L-2](#L-2) | Use increase/decrease allowance instead of `approve()`/`safeApprove()` | 4 |
| [L-3](#L-3) | Consider implementing two-step procedure for updating protocol addresses | 4 |
| [L-4](#L-4) | Constructor / initialization function lacks parameter validation | 5 |
| [L-5](#L-5) | Contracts use infinite approvals | 4 |
| [L-6](#L-6) | Code does not follow the best practice of check-effects-interaction | 9 |
| [L-7](#L-7) | External function calls within loops | 4 |
| [L-8](#L-8) | Functions calling contracts/addresses with transfer hooks are missing reentrancy guards | 7 |
| [L-9](#L-9) | Large approvals may not work with some `ERC20` tokens | 4 |
| [L-10](#L-10) | Loss of precision in divisions | 31 |
| [L-11](#L-11) | Missing checks for state variable assignments | 23 |
| [L-12](#L-12) | Missing zero address check in constructor | 3 |
| [L-13](#L-13) | Consider some checks for `address(0)` when setting address state variables | 15 |
| [L-14](#L-14) | Multiplication on the result of a division | 4 |
| [L-15](#L-15) | Solidity version 0.8.20 or above may not work on other chains due to PUSH0 | 20 |
| [L-16](#L-16) | Some tokens may revert when large transfers are made | 2 |
| [L-17](#L-17) | Some tokens may revert when zero value transfers are made | 2 |
| [L-18](#L-18) | Subtraction may underflow if result of multiplication is too large | 36 |
| [L-19](#L-19) | Sending tokens in a for loop | 1 |
| [L-20](#L-20) | Tokens may be minted to `address(0)` | 3 |
| [L-21](#L-21) | Unsafe downcast | 122 |
| [L-22](#L-22) | Unsafe addition/multiplication in `unchecked` block | 72 |
| [L-23](#L-23) | Using zero as a parameter | 11 |
| [L-24](#L-24) | Vulnerable version of OZ contarcts is used (`4.8.3`) | 1 |
| [L-25](#L-25) | Missing zero address check in initializer | 2 |
| [L-26](#L-26) | `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()` | 2 |
| [L-27](#L-27) | Centralization Risk for trusted owners | 7 |
| [L-28](#L-28) | `decimals()` is not a part of the ERC-20 standard | 1 |
| [L-29](#L-29) | Initializers could be front-run | 1 |
| [L-30](#L-30) | `symbol()` is not a part of the ERC-20 standard | 3 |
| [L-31](#L-31) | Low level calls in solidity versions preceding 0.8.14 can result in an optimiser bug | 30 |
| [L-32](#L-32) | For loops in public or external functions should be avoided due to high gas costs and possible DOS | 3 |
| [L-33](#L-33) | Function with two (or more) array parameters missing a length check | 4 |
| [L-34](#L-34) | Library has public/external functions | 13 |
| [L-35](#L-35) | `_safeMint()` should be used rather than `_mint()` wherever possible | 1 |
| [L-36](#L-36) | int/uint passed into abi.encodePacked without casting to a string | 35 |

## Non Critical Issues


*Total <b>2220</b> instances over <b>90</b> issues:*

|ID|Issue|Instances|
|-|:-|:-:|
| [NC-1](#NC-1) | Assembly blocks should have extensive comments | 31 |
| [NC-2](#NC-2) | `abi.encodePacked()` should be replaced with `bytes.concat()` | 12 |
| [NC-3](#NC-3) | Add inline comments for unnamed variables | 2 |
| [NC-4](#NC-4) | Avoid mutating function parameters | 4 |
| [NC-5](#NC-5) | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability | 4 |
| [NC-6](#NC-6) | Complex casting | 70 |
| [NC-7](#NC-7) | Consider adding a block/deny-list | 7 |
| [NC-8](#NC-8) | Consider adding emergency-stop functionality | 4 |
| [NC-9](#NC-9) | Consider adding formal verification proofs | 1 |
| [NC-10](#NC-10) | Consider bounding input array length | 7 |
| [NC-11](#NC-11) | Consider using descriptive `constant`s when passing zero as a function argument | 62 |
| [NC-12](#NC-12) | Constant decimal values | 1 |
| [NC-13](#NC-13) | Constant redefined elsewhere | 1 |
| [NC-14](#NC-14) | Constants should be put on the left side of comparisons | 92 |
| [NC-15](#NC-15) | `Constructor` should emit an event | 4 |
| [NC-16](#NC-16) | Contract does not follow the Solidity Style Guide's suggested layout ordering | 81 |
| [NC-17](#NC-17) | Contract should expose an `interface` | 73 |
| [NC-18](#NC-18) | Contracts should have full test coverage | 1 |
| [NC-19](#NC-19) | Convert simple `if` statements to ternary expressions | 2 |
| [NC-20](#NC-20) | Events that mark critical parameter changes should contain both the old and the new value | 24 |
| [NC-21](#NC-21) | Custom errors has no error details | 34 |
| [NC-22](#NC-22) | Solidity version is different in some files | 2 |
| [NC-23](#NC-23) | Polymorphic functions make security audits more time-consuming and error-prone | 15 |
| [NC-24](#NC-24) | Duplicated `require()`/`revert()` checks should be refactored | 2 |
| [NC-25](#NC-25) | `else` block not required | 6 |
| [NC-26](#NC-26) | Empty bytes check is missing | 7 |
| [NC-27](#NC-27) | Enable IR-based code generation | 1 |
| [NC-28](#NC-28) | Enum values should be used instead of constant array indexes | 26 |
| [NC-29](#NC-29) | Events are emitted without the sender information | 8 |
| [NC-30](#NC-30) | Events may be emitted out of order due to reentrancy | 5 |
| [NC-31](#NC-31) |  Function ordering does not follow the Solidity Style Guide | 56 |
| [NC-32](#NC-32) | Functions and modifiers should be named in mixedCase style | 1 |
| [NC-33](#NC-33) | Functions with array parameters should have length checks in place | 19 |
| [NC-34](#NC-34) | High cyclomatic complexity | 3 |
| [NC-35](#NC-35) | Inconsistent spacing in comments | 95 |
| [NC-36](#NC-36) | Invalid NatSpec comment style | 7 |
| [NC-37](#NC-37) | It is best practice to use linear inheritance | 3 |
| [NC-38](#NC-38) | Lack of brace spacing | 1 |
| [NC-39](#NC-39) | Large or complicated code bases should implement invariant tests | 1 |
| [NC-40](#NC-40) | Large multiples of ten should use scientific notation | 12 |
| [NC-41](#NC-41) | Large numeric literals should use underscores for readability | 12 |
| [NC-42](#NC-42) | Long functions should be refactored into multiple, smaller, functions | 33 |
| [NC-43](#NC-43) | Magic numbers should be replaced with constants | 108 |
| [NC-44](#NC-44) | Missing NatSpec from contract/error/event/function/modifier declarations | 2 |
| [NC-45](#NC-45) | Missing NatSpec `@author` from contract declaration | 3 |
| [NC-46](#NC-46) | Missing NatSpec `@dev` from contract/event/function/modifier declarations | 171 |
| [NC-47](#NC-47) | Missing NatSpec `@notice` from contract/event/function/modifier declarations | 12 |
| [NC-48](#NC-48) | Missing NatSpec `@param` from event/function/modifier declarations | 5 |
| [NC-49](#NC-49) | Missing NatSpec `@return` from function declaration | 8 |
| [NC-50](#NC-50) | Missing NatSpec `@title` from contract declaration | 5 |
| [NC-51](#NC-51) | There is no need to initialize variables with 0 | 31 |
| [NC-52](#NC-52) | Non-assembly method available | 10 |
| [NC-53](#NC-53) | Put all system-wide constants in one file | 49 |
| [NC-54](#NC-54) | Redundant `return` statement in a function with named return variables | 21 |
| [NC-55](#NC-55) | Lines are too long | 5 |
| [NC-56](#NC-56) | Typos | 11 |
| [NC-57](#NC-57) | Unnecessary cast | 120 |
| [NC-58](#NC-58) | Unsafe conversion from unsigned to signed values | 79 |
| [NC-59](#NC-59) | Unsafe solidity low-level call can cause gas grief attack | 1 |
| [NC-60](#NC-60) | Unused `error` definition | 33 |
| [NC-61](#NC-61) | Unused arguments should be removed or implemented | 4 |
| [NC-62](#NC-62) | Unused import | 1 |
| [NC-63](#NC-63) | Unused named return | 18 |
| [NC-64](#NC-64) | Unused contract variables | 10 |
| [NC-65](#NC-65) | Consider using `delete` rather than assigning zero/false to clear values | 1 |
| [NC-66](#NC-66) | Solidity compiler version is not fixed | 20 |
| [NC-67](#NC-67) | Expressions for constant values should use `immutable` rather than `constant` | 49 |
| [NC-68](#NC-68) | Upgrade `openzeppelin` to the latest version (`5.0.2`) | 1 |
| [NC-69](#NC-69) | Use the latest solidity version for deployment (`0.8.25`) | 20 |
| [NC-70](#NC-70) | Use the Modern Upgradeable Contract Paradigm | 7 |
| [NC-71](#NC-71) | Consider using modifiers for address control | 8 |
| [NC-72](#NC-72) | Use of `override` is unnecessary | 2 |
| [NC-73](#NC-73) | Use scientific notation (e.g. `1e18`) rather than exponentiation (e.g. `10**18`) | 1 |
| [NC-74](#NC-74) | Use a struct to encapsulate multiple function parameters | 3 |
| [NC-75](#NC-75) | Use `type(X).max` instead of constant formulas like `2**n` | 34 |
| [NC-76](#NC-76) | Visibility of state variables is not explicitly defined | 8 |
| [NC-77](#NC-77) | Whitespace in Expressions | 19 |
| [NC-78](#NC-78) | Common functions should be refactored to a common base contract | 4 |
| [NC-79](#NC-79) | Names of `private`/`internal` functions should be prefixed with an underscore | 104 |
| [NC-80](#NC-80) | Names of `private`/`internal` state variables should be prefixed with an underscore | 93 |
| [NC-81](#NC-81) | Internal function calls within for loops | 3 |
| [NC-82](#NC-82) |  `require()` / `revert()` statements should have descriptive reason strings | 74 |
| [NC-83](#NC-83) | Variables should be named in mixedCase style | 2 |
| [NC-84](#NC-84) | Event is missing `indexed` fields | 12 |
| [NC-85](#NC-85) | Functions not used internally could be marked `external` | 13 |
| [NC-86](#NC-86) | Default address(0) can be returned | 2 |
| [NC-87](#NC-87) | Consider moving duplicated strings to constants | 5 |
| [NC-88](#NC-88) | Don't only depend on Solidity's arithmetic ordering | 24 |
| [NC-89](#NC-89) | Payable functions which do not interact with the native token should not be payable | 1 |
| [NC-90](#NC-90) | Use `using` keyword when using specific imports rather than calling the specific import directly | 171 |

## Medium Issues

<a name="M-2"></a> 
### [M-2] Return values of `approve()` not checked
Not all IERC20 implementations `revert()` when there's a failure in `approve()`. The function signature has a boolean return value and they indicate errors that way instead. By not checking the return value, operations that should have marked as failed, may potentially go through without actually approving anything

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/libraries/InteractionHelper.sol

32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L33), [36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L37)]



<a name="M-3"></a> 
### [M-3] Return values of `transfer()`/`transferFrom()` not checked
Not all ERC20 implementations `revert()` when there's a failure in `transfer()` or `transferFrom()`. The function signature has a boolean return value and they indicate errors that way instead. By not checking the return value, operations that should have marked as failed, may potentially go through without actually transfer anything.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

333:         return ERC20Minimal.transfer(recipient, amount);

352:         return ERC20Minimal.transferFrom(from, to, amount);

```
*Github:* [[333](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L333), [352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L352)]



<a name="M-4"></a> 
### [M-4] Usage of `slot0` is extremely easy to manipulate

<details>
<summary>
There are <b>12</b> instances (click to show):
</summary>

```solidity
File: ./contracts/PanopticFactory.sol

341:         (uint160 currentSqrtPriceX96, , , , , , ) = v3Pool.slot0();

```
*Github:* [[341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L341)]


```solidity
File: ./contracts/PanopticPool.sol

304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

339:         (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();

387:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

523:         (, , uint16 observationIndex, uint16 observationCardinality, , , ) = s_univ3pool.slot0();

904:         ) = _univ3pool.slot0();

1032:             (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

1094:             (, finalTick, , , , , ) = s_univ3pool.slot0();

1202:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

1598:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

```
*Github:* [[304](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L304), [339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L339), [387](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L387), [523](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L523), [904](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L904), [1032](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1032), [1094](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1094), [1202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1202), [1598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1598)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

725:         (, int24 currentTick, , , , , ) = univ3pool.slot0();

788:                 (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

```
*Github:* [[725](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L725), [788](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L788)]


</details>



## Low Issues

<a name="L-1"></a> 
### [L-1] Missing zero address check in functions with address parameters
Adding a zero address check for each address type parameter can prevent errors.

<details>
<summary>
There are <b>80</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit missing zero check for `token0`
/// @audit missing zero check for `token1`
/// @audit missing zero check for `panopticPool`
221:     function startToken(
             bool underlyingIsToken0,
             address token0,
             address token1,
             uint24 fee,
             PanopticPool panopticPool
         ) external {
             // fails if already initialized

/// @audit missing zero check for `recipient`
323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions

/// @audit missing zero check for `to`
341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions

/// @audit missing zero check for ``
392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {
             return type(uint104).max;

/// @audit missing zero check for `receiver`
417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
             if (assets > type(uint104).max) revert Errors.DepositTooLarge();

/// @audit missing zero check for ``
444:     function maxMint(address) external view returns (uint256 maxShares) {
             unchecked {

/// @audit missing zero check for `receiver`
477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {
             assets = previewMint(shares);

/// @audit missing zero check for `receiver`
531:     function withdraw(
             uint256 assets,
             address receiver,
             address owner
         ) external returns (uint256 shares) {
             if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

/// @audit missing zero check for `receiver`
591:     function redeem(
             uint256 shares,
             address receiver,
             address owner
         ) external returns (uint256 assets) {
             if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

/// @audit missing zero check for `delegator`
/// @audit missing zero check for `delegatee`
864:     function delegate(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {
             /*

/// @audit missing zero check for `delegatee`
898:     /// @notice Refunds delegated tokens back to the protocol
         /// @dev Assumes that `delegatee` has enough money to pay for the refund

/// @audit missing zero check for `delegatee`
907:     /// @notice Revoke previously delegated shares. The opposite of 'delegate'.
         /// @param delegator The delegator to send shares *to* (because we are revoking - opposite when we delegate).

/// @audit missing zero check for `delegator`
/// @audit missing zero check for `delegatee`
917:                 ┌────────┐
                     │Panoptic│
                     │Pool    │
                     └────┬───┘
                          │(1) convert 'assets' to shares (this ERC20 contract)

/// @audit missing zero check for `refunder`
/// @audit missing zero check for `refundee`
980:                 _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));
                 }
             }
         }
     
         /*//////////////////////////////////////////////////////////////

/// @audit missing zero check for `optionOwner`
1002:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
                  int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
      
                  // constrict premium to only assets not belonging to PLPs (i.e premium paid by sellers or collected from the pool earlier)

/// @audit missing zero check for `optionOwner`
1051:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
                  int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
      
                  // add premium to be paid/collected on position close
                  int256 tokenToPay = -realizedPremium;

/// @audit missing zero check for `user`
1147:         tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);
          }
      
          /// @notice Get the collateral status/margin details of an account/user.
          /// NOTE: It's up to the caller to confirm from the returned result that the account has enough collateral.
          /// @dev This can be used to check the health: how many tokens a user has compared to the margin threshold.

/// @audit missing zero check for `user`
1167:         // if the account has active options, compute the required collateral to keep account in good health
              if (positionBalanceArray.length > 0) {
                  // get all collateral required for the incoming list of positions
                  tokenRequired = _getTotalRequiredCollateral(atTick, positionBalanceArray);

```
*Github:* [[221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L221), [323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L341), [392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392), [417](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L417), [444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444), [477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L477), [531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L531), [591](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L591), [864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L864), [898](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L898), [907](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L907), [917](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L917), [980](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L980), [1002](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1002), [1051](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1051), [1147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1147), [1167](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1167)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit missing zero check for `_owner`
134:     function initialize(address _owner) public {

/// @audit missing zero check for `newOwner`
147:     function transferOwnership(address newOwner) external {

/// @audit missing zero check for `token0`
/// @audit missing zero check for `token1`
210:     function deployNewPool(
             address token0,
             address token1,
             uint24 fee,
             bytes32 salt
         ) external returns (PanopticPool newPoolContract) {

/// @audit missing zero check for `token0`
/// @audit missing zero check for `token1`
335:     function _mintFullRange(
             IUniswapV3Pool v3Pool,
             address token0,
             address token1,
             uint24 fee
         ) internal returns (uint256, uint256) {

/// @audit missing zero check for `univ3pool`
420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {
             return s_getPanopticPool[univ3pool];

```
*Github:* [[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L134), [147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L147), [210](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L210), [335](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L335), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L420)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit missing zero check for `token0`
/// @audit missing zero check for `token1`
/// @audit missing zero check for `collateralTracker0`
/// @audit missing zero check for `collateralTracker1`
291:     function startPool(
             IUniswapV3Pool _univ3pool,
             address token0,
             address token1,
             CollateralTracker collateralTracker0,
             CollateralTracker collateralTracker1
         ) external {

/// @audit missing zero check for `user`
352:     function optionPositionBalance(
             address user,
             TokenId tokenId
         ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

/// @audit missing zero check for `user`
381:     function calculateAccumulatedFeesBatch(
             address user,
             bool includePendingPremium,
             TokenId[] calldata positionIdList
         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

/// @audit missing zero check for `user`
410:     function calculatePortfolioValue(
             address user,
             int24 atTick,
             TokenId[] calldata positionIdList
         ) external view returns (int256 value0, int256 value1) {

/// @audit missing zero check for `user`
429:     function _calculateAccumulatedPremia(
             address user,
             TokenId[] calldata positionIdList,
             bool computeAllPremia,
             bool includePendingPremium,
             int24 atTick
         ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

/// @audit missing zero check for `owner`
794:     function _burnAllOptionsFrom(
             address owner,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool commitLongSettled,
             TokenId[] calldata positionIdList
         ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

/// @audit missing zero check for `owner`
826:     function _burnOptions(
             bool commitLongSettled,
             TokenId tokenId,
             address owner,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

/// @audit missing zero check for `owner`
859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

/// @audit missing zero check for `user`
887:     function _validateSolvency(
             address user,
             TokenId[] calldata positionIdList,
             uint256 buffer
         ) internal view returns (uint256 medianData) {

/// @audit missing zero check for `owner`
955:     function _burnAndHandleExercise(
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
         {

/// @audit missing zero check for `liquidatee`
1017:     function liquidate(
              TokenId[] calldata positionIdListLiquidator,
              address liquidatee,
              LeftRightUnsigned delegations,
              TokenId[] calldata positionIdList
          ) external {

/// @audit missing zero check for `account`
1179:     function forceExercise(
              address account,
              TokenId[] calldata touchedId,
              TokenId[] calldata positionIdListExercisee,
              TokenId[] calldata positionIdListExercisor
          ) external {

/// @audit missing zero check for `account`
1290:     function _checkSolvencyAtTick(
              address account,
              TokenId[] calldata positionIdList,
              int24 currentTick,
              int24 atTick,
              uint256 buffer
          ) internal view returns (bool) {

/// @audit missing zero check for `account`
1367:     function _validatePositionList(
              address account,
              TokenId[] calldata positionIdList,
              uint256 offset
          ) internal view {
              uint256 pLength;

/// @audit missing zero check for `account`
1405:     function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {
              // Get the current position hash value (fingerprint of all pre-existing positions created by '_account')

/// @audit missing zero check for `user`
1444:     function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {
              _numberOfPositions = (s_positionsHash[user] >> 248);

/// @audit missing zero check for `owner`
1503:     function _getPremia(
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
          {
              uint256 numLegs = tokenId.countLegs();

/// @audit missing zero check for `owner`
1587:     function settleLongPremium(
              TokenId[] calldata positionIdList,
              address owner,
              uint256 legIndex
          ) external {
              _validatePositionList(owner, positionIdList, 0);

/// @audit missing zero check for `owner`
1833:     function _updateSettlementPostBurn(
              address owner,
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize,
              bool commitLongSettled
          ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
              uint256 numLegs = tokenId.countLegs();

```
*Github:* [[291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L291), [352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L352), [381](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L381), [410](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L410), [429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L429), [794](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L794), [826](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L826), [859](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L859), [887](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L887), [955](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L955), [1017](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1017), [1179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1179), [1290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1290), [1367](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1367), [1405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1405), [1444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1444), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1503), [1587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1587), [1833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1833)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit missing zero check for `token0`
/// @audit missing zero check for `token1`
361:         // if poolId == 0, we have a bit on the left set if it was initialized, so this will still return properly
             if (s_AddrToPoolIdData[univ3pool] != 0) return;

/// @audit missing zero check for `from`
/// @audit missing zero check for `to`
555:         super.safeTransferFrom(from, to, id, amount, data);
         }
     
         /// @notice Transfer multiple tokens from one user to another
         /// @dev supports token approvals
         /// @dev ids and amounts must be of equal length

/// @audit missing zero check for `from`
/// @audit missing zero check for `to`
583:         // transfer the token (note that all state updates are completed before reentrancy is possible)
             super.safeBatchTransferFrom(from, to, ids, amounts, data);
         }
     
         /// @notice update user position data following a token transfer
         /// @dev token transfers are only allowed if you transfer your entire liquidity of a given chunk and the recipient has none

/// @audit missing zero check for `from`
/// @audit missing zero check for `to`
611:             bytes32 positionKey_from = keccak256(
                     abi.encodePacked(
                         address(univ3pool),

/// @audit missing zero check for `univ3pool`
786:             // this is simply a convenience feature, and should be treated as such
                 if ((itm0 != 0) && (itm1 != 0)) {
                     (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

/// @audit missing zero check for `univ3pool`
897:                     // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,
                         // allowing the corresponding short liquidity to be removed
                         _leg = _isBurn ? numLegs - leg - 1 : leg;
                     }
     
                     // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick

/// @audit missing zero check for `univ3pool`
1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))
                      )
                      .toLeftSlot(
                          int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))
                      )
                  : LeftRightSigned

/// @audit missing zero check for `univ3pool`
1221:     /// @param liquidityChunk the chunk of liquidity to burn given by tick upper, tick lower, and its size
          /// @param univ3pool the Uniswap v3 pool to burn liquidity in/from

/// @audit missing zero check for `univ3pool`
1252:     /// @param movedInLeg how much liquidity has been moved between msg.sender and Uniswap before this function call
          /// @param isLong whether the leg in question is long (=1) or short (=0)
          /// @return collectedChunk the incoming amount collected with potentially whatever is collected in this function added to it

/// @audit missing zero check for `univ3pool`
1288:                 uint128(amountToCollect.rightSlot()),
                      uint128(amountToCollect.leftSlot())
                  );
      
                  // moved will be negative if the leg was long (funds left the caller, don't count it in collected fees)
                  uint128 collected0;
                  uint128 collected1;
                  unchecked {
                      collected0 = movedInLeg.rightSlot() < 0

/// @audit missing zero check for `univ3pool`
/// @audit missing zero check for `owner`
1445:     /// @param atTick The current tick. Set atTick < type(int24).max = 8388608 to get latest premium up to the current block
          /// @param isLong whether the position is long (=1) or short (=0)
          /// @return premiumToken0 The amount of premium (per liquidity X64) for token0 = sum (feeGrowthLast0X128) over every block where the position has been touched

/// @audit missing zero check for `owner`
1479:                     // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])
                          LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(
                              _univ3pool,
                              atTick,
                              _tickLower,
                              _tickUpper,

/// @audit missing zero check for `univ3pool`
/// @audit missing zero check for `owner`
1570: 

/// @audit missing zero check for `univ3pool`
1570: 

```
*Github:* [[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L361), [555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L555), [583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L583), [611](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L611), [786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L786), [897](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L897), [1169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1169), [1221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1221), [1252](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1252), [1288](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1288), [1445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1445), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1479), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570)]


```solidity
File: ./contracts/libraries/CallbackLib.sol

/// @audit missing zero check for `sender`
/// @audit missing zero check for `factory`
30:     function validateCallback(
            address sender,
            IUniswapV3Factory factory,
            PoolFeatures memory features
        ) internal view {

```
*Github:* [[30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L30)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

/// @audit missing zero check for `univ3pool`
104:         // extract the amount of AMM fees collected within the liquidity chunk`
             // note: the fee variables are *per unit of liquidity*; so more "rate" variables
             (
                 uint256 ammFeesPerLiqToken0X128,

/// @audit missing zero check for `univ3pool`
135:     ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
             // Get feesGrowths from the option position's lower+upper ticks
             // lowerOut0: For token0: fee growth per unit of liquidity on the _other_ side of tickLower (relative to currentTick)
             // only has relative meaning, not absolute — the value depends on when the tick is initialized

```
*Github:* [[104](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L104), [135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L135)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit missing zero check for `univ3pool`
125:     function computeMedianObservedPrice(
             IUniswapV3Pool univ3pool,
             uint256 observationIndex,
             uint256 observationCardinality,
             uint256 cardinality,
             uint256 period
         ) external view returns (int24) {
             unchecked {

/// @audit missing zero check for `univ3pool`
168:     function computeInternalMedian(
             uint256 observationIndex,
             uint256 observationCardinality,
             uint256 period,
             uint256 medianData,
             IUniswapV3Pool univ3pool
         ) external view returns (int24 medianTick, uint256 updatedMedianData) {
             unchecked {

/// @audit missing zero check for `univ3pool`
241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {
             uint32[] memory secondsAgos = new uint32[](20);

/// @audit missing zero check for `liquidatee`
/// @audit missing zero check for `collateral0`
/// @audit missing zero check for `collateral1`
770:         TokenId[] memory positionIdList,
             LeftRightSigned[4][] memory premiasByLeg,
             LeftRightSigned collateralRemaining,
             CollateralTracker collateral0,
             CollateralTracker collateral1,
             uint160 sqrtPriceX96Final,
             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
         ) external returns (int256, int256) {
             unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;

/// @audit missing zero check for `collateral0`
/// @audit missing zero check for `collateral1`
919:         LeftRightSigned refundValues,
             int24 atTick,
             CollateralTracker collateral0,
             CollateralTracker collateral1
         ) external view returns (LeftRightSigned) {
             uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);
             unchecked {
                 // if the refunder lacks sufficient token0 to pay back the refundee, have them pay back the equivalent value in token1

```
*Github:* [[125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L125), [168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L168), [241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L241), [770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L770), [919](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L919)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

/// @audit missing zero check for `token`
/// @audit missing zero check for `from`
/// @audit missing zero check for `to`
21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

/// @audit missing zero check for `token`
/// @audit missing zero check for `to`
52:     function safeTransfer(address token, address to, uint256 amount) internal {

```
*Github:* [[21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L21), [52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L52)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

/// @audit missing zero check for `operator`
81:     function setApprovalForAll(address operator, bool approved) public {

/// @audit missing zero check for `from`
94:     function safeTransferFrom(
            address from,
            address to,
            uint256 id,
            uint256 amount,
            bytes calldata data
        ) public virtual {

/// @audit missing zero check for `from`
130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {

/// @audit missing zero check for `from`
236:     function _burn(address from, uint256 id, uint256 amount) internal {

```
*Github:* [[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L81), [94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L94), [130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L130), [236](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L236)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

/// @audit missing zero check for `spender`
49:     function approve(address spender, uint256 amount) public returns (bool) {

/// @audit missing zero check for `to`
61:     function transfer(address to, uint256 amount) public virtual returns (bool) {

/// @audit missing zero check for `from`
/// @audit missing zero check for `to`
81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

/// @audit missing zero check for `from`
/// @audit missing zero check for `to`
103:     function _transferFrom(address from, address to, uint256 amount) internal {

/// @audit missing zero check for `to`
122:     function _mint(address to, uint256 amount) internal {

/// @audit missing zero check for `from`
136:     function _burn(address from, uint256 amount) internal {

```
*Github:* [[49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L49), [61](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L61), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L81), [103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L103), [122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L122), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L136)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

/// @audit missing zero check for `deployer`
/// @audit missing zero check for `newPoolContract`
/// @audit missing zero check for `token0`
/// @audit missing zero check for `token1`
13:     function issueNFT(

```
*Github:* [[13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L13)]


```solidity
File: ./contracts/tokens/interfaces/IERC20Partial.sol

/// @audit missing zero check for `account`
16:     function balanceOf(address account) external view returns (uint256);

/// @audit missing zero check for `spender`
22:     function approve(address spender, uint256 amount) external;

/// @audit missing zero check for `to`
27:     function transfer(address to, uint256 amount) external;

```
*Github:* [[16](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L16), [22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L22), [27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L27)]


</details>


<a name="L-2"></a> 
### [L-2] Use increase/decrease allowance instead of `approve()`/`safeApprove()`
Changing an allowance with approve() brings the risk that someone may use both the old and the new allowance by unfortunate transaction ordering. Refer to [ERC20 API: An Attack Vector on the Approve/TransferFrom Methods](https://docs.google.com/document/d/1YLPtQxZu1UAvO9cZ1O2RPXBbT0mooh4DYKjA_jp-RLM). It is recommended to use the `increaseAllowance()`/`decreaseAllowance()` to avoid this problem.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/libraries/InteractionHelper.sol

32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L33), [36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L37)]



<a name="L-3"></a> 
### [L-3] Consider implementing two-step procedure for updating protocol addresses
A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must "accept" the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement [EIP-165](https://eips.ethereum.org/EIPS/eip-165), and to have the "set" functions ensure that the recipient is of the right interface type.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `s_underlyingToken`
/// @audit `s_panopticPool`
/// @audit `s_univ3token0`
/// @audit `s_univ3token1`
221:     function startToken(
             bool underlyingIsToken0,
             address token0,
             address token1,
             uint24 fee,
             PanopticPool panopticPool
         ) external {
             // fails if already initialized

```
*Github:* [[221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L221)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `s_owner`
147:     function transferOwnership(address newOwner) external {

/// @audit `s_getPanopticPool`
210:     function deployNewPool(
             address token0,
             address token1,
             uint24 fee,
             bytes32 salt
         ) external returns (PanopticPool newPoolContract) {

```
*Github:* [[147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L147), [210](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L210)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `s_univ3pool`
/// @audit `s_collateralToken0`
/// @audit `s_collateralToken1`
291:     function startPool(
             IUniswapV3Pool _univ3pool,
             address token0,
             address token1,
             CollateralTracker collateralTracker0,
             CollateralTracker collateralTracker1
         ) external {

```
*Github:* [[291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L291)]



<a name="L-4"></a> 
### [L-4] Constructor / initialization function lacks parameter validation
Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

*There are <b>5</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `_commissionFee` not validated
/// @audit `_buyerCollateralRatio` not validated
/// @audit `_forceExerciseCost` not validated
/// @audit `_targetPoolUtilization` not validated
/// @audit `_saturatedPoolUtilization` not validated
/// @audit `_ITMSpreadMultiplier` not validated
178:     constructor(

```
*Github:* [[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `_WETH9` not validated
/// @audit `_SFPM` not validated
/// @audit `_univ3Factory` not validated
/// @audit `_donorNFT` not validated
/// @audit `_poolReference` not validated
/// @audit `_collateralReference` not validated
115:     constructor(

/// @audit `_owner` not validated
134:     function initialize(address _owner) public {

```
*Github:* [[115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L115), [134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L134)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `_sfpm` not validated
280:     constructor(SemiFungiblePositionManager _sfpm) {

```
*Github:* [[280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L280)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `_factory` not validated
355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

```
*Github:* [[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L355)]



<a name="L-5"></a> 
### [L-5] Contracts use infinite approvals
Infinite approvals on external contracts can be dangerous if the target becomes compromised. See [here](https://revoke.cash/exploits) for a list of approval exploits. The following contracts are vulnerable to such attacks since they have no functionality to revoke the approval (call approve with amount 0). Consider enabling the contract to revoke approval in emergency situations.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/libraries/InteractionHelper.sol

32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L33), [36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L37)]



<a name="L-6"></a> 
### [L-6] Code does not follow the best practice of check-effects-interaction
Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

*There are <b>9</b> instances of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `.getPool(...)` is called on line 226
/// @audit `.initializeAMMPool(...)` is called on line 233
/// @audit `.cloneDeterministic(...)` is called on line 237
/// @audit `.startToken(...)` is called on line 248
/// @audit `.startToken(...)` is called on line 249
/// @audit `.startPool(...)` is called on line 251
253:         s_getPanopticPool[v3Pool] = newPoolContract;

```
*Github:* [[253](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L253)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `.slot0(...)` is called on line 304
308:             s_miniMedian =

/// @audit `.slot0(...)` is called on line 304
318:         s_collateralToken0 = collateralTracker0;

/// @audit `.slot0(...)` is called on line 304
319:         s_collateralToken1 = collateralTracker1;

/// @audit `.slot0(...)` is called on line 523
533:         if (medianData != 0) s_miniMedian = medianData;

/// @audit `.getPoolId(...)` is called on line 633
654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned

/// @audit `.getPoolId(...)` is called on line 633
664:         if (medianData != 0) s_miniMedian = medianData;

/// @audit `.slot0(...)` is called on line 1598
/// @audit `.getAccountPremium(...)` is called on line 1605
/// @audit `.exercise(...)` is called on line 1639
/// @audit `.exercise(...)` is called on line 1640
1650:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(

/// @audit `.getAccountPremium(...)` is called on line 1707
1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned

```
*Github:* [[308](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L308), [318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L318), [319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L319), [533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L533), [654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L654), [664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L664), [1650](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1650), [1725](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1725)]



<a name="L-7"></a> 
### [L-7] External function calls within loops
Calling external functions within loops can easily result in insufficient gas. This greatly increases the likelihood of transaction failures, DOS attacks, and other unexpected actions. It is recommended to limit the number of loops within loops that call external functions, and to limit the gas line for each external call.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `.predictDeterministicAddress(...)`
305:                 POOL_REFERENCE.predictDeterministicAddress(salt)

```
*Github:* [[305](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L305)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `.getAccountPremium(...)`
751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

/// @audit `.getAccountPremium(...)`
1707:                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(

```
*Github:* [[751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L751), [1707](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1707)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit `.observations(...)`
138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(

```
*Github:* [[138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L138)]



<a name="L-8"></a> 
### [L-8] Functions calling contracts/addresses with transfer hooks are missing reentrancy guards
While adherence to the check-effects-interaction pattern is commendable, the absence of a reentrancy guard in functions, especially where transfer hooks might be present, can expose the protocol users to risks of read-only reentrancies. Such reentrancy vulnerabilities can be exploited to execute malicious actions even without altering the contract state. Without a reentrancy guard, the only potential mitigation would be to blocklist the entire protocol - an extreme and disruptive measure. Therefore, incorporating a reentrancy guard into these functions is vital to bolster security, as it helps protect against both traditional reentrancy attacks and read-only reentrancies, ensuring robust and safe protocol operations.

*There are <b>7</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions
             // if they do: we don't want them sending panoptic pool shares to others
             // as this would reduce their amount of collateral against the opened positions
     
             if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();
     
             return ERC20Minimal.transferFrom(from, to, amount);

```
*Github:* [[341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L341)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

450:         // Transform the amount to pay to uint256 (take positive one from amount0 and amount1)
             // the pool will always pass one delta with a positive sign and one with a negative sign or zero,
             // so this logic always picks the correct delta to pay
             uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);
     
             // Pay the required token from the payer to the caller of this contract
             SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

583:         // transfer the token (note that all state updates are completed before reentrancy is possible)
             super.safeBatchTransferFrom(from, to, ids, amounts, data);
         }
     
         /// @notice update user position data following a token transfer
         /// @dev token transfers are only allowed if you transfer your entire liquidity of a given chunk and the recipient has none
         /// @param from The address of the sender
         /// @param to The address of the recipient
         /// @param id The tokenId being transferred'
         /// @param amount The amount of the token being transferred
         function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

```
*Github:* [[450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L450), [583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L583)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

94:     function safeTransferFrom(
            address from,
            address to,
            uint256 id,
            uint256 amount,
            bytes calldata data
        ) public virtual {
            if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
    
            balanceOf[from][id] -= amount;
    
            // balance will never overflow
            unchecked {
                balanceOf[to][id] += amount;
            }
    
            emit TransferSingle(msg.sender, from, to, id, amount);

130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {
             if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
     
             // Storing these outside the loop saves ~15 gas per iteration.
             uint256 id;
             uint256 amount;
     
             for (uint256 i = 0; i < ids.length; ) {
                 id = ids[i];
                 amount = amounts[i];
     
                 balanceOf[from][id] -= amount;
     
                 // balance will never overflow
                 unchecked {
                     balanceOf[to][id] += amount;
                 }
     
                 // An array can't have a total length
                 // larger than the max uint256 value.
                 unchecked {
                     ++i;
                 }
             }
     
             emit TransferBatch(msg.sender, from, to, ids, amounts);

```
*Github:* [[94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L94), [130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L130)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

61:     function transfer(address to, uint256 amount) public virtual returns (bool) {
            balanceOf[msg.sender] -= amount;
    
            // Cannot overflow because the sum of all user
            // balances can't exceed the max uint256 value.
            unchecked {
                balanceOf[to] += amount;
            }
    
            emit Transfer(msg.sender, to, amount);

81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
            uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.
    
            if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
    
            balanceOf[from] -= amount;
    
            // Cannot overflow because the sum of all user
            // balances can't exceed the max uint256 value.
            unchecked {
                balanceOf[to] += amount;
            }
    
            emit Transfer(from, to, amount);

```
*Github:* [[61](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L61), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L81)]



<a name="L-9"></a> 
### [L-9] Large approvals may not work with some `ERC20` tokens
Not all `IERC20` implementations are totally compliant, and some (e.g `UNI`, `COMP`) may fail if the valued passed to `approve` is larger than `uint96`. If the approval amount is `type(uint256).max`, which may cause issues with systems that expect the value passed to approve to be reflected in the allowances mapping.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/libraries/InteractionHelper.sol

32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L33), [36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L37)]



<a name="L-10"></a> 
### [L-10] Loss of precision in divisions
Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator.

<details>
<summary>
There are <b>31</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

743:             return int256((s_inAMM * DECIMALS) / totalAssets());

797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

1121:                     uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,

1409:                             (tickUpper - strike) + (strike - tickLower)

1571:                     ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)

1572:                     : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

```
*Github:* [[262](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L262), [446](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L446), [677](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L677), [743](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L743), [797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L797), [1121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1121), [1409](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1409), [1571](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1571), [1572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1572)]


```solidity
File: ./contracts/PanopticFactory.sol

392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```
*Github:* [[392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L392)]


```solidity
File: ./contracts/PanopticPool.sol

1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

```
*Github:* [[1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

228:               s_accountPremiumOwed += feeGrowthX128 * R * (1 + ν*R/N) / R

271:                                 = ∆feeGrowthX128 * t * (T - R + ν*R^2/T) / N 

272:                                 = ∆feeGrowthX128 * t * (N + ν*R^2/T) / N

```
*Github:* [[228](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L228), [271](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L271), [272](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L272)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

62:             return (poolId & TICKSPACING_MASK) + (uint48(poolId) + 1);

107:                     ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)

108:                     : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);

178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)

223:                     newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));

346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

```
*Github:* [[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L62), [107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L107), [108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L108), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L178), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L179), [188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L188), [223](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L223), [346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L346), [347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L347)]


```solidity
File: ./contracts/types/TokenId.sol

212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

521:                     if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {

589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {

```
*Github:* [[212](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L212), [229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L229), [246](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L246), [263](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L263), [281](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L281), [406](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L406), [521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L521), [589](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L589)]


</details>


<a name="L-11"></a> 
### [L-11] Missing checks for state variable assignments
There are some missing checks in these functions, and this could lead to unexpected scenarios. Consider always adding a sanity check for state variables.

<details>
<summary>
There are <b>23</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `_commissionFee`
187:         COMMISSION_FEE = _commissionFee;

/// @audit `_sellerCollateralRatio`
188:         SELLER_COLLATERAL_RATIO = _sellerCollateralRatio;

/// @audit `_buyerCollateralRatio`
189:         BUYER_COLLATERAL_RATIO = _buyerCollateralRatio;

/// @audit `_forceExerciseCost`
190:         FORCE_EXERCISE_COST = _forceExerciseCost;

/// @audit `_targetPoolUtilization`
191:         TARGET_POOL_UTIL = _targetPoolUtilization;

/// @audit `_saturatedPoolUtilization`
192:         SATURATED_POOL_UTIL = _saturatedPoolUtilization;

/// @audit `_ITMSpreadMultiplier`
193:         ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;

/// @audit `panopticPool`
244:         s_panopticPool = panopticPool;

/// @audit `token0`
254:         s_univ3token0 = token0;

/// @audit `token1`
255:         s_univ3token1 = token1;

/// @audit `underlyingIsToken0`
258:         s_underlyingIsToken0 = underlyingIsToken0;

```
*Github:* [[187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L187), [188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L188), [189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L189), [190](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L190), [191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L191), [192](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L192), [193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L193), [244](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L244), [254](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L254), [255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L255), [258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L258)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `_WETH9`
123:         WETH = _WETH9;

/// @audit `_SFPM`
124:         SFPM = _SFPM;

/// @audit `_donorNFT`
125:         DONOR_NFT = _donorNFT;

/// @audit `_univ3Factory`
127:         UNIV3_FACTORY = _univ3Factory;

/// @audit `_poolReference`
128:         POOL_REFERENCE = _poolReference;

/// @audit `_collateralReference`
129:         COLLATERAL_REFERENCE = _collateralReference;

/// @audit `_owner`
136:             s_owner = _owner;

/// @audit `newOwner`
152:         s_owner = newOwner;

```
*Github:* [[123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L123), [124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L124), [125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L125), [127](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L127), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L128), [129](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L129), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L136), [152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L152)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `_sfpm`
281:         SFPM = _sfpm;

/// @audit `collateralTracker0`
318:         s_collateralToken0 = collateralTracker0;

/// @audit `collateralTracker1`
319:         s_collateralToken1 = collateralTracker1;

```
*Github:* [[281](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L281), [318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L318), [319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L319)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `_factory`
357:         // return if the pool has already been initialized in SFPM

```
*Github:* [[357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L357)]


</details>


<a name="L-12"></a> 
### [L-12] Missing zero address check in constructor
Constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a checking, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could be due to an error or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it will be irretrievable. It's therefore crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

/// @audit missing zero check for `_WETH9`
/// @audit missing zero check for `_SFPM`
/// @audit missing zero check for `_univ3Factory`
/// @audit missing zero check for `_donorNFT`
/// @audit missing zero check for `_poolReference`
/// @audit missing zero check for `_collateralReference`
115:     constructor(
             address _WETH9,
             SemiFungiblePositionManager _SFPM,
             IUniswapV3Factory _univ3Factory,
             IDonorNFT _donorNFT,
             address _poolReference,
             address _collateralReference
         ) {

```
*Github:* [[115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L115)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit missing zero check for `_sfpm`
280:     constructor(SemiFungiblePositionManager _sfpm) {

```
*Github:* [[280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L280)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit missing zero check for `_factory`
355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

```
*Github:* [[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L355)]



<a name="L-13"></a> 
### [L-13] Consider some checks for `address(0)` when setting address state variables
Check for zero-address to avoid the risk of setting `address(0)` for state variables after an update.

<details>
<summary>
There are <b>15</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `panopticPool`
244:         s_panopticPool = panopticPool;

/// @audit `token0`
254:         s_univ3token0 = token0;

/// @audit `token1`
255:         s_univ3token1 = token1;

```
*Github:* [[244](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L244), [254](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L254), [255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L255)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `_WETH9`
123:         WETH = _WETH9;

/// @audit `_SFPM`
124:         SFPM = _SFPM;

/// @audit `_donorNFT`
125:         DONOR_NFT = _donorNFT;

/// @audit `_univ3Factory`
127:         UNIV3_FACTORY = _univ3Factory;

/// @audit `_poolReference`
128:         POOL_REFERENCE = _poolReference;

/// @audit `_collateralReference`
129:         COLLATERAL_REFERENCE = _collateralReference;

/// @audit `_owner`
136:             s_owner = _owner;

/// @audit `newOwner`
152:         s_owner = newOwner;

```
*Github:* [[123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L123), [124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L124), [125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L125), [127](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L127), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L128), [129](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L129), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L136), [152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L152)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `_sfpm`
281:         SFPM = _sfpm;

/// @audit `collateralTracker0`
318:         s_collateralToken0 = collateralTracker0;

/// @audit `collateralTracker1`
319:         s_collateralToken1 = collateralTracker1;

```
*Github:* [[281](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L281), [318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L318), [319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L319)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `_factory`
357:         // return if the pool has already been initialized in SFPM

```
*Github:* [[357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L357)]


</details>


<a name="L-14"></a> 
### [L-14] Multiplication on the result of a division
Dividing an integer by another integer will often result in loss of precision. When the result is multiplied by another number, the loss of precision is magnified, often to material magnitudes. `(X / Z) * Y` should be re-written as `(X * Y) / Z`

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

1614:                     Put side of a short strangle, BPR = 100% - (100% - SCR/2)*(price/strike)

```
*Github:* [[1614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1614)]


```solidity
File: ./contracts/PanopticFactory.sol

392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```
*Github:* [[392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L392)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

```
*Github:* [[346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L346), [347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L347)]



<a name="L-15"></a> 
### [L-15] Solidity version 0.8.20 or above may not work on other chains due to PUSH0
Solidity version 0.8.20 or above uses the new [Shanghai EVM](https://blog.soliditylang.org/2023/05/10/solidity-0.8.20-release-announcement/#important-note) which introduces the PUSH0 opcode. This op code may not yet be implemented on all evm-chains or Layer2s, so deployment on these chains will fail. Consider using an earlier solidity version.

<details>
<summary>
There are <b>20</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L2)]


```solidity
File: ./contracts/PanopticFactory.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L2)]


```solidity
File: ./contracts/PanopticPool.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L2)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L2)]


```solidity
File: ./contracts/libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L2)]


```solidity
File: ./contracts/libraries/Constants.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L2)]


```solidity
File: ./contracts/libraries/Errors.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L2)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L2)]


```solidity
File: ./contracts/libraries/InteractionHelper.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L2)]


```solidity
File: ./contracts/libraries/Math.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L2)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L2)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L2)]


```solidity
File: ./contracts/multicall/Multicall.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L2)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L2)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L2)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L2)]


```solidity
File: ./contracts/tokens/interfaces/IERC20Partial.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L2)]


```solidity
File: ./contracts/types/LeftRight.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L2)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L2)]


```solidity
File: ./contracts/types/TokenId.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L2)]


</details>


<a name="L-16"></a> 
### [L-16] Some tokens may revert when large transfers are made
Tokens such as COMP or UNI will revert when an address' balance reaches `type(uint96).max`. Ensure that the calls below can be broken up into smaller batches if necessary.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

333:         return ERC20Minimal.transfer(recipient, amount);

352:         return ERC20Minimal.transferFrom(from, to, amount);

```
*Github:* [[333](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L333), [352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L352)]



<a name="L-17"></a> 
### [L-17] Some tokens may revert when zero value transfers are made
Despite the fact that [EIP-20 states](https://github.com/ethereum/EIPs/blob/7500ac4fc1bbdfaf684e7ef851f798f6b667b2fe/EIPS/eip-20.md?plain=1#L116) that zero-value transfers must be accepted, some tokens, such as LEND, will revert if this is attempted, which may cause transactions that involve other tokens (such as batch operations) to fully revert. Consider skipping the transfer if the amount is zero, which will also save gas.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

333:         return ERC20Minimal.transfer(recipient, amount);

352:         return ERC20Minimal.transferFrom(from, to, amount);

```
*Github:* [[333](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L333), [352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L352)]



<a name="L-18"></a> 
### [L-18] Subtraction may underflow if result of multiplication is too large
The following expressions may underflow, as the subtrahend could be greater than the minuend in case the former is multiplied by a large number.

<details>
<summary>
There are <b>36</b> instances (click to show):
</summary>

```solidity
File: ./contracts/libraries/Math.sol

/// @audit `denominator * inv`
418:             inv *= 2 - denominator * inv; // inverse mod 2**8

/// @audit `denominator * inv`
418:             inv *= 2 - denominator * inv; // inverse mod 2**8

/// @audit `denominator * inv`
418:             inv *= 2 - denominator * inv; // inverse mod 2**8

/// @audit `denominator * inv`
418:             inv *= 2 - denominator * inv; // inverse mod 2**8

/// @audit `denominator * inv`
418:             inv *= 2 - denominator * inv; // inverse mod 2**8

/// @audit `denominator * inv`
418:             inv *= 2 - denominator * inv; // inverse mod 2**8

/// @audit `denominator * inv`
419:             inv *= 2 - denominator * inv; // inverse mod 2**16

/// @audit `denominator * inv`
419:             inv *= 2 - denominator * inv; // inverse mod 2**16

/// @audit `denominator * inv`
419:             inv *= 2 - denominator * inv; // inverse mod 2**16

/// @audit `denominator * inv`
419:             inv *= 2 - denominator * inv; // inverse mod 2**16

/// @audit `denominator * inv`
419:             inv *= 2 - denominator * inv; // inverse mod 2**16

/// @audit `denominator * inv`
419:             inv *= 2 - denominator * inv; // inverse mod 2**16

/// @audit `denominator * inv`
420:             inv *= 2 - denominator * inv; // inverse mod 2**32

/// @audit `denominator * inv`
420:             inv *= 2 - denominator * inv; // inverse mod 2**32

/// @audit `denominator * inv`
420:             inv *= 2 - denominator * inv; // inverse mod 2**32

/// @audit `denominator * inv`
420:             inv *= 2 - denominator * inv; // inverse mod 2**32

/// @audit `denominator * inv`
420:             inv *= 2 - denominator * inv; // inverse mod 2**32

/// @audit `denominator * inv`
420:             inv *= 2 - denominator * inv; // inverse mod 2**32

/// @audit `denominator * inv`
421:             inv *= 2 - denominator * inv; // inverse mod 2**64

/// @audit `denominator * inv`
421:             inv *= 2 - denominator * inv; // inverse mod 2**64

/// @audit `denominator * inv`
421:             inv *= 2 - denominator * inv; // inverse mod 2**64

/// @audit `denominator * inv`
421:             inv *= 2 - denominator * inv; // inverse mod 2**64

/// @audit `denominator * inv`
421:             inv *= 2 - denominator * inv; // inverse mod 2**64

/// @audit `denominator * inv`
421:             inv *= 2 - denominator * inv; // inverse mod 2**64

/// @audit `denominator * inv`
422:             inv *= 2 - denominator * inv; // inverse mod 2**128

/// @audit `denominator * inv`
422:             inv *= 2 - denominator * inv; // inverse mod 2**128

/// @audit `denominator * inv`
422:             inv *= 2 - denominator * inv; // inverse mod 2**128

/// @audit `denominator * inv`
422:             inv *= 2 - denominator * inv; // inverse mod 2**128

/// @audit `denominator * inv`
422:             inv *= 2 - denominator * inv; // inverse mod 2**128

/// @audit `denominator * inv`
422:             inv *= 2 - denominator * inv; // inverse mod 2**128

/// @audit `denominator * inv`
423:             inv *= 2 - denominator * inv; // inverse mod 2**256

/// @audit `denominator * inv`
423:             inv *= 2 - denominator * inv; // inverse mod 2**256

/// @audit `denominator * inv`
423:             inv *= 2 - denominator * inv; // inverse mod 2**256

/// @audit `denominator * inv`
423:             inv *= 2 - denominator * inv; // inverse mod 2**256

/// @audit `denominator * inv`
423:             inv *= 2 - denominator * inv; // inverse mod 2**256

/// @audit `denominator * inv`
423:             inv *= 2 - denominator * inv; // inverse mod 2**256

```
*Github:* [[418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L418), [418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L418), [418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L418), [418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L418), [418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L418), [418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L418), [419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L419), [419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L419), [419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L419), [419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L419), [419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L419), [419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L419), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L420), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L420), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L420), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L420), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L420), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L420), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L421), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L421), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L421), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L421), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L421), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L421), [422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L422), [422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L422), [422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L422), [422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L422), [422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L422), [422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L422), [423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L423), [423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L423), [423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L423), [423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L423), [423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L423), [423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L423)]


</details>


<a name="L-19"></a> 
### [L-19] Sending tokens in a for loop
Performing token transfers in a loop in a Solidity contract is generally not recommended due to various reasons. One of these reasons is the "Fail-Silently" issue.

In a Solidity loop, if one transfer operation fails, it causes the entire transaction to fail. This issue can be particularly troublesome when you're dealing with multiple transfers in one transaction. For instance, if you're looping through an array of recipients to distribute dividends or rewards, a single failed transfer will prevent all the subsequent recipients from receiving their transfers. This could be due to the recipient contract throwing an exception or due to other issues like a gas limit being exceeded.

Moreover, such a design could also inadvertently lead to a situation where a malicious contract intentionally causes a failure when receiving Ether to prevent other participants from getting their rightful transfers. This could open up avenues for griefing attacks in the system.

Resolution: To mitigate this problem, it's typically recommended to follow the "withdraw pattern" in your contracts instead of pushing payments. In this model, each recipient would be responsible for triggering their own payment. This separates each transfer operation, so a failure in one doesn't impact the others. Additionally, it greatly reduces the chance of malicious interference as the control over fund withdrawal lies with the intended recipient and not with an external loop operation.

*There is one instance of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `poolId`
591:     /// @param id The tokenId being transferred'
         /// @param amount The amount of the token being transferred
         function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

```
*Github:* [[591](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L591)]



<a name="L-20"></a> 
### [L-20] Tokens may be minted to `address(0)`

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {
             assets = previewMint(shares);
     
             if (assets > type(uint104).max) revert Errors.DepositTooLarge();
     
             // transfer assets (underlying token funds) from the user/the LP to the PanopticPool
             // in return for the shares to be minted
             SafeTransferLib.safeTransferFrom(
                 s_underlyingToken,
                 msg.sender,
                 address(s_panopticPool),
                 assets
             );
     
             // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
             _mint(receiver, shares);
     
             // update tracked asset balance
             unchecked {
                 s_poolAssets += uint128(assets);
             }
     
             emit Deposit(msg.sender, receiver, assets, shares);
         }

```
*Github:* [[477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L477)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

214:     function _mint(address to, uint256 id, uint256 amount) internal {
             // balance will never overflow
             unchecked {
                 balanceOf[to][id] += amount;
             }
     
             emit TransferSingle(msg.sender, address(0), to, id, amount);
     
             if (to.code.length != 0) {
                 if (
                     ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
                     ERC1155Holder.onERC1155Received.selector
                 ) {
                     revert UnsafeRecipient();
                 }
             }
         }

```
*Github:* [[214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L214)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

122:     function _mint(address to, uint256 amount) internal {
             // Cannot overflow because the sum of all user
             // balances can't exceed the max uint256 value.
             unchecked {
                 balanceOf[to] += amount;
             }
             totalSupply += amount;
     
             emit Transfer(address(0), to, amount);
         }

```
*Github:* [[122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L122)]



<a name="L-21"></a> 
### [L-21] Unsafe downcast
When a type is downcast to a smaller type, the higher order bits are truncated, effectively applying a modulo to the original value. Without any other checks, this wrapping will lead to unexpected behavior and bugs.

<details>
<summary>
There are <b>122</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit uint256 -> uint128
262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

/// @audit uint256 -> uint128
436:             s_poolAssets += uint128(assets);

/// @audit uint256 -> uint128
496:             s_poolAssets += uint128(assets);

/// @audit uint256 -> uint128
552:             s_poolAssets -= uint128(assets);

/// @audit uint256 -> uint128
612:             s_poolAssets -= uint128(assets);

/// @audit int256 -> int24
667:                     int24 range = int24(

/// @audit uint256 -> uint128
715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

/// @audit uint256 -> uint128
715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

/// @audit uint256 -> uint128
718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

/// @audit uint256 -> uint128
718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

/// @audit int256 -> int128
731:                 .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))

/// @audit int256 -> int128
732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

/// @audit uint256 -> uint128
1036:     /// @dev Called when a position is burnt because it may need to be exercised.

/// @audit uint256 -> uint128
1037:     /// @param optionOwner The owner of the option being burned and potentially exercised.

/// @audit uint256 -> uint128
1092:     /// @param longAmount The amount of long options held.

/// @audit uint256 -> uint128
1094:     /// @param swappedAmount The (potential) amount swapped during any ITM option creations.

/// @audit int256 -> int128
1095:     /// @return exchangedAmount The amount of funds to be exchanged for minting an option (includes commission, swapFee, and intrinsic value).

/// @audit uint128 -> uint64
1337:         // if the position is long, required tokens does not depend on price

/// @audit uint128 -> uint64
1338:         unchecked {

/// @audit uint128 -> uint64
1593:     /// @dev A strangle can only have only one of its leg tested at the same time, so this reduces the total risk and collateral requirement.

/// @audit uint128 -> uint64
1593:     /// @dev A strangle can only have only one of its leg tested at the same time, so this reduces the total risk and collateral requirement.

/// @audit uint128 -> uint64
1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

/// @audit uint128 -> uint64
1641:                 strangleRequired = _getRequiredCollateralSingleLegNoPartner(

```
*Github:* [[262](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L262), [436](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L436), [496](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L496), [552](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L552), [612](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L612), [667](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L667), [715](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L715), [715](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L715), [718](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L718), [718](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L718), [731](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L731), [732](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L732), [1036](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1036), [1037](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1037), [1092](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1092), [1094](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1094), [1095](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1095), [1337](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1337), [1338](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1338), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1593), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1593), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1638), [1641](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1641)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit uint256 -> uint128
352:                 fullRangeLiquidity = uint128(

/// @audit uint256 -> uint128
356:                 fullRangeLiquidity = uint128(

/// @audit uint256 -> uint128
365:                 uint128 liquidity0 = uint128(

/// @audit uint256 -> uint128
368:                 uint128 liquidity1 = uint128(

```
*Github:* [[352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L352), [356](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L356), [365](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L365), [368](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L368)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit uint128 -> uint64
366:         poolUtilization0 = uint64(balanceData.leftSlot());

/// @audit uint128 -> uint64
370:         poolUtilization1 = uint64(balanceData.leftSlot() >> 64);

/// @audit uint256 -> uint128
730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

/// @audit uint256 -> uint128
730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

/// @audit uint256 -> uint64
775:                     uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))

/// @audit int256 -> int128
1167:             .toRightSlot(int128(liquidationBonus0))

/// @audit int256 -> int128
1168:             .toLeftSlot(int128(liquidationBonus1));

/// @audit int256 -> int128
1549:                                 int256(

/// @audit int256 -> int128
1558:                                 int256(

/// @audit int256 -> int128
1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

/// @audit int256 -> int128
1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

/// @audit uint256 -> uint128
1728:                             uint128(

/// @audit uint256 -> uint128
1736:                             uint128(

/// @audit uint256 -> uint128
1777:                         uint128(

/// @audit uint256 -> uint128
1786:                         uint128(

/// @audit uint256 -> uint128
1932:                                     uint128(

/// @audit uint256 -> uint128
1949:                                     uint128(

/// @audit uint256 -> uint128
1967:                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))

/// @audit uint256 -> uint128
1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));

```
*Github:* [[366](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L366), [370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L370), [730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730), [730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730), [775](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L775), [1167](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1167), [1168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1168), [1549](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1549), [1558](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1558), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1636), [1728](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1728), [1736](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1736), [1777](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1777), [1786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1786), [1932](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1932), [1949](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1949), [1967](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1967), [1968](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1968)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit uint256 -> uint128
631:             if (

/// @audit int256 -> int128
1201:         /// mint the required amount in the Uniswap pool

/// @audit int256 -> int128
1204:             address(this),

/// @audit int256 -> int128
1211:         // amount0 The amount of token0 that was paid to mint the given amount of liquidity

/// @audit int256 -> int128
1212:         // amount1 The amount of token1 that was paid to mint the given amount of liquidity

/// @audit int256 -> int128
1247:     /// @notice Helper to collect amounts between msg.sender and Uniswap and also to update the Uniswap fees collected to date from the AMM.

/// @audit int256 -> int128
1247:     /// @notice Helper to collect amounts between msg.sender and Uniswap and also to update the Uniswap fees collected to date from the AMM.

/// @audit int256 -> int128
1267:         // When this is the case, we want to behave as if there are 0 fees, so we just rectify the values.

/// @audit int256 -> int128
1267:         // When this is the case, we want to behave as if there are 0 fees, so we just rectify the values.

/// @audit uint256 -> uint64
1570: 

```
*Github:* [[631](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L631), [1201](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1201), [1204](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1204), [1211](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1211), [1212](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1212), [1247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1247), [1247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1247), [1267](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1267), [1267](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1267), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

/// @audit int256 -> int128
121:     /// @notice Calculates the fee growth that has occurred (per unit of liquidity) in the AMM/Uniswap for an

/// @audit int256 -> int128
122:     /// option position's tick range.

```
*Github:* [[121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L121), [122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L122)]


```solidity
File: ./contracts/libraries/Math.sol

/// @audit uint256 -> uint160
179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

/// @audit uint256 -> uint128
297:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

/// @audit uint256 -> uint128
303:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) {

/// @audit int256 -> int128
319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

```
*Github:* [[179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L179), [297](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L297), [303](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L303), [319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L319)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit uint160 -> uint64
50:             uint64 poolId = uint64(uint160(univ3pool) >> 112);

/// @audit uint64 -> uint48
62:             return (poolId & TICKSPACING_MASK) + (uint48(poolId) + 1);

/// @audit uint256 -> uint248
102:             uint248 updatedHash = uint248(existingHash) ^

/// @audit uint256 -> uint248
103:                 (uint248(uint256(keccak256(abi.encode(tokenId)))));

/// @audit int256 -> int24
155:             return int24(Math.sort(ticks)[cardinality / 2]);

/// @audit uint256 -> uint24
178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

/// @audit uint256 -> uint24
178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

/// @audit uint256 -> uint24
179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

/// @audit uint256 -> uint24
179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

/// @audit uint256 -> uint40
183:             if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

/// @audit int256 -> int24
195:                         (tickCumulative_last - tickCumulative_old) /

/// @audit uint256 -> uint24
200:                 uint24 orderMap = uint24(medianData >> 192);

/// @audit uint256 -> uint24
217:                     entry = int24(uint24(medianData >> (rank * 24)));

/// @audit uint256 -> uint192
229:                     uint256(uint192(medianData << 24)) +

/// @audit uint256 -> uint32
249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);

/// @audit int56 -> int24
258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

/// @audit int256 -> int24
266:             return int24(sortedTicks[10]);

/// @audit int256 -> int24
378:         );

/// @audit uint256 -> uint128
485:     /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

/// @audit uint256 -> uint128
588:                 .getAmount1ForLiquidity(Math.getLiquidityForAmount0(tickLower, tickUpper, amount0))

/// @audit uint256 -> uint128
594:                 .getAmount0ForLiquidity(Math.getLiquidityForAmount1(tickLower, tickUpper, amount1))

/// @audit int256 -> int128
751:                 )

/// @audit int256 -> int128
756:     /// @notice Haircut/clawback any premium paid by `liquidatee` on `positionIdList` over the protocol loss threshold during a liquidation.

/// @audit int256 -> int128
857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

/// @audit int256 -> int128
860:             for (uint256 i = 0; i < positionIdList.length; i++) {

/// @audit uint256 -> uint128
900:                             )

/// @audit uint256 -> uint128
902:                     }

/// @audit int256 -> int128
937:                             int128(

/// @audit int256 -> int128
939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)

/// @audit int256 -> int128
955:                             int128(

/// @audit int256 -> int128
957:                                     PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)

```
*Github:* [[50](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L50), [62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L62), [102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L102), [103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L103), [155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L155), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L178), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L178), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L179), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L179), [183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L183), [195](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L195), [200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L200), [217](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L217), [229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L229), [249](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L249), [258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L258), [266](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L266), [378](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L378), [485](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L485), [588](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L588), [594](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L594), [751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L751), [756](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L756), [857](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L857), [860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L860), [900](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L900), [902](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L902), [937](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L937), [939](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L939), [955](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L955), [957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L957)]


```solidity
File: ./contracts/types/LeftRight.sol

/// @audit uint256 -> uint128
40:         return uint128(LeftRightUnsigned.unwrap(self));

/// @audit int256 -> int128
47:         return int128(LeftRightSigned.unwrap(self));

/// @audit uint256 -> uint128
69:                         uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)

/// @audit int256 -> int128
89:                         (int256(int128(LeftRightSigned.unwrap(self)) + right) & RIGHT_HALF_BIT_MASK)

/// @audit uint256 -> uint128
102:         return uint128(LeftRightUnsigned.unwrap(self) >> 128);

/// @audit int256 -> int128
109:         return int128(LeftRightSigned.unwrap(self) >> 128);

/// @audit uint256 -> uint128
162:                 (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))

/// @audit uint256 -> uint128
162:                 (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))

/// @audit uint256 -> uint128
185:                 (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))

/// @audit uint256 -> uint128
185:                 (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))

/// @audit int256 -> int128
197:             int128 left128 = int128(left);

/// @audit int256 -> int128
202:             int128 right128 = int128(right);

/// @audit int256 -> int128
217:             int128 left128 = int128(left256);

/// @audit int256 -> int128
220:             int128 right128 = int128(right256);

/// @audit int256 -> int128
235:             int128 left128 = int128(left256);

/// @audit int256 -> int128
238:             int128 right128 = int128(right256);

/// @audit int256 -> int128
257:             int128 left128 = int128(left256);

/// @audit int256 -> int128
260:             int128 right128 = int128(right256);

/// @audit int256 -> int128
265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

/// @audit int256 -> int128
266:                     int128(Math.max(left128, 0))

```
*Github:* [[40](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L40), [47](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L47), [69](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L69), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L89), [102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L109), [162](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L162), [162](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L162), [185](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L185), [185](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L185), [197](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L197), [202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L202), [217](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L217), [220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L220), [235](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L235), [238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L238), [257](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L257), [260](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L260), [265](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L265), [266](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L266)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

/// @audit int256 -> int24
178:     /// @param self The LiquidityChunk to get the upper tick from

/// @audit int256 -> int24
187:     /// @param self The LiquidityChunk to get the liquidity from

/// @audit uint256 -> uint128
195: 

```
*Github:* [[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L178), [187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L187), [195](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L195)]


```solidity
File: ./contracts/types/TokenId.sol

/// @audit uint256 -> uint64
89:             return uint64(TokenId.unwrap(self));

/// @audit uint256 -> uint24
98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

/// @audit int256 -> int24
160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

/// @audit int256 -> int24
171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

/// @audit uint256 -> uint48
521:                     if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {

/// @audit uint256 -> uint48
521:                     if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {

```
*Github:* [[89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L89), [98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L98), [160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L171), [521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L521), [521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L521)]


</details>


<a name="L-22"></a> 
### [L-22] Unsafe addition/multiplication in `unchecked` block
These additions/multiplications may silently overflow because they're in unchecked blocks with no preceding value checks, which may lead to unexpected results.

<details>
<summary>
There are <b>72</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

202:                 2230 +

203:                     (12500 * ratioTick) /

205:                     (7812 * ratioTick ** 2) /

207:                     (6510 * ratioTick ** 3) /

262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

372:             return s_poolAssets + s_inAMM;

403:                 assets * (DECIMALS - COMMISSION_FEE),

405:                 totalAssets() * DECIMALS

446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

463:                 shares * DECIMALS,

465:                 totalSupply * (DECIMALS - COMMISSION_FEE)

670:                                 uint24(positionId.width(leg) * positionId.tickSpacing()),

731:                 .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))

732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

743:             return int256((s_inAMM * DECIMALS) / totalAssets());

796:                 min_sell_ratio +

797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

849:                 (BUYER_COLLATERAL_RATIO +

850:                     (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /

1037:     /// @param optionOwner The owner of the option being burned and potentially exercised.

1093:     /// @param shortAmount The amount of short options held.

1118:             //compute total commission amount = commission rate + spread fee

1122:                     DECIMALS

1130:     //////////////////////////////////////////////////////////////*/

1132:     /// @notice Get the collateral status/margin details of an account/user.

1370:                     // compute the collateral requirement depending on whether the position is ITM & out-of-range or ITM and in-range:

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1416:                         // position is in-the-money, collateral requirement = amountMoved*(1-SRC)*(scaleFactor-ratio)/(scaleFactor+1) + SCR*amountMoved

1424:     /// @notice Calculate the required amount of collateral for leg 'index' for position 'tokenId' accounting for its partner leg.

1493:             // compute required as amount*collateralRatio

1503:     /// @dev may be higher than the requirement of non risk-partnered legs if the spread is very wide (risky)

1577:         // narrower spreads will be very capital efficient (1/3 of non-partnered CR!), but

1578:         // wider spreads (an uncommon position w/ high max loss) may not benefit from risk partnering

1644:                     positionSize,

```
*Github:* [[202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L203), [205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L205), [207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L207), [262](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L262), [372](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L372), [403](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L403), [405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L405), [446](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L446), [463](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L463), [465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L465), [670](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L670), [731](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L731), [732](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L732), [743](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L743), [796](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L796), [797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L797), [849](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L849), [850](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L850), [1037](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1037), [1093](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1093), [1118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1118), [1122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1122), [1130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1130), [1132](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1132), [1370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1370), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1374), [1416](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1416), [1424](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1424), [1493](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1493), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1503), [1577](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1577), [1578](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1578), [1644](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1644)]


```solidity
File: ./contracts/PanopticFactory.sol

300:             maxSalt = uint256(salt) + loops;

323:                 salt = bytes32(uint256(salt) + 1);

392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```
*Github:* [[300](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L300), [323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L323), [392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L392)]


```solidity
File: ./contracts/PanopticPool.sol

309:                 (uint256(block.timestamp) << 216) +

730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

1550:                                     ((premiumAccumulatorsByLeg[leg][0] -

1559:                                     ((premiumAccumulatorsByLeg[leg][1] -

1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1729:                                 (grossCurrent[0] *

1731:                                     grossPremiumLast.rightSlot() *

1737:                                 (grossCurrent[1] *

1739:                                     grossPremiumLast.leftSlot() *

1768:             uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *

1770:             uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *

1779:                                 (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /

1788:                                 (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /

1820:             totalLiquidity = accountLiquidities.rightSlot() + accountLiquidities.leftSlot();

1935:                                                 (int256(

1936:                                                     grossPremiumLast.rightSlot() *

1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *

1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),

1952:                                                 (int256(

1953:                                                     grossPremiumLast.leftSlot() *

1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *

1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,

```
*Github:* [[309](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L309), [730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730), [1329](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1329), [1348](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1348), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1353), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487), [1550](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1550), [1559](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1559), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1636), [1729](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1729), [1731](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1731), [1737](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1737), [1739](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1739), [1768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1768), [1770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1770), [1779](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1779), [1788](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1788), [1820](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1820), [1935](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1935), [1936](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1936), [1940](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1940), [1942](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1942), [1952](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1952), [1953](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1953), [1957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1957), [1959](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1959)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

404:         uint256 amount1Owed,

872:             LeftRightUnsigned[4] memory collectedByLeg,

1385:                 uint128 premium1X64_gross;

1395:                         .toUint128Capped();

1398:                         .toUint128Capped();

1409:     /*//////////////////////////////////////////////////////////////

1420:     /// @return accountLiquidities The amount of liquidity that has been shorted/added to the Uniswap contract (netLiquidity:removedLiquidity -> rightSlot:leftSlot)

1421:     function getAccountLiquidity(

```
*Github:* [[404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L404), [872](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L872), [1385](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1385), [1395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1395), [1398](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1398), [1409](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1409), [1420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1420), [1421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1421)]


</details>


<a name="L-23"></a> 
### [L-23] Using zero as a parameter
Taking `0` as a valid argument in Solidity without checks can lead to severe security issues. A historical example is the infamous `0x0` address bug where numerous tokens were lost. This happens because 0 can be interpreted as an uninitialized `address`, leading to transfers to the 0x0 address, effectively burning tokens. Moreover, `0` as a denominator in division operations would cause a runtime exception. It's also often indicative of a logical error in the caller's code. It's important to always validate input and handle edge cases like `0` appropriately. Use `require()` statements to enforce conditions and provide clear error messages to facilitate debugging and safer code.

<details>
<summary>
There are <b>11</b> instances (click to show):
</summary>

```solidity
File: ./contracts/PanopticPool.sol

893:         _validatePositionList(user, positionIdList, 0);

1023:         _validatePositionList(liquidatee, positionIdList, 0);

1153:         _validatePositionList(msg.sender, positionIdListLiquidator, 0);

1191:         _validatePositionList(msg.sender, positionIdListExercisor, 0);

1227:         _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

1592:         _validatePositionList(owner, positionIdList, 0);

```
*Github:* [[893](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L893), [1023](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1023), [1153](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1153), [1191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1191), [1227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1227), [1592](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1592)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

729:     }
     
         /// @notice When a position is minted or burnt in-the-money (ITM) we are *not* 100% token0 or 100% token1: we have a mix of both tokens.

```
*Github:* [[729](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L729)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

220:         emit TransferSingle(msg.sender, address(0), to, id, amount);

239:         emit TransferSingle(msg.sender, from, address(0), id, amount);

```
*Github:* [[220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L220), [239](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L239)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

130:         emit Transfer(address(0), to, amount);

145:         emit Transfer(from, address(0), amount);

```
*Github:* [[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L130), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L145)]


</details>


<a name="L-24"></a> 
### [L-24] Vulnerable version of OZ contarcts is used (`4.8.3`)
The project is using a vulnerable version.
See the list of OZ vulnerabilities [here](https://security.snyk.io/package/npm/@openzeppelin%2Fcontracts).

*There is one instance of this issue:*
```solidity

Global finding

```
*Github:* [[Global](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/)]



<a name="L-25"></a> 
### [L-25] Missing zero address check in initializer

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

/// @audit missing zero check for `_owner`
134:     function initialize(address _owner) public {

```
*Github:* [[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L134)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit missing zero check for `token0`
/// @audit missing zero check for `token1`
361:         // if poolId == 0, we have a bit on the left set if it was initialized, so this will still return properly
             if (s_AddrToPoolIdData[univ3pool] != 0) return;

```
*Github:* [[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L361)]



<a name="L-26"></a> 
### [L-26] `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()`
Use `abi.encode()` instead which will pad items to 32 bytes, which will [prevent hash collisions](https://docs.soliditylang.org/en/v0.8.13/abi-spec.html#non-standard-packed-mode) (e.g. `abi.encodePacked(0x123,0x456)` => `0x123456` => `abi.encodePacked(0x1,0x23456)`, but `abi.encode(0x123,0x456)` => `0x0...1230...456`). "Unless there is a compelling reason, `abi.encode` should be preferred". If there is only one argument to `abi.encodePacked()` it can often be cast to `bytes()` or `bytes32()` [instead](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739).
If all arguments are strings and or bytes, `bytes.concat()` should be used instead

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

1431:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

1544:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

```
*Github:* [[1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1431), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1544)]



<a name="L-27"></a> 
### [L-27] Centralization Risk for trusted owners
Contracts have owners with privileged rights to perform admin tasks and need to be trusted to not perform malicious updates or drain funds.

*There are <b>7</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

864:     function delegate(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {

898:     /// @notice Refunds delegated tokens back to the protocol
         /// @dev Assumes that `delegatee` has enough money to pay for the refund

907:     /// @notice Revoke previously delegated shares. The opposite of 'delegate'.
         /// @param delegator The delegator to send shares *to* (because we are revoking - opposite when we delegate).

917:                 ┌────────┐
                     │Panoptic│
                     │Pool    │
                     └────┬───┘
                          │(1) convert 'assets' to shares (this ERC20 contract)

980:                 _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));
                 }
             }
         }
     
         /*//////////////////////////////////////////////////////////////

1002:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
                  int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
      
                  // constrict premium to only assets not belonging to PLPs (i.e premium paid by sellers or collected from the pool earlier)

1051:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
                  int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
      
                  // add premium to be paid/collected on position close
                  int256 tokenToPay = -realizedPremium;

```
*Github:* [[864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L864), [898](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L898), [907](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L907), [917](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L917), [980](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L980), [1002](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1002), [1051](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1051)]



<a name="L-28"></a> 
### [L-28] `decimals()` is not a part of the ERC-20 standard
The `decimals()` function is not a part of the ERC-20 standard, and was added later as an optional extension. As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

*There is one instance of this issue:*
```solidity
File: ./contracts/libraries/InteractionHelper.sol

110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {

```
*Github:* [[110](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L110)]



<a name="L-29"></a> 
### [L-29] Initializers could be front-run
Initializers could be front-run, allowing an attacker to either set their own values, take ownership of the contract, and in the best case forcing a re-deployment

*There is one instance of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

134:     function initialize(address _owner) public {

```
*Github:* [[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L134)]



<a name="L-30"></a> 
### [L-30] `symbol()` is not a part of the ERC-20 standard
The `symbol()` function is not a part of the ERC-20 standard, and was added later as an optional extension. As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/libraries/InteractionHelper.sol

60:         try IERC20Metadata(token0).symbol() returns (string memory _symbol) {

65:         try IERC20Metadata(token1).symbol() returns (string memory _symbol) {

97:         try IERC20Metadata(token).symbol() returns (string memory tokenSymbol) {

```
*Github:* [[60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L60), [65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L65), [97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L97)]



<a name="L-31"></a> 
### [L-31] Low level calls in solidity versions preceding 0.8.14 can result in an optimiser bug
In Solidity versions 0.8.13 and 0.8.14, a known optimizer bug presents potential risks when a variable is used in a separate assembly block from the one in which it was stored. Specifically, the 'mstore' operation could be optimized out due to this bug, leading to the use of uninitialized memory. Although the current code does not exhibit this risky pattern of execution, it does utilize 'mstore' within assembly blocks, which introduces a vulnerability risk for future code modifications. As a preventative measure, it is advisable to avoid the usage of the afflicted Solidity versions, 0.8.13 and 0.8.14. Instead, consider utilizing a version that is not impacted by this optimizer bug to prevent potential memory initialization issues in your smart contract.

<details>
<summary>
There are <b>30</b> instances (click to show):
</summary>

```solidity
File: ./contracts/libraries/Math.sol

353:             assembly ("memory-safe") {

362:                 assembly ("memory-safe") {

379:             assembly ("memory-safe") {

383:             assembly ("memory-safe") {

393:             assembly ("memory-safe") {

398:             assembly ("memory-safe") {

404:             assembly ("memory-safe") {

467:             assembly ("memory-safe") {

476:                 assembly ("memory-safe") {

493:             assembly ("memory-safe") {

497:             assembly ("memory-safe") {

503:             assembly ("memory-safe") {

530:             assembly ("memory-safe") {

539:                 assembly ("memory-safe") {

556:             assembly ("memory-safe") {

560:             assembly ("memory-safe") {

566:             assembly ("memory-safe") {

607:             assembly ("memory-safe") {

616:                 assembly ("memory-safe") {

633:             assembly ("memory-safe") {

637:             assembly ("memory-safe") {

643:             assembly ("memory-safe") {

684:             assembly ("memory-safe") {

693:                 assembly ("memory-safe") {

710:             assembly ("memory-safe") {

714:             assembly ("memory-safe") {

720:             assembly ("memory-safe") {

739:         assembly ("memory-safe") {

```
*Github:* [[353](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L353), [362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L362), [379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L379), [383](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L383), [393](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L393), [398](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L398), [404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L404), [467](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L467), [476](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L476), [493](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L493), [497](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L497), [503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L503), [530](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L530), [539](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L539), [556](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L556), [560](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L560), [566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L566), [607](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L607), [616](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L616), [633](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L633), [637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L637), [643](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L643), [684](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L684), [693](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L693), [710](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L710), [714](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L714), [720](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L720), [739](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L739)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

24:         assembly ("memory-safe") {

55:         assembly ("memory-safe") {

```
*Github:* [[24](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L24), [55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L55)]


</details>


<a name="L-32"></a> 
### [L-32] For loops in public or external functions should be avoided due to high gas costs and possible DOS
In Solidity, for loops can potentially cause Denial of Service (DoS) attacks if not handled carefully. DoS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. Below are some scenarios where for loops can lead to DoS attacks: Nested for loops can become exceptionally gas expensive and should be used sparingly.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/multicall/Multicall.sol

12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
            results = new bytes[](data.length);
            for (uint256 i = 0; i < data.length; ) {

```
*Github:* [[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L12)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {
             if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
     
             // Storing these outside the loop saves ~15 gas per iteration.
             uint256 id;
             uint256 amount;
     
             for (uint256 i = 0; i < ids.length; ) {

178:     function balanceOfBatch(
             address[] calldata owners,
             uint256[] calldata ids
         ) public view returns (uint256[] memory balances) {
             balances = new uint256[](owners.length);
     
             // Unchecked because the only math done is incrementing
             // the array index counter which cannot possibly overflow.
             unchecked {
                 for (uint256 i = 0; i < owners.length; ++i) {

```
*Github:* [[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L130), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L178)]



<a name="L-33"></a> 
### [L-33] Function with two (or more) array parameters missing a length check
In Solidity, if two array parameters are used within a function and one of their lengths is used as the for-loop range, it's essential to have a length check. If the arrays are not the same length, you could experience out-of-bounds errors or unintended behavior. This could happen if the function tries to access an index that doesn't exist in the shorter array.

Resolution: Always validate that the lengths of both arrays are the same before entering the loop. Add a require statement at the start of the function to check that both arrays are of equal length. This helps maintain the integrity of the function and prevents potential errors due to differing array lengths. This requirement ensures the function fails early if the arrays don't match, rather than failing unpredictably or silently during execution.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

583:         // transfer the token (note that all state updates are completed before reentrancy is possible)

```
*Github:* [[583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L583)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

770:         TokenId[] memory positionIdList,
             LeftRightSigned[4][] memory premiasByLeg,
             LeftRightSigned collateralRemaining,
             CollateralTracker collateral0,
             CollateralTracker collateral1,
             uint160 sqrtPriceX96Final,
             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
         ) external returns (int256, int256) {
             unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;
                 for (uint256 i = 0; i < positionIdList.length; ++i) {

```
*Github:* [[770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L770)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {
             if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
     
             // Storing these outside the loop saves ~15 gas per iteration.
             uint256 id;
             uint256 amount;
     
             for (uint256 i = 0; i < ids.length; ) {

178:     function balanceOfBatch(
             address[] calldata owners,
             uint256[] calldata ids
         ) public view returns (uint256[] memory balances) {
             balances = new uint256[](owners.length);
     
             // Unchecked because the only math done is incrementing
             // the array index counter which cannot possibly overflow.
             unchecked {
                 for (uint256 i = 0; i < owners.length; ++i) {

```
*Github:* [[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L130), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L178)]



<a name="L-34"></a> 
### [L-34] Library has public/external functions
Libraries in Solidity are meant to be static collections of functions. They are deployed once and their code is reused by contracts through DELEGATECALL, which executes the library's code in the context of the calling contract. Public or external functions in libraries can be misleading because libraries are not supposed to maintain state or have external interactions in the way contracts do. Designing libraries with these kinds of functions goes against their intended purpose and can lead to confusion or misuse. For state management or external interactions, using contracts instead of libraries is more appropriate. Libraries should focus on utility functions that can operate on the data passed to them without side effects, enhancing code reuse and gas efficiency.

<details>
<summary>
There are <b>13</b> instances (click to show):
</summary>

```solidity
File: ./contracts/libraries/FeesCalc.sol

50:     ) external view returns (int256 value0, int256 value1) {
            for (uint256 k = 0; k < positionIdList.length; ) {
                TokenId tokenId = positionIdList[k];
                uint128 positionSize = userBalance[tokenId].rightSlot();
                uint256 numLegs = tokenId.countLegs();

104:         // extract the amount of AMM fees collected within the liquidity chunk`
             // note: the fee variables are *per unit of liquidity*; so more "rate" variables
             (
                 uint256 ammFeesPerLiqToken0X128,

```
*Github:* [[50](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L50), [104](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L104)]


```solidity
File: ./contracts/libraries/InteractionHelper.sol

24:     function doApprovals(
            SemiFungiblePositionManager sfpm,
            CollateralTracker ct0,
            CollateralTracker ct1,
            address token0,
            address token1
        ) external {

48:     function computeName(
            address token0,
            address token1,
            bool isToken0,
            uint24 fee,
            string memory prefix
        ) external view returns (string memory) {

91:     function computeSymbol(
            address token,
            string memory prefix
        ) external view returns (string memory) {

107:     function computeDecimals(address token) external view returns (uint8) {

```
*Github:* [[24](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L24), [48](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L48), [91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L91), [107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L107)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

75:     function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {
            unchecked {

125:     function computeMedianObservedPrice(
             IUniswapV3Pool univ3pool,
             uint256 observationIndex,
             uint256 observationCardinality,
             uint256 cardinality,
             uint256 period
         ) external view returns (int24) {
             unchecked {

168:     function computeInternalMedian(
             uint256 observationIndex,
             uint256 observationCardinality,
             uint256 period,
             uint256 medianData,
             IUniswapV3Pool univ3pool
         ) external view returns (int24 medianTick, uint256 updatedMedianData) {
             unchecked {

241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {
             uint32[] memory secondsAgos = new uint32[](20);

653:         LeftRightUnsigned tokenData1,
             uint160 sqrtPriceX96Twap,
             uint160 sqrtPriceX96Final,
             LeftRightSigned netExchanged,
             LeftRightSigned premia
         ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {
             unchecked {
                 // compute bonus as min(collateralBalance/2, required-collateralBalance)

770:         TokenId[] memory positionIdList,
             LeftRightSigned[4][] memory premiasByLeg,
             LeftRightSigned collateralRemaining,
             CollateralTracker collateral0,
             CollateralTracker collateral1,
             uint160 sqrtPriceX96Final,
             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
         ) external returns (int256, int256) {
             unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;

919:         LeftRightSigned refundValues,
             int24 atTick,
             CollateralTracker collateral0,
             CollateralTracker collateral1
         ) external view returns (LeftRightSigned) {
             uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);
             unchecked {
                 // if the refunder lacks sufficient token0 to pay back the refundee, have them pay back the equivalent value in token1

```
*Github:* [[75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L75), [125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L125), [168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L168), [241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L241), [653](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L653), [770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L770), [919](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L919)]


</details>


<a name="L-35"></a> 
### [L-35] `_safeMint()` should be used rather than `_mint()` wherever possible
`_mint()` is [discouraged](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/d4d8d2ed9798cc3383912a23b5e8d5cb602f7d4b/contracts/token/ERC721/ERC721.sol#L271) in favor of `_safeMint()` which ensures that the recipient is either an EOA or implements `IERC721Receiver`.

*There is one instance of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

515:         _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);

```
*Github:* [[515](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L515)]



<a name="L-36"></a> 
### [L-36] int/uint passed into abi.encodePacked without casting to a string
Not casting an integer as a string before passing it into abi.encode can result in unintended behaviour. lets say '1' being encoded as '1' it will be encoded as char(1) which is the 'start of heading' control character or id of 60 would be encoded as '<'. This is may not be intended. To rectify this, simply cast the Id as a string with string(id) or ideally use solmate's libString library (toString)

<details>
<summary>
There are <b>35</b> instances (click to show):
</summary>

```solidity
File: ./contracts/PanopticPool.sol

462:                         abi.encodePacked(

462:                         abi.encodePacked(

462:                         abi.encodePacked(

1643:                 abi.encodePacked(

1643:                 abi.encodePacked(

1643:                 abi.encodePacked(

1674:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

1674:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

1674:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

1856:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

1856:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

1856:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

```
*Github:* [[462](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L462), [462](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L462), [462](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L462), [1643](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1643), [1643](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1643), [1643](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1643), [1674](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1674), [1674](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1674), [1674](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1674), [1856](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1856), [1856](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1856), [1856](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1856)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

638:             if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity())

638:             if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity())

638:             if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity())

997:             uint128 chunkLiquidity = liquidityChunk.liquidity();

997:             uint128 chunkLiquidity = liquidityChunk.liquidity();

997:             uint128 chunkLiquidity = liquidityChunk.liquidity();

1181:     /// @dev note that "moved" means: mint in Uniswap and move tokens from msg.sender.

1181:     /// @dev note that "moved" means: mint in Uniswap and move tokens from msg.sender.

1450:         address univ3pool,

1450:         address univ3pool,

1450:         address univ3pool,

1485:                         netLiquidity

1485:                         netLiquidity

1485:                         netLiquidity

1570: 

1570: 

1570: 

```
*Github:* [[633](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L633), [633](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L633), [633](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L633), [638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L638), [638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L638), [638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L638), [997](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L997), [997](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L997), [997](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L997), [1181](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1181), [1181](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1181), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1450), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1450), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1450), [1485](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1485), [1485](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1485), [1485](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1485), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

881:                                 tokenId.width(0),

881:                                 tokenId.width(0),

881:                                 tokenId.width(0),

```
*Github:* [[881](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L881), [881](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L881), [881](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L881)]


</details>



## Non Critical Issues

<a name="NC-1"></a> 
### [NC-1] Assembly blocks should have extensive comments
Assembly blocks take a lot more time to audit than normal Solidity code, and often have gotchas and side-effects that the Solidity versions of the same code do not. Consider adding more comments explaining what is being done in every step of the assembly code, and describe why assembly is being used instead of Solidity.

<details>
<summary>
There are <b>31</b> instances (click to show):
</summary>

```solidity
File: ./contracts/libraries/Math.sol

353:             assembly ("memory-safe") {

362:                 assembly ("memory-safe") {

379:             assembly ("memory-safe") {

383:             assembly ("memory-safe") {

393:             assembly ("memory-safe") {

398:             assembly ("memory-safe") {

404:             assembly ("memory-safe") {

467:             assembly ("memory-safe") {

476:                 assembly ("memory-safe") {

493:             assembly ("memory-safe") {

497:             assembly ("memory-safe") {

503:             assembly ("memory-safe") {

530:             assembly ("memory-safe") {

539:                 assembly ("memory-safe") {

556:             assembly ("memory-safe") {

560:             assembly ("memory-safe") {

566:             assembly ("memory-safe") {

607:             assembly ("memory-safe") {

616:                 assembly ("memory-safe") {

633:             assembly ("memory-safe") {

637:             assembly ("memory-safe") {

643:             assembly ("memory-safe") {

684:             assembly ("memory-safe") {

693:                 assembly ("memory-safe") {

710:             assembly ("memory-safe") {

714:             assembly ("memory-safe") {

720:             assembly ("memory-safe") {

739:         assembly ("memory-safe") {

```
*Github:* [[353](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L353), [362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L362), [379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L379), [383](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L383), [393](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L393), [398](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L398), [404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L404), [467](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L467), [476](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L476), [493](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L493), [497](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L497), [503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L503), [530](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L530), [539](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L539), [556](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L556), [560](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L560), [566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L566), [607](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L607), [616](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L616), [633](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L633), [637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L637), [643](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L643), [684](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L684), [693](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L693), [710](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L710), [714](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L714), [720](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L720), [739](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L739)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

24:         assembly ("memory-safe") {

55:         assembly ("memory-safe") {

```
*Github:* [[24](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L24), [55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L55)]


```solidity
File: ./contracts/multicall/Multicall.sol

25:                 assembly ("memory-safe") {

```
*Github:* [[25](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L25)]


</details>


<a name="NC-2"></a> 
### [NC-2] `abi.encodePacked()` should be replaced with `bytes.concat()`
Solidity version 0.8.4 introduces `bytes.concat()`, which can be used to replace `abi.encodePacked()` on bytes/strings. It can make the intended operation clearer, leading to less reviewer confusion.

<details>
<summary>
There are <b>12</b> instances (click to show):
</summary>

```solidity
File: ./contracts/PanopticPool.sol

462:                         abi.encodePacked(

1643:                 abi.encodePacked(

1674:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

1856:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

```
*Github:* [[462](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L462), [1643](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1643), [1674](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1674), [1856](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1856)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

612:                 abi.encodePacked(

621:                 abi.encodePacked(

975:             abi.encodePacked(

1151:                     abi.encodePacked(

1431:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

1459:             abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)

1544:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

```
*Github:* [[612](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L612), [621](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L621), [975](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L975), [1151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1151), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1431), [1459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1459), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1544)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

879:                             abi.encodePacked(

```
*Github:* [[879](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L879)]


</details>


<a name="NC-3"></a> 
### [NC-3] Add inline comments for unnamed variables
`function foo(address x, address)` -> `function foo(address x, address /* y */)`

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {
             return type(uint104).max;

444:     function maxMint(address) external view returns (uint256 maxShares) {
             unchecked {

```
*Github:* [[392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444)]



<a name="NC-4"></a> 
### [NC-4] Avoid mutating function parameters
Function parameters in Solidity are passed by value, meaning they are essentially local copies. Mutating them can lead to confusion and errors because the changes don't persist outside the function. By keeping function parameters immutable, you ensure clarity in code behavior, preventing unintended side-effects. If you need to modify a value based on a parameter, use a local variable inside the function, leaving the original parameter unaltered. By adhering to this practice, you maintain a clear distinction between input data and the internal processing logic, improving code readability and reducing the potential for bugs.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `utilization`
751:     function _sellCollateralRatio(
             int256 utilization
         ) internal view returns (uint256 sellCollateralRatio) {
             // the sell ratio is on a straight line defined between two points (x0,y0) and (x1,y1):
             //   (x0,y0) = (targetPoolUtilization,min_sell_ratio) and
             //   (x1,y1) = (saturatedPoolUtilization,max_sell_ratio)
             // the line's formula: y = a * (x - x0) + y0, where a = (y1 - y0) / (x1 - x0)
             /**
                 SELL
                 COLLATERAL
                 RATIO
                               ^
                               |                  max ratio = 100%
                        100% - |                _------
                               |             _-¯
                               |          _-¯
                         20% - |---------¯
                               |         .       . .
                               +---------+-------+-+--->   POOL_
                                        50%    90% 100%     UTILIZATION
             */
     
             uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;
             /// if utilization is less than zero, this is the calculation for a strangle, which gets 2x the capital efficiency at low pool utilization
             /// at 0% utilization, strangle legs do not compound efficiency
             if (utilization < 0) {
                 unchecked {
                     min_sell_ratio /= 2;
                     utilization = -utilization;

/// @audit `poolUtilization`
1608:         // A strangle is an options strategy in which the investor holds a position
              // in both a call and a put option with different strike prices,
              // but with the same expiration date and underlying asset.
      
              /// collateral requirement is for short strangles depicted:
              /**
                          Put side of a short strangle, BPR = 100% - (100% - SCR/2)*(price/strike)
                 BUYING
                 POWER
                 REQUIREMENT
                               ^                    .
                               |           <- ITM   .  OTM ->
                        100% - |--__                .
                               |    ¯¯--__          .
                               |          ¯¯--__    .
                       SCR/2 - |                ¯¯--______ <------ base collateral is half that of a single-leg
                               +--------------------+--->   current
                               0                  strike     price
               */
              unchecked {
                  // A negative pool utilization is used to denote a position which is a strangle
                  // at low pool utilization's strangle legs are evaluated at 2x capital efficiency
      
                  uint64 poolUtilization0 = uint64(poolUtilization);
                  uint64 poolUtilization1 = uint64(poolUtilization >> 64);
      
                  // add 1 to handle poolUtilization = 0
      
                  poolUtilization =
                      uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +
                      (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
      
                  return
                      strangleRequired = _getRequiredCollateralSingleLegNoPartner(
                          tokenId,
                          index,

```
*Github:* [[751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L751), [1608](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1608)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `salt`
290:     function minePoolAddress(
             bytes32 salt,
             uint256 loops,
             uint256 minTargetRarity
         ) external view returns (bytes32 bestSalt, uint256 highestRarity) {
             // Start at the given 'salt' value (a checkpoint used to continue mining across multiple calls)
     
             // Runs until 'bestSalt' reaches 'minTargetRarity' or for 'loops', whichever comes first
             uint256 maxSalt;
             unchecked {
                 maxSalt = uint256(salt) + loops;
             }
     
             for (; uint256(salt) < maxSalt; ) {
                 uint256 rarity = PanopticMath.numberOfLeadingHexZeros(
                     POOL_REFERENCE.predictDeterministicAddress(salt)
                 );
     
                 if (rarity > highestRarity) {
                     // found a more rare address at this nonce
                     highestRarity = rarity;
                     bestSalt = salt;
                 }
     
                 if (rarity >= minTargetRarity) {
                     // desired target met
                     highestRarity = rarity;
                     bestSalt = salt;
                     break;
                 }
     
                 unchecked {
                     // increment the nonce of `currentSalt` (lower 96 bits)
                     salt = bytes32(uint256(salt) + 1);

```
*Github:* [[290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L290)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `tokenId`
708:         (totalMoved, collectedByLeg, itmAmounts) = _createPositionInAMM(
                 univ3pool,
                 tokenId,
                 positionSize,
                 isBurn
             );
     
             if (tickLimitLow > tickLimitHigh) {
                 // if the in-the-money amount is not zero (i.e. positions were minted ITM) and the user did provide tick limits LOW > HIGH, then swap necessary amounts
                 if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {
                     totalMoved = swapInAMM(univ3pool, itmAmounts).add(totalMoved);
                 }
     
                 (tickLimitLow, tickLimitHigh) = (tickLimitHigh, tickLimitLow);

```
*Github:* [[708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L708)]



<a name="NC-5"></a> 
### [NC-5] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability
Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/PanopticPool.sol

238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

```
*Github:* [[238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L238)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

66:     mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;

71:     mapping(address owner => mapping(address operator => bool approvedForAll))

```
*Github:* [[66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L66), [71](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L71)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

39:     mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;

```
*Github:* [[39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L39)]



<a name="NC-6"></a> 
### [NC-6] Complex casting
Consider whether the number of casts is really necessary, or whether using a different type would be more appropriate. Alternatively, add comments to explain in detail why the casts are necessary, and any implicit reasons why the cast does not introduce an overflow.

<details>
<summary>
There are <b>70</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

1003:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

1028:             s_poolAssets = uint128(uint256(updatedAssets));

1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

1052:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

1084:             s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));

1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

1121:                     uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,

1184:                 netBalance += uint256(uint128(premiumAllPositions));

1329:             ? int64(uint64(poolUtilization))

1330:             : int64(uint64(poolUtilization >> 64));

1585:                     ? int64(uint64(poolUtilization))

1586:                     : int64(uint64(poolUtilization >> 64))

1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```
*Github:* [[715](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L715), [715](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L715), [718](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L718), [718](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L718), [1003](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1003), [1028](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1028), [1029](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1029), [1029](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1029), [1052](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1052), [1084](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1084), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1085), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1085), [1121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1121), [1184](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1184), [1329](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1329), [1330](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1330), [1585](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1585), [1586](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1586), [1637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1638)]


```solidity
File: ./contracts/PanopticFactory.sol

323:                 salt = bytes32(uint256(salt) + 1);

```
*Github:* [[323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L323)]


```solidity
File: ./contracts/PanopticPool.sol

313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

314:                 (uint256(uint24(currentTick))); // add to slot 3

730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

1144:             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)

1149:             uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)

1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

```
*Github:* [[313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L314), [730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730), [730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730), [1144](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1144), [1149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1149), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1636)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

1172:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

1176:                 .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

1177:                 .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

1215:             int128(int256(amount1))

1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

1242:                 -int128(int256(amount1))

```
*Github:* [[1169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1169), [1172](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1172), [1176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1176), [1177](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1177), [1214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1214), [1215](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1215), [1241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1241), [1242](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1242)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

```
*Github:* [[117](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L117), [118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L118)]


```solidity
File: ./contracts/libraries/Math.sol

130:             uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));

131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

```
*Github:* [[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L130), [131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L131)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

50:             uint64 poolId = uint64(uint160(univ3pool) >> 112);

51:             poolId += uint64(uint24(tickSpacing)) << 48;

103:                 (uint248(uint256(keccak256(abi.encode(tokenId)))));

178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

183:             if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

217:                     entry = int24(uint24(medianData >> (rank * 24)));

229:                     uint256(uint192(medianData << 24)) +

230:                     uint256(uint24(lastObservedTick));

258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

693:             int256 balance0 = int256(uint256(tokenData0.rightSlot())) -

695:             int256 balance1 = int256(uint256(tokenData1.rightSlot())) -

```
*Github:* [[50](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L50), [51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L51), [103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L103), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L178), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L179), [183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L183), [217](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L217), [229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L229), [230](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L230), [258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L258), [377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L377), [693](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L693), [695](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L695)]


```solidity
File: ./contracts/types/LeftRight.sol

27:         int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

69:                         uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)

89:                         (int256(int128(LeftRightSigned.unwrap(self)) + right) & RIGHT_HALF_BIT_MASK)

196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();

201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();

```
*Github:* [[27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L27), [69](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L69), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L89), [196](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L196), [201](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L201)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

78:                     (uint256(uint24(_tickLower)) << 232) +

79:                         (uint256(uint24(_tickUpper)) << 208) +

109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));

182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));

```
*Github:* [[78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L78), [79](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L79), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L109), [126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L126), [173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L173), [182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L182)]


```solidity
File: ./contracts/types/TokenId.sol

98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

195:             return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

```
*Github:* [[98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L98), [160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L171), [195](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L195), [320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L320)]


</details>


<a name="NC-7"></a> 
### [NC-7] Consider adding a block/deny-list
Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens.

*There are <b>7</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

```
*Github:* [[36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36)]


```solidity
File: ./contracts/PanopticFactory.sol

26: contract PanopticFactory is Multicall {

```
*Github:* [[26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L26)]


```solidity
File: ./contracts/PanopticPool.sol

27: contract PanopticPool is ERC1155Holder, Multicall {

```
*Github:* [[27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L27)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

82:     /// @notice Emitted when a position is destroyed/burned
        /// @dev Recipient is used to track whether it was burned directly by the user or through an option contract
        /// @param recipient The address of the user who burned the position
        /// @param tokenId The tokenId of the burned position
        /// @param positionSize The number of contracts burnt, expressed in terms of the asset
        event TokenizedPositionBurnt(
            address indexed recipient,
            TokenId indexed tokenId,
            uint128 positionSize
        );
    
        /// @notice Emitted when a position is created/minted
        /// @dev Recipient is used to track whether it was minted directly by the user or through an option contract
        /// @param caller the caller who created the position. In 99% of cases `caller` == `recipient`.
        /// @param tokenId The tokenId of the minted position
        /// @param positionSize The number of contracts minted, expressed in terms of the asset
        event TokenizedPositionMinted(
            address indexed caller,
            TokenId indexed tokenId,
            uint128 positionSize
        );
    
        /*//////////////////////////////////////////////////////////////
                                     TYPES
        //////////////////////////////////////////////////////////////*/
    
        // Used for safecasting
        using Math for uint256;
        using Math for int256;
    
        // Packs the pool address and reentrancy lock into a single slot
        // `locked` can be initialized to false because the pool address makes the slot nonzero
        // false = unlocked, true = locked
        struct PoolAddressAndLock {

```
*Github:* [[82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L82)]


```solidity
File: ./contracts/multicall/Multicall.sol

8: abstract contract Multicall {

```
*Github:* [[8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L8)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

11: abstract contract ERC1155 {

```
*Github:* [[11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L11)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

9: abstract contract ERC20Minimal {

```
*Github:* [[9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L9)]



<a name="NC-8"></a> 
### [NC-8] Consider adding emergency-stop functionality
Consider adding `Pausable` to the following contracts so it's possible to stop them in case of an emergency.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

```
*Github:* [[36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36)]


```solidity
File: ./contracts/PanopticFactory.sol

26: contract PanopticFactory is Multicall {

```
*Github:* [[26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L26)]


```solidity
File: ./contracts/PanopticPool.sol

27: contract PanopticPool is ERC1155Holder, Multicall {

```
*Github:* [[27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L27)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

82:     /// @notice Emitted when a position is destroyed/burned

```
*Github:* [[82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L82)]



<a name="NC-9"></a> 
### [NC-9] Consider adding formal verification proofs
Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).

*There is one instance of this issue:*
```solidity

Global finding

```
*Github:* [[Global](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/)]



<a name="NC-10"></a> 
### [NC-10] Consider bounding input array length
The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to require() that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.

*There are <b>7</b> instances of this issue:*
```solidity
File: ./contracts/PanopticPool.sol

/// @audit consider length check for `positionIdList`
802:         for (uint256 i = 0; i < positionIdList.length; ) {

```
*Github:* [[802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L802)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit consider length check for `ids`
575:         for (uint256 i = 0; i < ids.length; ) {

```
*Github:* [[575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L575)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

/// @audit consider length check for `positionIdList`
51:         for (uint256 k = 0; k < positionIdList.length; ) {

```
*Github:* [[51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L51)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit consider length check for `positionIdList`
781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

```
*Github:* [[781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L781)]


```solidity
File: ./contracts/multicall/Multicall.sol

/// @audit consider length check for `data`
14:         for (uint256 i = 0; i < data.length; ) {

```
*Github:* [[14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L14)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

/// @audit consider length check for `ids`
143:         for (uint256 i = 0; i < ids.length; ) {

/// @audit consider length check for `owners`
187:             for (uint256 i = 0; i < owners.length; ++i) {

```
*Github:* [[143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L143), [187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L187)]



<a name="NC-11"></a> 
### [NC-11] Consider using descriptive `constant`s when passing zero as a function argument
Passing zero as a function argument can sometimes result in a security issue (e.g. passing zero as the slippage parameter). Consider using a `constant` variable with a descriptive name, so it's clear that the argument is intentionally being used, and for the right reasons.

<details>
<summary>
There are <b>62</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

712:                         LeftRightSigned
                                 .wrap(0)

```
*Github:* [[712](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L712)]


```solidity
File: ./contracts/PanopticPool.sol

634:             revert Errors.InvalidTokenIdParameter(0);

654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
                 .wrap(0)

762:                 s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
                         .wrap(0)

861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);

893:         _validatePositionList(user, positionIdList, 0);

1023:         _validatePositionList(liquidatee, positionIdList, 0);

1153:         _validatePositionList(msg.sender, positionIdListLiquidator, 0);

1165:         LeftRightSigned bonusAmounts = LeftRightSigned
                  .wrap(0)

1191:         _validatePositionList(msg.sender, positionIdListExercisor, 0);

1227:         _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

1545:                     premiaByLeg[leg] = LeftRightSigned
                              .wrap(0)
                              .toRightSlot(

1567:                         premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

1592:         _validatePositionList(owner, positionIdList, 0);
      
              TokenId tokenId = positionIdList[positionIdList.length - 1];

1614:             accumulatedPremium = LeftRightUnsigned
                      .wrap(0)
                      .toRightSlot(premiumAccumulator0)

1633:             LeftRightSigned realizedPremia = LeftRightSigned
                      .wrap(0)
                      .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1639:             s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1640:             s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

1707:                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
                          address(s_univ3pool),
                          address(this),
                          tokenId.tokenType(leg),
                          liquidityChunk.tickLower(),
                          liquidityChunk.tickUpper(),
                          type(int24).max,
                          0
                      );

1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned
                              .wrap(0)
                              .toRightSlot(

1774:                 LeftRightUnsigned
                          .wrap(0)
                          .toRightSlot(

1929:                             ? LeftRightUnsigned
                                      .wrap(0)
                                      .toRightSlot(

1934:                                             Math.max(
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

1951:                                             Math.max(
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

1965:                             : LeftRightUnsigned
                                      .wrap(0)
                                      .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))

```
*Github:* [[634](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L634), [654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L654), [762](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L762), [861](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L861), [870](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L870), [893](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L893), [1023](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1023), [1153](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1153), [1165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1165), [1191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1191), [1227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1227), [1545](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1545), [1567](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1567), [1592](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1592), [1614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1614), [1633](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1633), [1639](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1639), [1640](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1640), [1707](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1707), [1725](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1725), [1774](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1774), [1929](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1929), [1934](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1934), [1951](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1951), [1965](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1965)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

664:     /// @notice and then forwards the minting/burning/swapping to another internal helper functions which perform the AMM pool actions.

666:     ///   │mintTokenizedPosition()├───┐

862:     /// @return itmAmounts the amount of tokens swapped due to legs being in-the-money

878:         uint256 amount1;
     
             uint256 numLegs = tokenId.countLegs();

1063:                 └──┴───────┴──►      └──────┘
                          Uniswap v3      msg.sender 

1197:                     payer: msg.sender
                      })
              );
      
              /// mint the required amount in the Uniswap pool

1207:             liquidityChunk.liquidity(),
                  mintdata

1244:         }
          }
      
          /// @notice Helper to collect amounts between msg.sender and Uniswap and also to update the Uniswap fees collected to date from the AMM.

1266:         // This is because the stored feesBase is rounded up, and the current feesBase is rounded down.
              // When this is the case, we want to behave as if there are 0 fees, so we just rectify the values.

1334:         // explains how we get from the premium per liquidity (calculated here) to the total premia collected and the multiplier
              // as well as how the value of VEGOID affects the premia

1416:     /// @param owner The address of the account that is queried
          /// @param tokenType The tokenType of the position (the token it started as)

1431:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

```
*Github:* [[664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L664), [666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L666), [862](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L862), [878](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L878), [1063](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1063), [1197](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1197), [1207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1207), [1244](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1244), [1266](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1266), [1334](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1334), [1416](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1416), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1431)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));
         }
     
         /// @notice Calculates the fee growth that has occurred (per unit of liquidity) in the AMM/Uniswap for an

```
*Github:* [[118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L118)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

601:     /// @notice Compute the amount of funds that are moved to and removed from the Panoptic Pool.

673:                     tokenData1,
                         0,
                         sqrtPriceX96Twap
                     );
     
                     uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

695:             int256 balance1 = int256(uint256(tokenData1.rightSlot())) -
                     Math.max(premia.leftSlot(), 0);

698:             int256 paid0 = bonus0 + int256(netExchanged.rightSlot());
                 int256 paid1 = bonus1 + int256(netExchanged.leftSlot());

750:                     int128(balance1 - paid1)

792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);
                 int256 haircut0;

794:             int256 haircut1;
                 // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

882:                                 tokenId.tokenType(0)

883:                             )
                             );

886:                         // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount

890:                             uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
                             );

894:                             uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
                             );

899:                                 uint128(settled1)

935:                         .toRightSlot(int128(refundValues.rightSlot() - balanceShortage))

953:                         .toLeftSlot(int128(refundValues.leftSlot() - balanceShortage))
                             .toRightSlot(

```
*Github:* [[601](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L601), [673](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L673), [695](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L695), [698](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L698), [750](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L750), [792](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L792), [794](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L794), [857](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L857), [860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L860), [882](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L882), [883](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L883), [886](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L886), [890](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L890), [894](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L894), [899](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L899), [935](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L935), [953](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L953)]


```solidity
File: ./contracts/types/LeftRight.sol

265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

266:                     int128(Math.max(left128, 0))

294:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(

297:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(

```
*Github:* [[265](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L265), [266](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L266), [294](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L294), [297](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L297)]


```solidity
File: ./contracts/types/TokenId.sol

406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

```
*Github:* [[406](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L406), [501](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L501)]


</details>


<a name="NC-12"></a> 
### [NC-12] Constant decimal values
The use of fixed decimal values such as 1e18 or 1e8 in Solidity contracts can lead to inaccuracies, bugs, and vulnerabilities, particularly when interacting with tokens having different decimal configurations. Not all ERC20 tokens follow the standard 18 decimal places, and assumptions about decimal places can lead to miscalculations.

Resolution: Always retrieve and use the decimals() function from the token contract itself when performing calculations involving token amounts. This ensures that your contract correctly handles tokens with any number of decimal places, mitigating the risk of numerical errors or under/overflows that could jeopardize contract integrity and user funds.

*There is one instance of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

86:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

```
*Github:* [[86](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L86)]



<a name="NC-13"></a> 
### [NC-13] Constant redefined elsewhere
Consider defining in only one contract so that values cannot become out of sync when only one location is updated. A [cheap way](https://medium.com/coinmonks/gas-cost-of-solidity-library-functions-dbe0cedd4678) to store constants in a single location is to create an `internal constant` in a `library`. If the variable is a local cache of another contract's value, consider making the cache variable internal or private, which will require external users to query the contract with the source of truth, so that callers don't get out of sync.

*There is one instance of this issue:*
```solidity
File: ./contracts/libraries/Math.sol

/// @audit also seen in ./contracts/libraries/PanopticMath.sol
15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*Github:* [[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L15)]



<a name="NC-14"></a> 
### [NC-14] Constants should be put on the left side of comparisons
Putting constants on the left side of comparison statements is a best practice known as [Yoda conditions](https://en.wikipedia.org/wiki/Yoda_conditions). Although solidity's static typing system prevents accidental assignments within conditionals, adopting this practice can improve code readability and consistency, especially when working across multiple languages.

<details>
<summary>
There are <b>92</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

664:                 if (positionId.isLong(leg) == 0) continue;

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1107:             if (intrinsicValue != 0) {

1339:             if (isLong == 0) {

1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1479:         if (isLong == 0) {

1544:                 if (tokenType == 0) {

1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```
*Github:* [[331](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L331), [350](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L350), [512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L512), [575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L575), [664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L664), [708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L708), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1060), [1107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1107), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1339), [1347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1347), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1375), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1479), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1544), [1637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1638)]


```solidity
File: ./contracts/PanopticFactory.sol

224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

229:         if (address(s_getPanopticPool[v3Pool]) != address(0))

```
*Github:* [[224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L224), [227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L227), [229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L229)]


```solidity
File: ./contracts/PanopticPool.sol

299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

533:         if (medianData != 0) s_miniMedian = medianData;

638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

664:         if (medianData != 0) s_miniMedian = medianData;

865:             if (tokenId.isLong(leg) == 0) {

1483:         if (netLiquidity == 0) return;

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1679:             if (tokenId.isLong(leg) == 0) {

1780:                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),

1789:                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),

1862:             if (LeftRightSigned.unwrap(legPremia) != 0) {

```
*Github:* [[299](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L299), [460](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L460), [533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L533), [638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L638), [664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L664), [865](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L865), [1483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1483), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1596), [1679](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1679), [1780](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1780), [1789](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1789), [1862](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1862)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

362:         if (s_AddrToPoolIdData[univ3pool] != 0) return;

372:         while (address(s_poolContext[poolId].pool) != address(0)) {

632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

787:             if ((itm0 != 0) && (itm1 != 0)) {

823:             } else if (itm0 != 0) {

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

999:             if (isLong == 0) {

1078:             if (tokenType == 0) {

1279:         if (LeftRightSigned.unwrap(amountToCollect) != 0) {

1469:             if (netLiquidity != 0) {

```
*Github:* [[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L355), [362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L362), [372](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L372), [632](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L632), [633](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L633), [688](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L688), [717](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L717), [787](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L787), [823](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L823), [833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L833), [999](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L999), [1078](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1078), [1279](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1279), [1469](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1469)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

67:                 if (tokenId.isLong(leg) == 0) {

```
*Github:* [[67](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L67)]


```solidity
File: ./contracts/libraries/Math.sol

93:             if (x >= 0x100000000000000000000000000000000) {

97:             if (x >= 0x10000000000000000) {

101:             if (x >= 0x100000000) {

105:             if (x >= 0x10000) {

109:             if (x >= 0x100) {

113:             if (x >= 0x10) {

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

360:             if (prod1 == 0) {

474:             if (prod1 == 0) {

537:             if (prod1 == 0) {

614:             if (prod1 == 0) {

691:             if (prod1 == 0) {

```
*Github:* [[93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L93), [97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L97), [101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L109), [113](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L113), [137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L137), [139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L139), [141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L141), [143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L143), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L145), [147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L147), [149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L149), [151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L151), [153](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L153), [155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L155), [157](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L157), [159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L159), [161](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L161), [163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L163), [165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L165), [167](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L167), [169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L169), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L171), [173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L173), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L179), [360](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L360), [474](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L474), [537](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L537), [614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L614), [691](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L691)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

325:         if (tokenId.asset(legIndex) == 0) {

425:         if (tokenType == 0) {

479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

584:         if (tokenId.asset(legIndex) == 0) {

615:         bool isShort = tokenId.isLong(legIndex) == 0;

618:         if (tokenId.tokenType(legIndex) == 0) {

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

```
*Github:* [[325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L325), [425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L425), [479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L479), [584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L584), [615](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L615), [618](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L618), [856](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L857)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

112:         if (to.code.length != 0) {

163:         if (to.code.length != 0) {

222:         if (to.code.length != 0) {

```
*Github:* [[112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L112), [163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L163), [222](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L222)]


```solidity
File: ./contracts/types/TokenId.sol

465:         if (i == 0)

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

508:                 if (self.optionRatio(i) == 0) {

512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

```
*Github:* [[465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L465), [501](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L501), [508](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L508), [512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L512), [528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L528)]


</details>


<a name="NC-15"></a> 
### [NC-15] `Constructor` should emit an event
Use events to signal significant changes to off-chain monitoring tools.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

178:     constructor(

```
*Github:* [[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178)]


```solidity
File: ./contracts/PanopticFactory.sol

115:     constructor(

```
*Github:* [[115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L115)]


```solidity
File: ./contracts/PanopticPool.sol

280:     constructor(SemiFungiblePositionManager _sfpm) {

```
*Github:* [[280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L280)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

```
*Github:* [[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L355)]



<a name="NC-16"></a> 
### [NC-16] Contract does not follow the Solidity Style Guide's suggested layout ordering
The [style guide](https://docs.soliditylang.org/en/v0.8.16/style-guide.html#order-of-layout) says that, within a contract, the ordering should be `1) Type declarations`, `2) State variables`, `3) Events`, `4) Modifiers`, and `5) Functions`, but the contract(s) below do not follow this ordering

<details>
<summary>
There are <b>81</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
70:     string internal constant TICKER_PREFIX = "po";

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
73:     string internal constant NAME_PREFIX = "POPT-V1";

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
77:     uint256 internal constant DECIMALS = 10_000;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
81:     int128 internal constant DECIMALS_128 = 10_000;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
89:     address internal s_underlyingToken;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
93:     bool internal s_initialized;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
96:     address internal s_univ3token0;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
99:     address internal s_univ3token1;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
102:     bool internal s_underlyingIsToken0;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
109:     PanopticPool internal s_panopticPool;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
112:     uint128 internal s_poolAssets;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
115:     uint128 internal s_inAMM;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
121:     uint128 internal s_ITMSpreadFee;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
124:     uint24 internal s_poolFee;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
131:     uint256 immutable TICK_DEVIATION;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
136:     uint256 immutable COMMISSION_FEE;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
141:     uint256 immutable SELLER_COLLATERAL_RATIO;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
145:     uint256 immutable BUYER_COLLATERAL_RATIO;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
149:     int256 immutable FORCE_EXERCISE_COST;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
154:     uint256 immutable TARGET_POOL_UTIL;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
158:     uint256 immutable SATURATED_POOL_UTIL;

/// @audit event/error `Deposit` came earlier
/// @audit event/error `Withdraw` came earlier
162:     uint256 immutable ITM_SPREAD_MULTIPLIER;

```
*Github:* [[70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L73), [77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L81), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L89), [93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L93), [96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L109), [112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L112), [115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L115), [121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L121), [124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L124), [131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L131), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L136), [141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L141), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L145), [149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L149), [154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L154), [158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L158), [162](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L162)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
63:     IUniswapV3Factory internal immutable UNIV3_FACTORY;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
66:     SemiFungiblePositionManager internal immutable SFPM;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
69:     IDonorNFT internal immutable DONOR_NFT;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
72:     address internal immutable POOL_REFERENCE;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
75:     address internal immutable COLLATERAL_REFERENCE;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
78:     address internal immutable WETH;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
82:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
86:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
89:     uint16 internal constant CARDINALITY_INCREASE = 100;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
96:     address internal s_owner;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
99:     bool internal s_initialized;

/// @audit event/error `OwnershipTransferred` came earlier
/// @audit event/error `PoolDeployed` came earlier
102:     mapping(IUniswapV3Pool univ3pool => PanopticPool panopticPool) internal s_getPanopticPool;

```
*Github:* [[63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L66), [69](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L69), [72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L72), [75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L75), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L78), [82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L82), [86](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L86), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L89), [96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L102)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
109:     bool internal constant COMPUTE_ALL_PREMIA = true;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
111:     bool internal constant COMPUTE_LONG_PREMIA = false;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
114:     bool internal constant ONLY_AVAILABLE_PREMIUM = false;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
119:     bool internal constant COMMIT_LONG_SETTLED = true;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
120:     bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
123:     bool internal constant ADD = true;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
128:     uint32 internal constant TWAP_WINDOW = 600;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
133:     bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
136:     uint256 internal constant MEDIAN_PERIOD = 60;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
139:     uint256 internal constant FAST_ORACLE_CARDINALITY = 3;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
145:     uint256 internal constant FAST_ORACLE_PERIOD = 1;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
148:     uint256 internal constant SLOW_ORACLE_CARDINALITY = 7;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
152:     uint256 internal constant SLOW_ORACLE_PERIOD = 5;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
156:     int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
160:     int256 internal constant MAX_SLOW_FAST_DELTA = 1800;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
168:     uint64 internal constant MAX_POSITIONS = 32;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
171:     uint256 internal constant BP_DECREASE_BUFFER = 13_333;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
174:     uint256 internal constant NO_BUFFER = 10_000;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
179:     SemiFungiblePositionManager internal immutable SFPM;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
186:     IUniswapV3Pool internal s_univ3pool;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
225:     uint256 internal s_miniMedian;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
231:     CollateralTracker internal s_collateralToken0;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
233:     CollateralTracker internal s_collateralToken1;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
245:     mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
251:     mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))

/// @audit event/error `AccountLiquidated` came earlier
/// @audit event/error `ForcedExercised` came earlier
/// @audit event/error `PremiumSettled` came earlier
/// @audit event/error `OptionBurnt` came earlier
/// @audit event/error `OptionMinted` came earlier
272:     mapping(address account => uint256 positionsHash) internal s_positionsHash;

```
*Github:* [[103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L109), [111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L111), [114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L114), [119](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L119), [120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L120), [123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L123), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L128), [133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L133), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L136), [139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L139), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L145), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L148), [152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L152), [156](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L156), [160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L160), [165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L165), [168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L168), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L171), [174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L174), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L179), [186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L186), [225](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L225), [231](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L231), [233](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L233), [238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L238), [245](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L245), [251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L251), [258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L258), [272](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L272)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
130:     // and vegoid modifies the sensitivity of the streamia to changes in that utilization,

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
133:     uint128 private constant VEGOID = 2;

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
135:     /// @dev Uniswap V3 Factory address. Initialized in the constructor.

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
144:     /// @dev pool address => pool id + 2 ** 255 (initialization bit for `poolId == 0`, set if the pool exists)

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
147:     /// @dev also contains a boolean which is used for the reentrancy lock - saves gas since this slot is often warmed

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
155:              net amount    

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
163:           │  │    │         │    │         │    │     

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
190:         Let`s say Charlie the smart contract deposited T into the AMM and later removed R from that

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
295:     mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
297:     /*//////////////////////////////////////////////////////////////

/// @audit event/error `PoolInitialized` came earlier
/// @audit event/error `TokenizedPositionBurnt` came earlier
/// @audit event/error `TokenizedPositionMinted` came earlier
310:         // execute function

```
*Github:* [[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L130), [133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L133), [135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L135), [144](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L144), [147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L147), [155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L155), [163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L163), [190](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L190), [295](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L295), [297](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L297), [310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L310)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

/// @audit event/error `TransferSingle` came earlier
/// @audit event/error `TransferBatch` came earlier
/// @audit event/error `ApprovalForAll` came earlier
/// @audit event/error `NotAuthorized` came earlier
/// @audit event/error `UnsafeRecipient` came earlier
66:     mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;

/// @audit event/error `TransferSingle` came earlier
/// @audit event/error `TransferBatch` came earlier
/// @audit event/error `ApprovalForAll` came earlier
/// @audit event/error `NotAuthorized` came earlier
/// @audit event/error `UnsafeRecipient` came earlier
71:     mapping(address owner => mapping(address operator => bool approvedForAll))

```
*Github:* [[66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L66), [71](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L71)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

/// @audit event/error `Transfer` came earlier
/// @audit event/error `Approval` came earlier
32:     uint256 public totalSupply;

/// @audit event/error `Transfer` came earlier
/// @audit event/error `Approval` came earlier
35:     mapping(address account => uint256 balance) public balanceOf;

/// @audit event/error `Transfer` came earlier
/// @audit event/error `Approval` came earlier
39:     mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;

```
*Github:* [[32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L32), [35](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L35), [39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L39)]


</details>


<a name="NC-17"></a> 
### [NC-17] Contract should expose an `interface`
All `external`/`public` functions should extend an `interface`. This is useful to make sure that the whole API is extracted.

*Note:* It is possible that the interface is out-of-scope and has not been seen by the bot.

<details>
<summary>
There are <b>73</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

221:     function startToken(

277:     function getPoolData()

289:     function name() external view returns (string memory) {

303:     function symbol() external view returns (string memory) {

310:     function decimals() external view returns (uint8) {

341:     function transferFrom(

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

898:     /// @notice Refunds delegated tokens back to the protocol

907:     /// @notice Revoke previously delegated shares. The opposite of 'delegate'.

917:                 ┌────────┐

980:                 _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));

1002:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid

1051:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid

1147:         tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);

```
*Github:* [[221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L221), [277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L277), [289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L310), [341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L341), [361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L370), [379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392), [399](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L399), [417](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L417), [444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444), [453](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L453), [477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L477), [507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L507), [518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L518), [531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L531), [572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L581), [591](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L591), [650](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L650), [864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L864), [898](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L898), [907](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L907), [917](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L917), [980](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L980), [1002](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1002), [1051](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1051), [1147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1147)]


```solidity
File: ./contracts/PanopticFactory.sol

134:     function initialize(address _owner) public {

147:     function transferOwnership(address newOwner) external {

159:     function owner() external view returns (address) {

172:     function uniswapV3MintCallback(

210:     function deployNewPool(

290:     function minePoolAddress(

420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {

```
*Github:* [[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L134), [147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L147), [159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L159), [172](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L172), [210](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L210), [290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L290), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L420)]


```solidity
File: ./contracts/PanopticPool.sol

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
*Github:* [[291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L291), [338](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L338), [352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L352), [381](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L381), [410](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L410), [522](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L522), [547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L547), [569](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L569), [586](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L586), [1017](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1017), [1179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1179), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1425), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1437), [1444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1444), [1587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1587)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

361:         // if poolId == 0, we have a bit on the left set if it was initialized, so this will still return properly

421:                 decoded.poolFeatures.token1,

450:         // Transform the amount to pay to uint256 (take positive one from amount0 and amount1)

492:             slippageTickLimitHigh,

524:             slippageTickLimitHigh,

555:         super.safeTransferFrom(from, to, id, amount, data);

583:         // transfer the token (note that all state updates are completed before reentrancy is possible)

1445:     /// @param atTick The current tick. Set atTick < type(int24).max = 8388608 to get latest premium up to the current block

1479:                     // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])

1570: 

1570: 

1570: 

```
*Github:* [[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L361), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L421), [450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L450), [492](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L492), [524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L524), [555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L555), [583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L583), [1445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1445), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1479), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570)]


```solidity
File: ./contracts/multicall/Multicall.sol

12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {

```
*Github:* [[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L12)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

81:     function setApprovalForAll(address operator, bool approved) public {

94:     function safeTransferFrom(

130:     function safeBatchTransferFrom(

178:     function balanceOfBatch(

200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

```
*Github:* [[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L81), [94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L94), [130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L130), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L178), [200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L200)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

```
*Github:* [[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L81)]


</details>


<a name="NC-18"></a> 
### [NC-18] Contracts should have full test coverage
While 100% code coverage does not guarantee that there are no bugs, it often will catch easy-to-find bugs, and will ensure that there are fewer regressions when the code invariably has to be modified. Furthermore, in order to get full coverage, code authors will often have to re-organize their code so that it is more modular, so that each component can be tested separately, which reduces interdependencies between modules and layers, and makes for code that is easier to reason about and audit.

*There is one instance of this issue:*
```solidity

Global finding

```
*Github:* [[Global](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/)]



<a name="NC-19"></a> 
### [NC-19] Convert simple `if` statements to ternary expressions
Converting some if statements to ternaries (such as `z = (a < b) ? x : y`) can make the code more concise and easier to read.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

1550:                         ? movedPartnerLeft - movedLeft
                              : movedLeft - movedPartnerLeft;
                      }
                  }
              } else {
                  unchecked {
                      uint256 notional;
                      uint256 notionalP;
                      uint128 contracts;

```
*Github:* [[1550](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1550)]


```solidity
File: ./contracts/types/TokenId.sol

382:             } else if (optionRatios < 2 ** 208) {
                     optionRatios = 3;
                 } else {
                     optionRatios = 4;

```
*Github:* [[382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L382)]



<a name="NC-20"></a> 
### [NC-20] Events that mark critical parameter changes should contain both the old and the new value
This should especially be done if the new value is not required to be different from the old value.

<details>
<summary>
There are <b>24</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

439:         emit Deposit(msg.sender, receiver, assets, shares);

499:         emit Deposit(msg.sender, receiver, assets, shares);

563:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

623:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

```
*Github:* [[439](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L439), [499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L499), [563](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L563), [623](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L623)]


```solidity
File: ./contracts/PanopticFactory.sol

154:         emit OwnershipTransferred(currentOwner, newOwner);

```
*Github:* [[154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L154)]


```solidity
File: ./contracts/PanopticPool.sol

666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);

853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

1170:         emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

1277:         emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

1654:             emit PremiumSettled(owner, tokenId, realizedPremia);

```
*Github:* [[666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L666), [853](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L853), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1170), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1277), [1654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1654)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

390:         emit PoolInitialized(univ3pool, poolId);

485:         emit TokenizedPositionBurnt(msg.sender, tokenId, positionSize);

517:         emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);

```
*Github:* [[390](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L390), [485](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L485), [517](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L517)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

84:         emit ApprovalForAll(msg.sender, operator, approved);

110:         emit TransferSingle(msg.sender, from, to, id, amount);

161:         emit TransferBatch(msg.sender, from, to, ids, amounts);

220:         emit TransferSingle(msg.sender, address(0), to, id, amount);

239:         emit TransferSingle(msg.sender, from, address(0), id, amount);

```
*Github:* [[84](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L84), [110](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L110), [161](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L161), [220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L220), [239](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L239)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

52:         emit Approval(msg.sender, spender, amount);

70:         emit Transfer(msg.sender, to, amount);

94:         emit Transfer(from, to, amount);

112:         emit Transfer(from, to, amount);

130:         emit Transfer(address(0), to, amount);

145:         emit Transfer(from, address(0), amount);

```
*Github:* [[52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L52), [70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L70), [94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L94), [112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L112), [130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L130), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L145)]


</details>


<a name="NC-21"></a> 
### [NC-21] Custom errors has no error details
Consider adding parameters to the error to indicate which user or values caused the failure.

<details>
<summary>
There are <b>34</b> instances (click to show):
</summary>

```solidity
File: ./contracts/libraries/Errors.sol

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
*Github:* [[10](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L10), [13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L13), [16](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L16), [20](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L20), [23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L26), [29](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L29), [32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L32), [35](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L35), [38](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L38), [45](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L45), [48](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L48), [51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L51), [54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L54), [57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L57), [60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L60), [63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L73), [76](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L76), [79](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L79), [82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L82), [85](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L85), [88](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L88), [91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L91), [95](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L95), [98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L98), [101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L105), [108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L108), [111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L111)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

55:     error NotAuthorized();

58:     error UnsafeRecipient();

```
*Github:* [[55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L55), [58](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L58)]


</details>


<a name="NC-22"></a> 
### [NC-22] Solidity version is different in some files

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L2)]


```solidity
File: ./contracts/libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L2)]



<a name="NC-23"></a> 
### [NC-23] Polymorphic functions make security audits more time-consuming and error-prone
The instances below point to one of two functions with the same name. Consider naming each function differently, in order to make code navigation and analysis easier.

<details>
<summary>
There are <b>15</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit also found on line 898
864:     function delegate(

/// @audit also found on line 980
907:     /// @notice Revoke previously delegated shares. The opposite of 'delegate'.

```
*Github:* [[864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L864), [907](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L907)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit also found on line 586
569:     function burnOptions(

```
*Github:* [[569](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L569)]


```solidity
File: ./contracts/libraries/Math.sol

/// @audit also found on line 49
41:     function min(uint256 a, uint256 b) internal pure returns (uint256) {

/// @audit also found on line 65
57:     function max(uint256 a, uint256 b) internal pure returns (uint256) {

/// @audit also found on line 318
311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

```
*Github:* [[41](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L41), [57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L57), [311](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L311)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit also found on line 447
421:         LeftRightUnsigned tokenData1,

/// @audit also found on line 524
490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

/// @audit also found on line 547
507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

```
*Github:* [[421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L421), [490](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L490), [507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L507)]


```solidity
File: ./contracts/types/LeftRight.sol

/// @audit also found on line 46
39:     function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

/// @audit also found on line 78
59:     function toRightSlot(

/// @audit also found on line 108
101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

/// @audit also found on line 134
121:     function toLeftSlot(

/// @audit also found on line 194
148:     function add(

/// @audit also found on line 232
171:     function sub(

```
*Github:* [[39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L39), [59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L59), [101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L101), [121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L121), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L148), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L171)]


</details>


<a name="NC-24"></a> 
### [NC-24] Duplicated `require()`/`revert()` checks should be refactored
Refactoring duplicate `require()`/`revert()` checks into a modifier or function can make the code more concise, readable and maintainable, and less likely to make errors or omissions when modifying the `require()` or `revert()`.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/libraries/Math.sol

/// @audit duplicated on line 588
448:                 require(result < type(uint256).max);

```
*Github:* [[448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L448)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

/// @audit duplicated on line 168
117:                 revert UnsafeRecipient();

```
*Github:* [[117](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L117)]



<a name="NC-25"></a> 
### [NC-25] `else` block not required
One level of nesting can be removed by not having an `else` block when the `if`-block always jumps at the end. For example:
```solidity
if (condition) {
	body1...
	return x;
} else {
	body2...
}
```
can be changed to:
```solidity
if (condition) {
	body1...
	return x;
}
body2...
```

*There are <b>6</b> instances of this issue:*
```solidity
File: ./contracts/libraries/PanopticMath.sol

326:             return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
             } else {
                 return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
             }
         }

427:                 tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
                     tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
                 );
             } else {
                 return (
                     tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),

495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
                 } else {
                     return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
                 } else {
                     return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
                         .toInt256();
                     return amount < 0 ? -absResult : absResult;
                 } else {
                     int256 absResult = Math
                         .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
                         .toInt256();
                     return amount < 0 ? -absResult : absResult;
                 } else {
                     int256 absResult = Math
                         .mulDiv(
                             Math.absUint(amount),

```
*Github:* [[326](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L326), [427](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L427), [495](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L495), [512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L512), [530](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L530), [553](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L553)]



<a name="NC-26"></a> 
### [NC-26] Empty bytes check is missing
Passing empty bytes to a function can cause unexpected behavior, such as certain operations failing, producing incorrect results, or wasting gas. It is recommended to check that all byte parameters are not empty.

*There are <b>7</b> instances of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

/// @audit missing empty check for `data`
172:     function uniswapV3MintCallback(
             uint256 amount0Owed,
             uint256 amount1Owed,
             bytes calldata data
         ) external {

```
*Github:* [[172](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L172)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit missing empty check for `data`
421:                 decoded.poolFeatures.token1,
                     decoded.payer,
                     msg.sender,
                     amount1Owed
                 );

/// @audit missing empty check for `data`
450:         // Transform the amount to pay to uint256 (take positive one from amount0 and amount1)
             // the pool will always pass one delta with a positive sign and one with a negative sign or zero,
             // so this logic always picks the correct delta to pay

/// @audit missing empty check for `data`
555:         super.safeTransferFrom(from, to, id, amount, data);
         }
     
         /// @notice Transfer multiple tokens from one user to another
         /// @dev supports token approvals
         /// @dev ids and amounts must be of equal length

/// @audit missing empty check for `data`
583:         // transfer the token (note that all state updates are completed before reentrancy is possible)
             super.safeBatchTransferFrom(from, to, ids, amounts, data);
         }
     
         /// @notice update user position data following a token transfer
         /// @dev token transfers are only allowed if you transfer your entire liquidity of a given chunk and the recipient has none

```
*Github:* [[421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L421), [450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L450), [555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L555), [583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L583)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

/// @audit missing empty check for `data`
94:     function safeTransferFrom(
            address from,
            address to,
            uint256 id,
            uint256 amount,
            bytes calldata data
        ) public virtual {

/// @audit missing empty check for `data`
130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {

```
*Github:* [[94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L94), [130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L130)]



<a name="NC-27"></a> 
### [NC-27] Enable IR-based code generation
The IR-based code generator was introduced with an aim to not only allow code generation to be more transparent and auditable but also to enable more powerful optimization passes that span across functions. You can enable it on the command line using `--via-ir` or with the option `{"viaIR": true}`. This will take longer to compile, but you can just simple test it before deploying and if you got a better benchmark then you can add --via-ir to your deploy command More on: https://docs.soliditylang.org/en/v0.8.17/ir-breaking-changes.html

*There is one instance of this issue:*
```solidity

Global finding

```
*Github:* [[Global](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/)]



<a name="NC-28"></a> 
### [NC-28] Enum values should be used instead of constant array indexes
Create a commented enum value to use instead of constant array indexes, this makes the code far easier to understand.

<details>
<summary>
There are <b>26</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

1219:             uint256 _tokenRequired = _getRequiredCollateralAtTickSinglePosition(

1224:             );

```
*Github:* [[1216](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1216), [1219](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1219), [1224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1224)]


```solidity
File: ./contracts/PanopticPool.sol

444:             balances[k][0] = TokenId.unwrap(tokenId);

445:             balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);

452:                     LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),

1193:         uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();

1198:             .computeExercisedAmounts(touchedId[0], positionBalance);

1219:         touchedId[0].validateIsExercisable(twapTick);

1234:             touchedId[0],

1277:         emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

1528:                 (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM

1528:                 (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM

1550:                                     ((premiumAccumulatorsByLeg[leg][0] -

1559:                                     ((premiumAccumulatorsByLeg[leg][1] -

1707:                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(

1707:                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(

1729:                                 (grossCurrent[0] *

1737:                                 (grossCurrent[1] *

1768:             uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *

1770:             uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *

1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *

1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *

1967:                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))

1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));

```
*Github:* [[444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L444), [445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L445), [452](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L452), [1193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1193), [1198](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1198), [1219](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1219), [1234](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1234), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1277), [1528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1528), [1528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1528), [1550](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1550), [1559](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1559), [1707](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1707), [1707](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1707), [1729](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1729), [1737](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1737), [1768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1768), [1770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1770), [1940](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1940), [1957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1957), [1967](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1967), [1968](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1968)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

266:             return int24(sortedTicks[10]);

```
*Github:* [[266](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L266)]


</details>


<a name="NC-29"></a> 
### [NC-29] Events are emitted without the sender information
When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the `msg.sender` the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

*There are <b>8</b> instances of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

154:         emit OwnershipTransferred(currentOwner, newOwner);

268:         emit PoolDeployed(

```
*Github:* [[154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L154), [268](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L268)]


```solidity
File: ./contracts/PanopticPool.sol

853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

```
*Github:* [[853](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L853)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

406:     ) external {

```
*Github:* [[406](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L406)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

94:         emit Transfer(from, to, amount);

112:         emit Transfer(from, to, amount);

130:         emit Transfer(address(0), to, amount);

145:         emit Transfer(from, address(0), amount);

```
*Github:* [[94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L94), [112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L112), [130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L130), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L145)]



<a name="NC-30"></a> 
### [NC-30] Events may be emitted out of order due to reentrancy
Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls.

*There are <b>5</b> instances of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `.getPool(...)` is called on line 226
/// @audit `.initializeAMMPool(...)` is called on line 233
/// @audit `.cloneDeterministic(...)` is called on line 237
/// @audit `.startToken(...)` is called on line 248
/// @audit `.startToken(...)` is called on line 249
/// @audit `.startPool(...)` is called on line 251
/// @audit `.increaseObservationCardinalityNext(...)` is called on line 258
/// @audit `.issueNFT(...)` is called on line 266
268:         emit PoolDeployed(

```
*Github:* [[268](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L268)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `.getPoolId(...)` is called on line 633
666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);

/// @audit `.slot0(...)` is called on line 1032
/// @audit `.getAccountMarginDetails(...)` is called on line 1046
/// @audit `.getAccountMarginDetails(...)` is called on line 1053
/// @audit `.delegate(...)` is called on line 1072
/// @audit `.delegate(...)` is called on line 1073
/// @audit `.slot0(...)` is called on line 1094
/// @audit `.revoke(...)` is called on line 1141
/// @audit `.revoke(...)` is called on line 1146
1170:         emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

/// @audit `.slot0(...)` is called on line 1202
/// @audit `.delegate(...)` is called on line 1222
/// @audit `.delegate(...)` is called on line 1223
/// @audit `.exerciseCost(...)` is called on line 1231
/// @audit `.refund(...)` is called on line 1252
/// @audit `.refund(...)` is called on line 1257
/// @audit `.refund(...)` is called on line 1265
/// @audit `.refund(...)` is called on line 1266
1277:         emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

/// @audit `.slot0(...)` is called on line 1598
/// @audit `.getAccountPremium(...)` is called on line 1605
/// @audit `.exercise(...)` is called on line 1639
/// @audit `.exercise(...)` is called on line 1640
1654:             emit PremiumSettled(owner, tokenId, realizedPremia);

```
*Github:* [[666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L666), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1170), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1277), [1654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1654)]



<a name="NC-31"></a> 
### [NC-31]  Function ordering does not follow the Solidity Style Guide
According to the [solidity style guide](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-functions), functions should be laid out in the following order: `constructor()`, `receive()`, `fallback()`, `external`, `public`, `internal`, `private`, but the cases below do not follow this pattern

<details>
<summary>
There are <b>56</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
361:     function asset() external view returns (address assetTokenAddress) {

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
444:     function maxMint(address) external view returns (uint256 maxShares) {

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
531:     function withdraw(

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
591:     function redeem(

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
650:     function exerciseCost(

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
/// @audit internal function `_poolUtilization` came earlier from this external function
/// @audit internal function `_sellCollateralRatio` came earlier from this external function
/// @audit internal function `_buyCollateralRatio` came earlier from this external function
864:     function delegate(

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
/// @audit internal function `_poolUtilization` came earlier from this external function
/// @audit internal function `_sellCollateralRatio` came earlier from this external function
/// @audit internal function `_buyCollateralRatio` came earlier from this external function
898:     /// @notice Refunds delegated tokens back to the protocol

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
/// @audit internal function `_poolUtilization` came earlier from this external function
/// @audit internal function `_sellCollateralRatio` came earlier from this external function
/// @audit internal function `_buyCollateralRatio` came earlier from this external function
907:     /// @notice Revoke previously delegated shares. The opposite of 'delegate'.

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
/// @audit internal function `_poolUtilization` came earlier from this external function
/// @audit internal function `_sellCollateralRatio` came earlier from this external function
/// @audit internal function `_buyCollateralRatio` came earlier from this external function
917:                 ┌────────┐

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
/// @audit internal function `_poolUtilization` came earlier from this external function
/// @audit internal function `_sellCollateralRatio` came earlier from this external function
/// @audit internal function `_buyCollateralRatio` came earlier from this external function
980:                 _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
/// @audit internal function `_poolUtilization` came earlier from this external function
/// @audit internal function `_sellCollateralRatio` came earlier from this external function
/// @audit internal function `_buyCollateralRatio` came earlier from this external function
1002:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid

/// @audit public function `transfer` came earlier from this external function
/// @audit public function `transferFrom` came earlier from this external function
/// @audit public function `totalAssets` came earlier from this external function
/// @audit public function `convertToShares` came earlier from this external function
/// @audit public function `convertToAssets` came earlier from this external function
/// @audit public function `previewDeposit` came earlier from this external function
/// @audit public function `previewMint` came earlier from this external function
/// @audit public function `maxWithdraw` came earlier from this external function
/// @audit public function `previewWithdraw` came earlier from this external function
/// @audit public function `maxRedeem` came earlier from this external function
/// @audit public function `previewRedeem` came earlier from this external function
/// @audit internal function `_poolUtilization` came earlier from this external function
/// @audit internal function `_sellCollateralRatio` came earlier from this external function
/// @audit internal function `_buyCollateralRatio` came earlier from this external function
1051:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid

/// @audit internal function `_poolUtilization` came earlier from this public function
/// @audit internal function `_sellCollateralRatio` came earlier from this public function
/// @audit internal function `_buyCollateralRatio` came earlier from this public function
/// @audit internal function `_getExchangedAmount` came earlier from this public function
1147:         tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);

```
*Github:* [[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L361), [392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392), [417](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L417), [444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444), [477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L477), [531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L531), [591](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L591), [650](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L650), [864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L864), [898](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L898), [907](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L907), [917](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L917), [980](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L980), [1002](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1002), [1051](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1051), [1147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1147)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit public function `initialize` came earlier from this external function
147:     function transferOwnership(address newOwner) external {

/// @audit public function `initialize` came earlier from this external function
159:     function owner() external view returns (address) {

/// @audit public function `initialize` came earlier from this external function
172:     function uniswapV3MintCallback(

/// @audit public function `initialize` came earlier from this external function
210:     function deployNewPool(

/// @audit public function `initialize` came earlier from this external function
290:     function minePoolAddress(

/// @audit public function `initialize` came earlier from this external function
/// @audit internal function `_mintFullRange` came earlier from this external function
420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {

```
*Github:* [[147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L147), [159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L159), [172](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L172), [210](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L210), [290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L290), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L420)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
522:     function pokeMedian() external {

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
547:     function mintOptions(

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
569:     function burnOptions(

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
586:     function burnOptions(

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
/// @audit internal function `_mintOptions` came earlier from this external function
/// @audit internal function `_mintInSFPMAndUpdateCollateral` came earlier from this external function
/// @audit internal function `_payCommissionAndWriteData` came earlier from this external function
/// @audit internal function `_addUserOption` came earlier from this external function
/// @audit internal function `_burnAllOptionsFrom` came earlier from this external function
/// @audit internal function `_burnOptions` came earlier from this external function
/// @audit internal function `_updatePositionDataBurn` came earlier from this external function
/// @audit internal function `_validateSolvency` came earlier from this external function
/// @audit internal function `_burnAndHandleExercise` came earlier from this external function
1017:     function liquidate(

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
/// @audit internal function `_mintOptions` came earlier from this external function
/// @audit internal function `_mintInSFPMAndUpdateCollateral` came earlier from this external function
/// @audit internal function `_payCommissionAndWriteData` came earlier from this external function
/// @audit internal function `_addUserOption` came earlier from this external function
/// @audit internal function `_burnAllOptionsFrom` came earlier from this external function
/// @audit internal function `_burnOptions` came earlier from this external function
/// @audit internal function `_updatePositionDataBurn` came earlier from this external function
/// @audit internal function `_validateSolvency` came earlier from this external function
/// @audit internal function `_burnAndHandleExercise` came earlier from this external function
1179:     function forceExercise(

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
/// @audit internal function `_mintOptions` came earlier from this external function
/// @audit internal function `_mintInSFPMAndUpdateCollateral` came earlier from this external function
/// @audit internal function `_payCommissionAndWriteData` came earlier from this external function
/// @audit internal function `_addUserOption` came earlier from this external function
/// @audit internal function `_burnAllOptionsFrom` came earlier from this external function
/// @audit internal function `_burnOptions` came earlier from this external function
/// @audit internal function `_updatePositionDataBurn` came earlier from this external function
/// @audit internal function `_validateSolvency` came earlier from this external function
/// @audit internal function `_burnAndHandleExercise` came earlier from this external function
/// @audit internal function `_checkSolvencyAtTick` came earlier from this external function
/// @audit internal function `_getSolvencyBalances` came earlier from this external function
/// @audit internal function `_validatePositionList` came earlier from this external function
/// @audit internal function `_updatePositionsHash` came earlier from this external function
1425:     function univ3pool() external view returns (IUniswapV3Pool) {

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
/// @audit internal function `_mintOptions` came earlier from this external function
/// @audit internal function `_mintInSFPMAndUpdateCollateral` came earlier from this external function
/// @audit internal function `_payCommissionAndWriteData` came earlier from this external function
/// @audit internal function `_addUserOption` came earlier from this external function
/// @audit internal function `_burnAllOptionsFrom` came earlier from this external function
/// @audit internal function `_burnOptions` came earlier from this external function
/// @audit internal function `_updatePositionDataBurn` came earlier from this external function
/// @audit internal function `_validateSolvency` came earlier from this external function
/// @audit internal function `_burnAndHandleExercise` came earlier from this external function
/// @audit internal function `_checkSolvencyAtTick` came earlier from this external function
/// @audit internal function `_getSolvencyBalances` came earlier from this external function
/// @audit internal function `_validatePositionList` came earlier from this external function
/// @audit internal function `_updatePositionsHash` came earlier from this external function
1431:     function collateralToken0() external view returns (CollateralTracker collateralToken) {

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
/// @audit internal function `_mintOptions` came earlier from this external function
/// @audit internal function `_mintInSFPMAndUpdateCollateral` came earlier from this external function
/// @audit internal function `_payCommissionAndWriteData` came earlier from this external function
/// @audit internal function `_addUserOption` came earlier from this external function
/// @audit internal function `_burnAllOptionsFrom` came earlier from this external function
/// @audit internal function `_burnOptions` came earlier from this external function
/// @audit internal function `_updatePositionDataBurn` came earlier from this external function
/// @audit internal function `_validateSolvency` came earlier from this external function
/// @audit internal function `_burnAndHandleExercise` came earlier from this external function
/// @audit internal function `_checkSolvencyAtTick` came earlier from this external function
/// @audit internal function `_getSolvencyBalances` came earlier from this external function
/// @audit internal function `_validatePositionList` came earlier from this external function
/// @audit internal function `_updatePositionsHash` came earlier from this external function
1437:     function collateralToken1() external view returns (CollateralTracker) {

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this public function
/// @audit internal function `_getSlippageLimits` came earlier from this public function
/// @audit internal function `_mintOptions` came earlier from this public function
/// @audit internal function `_mintInSFPMAndUpdateCollateral` came earlier from this public function
/// @audit internal function `_payCommissionAndWriteData` came earlier from this public function
/// @audit internal function `_addUserOption` came earlier from this public function
/// @audit internal function `_burnAllOptionsFrom` came earlier from this public function
/// @audit internal function `_burnOptions` came earlier from this public function
/// @audit internal function `_updatePositionDataBurn` came earlier from this public function
/// @audit internal function `_validateSolvency` came earlier from this public function
/// @audit internal function `_burnAndHandleExercise` came earlier from this public function
/// @audit internal function `_checkSolvencyAtTick` came earlier from this public function
/// @audit internal function `_getSolvencyBalances` came earlier from this public function
/// @audit internal function `_validatePositionList` came earlier from this public function
/// @audit internal function `_updatePositionsHash` came earlier from this public function
1444:     function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

/// @audit internal function `_calculateAccumulatedPremia` came earlier from this external function
/// @audit internal function `_getSlippageLimits` came earlier from this external function
/// @audit internal function `_mintOptions` came earlier from this external function
/// @audit internal function `_mintInSFPMAndUpdateCollateral` came earlier from this external function
/// @audit internal function `_payCommissionAndWriteData` came earlier from this external function
/// @audit internal function `_addUserOption` came earlier from this external function
/// @audit internal function `_burnAllOptionsFrom` came earlier from this external function
/// @audit internal function `_burnOptions` came earlier from this external function
/// @audit internal function `_updatePositionDataBurn` came earlier from this external function
/// @audit internal function `_validateSolvency` came earlier from this external function
/// @audit internal function `_burnAndHandleExercise` came earlier from this external function
/// @audit internal function `_checkSolvencyAtTick` came earlier from this external function
/// @audit internal function `_getSolvencyBalances` came earlier from this external function
/// @audit internal function `_validatePositionList` came earlier from this external function
/// @audit internal function `_updatePositionsHash` came earlier from this external function
/// @audit public function `numberOfPositions` came earlier from this external function
/// @audit internal function `getUniV3TWAP` came earlier from this external function
/// @audit internal function `_checkLiquiditySpread` came earlier from this external function
/// @audit internal function `_getPremia` came earlier from this external function
1587:     function settleLongPremium(

```
*Github:* [[522](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L522), [547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L547), [569](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L569), [586](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L586), [1017](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1017), [1179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1179), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1425), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1437), [1444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1444), [1587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1587)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit a function was seen before constructor
/// @audit a function was seen before constructor
355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
361:         // if poolId == 0, we have a bit on the left set if it was initialized, so this will still return properly

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
421:                 decoded.poolFeatures.token1,

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
450:         // Transform the amount to pay to uint256 (take positive one from amount0 and amount1)

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
492:             slippageTickLimitHigh,

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
524:             slippageTickLimitHigh,

/// @audit internal function `beginReentrancyLock` came earlier from this public function
/// @audit internal function `endReentrancyLock` came earlier from this public function
555:         super.safeTransferFrom(from, to, id, amount, data);

/// @audit internal function `beginReentrancyLock` came earlier from this public function
/// @audit internal function `endReentrancyLock` came earlier from this public function
583:         // transfer the token (note that all state updates are completed before reentrancy is possible)

/// @audit private function `_updateStoredPremia` came earlier from this internal function
/// @audit private function `_getFeesBase` came earlier from this internal function
1221:     /// @param liquidityChunk the chunk of liquidity to burn given by tick upper, tick lower, and its size

/// @audit private function `_updateStoredPremia` came earlier from this internal function
/// @audit private function `_getFeesBase` came earlier from this internal function
1252:     /// @param movedInLeg how much liquidity has been moved between msg.sender and Uniswap before this function call

/// @audit private function `_updateStoredPremia` came earlier from this internal function
/// @audit private function `_getFeesBase` came earlier from this internal function
1288:                 uint128(amountToCollect.rightSlot()),

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
/// @audit public function `safeTransferFrom` came earlier from this external function
/// @audit public function `safeBatchTransferFrom` came earlier from this external function
/// @audit internal function `registerTokenTransfer` came earlier from this external function
/// @audit internal function `_validateAndForwardToAMM` came earlier from this external function
/// @audit internal function `swapInAMM` came earlier from this external function
/// @audit internal function `_createPositionInAMM` came earlier from this external function
/// @audit internal function `_createLegInAMM` came earlier from this external function
/// @audit private function `_updateStoredPremia` came earlier from this external function
/// @audit private function `_getFeesBase` came earlier from this external function
/// @audit internal function `_mintLiquidity` came earlier from this external function
/// @audit internal function `_burnLiquidity` came earlier from this external function
/// @audit internal function `_collectAndWritePositionData` came earlier from this external function
/// @audit private function `_getPremiaDeltas` came earlier from this external function
1445:     /// @param atTick The current tick. Set atTick < type(int24).max = 8388608 to get latest premium up to the current block

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
/// @audit public function `safeTransferFrom` came earlier from this external function
/// @audit public function `safeBatchTransferFrom` came earlier from this external function
/// @audit internal function `registerTokenTransfer` came earlier from this external function
/// @audit internal function `_validateAndForwardToAMM` came earlier from this external function
/// @audit internal function `swapInAMM` came earlier from this external function
/// @audit internal function `_createPositionInAMM` came earlier from this external function
/// @audit internal function `_createLegInAMM` came earlier from this external function
/// @audit private function `_updateStoredPremia` came earlier from this external function
/// @audit private function `_getFeesBase` came earlier from this external function
/// @audit internal function `_mintLiquidity` came earlier from this external function
/// @audit internal function `_burnLiquidity` came earlier from this external function
/// @audit internal function `_collectAndWritePositionData` came earlier from this external function
/// @audit private function `_getPremiaDeltas` came earlier from this external function
1479:                     // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
/// @audit public function `safeTransferFrom` came earlier from this external function
/// @audit public function `safeBatchTransferFrom` came earlier from this external function
/// @audit internal function `registerTokenTransfer` came earlier from this external function
/// @audit internal function `_validateAndForwardToAMM` came earlier from this external function
/// @audit internal function `swapInAMM` came earlier from this external function
/// @audit internal function `_createPositionInAMM` came earlier from this external function
/// @audit internal function `_createLegInAMM` came earlier from this external function
/// @audit private function `_updateStoredPremia` came earlier from this external function
/// @audit private function `_getFeesBase` came earlier from this external function
/// @audit internal function `_mintLiquidity` came earlier from this external function
/// @audit internal function `_burnLiquidity` came earlier from this external function
/// @audit internal function `_collectAndWritePositionData` came earlier from this external function
/// @audit private function `_getPremiaDeltas` came earlier from this external function
1570: 

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
/// @audit public function `safeTransferFrom` came earlier from this external function
/// @audit public function `safeBatchTransferFrom` came earlier from this external function
/// @audit internal function `registerTokenTransfer` came earlier from this external function
/// @audit internal function `_validateAndForwardToAMM` came earlier from this external function
/// @audit internal function `swapInAMM` came earlier from this external function
/// @audit internal function `_createPositionInAMM` came earlier from this external function
/// @audit internal function `_createLegInAMM` came earlier from this external function
/// @audit private function `_updateStoredPremia` came earlier from this external function
/// @audit private function `_getFeesBase` came earlier from this external function
/// @audit internal function `_mintLiquidity` came earlier from this external function
/// @audit internal function `_burnLiquidity` came earlier from this external function
/// @audit internal function `_collectAndWritePositionData` came earlier from this external function
/// @audit private function `_getPremiaDeltas` came earlier from this external function
1570: 

/// @audit internal function `beginReentrancyLock` came earlier from this external function
/// @audit internal function `endReentrancyLock` came earlier from this external function
/// @audit public function `safeTransferFrom` came earlier from this external function
/// @audit public function `safeBatchTransferFrom` came earlier from this external function
/// @audit internal function `registerTokenTransfer` came earlier from this external function
/// @audit internal function `_validateAndForwardToAMM` came earlier from this external function
/// @audit internal function `swapInAMM` came earlier from this external function
/// @audit internal function `_createPositionInAMM` came earlier from this external function
/// @audit internal function `_createLegInAMM` came earlier from this external function
/// @audit private function `_updateStoredPremia` came earlier from this external function
/// @audit private function `_getFeesBase` came earlier from this external function
/// @audit internal function `_mintLiquidity` came earlier from this external function
/// @audit internal function `_burnLiquidity` came earlier from this external function
/// @audit internal function `_collectAndWritePositionData` came earlier from this external function
/// @audit private function `_getPremiaDeltas` came earlier from this external function
1570: 

```
*Github:* [[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L355), [361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L361), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L421), [450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L450), [492](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L492), [524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L524), [555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L555), [583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L583), [1221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1221), [1252](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1252), [1288](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1288), [1445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1445), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1479), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit internal function `getPoolId` came earlier from this external function
/// @audit internal function `incrementPoolPattern` came earlier from this external function
75:     function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

/// @audit internal function `getPoolId` came earlier from this external function
/// @audit internal function `incrementPoolPattern` came earlier from this external function
/// @audit internal function `updatePositionsHash` came earlier from this external function
125:     function computeMedianObservedPrice(

/// @audit internal function `getPoolId` came earlier from this external function
/// @audit internal function `incrementPoolPattern` came earlier from this external function
/// @audit internal function `updatePositionsHash` came earlier from this external function
168:     function computeInternalMedian(

/// @audit internal function `getPoolId` came earlier from this external function
/// @audit internal function `incrementPoolPattern` came earlier from this external function
/// @audit internal function `updatePositionsHash` came earlier from this external function
241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

/// @audit internal function `getPoolId` came earlier from this external function
/// @audit internal function `incrementPoolPattern` came earlier from this external function
/// @audit internal function `updatePositionsHash` came earlier from this external function
/// @audit internal function `getLiquidityChunk` came earlier from this external function
/// @audit internal function `getTicks` came earlier from this external function
/// @audit internal function `getRangesFromStrike` came earlier from this external function
/// @audit internal function `computeExercisedAmounts` came earlier from this external function
/// @audit internal function `convertCollateralData` came earlier from this external function
/// @audit internal function `convertCollateralData` came earlier from this external function
/// @audit internal function `convertNotional` came earlier from this external function
/// @audit internal function `convert0to1` came earlier from this external function
/// @audit internal function `convert1to0` came earlier from this external function
/// @audit internal function `convert0to1` came earlier from this external function
/// @audit internal function `convert1to0` came earlier from this external function
/// @audit internal function `getAmountsMoved` came earlier from this external function
/// @audit internal function `_calculateIOAmounts` came earlier from this external function
653:         LeftRightUnsigned tokenData1,

/// @audit internal function `getPoolId` came earlier from this external function
/// @audit internal function `incrementPoolPattern` came earlier from this external function
/// @audit internal function `updatePositionsHash` came earlier from this external function
/// @audit internal function `getLiquidityChunk` came earlier from this external function
/// @audit internal function `getTicks` came earlier from this external function
/// @audit internal function `getRangesFromStrike` came earlier from this external function
/// @audit internal function `computeExercisedAmounts` came earlier from this external function
/// @audit internal function `convertCollateralData` came earlier from this external function
/// @audit internal function `convertCollateralData` came earlier from this external function
/// @audit internal function `convertNotional` came earlier from this external function
/// @audit internal function `convert0to1` came earlier from this external function
/// @audit internal function `convert1to0` came earlier from this external function
/// @audit internal function `convert0to1` came earlier from this external function
/// @audit internal function `convert1to0` came earlier from this external function
/// @audit internal function `getAmountsMoved` came earlier from this external function
/// @audit internal function `_calculateIOAmounts` came earlier from this external function
770:         TokenId[] memory positionIdList,

/// @audit internal function `getPoolId` came earlier from this external function
/// @audit internal function `incrementPoolPattern` came earlier from this external function
/// @audit internal function `updatePositionsHash` came earlier from this external function
/// @audit internal function `getLiquidityChunk` came earlier from this external function
/// @audit internal function `getTicks` came earlier from this external function
/// @audit internal function `getRangesFromStrike` came earlier from this external function
/// @audit internal function `computeExercisedAmounts` came earlier from this external function
/// @audit internal function `convertCollateralData` came earlier from this external function
/// @audit internal function `convertCollateralData` came earlier from this external function
/// @audit internal function `convertNotional` came earlier from this external function
/// @audit internal function `convert0to1` came earlier from this external function
/// @audit internal function `convert1to0` came earlier from this external function
/// @audit internal function `convert0to1` came earlier from this external function
/// @audit internal function `convert1to0` came earlier from this external function
/// @audit internal function `getAmountsMoved` came earlier from this external function
/// @audit internal function `_calculateIOAmounts` came earlier from this external function
919:         LeftRightSigned refundValues,

```
*Github:* [[75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L75), [125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L125), [168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L168), [241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L241), [653](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L653), [770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L770), [919](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L919)]


</details>


<a name="NC-32"></a> 
### [NC-32] Functions and modifiers should be named in mixedCase style
As the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.21/style-guide.html#function-names) suggests: functions and modifiers should be named in mixedCase style.

*There is one instance of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

329:     /// @param poolId The poolId of the pool to remove the reentrancy lock from

```
*Github:* [[329](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L329)]



<a name="NC-33"></a> 
### [NC-33] Functions with array parameters should have length checks in place

<details>
<summary>
There are <b>19</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `positionBalanceArray`
1147:         tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);

```
*Github:* [[1147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1147)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `positionIdList`
381:     function calculateAccumulatedFeesBatch(

/// @audit `positionIdList`
410:     function calculatePortfolioValue(

/// @audit `positionIdList`
547:     function mintOptions(

/// @audit `newPositionIdList`
569:     function burnOptions(

/// @audit `positionIdList`
/// @audit `newPositionIdList`
586:     function burnOptions(

/// @audit `positionIdList`
887:     function _validateSolvency(

/// @audit `positionIdListLiquidator`
1017:     function liquidate(

/// @audit `positionIdListExercisee`
1179:     function forceExercise(

/// @audit `positionIdList`
1290:     function _checkSolvencyAtTick(

/// @audit `collectedByLeg`
1666:     function _updateSettlementPostMint(

/// @audit `premiumAccumulators`
1757:     function _getAvailablePremium(

/// @audit `collectedByLeg`
1833:     function _updateSettlementPostBurn(

```
*Github:* [[381](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L381), [410](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L410), [547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L547), [569](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L569), [586](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L586), [887](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L887), [1017](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1017), [1179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1179), [1290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1290), [1666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1666), [1757](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1757), [1833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1833)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `ids`
/// @audit `amounts`
583:         // transfer the token (note that all state updates are completed before reentrancy is possible)

```
*Github:* [[583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L583)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

/// @audit `positionIdList`
50:     ) external view returns (int256 value0, int256 value1) {

```
*Github:* [[50](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L50)]


```solidity
File: ./contracts/libraries/Math.sol

/// @audit `arr`
753:     function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {

```
*Github:* [[753](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L753)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit `positionIdList`
/// @audit `premiasByLeg`
770:         TokenId[] memory positionIdList,

```
*Github:* [[770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L770)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

/// @audit `ids`
/// @audit `amounts`
130:     function safeBatchTransferFrom(

/// @audit `ids`
178:     function balanceOfBatch(

```
*Github:* [[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L130), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L178)]


</details>


<a name="NC-34"></a> 
### [NC-34] High cyclomatic complexity
Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit Number of blocks: 14
992:             // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user

```
*Github:* [[992](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L992)]


```solidity
File: ./contracts/libraries/Math.sol

/// @audit Number of blocks: 10
340:     function mulDiv(

```
*Github:* [[340](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L340)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit Number of blocks: 12
770:         TokenId[] memory positionIdList,

```
*Github:* [[770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L770)]



<a name="NC-35"></a> 
### [NC-35] Inconsistent spacing in comments
Some lines use `// x` and some use `//x`. The instances below point out the usages that don't follow the majority, within each file

<details>
<summary>
There are <b>95</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

42:     //////////////////////////////////////////////////////////////*/

67:     //////////////////////////////////////////////////////////////*/

85:     //////////////////////////////////////////////////////////////*/

106:     //////////////////////////////////////////////////////////////*/

128:     //////////////////////////////////////////////////////////////*/

166:     //////////////////////////////////////////////////////////////*/

176:     //////////////////////////////////////////////////////////////*/

268:     //////////////////////////////////////////////////////////////*/

317:     //////////////////////////////////////////////////////////////*/

357:     //////////////////////////////////////////////////////////////*/

630:     //////////////////////////////////////////////////////////////*/

857:     ////////////////////////////////////////////////////////////////////*/

987:     //////////////////////////////////////////////////////////////*/

1118:             //compute total commission amount = commission rate + spread fee

1130:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[42](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L42), [67](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L67), [85](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L85), [106](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L106), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L128), [166](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L166), [176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L176), [268](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L268), [317](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L317), [357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L357), [630](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L630), [857](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L857), [987](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L987), [1118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1118), [1130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1130)]


```solidity
File: ./contracts/PanopticFactory.sol

29:     //////////////////////////////////////////////////////////////*/

54:     //////////////////////////////////////////////////////////////*/

60:     //////////////////////////////////////////////////////////////*/

93:     //////////////////////////////////////////////////////////////*/

106:     //////////////////////////////////////////////////////////////*/

143:     //////////////////////////////////////////////////////////////*/

165:     //////////////////////////////////////////////////////////////*/

199:     //////////////////////////////////////////////////////////////*/

280:     //////////////////////////////////////////////////////////////*/

415:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[29](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L29), [54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L54), [60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L60), [93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L93), [106](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L106), [143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L143), [165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L165), [199](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L199), [280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L280), [415](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L415)]


```solidity
File: ./contracts/PanopticPool.sol

30:     //////////////////////////////////////////////////////////////*/

99:     //////////////////////////////////////////////////////////////*/

183:     //////////////////////////////////////////////////////////////*/

276:     //////////////////////////////////////////////////////////////*/

331:     //////////////////////////////////////////////////////////////*/

519:     //////////////////////////////////////////////////////////////*/

538:     //////////////////////////////////////////////////////////////*/

605:     //////////////////////////////////////////////////////////////*/

786:     //////////////////////////////////////////////////////////////*/

1009:     //////////////////////////////////////////////////////////////*/

1282:     //////////////////////////////////////////////////////////////*/

1360:     //////////////////////////////////////////////////////////////*/

1421:     //////////////////////////////////////////////////////////////*/

1456:     //////////////////////////////////////////////////////////////*/

1579:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L30), [99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L99), [183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L183), [276](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L276), [331](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L331), [519](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L519), [538](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L538), [605](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L605), [786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L786), [1009](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1009), [1282](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1282), [1360](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1360), [1421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1421), [1456](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1456), [1579](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1579)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

75:     //////////////////////////////////////////////////////////////*/

106:     //////////////////////////////////////////////////////////////*/

122:     //////////////////////////////////////////////////////////////*/

141:     //////////////////////////////////////////////////////////////*/

299:     //////////////////////////////////////////////////////////////*/

337:     //////////////////////////////////////////////////////////////*/

395:     //////////////////////////////////////////////////////////////*/

461:     //////////////////////////////////////////////////////////////*/

531:     //////////////////////////////////////////////////////////////*/

610:             //construct the positionKey for the from and to addresses

643:             //update+store liquidity and fee values between accounts

657:     //////////////////////////////////////////////////////////////*/

821:                 //compute the swap amount, set as positive (exact input)

1411:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L75), [106](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L106), [122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L122), [141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L141), [299](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L299), [337](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L337), [395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L395), [461](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L461), [531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L531), [610](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L610), [643](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L643), [657](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L657), [821](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L821), [1411](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1411)]


```solidity
File: ./contracts/libraries/Math.sol

19:     //////////////////////////////////////////////////////////////*/

121:     //////////////////////////////////////////////////////////////*/

185:     //////////////////////////////////////////////////////////////*/

291:     //////////////////////////////////////////////////////////////*/

332:     //////////////////////////////////////////////////////////////*/

372:             ///////////////////////////////////////////////

374:             ///////////////////////////////////////////////

486:             ///////////////////////////////////////////////

488:             ///////////////////////////////////////////////

549:             ///////////////////////////////////////////////

551:             ///////////////////////////////////////////////

626:             ///////////////////////////////////////////////

628:             ///////////////////////////////////////////////

703:             ///////////////////////////////////////////////

705:             ///////////////////////////////////////////////

746:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[19](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L19), [121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L121), [185](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L185), [291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L291), [332](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L332), [372](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L372), [374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L374), [486](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L486), [488](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L488), [549](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L549), [551](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L551), [626](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L626), [628](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L628), [703](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L703), [705](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L705), [746](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L746)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

30:     //////////////////////////////////////////////////////////////*/

83:     //////////////////////////////////////////////////////////////*/

272:     //////////////////////////////////////////////////////////////*/

383:     //////////////////////////////////////////////////////////////*/

639:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L30), [83](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L83), [272](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L272), [383](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L383), [639](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L639)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

14:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L14)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

14:     //////////////////////////////////////////////////////////////*/

52:     //////////////////////////////////////////////////////////////*/

62:     //////////////////////////////////////////////////////////////*/

76:     //////////////////////////////////////////////////////////////*/

195:     //////////////////////////////////////////////////////////////*/

208:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L14), [52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L52), [62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L62), [76](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L76), [195](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L195), [208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L208)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

12:     //////////////////////////////////////////////////////////////*/

28:     //////////////////////////////////////////////////////////////*/

43:     //////////////////////////////////////////////////////////////*/

117:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L12), [28](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L28), [43](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L43), [117](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L117)]


```solidity
File: ./contracts/types/LeftRight.sol

34:     //////////////////////////////////////////////////////////////*/

96:     //////////////////////////////////////////////////////////////*/

142:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[34](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L34), [96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L96), [142](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L142)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

63:     //////////////////////////////////////////////////////////////*/

166:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L63), [166](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L166)]


```solidity
File: ./contracts/types/TokenId.sol

82:     //////////////////////////////////////////////////////////////*/

177:     //////////////////////////////////////////////////////////////*/

358:     //////////////////////////////////////////////////////////////*/

495:     //////////////////////////////////////////////////////////////*/

```
*Github:* [[82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L82), [177](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L177), [358](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L358), [495](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L495)]


</details>


<a name="NC-36"></a> 
### [NC-36] Invalid NatSpec comment style
NatSpec must begin with `///` or use `/* ... */` syntax

*There are <b>7</b> instances of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

358:         // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting

360:         // @dev some pools may not be deployable if the poolId has a collision (since we take only 8 bytes)

603:             // @dev see `contracts/types/LiquidityChunk.sol`

790:                 // implement a single "netting" swap. Thank you @danrobinson for this puzzle/idea

836:             // @dev note this triggers our swap callback function

903:                 // @dev see `contracts/types/LiquidityChunk.sol`

```
*Github:* [[358](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L358), [360](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L360), [603](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L603), [790](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L790), [836](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L836), [903](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L903)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

98:         // @dev 0 ^ x = x

```
*Github:* [[98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L98)]



<a name="NC-37"></a> 
### [NC-37] It is best practice to use linear inheritance
In Solidity, complex inheritance structures can obfuscate code understanding, introducing potential security risks. Multiple inheritance, especially with overlapping function names or state variables, can cause unintentional overrides or ambiguous behavior. 

Resolution: Strive for linear and simple inheritance chains. Avoid diamond or circular inheritance patterns. Clearly document the purpose and relationships of base contracts, ensuring that overrides are intentional. Tools like Remix or Hardhat can visualize inheritance chains, assisting in verification. Keeping inheritance streamlined aids in better code readability, reduces potential errors, and ensures smoother audits and upgrades.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

```
*Github:* [[36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36)]


```solidity
File: ./contracts/PanopticPool.sol

27: contract PanopticPool is ERC1155Holder, Multicall {

```
*Github:* [[27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L27)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

82:     /// @notice Emitted when a position is destroyed/burned
        /// @dev Recipient is used to track whether it was burned directly by the user or through an option contract

```
*Github:* [[82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L82)]



<a name="NC-38"></a> 
### [NC-38] Lack of brace spacing
Lack of brace spacing in coding refers to the absence of spaces around braces, which can hinder code readability. In Solidity, as in many programming languages, spacing can enhance the visual distinction between different parts of the code, making it easier to follow. A lack of spacing can lead to a dense, confusing appearance. The resolution to this issue is to follow a consistent style guide that defines rules for brace spacing. By including spaces around braces, such as `{ statement }` instead of `{statement}`, developers can ensure that the code is more legible and maintainable, especially in larger codebases.

*There is one instance of this issue:*
```solidity
File: ./contracts/PanopticFactory.sol

398:                 poolFeatures: CallbackLib.PoolFeatures({token0: token0, token1: token1, fee: fee}),

```
*Github:* [[398](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L398)]



<a name="NC-39"></a> 
### [NC-39] Large or complicated code bases should implement invariant tests
This includes: large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts. Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold. Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers may help significantly.

*There is one instance of this issue:*
```solidity

Global finding

```
*Github:* [[Global](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/)]



<a name="NC-40"></a> 
### [NC-40] Large multiples of ten should use scientific notation
Use a scientific notation rather than decimal literals (e.g. `1e6` instead of `1000000`), for better code readability.

<details>
<summary>
There are <b>12</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

77:     uint256 internal constant DECIMALS = 10_000;

81:     int128 internal constant DECIMALS_128 = 10_000;

204:                     10_000 +

206:                     10_000 ** 2 +

208:                     10_000 ** 3

```
*Github:* [[77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L81), [204](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L204), [206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L206), [208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L208)]


```solidity
File: ./contracts/PanopticPool.sol

174:     uint256 internal constant NO_BUFFER = 10_000;

1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

```
*Github:* [[174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L174), [1329](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1329)]


```solidity
File: ./contracts/types/TokenId.sol

63:         0x100_000000000100_000000000100_000000000100_0000000000000000;

63:         0x100_000000000100_000000000100_000000000100_0000000000000000;

63:         0x100_000000000100_000000000100_000000000100_0000000000000000;

63:         0x100_000000000100_000000000100_000000000100_0000000000000000;

75:         0xFFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_0000000000000000;

```
*Github:* [[63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L63), [63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L63), [63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L63), [63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L63), [75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L75)]


</details>


<a name="NC-41"></a> 
### [NC-41] Large numeric literals should use underscores for readability
Large hardcoded numbers in code can be difficult to read. Consider using underscores for number literals to improve readability (e.g `1234567` -> `1_234_567`). Consider using an underscore for every third digit from the right.

<details>
<summary>
There are <b>12</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

202:                 2230 +

203:                     (12500 * ratioTick) /

205:                     (7812 * ratioTick ** 2) /

207:                     (6510 * ratioTick ** 3) /

```
*Github:* [[200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L200), [202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L203), [205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L205), [207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L207)]


```solidity
File: ./contracts/PanopticPool.sol

160:     int256 internal constant MAX_SLOW_FAST_DELTA = 1800;

```
*Github:* [[160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L160)]


```solidity
File: ./contracts/libraries/Constants.sol

12:     int24 internal constant MIN_V3POOL_TICK = -887272;

15:     int24 internal constant MAX_V3POOL_TICK = 887272;

18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

22:         1461446703485210103287273052203988822378723970342;

```
*Github:* [[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L12), [15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L15), [18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L18), [22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L22)]


```solidity
File: ./contracts/types/TokenId.sol

171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

```
*Github:* [[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L171), [320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L320)]


</details>


<a name="NC-42"></a> 
### [NC-42] Long functions should be refactored into multiple, smaller, functions

<details>
<summary>
There are <b>33</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit 84 lines
650:     function exerciseCost(
             int24 currentTick,
             int24 oracleTick,
             TokenId positionId,
             uint128 positionBalance,
             LeftRightSigned longAmounts
         ) external view returns (LeftRightSigned exerciseFees) {
             // find the leg furthest to the strike price 'currentTick'; this will have the lowest exercise cost

/// @audit 56 lines
917:                 ┌────────┐
                     │Panoptic│
                     │Pool    │
                     └────┬───┘
                          │(1) convert 'assets' to shares (this ERC20 contract)

/// @audit 119 lines
1319:         uint256 tokenType = tokenId.tokenType(index);
      
              // compute the total amount of funds moved for that position
              LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);
      
              // amount moved is right slot if tokenType=0, left slot otherwise

/// @audit 79 lines
1518:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);
      
              // compute the total amount of funds moved for the position's partner leg
              LeftRightUnsigned amountsMovedPartner = PanopticMath.getAmountsMoved(

```
*Github:* [[650](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L650), [917](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L917), [1319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1319), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1518)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit 66 lines
210:     function deployNewPool(
             address token0,
             address token1,
             uint24 fee,
             bytes32 salt
         ) external returns (PanopticPool newPoolContract) {

/// @audit 76 lines
335:     function _mintFullRange(
             IUniswapV3Pool v3Pool,
             address token0,
             address token1,
             uint24 fee
         ) internal returns (uint256, uint256) {

```
*Github:* [[210](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L210), [335](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L335)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit 166 lines
280:     constructor(SemiFungiblePositionManager _sfpm) {

/// @audit 63 lines
429:     function _calculateAccumulatedPremia(
             address user,
             TokenId[] calldata positionIdList,
             bool computeAllPremia,
             bool includePendingPremium,
             int24 atTick
         ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

/// @audit 53 lines
614:     function _mintOptions(
             TokenId[] calldata positionIdList,
             uint128 positionSize,
             uint64 effectiveLiquidityLimitX32,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal {

/// @audit 59 lines
887:     function _validateSolvency(
             address user,
             TokenId[] calldata positionIdList,
             uint256 buffer
         ) internal view returns (uint256 medianData) {

/// @audit 154 lines
1017:     function liquidate(
              TokenId[] calldata positionIdListLiquidator,
              address liquidatee,
              LeftRightUnsigned delegations,
              TokenId[] calldata positionIdList
          ) external {

/// @audit 99 lines
1179:     function forceExercise(
              address account,
              TokenId[] calldata touchedId,
              TokenId[] calldata positionIdListExercisee,
              TokenId[] calldata positionIdListExercisor
          ) external {

/// @audit 72 lines
1503:     function _getPremia(
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
          {
              uint256 numLegs = tokenId.countLegs();

/// @audit 72 lines
1587:     function settleLongPremium(
              TokenId[] calldata positionIdList,
              address owner,
              uint256 legIndex
          ) external {
              _validatePositionList(owner, positionIdList, 0);

/// @audit 80 lines
1666:     function _updateSettlementPostMint(
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize
          ) internal {
              uint256 numLegs = tokenId.countLegs();

/// @audit 147 lines
1833:     function _updateSettlementPostBurn(
              address owner,
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize,
              bool commitLongSettled
          ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
              uint256 numLegs = tokenId.countLegs();

```
*Github:* [[280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L280), [429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L429), [614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L614), [887](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L887), [1017](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1017), [1179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1179), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1503), [1587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1587), [1666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1666), [1833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1833)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit 60 lines
611:             bytes32 positionKey_from = keccak256(
                     abi.encodePacked(
                         address(univ3pool),

/// @audit 96 lines
786:             // this is simply a convenience feature, and should be treated as such
                 if ((itm0 != 0) && (itm1 != 0)) {
                     (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

/// @audit 78 lines
897:                     // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,
                         // allowing the corresponding short liquidity to be removed
                         _leg = _isBurn ? numLegs - leg - 1 : leg;
                     }
     
                     // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick

/// @audit 146 lines
992:             // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user
                 // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller
                 // the reason why it is called "removedLiquidity" is because long options are created by removing -ie.short selling LP positions

/// @audit 58 lines
1288:                 uint128(amountToCollect.rightSlot()),
                      uint128(amountToCollect.leftSlot())
                  );
      
                  // moved will be negative if the leg was long (funds left the caller, don't count it in collected fees)
                  uint128 collected0;
                  uint128 collected1;
                  unchecked {
                      collected0 = movedInLeg.rightSlot() < 0

/// @audit 86 lines
1357:                     totalLiquidity * 2 ** 64,
                          netLiquidity ** 2
                      );
                  }
      
                  {
                      uint128 premium0X64_owed;
                      uint128 premium1X64_owed;
                      {
                          // compute the owed premium (from Eqn 3)

/// @audit 74 lines
1479:                     // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])
                          LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(
                              _univ3pool,
                              atTick,
                              _tickLower,
                              _tickUpper,

```
*Github:* [[611](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L611), [786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L786), [897](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L897), [992](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L992), [1288](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1288), [1357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1357), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1479)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

/// @audit 78 lines
135:     ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
             // Get feesGrowths from the option position's lower+upper ticks
             // lowerOut0: For token0: fee growth per unit of liquidity on the _other_ side of tickLower (relative to currentTick)
             // only has relative meaning, not absolute — the value depends on when the tick is initialized

```
*Github:* [[135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L135)]


```solidity
File: ./contracts/libraries/Math.sol

/// @audit 53 lines
128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {
             unchecked {

/// @audit 93 lines
340:     function mulDiv(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {
             unchecked {

/// @audit 57 lines
458:     function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {
             unchecked {

/// @audit 57 lines
521:     function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {
             unchecked {

/// @audit 57 lines
598:     function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {
             unchecked {

/// @audit 57 lines
675:     function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {
             unchecked {

```
*Github:* [[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L128), [340](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L340), [458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L521), [598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L598), [675](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L675)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit 65 lines
168:     function computeInternalMedian(
             uint256 observationIndex,
             uint256 observationCardinality,
             uint256 period,
             uint256 medianData,
             IUniswapV3Pool univ3pool
         ) external view returns (int24 medianTick, uint256 updatedMedianData) {
             unchecked {

/// @audit 103 lines
653:         LeftRightUnsigned tokenData1,
             uint160 sqrtPriceX96Twap,
             uint160 sqrtPriceX96Final,
             LeftRightSigned netExchanged,
             LeftRightSigned premia
         ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {
             unchecked {
                 // compute bonus as min(collateralBalance/2, required-collateralBalance)

/// @audit 140 lines
770:         TokenId[] memory positionIdList,
             LeftRightSigned[4][] memory premiasByLeg,
             LeftRightSigned collateralRemaining,
             CollateralTracker collateral0,
             CollateralTracker collateral1,
             uint160 sqrtPriceX96Final,
             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
         ) external returns (int256, int256) {
             unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;

```
*Github:* [[168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L168), [653](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L653), [770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L770)]


</details>


<a name="NC-43"></a> 
### [NC-43] Magic numbers should be replaced with constants
Magic numbers are hard-coded values in code that can make it difficult for developers and maintainers to understand the code, and can also cause confusion or errors. To improve the readability and maintainability of code, it is recommended to replace magic numbers with constants that have good readability.

<details>
<summary>
There are <b>108</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

// @audit `2000`
200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

// @audit `2230`
202:                 2230 +

// @audit `12500`
203:                     (12500 * ratioTick) /

// @audit `10_000`
204:                     10_000 +

// @audit `7812`
205:                     (7812 * ratioTick ** 2) /

// @audit `2`
205:                     (7812 * ratioTick ** 2) /

// @audit `10_000`
206:                     10_000 ** 2 +

// @audit `2`
206:                     10_000 ** 2 +

// @audit `6510`
207:                     (6510 * ratioTick ** 3) /

// @audit `3`
207:                     (6510 * ratioTick ** 3) /

// @audit `10_000`
208:                     10_000 ** 3

// @audit `3`
209:             );

// @audit `10`
234:         totalSupply = 10 ** 6;

// @audit `6`
234:         totalSupply = 10 ** 6;

// @audit `100`
249:             _poolFee = fee / 100;

// @audit `2`
672:                             )

// @audit `2`
779:                 utilization = -utilization;

// @audit `2`
844:             }

// @audit `2`
851:                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

// @audit `2`
1151:     /// NOTE: It's up to the caller to confirm from the returned result that the account has enough collateral.

// @audit `2`
1169:             // get all collateral required for the incoming list of positions

// @audit `2`
1207:         uint256 totalIterations = positionBalanceArray.length;

// @audit `64`
1339:             if (isLong == 0) {

// @audit `2`
1370:                     // compute the collateral requirement depending on whether the position is ITM & out-of-range or ITM and in-range:

// @audit `2`
1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

// @audit `64`
1593:     /// @dev A strangle can only have only one of its leg tested at the same time, so this reduces the total risk and collateral requirement.

// @audit `64`
1641:                 strangleRequired = _getRequiredCollateralSingleLegNoPartner(

// @audit `64`
1651: 

```
*Github:* [[200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L200), [202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L203), [204](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L204), [205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L205), [205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L205), [206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L206), [206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L206), [207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L207), [207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L207), [208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L208), [209](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L209), [234](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L234), [234](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L234), [249](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L249), [672](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L672), [779](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L779), [844](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L844), [851](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L851), [1151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1151), [1169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1169), [1207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1207), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1339), [1370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1370), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1374), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1593), [1641](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1641), [1651](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1651)]


```solidity
File: ./contracts/PanopticPool.sol

// @audit `216`
309:                 (uint256(block.timestamp) << 216) +

// @audit `0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000`
312:                 (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +

// @audit `24`
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

// @audit `64`
370:         poolUtilization1 = uint64(balanceData.leftSlot() >> 64);

// @audit `2`
385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

// @audit `2`
390:         (LeftRightSigned premia, uint256[2][] memory balances) = _calculateAccumulatedPremia(

// @audit `2`
435:     ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

// @audit `2`
437:         balances = new uint256[2][](pLength);

// @audit `4`
448:                 LeftRightSigned[4] memory premiaByLeg,

// @audit `2`
449:                 uint256[2][4] memory premiumAccumulatorsByLeg

// @audit `4`
449:                 uint256[2][4] memory premiumAccumulatorsByLeg

// @audit `4`
685:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM

// @audit `64`
730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

// @audit `4`
800:     ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

// @audit `4`
801:         premiasByLeg = new LeftRightSigned[4][](positionIdList.length);

// @audit `4`
832:     ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

// @audit `4`
966:             LeftRightSigned[4] memory premiaByLeg,

// @audit `4`
970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM

// @audit `2`
1038:             uint256[2][] memory positionBalanceArray = new uint256[2][](positionIdList.length);

// @audit `2`
1038:             uint256[2][] memory positionBalanceArray = new uint256[2][](positionIdList.length);

// @audit `4`
1080:             LeftRightSigned[4][] memory premiasByLeg;

// @audit `2`
1299:             uint256[2][] memory positionBalanceArray

// @audit `10_000`
1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

// @audit `2`
1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

// @audit `96`
1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

// @audit `2`
1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

// @audit `96`
1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

// @audit `248`
1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

// @audit `248`
1446:     }

// @audit `2`
1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

// @audit `32`
1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

// @audit `4`
1513:             LeftRightSigned[4] memory premiaByLeg,

// @audit `2`
1514:             uint256[2][4] memory premiumAccumulatorsByLeg

// @audit `4`
1514:             uint256[2][4] memory premiumAccumulatorsByLeg

// @audit `2`
1553:                                 )

// @audit `64`
1553:                                 )

// @audit `2`
1562:                                 )

// @audit `64`
1562:                                 )

// @audit `3`
1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

// @audit `2`
1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

// @audit `2`
1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

// @audit `64`
1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

// @audit `64`
1638:             // deduct the paid premium tokens from the owner's balance and add them to the cumulative settled token delta

// @audit `4`
1668:         LeftRightUnsigned[4] memory collectedByLeg,

// @audit `2`
1706:                 uint256[2] memory grossCurrent;

// @audit `2`
1762:         uint256[2] memory premiumAccumulators

// @audit `2`
1769:                 totalLiquidity) / 2 ** 64;

// @audit `64`
1770:             uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *

// @audit `2`
1771:                 totalLiquidity) / 2 ** 64;

// @audit `64`
1773:             return (

// @audit `4`
1836:         LeftRightUnsigned[4] memory collectedByLeg,

// @audit `4`
1839:     ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {

// @audit `2`
1841:         uint256[2][4] memory premiumAccumulatorsByLeg;

// @audit `4`
1841:         uint256[2][4] memory premiumAccumulatorsByLeg;

// @audit `2`
1923:                         uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;

// @audit `4`
1923:                         uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;

// @audit `2`
1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),

// @audit `64`
1943:                                                 0

// @audit `2`
1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,

// @audit `64`
1960:                                                 0

```
*Github:* [[309](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L309), [312](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L312), [313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L370), [385](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L385), [390](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L390), [435](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L435), [437](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L437), [448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L448), [449](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L449), [449](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L449), [685](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L685), [730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730), [800](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L800), [801](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L801), [832](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L832), [966](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L966), [970](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L970), [1038](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1038), [1038](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1038), [1080](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1080), [1299](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1299), [1329](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1329), [1348](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1348), [1348](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1348), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1353), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1353), [1415](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1415), [1446](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1446), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487), [1513](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1513), [1514](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1514), [1514](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1514), [1553](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1553), [1553](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1553), [1562](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1562), [1562](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1562), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1596), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1636), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1636), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1638), [1668](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1668), [1706](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1706), [1762](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1762), [1769](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1769), [1770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1770), [1771](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1771), [1773](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1773), [1836](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1836), [1839](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1839), [1841](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1841), [1841](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1841), [1923](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1923), [1923](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1923), [1942](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1942), [1943](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1943), [1959](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1959), [1960](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1960)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

// @audit `2`
405:         bytes calldata data

// @audit `255`
405:         bytes calldata data

// @audit `4`
499:     /// @param positionSize The number of contracts minted, expressed in terms of the asset

// @audit `4`
533:     /// @notice Transfer a single token from one user to another

// @audit `4`
716:             // if the in-the-money amount is not zero (i.e. positions were minted ITM) and the user did provide tick limits LOW > HIGH, then swap necessary amounts

// @audit `4`
902:                 // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick

// @audit `2`
1395:                         .toUint128Capped();

// @audit `64`
1395:                         .toUint128Capped();

// @audit `2`
1396:                     premium1X64_gross = Math

// @audit `2`
1398:                         .toUint128Capped();

// @audit `64`
1398:                         .toUint128Capped();

// @audit `2`
1400:                     deltaPremiumGross = LeftRightUnsigned

// @audit `2`
1410:                             SFPM PROPERTIES

// @audit `2`
1420:     /// @return accountLiquidities The amount of liquidity that has been shorted/added to the Uniswap contract (netLiquidity:removedLiquidity -> rightSlot:leftSlot)

// @audit `2`
1425:         int24 tickLower,

// @audit `2`
1425:         int24 tickLower,

// @audit `2`
1428:         /// Extract the account liquidity for a given uniswap pool, owner, token type, and ticks

// @audit `2`
1429:         /// @dev tokenType input here is the asset of the positions minted, this avoids put liquidity to be used for call, and vice-versa

```
*Github:* [[405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L405), [405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L405), [499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L499), [533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L533), [716](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L716), [902](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L902), [1395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1395), [1395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1395), [1396](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1396), [1398](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1398), [1398](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1398), [1400](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1400), [1410](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1410), [1420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1420), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1425), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1425), [1428](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1428), [1429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1429)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

// @audit `0x01ffc9a7`
202:             interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

// @audit `0xd9b67a26`
203:             interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

```
*Github:* [[202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L203)]


</details>


<a name="NC-44"></a> 
### [NC-44] Missing NatSpec from contract/error/event/function/modifier declarations
e.g. `@dev` or `@notice`, and it must appear above the contract definition braces in order to be identified by the compiler as NatSpec.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

178:     constructor(
             uint256 _commissionFee,
             uint256 _sellerCollateralRatio,
             uint256 _buyerCollateralRatio,
             int256 _forceExerciseCost,
             uint256 _targetPoolUtilization,
             uint256 _saturatedPoolUtilization,
             uint256 _ITMSpreadMultiplier
         ) {
             COMMISSION_FEE = _commissionFee;

```
*Github:* [[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

6: interface IDonorNFT {

```
*Github:* [[6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L6)]



<a name="NC-45"></a> 
### [NC-45] Missing NatSpec `@author` from contract declaration
Some contract definitions have an incomplete NatSpec: add a `@author` notation to improve the code documentation.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

```
*Github:* [[36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

6: interface IDonorNFT {

```
*Github:* [[6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L6)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

54:     uint256 internal constant CLEAR_TL_MASK =

```
*Github:* [[54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L54)]



<a name="NC-46"></a> 
### [NC-46] Missing NatSpec `@dev` from contract/event/function/modifier declarations
Some contract definitions have an incomplete NatSpec: add a `@dev` notation to improve the code documentation.

<details>
<summary>
There are <b>171</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

49:     event Deposit(address indexed sender, address indexed owner, uint256 assets, uint256 shares);

57:     event Withdraw(

169:     modifier onlyPanopticPool() {

178:     constructor(

289:     function name() external view returns (string memory) {

303:     function symbol() external view returns (string memory) {

310:     function decimals() external view returns (uint8) {

361:     function asset() external view returns (address assetTokenAddress) {

379:     function convertToShares(uint256 assets) public view returns (uint256 shares) {

386:     function convertToAssets(uint256 shares) public view returns (uint256 assets) {

392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

399:     function previewDeposit(uint256 assets) public view returns (uint256 shares) {

444:     function maxMint(address) external view returns (uint256 maxShares) {

453:     function previewMint(uint256 shares) public view returns (uint256 assets) {

518:     function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {

581:     function previewRedeem(uint256 shares) public view returns (uint256 assets) {

591:     function redeem(

917:                 ┌────────┐

1002:             // current available assets belonging to PLPs (updated after settlement) excluding any premium paid

1104:             // intrinsic value is the amount that need to be exchanged due to minting in-the-money

1254:         unchecked {

```
*Github:* [[36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36), [49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L57), [169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L169), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178), [289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L310), [361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L361), [379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392), [399](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L399), [444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444), [453](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L453), [518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L518), [572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L581), [591](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L591), [917](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L917), [1002](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1002), [1104](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1104), [1254](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1254)]


```solidity
File: ./contracts/PanopticFactory.sol

26: contract PanopticFactory is Multicall {

34:     event OwnershipTransferred(address indexed oldOwner, address indexed newOwner);

43:     event PoolDeployed(

115:     constructor(

134:     function initialize(address _owner) public {

147:     function transferOwnership(address newOwner) external {

159:     function owner() external view returns (address) {

335:     function _mintFullRange(

420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {

```
*Github:* [[26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L26), [34](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L34), [43](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L43), [115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L115), [134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L134), [147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L147), [159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L159), [335](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L335), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L420)]


```solidity
File: ./contracts/PanopticPool.sol

62:     event PremiumSettled(

280:     constructor(SemiFungiblePositionManager _sfpm) {

352:     function optionPositionBalance(

429:     function _calculateAccumulatedPremia(

499:     function _getSlippageLimits(

522:     function pokeMedian() external {

547:     function mintOptions(

614:     function _mintOptions(

794:     function _burnAllOptionsFrom(

826:     function _burnOptions(

859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

955:     function _burnAndHandleExercise(

1290:     function _checkSolvencyAtTick(

1339:     function _getSolvencyBalances(

1425:     function univ3pool() external view returns (IUniswapV3Pool) {

1431:     function collateralToken0() external view returns (CollateralTracker collateralToken) {

1437:     function collateralToken1() external view returns (CollateralTracker) {

1444:     function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

1450:     function getUniV3TWAP() internal view returns (int24 twapTick) {

1465:     function _checkLiquiditySpread(

1503:     function _getPremia(

```
*Github:* [[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L62), [280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L280), [352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L352), [429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L429), [499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L499), [522](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L522), [547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L547), [614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L614), [794](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L794), [826](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L826), [859](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L859), [955](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L955), [1290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1290), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1339), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1425), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1437), [1444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1444), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1450), [1465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1465), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1503)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

90:         uint128 positionSize

347:     /// @param token0 The contract address of token0 of the pool

355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

524:             slippageTickLimitHigh,

708:         (totalMoved, collectedByLeg, itmAmounts) = _createPositionInAMM(

786:             // this is simply a convenience feature, and should be treated as such

1137:     /// @dev stored fees base is rounded up and the current fees base is rounded down to minimize the amount of fees collected (Δfeesbase) in favor of the protocol

1288:                 uint128(amountToCollect.rightSlot()),

```
*Github:* [[90](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L90), [347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L347), [355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L355), [524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L524), [708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L708), [786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L786), [1137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1137), [1288](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1288)]


```solidity
File: ./contracts/libraries/CallbackLib.sol

12: library CallbackLib {

30:     function validateCallback(

```
*Github:* [[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L12), [30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L30)]


```solidity
File: ./contracts/libraries/Constants.sol

7: library Constants {

```
*Github:* [[7](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L7)]


```solidity
File: ./contracts/libraries/Errors.sol

7: library Errors {

```
*Github:* [[7](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L7)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

50:     ) external view returns (int256 value0, int256 value1) {

```
*Github:* [[50](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L50)]


```solidity
File: ./contracts/libraries/InteractionHelper.sol

17: library InteractionHelper {

24:     function doApprovals(

91:     function computeSymbol(

107:     function computeDecimals(address token) external view returns (uint8) {

```
*Github:* [[17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L17), [24](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L24), [91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L91), [107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L107)]


```solidity
File: ./contracts/libraries/Math.sol

13: library Math {

25:     function min24(int24 a, int24 b) internal pure returns (int24) {

33:     function max24(int24 a, int24 b) internal pure returns (int24) {

41:     function min(uint256 a, uint256 b) internal pure returns (uint256) {

49:     function min(int256 a, int256 b) internal pure returns (int256) {

57:     function max(uint256 a, uint256 b) internal pure returns (uint256) {

65:     function max(int256 a, int256 b) internal pure returns (int256) {

91:     function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {

207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

221:     function getAmountsForLiquidity(

296:     function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

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
*Github:* [[13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L13), [25](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L33), [41](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L41), [49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L57), [65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L65), [91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L91), [207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L207), [221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L221), [296](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L296), [302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L302), [311](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L311), [318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L318), [325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L325), [440](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L440), [458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L521), [584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L584), [598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L598), [661](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L661), [675](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L675), [738](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L738), [753](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L753), [776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L776)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

18: library PanopticMath {

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

75:     function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

292:         uint128 positionSize

342:     ) internal pure returns (int24 tickLower, int24 tickUpper) {

393:     ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {

421:         LeftRightUnsigned tokenData1,

447:         LeftRightUnsigned tokenData1,

577:         uint256 legIndex

610:         uint256 legIndex

653:         LeftRightUnsigned tokenData1,

919:         LeftRightSigned refundValues,

```
*Github:* [[18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L18), [59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L59), [75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L75), [292](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L292), [342](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L342), [393](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L393), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L421), [447](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L447), [577](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L577), [610](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L610), [653](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L653), [919](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L919)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:     function safeTransfer(address token, address to, uint256 amount) internal {

```
*Github:* [[21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L21), [52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L52)]


```solidity
File: ./contracts/multicall/Multicall.sol

12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {

```
*Github:* [[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L12)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

22:     event TransferSingle(

36:     event TransferBatch(

48:     event ApprovalForAll(address indexed owner, address indexed operator, bool approved);

81:     function setApprovalForAll(address operator, bool approved) public {

200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

214:     function _mint(address to, uint256 id, uint256 amount) internal {

236:     function _burn(address from, uint256 id, uint256 amount) internal {

```
*Github:* [[22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L22), [36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L36), [48](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L48), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L81), [200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L200), [214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L214), [236](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L236)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

18:     event Transfer(address indexed from, address indexed to, uint256 amount);

24:     event Approval(address indexed owner, address indexed spender, uint256 amount);

49:     function approve(address spender, uint256 amount) public returns (bool) {

61:     function transfer(address to, uint256 amount) public virtual returns (bool) {

103:     function _transferFrom(address from, address to, uint256 amount) internal {

122:     function _mint(address to, uint256 amount) internal {

136:     function _burn(address from, uint256 amount) internal {

```
*Github:* [[18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L18), [24](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L24), [49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L49), [61](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L61), [103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L103), [122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L122), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L136)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

6: interface IDonorNFT {

13:     function issueNFT(

```
*Github:* [[6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L6), [13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L13)]


```solidity
File: ./contracts/tokens/interfaces/IERC20Partial.sol

27:     function transfer(address to, uint256 amount) external;

```
*Github:* [[27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L27)]


```solidity
File: ./contracts/types/LeftRight.sol

17: library LeftRightLibrary {

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

```
*Github:* [[17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L17), [39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L39), [46](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L46), [59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L59), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L78), [101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L101), [108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L108), [121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L121), [134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L134), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L148), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L171), [194](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L194), [214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L232), [251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L251)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

54:     uint256 internal constant CLEAR_TL_MASK =

75:         unchecked {

94:             return LiquidityChunk.wrap(LiquidityChunk.unwrap(self) + amount);

107:             return

123:             // convert tick upper to uint24 as explicit conversion from int24 to uint256 is not allowed

139:         unchecked {

155:         unchecked {

173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));

182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));

191:             return uint128(LiquidityChunk.unwrap(self));

```
*Github:* [[54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L54), [75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L75), [94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L94), [107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L107), [123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L123), [139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L139), [155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L155), [173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L173), [182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L182), [191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L191)]


```solidity
File: ./contracts/types/TokenId.sol

60: library TokenIdLibrary {

87:     function poolId(TokenId self) internal pure returns (uint64) {

96:     function tickSpacing(TokenId self) internal pure returns (int24) {

118:     function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {

128:     function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {

138:     function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {

148:     function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {

158:     function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

221:     function addOptionRatio(

240:     function addIsLong(

255:     function addTokenType(

273:     function addRiskPartner(

291:     function addStrike(

310:     function addWidth(

336:     function addLeg(

404:     function countLongs(TokenId self) internal pure returns (uint256) {

464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```
*Github:* [[60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L60), [87](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L87), [96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L96), [118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L118), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L128), [138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L138), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L148), [158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L158), [183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L183), [193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L193), [221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L221), [240](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L240), [255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L255), [273](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L273), [291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L291), [310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L310), [336](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L336), [404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L404), [464](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L464)]


</details>


<a name="NC-47"></a> 
### [NC-47] Missing NatSpec `@notice` from contract/event/function/modifier declarations
Some contract definitions have an incomplete NatSpec: add a `@notice` notation to improve the code documentation.

<details>
<summary>
There are <b>12</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

178:     constructor(

323:     function transfer(

341:     function transferFrom(

741:     function _poolUtilization() internal view returns (int256 poolUtilization) {

```
*Github:* [[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178), [323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L341), [741](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L741)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

708:         (totalMoved, collectedByLeg, itmAmounts) = _createPositionInAMM(

```
*Github:* [[708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L708)]


```solidity
File: ./contracts/libraries/InteractionHelper.sol

17: library InteractionHelper {

```
*Github:* [[17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L17)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

18: library PanopticMath {

```
*Github:* [[18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L18)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

11: abstract contract ERC1155 {

```
*Github:* [[11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L11)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

9: abstract contract ERC20Minimal {

```
*Github:* [[9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L9)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

6: interface IDonorNFT {

```
*Github:* [[6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L6)]


```solidity
File: ./contracts/tokens/interfaces/IERC20Partial.sol

11: interface IERC20Partial {

```
*Github:* [[11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L11)]


```solidity
File: ./contracts/types/TokenId.sol

464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```
*Github:* [[464](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L464)]


</details>


<a name="NC-48"></a> 
### [NC-48] Missing NatSpec `@param` from event/function/modifier declarations
Some event definitions have an incomplete NatSpec: add a `@param` notation to improve the code documentation.

*There are <b>5</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

/// @audit missing @param for `_commissionFee`
/// @audit missing @param for `_sellerCollateralRatio`
/// @audit missing @param for `_buyerCollateralRatio`
/// @audit missing @param for `_forceExerciseCost`
/// @audit missing @param for `_targetPoolUtilization`
/// @audit missing @param for `_saturatedPoolUtilization`
/// @audit missing @param for `_ITMSpreadMultiplier`
178:     constructor(
             uint256 _commissionFee,
             uint256 _sellerCollateralRatio,
             uint256 _buyerCollateralRatio,
             int256 _forceExerciseCost,
             uint256 _targetPoolUtilization,
             uint256 _saturatedPoolUtilization,
             uint256 _ITMSpreadMultiplier
         ) {
             COMMISSION_FEE = _commissionFee;

/// @audit missing @param for `recipient`
/// @audit missing @param for `amount`
323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions

/// @audit missing @param for `from`
/// @audit missing @param for `to`
/// @audit missing @param for `amount`
341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions

```
*Github:* [[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178), [323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L341)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit missing @param for `atTick`
429:     function _calculateAccumulatedPremia(
             address user,
             TokenId[] calldata positionIdList,
             bool computeAllPremia,
             bool includePendingPremium,
             int24 atTick
         ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

```
*Github:* [[429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L429)]


```solidity
File: ./contracts/libraries/Math.sol

/// @audit missing @param for `toDowncast`
302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {
             if ((downcastedInt = uint128(toDowncast)) != toDowncast) {

```
*Github:* [[302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L302)]



<a name="NC-49"></a> 
### [NC-49] Missing NatSpec `@return` from function declaration
Some function definitions have an incomplete NatSpec: add a `@return` notation to improve the code documentation.

*There are <b>8</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions

341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions

```
*Github:* [[323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L341)]


```solidity
File: ./contracts/PanopticPool.sol

794:     function _burnAllOptionsFrom(
             address owner,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool commitLongSettled,
             TokenId[] calldata positionIdList
         ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

955:     function _burnAndHandleExercise(
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
         {

1290:     function _checkSolvencyAtTick(
              address account,
              TokenId[] calldata positionIdList,
              int24 currentTick,
              int24 atTick,
              uint256 buffer
          ) internal view returns (bool) {

1503:     function _getPremia(
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
          {
              uint256 numLegs = tokenId.countLegs();

1802:     function _getTotalLiquidity(
              TokenId tokenId,
              uint256 leg
          ) internal view returns (uint256 totalLiquidity) {
              unchecked {

```
*Github:* [[794](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L794), [955](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L955), [1290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1290), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1503), [1802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1802)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))
                      )
                      .toLeftSlot(
                          int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))
                      )
                  : LeftRightSigned

```
*Github:* [[1169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1169)]



<a name="NC-50"></a> 
### [NC-50] Missing NatSpec `@title` from contract declaration
Some contract definitions have an incomplete NatSpec: add a `@title` notation to improve the code documentation.

*There are <b>5</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

```
*Github:* [[36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36)]


```solidity
File: ./contracts/libraries/InteractionHelper.sol

17: library InteractionHelper {

```
*Github:* [[17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L17)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

11: library SafeTransferLib {

```
*Github:* [[11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L11)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

6: interface IDonorNFT {

```
*Github:* [[6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L6)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

54:     uint256 internal constant CLEAR_TL_MASK =

```
*Github:* [[54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L54)]



<a name="NC-51"></a> 
### [NC-51] There is no need to initialize variables with 0
Since the variables are automatically set to 0 when created, it is redundant to initialize it with 0 again.

<details>
<summary>
There are <b>31</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

1208:         for (uint256 i = 0; i < totalIterations; ) {

1255:             for (uint256 index = 0; index < numLegs; ++index) {

```
*Github:* [[662](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L662), [1208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1208), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1255)]


```solidity
File: ./contracts/PanopticPool.sol

441:         for (uint256 k = 0; k < pLength; ) {

459:             for (uint256 leg = 0; leg < numLegs; ) {

745:         for (uint256 leg = 0; leg < numLegs; ) {

802:         for (uint256 i = 0; i < positionIdList.length; ) {

864:         for (uint256 leg = 0; leg < numLegs; ) {

1382:         for (uint256 i = 0; i < pLength; ) {

1518:         for (uint256 leg = 0; leg < numLegs; ) {

1672:         for (uint256 leg = 0; leg < numLegs; ++leg) {

1852:         for (uint256 leg = 0; leg < numLegs; ) {

```
*Github:* [[441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L441), [459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L459), [745](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L745), [802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L802), [864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L864), [1382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1382), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1518), [1672](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1672), [1852](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1852)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

575:         for (uint256 i = 0; i < ids.length; ) {

601:         for (uint256 leg = 0; leg < numLegs; ) {

882:         for (uint256 leg = 0; leg < numLegs; ) {

```
*Github:* [[575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L575), [601](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L601), [882](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L882)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

51:         for (uint256 k = 0; k < positionIdList.length; ) {

55:             for (uint256 leg = 0; leg < numLegs; ) {

```
*Github:* [[51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L51), [55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L55)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

137:             for (uint256 i = 0; i < cardinality + 1; ++i) {

148:             for (uint256 i = 0; i < cardinality; ++i) {

248:             for (uint256 i = 0; i < 20; ++i) {

256:             for (uint256 i = 0; i < 19; ++i) {

395:         for (uint256 leg = 0; leg < numLegs; ) {

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

```
*Github:* [[137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L137), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L148), [248](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L248), [256](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L256), [395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L395), [781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L781), [784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L784), [860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L860), [863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L863)]


```solidity
File: ./contracts/multicall/Multicall.sol

14:         for (uint256 i = 0; i < data.length; ) {

```
*Github:* [[14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L14)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {

```
*Github:* [[143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L143), [187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L187)]


```solidity
File: ./contracts/types/TokenId.sol

507:             for (uint256 i = 0; i < 4; ++i) {

581:             for (uint256 i = 0; i < numLegs; ++i) {

```
*Github:* [[507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L507), [581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L581)]


</details>


<a name="NC-52"></a> 
### [NC-52] Non-assembly method available
There are some automated tools that will flag a project as having higher complexity if there is inline-assembly, so it's best to avoid using it where it's not necessary. In addition, most assembly methods can be replaced by non-assembly methods, for example:
- `assembly{ g := gas() }` => `uint256 g = gasleft()`
- `assembly{ id := chainid() }` => `uint256 id = block.chainid`
- `assembly { r := mulmod(a, b, d) }` => `uint256 m = mulmod(x, y, k)`
- `assembly { size := extcodesize() }` => `uint256 size = address(a).code.length`
- etc.

*There are <b>10</b> instances of this issue:*
```solidity
File: ./contracts/libraries/Math.sol

354:                 let mm := mulmod(a, b, not(0))

380:                 remainder := mulmod(a, b, denominator)

468:                 let mm := mulmod(a, b, not(0))

494:                 remainder := mulmod(a, b, 0x10000000000000000)

531:                 let mm := mulmod(a, b, not(0))

557:                 remainder := mulmod(a, b, 0x1000000000000000000000000)

608:                 let mm := mulmod(a, b, not(0))

634:                 remainder := mulmod(a, b, 0x100000000000000000000000000000000)

685:                 let mm := mulmod(a, b, not(0))

711:                 remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)

```
*Github:* [[354](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L354), [380](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L380), [468](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L468), [494](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L494), [531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L531), [557](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L557), [608](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L608), [634](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L634), [685](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L685), [711](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L711)]



<a name="NC-53"></a> 
### [NC-53] Put all system-wide constants in one file
Putting all the system-wide constants in a single file improves code readability, makes it easier to understand the basic configuration and limitations of the system, and makes maintenance easier.

<details>
<summary>
There are <b>49</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

70:     string internal constant TICKER_PREFIX = "po";

73:     string internal constant NAME_PREFIX = "POPT-V1";

77:     uint256 internal constant DECIMALS = 10_000;

81:     int128 internal constant DECIMALS_128 = 10_000;

```
*Github:* [[70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L73), [77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L81)]


```solidity
File: ./contracts/PanopticFactory.sol

82:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;

86:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

89:     uint16 internal constant CARDINALITY_INCREASE = 100;

```
*Github:* [[82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L82), [86](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L86), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L89)]


```solidity
File: ./contracts/PanopticPool.sol

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

```
*Github:* [[103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L109), [111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L111), [114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L114), [119](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L119), [120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L120), [123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L123), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L128), [133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L133), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L136), [139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L139), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L145), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L148), [152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L152), [156](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L156), [160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L160), [165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L165), [168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L168), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L171), [174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L174)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

133:     uint128 private constant VEGOID = 2;

135:     /// @dev Uniswap V3 Factory address. Initialized in the constructor.

144:     /// @dev pool address => pool id + 2 ** 255 (initialization bit for `poolId == 0`, set if the pool exists)

```
*Github:* [[133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L133), [135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L135), [144](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L144)]


```solidity
File: ./contracts/libraries/Constants.sol

9:     uint256 internal constant FP96 = 0x1000000000000000000000000;

12:     int24 internal constant MIN_V3POOL_TICK = -887272;

15:     int24 internal constant MAX_V3POOL_TICK = 887272;

18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

21:     uint160 internal constant MAX_V3POOL_SQRT_RATIO =

```
*Github:* [[9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L9), [12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L12), [15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L15), [18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L18), [21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L21)]


```solidity
File: ./contracts/libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*Github:* [[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L15)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

26:     uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

```
*Github:* [[23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L26)]


```solidity
File: ./contracts/types/LeftRight.sol

22:     uint256 internal constant LEFT_HALF_BIT_MASK =

26:     int256 internal constant LEFT_HALF_BIT_MASK_INT =

30:     int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```
*Github:* [[22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L22), [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L26), [30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L30)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

57:     /// @notice AND mask to strip the `tickUpper` value from a packed LiquidityChunk

61:     /*//////////////////////////////////////////////////////////////

```
*Github:* [[57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L57), [61](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L61)]


```solidity
File: ./contracts/types/TokenId.sol

62:     uint256 internal constant LONG_MASK =

66:     uint256 internal constant CLEAR_POOLID_MASK =

70:     uint256 internal constant OPTION_RATIO_MASK =

74:     uint256 internal constant CHUNK_MASK =

78:     int256 internal constant BITMASK_INT24 = 0xFFFFFF;

```
*Github:* [[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L62), [66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L70), [74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L74), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L78)]


</details>


<a name="NC-54"></a> 
### [NC-54] Redundant `return` statement in a function with named return variables
Because the return variable (or its default value) has been assigned, explicit return at the end of the function is unnecessary, as it is returned automatically.

<details>
<summary>
There are <b>21</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

361:     function asset() external view returns (address assetTokenAddress) {

370:     function totalAssets() public view returns (uint256 totalManagedAssets) {

379:     function convertToShares(uint256 assets) public view returns (uint256 shares) {

386:     function convertToAssets(uint256 shares) public view returns (uint256 assets) {

392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

444:     function maxMint(address) external view returns (uint256 maxShares) {

507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

518:     function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

531:     function withdraw(

572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {

581:     function previewRedeem(uint256 shares) public view returns (uint256 assets) {

591:     function redeem(

741:     function _poolUtilization() internal view returns (int256 poolUtilization) {

751:     function _sellCollateralRatio(

806:     function _buyCollateralRatio(

1167:         // if the account has active options, compute the required collateral to keep account in good health

1206:         // (a potentially newly minted position)

```
*Github:* [[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L370), [379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444), [507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L507), [518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L518), [531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L531), [572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L581), [591](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L591), [741](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L741), [751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L751), [806](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L806), [1167](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1167), [1206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1206)]


```solidity
File: ./contracts/PanopticPool.sol

1431:     function collateralToken0() external view returns (CollateralTracker collateralToken) {

```
*Github:* [[1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1431)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

786:             // this is simply a convenience feature, and should be treated as such

1570: 

```
*Github:* [[786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L786), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570)]


```solidity
File: ./contracts/libraries/Math.sol

340:     function mulDiv(

```
*Github:* [[340](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L340)]


</details>


<a name="NC-55"></a> 
### [NC-55] Lines are too long
The [solidity style guide](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#maximum-line-length) recommends a maximum line length of 120 characters. Lines of code that are longer than 120 should be wrapped.

*There are <b>5</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

727:             int256 fee = (FORCE_EXERCISE_COST >> (maxNumRangesFromStrike - 1)); // exponential decay of fee based on number of half ranges away from the price

851:                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

```
*Github:* [[727](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L727), [851](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L851), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1374), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1375)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

219:         For an arbitrary parameter 0 <= ν <= 1 (ν = 1/2^VEGOID). This way, the gross_feesCollectedX128 will be given by: 

```
*Github:* [[219](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L219)]



<a name="NC-56"></a> 
### [NC-56] Typos

<details>
<summary>
There are <b>11</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `initalized`
92:     /// @dev As each instance is deployed via proxy clone, initial parameters must only be initalized once via startToken().

/// @audit `premum`
1180:         // if premium is positive (ie. user will receive funds due to selling options), add this premum to the user's balance

```
*Github:* [[92](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L92), [1180](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1180)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `caluculation`
107:     // Flags used as arguments to premia caluculation functions

```
*Github:* [[107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L107)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `seperated`
1337:         // premia, and is only seperated to simplify the calculation

```
*Github:* [[1337](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1337)]


```solidity
File: ./contracts/libraries/Errors.sol

/// @audit `avaiable`
62:     /// @notice PanopticPool: there is not enough avaiable liquidity to buy an option

```
*Github:* [[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L62)]


```solidity
File: ./contracts/libraries/InteractionHelper.sol

/// @audit `metadada`
95:         // not guaranteed that token supports metadada extension

/// @audit `metadada`
108:         // not guaranteed that token supports metadada extension

```
*Github:* [[95](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L95), [108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L108)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit `stots`
247:             // construct the time stots

/// @audit `consistentcy`
663:                 // evaluate at TWAP price to keep consistentcy with solvency calculations

```
*Github:* [[247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L247), [663](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L663)]


```solidity
File: ./contracts/types/LeftRight.sol

/// @audit `explictily`
153:             // adding leftRight packed uint128's is same as just adding the values explictily

/// @audit `explictily`
176:             // subtracting leftRight packed uint128's is same as just subtracting the values explictily

```
*Github:* [[153](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L153), [176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L176)]


</details>


<a name="NC-57"></a> 
### [NC-57] Unnecessary cast
The variable is being cast to its own type.

<details>
<summary>
There are <b>120</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit no need to cast `utilization` into int256
784:         if (uint256(utilization) < TARGET_POOL_UTIL) {

/// @audit no need to cast `utilization` into uint256
784:         if (uint256(utilization) < TARGET_POOL_UTIL) {

/// @audit no need to cast `utilization` into int256
784:         if (uint256(utilization) < TARGET_POOL_UTIL) {

/// @audit no need to cast `utilization` into int256
784:         if (uint256(utilization) < TARGET_POOL_UTIL) {

/// @audit no need to cast `utilization` into int256
790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {

/// @audit no need to cast `utilization` into uint256
790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {

/// @audit no need to cast `utilization` into int256
790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {

/// @audit no need to cast `utilization` into int256
790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {

/// @audit no need to cast `utilization` into int256
797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

/// @audit no need to cast `utilization` into uint256
797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

/// @audit no need to cast `utilization` into int256
797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

/// @audit no need to cast `utilization` into int256
797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

/// @audit no need to cast `assets` into int256
959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into uint256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `assets` into int256
977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

/// @audit no need to cast `tokenToPay` into int256
1013:                     uint256(tokenToPay),

/// @audit no need to cast `tokenToPay` into int256
1013:                     uint256(tokenToPay),

/// @audit no need to cast `updatedAssets` into int256
1028:             s_poolAssets = uint128(uint256(updatedAssets));

/// @audit no need to cast `updatedAssets` into int256
1028:             s_poolAssets = uint128(uint256(updatedAssets));

/// @audit no need to cast `tokenToPay` into int256
1070:                     uint256(tokenToPay),

/// @audit no need to cast `tokenToPay` into int256
1070:                     uint256(tokenToPay),

/// @audit no need to cast `premiumAllPositions` into int128
1184:                 netBalance += uint256(uint128(premiumAllPositions));

/// @audit no need to cast `premiumAllPositions` into int128
1184:                 netBalance += uint256(uint128(premiumAllPositions));

/// @audit no need to cast `` into int128
1189:         tokenData = tokenData.toRightSlot(netBalance.toUint128()).toLeftSlot(

/// @audit no need to cast `` into int128
1190:             tokenRequired.toUint128()

/// @audit no need to cast `utilization` into int256
1491:             uint256 buyCollateral = _buyCollateralRatio(uint256(utilization));

/// @audit no need to cast `utilization` into uint256
1491:             uint256 buyCollateral = _buyCollateralRatio(uint256(utilization));

/// @audit no need to cast `utilization` into int256
1491:             uint256 buyCollateral = _buyCollateralRatio(uint256(utilization));

/// @audit no need to cast `utilization` into int256
1491:             uint256 buyCollateral = _buyCollateralRatio(uint256(utilization));

```
*Github:* [[784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L784), [784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L784), [784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L784), [784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L784), [790](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L790), [790](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L790), [790](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L790), [790](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L790), [797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L797), [797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L797), [797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L797), [797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L797), [959](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L959), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L977), [1013](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1013), [1013](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1013), [1028](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1028), [1028](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1028), [1070](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1070), [1070](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1070), [1184](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1184), [1184](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1184), [1189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1189), [1190](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1190), [1491](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1491), [1491](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1491), [1491](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1491), [1491](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1491)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit no need to cast `currentTick` into int24
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

/// @audit no need to cast `currentTick` into int24
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

/// @audit no need to cast `currentTick` into int24
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

/// @audit no need to cast `currentTick` into int24
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

/// @audit no need to cast `currentTick` into int24
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

/// @audit no need to cast `currentTick` into int24
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

/// @audit no need to cast `currentTick` into int24
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

/// @audit no need to cast `currentTick` into int24
314:                 (uint256(uint24(currentTick))); // add to slot 3

/// @audit no need to cast `currentTick` into int24
314:                 (uint256(uint24(currentTick))); // add to slot 3

/// @audit no need to cast `currentTick` into int24
314:                 (uint256(uint24(currentTick))); // add to slot 3

/// @audit no need to cast `currentTick` into int24
314:                 (uint256(uint24(currentTick))); // add to slot 3

/// @audit no need to cast `currentTick` into int24
314:                 (uint256(uint24(currentTick))); // add to slot 3

/// @audit no need to cast `currentTick` into int24
314:                 (uint256(uint24(currentTick))); // add to slot 3

/// @audit no need to cast `currentTick` into int24
314:                 (uint256(uint24(currentTick))); // add to slot 3

/// @audit no need to cast `utilization0` into int256
730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

/// @audit no need to cast `utilization1` into int256
730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

/// @audit no need to cast `totalLiquidity` into uint256
1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

/// @audit no need to cast `totalLiquidity` into uint256
1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

/// @audit no need to cast `totalLiquidity` into uint256
1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

/// @audit no need to cast `totalLiquidity` into uint256
1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

```
*Github:* [[313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [313](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L313), [314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L314), [314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L314), [314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L314), [314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L314), [314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L314), [314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L314), [314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L314), [730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730), [730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit no need to cast `amount0Delta` into int256
453:         uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);

/// @audit no need to cast `amount1Delta` into int256
453:         uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);

/// @audit no need to cast `univ3pool` into address
613:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
613:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
613:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
613:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
613:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
622:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
622:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
622:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
622:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
622:                     address(univ3pool),

/// @audit no need to cast `univ3pool` into address
976:                 address(univ3pool),

/// @audit no need to cast `univ3pool` into address
976:                 address(univ3pool),

/// @audit no need to cast `univ3pool` into address
976:                 address(univ3pool),

/// @audit no need to cast `univ3pool` into address
976:                 address(univ3pool),

/// @audit no need to cast `univ3pool` into address
976:                 address(univ3pool),

```
*Github:* [[453](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L453), [453](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L453), [613](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L613), [613](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L613), [613](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L613), [613](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L613), [613](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L613), [622](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L622), [622](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L622), [622](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L622), [622](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L622), [622](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L622), [976](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L976), [976](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L976), [976](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L976), [976](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L976), [976](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L976)]


```solidity
File: ./contracts/libraries/Math.sol

/// @audit no need to cast `x` into int256
83:             return x > 0 ? uint256(x) : uint256(-x);

/// @audit no need to cast `x` into int256
83:             return x > 0 ? uint256(x) : uint256(-x);

/// @audit no need to cast `toCast` into int256
327:         return int256(toCast);

/// @audit no need to cast `i` into int256
760:                 while (arr[uint256(i)] < pivot) i++;

/// @audit no need to cast `j` into int256
761:                 while (pivot < arr[uint256(j)]) j--;

/// @audit no need to cast `i` into int256
763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);

/// @audit no need to cast `j` into int256
763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);

```
*Github:* [[83](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L83), [83](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L83), [327](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L327), [760](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L760), [761](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L761), [763](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L763), [763](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L763)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit no need to cast `tickSpacing` into int24
51:             poolId += uint64(uint24(tickSpacing)) << 48;

/// @audit no need to cast `tickSpacing` into int24
51:             poolId += uint64(uint24(tickSpacing)) << 48;

/// @audit no need to cast `tickSpacing` into int24
51:             poolId += uint64(uint24(tickSpacing)) << 48;

/// @audit no need to cast `lastObservedTick` into int24
230:                     uint256(uint24(lastObservedTick));

/// @audit no need to cast `tickSpacing` into int24
377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

/// @audit no need to cast `width` into int24
377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

/// @audit no need to cast `tickSpacing` into int24
377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

/// @audit no need to cast `width` into int24
377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

/// @audit no need to cast `tickSpacing` into int24
377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

/// @audit no need to cast `haircut0` into int256
870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),

/// @audit no need to cast `haircut1` into int256
874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),

/// @audit no need to cast `balanceShortage` into int256
939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)

/// @audit no need to cast `balanceShortage` into int256
957:                                     PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)

```
*Github:* [[51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L51), [51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L51), [51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L51), [230](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L230), [377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L377), [377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L377), [377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L377), [377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L377), [377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L377), [870](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L870), [874](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L874), [939](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L939), [957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L957)]


```solidity
File: ./contracts/types/LeftRight.sol

/// @audit no need to cast `left` into int256
126:             return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));

/// @audit no need to cast `left` into int256
136:             return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));

/// @audit no need to cast `left` into int128
197:             int128 left128 = int128(left);

/// @audit no need to cast `right` into int128
202:             int128 right128 = int128(right);

```
*Github:* [[126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L126), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L136), [197](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L197), [202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L202)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

/// @audit no need to cast `_tickLower` into int24
78:                     (uint256(uint24(_tickLower)) << 232) +

/// @audit no need to cast `_tickLower` into int24
78:                     (uint256(uint24(_tickLower)) << 232) +

/// @audit no need to cast `_tickLower` into int24
78:                     (uint256(uint24(_tickLower)) << 232) +

/// @audit no need to cast `_tickUpper` into int24
79:                         (uint256(uint24(_tickUpper)) << 208) +

/// @audit no need to cast `_tickUpper` into int24
79:                         (uint256(uint24(_tickUpper)) << 208) +

/// @audit no need to cast `_tickUpper` into int24
79:                         (uint256(uint24(_tickUpper)) << 208) +

/// @audit no need to cast `_tickLower` into int24
109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

/// @audit no need to cast `_tickLower` into int24
109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

/// @audit no need to cast `_tickLower` into int24
109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

/// @audit no need to cast `_tickUpper` into int24
126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

/// @audit no need to cast `_tickUpper` into int24
126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

/// @audit no need to cast `_tickUpper` into int24
126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

```
*Github:* [[78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L78), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L78), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L78), [79](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L79), [79](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L79), [79](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L79), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L109), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L109), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L109), [126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L126), [126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L126), [126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L126)]


```solidity
File: ./contracts/types/TokenId.sol

/// @audit no need to cast `_tickSpacing` into int24
195:             return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

/// @audit no need to cast `_width` into int24
320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

/// @audit no need to cast `_width` into int24
320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

```
*Github:* [[195](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L195), [320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L320), [320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L320)]


</details>


<a name="NC-58"></a> 
### [NC-58] Unsafe conversion from unsigned to signed values
Solidity follows [two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) rules for its integers, meaning that the most significant bit for signed integers is used to denote the sign, and converting between the two requires inverting all of the bits and adding one. Because of this, casting an unsigned integer to a signed one may result in a change of the sign and or magnitude of the value. For example, `int8(type(uint8).max)` is not equal to `type(int8).max`, but is equal to `-1`. `type(uint8).max` in binary is `11111111`, which if cast to a signed value, means the first binary `1` indicates a negative value, and the binary `1`s, invert to all zeroes, and when one is added, it becomes one, but negative, and therefore the decimal value of binary `11111111` is `-1`.

<details>
<summary>
There are <b>79</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit uint256 -> int256
200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

/// @audit uint256 -> int256
668:                         int256(

/// @audit uint128 -> int128
715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

/// @audit uint128 -> int128
715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

/// @audit uint128 -> int128
718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

/// @audit uint128 -> int128
718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

/// @audit uint256 -> int256
743:             return int256((s_inAMM * DECIMALS) / totalAssets());

/// @audit uint256 -> int256
969:     /// @notice Refunds delegated tokens to 'refunder' from 'refundee', similar to 'revoke'

/// @audit uint256 -> int256
969:     /// @notice Refunds delegated tokens to 'refunder' from 'refundee', similar to 'revoke'

/// @audit uint256 -> int256
1008:             // compute tokens to be paid due to swap

/// @audit uint256 -> int256
1037:     /// @param optionOwner The owner of the option being burned and potentially exercised.

/// @audit uint256 -> int256
1058:             int256 intrinsicValue = swappedAmount - (longAmount - shortAmount);

/// @audit uint256 -> int256
1094:     /// @param swappedAmount The (potential) amount swapped during any ITM option creations.

/// @audit uint256 -> int256
1123:                 )

/// @audit uint256 -> int256
1129:                      HEALTH AND COLLATERAL TRACKING

/// @audit uint64 -> int64
1337:         // if the position is long, required tokens does not depend on price

/// @audit uint64 -> int64
1337:         // if the position is long, required tokens does not depend on price

/// @audit uint64 -> int64
1593:     /// @dev A strangle can only have only one of its leg tested at the same time, so this reduces the total risk and collateral requirement.

/// @audit uint64 -> int64
1593:     /// @dev A strangle can only have only one of its leg tested at the same time, so this reduces the total risk and collateral requirement.

/// @audit uint64 -> int64
1644:                     positionSize,

/// @audit uint64 -> int64
1648:         }

```
*Github:* [[200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L200), [668](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L668), [715](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L715), [715](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L715), [718](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L718), [718](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L718), [743](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L743), [969](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L969), [969](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L969), [1008](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1008), [1037](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1037), [1058](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1058), [1094](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1094), [1123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1123), [1129](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1129), [1337](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1337), [1337](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1337), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1593), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1593), [1644](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1644), [1648](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1648)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit uint256 -> int256
477:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

/// @audit uint256 -> int256
1144:             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)

/// @audit uint256 -> int256
1149:             uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)

/// @audit uint256 -> int256
1550:                                     ((premiumAccumulatorsByLeg[leg][0] -

/// @audit uint256 -> int256
1559:                                     ((premiumAccumulatorsByLeg[leg][1] -

/// @audit uint256 -> int256
1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

/// @audit uint256 -> int256
1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

/// @audit uint256 -> int256
1870:                                         .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))

/// @audit uint256 -> int256
1901:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

/// @audit uint256 -> int256
1936:                                                     grossPremiumLast.rightSlot() *

/// @audit uint256 -> int256
1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *

/// @audit uint256 -> int256
1953:                                                     grossPremiumLast.leftSlot() *

/// @audit uint256 -> int256
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *

```
*Github:* [[477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L477), [1144](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1144), [1149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1149), [1550](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1550), [1559](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1559), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1636), [1870](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1870), [1901](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1901), [1936](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1936), [1940](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1940), [1953](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1953), [1957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1957)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit uint256 -> int256
1202:         /// @dev this triggers the uniswap mint callback function

/// @audit uint256 -> int256
1204:             address(this),

/// @audit uint256 -> int256
1211:         // amount0 The amount of token0 that was paid to mint the given amount of liquidity

/// @audit uint256 -> int256
1212:         // amount1 The amount of token1 that was paid to mint the given amount of liquidity

/// @audit uint256 -> int256
1247:     /// @notice Helper to collect amounts between msg.sender and Uniswap and also to update the Uniswap fees collected to date from the AMM.

/// @audit uint256 -> int256
1247:     /// @notice Helper to collect amounts between msg.sender and Uniswap and also to update the Uniswap fees collected to date from the AMM.

/// @audit uint256 -> int256
1267:         // When this is the case, we want to behave as if there are 0 fees, so we just rectify the values.

/// @audit uint256 -> int256
1267:         // When this is the case, we want to behave as if there are 0 fees, so we just rectify the values.

```
*Github:* [[1202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1202), [1204](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1204), [1211](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1211), [1212](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1212), [1247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1247), [1247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1247), [1267](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1267), [1267](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1267)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

/// @audit uint256 -> int256
75:                         value1 -= int256(amount1);

/// @audit uint256 -> int256
77:                 }

/// @audit uint256 -> int256
84:                 ++k;

/// @audit uint256 -> int256
89:     /// @notice Calculate the AMM Swap/trading fees for a `liquidityChunk` of each token.

/// @audit uint256 -> int256
121:     /// @notice Calculates the fee growth that has occurred (per unit of liquidity) in the AMM/Uniswap for an

/// @audit uint256 -> int256
123:     /// @dev Extracts the feeGrowth from the uniswap v3 pool.

```
*Github:* [[75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L75), [77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L77), [84](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L84), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L89), [121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L121), [123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L123)]


```solidity
File: ./contracts/libraries/Math.sol

/// @audit uint128 -> int128
312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

/// @audit uint256 -> int256
327:         return int256(toCast);

/// @audit uint256 -> int256
778:             quickSort(data, int256(0), int256(data.length - 1));

```
*Github:* [[312](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L312), [327](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L327), [778](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L778)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit uint256 -> int256
140:                         (int256(observationIndex) - int256(i * period)) +

/// @audit uint256 -> int256
140:                         (int256(observationIndex) - int256(i * period)) +

/// @audit uint256 -> int256
141:                             int256(observationCardinality)

/// @audit uint256 -> int256
151:                     int256(timestamps[i] - timestamps[i + 1]);

/// @audit uint24 -> int24
178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

/// @audit uint24 -> int24
179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

/// @audit uint256 -> int256
188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)

/// @audit uint256 -> int256
188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)

/// @audit uint256 -> int256
196:                             int256(timestamp_last - timestamp_old)

/// @audit uint24 -> int24
217:                     entry = int24(uint24(medianData >> (rank * 24)));

/// @audit uint56 -> int56
258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

/// @audit uint256 -> int256
379:     }

/// @audit uint256 -> int256
684:                     PanopticMath.convert0to1(

/// @audit uint256 -> int256
685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

/// @audit uint256 -> int256
694:                 Math.max(premia.rightSlot(), 0);

/// @audit uint256 -> int256
697: 

/// @audit uint256 -> int256
931:             if (balanceShortage > 0) {

/// @audit uint256 -> int256
939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)

/// @audit uint256 -> int256
949:             if (balanceShortage > 0) {

/// @audit uint256 -> int256
957:                                     PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)

```
*Github:* [[140](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L140), [140](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L140), [141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L141), [151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L151), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L178), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L179), [188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L188), [188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L188), [196](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L196), [217](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L217), [258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L258), [379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L379), [684](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L684), [685](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L685), [694](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L694), [697](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L697), [931](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L931), [939](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L939), [949](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L949), [957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L957)]


```solidity
File: ./contracts/types/LeftRight.sol

/// @audit uint256 -> int256
27:         int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

/// @audit uint256 -> int256
196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();

/// @audit uint256 -> int256
201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();

```
*Github:* [[27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L27), [196](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L196), [201](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L201)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

/// @audit uint256 -> int256
178:     /// @param self The LiquidityChunk to get the upper tick from

/// @audit uint256 -> int256
187:     /// @param self The LiquidityChunk to get the liquidity from

```
*Github:* [[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L178), [187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L187)]


```solidity
File: ./contracts/types/TokenId.sol

/// @audit uint24 -> int24
98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

/// @audit uint256 -> int256
160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

/// @audit uint256 -> int256
171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

```
*Github:* [[98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L98), [160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L171)]


</details>


<a name="NC-59"></a> 
### [NC-59] Unsafe solidity low-level call can cause gas grief attack
Using the low-level calls of a solidity address can leave the contract open to gas grief attacks. These attacks occur when the called contract returns a large amount of data. So when calling an external contract, it is necessary to check the length of the return data before reading/copying it (using `returndatasize()`).

*There is one instance of this issue:*
```solidity
File: ./contracts/multicall/Multicall.sol

15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);

```
*Github:* [[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L15)]



<a name="NC-60"></a> 
### [NC-60] Unused `error` definition
The following `error`s are defined but not used. It is recommended to check the code for logical omissions that cause them not to be used. If it's determined that they are not needed anywhere, it's best to remove them from the codebase to improve code clarity and minimize confusion. Note that there may be cases where an error appears to be used because it has multiple definitions in different files. In such cases, the definitions should be moved to a separate file.

<details>
<summary>
There are <b>33</b> instances (click to show):
</summary>

```solidity
File: ./contracts/libraries/Errors.sol

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

42:     error InvalidTokenIdParameter(uint256 parameterType);

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
*Github:* [[10](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L10), [13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L13), [16](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L16), [20](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L20), [23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L26), [29](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L29), [32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L32), [35](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L35), [38](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L38), [42](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L42), [45](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L45), [48](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L48), [51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L51), [54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L54), [57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L57), [60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L60), [63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L73), [76](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L76), [79](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L79), [82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L82), [85](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L85), [88](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L88), [91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L91), [95](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L95), [98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L98), [101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L105), [108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L108), [111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L111)]


</details>


<a name="NC-61"></a> 
### [NC-61] Unused arguments should be removed or implemented
Some arguments are never used: if this is intentional, consider removing these arguments from the function. Otherwise, implement the missing logic accordingly.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

/// @audit `deployer`
/// @audit `newPoolContract`
/// @audit `token0`
/// @audit `token1`
/// @audit `fee`
13:     function issueNFT(

```
*Github:* [[13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L13)]


```solidity
File: ./contracts/tokens/interfaces/IERC20Partial.sol

/// @audit `account`
16:     function balanceOf(address account) external view returns (uint256);

/// @audit `spender`
/// @audit `amount`
22:     function approve(address spender, uint256 amount) external;

/// @audit `to`
/// @audit `amount`
27:     function transfer(address to, uint256 amount) external;

```
*Github:* [[16](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L16), [22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L22), [27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L27)]



<a name="NC-62"></a> 
### [NC-62] Unused import
The identifier is imported but never used within the file.

*There is one instance of this issue:*
```solidity
File: ./contracts/types/LiquidityChunk.sol

/// @audit `TokenId`
5: import {TokenId} from "@types/TokenId.sol";

```
*Github:* [[5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L5)]



<a name="NC-63"></a> 
### [NC-63] Unused named return
Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment. This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

<details>
<summary>
There are <b>18</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `assetTokenAddress` not used
361:     function asset() external view returns (address assetTokenAddress) {
             return s_underlyingToken;

/// @audit `totalManagedAssets` not used
370:     function totalAssets() public view returns (uint256 totalManagedAssets) {
             unchecked {

/// @audit `shares` not used
379:     function convertToShares(uint256 assets) public view returns (uint256 shares) {
             return Math.mulDiv(assets, totalSupply, totalAssets());

/// @audit `assets` not used
386:     function convertToAssets(uint256 shares) public view returns (uint256 assets) {
             return Math.mulDiv(shares, totalAssets(), totalSupply);

/// @audit `maxAssets` not used
392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {
             return type(uint104).max;

/// @audit `maxShares` not used
444:     function maxMint(address) external view returns (uint256 maxShares) {
             unchecked {

/// @audit `maxAssets` not used
507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {
             // We can only use the standard 4626 withdraw function if the user has no open positions

/// @audit `shares` not used
518:     function previewWithdraw(uint256 assets) public view returns (uint256 shares) {
             uint256 supply = totalSupply; // Saves an extra SLOAD if totalSupply is non-zero.

/// @audit `maxShares` not used
572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {
             uint256 available = convertToShares(s_poolAssets);

/// @audit `assets` not used
581:     function previewRedeem(uint256 shares) public view returns (uint256 assets) {
             return convertToAssets(shares);

/// @audit `poolUtilization` not used
741:     function _poolUtilization() internal view returns (int256 poolUtilization) {
             unchecked {

/// @audit `sellCollateralRatio` not used
751:     function _sellCollateralRatio(
             int256 utilization
         ) internal view returns (uint256 sellCollateralRatio) {
             // the sell ratio is on a straight line defined between two points (x0,y0) and (x1,y1):

/// @audit `buyCollateralRatio` not used
806:     function _buyCollateralRatio(
             uint256 utilization
         ) internal view returns (uint256 buyCollateralRatio) {
             // linear from BUY to BUY/2 between 50% and 90%

/// @audit `required` not used
1286:             tokenId.riskPartner(index) == index // does this leg have a risk partner? Affects required collateral
                      ? _getRequiredCollateralSingleLegNoPartner(
                          tokenId,
                          index,
                          positionSize,
                          atTick,
                          poolUtilization

```
*Github:* [[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L370), [379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444), [507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L507), [518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L518), [572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L581), [741](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L741), [751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L751), [806](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L806), [1286](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1286)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `premium0` not used
/// @audit `premium1` not used
/// @audit `` not used
381:     function calculateAccumulatedFeesBatch(
             address user,
             bool includePendingPremium,
             TokenId[] calldata positionIdList
         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

/// @audit `collateralToken` not used
1431:     function collateralToken0() external view returns (CollateralTracker collateralToken) {
              return s_collateralToken0;

```
*Github:* [[381](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L381), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1431)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `UniswapV3Pool` not used
1570: 

```
*Github:* [[1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit `` not used
653:         LeftRightUnsigned tokenData1,
             uint160 sqrtPriceX96Twap,
             uint160 sqrtPriceX96Final,
             LeftRightSigned netExchanged,
             LeftRightSigned premia
         ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {
             unchecked {
                 // compute bonus as min(collateralBalance/2, required-collateralBalance)

```
*Github:* [[653](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L653)]


</details>


<a name="NC-64"></a> 
### [NC-64] Unused contract variables
The following state variables are defined but not used. It is recommended to check the code for logical omissions that cause them not to be used. If it's determined that they are not needed anywhere, it's best to remove them from the codebase to improve code clarity and minimize confusion.

*There are <b>10</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

81:     int128 internal constant DECIMALS_128 = 10_000;

131:     uint256 immutable TICK_DEVIATION;

```
*Github:* [[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L81), [131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L131)]


```solidity
File: ./contracts/PanopticPool.sol

105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

```
*Github:* [[105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L105)]


```solidity
File: ./contracts/libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*Github:* [[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L15)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*Github:* [[23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L23)]


```solidity
File: ./contracts/types/LeftRight.sol

30:     int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```
*Github:* [[30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L30)]


```solidity
File: ./contracts/types/TokenId.sol

66:     uint256 internal constant CLEAR_POOLID_MASK =

70:     uint256 internal constant OPTION_RATIO_MASK =

74:     uint256 internal constant CHUNK_MASK =

78:     int256 internal constant BITMASK_INT24 = 0xFFFFFF;

```
*Github:* [[66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L70), [74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L74), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L78)]



<a name="NC-65"></a> 
### [NC-65] Consider using `delete` rather than assigning zero/false to clear values
The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

*There is one instance of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

332:         s_poolContext[poolId].locked = false;

```
*Github:* [[332](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L332)]



<a name="NC-66"></a> 
### [NC-66] Solidity compiler version is not fixed
To prevent the actual contracts deployed from behaving differently depending on the compiler version, it is recommended to use a fixed solidity version.

<details>
<summary>
There are <b>20</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L2)]


```solidity
File: ./contracts/PanopticFactory.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L2)]


```solidity
File: ./contracts/PanopticPool.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L2)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L2)]


```solidity
File: ./contracts/libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L2)]


```solidity
File: ./contracts/libraries/Constants.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L2)]


```solidity
File: ./contracts/libraries/Errors.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L2)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L2)]


```solidity
File: ./contracts/libraries/InteractionHelper.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L2)]


```solidity
File: ./contracts/libraries/Math.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L2)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L2)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L2)]


```solidity
File: ./contracts/multicall/Multicall.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L2)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L2)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L2)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L2)]


```solidity
File: ./contracts/tokens/interfaces/IERC20Partial.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L2)]


```solidity
File: ./contracts/types/LeftRight.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L2)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L2)]


```solidity
File: ./contracts/types/TokenId.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L2)]


</details>


<a name="NC-67"></a> 
### [NC-67] Expressions for constant values should use `immutable` rather than `constant`
While it doesn't save any gas because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.

<details>
<summary>
There are <b>49</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

70:     string internal constant TICKER_PREFIX = "po";

73:     string internal constant NAME_PREFIX = "POPT-V1";

77:     uint256 internal constant DECIMALS = 10_000;

81:     int128 internal constant DECIMALS_128 = 10_000;

```
*Github:* [[70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L73), [77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L81)]


```solidity
File: ./contracts/PanopticFactory.sol

82:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;

86:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

89:     uint16 internal constant CARDINALITY_INCREASE = 100;

```
*Github:* [[82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L82), [86](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L86), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L89)]


```solidity
File: ./contracts/PanopticPool.sol

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

```
*Github:* [[103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L109), [111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L111), [114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L114), [119](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L119), [120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L120), [123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L123), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L128), [133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L133), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L136), [139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L139), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L145), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L148), [152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L152), [156](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L156), [160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L160), [165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L165), [168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L168), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L171), [174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L174)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

125:     bool internal constant MINT = false;

126:     bool internal constant BURN = true;

133:     uint128 private constant VEGOID = 2;

```
*Github:* [[125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L125), [126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L126), [133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L133)]


```solidity
File: ./contracts/libraries/Constants.sol

9:     uint256 internal constant FP96 = 0x1000000000000000000000000;

12:     int24 internal constant MIN_V3POOL_TICK = -887272;

15:     int24 internal constant MAX_V3POOL_TICK = 887272;

18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

21:     uint160 internal constant MAX_V3POOL_SQRT_RATIO =

```
*Github:* [[9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L9), [12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L12), [15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L15), [18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L18), [21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L21)]


```solidity
File: ./contracts/libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*Github:* [[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L15)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

26:     uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

```
*Github:* [[23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L26)]


```solidity
File: ./contracts/types/LeftRight.sol

22:     uint256 internal constant LEFT_HALF_BIT_MASK =

26:     int256 internal constant LEFT_HALF_BIT_MASK_INT =

30:     int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```
*Github:* [[22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L22), [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L26), [30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L30)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

54:     uint256 internal constant CLEAR_TL_MASK =

58:     uint256 internal constant CLEAR_TU_MASK =

```
*Github:* [[54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L54), [58](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L58)]


```solidity
File: ./contracts/types/TokenId.sol

62:     uint256 internal constant LONG_MASK =

66:     uint256 internal constant CLEAR_POOLID_MASK =

70:     uint256 internal constant OPTION_RATIO_MASK =

74:     uint256 internal constant CHUNK_MASK =

78:     int256 internal constant BITMASK_INT24 = 0xFFFFFF;

```
*Github:* [[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L62), [66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L70), [74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L74), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L78)]


</details>


<a name="NC-68"></a> 
### [NC-68] Upgrade `openzeppelin` to the latest version (`5.0.2`)
These contracts import contracts from openzeppelin contracts but they are not using the latest version. For more information, please visit: [OpenZeppelin GitHub Releases](https://github.com/OpenZeppelin/openzeppelin-contracts/releases) It is recommended to always use the latest version to take advantage of updates and security fixes.

*There is one instance of this issue:*
```solidity

Global finding

```
*Github:* [[Global](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/)]



<a name="NC-69"></a> 
### [NC-69] Use the latest solidity version for deployment (`0.8.25`)
Upgrading to a newer Solidity release can optimize gas usage, take advantage of new features and improve overall contract efficiency. Where possible, based on compatibility requirements, it is recommended to use newer/latest solidity version to take advantage of the latest optimizations and features.

<details>
<summary>
There are <b>20</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L2)]


```solidity
File: ./contracts/PanopticFactory.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L2)]


```solidity
File: ./contracts/PanopticPool.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L2)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L2)]


```solidity
File: ./contracts/libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L2)]


```solidity
File: ./contracts/libraries/Constants.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L2)]


```solidity
File: ./contracts/libraries/Errors.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L2)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L2)]


```solidity
File: ./contracts/libraries/InteractionHelper.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L2)]


```solidity
File: ./contracts/libraries/Math.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L2)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L2)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L2)]


```solidity
File: ./contracts/multicall/Multicall.sol

2: pragma solidity ^0.8.18;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L2)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L2)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L2)]


```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L2)]


```solidity
File: ./contracts/tokens/interfaces/IERC20Partial.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L2)]


```solidity
File: ./contracts/types/LeftRight.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L2)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L2)]


```solidity
File: ./contracts/types/TokenId.sol

2: pragma solidity ^0.8.0;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L2)]


</details>


<a name="NC-70"></a> 
### [NC-70] Use the Modern Upgradeable Contract Paradigm
Modern smart contract development often employs upgradeable contract structures, utilizing proxy patterns like OpenZeppelin’s Upgradeable Contracts. This paradigm separates logic and state, allowing developers to amend and enhance the contract's functionality without altering its state or the deployed contract address. Transitioning to this approach enhances long-term maintainability.

Resolution: Adopt a well-established proxy pattern for upgradeability, ensuring proper initialization and employing transparent proxies to mitigate potential risks. Embrace comprehensive testing and audit practices, particularly when updating contract logic, to ensure state consistency and security are preserved across upgrades. This ensures your contract remains robust and adaptable to future requirements.

*There are <b>7</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

```
*Github:* [[36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36)]


```solidity
File: ./contracts/PanopticFactory.sol

26: contract PanopticFactory is Multicall {

```
*Github:* [[26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L26)]


```solidity
File: ./contracts/PanopticPool.sol

27: contract PanopticPool is ERC1155Holder, Multicall {

```
*Github:* [[27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L27)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

82:     /// @notice Emitted when a position is destroyed/burned

```
*Github:* [[82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L82)]


```solidity
File: ./contracts/multicall/Multicall.sol

8: abstract contract Multicall {

```
*Github:* [[8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L8)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

11: abstract contract ERC1155 {

```
*Github:* [[11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L11)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

9: abstract contract ERC20Minimal {

```
*Github:* [[9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L9)]



<a name="NC-71"></a> 
### [NC-71] Consider using modifiers for address control
Modifiers in Solidity can improve code readability and modularity by encapsulating repetitive checks, such as address validity checks, into a reusable construct. For example, an `onlyOwner` modifier can be used to replace repetitive `require(msg.sender == owner)` checks across several functions, reducing code redundancy and enhancing maintainability. To implement, define a modifier with the check, then apply the modifier to relevant functions.

*There are <b>8</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

170:         if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

541:         if (msg.sender != owner) {

599:         if (msg.sender != owner) {

```
*Github:* [[170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L170), [541](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L541), [599](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L599)]


```solidity
File: ./contracts/PanopticFactory.sol

150:         if (msg.sender != currentOwner) revert Errors.NotOwner();

220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

```
*Github:* [[150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L150), [220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L220), [224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L224)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

101:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

```
*Github:* [[101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L101), [137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L137)]



<a name="NC-72"></a> 
### [NC-72] Use of `override` is unnecessary
Starting with Solidity version [0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), using the `override` keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

546:     ) public override {

572:     ) public override {

```
*Github:* [[546](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L546), [572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L572)]



<a name="NC-73"></a> 
### [NC-73] Use scientific notation (e.g. `1e18`) rather than exponentiation (e.g. `10**18`)
While the compiler knows to optimize away the exponentiation, it's still better coding practice to use idioms that do not require compiler optimization, if they exist.

*There is one instance of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

234:         totalSupply = 10 ** 6;

```
*Github:* [[234](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L234)]



<a name="NC-74"></a> 
### [NC-74] Use a struct to encapsulate multiple function parameters
If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit 7 parameters
1479:                     // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])
                          LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(
                              _univ3pool,
                              atTick,
                              _tickLower,
                              _tickUpper,

```
*Github:* [[1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1479)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

/// @audit 8 parameters
770:         TokenId[] memory positionIdList,
             LeftRightSigned[4][] memory premiasByLeg,
             LeftRightSigned collateralRemaining,
             CollateralTracker collateral0,
             CollateralTracker collateral1,
             uint160 sqrtPriceX96Final,
             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
         ) external returns (int256, int256) {
             unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;

```
*Github:* [[770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L770)]


```solidity
File: ./contracts/types/TokenId.sol

/// @audit 9 parameters
336:     function addLeg(
             TokenId self,
             uint256 legIndex,
             uint256 _optionRatio,
             uint256 _asset,
             uint256 _isLong,
             uint256 _tokenType,
             uint256 _riskPartner,
             int24 _strike,
             int24 _width
         ) internal pure returns (TokenId tokenId) {

```
*Github:* [[336](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L336)]



<a name="NC-75"></a> 
### [NC-75] Use `type(X).max` instead of constant formulas like `2**n`
Earlier versions of solidity can use `uint<n>(-1)` instead. Expressions `2**n -1` can often be rewritten to accommodate the change (e.g. by using a `>` instead of a `>=`, which will also saves gas).

<details>
<summary>
There are <b>34</b> instances (click to show):
</summary>

```solidity
File: ./contracts/PanopticPool.sol

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

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
*Github:* [[165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L165), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1487), [1552](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1552), [1561](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1561), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1636), [1769](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1769), [1771](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1771), [1942](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1942), [1959](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1959)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

1352:                     totalLiquidity * 2 ** 64,

1357:                     totalLiquidity * 2 ** 64,

```
*Github:* [[1352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1352), [1357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1357)]


```solidity
File: ./contracts/libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

418:             inv *= 2 - denominator * inv; // inverse mod 2**8

419:             inv *= 2 - denominator * inv; // inverse mod 2**16

420:             inv *= 2 - denominator * inv; // inverse mod 2**32

421:             inv *= 2 - denominator * inv; // inverse mod 2**64

422:             inv *= 2 - denominator * inv; // inverse mod 2**128

423:             inv *= 2 - denominator * inv; // inverse mod 2**256

484:             require(2 ** 64 > prod1);

574:             prod0 |= prod1 * 2 ** 160;

624:             require(2 ** 128 > prod1);

651:             prod0 |= prod1 * 2 ** 128;

664:             if (mulmod(a, b, 2 ** 128) > 0) {

728:             prod0 |= prod1 * 2 ** 64;

```
*Github:* [[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L15), [418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L418), [419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L419), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L420), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L421), [422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L422), [423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L423), [484](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L484), [574](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L574), [624](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L624), [651](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L651), [664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L664), [728](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L728)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

560:                         2 ** 128,

685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

```
*Github:* [[23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L23), [514](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L514), [560](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L560), [685](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L685)]


```solidity
File: ./contracts/types/TokenId.sol

98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

376:             if (optionRatios < 2 ** 64) {

380:             } else if (optionRatios < 2 ** 160) {

439:         if (optionRatios < 2 ** 64) {

443:         } else if (optionRatios < 2 ** 160) {

```
*Github:* [[98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L98), [376](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L376), [380](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L380), [439](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L439), [443](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L443)]


</details>


<a name="NC-76"></a> 
### [NC-76] Visibility of state variables is not explicitly defined
To avoid misunderstandings and unexpected state accesses, it is recommended to explicitly define the visibility of each state variable.

*There are <b>8</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

131:     uint256 immutable TICK_DEVIATION;

136:     uint256 immutable COMMISSION_FEE;

141:     uint256 immutable SELLER_COLLATERAL_RATIO;

145:     uint256 immutable BUYER_COLLATERAL_RATIO;

149:     int256 immutable FORCE_EXERCISE_COST;

154:     uint256 immutable TARGET_POOL_UTIL;

158:     uint256 immutable SATURATED_POOL_UTIL;

162:     uint256 immutable ITM_SPREAD_MULTIPLIER;

```
*Github:* [[131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L131), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L136), [141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L141), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L145), [149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L149), [154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L154), [158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L158), [162](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L162)]



<a name="NC-77"></a> 
### [NC-77] Whitespace in Expressions
See the [Whitespace in Expressions](https://docs.soliditylang.org/en/latest/style-guide.html#whitespace-in-expressions) section of the Solidity Style Guide.

<details>
<summary>
There are <b>19</b> instances (click to show):
</summary>

```solidity
File: ./contracts/PanopticFactory.sol

341:         (uint160 currentSqrtPriceX96, , , , , , ) = v3Pool.slot0();

```
*Github:* [[341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L341)]


```solidity
File: ./contracts/PanopticPool.sol

304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

339:         (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();

387:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

523:         (, , uint16 observationIndex, uint16 observationCardinality, , , ) = s_univ3pool.slot0();

1032:             (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

1094:             (, finalTick, , , , , ) = s_univ3pool.slot0();

1202:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

1206:             (LeftRightSigned positionPremia, ) = _calculateAccumulatedPremia(

1598:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

```
*Github:* [[304](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L304), [339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L339), [387](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L387), [523](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L523), [1032](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1032), [1094](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1094), [1202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1202), [1206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1206), [1598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1598)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

725:         (, int24 currentTick, , , , , ) = univ3pool.slot0();

788:                 (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

1148:         (, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, , ) = univ3pool

```
*Github:* [[725](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L725), [788](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L788), [1148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1148)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

142:         (, , uint256 lowerOut0, uint256 lowerOut1, , , , ) = univ3pool.ticks(tickLower);

143:         (, , uint256 upperOut0, uint256 upperOut1, , , , ) = univ3pool.ticks(tickUpper);

```
*Github:* [[142](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L142), [143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L143)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(

186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

192:                     (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool

253:             (int56[] memory tickCumulatives, ) = univ3pool.observe(secondsAgos);

```
*Github:* [[138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L138), [186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L186), [192](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L192), [253](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L253)]


</details>


<a name="NC-78"></a> 
### [NC-78] Common functions should be refactored to a common base contract
The functions below have the same implementation as is seen in other files. The functions should be refactored into functions of a common base contract.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/tokens/interfaces/IDonorNFT.sol

/// @audit seen in ./contracts/tokens/interfaces/IERC20Partial.sol
13:     function issueNFT(

```
*Github:* [[13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L13)]


```solidity
File: ./contracts/tokens/interfaces/IERC20Partial.sol

/// @audit seen in ./contracts/tokens/interfaces/IDonorNFT.sol
16:     function balanceOf(address account) external view returns (uint256);

/// @audit seen in ./contracts/tokens/interfaces/IDonorNFT.sol
22:     function approve(address spender, uint256 amount) external;

/// @audit seen in ./contracts/tokens/interfaces/IDonorNFT.sol
27:     function transfer(address to, uint256 amount) external;

```
*Github:* [[16](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L16), [22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L22), [27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol#L27)]



<a name="NC-79"></a> 
### [NC-79] Names of `private`/`internal` functions should be prefixed with an underscore
It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

<details>
<summary>
There are <b>104</b> instances (click to show):
</summary>

```solidity
File: ./contracts/PanopticPool.sol

1450:     function getUniV3TWAP() internal view returns (int24 twapTick) {
              twapTick = PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW);

```
*Github:* [[1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1450)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

339:     /// @notice Construct the Semi-Fungible Position Manager (SFPM)
         /// @param _factory the Uniswap v3 Factory used to retrieve registered Uniswap pools

347:     /// @param token0 The contract address of token0 of the pool
         /// @param token1 The contract address of token1 of the pool

611:             bytes32 positionKey_from = keccak256(
                     abi.encodePacked(
                         address(univ3pool),

786:             // this is simply a convenience feature, and should be treated as such
                 if ((itm0 != 0) && (itm1 != 0)) {
                     (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

```
*Github:* [[339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L339), [347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L347), [611](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L611), [786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L786)]


```solidity
File: ./contracts/libraries/CallbackLib.sol

30:     function validateCallback(
            address sender,
            IUniswapV3Factory factory,
            PoolFeatures memory features
        ) internal view {

```
*Github:* [[30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L30)]


```solidity
File: ./contracts/libraries/Math.sol

25:     function min24(int24 a, int24 b) internal pure returns (int24) {
            return a < b ? a : b;

33:     function max24(int24 a, int24 b) internal pure returns (int24) {
            return a > b ? a : b;

41:     function min(uint256 a, uint256 b) internal pure returns (uint256) {
            return a < b ? a : b;

49:     function min(int256 a, int256 b) internal pure returns (int256) {
            return a < b ? a : b;

57:     function max(uint256 a, uint256 b) internal pure returns (uint256) {
            return a > b ? a : b;

65:     function max(int256 a, int256 b) internal pure returns (int256) {
            return a > b ? a : b;

73:     function abs(int256 x) internal pure returns (int256) {
            return x > 0 ? x : -x;

81:     function absUint(int256 x) internal pure returns (uint256) {
            unchecked {

91:     function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {
            unchecked {

128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {
             unchecked {

191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
             uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());

207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
             uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());

221:     function getAmountsForLiquidity(
             int24 currentTick,
             LiquidityChunk liquidityChunk
         ) internal pure returns (uint256 amount0, uint256 amount1) {
             if (currentTick <= liquidityChunk.tickLower()) {

241:     function getLiquidityForAmount0(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount0
         ) internal pure returns (LiquidityChunk) {
             uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);

271:     function getLiquidityForAmount1(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount1
         ) internal pure returns (LiquidityChunk) {
             uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);

296:     function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {
             if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {
             if ((downcastedInt = uint128(toDowncast)) != toDowncast) {

311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {
             if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {
             if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

325:     function toInt256(uint256 toCast) internal pure returns (int256) {
             if (toCast > uint256(type(int256).max)) revert Errors.CastingError();

340:     function mulDiv(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {
             unchecked {

440:     function mulDivRoundingUp(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {
             unchecked {

458:     function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {
             unchecked {

521:     function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {
             unchecked {

584:     function mulDiv96RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
             unchecked {

598:     function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {
             unchecked {

661:     function mulDiv128RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
             unchecked {

675:     function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {
             unchecked {

738:     function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
             assembly ("memory-safe") {

753:     function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {
             unchecked {

776:     function sort(int256[] memory data) internal pure returns (int256[] memory) {
             unchecked {

```
*Github:* [[25](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L33), [41](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L41), [49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L57), [65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L65), [73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L73), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L81), [91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L91), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L128), [191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L191), [207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L207), [221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L221), [241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L241), [271](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L271), [296](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L296), [302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L302), [311](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L311), [318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L318), [325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L325), [340](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L340), [440](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L440), [458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L521), [584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L584), [598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L598), [661](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L661), [675](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L675), [738](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L738), [753](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L753), [776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L776)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

47:     function getPoolId(address univ3pool) internal view returns (uint64) {
            unchecked {

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {
            unchecked {

92:     function updatePositionsHash(
            uint256 existingHash,
            TokenId tokenId,
            bool addFlag
        ) internal pure returns (uint256) {
            // add the XOR`ed hash of the single option position `tokenId` to the `existingHash`

292:         uint128 positionSize
         ) internal pure returns (LiquidityChunk) {
             // get the tick range for this leg
             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);

342:     ) internal pure returns (int24 tickLower, int24 tickUpper) {
             unchecked {
                 // The max/min ticks that can be initialized are the closest multiple of tickSpacing to the actual max/min tick abs()=887272

374:     ) internal pure returns (int24, int24) {
             return (
                 (width * tickSpacing) / 2,
                 int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

393:     ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {
             uint256 numLegs = tokenId.countLegs();
             for (uint256 leg = 0; leg < numLegs; ) {

421:         LeftRightUnsigned tokenData1,
             uint256 tokenType,
             uint160 sqrtPriceX96
         ) internal pure returns (uint256, uint256) {
             if (tokenType == 0) {
                 return (
                     tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),

447:         LeftRightUnsigned tokenData1,
             uint256 tokenType,
             int24 tick
         ) internal pure returns (uint256, uint256) {
             return
                 convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));

471:         int24 tickUpper,
             uint256 asset
         ) internal pure returns (uint128) {
             unchecked {
                 uint256 notional = asset == 0
                     ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {
             unchecked {
                 // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)

507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {
             unchecked {
                 // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)

524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
             unchecked {
                 // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)

547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
             unchecked {
                 // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)

577:         uint256 legIndex
         ) internal pure returns (LeftRightUnsigned) {
             // get the tick range for this leg in order to get the strike price (the underlying price)

```
*Github:* [[47](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L47), [59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L59), [92](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L92), [292](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L292), [342](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L342), [374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L374), [393](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L393), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L421), [447](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L447), [471](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L471), [490](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L490), [507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L507), [524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L524), [547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L547), [577](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L577)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:     function safeTransfer(address token, address to, uint256 amount) internal {

```
*Github:* [[21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L21), [52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L52)]


```solidity
File: ./contracts/types/LeftRight.sol

39:     function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46:     function rightSlot(LeftRightSigned self) internal pure returns (int128) {

59:     function toRightSlot(
            LeftRightUnsigned self,
            uint128 right
        ) internal pure returns (LeftRightUnsigned) {

78:     function toRightSlot(
            LeftRightSigned self,
            int128 right
        ) internal pure returns (LeftRightSigned) {

101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

121:     function toLeftSlot(
             LeftRightUnsigned self,
             uint128 left
         ) internal pure returns (LeftRightUnsigned) {

134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

148:     function add(
             LeftRightUnsigned x,
             LeftRightUnsigned y
         ) internal pure returns (LeftRightUnsigned z) {

171:     function sub(
             LeftRightUnsigned x,
             LeftRightUnsigned y
         ) internal pure returns (LeftRightUnsigned z) {

194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

214:     function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

251:     function subRect(
             LeftRightSigned x,
             LeftRightSigned y
         ) internal pure returns (LeftRightSigned z) {

279:     function addCapped(
             LeftRightUnsigned x,
             LeftRightUnsigned dx,
             LeftRightUnsigned y,
             LeftRightUnsigned dy
         ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {

```
*Github:* [[39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L39), [46](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L46), [59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L59), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L78), [101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L101), [108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L108), [121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L121), [134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L134), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L148), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L171), [194](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L194), [214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L232), [251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L251), [279](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L279)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

75:         unchecked {
                return
                    LiquidityChunk.wrap(
                        (uint256(uint24(_tickLower)) << 232) +
                            (uint256(uint24(_tickUpper)) << 208) +

94:             return LiquidityChunk.wrap(LiquidityChunk.unwrap(self) + amount);
            }
        }
    
        /// @notice Add the lower tick to `self`.

107:             return
                     LiquidityChunk.wrap(
                         LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

123:             // convert tick upper to uint24 as explicit conversion from int24 to uint256 is not allowed
                 return
                     LiquidityChunk.wrap(

139:         unchecked {
                 return
                     LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TL_MASK).addTickLower(
                         _tickLower

155:         unchecked {
                 // convert tick upper to uint24 as explicit conversion from int24 to uint256 is not allowed
                 return
                     LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TU_MASK).addTickUpper(

173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));
             }
         }
     
         /// @notice Get the upper tick of `self`.

182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));
             }
         }
     
         /// @notice Get the amount of liquidity/size of `self`.

191:             return uint128(LiquidityChunk.unwrap(self));
             }
         }
     }
     

```
*Github:* [[75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L75), [94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L94), [107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L107), [123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L123), [139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L139), [155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L155), [173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L173), [182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L182), [191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L191)]


```solidity
File: ./contracts/types/TokenId.sol

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
             TokenId self,
             uint256 _asset,
             uint256 legIndex
         ) internal pure returns (TokenId) {

221:     function addOptionRatio(
             TokenId self,
             uint256 _optionRatio,
             uint256 legIndex
         ) internal pure returns (TokenId) {

240:     function addIsLong(
             TokenId self,
             uint256 _isLong,
             uint256 legIndex
         ) internal pure returns (TokenId) {

255:     function addTokenType(
             TokenId self,
             uint256 _tokenType,
             uint256 legIndex
         ) internal pure returns (TokenId) {

273:     function addRiskPartner(
             TokenId self,
             uint256 _riskPartner,
             uint256 legIndex
         ) internal pure returns (TokenId) {

291:     function addStrike(
             TokenId self,
             int24 _strike,
             uint256 legIndex
         ) internal pure returns (TokenId) {

310:     function addWidth(
             TokenId self,
             int24 _width,
             uint256 legIndex
         ) internal pure returns (TokenId) {

336:     function addLeg(
             TokenId self,
             uint256 legIndex,
             uint256 _optionRatio,
             uint256 _asset,
             uint256 _isLong,
             uint256 _tokenType,
             uint256 _riskPartner,
             int24 _strike,
             int24 _width
         ) internal pure returns (TokenId tokenId) {

366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

404:     function countLongs(TokenId self) internal pure returns (uint256) {

416:     function asTicks(
             TokenId self,
             uint256 legIndex
         ) internal pure returns (int24 legLowerTick, int24 legUpperTick) {

432:     function countLegs(TokenId self) internal pure returns (uint256) {

464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

500:     function validate(TokenId self) internal pure {

578:     function validateIsExercisable(TokenId self, int24 currentTick) internal pure {

```
*Github:* [[87](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L87), [96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L96), [108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L108), [118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L118), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L128), [138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L138), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L148), [158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L158), [169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L169), [183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L183), [193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L193), [205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L205), [221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L221), [240](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L240), [255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L255), [273](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L273), [291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L291), [310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L310), [336](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L336), [366](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L366), [404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L404), [416](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L416), [432](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L432), [464](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L464), [500](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L500), [578](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L578)]


</details>


<a name="NC-80"></a> 
### [NC-80] Names of `private`/`internal` state variables should be prefixed with an underscore
It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

<details>
<summary>
There are <b>93</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

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
*Github:* [[70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L73), [77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L81), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L89), [93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L93), [96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L109), [112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L112), [115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L115), [121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L121), [124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L124), [131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L131), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L136), [141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L141), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L145), [149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L149), [154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L154), [158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L158), [162](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L162)]


```solidity
File: ./contracts/PanopticFactory.sol

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
*Github:* [[63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L66), [69](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L69), [72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L72), [75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L75), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L78), [82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L82), [86](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L86), [89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L89), [96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L102)]


```solidity
File: ./contracts/PanopticPool.sol

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
*Github:* [[103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L109), [111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L111), [114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L114), [119](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L119), [120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L120), [123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L123), [128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L128), [133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L133), [136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L136), [139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L139), [145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L145), [148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L148), [152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L152), [156](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L156), [160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L160), [165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L165), [168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L168), [171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L171), [174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L174), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L179), [186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L186), [225](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L225), [231](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L231), [233](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L233), [238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L238), [245](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L245), [251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L251), [258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L258), [272](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L272)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

133:     uint128 private constant VEGOID = 2;

135:     /// @dev Uniswap V3 Factory address. Initialized in the constructor.

144:     /// @dev pool address => pool id + 2 ** 255 (initialization bit for `poolId == 0`, set if the pool exists)

147:     /// @dev also contains a boolean which is used for the reentrancy lock - saves gas since this slot is often warmed

155:              net amount    

163:           │  │    │         │    │         │    │     

190:         Let`s say Charlie the smart contract deposited T into the AMM and later removed R from that

295:     mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;

297:     /*//////////////////////////////////////////////////////////////

310:         // execute function

```
*Github:* [[133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L133), [135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L135), [144](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L144), [147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L147), [155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L155), [163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L163), [190](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L190), [295](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L295), [297](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L297), [310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L310)]


```solidity
File: ./contracts/libraries/Constants.sol

9:     uint256 internal constant FP96 = 0x1000000000000000000000000;

12:     int24 internal constant MIN_V3POOL_TICK = -887272;

15:     int24 internal constant MAX_V3POOL_TICK = 887272;

18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

21:     uint160 internal constant MAX_V3POOL_SQRT_RATIO =

```
*Github:* [[9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L9), [12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L12), [15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L15), [18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L18), [21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L21)]


```solidity
File: ./contracts/libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*Github:* [[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L15)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

26:     uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

```
*Github:* [[23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L26)]


```solidity
File: ./contracts/types/LeftRight.sol

22:     uint256 internal constant LEFT_HALF_BIT_MASK =

26:     int256 internal constant LEFT_HALF_BIT_MASK_INT =

30:     int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```
*Github:* [[22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L22), [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L26), [30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L30)]


```solidity
File: ./contracts/types/LiquidityChunk.sol

57:     /// @notice AND mask to strip the `tickUpper` value from a packed LiquidityChunk

61:     /*//////////////////////////////////////////////////////////////

```
*Github:* [[57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L57), [61](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L61)]


```solidity
File: ./contracts/types/TokenId.sol

62:     uint256 internal constant LONG_MASK =

66:     uint256 internal constant CLEAR_POOLID_MASK =

70:     uint256 internal constant OPTION_RATIO_MASK =

74:     uint256 internal constant CHUNK_MASK =

78:     int256 internal constant BITMASK_INT24 = 0xFFFFFF;

```
*Github:* [[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L62), [66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L70), [74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L74), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L78)]


</details>


<a name="NC-81"></a> 
### [NC-81] Internal function calls within for loops
Making function calls or external calls within loops in Solidity can lead to inefficient gas usage, potential bottlenecks, and increased vulnerability to attacks. Each function call or external call consumes gas, and when executed within a loop, the gas cost multiplies, potentially causing the transaction to run out of gas or exceed block gas limits. This can result in transaction failure or unpredictable behavior.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `_getRequiredCollateralAtTickSinglePosition`
/// @audit `_getRequiredCollateralSingleLeg`
1259:                 tokenRequired += _getRequiredCollateralSingleLeg(

```
*Github:* [[1259](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1259)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `_getPremia`
/// @audit `_getAvailablePremium`
/// @audit `_getTotalLiquidity`
/// @audit `_getAvailablePremium`
/// @audit `_getTotalLiquidity`
/// @audit `_checkLiquiditySpread`
/// @audit `_burnOptions`
/// @audit `_checkLiquiditySpread`
/// @audit `_getTotalLiquidity`
/// @audit `_getTotalLiquidity`
/// @audit `_getAvailablePremium`
1852:         for (uint256 leg = 0; leg < numLegs; ) {

```
*Github:* [[1852](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1852)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `registerTokenTransfer`
/// @audit `_createLegInAMM`
908:                 );

```
*Github:* [[908](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L908)]



<a name="NC-82"></a> 
### [NC-82]  `require()` / `revert()` statements should have descriptive reason strings

<details>
<summary>
There are <b>74</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

170:         if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

229:         if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();

331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

```
*Github:* [[170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L170), [229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L229), [331](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L331), [350](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L350), [418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L418), [480](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L480), [536](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L536), [596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L596)]


```solidity
File: ./contracts/PanopticFactory.sol

150:         if (msg.sender != currentOwner) revert Errors.NotOwner();

220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

230:             revert Errors.PoolAlreadyInitialized();

```
*Github:* [[150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L150), [220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L220), [224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L224), [227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L227), [230](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L230)]


```solidity
File: ./contracts/PanopticPool.sol

299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

342:             revert Errors.PriceBoundFail();

634:             revert Errors.InvalidTokenIdParameter(0);

639:             revert Errors.PositionAlreadyMinted();

940:         if (!solventAtFast) revert Errors.NotEnoughCollateral();

945:                 revert Errors.NotEnoughCollateral();

1036:                 revert Errors.StaleTWAP();

1066:             if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();

1163:         ) revert Errors.NotEnoughCollateral();

1188:         if (touchedId.length != 1) revert Errors.InputListFail();

1394:         if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();

1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

1493:             revert Errors.EffectiveLiquidityAboveThreshold();

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

```
*Github:* [[299](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L299), [342](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L342), [634](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L634), [639](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L639), [940](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L940), [945](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L945), [1036](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1036), [1066](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1066), [1163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1163), [1188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1188), [1394](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1394), [1415](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1415), [1493](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1493), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1596)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

341:     constructor(IUniswapV3Factory _factory) {

369:         // There are 281,474,976,710,655 possible pool patterns.

566:     function safeBatchTransferFrom(

593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

650:                 ++leg;

659:     /// @notice Helper that checks the proposed option position and size and forwards the minting and potential swapping tasks.

717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

731:     /// @notice When a position is minted or burnt in-the-money (ITM) we are *not* 100% token0 or 100% token1: we have a mix of both tokens.

752:     ///   It that position is burnt, then we remove a mix of the two tokens and swap one of them so that the user receives only one.

964:     )

1047:             /** if the position is NOT long (selling a put or a call), then _mintLiquidity to move liquidity

```
*Github:* [[341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L341), [369](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L369), [566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L566), [593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L593), [650](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L650), [659](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L659), [717](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L717), [731](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L731), [752](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L752), [964](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L964), [1047](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1047)]


```solidity
File: ./contracts/libraries/CallbackLib.sol

37:             revert Errors.InvalidUniswapCallback();

```
*Github:* [[37](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L37)]


```solidity
File: ./contracts/libraries/Math.sol

131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

297:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

326:         if (toCast > uint256(type(int256).max)) revert Errors.CastingError();

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
*Github:* [[131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L131), [297](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L297), [312](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L312), [319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L319), [326](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L326), [361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L370), [448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L448), [484](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L484), [547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L547), [588](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L588), [624](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L624), [665](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L665), [701](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L701)]


```solidity
File: ./contracts/libraries/PanopticMath.sol

365:     /// @notice Returns the distances of the upper and lower ticks from the strike for a position with the given width and tickSpacing.

483:     }

```
*Github:* [[365](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L365), [483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L483)]


```solidity
File: ./contracts/libraries/SafeTransferLib.sol

45:         if (!success) revert Errors.TransferFailed();

75:         if (!success) revert Errors.TransferFailed();

```
*Github:* [[45](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L45), [75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L75)]


```solidity
File: ./contracts/types/LeftRight.sol

163:             ) revert Errors.UnderOverFlow();

186:             ) revert Errors.UnderOverFlow();

199:             if (left128 != left) revert Errors.UnderOverFlow();

204:             if (right128 != right) revert Errors.UnderOverFlow();

222:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

240:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

262:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

```
*Github:* [[163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L163), [186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L186), [199](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L199), [204](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L204), [222](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L222), [240](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L240), [262](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L262)]


```solidity
File: ./contracts/types/TokenId.sol

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

513:                         revert Errors.InvalidTokenIdParameter(1);

522:                         revert Errors.InvalidTokenIdParameter(6);

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

533:                 ) revert Errors.InvalidTokenIdParameter(4);

542:                         revert Errors.InvalidTokenIdParameter(3);

548:                     ) revert Errors.InvalidTokenIdParameter(3);

561:                         revert Errors.InvalidTokenIdParameter(4);

567:                         revert Errors.InvalidTokenIdParameter(5);

598:         revert Errors.NoLegsExercisable();

```
*Github:* [[501](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L501), [513](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L513), [522](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L522), [528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L528), [533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L533), [542](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L542), [548](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L548), [561](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L561), [567](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L567), [598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L598)]


</details>


<a name="NC-83"></a> 
### [NC-83] Variables should be named in mixedCase style
As the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#naming-styles) suggests: `arguments`, `local variables` and `mutable state variables` should be named in mixedCase style.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `min_sell_ratio`
773:         uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;

```
*Github:* [[773](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L773)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `UniswapV3Pool`
1570: 

```
*Github:* [[1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1570)]



<a name="NC-84"></a> 
### [NC-84] Event is missing `indexed` fields
Index event fields make the field more quickly accessible to off-chain tools that parse events. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

<details>
<summary>
There are <b>12</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

49:     event Deposit(address indexed sender, address indexed owner, uint256 assets, uint256 shares);

```
*Github:* [[49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L49)]


```solidity
File: ./contracts/PanopticFactory.sol

43:     event PoolDeployed(

```
*Github:* [[43](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L43)]


```solidity
File: ./contracts/PanopticPool.sol

38:     event AccountLiquidated(

62:     event PremiumSettled(

75:     event OptionBurnt(

90:     event OptionMinted(

```
*Github:* [[38](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L38), [62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L62), [75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L75), [90](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L90)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

90:         uint128 positionSize

98:     event TokenizedPositionMinted(

114:     // false = unlocked, true = locked

```
*Github:* [[90](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L90), [98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L98), [114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L114)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

48:     event ApprovalForAll(address indexed owner, address indexed operator, bool approved);

```
*Github:* [[48](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L48)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

18:     event Transfer(address indexed from, address indexed to, uint256 amount);

24:     event Approval(address indexed owner, address indexed spender, uint256 amount);

```
*Github:* [[18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L18), [24](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L24)]


</details>


<a name="NC-85"></a> 
### [NC-85] Functions not used internally could be marked `external`

<details>
<summary>
There are <b>13</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

323:     function transfer(

341:     function transferFrom(

1147:         tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);

```
*Github:* [[323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L341), [1147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1147)]


```solidity
File: ./contracts/PanopticFactory.sol

134:     function initialize(address _owner) public {

```
*Github:* [[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L134)]


```solidity
File: ./contracts/PanopticPool.sol

1444:     function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

```
*Github:* [[1444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1444)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

555:         super.safeTransferFrom(from, to, id, amount, data);

583:         // transfer the token (note that all state updates are completed before reentrancy is possible)

```
*Github:* [[555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L555), [583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L583)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

104:         // extract the amount of AMM fees collected within the liquidity chunk`

```
*Github:* [[104](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L104)]


```solidity
File: ./contracts/multicall/Multicall.sol

12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {

```
*Github:* [[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L12)]


```solidity
File: ./contracts/tokens/ERC1155Minimal.sol

81:     function setApprovalForAll(address operator, bool approved) public {

178:     function balanceOfBatch(

200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

```
*Github:* [[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L81), [178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L178), [200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L200)]


```solidity
File: ./contracts/tokens/ERC20Minimal.sol

49:     function approve(address spender, uint256 amount) public returns (bool) {

```
*Github:* [[49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L49)]


</details>


<a name="NC-86"></a> 
### [NC-86] Default address(0) can be returned
Allowing a function in Solidity to return the default address (address(0)) can be problematic as it can represent uninitialized or invalid addresses. If such an address is utilized in transfer operations or other sensitive actions, it could lead to loss of funds or unpredicted behavior. It's prudent to include checks in your functions to prevent the return of the zero address, enhancing contract security.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `address assetTokenAddress`
361:     function asset() external view returns (address assetTokenAddress) {
             return s_underlyingToken;

```
*Github:* [[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L361)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `address `
159:     function owner() external view returns (address) {

```
*Github:* [[159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L159)]



<a name="NC-87"></a> 
### [NC-87] Consider moving duplicated strings to constants

*There are <b>5</b> instances of this issue:*
```solidity
File: ./contracts/libraries/InteractionHelper.sol

63:             symbol0 = "???";

68:             symbol1 = "???";

74:                     " ",

80:                     " ",

100:             return string.concat(prefix, "???");

```
*Github:* [[63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L63), [68](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L68), [74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L74), [80](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L80), [100](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L100)]



<a name="NC-88"></a> 
### [NC-88] Don't only depend on Solidity's arithmetic ordering
Relying on Solidity's default arithmetic operator precedence can lead to misunderstood or overlooked nuances in code execution. Misinterpretation risks can be significant, especially when different developers or auditors review the code. To ensure clarity and minimize potential errors, it's recommended to use parentheses. These not only override the default precedence when needed but also emphasize the intended order of operations. By deliberately showing the intended calculation sequence using parentheses, developers make the code's logic explicit, reducing the risk of unintended behaviors and making the codebase more maintainable and understandable for all stakeholders.

<details>
<summary>
There are <b>24</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

764:                    100% - |                _------

767:                     20% - |---------¯

827:            10% - |----------__       min_ratio = 5%

828:            5%  - | . . . . .  ¯¯¯--______

1386:                            100% + SCR% - |--__           .    .    .

1387:                                   100% - | . .¯¯--__     .    .    .

1389:                                    SCR - |    .          .¯¯--__________

1620:                   100% - |--__                .

1623:                  SCR/2 - |                ¯¯--______ <------ base collateral is half that of a single-leg

```
*Github:* [[764](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L764), [767](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L767), [827](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L827), [828](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L828), [1386](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1386), [1387](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1387), [1389](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1389), [1620](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1620), [1623](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1623)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

222:                                       = feeGrowthX128 * T + feesGrowthX128*ν*R^2/N         

899:                     _leg = _isBurn ? numLegs - leg - 1 : leg;

1352:                     totalLiquidity * 2 ** 64,

1357:                     totalLiquidity * 2 ** 64,

```
*Github:* [[222](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L222), [899](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L899), [1352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1352), [1357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1357)]


```solidity
File: ./contracts/libraries/FeesCalc.sol

166:                 feeGrowthInside0X128 = lowerOut0 - upperOut0; // fee growth inside the chunk

```
*Github:* [[166](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L166)]


```solidity
File: ./contracts/libraries/Math.sol

418:             inv *= 2 - denominator * inv; // inverse mod 2**8

419:             inv *= 2 - denominator * inv; // inverse mod 2**16

420:             inv *= 2 - denominator * inv; // inverse mod 2**32

421:             inv *= 2 - denominator * inv; // inverse mod 2**64

422:             inv *= 2 - denominator * inv; // inverse mod 2**128

423:             inv *= 2 - denominator * inv; // inverse mod 2**256

511:             prod0 |= prod1 * 2 ** 192;

574:             prod0 |= prod1 * 2 ** 160;

651:             prod0 |= prod1 * 2 ** 128;

728:             prod0 |= prod1 * 2 ** 64;

```
*Github:* [[418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L418), [419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L419), [420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L420), [421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L421), [422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L422), [423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L423), [511](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L511), [574](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L574), [651](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L651), [728](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L728)]


</details>


<a name="NC-89"></a> 
### [NC-89] Payable functions which do not interact with the native token should not be payable
In Ethereum, a function marked `payable` can accept Ether. If a function is intended to work with Ether but isn't marked payable, it will reject any Ether sent to it, leading to failed transactions. Conversely, if a function doesn't involve Ether transactions but is mistakenly marked payable, it can inadvertently accept Ether, potentially locking it in the contract. Thus, functions that should handle Ether transfers must be correctly marked payable, and those that shouldn't must be non-payable. Proper function designation ensures the intended flow of Ether and guards against unintended Ether reception or loss.

*There is one instance of this issue:*
```solidity
File: ./contracts/multicall/Multicall.sol

12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {

```
*Github:* [[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L12)]



<a name="NC-90"></a> 
### [NC-90] Use `using` keyword when using specific imports rather than calling the specific import directly
In Solidity, the `using` keyword can streamline the use of library functions for specific types. Instead of calling library functions directly with their full import paths, you can declare a library once with `using` for a specific type. This approach makes your code more readable and concise. For example, instead of `LibraryName.functionName(variable)`, you would first declare `using LibraryName for TypeName;` at the contract level. After this, you can call library functions directly on variables of `TypeName` like `variable.functionName()`. This method not only enhances code clarity but also promotes cleaner and more organized code, especially when multiple functions from the same library are used frequently.

<details>
<summary>
There are <b>171</b> instances (click to show):
</summary>

```solidity
File: ./contracts/CollateralTracker.sol

/// @audit `Errors`
170:         if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

/// @audit `Errors`
229:         if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();

/// @audit `InteractionHelper`
292:             InteractionHelper.computeName(

/// @audit `InteractionHelper`
305:         return InteractionHelper.computeSymbol(s_underlyingToken, TICKER_PREFIX);

/// @audit `InteractionHelper`
312:         return InteractionHelper.computeDecimals(s_underlyingToken);

/// @audit `Errors`
331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

/// @audit `Errors`
350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

/// @audit `Math`
380:         return Math.mulDiv(assets, totalSupply, totalAssets());

/// @audit `Math`
387:         return Math.mulDiv(shares, totalAssets(), totalSupply);

/// @audit `Math`
402:             shares = Math.mulDiv(

/// @audit `Errors`
418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

/// @audit `SafeTransferLib`
424:         SafeTransferLib.safeTransferFrom(

/// @audit `Math`
462:             assets = Math.mulDivRoundingUp(

/// @audit `Errors`
480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

/// @audit `SafeTransferLib`
484:         SafeTransferLib.safeTransferFrom(

/// @audit `Math`
512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

/// @audit `Math`
521:         return Math.mulDivRoundingUp(assets, supply, totalAssets());

/// @audit `Errors`
536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

/// @audit `SafeTransferLib`
556:         SafeTransferLib.safeTransferFrom(

/// @audit `Math`
575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

/// @audit `Errors`
596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

/// @audit `SafeTransferLib`
616:         SafeTransferLib.safeTransferFrom(

/// @audit `Math`
669:                             Math.unsafeDivRoundingUp(

/// @audit `Math`
675:                     maxNumRangesFromStrike = Math.max(

/// @audit `Math`
677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

/// @audit `PanopticMath`
687:                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

/// @audit `Math`
693:                     (currentValue0, currentValue1) = Math.getAmountsForLiquidity(

/// @audit `Math`
698:                     (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(

/// @audit `Math`
964:         else {

/// @audit `Math`
969:     /// @notice Refunds delegated tokens to 'refunder' from 'refundee', similar to 'revoke'

/// @audit `Math`
1020:                 uint256 sharesToMint = convertToShares(uint256(-tokenToPay));

/// @audit `Math`
1077:                 uint256 sharesToMint = convertToShares(uint256(-tokenToPay));

/// @audit `Math`
1116:             }

/// @audit `Math`
1118:             //compute total commission amount = commission rate + spread fee

/// @audit `Math`
1130:     //////////////////////////////////////////////////////////////*/

/// @audit `PanopticMath`
1328:         int64 utilization = tokenType == 0

/// @audit `Math`
1368:                         ); // calls -> strike/price

/// @audit `Constants`
1370:                     // compute the collateral requirement depending on whether the position is ITM & out-of-range or ITM and in-range:

/// @audit `Math`
1370:                     // compute the collateral requirement depending on whether the position is ITM & out-of-range or ITM and in-range:

/// @audit `Math`
1372:                     /// ITM and out-of-range

/// @audit `Constants`
1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

/// @audit `Math`
1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

/// @audit `Constants`
1403:                         // position is in-range (ie. current tick is between upper+lower tick): we draw a line between the

/// @audit `Math`
1405:                         // the collateral requirement when in-range, which always over-estimates the amount of token required

/// @audit `Math`
1414:                             scaleFactor + Constants.FP96

/// @audit `Math`
1416:                         // position is in-the-money, collateral requirement = amountMoved*(1-SRC)*(scaleFactor-ratio)/(scaleFactor+1) + SCR*amountMoved

/// @audit `Constants`
1424:     /// @notice Calculate the required amount of collateral for leg 'index' for position 'tokenId' accounting for its partner leg.

/// @audit `Math`
1491:             uint256 buyCollateral = _buyCollateralRatio(uint256(utilization));

/// @audit `Math`
1503:     /// @dev may be higher than the requirement of non risk-partnered legs if the spread is very wide (risky)

/// @audit `PanopticMath`
1527:         // amount moved is right slot if tokenType=0, left slot otherwise

/// @audit `PanopticMath`
1531:         // amounts moved for partner

/// @audit `Math`
1577:         // narrower spreads will be very capital efficient (1/3 of non-partnered CR!), but

/// @audit `Math`
1578:         // wider spreads (an uncommon position w/ high max loss) may not benefit from risk partnering

/// @audit `Math`
1588:         );

```
*Github:* [[170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L170), [229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L229), [292](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L292), [305](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L305), [312](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L312), [331](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L331), [350](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L350), [380](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L380), [387](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L387), [402](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L402), [418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L418), [424](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L424), [462](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L462), [480](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L480), [484](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L484), [512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L512), [521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L521), [536](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L536), [556](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L556), [575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L575), [596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L596), [616](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L616), [669](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L669), [675](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L675), [677](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L677), [687](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L687), [693](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L693), [698](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L698), [964](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L964), [969](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L969), [1020](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1020), [1077](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1077), [1116](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1116), [1118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1118), [1130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1130), [1328](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1328), [1368](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1368), [1370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1370), [1370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1370), [1372](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1372), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1374), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1374), [1403](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1403), [1405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1405), [1414](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1414), [1416](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1416), [1424](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1424), [1491](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1491), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1503), [1527](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1527), [1531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1531), [1577](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1577), [1578](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1578), [1588](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1588)]


```solidity
File: ./contracts/PanopticFactory.sol

/// @audit `Errors`
150:         if (msg.sender != currentOwner) revert Errors.NotOwner();

/// @audit `CallbackLib`
177:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

/// @audit `CallbackLib`
179:         CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);

/// @audit `SafeTransferLib`
182:             SafeTransferLib.safeTransferFrom(

/// @audit `SafeTransferLib`
189:             SafeTransferLib.safeTransferFrom(

/// @audit `Errors`
220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

/// @audit `Errors`
224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

/// @audit `Errors`
227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

/// @audit `Errors`
230:             revert Errors.PoolAlreadyInitialized();

/// @audit `PanopticMath`
304:             uint256 rarity = PanopticMath.numberOfLeadingHexZeros(

/// @audit `Math`
353:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)

/// @audit `Math`
357:                     Math.mulDivRoundingUp(

/// @audit `Constants`
359:                         Constants.FP96,

/// @audit `Math`
366:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)

/// @audit `Math`
369:                     Math.mulDivRoundingUp(

/// @audit `Constants`
371:                         Constants.FP96,

/// @audit `Constants`
392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

/// @audit `CallbackLib`
397:             CallbackLib.CallbackData({

/// @audit `CallbackLib`
398:                 poolFeatures: CallbackLib.PoolFeatures({token0: token0, token1: token1, fee: fee}),

```
*Github:* [[150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L150), [177](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L177), [179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L179), [182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L182), [189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L189), [220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L220), [224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L224), [227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L227), [230](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L230), [304](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L304), [353](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L353), [357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L357), [359](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L359), [366](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L366), [369](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L369), [371](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L371), [392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L392), [397](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L397), [398](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L398)]


```solidity
File: ./contracts/PanopticPool.sol

/// @audit `Constants`
103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

/// @audit `Constants`
105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

/// @audit `Errors`
299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

/// @audit `InteractionHelper`
326:         InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);

/// @audit `Errors`
342:             revert Errors.PriceBoundFail();

/// @audit `FeesCalc`
415:         (value0, value1) = FeesCalc.getPortfolioValue(

/// @audit `PanopticMath`
525:         (, uint256 medianData) = PanopticMath.computeInternalMedian(

/// @audit `Errors`
634:             revert Errors.InvalidTokenIdParameter(0);

/// @audit `Errors`
639:             revert Errors.PositionAlreadyMinted();

/// @audit `PanopticMath`
712:         (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath

/// @audit `Math`
775:                     uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))

/// @audit `PanopticMath`
905:         int24 fastOracleTick = PanopticMath.computeMedianObservedPrice(

/// @audit `PanopticMath`
915:             slowOracleTick = PanopticMath.computeMedianObservedPrice(

/// @audit `PanopticMath`
923:             (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(

/// @audit `Errors`
940:         if (!solventAtFast) revert Errors.NotEnoughCollateral();

/// @audit `Math`
943:         if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

/// @audit `Errors`
945:                 revert Errors.NotEnoughCollateral();

/// @audit `PanopticMath`
981:         (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath

/// @audit `Math`
1035:             if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

/// @audit `Errors`
1036:                 revert Errors.StaleTWAP();

/// @audit `Math`
1063:                 Math.getSqrtRatioAtTick(twapTick)

/// @audit `Errors`
1066:             if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();

/// @audit `Constants`
1088:                 Constants.MIN_V3POOL_TICK,

/// @audit `Constants`
1089:                 Constants.MAX_V3POOL_TICK,

/// @audit `PanopticMath`
1098:             (liquidationBonus0, liquidationBonus1, collateralRemaining) = PanopticMath

/// @audit `Math`
1102:                     Math.getSqrtRatioAtTick(twapTick),

/// @audit `Math`
1103:                     Math.getSqrtRatioAtTick(finalTick),

/// @audit `PanopticMath`
1122:             (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(

/// @audit `Math`
1129:                 Math.getSqrtRatioAtTick(_finalTick),

/// @audit `Errors`
1163:         ) revert Errors.NotEnoughCollateral();

/// @audit `Errors`
1188:         if (touchedId.length != 1) revert Errors.InputListFail();

/// @audit `PanopticMath`
1197:         (LeftRightSigned longAmounts, LeftRightSigned delegatedAmounts) = PanopticMath

/// @audit `PanopticMath`
1242:         refundAmounts = PanopticMath.getRefundAmounts(

/// @audit `Math`
1324:             Math.getSqrtRatioAtTick(atTick)

/// @audit `Math`
1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

/// @audit `Math`
1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

/// @audit `Math`
1349:                 Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);

/// @audit `Math`
1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

/// @audit `Math`
1354:                 Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);

/// @audit `PanopticMath`
1383:             fingerprintIncomingList = PanopticMath.updatePositionsHash(

/// @audit `Errors`
1394:         if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();

/// @audit `PanopticMath`
1410:         uint256 newHash = PanopticMath.updatePositionsHash(

/// @audit `Errors`
1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

/// @audit `PanopticMath`
1451:         twapTick = PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW);

/// @audit `Errors`
1493:             revert Errors.EffectiveLiquidityAboveThreshold();

/// @audit `PanopticMath`
1521:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

/// @audit `Errors`
1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

/// @audit `PanopticMath`
1627:         uint256 liquidity = PanopticMath

/// @audit `PanopticMath`
1680:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

/// @audit `Math`
1778:                             Math.min(

/// @audit `Math`
1787:                             Math.min(

/// @audit `PanopticMath`
1877:                     uint256 positionLiquidity = PanopticMath

/// @audit `Math`
1934:                                             Math.max(

/// @audit `Math`
1951:                                             Math.max(

```
*Github:* [[103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L105), [299](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L299), [326](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L326), [342](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L342), [415](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L415), [525](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L525), [634](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L634), [639](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L639), [712](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L712), [775](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L775), [905](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L905), [915](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L915), [923](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L923), [940](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L940), [943](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L943), [945](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L945), [981](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L981), [1035](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1035), [1036](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1036), [1063](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1063), [1066](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1066), [1088](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1088), [1089](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1089), [1098](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1098), [1102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1102), [1103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1103), [1122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1122), [1129](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1129), [1163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1163), [1188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1188), [1197](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1197), [1242](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1242), [1324](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1324), [1329](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1329), [1348](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1348), [1349](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1349), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1353), [1354](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1354), [1383](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1383), [1394](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1394), [1410](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1410), [1415](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1415), [1451](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1451), [1493](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1493), [1521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1521), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1596), [1627](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1627), [1680](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1680), [1778](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1778), [1787](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1787), [1877](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1877), [1934](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1934), [1951](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1951)]


```solidity
File: ./contracts/SemiFungiblePositionManager.sol

/// @audit `Errors`
341:     constructor(IUniswapV3Factory _factory) {

/// @audit `Errors`
369:         // There are 281,474,976,710,655 possible pool patterns.

/// @audit `PanopticMath`
380:             pool: IUniswapV3Pool(univ3pool),

/// @audit `PanopticMath`
388:             s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;

/// @audit `CallbackLib`
429:     /// @dev Pays the pool tokens owed for the swap from the payer (always the caller)

/// @audit `CallbackLib`
430:     /// @param amount0Delta The amount of token0 that was sent (negative) or must be received (positive) by the pool by

/// @audit `SafeTransferLib`
431:     /// the end of the swap. If positive, the callback must send that amount of token0 to the pool.

/// @audit `SafeTransferLib`
433:     /// the end of the swap. If positive, the callback must send that amount of token1 to the pool.

/// @audit `CallbackLib`
455:         // Pay the required token from the payer to the caller of this contract

/// @audit `CallbackLib`
456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

/// @audit `SafeTransferLib`
468:     /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)

/// @audit `Errors`
567:         address from,

/// @audit `Errors`
593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

/// @audit `PanopticMath`
627:                 )

/// @audit `Errors`
650:                 ++leg;

/// @audit `Errors`
659:     /// @notice Helper that checks the proposed option position and size and forwards the minting and potential swapping tasks.

/// @audit `Errors`
717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

/// @audit `Errors`
731:     /// @notice When a position is minted or burnt in-the-money (ITM) we are *not* 100% token0 or 100% token1: we have a mix of both tokens.

/// @audit `Errors`
752:     ///   It that position is burnt, then we remove a mix of the two tokens and swap one of them so that the user receives only one.

/// @audit `CallbackLib`
793:                 // we do this by flipping the signs on the token1 ITM amount converting+deducting it against the token0 ITM amount

/// @audit `CallbackLib`
794:                 // couple examples (price = 2 1/0):

/// @audit `PanopticMath`
854:     /// @notice Create the position in the AMM given in the tokenId.

/// @audit `Constants`
872:             LeftRightUnsigned[4] memory collectedByLeg,

/// @audit `Constants`
874:         )

/// @audit `PanopticMath`
939:         if (amount0 > uint128(type(int128).max) || amount1 > uint128(type(int128).max))

/// @audit `Math`
949:     /// but we need to pass in a flag to indicate that so the removedLiquidity is updated.

/// @audit `Math`
951:     /// @param tokenId the option position

/// @audit `Errors`
965:         internal

/// @audit `Errors`
1047:             /** if the position is NOT long (selling a put or a call), then _mintLiquidity to move liquidity

/// @audit `LeftRightLibrary`
1156:                 )

/// @audit `Math`
1202:         /// @dev this triggers the uniswap mint callback function

/// @audit `Math`
1205:             liquidityChunk.tickLower(),

/// @audit `Math`
1211:         // amount0 The amount of token0 that was paid to mint the given amount of liquidity

/// @audit `Math`
1212:         // amount1 The amount of token1 that was paid to mint the given amount of liquidity

/// @audit `CallbackLib`
1223:     /// @return movedAmounts how many tokens were moved from Uniswap to msg.sender

/// @audit `CallbackLib`
1226:         IUniswapV3Pool univ3pool

/// @audit `Math`
1394:                         .mulDiv(premium0X64_base, numerator, totalLiquidity ** 2)

/// @audit `Math`
1397:                         .mulDiv(premium1X64_base, numerator, totalLiquidity ** 2)

/// @audit `Math`
1411:     //////////////////////////////////////////////////////////////*/

/// @audit `Math`
1414:     /// @dev Computes accountLiquidity[keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))]

/// @audit `Math`
1427:     ) external view returns (LeftRightUnsigned accountLiquidities) {

/// @audit `Math`
1429:         /// @dev tokenType input here is the asset of the positions minted, this avoids put liquidity to be used for call, and vice-versa

/// @audit `FeesCalc`
1508:                     s_accountPremiumOwed[positionKey],

/// @audit `LeftRightLibrary`
1541:     ) external view returns (int128 feesBase0, int128 feesBase1) {

```
*Github:* [[341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L341), [369](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L369), [380](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L380), [388](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L388), [429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L429), [430](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L430), [431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L431), [433](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L433), [455](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L455), [456](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L456), [468](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L468), [567](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L567), [593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L593), [627](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L627), [650](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L650), [659](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L659), [717](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L717), [731](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L731), [752](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L752), [793](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L793), [794](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L794), [854](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L854), [872](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L872), [874](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L874), [939](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L939), [949](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L949), [951](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L951), [965](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L965), [1047](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1047), [1156](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1156), [1202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1202), [1205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1205), [1211](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1211), [1212](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1212), [1223](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1223), [1226](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1226), [1394](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1394), [1397](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1397), [1411](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1411), [1414](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1414), [1427](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1427), [1429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1429), [1508](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1508), [1541](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1541)]


</details>