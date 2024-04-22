# QA Report

## Summary

### Low Issues

Total **138 instances** over **17 issues**:

|ID|Issue|Instances|
|:--:|:---|:--:|
| [[L-01]](#l-01-array-length-is-not-checked-before-access-its-index) | Array length is not checked before access its index | 12 |
| [[L-02]](#l-02-return-values-of-approve-not-checked) | Return values of `approve()` not checked | 4 |
| [[L-03]](#l-03-events-may-be-emitted-out-of-order-due-to-reentrancy) | Events may be emitted out of order due to reentrancy | 11 |
| [[L-04]](#l-04-missing-zero-address-check-in-constructor) | Missing zero address check in constructor | 8 |
| [[L-05]](#l-05-missing-zero-address-check-in-initializer) | Missing zero address check in initializer | 1 |
| [[L-06]](#l-06-named-return-variable-used-before-assignment) | Named return variable used before assignment | 5 |
| [[L-07]](#l-07-revert-on-transfer-to-the-zero-address) | Revert on transfer to the zero address | 7 |
| [[L-08]](#l-08-written-only-contract-variables) | Written only contract variables | 1 |
| [[L-09]](#l-09-downcasting-other-types-to-an-address-can-cause-collisions) | Downcasting other types to an address can cause collisions | 1 |
| [[L-10]](#l-10-vulnerable-versions-of-packages-are-being-used) | Vulnerable versions of packages are being used | 2 |
| [[L-11]](#l-11-constructor--initialization-function-lacks-parameter-validation) | Constructor / initialization function lacks parameter validation | 7 |
| [[L-12]](#l-12-minting-in-a-loop-may-lead-to-a-dos) | Minting in a loop may lead to a DOS | 2 |
| [[L-13]](#l-13-contracts-are-vulnerable-to-fee-on-transfer-accounting-related-issues) | Contracts are vulnerable to fee-on-transfer accounting-related issues | 7 |
| [[L-14]](#l-14-functions-calling-contractsaddresses-with-transfer-hooks-should-be-protected-by-reentrancy-guard) | Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard | 11 |
| [[L-15]](#l-15-critical-functions-should-be-controlled-by-time-locks) | Critical functions should be controlled by time locks | 7 |
| [[L-16]](#l-16-tokens-may-be-minted-to-the-zero-address) | Tokens may be minted to the zero address | 13 |
| [[L-17]](#l-17-code-does-not-follow-the-best-practice-of-check-effects-interaction) | Code does not follow the best practice of check-effects-interaction | 39 |

### Non Critical Issues

Total **850 instances** over **67 issues**:

|ID|Issue|Instances|
|:--:|:---|:--:|
| [[N-01]](#n-01-visibility-of-state-variables-is-not-explicitly-defined) | Visibility of state variables is not explicitly defined | 8 |
| [[N-02]](#n-02-names-of-privateinternal-functions-should-be-prefixed-with-an-underscore) | Names of `private`/`internal` functions should be prefixed with an underscore | 104 |
| [[N-03]](#n-03-names-of-privateinternal-state-variables-should-be-prefixed-with-an-underscore) | Names of `private`/`internal` state variables should be prefixed with an underscore | 75 |
| [[N-04]](#n-04-use-of-override-is-unnecessary) | Use of `override` is unnecessary | 4 |
| [[N-05]](#n-05-custom-errors-should-be-used-rather-than-revertrequire) | Custom errors should be used rather than `revert()`/`require()` | 9 |
| [[N-06]](#n-06-add-inline-comments-for-unnamed-parameters) | Add inline comments for unnamed parameters | 2 |
| [[N-07]](#n-07-assembly-blocks-should-have-extensive-comments) | Assembly blocks should have extensive comments | 21 |
| [[N-08]](#n-08-consider-splitting-complex-checks-into-multiple-steps) | Consider splitting complex checks into multiple steps | 2 |
| [[N-09]](#n-09-complex-casting) | Complex casting | 20 |
| [[N-10]](#n-10-complex-math-should-be-split-into-multiple-steps) | Complex math should be split into multiple steps | 26 |
| [[N-11]](#n-11-consider-adding-a-blockdeny-list) | Consider adding a block/deny-list | 3 |
| [[N-12]](#n-12-constantsimmutables-redefined-elsewhere) | Constants/Immutables redefined elsewhere | 4 |
| [[N-13]](#n-13-convert-simple-if-statements-to-ternary-expressions) | Convert simple `if`-statements to ternary expressions | 2 |
| [[N-14]](#n-14-contract-name-does-not-match-its-filename) | Contract name does not match its filename | 4 |
| [[N-15]](#n-15-upper_case-names-should-be-reserved-for-constantimmutable-variables) | UPPER_CASE names should be reserved for `constant`/`immutable` variables | 2 |
| [[N-16]](#n-16-consider-emitting-an-event-at-the-end-of-the-constructor) | Consider emitting an event at the end of the constructor | 4 |
| [[N-17]](#n-17-events-are-emitted-without-the-sender-information) | Events are emitted without the sender information | 3 |
| [[N-18]](#n-18-inconsistent-floating-version-pragma) | Inconsistent floating version pragma | 2 |
| [[N-19]](#n-19-contract-implements-interface-without-extending-the-interface) | Contract implements interface without extending the interface | 1 |
| [[N-20]](#n-20-imports-could-be-organized-more-systematically) | Imports could be organized more systematically | 4 |
| [[N-21]](#n-21-there-is-no-need-to-initialize-bool-variables-with-false) | There is no need to initialize bool variables with `false` | 5 |
| [[N-22]](#n-22-invalid-natspec-comment-style) | Invalid NatSpec comment style | 6 |
| [[N-23]](#n-23-openzeppelincontracts-should-be-upgraded-to-a-newer-version) | @openzeppelin/contracts should be upgraded to a newer version | 5 |
| [[N-24]](#n-24-lib-uniswapv3-core-should-be-upgraded-to-a-newer-version) | Lib @uniswap/v3-core should be upgraded to a newer version | 1 |
| [[N-25]](#n-25-lib-uniswapv3-periphery-should-be-upgraded-to-a-newer-version) | Lib @uniswap/v3-periphery should be upgraded to a newer version | 1 |
| [[N-26]](#n-26-expressions-for-constant-values-should-use-immutable-rather-than-constant) | Expressions for constant values should use `immutable` rather than `constant` | 3 |
| [[N-27]](#n-27-consider-moving-duplicated-strings-to-constants) | Consider moving duplicated strings to constants | 5 |
| [[N-28]](#n-28-contract-uses-both-requirerevert-as-well-as-custom-errors) | Contract uses both `require()`/`revert()` as well as custom errors | 1 |
| [[N-29]](#n-29-functions-should-be-named-in-mixedcase-style) | Functions should be named in mixedCase style | 11 |
| [[N-30]](#n-30-modifiers-should-be-named-in-mixedcase-style) | Modifiers should be named in mixedCase style | 1 |
| [[N-31]](#n-31-constants-should-be-put-on-the-left-side-of-comparisons) | Constants should be put on the left side of comparisons | 78 |
| [[N-32]](#n-32-else-block-not-required) | `else`-block not required | 10 |
| [[N-33]](#n-33-large-multiples-of-ten-should-use-scientific-notation) | Large multiples of ten should use scientific notation | 8 |
| [[N-34]](#n-34-non-interface-files-should-use-fixed-compiler-versions) | Non-interface files should use fixed compiler versions | 18 |
| [[N-35]](#n-35-high-cyclomatic-complexity) | High cyclomatic complexity | 2 |
| [[N-36]](#n-36-typos) | Typos | 17 |
| [[N-37]](#n-37-consider-bounding-input-array-length) | Consider bounding input array length | 9 |
| [[N-38]](#n-38-unnecessary-casting) | Unnecessary casting | 15 |
| [[N-39]](#n-39-unused-contract-variables) | Unused contract variables | 1 |
| [[N-40]](#n-40-unused-import) | Unused import | 29 |
| [[N-41]](#n-41-unused-named-return) | Unused named return | 18 |
| [[N-42]](#n-42-use-delete-instead-of-assigning-values-to-false) | Use delete instead of assigning values to `false` | 2 |
| [[N-43]](#n-43-consider-using-delete-rather-than-assigning-zero-to-clear-values) | Consider using `delete` rather than assigning zero to clear values | 3 |
| [[N-44]](#n-44-use-the-latest-solidity-version) | Use the latest Solidity version | 18 |
| [[N-45]](#n-45-use-a-struct-to-encapsulate-multiple-function-parameters) | Use a struct to encapsulate multiple function parameters | 9 |
| [[N-46]](#n-46-returning-a-struct-instead-of-a-bunch-of-variables-is-better) | Returning a struct instead of a bunch of variables is better | 5 |
| [[N-47]](#n-47-contract-variables-should-have-comments) | Contract variables should have comments | 1 |
| [[N-48]](#n-48-empty-bytes-check-is-missing) | Empty bytes check is missing | 7 |
| [[N-49]](#n-49-dont-define-functions-with-the-same-name-in-a-contract) | Don't define functions with the same name in a contract | 16 |
| [[N-50]](#n-50-assembly-block-creates-dirty-bits) | Assembly block creates dirty bits | 2 |
| [[N-51]](#n-51-multiple-mappings-with-same-keys-can-be-combined-into-a-single-struct-mapping-for-readability) | Multiple mappings with same keys can be combined into a single struct mapping for readability | 13 |
| [[N-52]](#n-52-do-not-cache-immutable-variables) | Do not cache immutable variables | 1 |
| [[N-53]](#n-53-function-state-mutability-can-be-restricted-to-view) | Function state mutability can be restricted to view | 1 |
| [[N-54]](#n-54-missing-event-for-critical-changes) | Missing event for critical changes | 9 |
| [[N-55]](#n-55-non-assembly-method-available) | Non-assembly method available | 6 |
| [[N-56]](#n-56-duplicated-requirerevert-checks-should-be-refactored) | Duplicated `require()`/`revert()` checks should be refactored | 13 |
| [[N-57]](#n-57-consider-adding-emergency-stop-functionality) | Consider adding emergency-stop functionality | 1 |
| [[N-58]](#n-58-missing-checks-for-uint-state-variable-assignments) | Missing checks for uint state variable assignments | 4 |
| [[N-59]](#n-59-use-the-modern-upgradeable-contract-paradigm) | Use the Modern Upgradeable Contract Paradigm | 3 |
| [[N-60]](#n-60-large-or-complicated-code-bases-should-implement-invariant-tests) | Large or complicated code bases should implement invariant tests | 1 |
| [[N-61]](#n-61-the-default-value-is-manually-set-when-it-is-declared) | The default value is manually set when it is declared | 31 |
| [[N-62]](#n-62-contracts-should-have-all-publicexternal-functions-exposed-by-interfaces) | Contracts should have all `public`/`external` functions exposed by `interface`s | 4 |
| [[N-63]](#n-63-top-level-declarations-should-be-separated-by-at-least-two-lines) | Top-level declarations should be separated by at least two lines | 2 |
| [[N-64]](#n-64-consider-adding-formal-verification-proofs) | Consider adding formal verification proofs | 20 |
| [[N-65]](#n-65-use-scopes-sparingly) | Use scopes sparingly | 21 |
| [[N-66]](#n-66-prevent-re-setting-a-state-variable-with-the-same-value) | Prevent re-setting a state variable with the same value | 15 |
| [[N-67]](#n-67-whitespace-in-expressions) | Whitespace in Expressions | 98 |

## Low Issues

### [L-01] Array length is not checked before access its index

Accessing the elements of the array without checking or ensuring the validity of the access index in advance. It may result in an unexpected out-of-bounds error, or may result in missing elements when trying to traverse the entire array.

<details>
<summary>There are 12 instances (click to show):</summary>

- *SemiFungiblePositionManager.sol* ( [577-577](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L577-L577) ):

```solidity
577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
```

- *Math.sol* ( [758-758](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L758-L758), [760-760](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L760-L760), [761-761](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L761-L761), [763-763](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L763-L763), [763-763](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L763-L763), [763-763](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L763-L763), [763-763](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L763-L763) ):

```solidity
758:             int256 pivot = arr[uint256(left + (right - left) / 2)];

760:                 while (arr[uint256(i)] < pivot) i++;

761:                 while (pivot < arr[uint256(j)]) j--;

763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);

763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);

763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);

763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);
```

- *PanopticMath.sol* ( [786-786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L786-L786), [786-786](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L786-L786) ):

```solidity
786:                         longPremium = longPremium.sub(premiasByLeg[i][leg]);

786:                         longPremium = longPremium.sub(premiasByLeg[i][leg]);
```

- *ERC1155Minimal.sol* ( [145-145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L145-L145), [188-188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L188-L188) ):

```solidity
145:             amount = amounts[i];

188:                 balances[i] = balanceOf[owners[i]][ids[i]];
```

</details>

### [L-02] Return values of `approve()` not checked

Not all ERC20 implementations `revert()` when there's a failure in `approve()`. The function signature has a boolean return value and they indicate errors that way instead. By not checking the return value, operations that should have marked as failed, may potentially go through without actually approving anything.

There are 4 instances:

- *InteractionHelper.sol* ( [32-32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L32-L32), [33-33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L33-L33), [36-36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L36-L36), [37-37](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L37-L37) ):

```solidity
32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```

### [L-03] Events may be emitted out of order due to reentrancy

Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls.

<details>
<summary>There are 11 instances (click to show):</summary>

- *CollateralTracker.sol* ( [439-439](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L439-L439), [499-499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L499-L499), [563-563](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L563-L563), [623-623](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L623-L623) ):

```solidity
/// @audit safeTransferFrom() is called prior to this emission in deposit()
439:         emit Deposit(msg.sender, receiver, assets, shares);

/// @audit safeTransferFrom() is called prior to this emission in mint()
499:         emit Deposit(msg.sender, receiver, assets, shares);

/// @audit safeTransferFrom() is called prior to this emission in withdraw()
563:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

/// @audit safeTransferFrom() is called prior to this emission in redeem()
623:         emit Withdraw(msg.sender, receiver, owner, assets, shares);
```

- *PanopticFactory.sol* ( [268-275](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L268-L275) ):

```solidity
/// @audit initializeAMMPool() is called prior to this emission in deployNewPool()
268:         emit PoolDeployed(
269:             newPoolContract,
270:             v3Pool,
271:             collateralTracker0,
272:             collateralTracker1,
273:             amount0,
274:             amount1
275:         );
```

- *PanopticPool.sol* ( [666-666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L666-L666), [853-853](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L853-L853), [1170-1170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1170-L1170), [1277-1277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1277-L1277), [1654-1654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1654-L1654) ):

```solidity
/// @audit _mintInSFPMAndUpdateCollateral() is called prior to this emission in _mintOptions(), which will call `mintTokenizedPosition()`
666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);

/// @audit _burnAndHandleExercise() is called prior to this emission in _burnOptions(), which will call `burnTokenizedPosition()`
853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

/// @audit delegate() is called prior to this emission in liquidate()
1170:         emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

/// @audit delegate() is called prior to this emission in forceExercise()
1277:         emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

/// @audit exercise() is called prior to this emission in settleLongPremium()
1654:             emit PremiumSettled(owner, tokenId, realizedPremia);
```

- *SemiFungiblePositionManager.sol* ( [517-517](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L517-L517) ):

```solidity
/// @audit _mint() is called prior to this emission in mintTokenizedPosition(), which will call `onERC1155Received()`
517:         emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);
```

</details>

### [L-04] Missing zero address check in constructor

Constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a checking, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could be due to an error or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it will be irretrievable. It's therefore crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.

<details>
<summary>There are 8 instances (click to show):</summary>

- *PanopticFactory.sol* ( [115-122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L115-L122) ):

```solidity
/// @audit `_WETH9 not checked`
/// @audit `_SFPM not checked`
/// @audit `_univ3Factory not checked`
/// @audit `_donorNFT not checked`
/// @audit `_poolReference not checked`
/// @audit `_collateralReference not checked`
115:     constructor(
116:         address _WETH9,
117:         SemiFungiblePositionManager _SFPM,
118:         IUniswapV3Factory _univ3Factory,
119:         IDonorNFT _donorNFT,
120:         address _poolReference,
121:         address _collateralReference
122:     ) {
```

- *PanopticPool.sol* ( [280-280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L280-L280) ):

```solidity
/// @audit `_sfpm not checked`
280:     constructor(SemiFungiblePositionManager _sfpm) {
```

- *SemiFungiblePositionManager.sol* ( [341-341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L341-L341) ):

```solidity
/// @audit `_factory not checked`
341:     constructor(IUniswapV3Factory _factory) {
```

</details>

### [L-05] Missing zero address check in initializer

Consider adding a zero address check for each address type parameter in initializer.

There is 1 instance:

- *PanopticFactory.sol* ( [134-134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L134-L134) ):

```solidity
/// @audit `_owner not checked`
134:     function initialize(address _owner) public {
```

### [L-06] Named return variable used before assignment

As no value is written to the variable, the default value is always read. This is usually due to a bug in the code logic that causes an invalid value to be used.

There are 5 instances:

- *Math.sol* ( [319-319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L319-L319) ):

```solidity
/// @audit downcastedInt
319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();
```

- *LeftRight.sol* ( [206-206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L206-L206), [224-224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L224-L224), [242-242](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L242-L242), [265-265](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L265-L265) ):

```solidity
/// @audit z
206:             return z.toRightSlot(right128).toLeftSlot(left128);

/// @audit z
224:             return z.toRightSlot(right128).toLeftSlot(left128);

/// @audit z
242:             return z.toRightSlot(right128).toLeftSlot(left128);

/// @audit z
265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(
```

### [L-07] Revert on transfer to the zero address

It's good practice to revert a token transfer transaction if the recipient's address is the zero address. This can prevent unintentional transfers to the zero address due to accidental operations or programming errors. Many token contracts implement such a safeguard, such as [OpenZeppelin - ERC20](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/9e3f4d60c581010c4a3979480e07cc7752f124cc/contracts/token/ERC20/ERC20.sol#L232), [OpenZeppelin - ERC721](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/9e3f4d60c581010c4a3979480e07cc7752f124cc/contracts/token/ERC721/ERC721.sol#L142).

<details>
<summary>There are 7 instances (click to show):</summary>

- *CollateralTracker.sol* ( [333-333](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L333-L333), [352-352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L352-L352), [424-429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L424-L429), [484-489](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L484-L489), [556-561](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L556-L561), [616-621](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L616-L621) ):

```solidity
333:         return ERC20Minimal.transfer(recipient, amount);

352:         return ERC20Minimal.transferFrom(from, to, amount);

424:         SafeTransferLib.safeTransferFrom(
425:             s_underlyingToken,
426:             msg.sender,
427:             address(s_panopticPool),
428:             assets
429:         );

484:         SafeTransferLib.safeTransferFrom(
485:             s_underlyingToken,
486:             msg.sender,
487:             address(s_panopticPool),
488:             assets
489:         );

556:         SafeTransferLib.safeTransferFrom(
557:             s_underlyingToken,
558:             address(s_panopticPool),
559:             receiver,
560:             assets
561:         );

616:         SafeTransferLib.safeTransferFrom(
617:             s_underlyingToken,
618:             address(s_panopticPool),
619:             receiver,
620:             assets
621:         );
```

- *SemiFungiblePositionManager.sol* ( [555-555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L555-L555) ):

```solidity
555:         super.safeTransferFrom(from, to, id, amount, data);
```

</details>

### [L-08] Written only contract variables

Write only contract variables are only written in the contract and are never read and cannot be accessed through an interface.
It is recommended to check if there is a bug causing the missing readings, or if some `view` interfaces should be provided. If not, consider removing them to improve code clarity, avoid confusion, and save gas.

There is 1 instance:

- *CollateralTracker.sol* ( [201-209](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L201-L209) ):

```solidity
201:             TICK_DEVIATION = uint256(
202:                 2230 +
203:                     (12500 * ratioTick) /
204:                     10_000 +
205:                     (7812 * ratioTick ** 2) /
206:                     10_000 ** 2 +
207:                     (6510 * ratioTick ** 3) /
208:                     10_000 ** 3
209:             );
```

### [L-09] Downcasting other types to an address can cause collisions

Downcasting other types to an address will truncates the upper bytes, which means that multiple values can be mapped to an address, i.e. address collisions can occur.

There is 1 instance:

- *PanopticFactory.sol* ( [220-220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L220-L220) ):

```solidity
220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();
```

### [L-10] Vulnerable versions of packages are being used

This project is using specific package versions which are vulnerable to the specific CVEs listed below. Consider switching to more recent versions of these packages that don't have these vulnerabilities.
- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`openzeppelin-solidity >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **MEDIUM** - (`openzeppelin-solidity >=4.7.0 <4.9.2`): OpenZeppelin Contracts is a library for smart contract development. Starting in version 4.7.0 and prior to version 4.9.2, when the `verifyMultiProof`, `verifyMultiProofCalldata`, `procesprocessMultiProof`, or `processMultiProofCalldat` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertedly for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe. The problem has been patched in version 4.9.2. Some workarounds are available. For those using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the @openzeppelin/merkle-tree package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.

There are 2 instances:

- Global finding

### [L-11] Constructor / initialization function lacks parameter validation

Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

There are 7 instances:

- *CollateralTracker.sol* ( [178-186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178-L186) ):

```solidity
/// @audit `_commissionFee`
/// @audit `_sellerCollateralRatio`
/// @audit `_buyerCollateralRatio`
/// @audit `_forceExerciseCost`
/// @audit `_targetPoolUtilization`
/// @audit `_saturatedPoolUtilization`
/// @audit `_ITMSpreadMultiplier`
178:     constructor(
179:         uint256 _commissionFee,
180:         uint256 _sellerCollateralRatio,
181:         uint256 _buyerCollateralRatio,
182:         int256 _forceExerciseCost,
183:         uint256 _targetPoolUtilization,
184:         uint256 _saturatedPoolUtilization,
185:         uint256 _ITMSpreadMultiplier
186:     ) {
```

### [L-12] Minting in a loop may lead to a DOS

The signature used seems to require all the minting operations to be done at once. If there are a lot of them, there may be too many to mint in one block.

<details>
<summary>There are 2 instances (click to show):</summary>

- *PanopticPool.sol* ( [802-815](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L802-L815) ):

```solidity
/// @audit mint by _burnOptions()
802:         for (uint256 i = 0; i < positionIdList.length; ) {
803:             LeftRightSigned paidAmounts;
804:             (paidAmounts, premiasByLeg[i]) = _burnOptions(
805:                 commitLongSettled,
806:                 positionIdList[i],
807:                 owner,
808:                 tickLimitLow,
809:                 tickLimitHigh
810:             );
811:             netPaid = netPaid.add(paidAmounts);
812:             unchecked {
813:                 ++i;
814:             }
815:         }
```

- *SemiFungiblePositionManager.sol* ( [882-934](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L882-L934) ):

```solidity
/// @audit mint by _createLegInAMM()
882:         for (uint256 leg = 0; leg < numLegs; ) {
883:             LeftRightSigned _moved;
884:             LeftRightSigned _itmAmounts;
885:             LeftRightUnsigned _collectedSingleLeg;
886: 
887:             {
888:                 // cache the univ3pool, tokenId, isBurn, and _positionSize variables to get rid of stack too deep error
889:                 IUniswapV3Pool _univ3pool = univ3pool;
890:                 TokenId _tokenId = tokenId;
891:                 bool _isBurn = isBurn;
892:                 uint128 _positionSize = positionSize;
893:                 uint256 _leg;
894: 
895:                 unchecked {
896:                     // Reverse the order of the legs if this call is burning a position (LIFO)
897:                     // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,
898:                     // allowing the corresponding short liquidity to be removed
899:                     _leg = _isBurn ? numLegs - leg - 1 : leg;
900:                 }
901: 
902:                 // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
903:                 // @dev see `contracts/types/LiquidityChunk.sol`
904:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
905:                     _tokenId,
906:                     _leg,
...... OMITTED ......
910:                 (_moved, _itmAmounts, _collectedSingleLeg) = _createLegInAMM(
911:                     _univ3pool,
912:                     _tokenId,
913:                     _leg,
914:                     liquidityChunk,
915:                     _isBurn
916:                 );
917: 
918:                 collectedByLeg[_leg] = _collectedSingleLeg;
919: 
920:                 unchecked {
921:                     // increment accumulators of the upper bound on tokens contained across all legs of the position at any given tick
922:                     amount0 += Math.getAmount0ForLiquidity(liquidityChunk);
923: 
924:                     amount1 += Math.getAmount1ForLiquidity(liquidityChunk);
925:                 }
926:             }
927: 
928:             totalMoved = totalMoved.add(_moved);
929:             itmAmounts = itmAmounts.add(_itmAmounts);
930: 
931:             unchecked {
932:                 ++leg;
933:             }
934:         }
```

</details>

### [L-13] Contracts are vulnerable to fee-on-transfer accounting-related issues

Some tokens take a transfer fee (e.g. STA, PAXG), some do not currently charge a fee but may do so in the future (e.g. USDT, USDC).
The functions below transfer funds from the caller to the receiver via `transferFrom()`, but do not ensure that the actual number of tokens received is the same as the input amount to the transfer. If the token is a fee-on-transfer token, the balance after the transfer will be smaller than expected, leading to accounting issues. Even if there are checks later, related to a secondary transfer, an attacker may be able to use latent funds (e.g. mistakenly sent by another user) in order to get a free credit.
One way to solve this problem is to measure the balance before and after the transfer, and use the difference as the amount, rather than the stated amount.

<details>
<summary>There are 7 instances (click to show):</summary>

- *CollateralTracker.sol* ( [333-333](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L333-L333), [352-352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L352-L352) ):

```solidity
333:         return ERC20Minimal.transfer(recipient, amount);

352:         return ERC20Minimal.transferFrom(from, to, amount);
```

- *PanopticFactory.sol* ( [182-187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L182-L187), [189-194](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L189-L194) ):

```solidity
182:             SafeTransferLib.safeTransferFrom(
183:                 decoded.poolFeatures.token0,
184:                 decoded.payer,
185:                 msg.sender,
186:                 amount0Owed
187:             );

189:             SafeTransferLib.safeTransferFrom(
190:                 decoded.poolFeatures.token1,
191:                 decoded.payer,
192:                 msg.sender,
193:                 amount1Owed
194:             );
```

- *SemiFungiblePositionManager.sol* ( [413-418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L413-L418), [420-425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L420-L425), [456-456](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L456-L456) ):

```solidity
413:             SafeTransferLib.safeTransferFrom(
414:                 decoded.poolFeatures.token0,
415:                 decoded.payer,
416:                 msg.sender,
417:                 amount0Owed
418:             );

420:             SafeTransferLib.safeTransferFrom(
421:                 decoded.poolFeatures.token1,
422:                 decoded.payer,
423:                 msg.sender,
424:                 amount1Owed
425:             );

456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);
```

</details>

### [L-14] Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks opens the users of this protocol up to [read-only reentrancy vulnerability](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect them except by block-listing the entire protocol.

<details>
<summary>There are 11 instances (click to show):</summary>

- *CollateralTracker.sol* ( [333-333](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L333-L333), [352-352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L352-L352), [424-429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L424-L429), [484-489](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L484-L489), [556-561](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L556-L561), [616-621](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L616-L621) ):

```solidity
333:         return ERC20Minimal.transfer(recipient, amount);

352:         return ERC20Minimal.transferFrom(from, to, amount);

424:         SafeTransferLib.safeTransferFrom(
425:             s_underlyingToken,
426:             msg.sender,
427:             address(s_panopticPool),
428:             assets
429:         );

484:         SafeTransferLib.safeTransferFrom(
485:             s_underlyingToken,
486:             msg.sender,
487:             address(s_panopticPool),
488:             assets
489:         );

556:         SafeTransferLib.safeTransferFrom(
557:             s_underlyingToken,
558:             address(s_panopticPool),
559:             receiver,
560:             assets
561:         );

616:         SafeTransferLib.safeTransferFrom(
617:             s_underlyingToken,
618:             address(s_panopticPool),
619:             receiver,
620:             assets
621:         );
```

- *PanopticFactory.sol* ( [182-187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L182-L187), [189-194](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L189-L194) ):

```solidity
182:             SafeTransferLib.safeTransferFrom(
183:                 decoded.poolFeatures.token0,
184:                 decoded.payer,
185:                 msg.sender,
186:                 amount0Owed
187:             );

189:             SafeTransferLib.safeTransferFrom(
190:                 decoded.poolFeatures.token1,
191:                 decoded.payer,
192:                 msg.sender,
193:                 amount1Owed
194:             );
```

- *SemiFungiblePositionManager.sol* ( [413-418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L413-L418), [420-425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L420-L425), [456-456](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L456-L456) ):

```solidity
413:             SafeTransferLib.safeTransferFrom(
414:                 decoded.poolFeatures.token0,
415:                 decoded.payer,
416:                 msg.sender,
417:                 amount0Owed
418:             );

420:             SafeTransferLib.safeTransferFrom(
421:                 decoded.poolFeatures.token1,
422:                 decoded.payer,
423:                 msg.sender,
424:                 amount1Owed
425:             );

456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);
```

</details>

### [L-15] Critical functions should be controlled by time locks

It is a good practice to give time for users to react and adjust to critical changes. A timelock provides more guarantees and reduces the level of trust required, thus decreasing risk for users. It also indicates that the project is legitimate (less risk of a malicious owner making a sandwich attack on a user).

<details>
<summary>There are 7 instances (click to show):</summary>

- *CollateralTracker.sol* ( [221-227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L221-L227), [995-1000](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L995-L1000) ):

```solidity
221:     function startToken(
222:         bool underlyingIsToken0,
223:         address token0,
224:         address token1,
225:         uint24 fee,
226:         PanopticPool panopticPool
227:     ) external {

995:     function takeCommissionAddData(
996:         address optionOwner,
997:         int128 longAmount,
998:         int128 shortAmount,
999:         int128 swappedAmount
1000:     ) external onlyPanopticPool returns (int256 utilization) {
```

- *PanopticPool.sol* ( [291-297](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L291-L297), [859-859](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L859-L859), [1405-1405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1405-L1405), [1833-1839](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1833-L1839) ):

```solidity
291:     function startPool(
292:         IUniswapV3Pool _univ3pool,
293:         address token0,
294:         address token1,
295:         CollateralTracker collateralTracker0,
296:         CollateralTracker collateralTracker1
297:     ) external {

859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

1405:     function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {

1833:     function _updateSettlementPostBurn(
1834:         address owner,
1835:         TokenId tokenId,
1836:         LeftRightUnsigned[4] memory collectedByLeg,
1837:         uint128 positionSize,
1838:         bool commitLongSettled
1839:     ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
```

- *ERC1155Minimal.sol* ( [81-81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L81-L81) ):

```solidity
81:     function setApprovalForAll(address operator, bool approved) public {
```

</details>

### [L-16] Tokens may be minted to the zero address

Neither the listed functions, nor `_mint()` prevent minting to `address(0x0)`

<details>
<summary>There are 13 instances (click to show):</summary>

- *CollateralTracker.sol* ( [432-432](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L432-L432), [477-477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L477-L477), [954-961](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L954-L961), [1021-1021](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1021-L1021), [1078-1078](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1078-L1078) ):

```solidity
432:         _mint(receiver, shares);

477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {

954:             _mint(
955:                 delegator,
956:                 Math.mulDiv(
957:                     assets,
958:                     totalSupply - delegateeBalance,
959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
960:                 ) - delegateeBalance
961:             );

1021:                 _mint(optionOwner, sharesToMint);

1078:                 _mint(optionOwner, sharesToMint);
```

- *PanopticFactory.sol* ( [335-340](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L335-L340) ):

```solidity
335:     function _mintFullRange(
336:         IUniswapV3Pool v3Pool,
337:         address token0,
338:         address token1,
339:         uint24 fee
340:     ) internal returns (uint256, uint256) {
```

- *PanopticPool.sol* ( [547-553](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L547-L553), [614-620](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L614-L620), [677-682](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L677-L682) ):

```solidity
547:     function mintOptions(
548:         TokenId[] calldata positionIdList,
549:         uint128 positionSize,
550:         uint64 effectiveLiquidityLimitX32,
551:         int24 tickLimitLow,
552:         int24 tickLimitHigh
553:     ) external {

614:     function _mintOptions(
615:         TokenId[] calldata positionIdList,
616:         uint128 positionSize,
617:         uint64 effectiveLiquidityLimitX32,
618:         int24 tickLimitLow,
619:         int24 tickLimitHigh
620:     ) internal {

677:     function _mintInSFPMAndUpdateCollateral(
678:         TokenId tokenId,
679:         uint128 positionSize,
680:         int24 tickLimitLow,
681:         int24 tickLimitHigh
682:     ) internal returns (uint128) {
```

- *SemiFungiblePositionManager.sol* ( [504-512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L504-L512), [1067-1067](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1067-L1067), [1185-1188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1185-L1188) ):

```solidity
504:     function mintTokenizedPosition(
505:         TokenId tokenId,
506:         uint128 positionSize,
507:         int24 slippageTickLimitLow,
508:         int24 slippageTickLimitHigh
509:     )
510:         external
511:         ReentrancyLock(tokenId.poolId())
512:         returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)

1067:                 ? _mintLiquidity(liquidityChunk, univ3pool)

1185:     function _mintLiquidity(
1186:         LiquidityChunk liquidityChunk,
1187:         IUniswapV3Pool univ3pool
1188:     ) internal returns (LeftRightSigned movedAmounts) {
```

- *ERC20Minimal.sol* ( [122-122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L122-L122) ):

```solidity
122:     function _mint(address to, uint256 amount) internal {
```

</details>

### [L-17] Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

<details>
<summary>There are 39 instances (click to show):</summary>

- *CollateralTracker.sol* ( [436-436](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L436-L436), [496-496](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L496-L496) ):

```solidity
/// @audit `safeTransferFrom()` is called on line 424
436:             s_poolAssets += uint128(assets);

/// @audit `safeTransferFrom()` is called on line 484
496:             s_poolAssets += uint128(assets);
```

- *PanopticFactory.sol* ( [237-237](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L237-L237), [253-253](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L253-L253) ):

```solidity
/// @audit `initializeAMMPool()` is called on line 233
237:         newPoolContract = PanopticPool(POOL_REFERENCE.cloneDeterministic(salt));

/// @audit `initializeAMMPool()` is called on line 233
253:         s_getPanopticPool[v3Pool] = newPoolContract;
```

- *PanopticPool.sol* ( [654-657](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L654-L657), [664-664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L664-L664), [811-811](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L811-L811), [813-813](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L813-L813), [973-979](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L973-L979), [992-992](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L992-L992), [1003-1003](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1003-L1003), [1086-1092](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1086-L1092), [1094-1094](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1094-L1094), [1098-1106](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1098-L1106), [1122-1131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1122-L1131), [1134-1134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1134-L1134), [1135-1135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1135-L1135), [1242-1248](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1242-L1248), [1650-1652](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1650-L1652) ):

```solidity
/// @audit `_mintInSFPMAndUpdateCollateral()` is called on line 642, triggering an external call - `mintTokenizedPosition()`
654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
655:             .wrap(0)
656:             .toLeftSlot(poolUtilizations)
657:             .toRightSlot(positionSize);

/// @audit `_mintInSFPMAndUpdateCollateral()` is called on line 642, triggering an external call - `mintTokenizedPosition()`
664:         if (medianData != 0) s_miniMedian = medianData;

/// @audit `_burnOptions()` is called on line 804, triggering an external call - `burnTokenizedPosition()`
811:             netPaid = netPaid.add(paidAmounts);

/// @audit `_burnOptions()` is called on line 804, triggering an external call - `burnTokenizedPosition()`
813:                 ++i;

/// @audit `burnTokenizedPosition()` is called on line 970
973:         (realizedPremia, premiaByLeg) = _updateSettlementPostBurn(
974:             owner,
975:             tokenId,
976:             collectedByLeg,
977:             positionSize,
978:             commitLongSettled
979:         );

/// @audit `burnTokenizedPosition()` is called on line 970
992:             paidAmounts = paidAmounts.toRightSlot(paid0);

/// @audit `burnTokenizedPosition()` is called on line 970
1003:             paidAmounts = paidAmounts.toLeftSlot(paid1);

/// @audit `getUniV3TWAP()` is called on line 1026, triggering an external call - `observe()`
1086:             (netExchanged, premiasByLeg) = _burnAllOptionsFrom(
1087:                 liquidatee,
1088:                 Constants.MIN_V3POOL_TICK,
1089:                 Constants.MAX_V3POOL_TICK,
1090:                 DONOT_COMMIT_LONG_SETTLED,
1091:                 positionIdList
1092:             );

/// @audit `getUniV3TWAP()` is called on line 1026, triggering an external call - `observe()`
1094:             (, finalTick, , , , , ) = s_univ3pool.slot0();

/// @audit `getUniV3TWAP()` is called on line 1026, triggering an external call - `observe()`
1098:             (liquidationBonus0, liquidationBonus1, collateralRemaining) = PanopticMath
1099:                 .getLiquidationBonus(
1100:                     tokenData0,
1101:                     tokenData1,
1102:                     Math.getSqrtRatioAtTick(twapTick),
1103:                     Math.getSqrtRatioAtTick(finalTick),
1104:                     netExchanged,
1105:                     premia
1106:                 );

/// @audit `getUniV3TWAP()` is called on line 1026, triggering an external call - `observe()`
1122:             (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(
1123:                 _liquidatee,
1124:                 _positionIdList,
1125:                 premiasByLeg,
1126:                 collateralRemaining,
1127:                 s_collateralToken0,
1128:                 s_collateralToken1,
1129:                 Math.getSqrtRatioAtTick(_finalTick),
1130:                 s_settledTokens
1131:             );

/// @audit `getUniV3TWAP()` is called on line 1026, triggering an external call - `observe()`
1134:                 liquidationBonus0 += deltaBonus0;

/// @audit `getUniV3TWAP()` is called on line 1026, triggering an external call - `observe()`
1135:                 liquidationBonus1 += deltaBonus1;

/// @audit `getUniV3TWAP()` is called on line 1200, triggering an external call - `observe()`
1242:         refundAmounts = PanopticMath.getRefundAmounts(
1243:             account,
1244:             refundAmounts,
1245:             twapTick,
1246:             s_collateralToken0,
1247:             s_collateralToken1
1248:         );

/// @audit `slot0()` is called on line 1598
1650:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(
1651:                 LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))
1652:             );
```

- *SemiFungiblePositionManager.sol* ( [520-526](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L520-L526), [721-721](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L721-L721), [848-850](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L848-L850), [918-918](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L918-L918), [922-922](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L922-L922), [924-924](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L924-L924), [928-928](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L928-L928), [929-929](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L929-L929), [932-932](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L932-L932), [1075-1075](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1075-L1075), [1080-1080](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1080-L1080), [1086-1093](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1086-L1093), [1098-1103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1098-L1103), [1214-1216](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1214-L1216), [1241-1243](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1241-L1243), [1296-1298](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1296-L1298), [1299-1301](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1299-L1301), [1306-1308](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1306-L1308) ):

```solidity
/// @audit `_mint()` is called on line 515, triggering an external call - `onERC1155Received()`
520:         (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
521:             tokenId,
522:             positionSize,
523:             slippageTickLimitLow,
524:             slippageTickLimitHigh,
525:             MINT
526:         );

/// @audit `slot0()` is called on line 725
721:             (tickLimitLow, tickLimitHigh) = (tickLimitHigh, tickLimitLow);

/// @audit `swap()` is called on line 837
848:             totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(
849:                 swap1.toInt128()
850:             );

/// @audit `_createLegInAMM()` is called on line 910, triggering an external call - `positions()`
918:                 collectedByLeg[_leg] = _collectedSingleLeg;

/// @audit `_createLegInAMM()` is called on line 910, triggering an external call - `positions()`
922:                     amount0 += Math.getAmount0ForLiquidity(liquidityChunk);

/// @audit `_createLegInAMM()` is called on line 910, triggering an external call - `positions()`
924:                     amount1 += Math.getAmount1ForLiquidity(liquidityChunk);

/// @audit `_createLegInAMM()` is called on line 910, triggering an external call - `positions()`
928:             totalMoved = totalMoved.add(_moved);

/// @audit `_createLegInAMM()` is called on line 910, triggering an external call - `positions()`
929:             itmAmounts = itmAmounts.add(_itmAmounts);

/// @audit `_createLegInAMM()` is called on line 910, triggering an external call - `positions()`
932:                 ++leg;

/// @audit `_getFeesBase()` is called on line 1098, triggering an external call - `positions()`
1075:                 itmAmounts = itmAmounts.toRightSlot(moved.rightSlot());

/// @audit `_getFeesBase()` is called on line 1098, triggering an external call - `positions()`
1080:                 itmAmounts = itmAmounts.toLeftSlot(moved.leftSlot());

/// @audit `_getFeesBase()` is called on line 1098, triggering an external call - `positions()`
1086:             collectedSingleLeg = _collectAndWritePositionData(
1087:                 liquidityChunk,
1088:                 univ3pool,
1089:                 currentLiquidity,
1090:                 positionKey,
1091:                 moved,
1092:                 isLong
1093:             );

/// @audit `_getFeesBase()` is called on line 1098, triggering an external call - `positions()`
1098:         s_accountFeesBase[positionKey] = _getFeesBase(
1099:             univ3pool,
1100:             updatedLiquidity,
1101:             liquidityChunk,
1102:             true
1103:         );

/// @audit `mint()` is called on line 1203
1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(
1215:             int128(int256(amount1))
1216:         );

/// @audit `burn()` is called on line 1230
1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(
1242:                 -int128(int256(amount1))
1243:             );

/// @audit `_getFeesBase()` is called on line 1268, triggering an external call - `positions()`
1296:                 collected0 = movedInLeg.rightSlot() < 0
1297:                     ? receivedAmount0 - uint128(-movedInLeg.rightSlot())
1298:                     : receivedAmount0;

/// @audit `_getFeesBase()` is called on line 1268, triggering an external call - `positions()`
1299:                 collected1 = movedInLeg.leftSlot() < 0
1300:                     ? receivedAmount1 - uint128(-movedInLeg.leftSlot())
1301:                     : receivedAmount1;

/// @audit `_getFeesBase()` is called on line 1268, triggering an external call - `positions()`
1306:             collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(
1307:                 collected1
1308:             );
```

- *Multicall.sol* ( [30-30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L30-L30), [33-33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L33-L33) ):

```solidity
/// @audit `delegatecall()` is called on line 15
30:             results[i] = result;

/// @audit `delegatecall()` is called on line 15
33:                 ++i;
```

</details>

## Non Critical Issues

### [N-01] Visibility of state variables is not explicitly defined

To avoid misunderstandings and unexpected state accesses, it is recommended to explicitly define the visibility of each state variable.

There are 8 instances:

- *CollateralTracker.sol* ( [131-131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L131-L131), [136-136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L136-L136), [141-141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L141-L141), [145-145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L145-L145), [149-149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L149-L149), [154-154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L154-L154), [158-158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L158-L158), [162-162](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L162-L162) ):

```solidity
131:     uint256 immutable TICK_DEVIATION;

136:     uint256 immutable COMMISSION_FEE;

141:     uint256 immutable SELLER_COLLATERAL_RATIO;

145:     uint256 immutable BUYER_COLLATERAL_RATIO;

149:     int256 immutable FORCE_EXERCISE_COST;

154:     uint256 immutable TARGET_POOL_UTIL;

158:     uint256 immutable SATURATED_POOL_UTIL;

162:     uint256 immutable ITM_SPREAD_MULTIPLIER;
```

### [N-02] Names of `private`/`internal` functions should be prefixed with an underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

<details>
<summary>There are 104 instances (click to show):</summary>

- *PanopticPool.sol* ( [1450-1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1450-L1450) ):

```solidity
1450:     function getUniV3TWAP() internal view returns (int24 twapTick) {
```

- *SemiFungiblePositionManager.sol* ( [320-320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L320-L320), [330-330](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L330-L330), [593-593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L593-L593), [756-759](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L756-L759) ):

```solidity
320:     function beginReentrancyLock(uint64 poolId) internal {

330:     function endReentrancyLock(uint64 poolId) internal {

593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

756:     function swapInAMM(
757:         IUniswapV3Pool univ3pool,
758:         LeftRightSigned itmAmounts
759:     ) internal returns (LeftRightSigned totalSwapped) {
```

- *CallbackLib.sol* ( [30-34](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L30-L34) ):

```solidity
30:     function validateCallback(
31:         address sender,
32:         IUniswapV3Factory factory,
33:         PoolFeatures memory features
34:     ) internal view {
```

- *Math.sol* ( [25-25](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L25-L25), [33-33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L33-L33), [41-41](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L41-L41), [49-49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L49-L49), [57-57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L57-L57), [65-65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L65-L65), [73-73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L73-L73), [81-81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L81-L81), [91-91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L91-L91), [128-128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L128-L128), [191-191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L191-L191), [207-207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L207-L207), [221-224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L221-L224), [241-245](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L241-L245), [271-275](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L271-L275), [296-296](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L296-L296), [302-302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L302-L302), [311-311](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L311-L311), [318-318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L318-L318), [325-325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L325-L325), [340-344](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L340-L344), [440-444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L440-L444), [458-458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L458-L458), [521-521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L521-L521), [584-584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L584-L584), [598-598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L598-L598), [661-661](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L661-L661), [675-675](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L675-L675), [738-738](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L738-L738), [753-753](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L753-L753), [776-776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L776-L776) ):

```solidity
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
222:         int24 currentTick,
223:         LiquidityChunk liquidityChunk
224:     ) internal pure returns (uint256 amount0, uint256 amount1) {

241:     function getLiquidityForAmount0(
242:         int24 tickLower,
243:         int24 tickUpper,
244:         uint256 amount0
245:     ) internal pure returns (LiquidityChunk) {

271:     function getLiquidityForAmount1(
272:         int24 tickLower,
273:         int24 tickUpper,
274:         uint256 amount1
275:     ) internal pure returns (LiquidityChunk) {

296:     function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

340:     function mulDiv(
341:         uint256 a,
342:         uint256 b,
343:         uint256 denominator
344:     ) internal pure returns (uint256 result) {

440:     function mulDivRoundingUp(
441:         uint256 a,
442:         uint256 b,
443:         uint256 denominator
444:     ) internal pure returns (uint256 result) {

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

- *PanopticMath.sol* ( [47-47](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L47-L47), [59-59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L59-L59), [92-96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L92-L96), [289-293](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L289-L293), [338-342](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L338-L342), [371-374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L371-L374), [390-393](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L390-L393), [419-424](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L419-L424), [445-450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L445-L450), [468-473](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L468-L473), [490-490](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L490-L490), [507-507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L507-L507), [524-524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L524-L524), [547-547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L547-L547), [574-578](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L574-L578) ):

```solidity
47:     function getPoolId(address univ3pool) internal view returns (uint64) {

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

92:     function updatePositionsHash(
93:         uint256 existingHash,
94:         TokenId tokenId,
95:         bool addFlag
96:     ) internal pure returns (uint256) {

289:     function getLiquidityChunk(
290:         TokenId tokenId,
291:         uint256 legIndex,
292:         uint128 positionSize
293:     ) internal pure returns (LiquidityChunk) {

338:     function getTicks(
339:         int24 strike,
340:         int24 width,
341:         int24 tickSpacing
342:     ) internal pure returns (int24 tickLower, int24 tickUpper) {

371:     function getRangesFromStrike(
372:         int24 width,
373:         int24 tickSpacing
374:     ) internal pure returns (int24, int24) {

390:     function computeExercisedAmounts(
391:         TokenId tokenId,
392:         uint128 positionSize
393:     ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {

419:     function convertCollateralData(
420:         LeftRightUnsigned tokenData0,
421:         LeftRightUnsigned tokenData1,
422:         uint256 tokenType,
423:         uint160 sqrtPriceX96
424:     ) internal pure returns (uint256, uint256) {

445:     function convertCollateralData(
446:         LeftRightUnsigned tokenData0,
447:         LeftRightUnsigned tokenData1,
448:         uint256 tokenType,
449:         int24 tick
450:     ) internal pure returns (uint256, uint256) {

468:     function convertNotional(
469:         uint128 contractSize,
470:         int24 tickLower,
471:         int24 tickUpper,
472:         uint256 asset
473:     ) internal pure returns (uint128) {

490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

574:     function getAmountsMoved(
575:         TokenId tokenId,
576:         uint128 positionSize,
577:         uint256 legIndex
578:     ) internal pure returns (LeftRightUnsigned) {
```

- *SafeTransferLib.sol* ( [21-21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L21-L21), [52-52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L52-L52) ):

```solidity
21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:     function safeTransfer(address token, address to, uint256 amount) internal {
```

- *LeftRight.sol* ( [39-39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L39-L39), [46-46](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L46-L46), [59-62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L59-L62), [78-81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L78-L81), [101-101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L101-L101), [108-108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L108-L108), [121-124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L121-L124), [134-134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L134-L134), [148-151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L148-L151), [171-174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L171-L174), [194-194](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L194-L194), [214-214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L214-L214), [232-232](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L232-L232), [251-254](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L251-L254), [279-284](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L279-L284) ):

```solidity
39:     function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46:     function rightSlot(LeftRightSigned self) internal pure returns (int128) {

59:     function toRightSlot(
60:         LeftRightUnsigned self,
61:         uint128 right
62:     ) internal pure returns (LeftRightUnsigned) {

78:     function toRightSlot(
79:         LeftRightSigned self,
80:         int128 right
81:     ) internal pure returns (LeftRightSigned) {

101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

121:     function toLeftSlot(
122:         LeftRightUnsigned self,
123:         uint128 left
124:     ) internal pure returns (LeftRightUnsigned) {

134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

148:     function add(
149:         LeftRightUnsigned x,
150:         LeftRightUnsigned y
151:     ) internal pure returns (LeftRightUnsigned z) {

171:     function sub(
172:         LeftRightUnsigned x,
173:         LeftRightUnsigned y
174:     ) internal pure returns (LeftRightUnsigned z) {

194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

214:     function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

251:     function subRect(
252:         LeftRightSigned x,
253:         LeftRightSigned y
254:     ) internal pure returns (LeftRightSigned z) {

279:     function addCapped(
280:         LeftRightUnsigned x,
281:         LeftRightUnsigned dx,
282:         LeftRightUnsigned y,
283:         LeftRightUnsigned dy
284:     ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {
```

- *LiquidityChunk.sol* ( [70-74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L70-L74), [89-92](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L89-L92), [102-105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L102-L105), [118-121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L118-L121), [135-138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L135-L138), [151-154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L151-L154), [171-171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L171-L171), [180-180](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L180-L180), [189-189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L189-L189) ):

```solidity
70:     function createChunk(
71:         int24 _tickLower,
72:         int24 _tickUpper,
73:         uint128 amount
74:     ) internal pure returns (LiquidityChunk) {

89:     function addLiquidity(
90:         LiquidityChunk self,
91:         uint128 amount
92:     ) internal pure returns (LiquidityChunk) {

102:     function addTickLower(
103:         LiquidityChunk self,
104:         int24 _tickLower
105:     ) internal pure returns (LiquidityChunk) {

118:     function addTickUpper(
119:         LiquidityChunk self,
120:         int24 _tickUpper
121:     ) internal pure returns (LiquidityChunk) {

135:     function updateTickLower(
136:         LiquidityChunk self,
137:         int24 _tickLower
138:     ) internal pure returns (LiquidityChunk) {

151:     function updateTickUpper(
152:         LiquidityChunk self,
153:         int24 _tickUpper
154:     ) internal pure returns (LiquidityChunk) {

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {
```

- *TokenId.sol* ( [87-87](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L87-L87), [96-96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L96-L96), [108-108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L108-L108), [118-118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L118-L118), [128-128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L128-L128), [138-138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L138-L138), [148-148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L148-L148), [158-158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L158-L158), [169-169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L169-L169), [183-183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L183-L183), [193-193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L193-L193), [205-209](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L205-L209), [221-225](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L221-L225), [240-244](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L240-L244), [255-259](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L255-L259), [273-277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L273-L277), [291-295](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L291-L295), [310-314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L310-L314), [336-346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L336-L346), [366-366](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L366-L366), [404-404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L404-L404), [416-419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L416-L419), [432-432](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L432-L432), [464-464](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L464-L464), [500-500](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L500-L500), [578-578](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L578-L578) ):

```solidity
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
206:         TokenId self,
207:         uint256 _asset,
208:         uint256 legIndex
209:     ) internal pure returns (TokenId) {

221:     function addOptionRatio(
222:         TokenId self,
223:         uint256 _optionRatio,
224:         uint256 legIndex
225:     ) internal pure returns (TokenId) {

240:     function addIsLong(
241:         TokenId self,
242:         uint256 _isLong,
243:         uint256 legIndex
244:     ) internal pure returns (TokenId) {

255:     function addTokenType(
256:         TokenId self,
257:         uint256 _tokenType,
258:         uint256 legIndex
259:     ) internal pure returns (TokenId) {

273:     function addRiskPartner(
274:         TokenId self,
275:         uint256 _riskPartner,
276:         uint256 legIndex
277:     ) internal pure returns (TokenId) {

291:     function addStrike(
292:         TokenId self,
293:         int24 _strike,
294:         uint256 legIndex
295:     ) internal pure returns (TokenId) {

310:     function addWidth(
311:         TokenId self,
312:         int24 _width,
313:         uint256 legIndex
314:     ) internal pure returns (TokenId) {

336:     function addLeg(
337:         TokenId self,
338:         uint256 legIndex,
339:         uint256 _optionRatio,
340:         uint256 _asset,
341:         uint256 _isLong,
342:         uint256 _tokenType,
343:         uint256 _riskPartner,
344:         int24 _strike,
345:         int24 _width
346:     ) internal pure returns (TokenId tokenId) {

366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

404:     function countLongs(TokenId self) internal pure returns (uint256) {

416:     function asTicks(
417:         TokenId self,
418:         uint256 legIndex
419:     ) internal pure returns (int24 legLowerTick, int24 legUpperTick) {

432:     function countLegs(TokenId self) internal pure returns (uint256) {

464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

500:     function validate(TokenId self) internal pure {

578:     function validateIsExercisable(TokenId self, int24 currentTick) internal pure {
```

</details>

### [N-03] Names of `private`/`internal` state variables should be prefixed with an underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

<details>
<summary>There are 75 instances (click to show):</summary>

- *CollateralTracker.sol* ( [70-70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L70-L70), [73-73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L73-L73), [77-77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L77-L77), [81-81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L81-L81), [89-89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L89-L89), [93-93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L93-L93), [96-96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L96-L96), [99-99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L99-L99), [102-102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L102-L102), [109-109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L109-L109), [112-112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L112-L112), [115-115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L115-L115), [121-121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L121-L121), [124-124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L124-L124), [131-131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L131-L131), [136-136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L136-L136), [141-141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L141-L141), [145-145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L145-L145), [149-149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L149-L149), [154-154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L154-L154), [158-158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L158-L158), [162-162](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L162-L162) ):

```solidity
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

- *PanopticFactory.sol* ( [63-63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L63-L63), [66-66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L66-L66), [69-69](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L69-L69), [72-72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L72-L72), [75-75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L75-L75), [78-78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L78-L78), [82-82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L82-L82), [86-86](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L86-L86), [89-89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L89-L89), [96-96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L96-L96), [99-99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L99-L99), [102-102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L102-L102) ):

```solidity
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

- *PanopticPool.sol* ( [103-103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L103-L103), [105-105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L105-L105), [109-109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L109-L109), [111-111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L111-L111), [114-114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L114-L114), [119-119](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L119-L119), [120-120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L120-L120), [123-123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L123-L123), [128-128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L128-L128), [133-133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L133-L133), [136-136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L136-L136), [139-139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L139-L139), [145-145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L145-L145), [148-148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L148-L148), [152-152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L152-L152), [156-156](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L156-L156), [160-160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L160-L160), [165-165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L165-L165), [168-168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L168-L168), [171-171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L171-L171), [174-174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L174-L174), [179-179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L179-L179), [186-186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L186-L186), [225-225](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L225-L225), [231-231](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L231-L231), [233-233](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L233-L233), [238-239](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L238-L239), [245-245](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L245-L245), [251-251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L251-L251), [258-259](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L258-L259), [272-272](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L272-L272) ):

```solidity
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
239:         internal s_options;

245:     mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

251:     mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;

258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
259:         internal s_positionBalance;

272:     mapping(address account => uint256 positionsHash) internal s_positionsHash;
```

- *SemiFungiblePositionManager.sol* ( [125-125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L125-L125), [126-126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L126-L126), [133-133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L133-L133), [137-137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L137-L137), [145-145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L145-L145), [150-150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L150-L150), [177-178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L177-L178), [287-287](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L287-L287), [289-289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L289-L289), [295-295](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L295-L295) ):

```solidity
125:     bool internal constant MINT = false;

126:     bool internal constant BURN = true;

133:     uint128 private constant VEGOID = 2;

137:     IUniswapV3Factory internal immutable FACTORY;

145:     mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;

150:     mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;

177:     mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
178:         internal s_accountLiquidity;

287:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

295:     mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;
```

</details>

### [N-04] Use of `override` is unnecessary

[Starting from Solidity 0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), the override keyword is not required when overriding an interface function, except for the case where the function is defined in multiple bases.

<details>
<summary>There are 4 instances (click to show):</summary>

- *CollateralTracker.sol* ( [323-326](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L323-L326), [341-345](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L341-L345) ):

```solidity
323:     function transfer(
324:         address recipient,
325:         uint256 amount
326:     ) public override(ERC20Minimal) returns (bool) {

341:     function transferFrom(
342:         address from,
343:         address to,
344:         uint256 amount
345:     ) public override(ERC20Minimal) returns (bool) {
```

- *SemiFungiblePositionManager.sol* ( [540-546](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L540-L546), [566-572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L566-L572) ):

```solidity
540:     function safeTransferFrom(
541:         address from,
542:         address to,
543:         uint256 id,
544:         uint256 amount,
545:         bytes calldata data
546:     ) public override {

566:     function safeBatchTransferFrom(
567:         address from,
568:         address to,
569:         uint256[] calldata ids,
570:         uint256[] calldata amounts,
571:         bytes calldata data
572:     ) public override {
```

</details>

### [N-05] Custom errors should be used rather than `revert()`/`require()`

Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in try-catch blocks, and are easier to re-use and maintain.

There are 9 instances:

- *Math.sol* ( [361-361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L361-L361), [370-370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L370-L370), [448-448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L448-L448), [484-484](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L484-L484), [547-547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L547-L547), [588-588](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L588-L588), [624-624](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L624-L624), [665-665](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L665-L665), [701-701](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L701-L701) ):

```solidity
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

### [N-06] Add inline comments for unnamed parameters

`function func(address a, address)` -> `function func(address a, address /* b */)`

There are 2 instances:

- *CollateralTracker.sol* ( [392-392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392-L392), [444-444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444-L444) ):

```solidity
392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

444:     function maxMint(address) external view returns (uint256 maxShares) {
```

### [N-07] Assembly blocks should have extensive comments

Assembly blocks take a lot more time to audit than normal Solidity code, and often have gotchas and side-effects that the Solidity versions of the same code do not. Consider adding more comments explaining what is being done in every step of the assembly code, and describe why assembly is being used instead of Solidity.

<details>
<summary>There are 21 instances (click to show):</summary>

- *Math.sol* ( [353-357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L353-L357), [362-364](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L362-L364), [379-381](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L379-L381), [383-386](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L383-L386), [393-395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L393-L395), [398-400](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L398-L400), [404-406](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L404-L406), [467-471](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L467-L471), [493-495](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L493-L495), [497-500](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L497-L500), [530-534](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L530-L534), [556-558](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L556-L558), [560-563](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L560-L563), [607-611](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L607-L611), [633-635](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L633-L635), [637-640](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L637-L640), [684-688](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L684-L688), [710-712](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L710-L712), [714-717](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L714-L717), [739-741](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L739-L741) ):

```solidity
353:             assembly ("memory-safe") {
354:                 let mm := mulmod(a, b, not(0))
355:                 prod0 := mul(a, b)
356:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
357:             }

362:                 assembly ("memory-safe") {
363:                     result := div(prod0, denominator)
364:                 }

379:             assembly ("memory-safe") {
380:                 remainder := mulmod(a, b, denominator)
381:             }

383:             assembly ("memory-safe") {
384:                 prod1 := sub(prod1, gt(remainder, prod0))
385:                 prod0 := sub(prod0, remainder)
386:             }

393:             assembly ("memory-safe") {
394:                 denominator := div(denominator, twos)
395:             }

398:             assembly ("memory-safe") {
399:                 prod0 := div(prod0, twos)
400:             }

404:             assembly ("memory-safe") {
405:                 twos := add(div(sub(0, twos), twos), 1)
406:             }

467:             assembly ("memory-safe") {
468:                 let mm := mulmod(a, b, not(0))
469:                 prod0 := mul(a, b)
470:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
471:             }

493:             assembly ("memory-safe") {
494:                 remainder := mulmod(a, b, 0x10000000000000000)
495:             }

497:             assembly ("memory-safe") {
498:                 prod1 := sub(prod1, gt(remainder, prod0))
499:                 prod0 := sub(prod0, remainder)
500:             }

530:             assembly ("memory-safe") {
531:                 let mm := mulmod(a, b, not(0))
532:                 prod0 := mul(a, b)
533:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
534:             }

556:             assembly ("memory-safe") {
557:                 remainder := mulmod(a, b, 0x1000000000000000000000000)
558:             }

560:             assembly ("memory-safe") {
561:                 prod1 := sub(prod1, gt(remainder, prod0))
562:                 prod0 := sub(prod0, remainder)
563:             }

607:             assembly ("memory-safe") {
608:                 let mm := mulmod(a, b, not(0))
609:                 prod0 := mul(a, b)
610:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
611:             }

633:             assembly ("memory-safe") {
634:                 remainder := mulmod(a, b, 0x100000000000000000000000000000000)
635:             }

637:             assembly ("memory-safe") {
638:                 prod1 := sub(prod1, gt(remainder, prod0))
639:                 prod0 := sub(prod0, remainder)
640:             }

684:             assembly ("memory-safe") {
685:                 let mm := mulmod(a, b, not(0))
686:                 prod0 := mul(a, b)
687:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
688:             }

710:             assembly ("memory-safe") {
711:                 remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)
712:             }

714:             assembly ("memory-safe") {
715:                 prod1 := sub(prod1, gt(remainder, prod0))
716:                 prod0 := sub(prod0, remainder)
717:             }

739:         assembly ("memory-safe") {
740:             result := add(div(a, b), gt(mod(a, b), 0))
741:         }
```

- *Multicall.sol* ( [25-27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L25-L27) ):

```solidity
25:                 assembly ("memory-safe") {
26:                     revert(add(result, 32), mload(result))
27:                 }
```

</details>

### [N-08] Consider splitting complex checks into multiple steps

Assign the expression's parts to intermediate local variables, and check against those instead.

There are 2 instances:

- *CollateralTracker.sol* ( [1060-1060](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1060-L1060) ):

```solidity
1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {
```

- *TokenId.sol* ( [566-566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L566-L566) ):

```solidity
566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))
```

### [N-09] Complex casting

Consider whether the number of casts is really necessary, or whether using a different type would be more appropriate. Alternatively, add comments to explain in detail why the casts are necessary, and any implicit reasons why the cast does not introduce an overflow.

<details>
<summary>There are 20 instances (click to show):</summary>

- *CollateralTracker.sol* ( [667-674](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L667-L674), [959-959](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L959-L959), [1029-1029](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1029-L1029), [1085-1085](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1085-L1085), [1119-1124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1119-L1124), [1637-1637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1637-L1637), [1638-1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1638-L1638) ):

```solidity
667:                     int24 range = int24(
668:                         int256(
669:                             Math.unsafeDivRoundingUp(
670:                                 uint24(positionId.width(leg) * positionId.tickSpacing()),
671:                                 2
672:                             )
673:                         )
674:                     );

959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

1119:             exchangedAmount += int256(
1120:                 Math.unsafeDivRoundingUp(
1121:                     uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
1122:                     DECIMALS
1123:                 )
1124:             );

1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
```

- *PanopticPool.sol* ( [730-730](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L730-L730), [1144-1144](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1144-L1144), [1149-1149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1149-L1149), [1932-1946](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1932-L1946), [1949-1963](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1949-L1963) ):

```solidity
730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

1144:             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)

1149:             uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)

1932:                                     uint128(
1933:                                         uint256(
1934:                                             Math.max(
1935:                                                 (int256(
1936:                                                     grossPremiumLast.rightSlot() *
1937:                                                         totalLiquidityBefore
1938:                                                 ) -
1939:                                                     int256(
1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941:                                                             positionLiquidity
1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),
1943:                                                 0
1944:                                             )
1945:                                         ) / totalLiquidity
1946:                                     )

1949:                                     uint128(
1950:                                         uint256(
1951:                                             Math.max(
1952:                                                 (int256(
1953:                                                     grossPremiumLast.leftSlot() *
1954:                                                         totalLiquidityBefore
1955:                                                 ) -
1956:                                                     int256(
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958:                                                             positionLiquidity
1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960:                                                 0
1961:                                             )
1962:                                         ) / totalLiquidity
1963:                                     )
```

- *PanopticMath.sol* ( [139-142](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L139-L142), [178-178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L178-L178), [179-179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L179-L179), [187-189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L187-L189), [257-259](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L257-L259), [377-377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L377-L377), [937-941](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L937-L941), [955-959](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L955-L959) ):

```solidity
139:                     uint256(
140:                         (int256(observationIndex) - int256(i * period)) +
141:                             int256(observationCardinality)
142:                     ) % observationCardinality

178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

187:                         uint256(
188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)
189:                         ) % observationCardinality

257:                 twapMeasurement[i] = int24(
258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
259:                 );

377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

937:                             int128(
938:                                 int256(
939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
940:                                 ) + refundValues.leftSlot()
941:                             )

955:                             int128(
956:                                 int256(
957:                                     PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
958:                                 ) + refundValues.rightSlot()
959:                             )
```

</details>

### [N-10] Complex math should be split into multiple steps

Consider splitting long arithmetic calculations into multiple steps to improve the code readability.

<details>
<summary>There are 26 instances (click to show):</summary>

- *CollateralTracker.sol* ( [201-209](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L201-L209), [402-406](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L402-L406), [730-732](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L730-L732), [954-961](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L954-L961), [1362-1368](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1362-L1368), [1570-1572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1570-L1572), [1636-1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1636-L1638) ):

```solidity
201:             TICK_DEVIATION = uint256(
202:                 2230 +
203:                     (12500 * ratioTick) /
204:                     10_000 +
205:                     (7812 * ratioTick ** 2) /
206:                     10_000 ** 2 +
207:                     (6510 * ratioTick ** 3) /
208:                     10_000 ** 3
209:             );

402:             shares = Math.mulDiv(
403:                 assets * (DECIMALS - COMMISSION_FEE),
404:                 totalSupply,
405:                 totalAssets() * DECIMALS
406:             );

730:             exerciseFees = exerciseFees
731:                 .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))
732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

954:             _mint(
955:                 delegator,
956:                 Math.mulDiv(
957:                     assets,
958:                     totalSupply - delegateeBalance,
959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
960:                 ) - delegateeBalance
961:             );

1362:                     uint160 ratio = tokenType == 1 // tokenType
1363:                         ? Math.getSqrtRatioAtTick(
1364:                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)
1365:                         ) // puts ->  price/strike
1366:                         : Math.getSqrtRatioAtTick(
1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)
1368:                         ); // calls -> strike/price

1570:                 spreadRequirement = (notional < notionalP)
1571:                     ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)
1572:                     : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

1636:             poolUtilization =
1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +
1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
```

- *PanopticPool.sol* ( [308-314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L308-L314), [1545-1564](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1545-L1564), [1633-1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1633-L1636), [1725-1742](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1725-L1742), [1768-1769](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1768-L1769), [1770-1771](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1770-L1771), [1928-1968](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1928-L1968) ):

```solidity
308:             s_miniMedian =
309:                 (uint256(block.timestamp) << 216) +
310:                 // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
311:                 // see comment on s_miniMedian initialization for format of this magic number
312:                 (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4
314:                 (uint256(uint24(currentTick))); // add to slot 3

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

1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929:                             ? LeftRightUnsigned
1930:                                 .wrap(0)
1931:                                 .toRightSlot(
1932:                                     uint128(
1933:                                         uint256(
1934:                                             Math.max(
1935:                                                 (int256(
1936:                                                     grossPremiumLast.rightSlot() *
1937:                                                         totalLiquidityBefore
1938:                                                 ) -
1939:                                                     int256(
1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941:                                                             positionLiquidity
1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),
1943:                                                 0
1944:                                             )
1945:                                         ) / totalLiquidity
1946:                                     )
1947:                                 )
1948:                                 .toLeftSlot(
1949:                                     uint128(
1950:                                         uint256(
1951:                                             Math.max(
1952:                                                 (int256(
1953:                                                     grossPremiumLast.leftSlot() *
1954:                                                         totalLiquidityBefore
1955:                                                 ) -
1956:                                                     int256(
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958:                                                             positionLiquidity
1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960:                                                 0
1961:                                             )
1962:                                         ) / totalLiquidity
1963:                                     )
1964:                                 )
1965:                             : LeftRightUnsigned
1966:                                 .wrap(0)
1967:                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
```

- *SemiFungiblePositionManager.sol* ( [1350-1354](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1350-L1354), [1355-1359](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1355-L1359), [1388-1391](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1388-L1391) ):

```solidity
1350:                 premium0X64_base = Math.mulDiv(
1351:                     collected0,
1352:                     totalLiquidity * 2 ** 64,
1353:                     netLiquidity ** 2
1354:                 );

1355:                 premium1X64_base = Math.mulDiv(
1356:                     collected1,
1357:                     totalLiquidity * 2 ** 64,
1358:                     netLiquidity ** 2
1359:                 );

1388:                     uint256 numerator = totalLiquidity ** 2 -
1389:                         totalLiquidity *
1390:                         removedLiquidity +
1391:                         ((removedLiquidity ** 2) / 2 ** (VEGOID));
```

- *PanopticMath.sol* ( [138-143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L138-L143), [149-151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L149-L151), [177-180](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L177-L180), [223-223](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L223-L223), [226-230](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L226-L230), [257-259](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L257-L259), [475-477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L475-L477), [802-817](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L802-L817), [826-841](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L826-L841) ):

```solidity
138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
139:                     uint256(
140:                         (int256(observationIndex) - int256(i * period)) +
141:                             int256(observationCardinality)
142:                     ) % observationCardinality
143:                 );

149:                 ticks[i] =
150:                     (tickCumulatives[i] - tickCumulatives[i + 1]) /
151:                     int256(timestamps[i] - timestamps[i + 1]);

177:             medianTick =
178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
180:                 2;

223:                     newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));

226:                 updatedMedianData =
227:                     (block.timestamp << 216) +
228:                     (uint256(newOrderMap) << 192) +
229:                     uint256(uint192(medianData << 24)) +
230:                     uint256(uint24(lastObservedTick));

257:                 twapMeasurement[i] = int24(
258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
259:                 );

475:             uint256 notional = asset == 0
476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))
477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

802:                 (collateralDelta0, collateralDelta1) = (
803:                     -Math.min(
804:                         collateralDelta0 - longPremium.rightSlot(),
805:                         PanopticMath.convert1to0(
806:                             longPremium.leftSlot() - collateralDelta1,
807:                             sqrtPriceX96Final
808:                         )
809:                     ),
810:                     Math.min(
811:                         longPremium.leftSlot() - collateralDelta1,
812:                         PanopticMath.convert0to1(
813:                             collateralDelta0 - longPremium.rightSlot(),
814:                             sqrtPriceX96Final
815:                         )
816:                     )
817:                 );

826:                 (collateralDelta0, collateralDelta1) = (
827:                     Math.min(
828:                         longPremium.rightSlot() - collateralDelta0,
829:                         PanopticMath.convert1to0(
830:                             collateralDelta1 - longPremium.leftSlot(),
831:                             sqrtPriceX96Final
832:                         )
833:                     ),
834:                     -Math.min(
835:                         collateralDelta1 - longPremium.leftSlot(),
836:                         PanopticMath.convert0to1(
837:                             longPremium.rightSlot() - collateralDelta0,
838:                             sqrtPriceX96Final
839:                         )
840:                     )
841:                 );
```

</details>

### [N-11] Consider adding a block/deny-list

Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens

There are 3 instances:

- *CollateralTracker.sol* ( [36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36) ):

```solidity
36: contract CollateralTracker is ERC20Minimal, Multicall {
```

- *PanopticFactory.sol* ( [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L26) ):

```solidity
26: contract PanopticFactory is Multicall {
```

- *SemiFungiblePositionManager.sol* ( [72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L72) ):

```solidity
72: contract SemiFungiblePositionManager is ERC1155, Multicall {
```

### [N-12] Constants/Immutables redefined elsewhere

Consider defining in only one contract so that values cannot become out of sync when only one location is updated. A [cheap way](https://medium.com/coinmonks/gas-cost-of-solidity-library-functions-dbe0cedd4678) to store constants/immutables in a single location is to create an `internal constant` in a `library`. If the variable is a local cache of another contract's value, consider making the cache variable internal or private, which will require external users to query the contract with the source of truth, so that callers don't get out of sync.

There are 4 instances:

- *PanopticFactory.sol* ( [66-66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L66-L66) ):

```solidity
/// @audit Seen in ./contracts/PanopticPool.sol#179
66:     SemiFungiblePositionManager internal immutable SFPM;
```

- *PanopticPool.sol* ( [179-179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L179-L179) ):

```solidity
/// @audit Seen in ./contracts/PanopticFactory.sol#66
179:     SemiFungiblePositionManager internal immutable SFPM;
```

- *Math.sol* ( [15-15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L15-L15) ):

```solidity
/// @audit Seen in ./contracts/libraries/PanopticMath.sol#23
15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```

- *PanopticMath.sol* ( [23-23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L23-L23) ):

```solidity
/// @audit Seen in ./contracts/libraries/Math.sol#15
23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```

### [N-13] Convert simple `if`-statements to ternary expressions

Converting some if statements to ternaries (such as `z = (a < b) ? x : y`) can make the code more concise and easier to read.

There are 2 instances:

- *CollateralTracker.sol* ( [1544-1552](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1544-L1552) ):

```solidity
1544:                 if (tokenType == 0) {
1545:                     spreadRequirement = movedRight < movedPartnerRight
1546:                         ? movedPartnerRight - movedRight
1547:                         : movedRight - movedPartnerRight;
1548:                 } else {
1549:                     spreadRequirement = movedLeft < movedPartnerLeft
1550:                         ? movedPartnerLeft - movedLeft
1551:                         : movedLeft - movedPartnerLeft;
1552:                 }
```

- *TokenId.sol* ( [382-386](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L382-L386) ):

```solidity
382:             } else if (optionRatios < 2 ** 208) {
383:                 optionRatios = 3;
384:             } else {
385:                 optionRatios = 4;
386:             }
```

### [N-14] Contract name does not match its filename

According to the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#contract-and-library-names), contract and library names should also match their filenames.

There are 4 instances:

- *ERC1155Minimal.sol* ( [11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L11) ):

```solidity
/// @audit Not match filename `ERC1155Minimal.sol`
11: abstract contract ERC1155 {
```

- *LeftRight.sol* ( [17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L17) ):

```solidity
/// @audit Not match filename `LeftRight.sol`
17: library LeftRightLibrary {
```

- *LiquidityChunk.sol* ( [52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L52) ):

```solidity
/// @audit Not match filename `LiquidityChunk.sol`
52: library LiquidityChunkLibrary {
```

- *TokenId.sol* ( [60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L60) ):

```solidity
/// @audit Not match filename `TokenId.sol`
60: library TokenIdLibrary {
```

### [N-15] UPPER_CASE names should be reserved for `constant`/`immutable` variables

If the variable needs to be different based on which class it comes from, a `view`/`pure` _function_ should be used instead (e.g. like [this](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59)).

There are 2 instances:

- *PanopticFactory.sol* ( [116](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L116), [117](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L117) ):

```solidity
116:         address _WETH9,

117:         SemiFungiblePositionManager _SFPM,
```

### [N-16] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

<details>
<summary>There are 4 instances (click to show):</summary>

- *CollateralTracker.sol* ( [178-186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178-L186) ):

```solidity
178:     constructor(
179:         uint256 _commissionFee,
180:         uint256 _sellerCollateralRatio,
181:         uint256 _buyerCollateralRatio,
182:         int256 _forceExerciseCost,
183:         uint256 _targetPoolUtilization,
184:         uint256 _saturatedPoolUtilization,
185:         uint256 _ITMSpreadMultiplier
186:     ) {
```

- *PanopticFactory.sol* ( [115-122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L115-L122) ):

```solidity
115:     constructor(
116:         address _WETH9,
117:         SemiFungiblePositionManager _SFPM,
118:         IUniswapV3Factory _univ3Factory,
119:         IDonorNFT _donorNFT,
120:         address _poolReference,
121:         address _collateralReference
122:     ) {
```

- *PanopticPool.sol* ( [280-280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L280-L280) ):

```solidity
280:     constructor(SemiFungiblePositionManager _sfpm) {
```

- *SemiFungiblePositionManager.sol* ( [341-341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L341-L341) ):

```solidity
341:     constructor(IUniswapV3Factory _factory) {
```

</details>

### [N-17] Events are emitted without the sender information

When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the `msg.sender` the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

There are 3 instances:

- *PanopticFactory.sol* ( [268-275](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L268-L275) ):

```solidity
268:         emit PoolDeployed(
269:             newPoolContract,
270:             v3Pool,
271:             collateralTracker0,
272:             collateralTracker1,
273:             amount0,
274:             amount1
275:         );
```

- *PanopticPool.sol* ( [1654-1654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1654-L1654) ):

```solidity
1654:             emit PremiumSettled(owner, tokenId, realizedPremia);
```

- *SemiFungiblePositionManager.sol* ( [390-390](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L390-L390) ):

```solidity
390:         emit PoolInitialized(univ3pool, poolId);
```

### [N-18] Inconsistent floating version pragma

Source files are using different floating version syntax, this is prone to compilation errors, and is not conducive to the code reliability and maintainability.

There are 2 instances:

- *CollateralTracker.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *CallbackLib.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

### [N-19] Contract implements interface without extending the interface

Not extending the interface may lead to the wrong function signature being used, leading to unexpected behavior. If the interface is in fact being implemented, use the `override` keyword to indicate that fact.

There is 1 instance:

- *ERC1155Minimal.sol* ( [11-21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L11-L21) ):

```solidity
/// @audit IERC165
11: abstract contract ERC1155 {
12:     /*//////////////////////////////////////////////////////////////
13:                                  EVENTS
14:     //////////////////////////////////////////////////////////////*/
15: 
16:     /// @notice Emitted when only a single token is transferred.
17:     /// @param operator The user who initiated the transfer
18:     /// @param from The user who sent the tokens
19:     /// @param to The user who received the tokens
20:     /// @param id The ERC1155 token id
21:     /// @param amount The amount of tokens transferred
```

### [N-20] Imports could be organized more systematically

The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

There are 4 instances:

- *PanopticFactory.sol* ( [8-8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L8-L8) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import {IDonorNFT} from "@contracts/tokens/interfaces/IDonorNFT.sol";
```

- *PanopticPool.sol* ( [7-7](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";
```

- *InteractionHelper.sol* ( [6-6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";
```

- *PanopticMath.sol* ( [6-6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";
```

### [N-21] There is no need to initialize bool variables with `false`

Since the bool variables are automatically set to `false` when created, it is redundant to initialize it with `false` again.

There are 5 instances:

- *PanopticPool.sol* ( [111-111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L111-L111), [114-114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L114-L114), [120-120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L120-L120), [133-133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L133-L133) ):

```solidity
111:     bool internal constant COMPUTE_LONG_PREMIA = false;

114:     bool internal constant ONLY_AVAILABLE_PREMIUM = false;

120:     bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

133:     bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;
```

- *SemiFungiblePositionManager.sol* ( [125-125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L125-L125) ):

```solidity
125:     bool internal constant MINT = false;
```

### [N-22] Invalid NatSpec comment style

NatSpec comment in solidity should use `///` or `/* ... */` syntax.

There are 6 instances:

- *SemiFungiblePositionManager.sol* ( [358-358](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L358-L358), [360-360](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L360-L360), [603-603](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L603-L603), [836-836](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L836-L836), [903-903](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L903-L903) ):

```solidity
358:         // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting

360:         // @dev some pools may not be deployable if the poolId has a collision (since we take only 8 bytes)

603:             // @dev see `contracts/types/LiquidityChunk.sol`

836:             // @dev note this triggers our swap callback function

903:                 // @dev see `contracts/types/LiquidityChunk.sol`
```

- *PanopticMath.sol* ( [98-98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L98-L98) ):

```solidity
98:         // @dev 0 ^ x = x
```

### [N-23] @openzeppelin/contracts should be upgraded to a newer version

These contracts import contracts from `@openzeppelin/contracts`, but they are not using [the latest version](https://github.com/OpenZeppelin/openzeppelin-contracts/releases). Using the latest version ensures contract security with fixes for known vulnerabilities, access to the latest feature updates, and enhanced community support and engagement.

The imported version is `4.8.3`.

There are 5 instances:

- *PanopticFactory.sol* ( [14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L14) ):

```solidity
14: import {Clones} from "@openzeppelin/contracts/proxy/Clones.sol";
```

- *PanopticPool.sol* ( [9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L9) ):

```solidity
9: import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```

- *InteractionHelper.sol* ( [6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L6), [10](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L10) ):

```solidity
6: import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

10: import {Strings} from "@openzeppelin/contracts/utils/Strings.sol";
```

- *ERC1155Minimal.sol* ( [5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L5) ):

```solidity
5: import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```

### [N-24] Lib @uniswap/v3-core should be upgraded to a newer version

These contracts import contracts from lib @uniswap/v3-core, but they are not using [the latest version](https://github.com/Uniswap/v3-core).

The imported version is `1.0.1-solc-0.8`.

There is 1 instance:

- Global finding

### [N-25] Lib @uniswap/v3-periphery should be upgraded to a newer version

These contracts import contracts from lib @uniswap/v3-periphery, but they are not using [the latest version](https://github.com/Uniswap/v3-periphery).

The imported version is `1.4.2-solc-0.8`.

There is 1 instance:

- Global finding

### [N-26] Expressions for constant values should use `immutable` rather than `constant`

While it doesn't save any gas because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.

There are 3 instances:

- *PanopticPool.sol* ( [103-103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L103-L103), [105-105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L105-L105), [165-165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L165-L165) ):

```solidity
103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);
```

### [N-27] Consider moving duplicated strings to constants

Moving duplicate strings to constants can improve code maintainability and readability.

There are 5 instances:

- *InteractionHelper.sol* ( [63-63](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L63-L63), [68-68](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L68-L68), [74-74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L74-L74), [80-80](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L80-L80), [100-100](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L100-L100) ):

```solidity
63:             symbol0 = "???";

68:             symbol1 = "???";

74:                     " ",

80:                     " ",

100:             return string.concat(prefix, "???");
```

### [N-28] Contract uses both `require()`/`revert()` as well as custom errors

Consider using just one method in a single file.

There is 1 instance:

- *Math.sol* ( [13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L13) ):

```solidity
13: library Math {
```

### [N-29] Functions should be named in mixedCase style

As the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.21/style-guide.html#function-names) suggests: functions should be named in mixedCase style.

<details>
<summary>There are 11 instances (click to show):</summary>

- *PanopticPool.sol* ( [677](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L677), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1450) ):

```solidity
677:     function _mintInSFPMAndUpdateCollateral(

1450:     function getUniV3TWAP() internal view returns (int24 twapTick) {
```

- *SemiFungiblePositionManager.sol* ( [350](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L350), [680](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L680), [756](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L756), [863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L863), [958](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L958) ):

```solidity
350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

680:     function _validateAndForwardToAMM(

756:     function swapInAMM(

863:     function _createPositionInAMM(

958:     function _createLegInAMM(
```

- *FeesCalc.sol* ( [97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L97), [130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L130) ):

```solidity
97:     function calculateAMMSwapFees(

130:     function _getAMMSwapFeesPerLiquidityCollected(
```

- *PanopticMath.sol* ( [607](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L607) ):

```solidity
607:     function _calculateIOAmounts(
```

- *IDonorNFT.sol* ( [13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L13) ):

```solidity
13:     function issueNFT(
```

</details>

### [N-30] Modifiers should be named in mixedCase style

As the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#modifier-names) suggests: modifiers should be named in mixedCase style. Use mixedCase. Examples: `onlyBy`, `onlyAfter`, `onlyDuringThePreSale`.

There is 1 instance:

- *SemiFungiblePositionManager.sol* ( [305](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L305) ):

```solidity
305:     modifier ReentrancyLock(uint64 poolId) {
```

### [N-31] Constants should be put on the left side of comparisons

Putting constants on the left side of comparison statements is a best practice known as [Yoda conditions](https://en.wikipedia.org/wiki/Yoda_conditions).
Although solidity's static typing system prevents accidental assignments within conditionals, adopting this practice can improve code readability and consistency, especially when working across multiple languages.

<details>
<summary>There are 78 instances (click to show):</summary>

- *CollateralTracker.sol* ( [708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L708), [709](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L709), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1060), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1060), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1060), [1107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1107), [1325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1325), [1328](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1328), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1339), [1346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1346), [1347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1347), [1362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1362), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1374), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1375), [1451](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1451), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1479), [1488](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1488), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1544), [1559](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1559), [1582](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1582), [1584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1584), [1637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1638) ):

```solidity
/// @audit put `0` on the left
708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

/// @audit put `1` on the left
709:                     (tokenType == 1 && currentValue0 < oracleValue0)

/// @audit put `0` on the left
1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

/// @audit put `0` on the left
1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

/// @audit put `0` on the left
1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

/// @audit put `0` on the left
1107:             if (intrinsicValue != 0) {

/// @audit put `0` on the left
1325:         uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();

/// @audit put `0` on the left
1328:         int64 utilization = tokenType == 0

/// @audit put `0` on the left
1339:             if (isLong == 0) {

/// @audit put `1` on the left
1346:                     ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1

/// @audit put `0` on the left
1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

/// @audit put `1` on the left
1362:                     uint160 ratio = tokenType == 1 // tokenType

/// @audit put `1` on the left
1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

/// @audit put `0` on the left
1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

/// @audit put `1` on the left
1451:             if (isLong == 1) {

/// @audit put `0` on the left
1479:         if (isLong == 0) {

/// @audit put `1` on the left
1488:         } else if (isLong == 1) {

/// @audit put `0` on the left
1544:                 if (tokenType == 0) {

/// @audit put `1` on the left
1559:                 if (tokenType == 1) {

/// @audit put `0` on the left
1582:                 tokenType == 0 ? movedRight : movedLeft,

/// @audit put `0` on the left
1584:                 tokenType == 0

/// @audit put `0` on the left
1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

/// @audit put `0` on the left
1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
```

- *PanopticFactory.sol* ( [224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L224) ):

```solidity
/// @audit put `address(0)` on the left
224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();
```

- *PanopticPool.sol* ( [533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L533), [664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L664), [768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L768), [1188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1188), [1483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1483), [1520](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1520), [1566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1566), [1780](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1780), [1789](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1789), [1928](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1928) ):

```solidity
/// @audit put `0` on the left
533:         if (medianData != 0) s_miniMedian = medianData;

/// @audit put `0` on the left
664:         if (medianData != 0) s_miniMedian = medianData;

/// @audit put `1` on the left
768:             if (isLong == 1) {

/// @audit put `1` on the left
1188:         if (touchedId.length != 1) revert Errors.InputListFail();

/// @audit put `0` on the left
1483:         if (netLiquidity == 0) return;

/// @audit put `1` on the left
1520:             if ((isLong == 1) || computeAllPremia) {

/// @audit put `1` on the left
1566:                     if (isLong == 1) {

/// @audit put `0` on the left
1780:                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),

/// @audit put `0` on the left
1789:                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),

/// @audit put `0` on the left
1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0
```

- *SemiFungiblePositionManager.sol* ( [355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L355), [362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L362), [688](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L688), [702](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L702), [787](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L787), [787](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L787), [823](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L823), [833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L833), [999](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L999), [1066](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1066), [1073](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1073), [1078](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1078), [1275](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1275), [1469](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1469), [1514](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1514), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1518) ):

```solidity
/// @audit put `address(0)` on the left
355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

/// @audit put `0` on the left
362:         if (s_AddrToPoolIdData[univ3pool] != 0) return;

/// @audit put `0` on the left
688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

/// @audit put `IUniswapV3Pool(address(0))` on the left
702:         if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

/// @audit put `0` on the left
787:             if ((itm0 != 0) && (itm1 != 0)) {

/// @audit put `0` on the left
787:             if ((itm0 != 0) && (itm1 != 0)) {

/// @audit put `0` on the left
823:             } else if (itm0 != 0) {

/// @audit put `0` on the left
833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

/// @audit put `0` on the left
999:             if (isLong == 0) {

/// @audit put `0` on the left
1066:             moved = isLong == 0

/// @audit put `1` on the left
1073:             if (tokenType == 1) {

/// @audit put `0` on the left
1078:             if (tokenType == 0) {

/// @audit put `1` on the left
1275:         if (isLong == 1) {

/// @audit put `0` on the left
1469:             if (netLiquidity != 0) {

/// @audit put `1` on the left
1514:                 acctPremia = isLong == 1 ? premiumOwed : premiumGross;

/// @audit put `1` on the left
1518:             acctPremia = isLong == 1
```

- *Math.sol* ( [93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L93), [97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L97), [101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L109), [113](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L113), [360](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L360), [474](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L474), [537](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L537), [614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L614), [691](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L691) ):

```solidity
/// @audit put `0x100000000000000000000000000000000` on the left
93:             if (x >= 0x100000000000000000000000000000000) {

/// @audit put `0x10000000000000000` on the left
97:             if (x >= 0x10000000000000000) {

/// @audit put `0x100000000` on the left
101:             if (x >= 0x100000000) {

/// @audit put `0x10000` on the left
105:             if (x >= 0x10000) {

/// @audit put `0x100` on the left
109:             if (x >= 0x100) {

/// @audit put `0x10` on the left
113:             if (x >= 0x10) {

/// @audit put `0` on the left
360:             if (prod1 == 0) {

/// @audit put `0` on the left
474:             if (prod1 == 0) {

/// @audit put `0` on the left
537:             if (prod1 == 0) {

/// @audit put `0` on the left
614:             if (prod1 == 0) {

/// @audit put `0` on the left
691:             if (prod1 == 0) {
```

- *PanopticMath.sol* ( [77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L77), [211](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L211), [425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L425), [475](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L475), [479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L479), [856](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L857) ):

```solidity
/// @audit put `address(0)` on the left
77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

/// @audit put `7` on the left
211:                     if (rank == 7) {

/// @audit put `0` on the left
425:         if (tokenType == 0) {

/// @audit put `0` on the left
475:             uint256 notional = asset == 0

/// @audit put `0` on the left
479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

/// @audit put `0` on the left
856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

/// @audit put `0` on the left
857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
```

- *ERC1155Minimal.sol* ( [112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L112), [163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L163), [202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L203), [222](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L222) ):

```solidity
/// @audit put `0` on the left
112:         if (to.code.length != 0) {

/// @audit put `0` on the left
163:         if (to.code.length != 0) {

/// @audit put `0x01ffc9a7` on the left
202:             interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

/// @audit put `0xd9b67a26` on the left
203:             interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

/// @audit put `0` on the left
222:         if (to.code.length != 0) {
```

- *TokenId.sol* ( [465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L465), [471](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L471), [477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L477), [483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L483), [566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L566) ):

```solidity
/// @audit put `0` on the left
465:         if (i == 0)

/// @audit put `1` on the left
471:         if (i == 1)

/// @audit put `2` on the left
477:         if (i == 2)

/// @audit put `3` on the left
483:         if (i == 3)

/// @audit put `1` on the left
566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))
```

</details>

### [N-32] `else`-block not required

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

<details>
<summary>There are 10 instances (click to show):</summary>

- *SemiFungiblePositionManager.sol* ( [1013-1019](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1013-L1019) ):

```solidity
1013:                 if (startingLiquidity < chunkLiquidity) {
1014:                     // the amount we want to move (liquidityChunk.legLiquidity()) out of uniswap is greater than
1015:                     // what the account that owns the liquidity in uniswap has (startingLiquidity)
1016:                     // we must ensure that an account can only move its own liquidity out of uniswap
1017:                     // so we revert in this case
1018:                     revert Errors.NotEnoughLiquidity();
1019:                 } else {
```

- *PanopticMath.sol* ( [325-327](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L325-L327), [425-430](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L425-L430), [494-496](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L494-L496), [511-513](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L511-L513), [528-533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L528-L533), [551-556](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L551-L556) ):

```solidity
325:         if (tokenId.asset(legIndex) == 0) {
326:             return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
327:         } else {

425:         if (tokenType == 0) {
426:             return (
427:                 tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
428:                 tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
429:             );
430:         } else {

494:             if (sqrtPriceX96 < type(uint128).max) {
495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
496:             } else {

511:             if (sqrtPriceX96 < type(uint128).max) {
512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
513:             } else {

528:             if (sqrtPriceX96 < type(uint128).max) {
529:                 int256 absResult = Math
530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
531:                     .toInt256();
532:                 return amount < 0 ? -absResult : absResult;
533:             } else {

551:             if (sqrtPriceX96 < type(uint128).max) {
552:                 int256 absResult = Math
553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
554:                     .toInt256();
555:                 return amount < 0 ? -absResult : absResult;
556:             } else {
```

- *TokenId.sol* ( [439-441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L439-L441), [441-443](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L441-L443), [443-445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L443-L445) ):

```solidity
439:         if (optionRatios < 2 ** 64) {
440:             return 0;
441:         } else if (optionRatios < 2 ** 112) {

441:         } else if (optionRatios < 2 ** 112) {
442:             return 1;
443:         } else if (optionRatios < 2 ** 160) {

443:         } else if (optionRatios < 2 ** 160) {
444:             return 2;
445:         } else if (optionRatios < 2 ** 208) {
```

</details>

### [N-33] Large multiples of ten should use scientific notation

Use a scientific notation rather than decimal literals (e.g. `1e6` instead of `1000000`), for better code readability.

<details>
<summary>There are 8 instances (click to show):</summary>

- *CollateralTracker.sol* ( [77-77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L77-L77), [81-81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L81-L81), [200-200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L200-L200), [204-204](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L204-L204), [206-206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L206-L206), [208-208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L208-L208) ):

```solidity
/// @audit 10_000 -> 1e4
77:     uint256 internal constant DECIMALS = 10_000;

/// @audit 10_000 -> 1e4
81:     int128 internal constant DECIMALS_128 = 10_000;

/// @audit 2000 -> 2e3
200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

/// @audit 10_000 -> 1e4
204:                     10_000 +

/// @audit 10_000 -> 1e4
206:                     10_000 ** 2 +

/// @audit 10_000 -> 1e4
208:                     10_000 ** 3
```

- *PanopticPool.sol* ( [174-174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L174-L174), [1329-1329](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1329-L1329) ):

```solidity
/// @audit 10_000 -> 1e4
174:     uint256 internal constant NO_BUFFER = 10_000;

/// @audit 10_000 -> 1e4
1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);
```

</details>

### [N-34] Non-interface files should use fixed compiler versions

To prevent the actual contracts being deployed from behaving differently depending on the compiler version, it is recommended to use fixed solidity versions for contracts and libraries.

Although we can configure a specific version through config (like hardhat, forge config files), it is recommended to **set the fixed version in the solidity pragma directly** before deploying to the mainnet.

<details>
<summary>There are 18 instances (click to show):</summary>

- *CollateralTracker.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *PanopticFactory.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *PanopticPool.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *SemiFungiblePositionManager.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *CallbackLib.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *Constants.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *Errors.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *FeesCalc.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *InteractionHelper.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *Math.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *PanopticMath.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *SafeTransferLib.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *Multicall.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *ERC1155Minimal.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *ERC20Minimal.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *LeftRight.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *LiquidityChunk.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *TokenId.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

</details>

### [N-35] High cyclomatic complexity

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

<details>
<summary>There are 2 instances (click to show):</summary>

- *CollateralTracker.sol* ( [1311-1422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1311-L1422) ):

```solidity
1311:     function _getRequiredCollateralSingleLegNoPartner(
1312:         TokenId tokenId,
1313:         uint256 index,
1314:         uint128 positionSize,
1315:         int24 atTick,
1316:         uint128 poolUtilization
1317:     ) internal view returns (uint256 required) {
1318:         // extract the tokenType (token0 or token1)
1319:         uint256 tokenType = tokenId.tokenType(index);
1320: 
1321:         // compute the total amount of funds moved for that position
1322:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);
1323: 
1324:         // amount moved is right slot if tokenType=0, left slot otherwise
1325:         uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();
1326: 
1327:         // match tokenType with the correct pool utilization
1328:         int64 utilization = tokenType == 0
1329:             ? int64(uint64(poolUtilization))
1330:             : int64(uint64(poolUtilization >> 64));
1331: 
1332:         uint256 isLong = tokenId.isLong(index);
1333: 
1334:         // start with base requirement, which is based on isLong value
1335:         required = _getRequiredCollateralAtUtilization(amountMoved, isLong, utilization);
...... OMITTED ......
1398: 
1399:                         // compute the tokens required
1400:                         // position is in-the-money, collateral requirement = amountMoved*(1-ratio) + SCR*amountMoved
1401:                         required += Math.mulDiv96RoundingUp(amountMoved, c2);
1402:                     } else {
1403:                         // position is in-range (ie. current tick is between upper+lower tick): we draw a line between the
1404:                         // collateral requirement at the lowerTick and the one at the upperTick. We use that interpolation as
1405:                         // the collateral requirement when in-range, which always over-estimates the amount of token required
1406:                         // Specifically:
1407:                         //  required = amountMoved * (scaleFactor - ratio) / (scaleFactor + 1) + sellCollateralRatio*amountMoved
1408:                         uint160 scaleFactor = Math.getSqrtRatioAtTick(
1409:                             (tickUpper - strike) + (strike - tickLower)
1410:                         );
1411:                         uint256 c3 = Math.mulDivRoundingUp(
1412:                             amountMoved,
1413:                             scaleFactor - ratio,
1414:                             scaleFactor + Constants.FP96
1415:                         );
1416:                         // position is in-the-money, collateral requirement = amountMoved*(1-SRC)*(scaleFactor-ratio)/(scaleFactor+1) + SCR*amountMoved
1417:                         required += c3;
1418:                     }
1419:                 }
1420:             }
1421:         }
1422:     }
```

- *SemiFungiblePositionManager.sol* ( [958-1104](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L958-L1104) ):

```solidity
958:     function _createLegInAMM(
959:         IUniswapV3Pool univ3pool,
960:         TokenId tokenId,
961:         uint256 leg,
962:         LiquidityChunk liquidityChunk,
963:         bool isBurn
964:     )
965:         internal
966:         returns (
967:             LeftRightSigned moved,
968:             LeftRightSigned itmAmounts,
969:             LeftRightUnsigned collectedSingleLeg
970:         )
971:     {
972:         uint256 tokenType = tokenId.tokenType(leg);
973:         // unique key to identify the liquidity chunk in this uniswap pool
974:         bytes32 positionKey = keccak256(
975:             abi.encodePacked(
976:                 address(univ3pool),
977:                 msg.sender,
978:                 tokenType,
979:                 liquidityChunk.tickLower(),
980:                 liquidityChunk.tickUpper()
981:             )
982:         );
...... OMITTED ......
1080:                 itmAmounts = itmAmounts.toLeftSlot(moved.leftSlot());
1081:             }
1082:         }
1083: 
1084:         // if there was liquidity at that tick before the transaction, collect any accumulated fees
1085:         if (currentLiquidity.rightSlot() > 0) {
1086:             collectedSingleLeg = _collectAndWritePositionData(
1087:                 liquidityChunk,
1088:                 univ3pool,
1089:                 currentLiquidity,
1090:                 positionKey,
1091:                 moved,
1092:                 isLong
1093:             );
1094:         }
1095: 
1096:         // position has been touched, update s_accountFeesBase with the latest values from the pool.positions
1097:         // round up the stored feesbase to minimize Δfeesbase when we next calculate it
1098:         s_accountFeesBase[positionKey] = _getFeesBase(
1099:             univ3pool,
1100:             updatedLiquidity,
1101:             liquidityChunk,
1102:             true
1103:         );
1104:     }
```

</details>

### [N-36] Typos

All typos should be corrected.

<details>
<summary>There are 17 instances (click to show):</summary>

- *CollateralTracker.sol* ( [92](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L92) ):

```solidity
/// @audit initalized
92:     /// @dev As each instance is deployed via proxy clone, initial parameters must only be initalized once via startToken().
```

- *PanopticPool.sol* ( [107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L107), [122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L122), [278](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L278) ):

```solidity
/// @audit caluculation
107:     // Flags used as arguments to premia caluculation functions

/// @audit wether
122:     /// @dev Boolean flag to determine wether a position is added (true) or not (!ADD = false)

/// @audit Mananger
278:     /// @notice During construction: sets the address of the panoptic factory smart contract and the SemiFungiblePositionMananger (SFPM).
```

- *SemiFungiblePositionManager.sol* ( [1106](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1106), [1337](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1337) ):

```solidity
/// @audit postion
1106:     /// @notice caches/stores the accumulated premia values for the specified postion.

/// @audit seperated
1337:         // premia, and is only seperated to simplify the calculation
```

- *Errors.sol* ( [62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L62) ):

```solidity
/// @audit avaiable
62:     /// @notice PanopticPool: there is not enough avaiable liquidity to buy an option
```

- *PanopticMath.sol* ( [486](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L486), [503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L503), [520](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L520), [543](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L543), [663](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L663), [886](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L886) ):

```solidity
/// @audit accomodate
486:     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of tick.s

/// @audit accomodate
503:     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.

/// @audit accomodate
520:     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.

/// @audit accomodate
543:     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.

/// @audit consistentcy
663:                 // evaluate at TWAP price to keep consistentcy with solvency calculations

/// @audit commited
886:                         // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
```

- *LeftRight.sol* ( [153](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L153), [159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L159), [176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L176), [182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L182) ):

```solidity
/// @audit explictily
153:             // adding leftRight packed uint128's is same as just adding the values explictily

/// @audit occured
159:             // then an overflow has occured

/// @audit explictily
176:             // subtracting leftRight packed uint128's is same as just subtracting the values explictily

/// @audit occured
182:             // then an underflow has occured
```

</details>

### [N-37] Consider bounding input array length

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to require() that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.

<details>
<summary>There are 9 instances (click to show):</summary>

- *CollateralTracker.sol* ( [1208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1208) ):

```solidity
1208:         for (uint256 i = 0; i < totalIterations; ) {
```

- *PanopticPool.sol* ( [441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L441), [459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L459), [802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L802), [1382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1382) ):

```solidity
441:         for (uint256 k = 0; k < pLength; ) {

459:             for (uint256 leg = 0; leg < numLegs; ) {

802:         for (uint256 i = 0; i < positionIdList.length; ) {

1382:         for (uint256 i = 0; i < pLength; ) {
```

- *SemiFungiblePositionManager.sol* ( [575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L575) ):

```solidity
575:         for (uint256 i = 0; i < ids.length; ) {
```

- *Multicall.sol* ( [14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L14) ):

```solidity
14:         for (uint256 i = 0; i < data.length; ) {
```

- *ERC1155Minimal.sol* ( [143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L143), [187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L187) ):

```solidity
143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {
```

</details>

### [N-38] Unnecessary casting

Unnecessary castings can be removed.

<details>
<summary>There are 15 instances (click to show):</summary>

- *PanopticFactory.sol* ( [404-404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L404-L404) ):

```solidity
/// @audit IUniswapV3Pool(v3Pool)
404:             IUniswapV3Pool(v3Pool).mint(
```

- *PanopticPool.sol* ( [302-302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L302-L302), [304-304](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L304-L304), [309-309](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L309-L309) ):

```solidity
/// @audit IUniswapV3Pool(_univ3pool)
302:         s_univ3pool = IUniswapV3Pool(_univ3pool);

/// @audit IUniswapV3Pool(_univ3pool)
304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

/// @audit uint256(block.timestamp)
309:                 (uint256(block.timestamp) << 216) +
```

- *SemiFungiblePositionManager.sol* ( [447-447](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L447-L447), [448-448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L448-L448) ):

```solidity
/// @audit address(decoded.poolFeatures.token0)
447:             ? address(decoded.poolFeatures.token0)

/// @audit address(decoded.poolFeatures.token1)
448:             : address(decoded.poolFeatures.token1);
```

- *TokenId.sol* ( [110-110](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L110-L110), [120-120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L120-L120), [130-130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L130-L130), [140-140](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L140-L140), [150-150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L150-L150), [212-212](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L212-L212), [229-229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L229-L229), [263-263](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L263-L263), [281-281](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L281-L281) ):

```solidity
/// @audit uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2)
110:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

/// @audit uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128)
120:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

/// @audit uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2)
130:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

/// @audit uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2)
140:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

/// @audit uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4)
150:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

/// @audit uint256(_asset % 2)
212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

/// @audit uint256(_optionRatio % 128)
229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

/// @audit uint256(_tokenType % 2)
263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

/// @audit uint256(_riskPartner % 4)
281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))
```

</details>

### [N-39] Unused contract variables

The following state variables are defined but not used.
It is recommended to check the code for logical omissions that cause them not to be used. If it's determined that they are not needed anywhere, it's best to remove them from the codebase to improve code clarity and minimize confusion.

There is 1 instance:

- *CollateralTracker.sol* ( [131-131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L131-L131) ):

```solidity
131:     uint256 immutable TICK_DEVIATION;
```

### [N-40] Unused import

The identifier is imported but never used within the file.

<details>
<summary>There are 29 instances (click to show):</summary>

- *CollateralTracker.sol* ( [5-5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L5-L5), [8-8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L8-L8), [18-18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L18-L18) ):

```solidity
/// @audit PanopticPool
5: import {PanopticPool} from "./PanopticPool.sol";

/// @audit Multicall
8: import {Multicall} from "@multicall/Multicall.sol";

/// @audit LiquidityChunk
18: import {LiquidityChunk} from "@types/LiquidityChunk.sol";
```

- *PanopticFactory.sol* ( [7-7](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L7-L7), [8-8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L8-L8), [9-9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L9-L9), [12-12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L12-L12) ):

```solidity
/// @audit SemiFungiblePositionManager
7: import {SemiFungiblePositionManager} from "@contracts/SemiFungiblePositionManager.sol";

/// @audit IDonorNFT
8: import {IDonorNFT} from "@contracts/tokens/interfaces/IDonorNFT.sol";

/// @audit IUniswapV3Factory
9: import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

/// @audit Multicall
12: import {Multicall} from "@multicall/Multicall.sol";
```

- *PanopticPool.sol* ( [5-5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L6-L6), [9-9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L9-L9), [10-10](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L10-L10), [20-20](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L20-L20) ):

```solidity
/// @audit CollateralTracker
5: import {CollateralTracker} from "@contracts/CollateralTracker.sol";

/// @audit SemiFungiblePositionManager
6: import {SemiFungiblePositionManager} from "@contracts/SemiFungiblePositionManager.sol";

/// @audit ERC1155Holder
9: import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";

/// @audit Multicall
10: import {Multicall} from "@multicall/Multicall.sol";

/// @audit LiquidityChunk
20: import {LiquidityChunk} from "@types/LiquidityChunk.sol";
```

- *SemiFungiblePositionManager.sol* ( [5-5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L5-L5), [8-8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L8-L8), [9-9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L9-L9), [20-20](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L20-L20) ):

```solidity
/// @audit IUniswapV3Factory
5: import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

/// @audit ERC1155
8: import {ERC1155} from "@tokens/ERC1155Minimal.sol";

/// @audit Multicall
9: import {Multicall} from "@multicall/Multicall.sol";

/// @audit LiquidityChunk
20: import {LiquidityChunk} from "@types/LiquidityChunk.sol";
```

- *CallbackLib.sol* ( [5-5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L5-L5) ):

```solidity
/// @audit IUniswapV3Factory
5: import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";
```

- *FeesCalc.sol* ( [5-5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L5-L5), [10-10](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L10-L10), [11-11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L11-L11), [12-12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L12-L12) ):

```solidity
/// @audit IUniswapV3Pool
5: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";

/// @audit LeftRightUnsigned
10: import {LeftRightUnsigned, LeftRightSigned} from "@types/LeftRight.sol";

/// @audit LiquidityChunk
11: import {LiquidityChunk} from "@types/LiquidityChunk.sol";

/// @audit TokenId
12: import {TokenId} from "@types/TokenId.sol";
```

- *InteractionHelper.sol* ( [5-5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L5-L5), [8-8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L8-L8) ):

```solidity
/// @audit CollateralTracker
5: import {CollateralTracker} from "@contracts/CollateralTracker.sol";

/// @audit SemiFungiblePositionManager
8: import {SemiFungiblePositionManager} from "@contracts/SemiFungiblePositionManager.sol";
```

- *Math.sol* ( [8-8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L8-L8) ):

```solidity
/// @audit LiquidityChunk
8: import {LiquidityChunk, LiquidityChunkLibrary} from "@types/LiquidityChunk.sol";
```

- *PanopticMath.sol* ( [5-5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L5-L5), [13-13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L13-L13), [14-14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L14-L14) ):

```solidity
/// @audit CollateralTracker
5: import {CollateralTracker} from "@contracts/CollateralTracker.sol";

/// @audit LiquidityChunk
13: import {LiquidityChunk} from "@types/LiquidityChunk.sol";

/// @audit TokenId
14: import {TokenId} from "@types/TokenId.sol";
```

- *IDonorNFT.sol* ( [4-4](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L4-L4) ):

```solidity
/// @audit PanopticPool
4: import {PanopticPool} from "@contracts/PanopticPool.sol";
```

- *LiquidityChunk.sol* ( [5-5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L5-L5) ):

```solidity
/// @audit TokenId
5: import {TokenId} from "@types/TokenId.sol";
```

</details>

### [N-41] Unused named return

Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment. This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

<details>
<summary>There are 18 instances (click to show):</summary>

- *CollateralTracker.sol* ( [361-361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L361-L361), [370-370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L370-L370), [379-379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L379-L379), [386-386](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L386-L386), [392-392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L392-L392), [444-444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L444-L444), [507-507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L507-L507), [518-518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L518-L518), [572-572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L572-L572), [581-581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L581-L581), [741-741](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L741-L741), [751-753](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L751-L753), [806-808](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L806-L808), [1278-1284](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1278-L1284) ):

```solidity
/// @audit assetTokenAddress
361:     function asset() external view returns (address assetTokenAddress) {

/// @audit totalManagedAssets
370:     function totalAssets() public view returns (uint256 totalManagedAssets) {

/// @audit shares
379:     function convertToShares(uint256 assets) public view returns (uint256 shares) {

/// @audit assets
386:     function convertToAssets(uint256 shares) public view returns (uint256 assets) {

/// @audit maxAssets
392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

/// @audit maxShares
444:     function maxMint(address) external view returns (uint256 maxShares) {

/// @audit maxAssets
507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

/// @audit shares
518:     function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

/// @audit maxShares
572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {

/// @audit assets
581:     function previewRedeem(uint256 shares) public view returns (uint256 assets) {

/// @audit poolUtilization
741:     function _poolUtilization() internal view returns (int256 poolUtilization) {

/// @audit sellCollateralRatio
751:     function _sellCollateralRatio(
752:         int256 utilization
753:     ) internal view returns (uint256 sellCollateralRatio) {

/// @audit buyCollateralRatio
806:     function _buyCollateralRatio(
807:         uint256 utilization
808:     ) internal view returns (uint256 buyCollateralRatio) {

/// @audit required
1278:     function _getRequiredCollateralSingleLeg(
1279:         TokenId tokenId,
1280:         uint256 index,
1281:         uint128 positionSize,
1282:         int24 atTick,
1283:         uint128 poolUtilization
1284:     ) internal view returns (uint256 required) {
```

- *PanopticPool.sol* ( [381-385](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L381-L385), [1431-1431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1431-L1431) ):

```solidity
/// @audit premium0
/// @audit premium1
381:     function calculateAccumulatedFeesBatch(
382:         address user,
383:         bool includePendingPremium,
384:         TokenId[] calldata positionIdList
385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

/// @audit collateralToken
1431:     function collateralToken0() external view returns (CollateralTracker collateralToken) {
```

- *SemiFungiblePositionManager.sol* ( [1555-1557](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1555-L1557) ):

```solidity
/// @audit UniswapV3Pool
1555:     function getUniswapV3PoolFromId(
1556:         uint64 poolId
1557:     ) external view returns (IUniswapV3Pool UniswapV3Pool) {
```

</details>

### [N-42] Use delete instead of assigning values to `false`

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

There are 2 instances:

- *SemiFungiblePositionManager.sol* ( [332-332](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L332-L332) ):

```solidity
332:         s_poolContext[poolId].locked = false;
```

- *PanopticMath.sol* ( [220-220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L220-L220) ):

```solidity
220:                         below = false;
```

### [N-43] Consider using `delete` rather than assigning zero to clear values

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

There are 3 instances:

- *PanopticMath.sol* ( [850-850](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L850-L850), [851-851](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L851-L851) ):

```solidity
850:                 collateralDelta0 = 0;

851:                 collateralDelta1 = 0;
```

- *TokenId.sol* ( [377-377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L377-L377) ):

```solidity
377:                 optionRatios = 0;
```

### [N-44] Use the latest Solidity version

Upgrading to the [latest solidity version](https://github.com/ethereum/solc-js/tags) (0.8.19 for L2s) can optimize gas usage, take advantage of new features and improve overall contract efficiency. Where possible, based on compatibility requirements, it is recommended to use newer/latest solidity version to take advantage of the latest optimizations and features.

<details>
<summary>There are 18 instances (click to show):</summary>

- *CollateralTracker.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *PanopticFactory.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *PanopticPool.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *SemiFungiblePositionManager.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *CallbackLib.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *Constants.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *Errors.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *FeesCalc.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *InteractionHelper.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *Math.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *PanopticMath.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *SafeTransferLib.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *Multicall.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L2) ):

```solidity
2: pragma solidity ^0.8.18;
```

- *ERC1155Minimal.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *ERC20Minimal.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *LeftRight.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *LiquidityChunk.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

- *TokenId.sol* ( [2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L2) ):

```solidity
2: pragma solidity ^0.8.0;
```

</details>

### [N-45] Use a struct to encapsulate multiple function parameters

If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

<details>
<summary>There are 9 instances (click to show):</summary>

- *CollateralTracker.sol* ( [178-186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L178-L186), [221-227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L221-L227), [650-656](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L650-L656), [1043-1049](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1043-L1049), [1278-1284](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1278-L1284), [1311-1317](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1311-L1317), [1439-1445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1439-L1445), [1510-1516](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1510-L1516), [1600-1606](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1600-L1606) ):

```solidity
178:     constructor(
179:         uint256 _commissionFee,
180:         uint256 _sellerCollateralRatio,
181:         uint256 _buyerCollateralRatio,
182:         int256 _forceExerciseCost,
183:         uint256 _targetPoolUtilization,
184:         uint256 _saturatedPoolUtilization,
185:         uint256 _ITMSpreadMultiplier
186:     ) {

221:     function startToken(
222:         bool underlyingIsToken0,
223:         address token0,
224:         address token1,
225:         uint24 fee,
226:         PanopticPool panopticPool
227:     ) external {

650:     function exerciseCost(
651:         int24 currentTick,
652:         int24 oracleTick,
653:         TokenId positionId,
654:         uint128 positionBalance,
655:         LeftRightSigned longAmounts
656:     ) external view returns (LeftRightSigned exerciseFees) {

1043:     function exercise(
1044:         address optionOwner,
1045:         int128 longAmount,
1046:         int128 shortAmount,
1047:         int128 swappedAmount,
1048:         int128 realizedPremium
1049:     ) external onlyPanopticPool returns (int128) {

1278:     function _getRequiredCollateralSingleLeg(
1279:         TokenId tokenId,
1280:         uint256 index,
1281:         uint128 positionSize,
1282:         int24 atTick,
1283:         uint128 poolUtilization
1284:     ) internal view returns (uint256 required) {

1311:     function _getRequiredCollateralSingleLegNoPartner(
1312:         TokenId tokenId,
1313:         uint256 index,
1314:         uint128 positionSize,
1315:         int24 atTick,
1316:         uint128 poolUtilization
1317:     ) internal view returns (uint256 required) {

1439:     function _getRequiredCollateralSingleLegPartner(
1440:         TokenId tokenId,
1441:         uint256 index,
1442:         uint128 positionSize,
1443:         int24 atTick,
1444:         uint128 poolUtilization
1445:     ) internal view returns (uint256 required) {

1510:     function _computeSpread(
1511:         TokenId tokenId,
1512:         uint128 positionSize,
1513:         uint256 index,
1514:         uint256 partnerIndex,
1515:         uint128 poolUtilization
1516:     ) internal view returns (uint256 spreadRequirement) {

1600:     function _computeStrangle(
1601:         TokenId tokenId,
1602:         uint256 index,
1603:         uint128 positionSize,
1604:         int24 atTick,
1605:         uint128 poolUtilization
1606:     ) internal view returns (uint256 strangleRequired) {
```

</details>

### [N-46] Returning a struct instead of a bunch of variables is better

If a function returns [too many variables](https://docs.soliditylang.org/en/v0.8.21/contracts.html#returning-multiple-values), replacing them with a struct can improve code readability, maintainability and reusability.

<details>
<summary>There are 5 instances (click to show):</summary>

- *CollateralTracker.sol* ( [277-280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L277-L280) ):

```solidity
277:     function getPoolData()
278:         external
279:         view
280:         returns (uint256 poolAssets, uint256 insideAMM, int256 currentPoolUtilization)
```

- *PanopticFactory.sol* ( [290-294](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L290-L294), [335-340](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L335-L340) ):

```solidity
290:     function minePoolAddress(
291:         bytes32 salt,
292:         uint256 loops,
293:         uint256 minTargetRarity
294:     ) external view returns (bytes32 bestSalt, uint256 highestRarity) {

335:     function _mintFullRange(
336:         IUniswapV3Pool v3Pool,
337:         address token0,
338:         address token1,
339:         uint24 fee
340:     ) internal returns (uint256, uint256) {
```

- *PanopticPool.sol* ( [352-355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L352-L355), [381-385](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L381-L385) ):

```solidity
352:     function optionPositionBalance(
353:         address user,
354:         TokenId tokenId
355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

381:     function calculateAccumulatedFeesBatch(
382:         address user,
383:         bool includePendingPremium,
384:         TokenId[] calldata positionIdList
385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {
```

</details>

### [N-47] Contract variables should have comments

Consider adding some comments on non-public contract variables to explain what they are supposed to do. This will help for future code reviews.

There is 1 instance:

- *SemiFungiblePositionManager.sol* ( [289-289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L289-L289) ):

```solidity
289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;
```

### [N-48] Empty bytes check is missing

Passing empty bytes to a function can cause unexpected behavior, such as certain operations failing, producing incorrect results, or wasting gas. It is recommended to check that all byte parameters are not empty.

<details>
<summary>There are 7 instances (click to show):</summary>

- *PanopticFactory.sol* ( [172-176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L172-L176) ):

```solidity
/// @audit data
172:     function uniswapV3MintCallback(
173:         uint256 amount0Owed,
174:         uint256 amount1Owed,
175:         bytes calldata data
176:     ) external {
```

- *SemiFungiblePositionManager.sol* ( [402-406](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L402-L406), [435-439](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L435-L439), [540-546](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L540-L546), [566-572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L566-L572) ):

```solidity
/// @audit data
402:     function uniswapV3MintCallback(
403:         uint256 amount0Owed,
404:         uint256 amount1Owed,
405:         bytes calldata data
406:     ) external {

/// @audit data
435:     function uniswapV3SwapCallback(
436:         int256 amount0Delta,
437:         int256 amount1Delta,
438:         bytes calldata data
439:     ) external {

/// @audit data
540:     function safeTransferFrom(
541:         address from,
542:         address to,
543:         uint256 id,
544:         uint256 amount,
545:         bytes calldata data
546:     ) public override {

/// @audit data
566:     function safeBatchTransferFrom(
567:         address from,
568:         address to,
569:         uint256[] calldata ids,
570:         uint256[] calldata amounts,
571:         bytes calldata data
572:     ) public override {
```

- *ERC1155Minimal.sol* ( [94-100](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L94-L100), [130-136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L130-L136) ):

```solidity
/// @audit data
94:     function safeTransferFrom(
95:         address from,
96:         address to,
97:         uint256 id,
98:         uint256 amount,
99:         bytes calldata data
100:     ) public virtual {

/// @audit data
130:     function safeBatchTransferFrom(
131:         address from,
132:         address to,
133:         uint256[] calldata ids,
134:         uint256[] calldata amounts,
135:         bytes calldata data
136:     ) public virtual {
```

</details>

### [N-49] Don't define functions with the same name in a contract

In Solidity, while function overriding allows for functions with the same name to coexist, it is advisable to avoid this practice to enhance code readability and maintainability. Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the likelihood of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function, but also helps prevent unintended function calls or incorrect overriding. By adopting a clear and consistent naming convention, developers can create more comprehensible and maintainable smart contracts.

<details>
<summary>There are 16 instances (click to show):</summary>

- *CollateralTracker.sol* ( [894](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L894), [975](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L975) ):

```solidity
/// @audit Different function with same name found on line 864
894:     function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

/// @audit Different function with same name found on line 903
975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {
```

- *PanopticPool.sol* ( [586](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L586) ):

```solidity
/// @audit Different function with same name found on line 569
586:     function burnOptions(
```

- *Math.sol* ( [49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L49), [65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L65), [318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L318) ):

```solidity
/// @audit Different function with same name found on line 41
49:     function min(int256 a, int256 b) internal pure returns (int256) {

/// @audit Different function with same name found on line 57
65:     function max(int256 a, int256 b) internal pure returns (int256) {

/// @audit Different function with same name found on line 311
318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {
```

- *PanopticMath.sol* ( [445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L445), [524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L524), [547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L547) ):

```solidity
/// @audit Different function with same name found on line 419
445:     function convertCollateralData(

/// @audit Different function with same name found on line 490
524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

/// @audit Different function with same name found on line 507
547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
```

- *LeftRight.sol* ( [46](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L46), [78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L78), [108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L108), [134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L134), [194](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L194), [214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol#L232) ):

```solidity
/// @audit Different function with same name found on line 39
46:     function rightSlot(LeftRightSigned self) internal pure returns (int128) {

/// @audit Different function with same name found on line 59
78:     function toRightSlot(

/// @audit Different function with same name found on line 101
108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

/// @audit Different function with same name found on line 121
134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

/// @audit Different function with same name found on line 148
194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

/// @audit Different function with same name found on line 148
214:     function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

/// @audit Different function with same name found on line 171
232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
```

</details>

### [N-50] Assembly block creates dirty bits

Writing data to the free memory pointer without later updating the free memory pointer will cause there to be dirty bits at that memory location. Not updating the free memory pointer will make it [harder](https://docs.soliditylang.org/en/latest/ir-breaking-changes.html#cleanup) for the optimizer to reason about whether the memory needs to be cleaned before use, which will lead to worse optimizations. Update the free memory pointer and annotate the block (`assembly ("memory-safe") { ... }`) to avoid this issue.

<details>
<summary>There are 2 instances (click to show):</summary>

- *SafeTransferLib.sol* ( [24-43](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L24-L43), [55-73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol#L55-L73) ):

```solidity
24:         assembly ("memory-safe") {
25:             // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
26:             let p := mload(0x40)
27: 
28:             // Write the abi-encoded calldata into memory, beginning with the function selector.
29:             mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)
30:             mstore(add(4, p), from) // Append the "from" argument.
31:             mstore(add(36, p), to) // Append the "to" argument.
32:             mstore(add(68, p), amount) // Append the "amount" argument.
33: 
34:             success := and(
35:                 // Set success to whether the call reverted, if not we check it either
36:                 // returned exactly 1 (can't just be non-zero data), or had no return data.
37:                 or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
38:                 // We use 100 because that's the total length of our calldata (4 + 32 * 3)
39:                 // Counterintuitively, this call() must be positioned after the or() in the
40:                 // surrounding and() because and() evaluates its arguments from right to left.
41:                 call(gas(), token, 0, p, 100, 0, 32)
42:             )
43:         }

55:         assembly ("memory-safe") {
56:             // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
57:             let p := mload(0x40)
58: 
59:             // Write the abi-encoded calldata into memory, beginning with the function selector.
60:             mstore(p, 0xa9059cbb00000000000000000000000000000000000000000000000000000000)
61:             mstore(add(4, p), to) // Append the "to" argument.
62:             mstore(add(36, p), amount) // Append the "amount" argument.
63: 
64:             success := and(
65:                 // Set success to whether the call reverted, if not we check it either
66:                 // returned exactly 1 (can't just be non-zero data), or had no return data.
67:                 or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
68:                 // We use 68 because that's the total length of our calldata (4 + 32 * 2)
69:                 // Counterintuitively, this call() must be positioned after the or() in the
70:                 // surrounding and() because and() evaluates its arguments from right to left.
71:                 call(gas(), token, 0, p, 68, 0, 32)
72:             )
73:         }
```

</details>

### [N-51] Multiple mappings with same keys can be combined into a single struct mapping for readability

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related.

<details>
<summary>There are 13 instances (click to show):</summary>

- *PanopticPool.sol* ( [238-238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L238-L238), [245-245](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L245-L245), [251-251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L251-L251), [258-258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L258-L258), [272-272](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L272-L272) ):

```solidity
238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

245:     mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

251:     mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;

258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))

272:     mapping(address account => uint256 positionsHash) internal s_positionsHash;
```

- *SemiFungiblePositionManager.sol* ( [177-177](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L177-L177), [287-287](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L287-L287), [289-289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L289-L289), [295-295](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L295-L295) ):

```solidity
177:     mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)

287:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

295:     mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;
```

- *ERC1155Minimal.sol* ( [66-66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L66-L66), [71-71](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L71-L71) ):

```solidity
66:     mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;

71:     mapping(address owner => mapping(address operator => bool approvedForAll))
```

- *ERC20Minimal.sol* ( [35-35](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L35-L35), [39-39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol#L39-L39) ):

```solidity
35:     mapping(address account => uint256 balance) public balanceOf;

39:     mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;
```

</details>

### [N-52] Do not cache immutable variables

Instead of caching immutable variables, using them directly can make code more consistent and less prone to errors.

There is 1 instance:

- *CollateralTracker.sol* ( [773-773](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L773-L773) ):

```solidity
773:         uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;
```

### [N-53] Function state mutability can be restricted to view

Function state mutability can be restricted to view

There is 1 instance:

- *SemiFungiblePositionManager.sol* ( [1110-1114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1110-L1114) ):

```solidity
1110:     function _updateStoredPremia(
1111:         bytes32 positionKey,
1112:         LeftRightUnsigned currentLiquidity,
1113:         LeftRightUnsigned collectedAmounts
1114:     ) private {
```

### [N-54] Missing event for critical changes

Events should be emitted when critical changes are made to the contracts.

<details>
<summary>There are 9 instances (click to show):</summary>

- *CollateralTracker.sol* ( [221-227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L221-L227), [995-1000](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L995-L1000) ):

```solidity
221:     function startToken(
222:         bool underlyingIsToken0,
223:         address token0,
224:         address token1,
225:         uint24 fee,
226:         PanopticPool panopticPool
227:     ) external {

995:     function takeCommissionAddData(
996:         address optionOwner,
997:         int128 longAmount,
998:         int128 shortAmount,
999:         int128 swappedAmount
1000:     ) external onlyPanopticPool returns (int256 utilization) {
```

- *PanopticPool.sol* ( [291-297](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L291-L297), [739-739](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L739-L739), [859-859](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L859-L859), [1405-1417](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1405-L1417), [1666-1670](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1666-L1670), [1833-1839](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1833-L1839) ):

```solidity
291:     function startPool(
292:         IUniswapV3Pool _univ3pool,
293:         address token0,
294:         address token1,
295:         CollateralTracker collateralTracker0,
296:         CollateralTracker collateralTracker1
297:     ) external {

739:     function _addUserOption(TokenId tokenId, uint64 effectiveLiquidityLimitX32) internal {

859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

1405:     function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {
1406:         // Get the current position hash value (fingerprint of all pre-existing positions created by '_account')
1407:         // Add the current tokenId to the positionsHash as XOR'd
1408:         // since 0 ^ x = x, no problem on first mint
1409:         // Store values back into the user option details with the updated hash (leaves the other parameters unchanged)
1410:         uint256 newHash = PanopticMath.updatePositionsHash(
1411:             s_positionsHash[account],
1412:             tokenId,
1413:             addFlag
1414:         );
1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();
1416:         s_positionsHash[account] = newHash;
1417:     }

1666:     function _updateSettlementPostMint(
1667:         TokenId tokenId,
1668:         LeftRightUnsigned[4] memory collectedByLeg,
1669:         uint128 positionSize
1670:     ) internal {

1833:     function _updateSettlementPostBurn(
1834:         address owner,
1835:         TokenId tokenId,
1836:         LeftRightUnsigned[4] memory collectedByLeg,
1837:         uint128 positionSize,
1838:         bool commitLongSettled
1839:     ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
```

- *SemiFungiblePositionManager.sol* ( [1110-1114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1110-L1114) ):

```solidity
1110:     function _updateStoredPremia(
1111:         bytes32 positionKey,
1112:         LeftRightUnsigned currentLiquidity,
1113:         LeftRightUnsigned collectedAmounts
1114:     ) private {
```

</details>

### [N-55] Non-assembly method available

There are some automated tools that will flag a project as having higher complexity if there is inline-assembly, so it's best to avoid using it where it's not necessary. In addition, most assembly methods can be replaced by non-assembly methods, for example:
- `assembly{ g := gas() }` => `uint256 g = gasleft()`
- `assembly{ id := chainid() }` => `uint256 id = block.chainid`
- `assembly { r := mulmod(a, b, d) }` => `uint256 m = mulmod(x, y, k)`
- `assembly { size := extcodesize() }` => `uint256 size = address(a).code.length`
- etc.

There are 6 instances:

- *Math.sol* ( [380-380](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L380-L380), [494-494](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L494-L494), [557-557](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L557-L557), [634-634](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L634-L634), [711-711](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol#L711-L711) ):

```solidity
380:                 remainder := mulmod(a, b, denominator)

494:                 remainder := mulmod(a, b, 0x10000000000000000)

557:                 remainder := mulmod(a, b, 0x1000000000000000000000000)

634:                 remainder := mulmod(a, b, 0x100000000000000000000000000000000)

711:                 remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)
```

- *Multicall.sol* ( [26-26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L26-L26) ):

```solidity
26:                     revert(add(result, 32), mload(result))
```

### [N-56] Duplicated `require()`/`revert()` checks should be refactored

Refactoring duplicate `require()`/`revert()` checks into a modifier or function can make the code more concise, readable and maintainable, and less likely to make errors or omissions when modifying the `require()` or `revert()`.

<details>
<summary>There are 13 instances (click to show):</summary>

- *CollateralTracker.sol* ( [331-331](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L331-L331), [418-418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L418-L418), [536-536](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L536-L536) ):

```solidity
/// @audit Duplicated on line 350
331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

/// @audit Duplicated on line 480
418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

/// @audit Duplicated on line 596
536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();
```

- *PanopticPool.sol* ( [940-940](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L940-L940), [1188-1188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1188-L1188) ):

```solidity
/// @audit Duplicated on line 945, 1163
940:         if (!solventAtFast) revert Errors.NotEnoughCollateral();

/// @audit Duplicated on line 1394
1188:         if (touchedId.length != 1) revert Errors.InputListFail();
```

- *SemiFungiblePositionManager.sol* ( [322-322](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L322-L322), [355-355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L355-L355), [634-634](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L634-L634) ):

```solidity
/// @audit Duplicated on line 549, 576
322:         if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();

/// @audit Duplicated on line 702
355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

/// @audit Duplicated on line 639
634:             ) revert Errors.TransferFailed();
```

- *ERC1155Minimal.sol* ( [101-101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L101-L101), [117-117](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L117-L117) ):

```solidity
/// @audit Duplicated on line 137
101:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

/// @audit Duplicated on line 168, 227
117:                 revert UnsafeRecipient();
```

</details>

### [N-57] Consider adding emergency-stop functionality

Adding a way to quickly halt protocol functionality in an emergency, rather than having to pause individual contracts one-by-one, will make in-progress hack mitigation faster and much less stressful.

There is 1 instance:

- *SemiFungiblePositionManager.sol* ( [72-72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L72-L72) ):

```solidity
72: contract SemiFungiblePositionManager is ERC1155, Multicall {
```

### [N-58] Missing checks for uint state variable assignments

Consider whether reasonable bounds checks for variables would be useful.

There are 4 instances:

- *CollateralTracker.sol* ( [251-251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L251-L251), [1028-1028](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1028-L1028) ):

```solidity
251:         s_poolFee = _poolFee;

1028:             s_poolAssets = uint128(uint256(updatedAssets));
```

- *PanopticPool.sol* ( [533-533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L533-L533), [664-664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L664-L664) ):

```solidity
533:         if (medianData != 0) s_miniMedian = medianData;

664:         if (medianData != 0) s_miniMedian = medianData;
```

### [N-59] Use the Modern Upgradeable Contract Paradigm

Modern smart contract development often employs upgradeable contract structures, utilizing proxy patterns like OpenZeppelin’s Upgradeable Contracts. This paradigm separates logic and state, allowing developers to amend and enhance the contract's functionality without altering its state or the deployed contract address. Transitioning to this approach enhances long-term maintainability.
Resolution: Adopt a well-established proxy pattern for upgradeability, ensuring proper initialization and employing transparent proxies to mitigate potential risks. Embrace comprehensive testing and audit practices, particularly when updating contract logic, to ensure state consistency and security are preserved across upgrades. This ensures your contract remains robust and adaptable to future requirements.

There are 3 instances:

- *CollateralTracker.sol* ( [36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36) ):

```solidity
36: contract CollateralTracker is ERC20Minimal, Multicall {
```

- *PanopticPool.sol* ( [27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L27) ):

```solidity
27: contract PanopticPool is ERC1155Holder, Multicall {
```

- *SemiFungiblePositionManager.sol* ( [72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L72) ):

```solidity
72: contract SemiFungiblePositionManager is ERC1155, Multicall {
```

### [N-60] Large or complicated code bases should implement invariant tests

This includes: large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts.
Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold.
Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers may help significantly.

There is 1 instance:

- Global finding

### [N-61] The default value is manually set when it is declared

In instances where a new variable is defined, there is no need to set it to it's default value.

<details>
<summary>There are 31 instances (click to show):</summary>

- *CollateralTracker.sol* ( [662-662](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L662-L662), [1208-1208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1208-L1208), [1255-1255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1255-L1255) ):

```solidity
662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

1208:         for (uint256 i = 0; i < totalIterations; ) {

1255:             for (uint256 index = 0; index < numLegs; ++index) {
```

- *PanopticPool.sol* ( [441-441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L441-L441), [459-459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L459-L459), [745-745](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L745-L745), [802-802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L802-L802), [864-864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L864-L864), [1382-1382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1382-L1382), [1518-1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1518-L1518), [1672-1672](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1672-L1672), [1852-1852](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1852-L1852) ):

```solidity
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

- *SemiFungiblePositionManager.sol* ( [575-575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L575-L575), [601-601](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L601-L601), [882-882](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L882-L882) ):

```solidity
575:         for (uint256 i = 0; i < ids.length; ) {

601:         for (uint256 leg = 0; leg < numLegs; ) {

882:         for (uint256 leg = 0; leg < numLegs; ) {
```

- *FeesCalc.sol* ( [51-51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L51-L51), [55-55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L55-L55) ):

```solidity
51:         for (uint256 k = 0; k < positionIdList.length; ) {

55:             for (uint256 leg = 0; leg < numLegs; ) {
```

- *PanopticMath.sol* ( [137-137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L137-L137), [148-148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L148-L148), [248-248](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L248-L248), [256-256](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L256-L256), [395-395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L395-L395), [781-781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L781-L781), [784-784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L784-L784), [860-860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L860-L860), [863-863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L863-L863) ):

```solidity
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

- *Multicall.sol* ( [14-14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L14-L14) ):

```solidity
14:         for (uint256 i = 0; i < data.length; ) {
```

- *ERC1155Minimal.sol* ( [143-143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L143-L143), [187-187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L187-L187) ):

```solidity
143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {
```

- *TokenId.sol* ( [507-507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L507-L507), [581-581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol#L581-L581) ):

```solidity
507:             for (uint256 i = 0; i < 4; ++i) {

581:             for (uint256 i = 0; i < numLegs; ++i) {
```

</details>

### [N-62] Contracts should have all `public`/`external` functions exposed by `interface`s

All `external`/`public` functions should extend an `interface`. This is useful to ensure that the whole API is extracted and can be more easily integrated by other projects.

There are 4 instances:

- *CollateralTracker.sol* ( [36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L36) ):

```solidity
36: contract CollateralTracker is ERC20Minimal, Multicall {
```

- *PanopticFactory.sol* ( [26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L26) ):

```solidity
26: contract PanopticFactory is Multicall {
```

- *PanopticPool.sol* ( [27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L27) ):

```solidity
27: contract PanopticPool is ERC1155Holder, Multicall {
```

- *SemiFungiblePositionManager.sol* ( [72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L72) ):

```solidity
72: contract SemiFungiblePositionManager is ERC1155, Multicall {
```

### [N-63] Top-level declarations should be separated by at least two lines

-

There are 2 instances:

- *IDonorNFT.sol* ( [2-4](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L2-L4), [4-6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol#L4-L6) ):

```solidity
2: pragma solidity ^0.8.0;
3: 
4: import {PanopticPool} from "@contracts/PanopticPool.sol";

4: import {PanopticPool} from "@contracts/PanopticPool.sol";
5: 
6: interface IDonorNFT {
```

### [N-64] Consider adding formal verification proofs

Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).

<details>
<summary>There are 20 instances (click to show):</summary>

- [*CollateralTracker.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol)

- [*PanopticFactory.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol)

- [*PanopticPool.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol)

- [*SemiFungiblePositionManager.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol)

- [*CallbackLib.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/CallbackLib.sol)

- [*Constants.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Constants.sol)

- [*Errors.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Errors.sol)

- [*FeesCalc.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol)

- [*InteractionHelper.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/InteractionHelper.sol)

- [*Math.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/Math.sol)

- [*PanopticMath.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol)

- [*SafeTransferLib.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/SafeTransferLib.sol)

- [*Multicall.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol)

- [*ERC1155Minimal.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol)

- [*ERC20Minimal.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC20Minimal.sol)

- [*IDonorNFT.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IDonorNFT.sol)

- [*IERC20Partial.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/interfaces/IERC20Partial.sol)

- [*LeftRight.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LeftRight.sol)

- [*LiquidityChunk.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/LiquidityChunk.sol)

- [*TokenId.sol*](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/types/TokenId.sol)

</details>

### [N-65] Use scopes sparingly

The use of scoped blocks, denoted by `{}` without a preceding control structure like `if`, `for`, etc., allows for the creation of isolated scopes within a function. While this can be useful for managing memory and preventing naming conflicts, it should be used sparingly. Excessive use of these scope blocks can obscure the code's logic flow and make it more difficult to understand, impeding code maintainability. As a best practice, only employ scoped blocks when necessary for memory management or to avoid clear naming conflicts. Otherwise, aim for clarity and simplicity in your code structure for optimal readability and maintainability.

<details>
<summary>There are 21 instances (click to show):</summary>

- *CollateralTracker.sol* ( [666-667](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L666-L667), [686-687](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L686-L687) ):

```solidity
666:                 {
667:                     int24 range = int24(

686:                 {
687:                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
```

- *PanopticPool.sol* ( [750-751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L750-L751), [984-985](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L984-L985), [995-996](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L995-L996), [1031-1032](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1031-L1032), [1078-1079](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1078-L1079), [1204-1205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1204-L1205), [1601-1602](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1601-L1602) ):

```solidity
750:             {
751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

984:         {
985:             int128 paid0 = s_collateralToken0.exercise(

995:         {
996:             int128 paid1 = s_collateralToken1.exercise(

1031:         {
1032:             (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

1078:         {
1079:             LeftRightSigned netExchanged;

1204:         {
1205:             // add the premia to the delegated amounts to ensure the user has enough collateral to exercise

1601:         {
1602:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);
```

- *SemiFungiblePositionManager.sol* ( [887-888](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L887-L888), [989-990](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L989-L990), [1046-1047](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1046-L1047), [1345-1346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1345-L1346), [1362-1363](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1362-L1363), [1365-1366](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1365-L1366), [1383-1384](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1383-L1384), [1386-1387](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1386-L1387), [1471-1472](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1471-L1472) ):

```solidity
887:             {
888:                 // cache the univ3pool, tokenId, isBurn, and _positionSize variables to get rid of stack too deep error

989:         {
990:             // did we have liquidity already deployed in Uniswap for this chunk range from some past mint?

1046:         {
1047:             /** if the position is NOT long (selling a put or a call), then _mintLiquidity to move liquidity

1345:             {
1346:                 uint128 collected0 = collectedAmounts.rightSlot();

1362:             {
1363:                 uint128 premium0X64_owed;

1365:                 {
1366:                     // compute the owed premium (from Eqn 3)

1383:             {
1384:                 uint128 premium0X64_gross;

1386:                 {
1387:                     // compute the gross premium (from Eqn 4)

1471:                 {
1472:                     IUniswapV3Pool _univ3pool = IUniswapV3Pool(univ3pool);
```

- *PanopticMath.sol* ( [185-186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L185-L186), [661-662](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L661-L662), [854-855](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L854-L855) ):

```solidity
185:                 {
186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

661:             {
662:                 // compute the ratio of token0 to total collateral requirements

854:             {
855:                 address _liquidatee = liquidatee;
```

</details>

### [N-66] Prevent re-setting a state variable with the same value

This especially problematic when the setter also emits the same value, which may be confusing to offline parsers.

<details>
<summary>There are 15 instances (click to show):</summary>

- *CollateralTracker.sol* ( [234-234](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L234-L234), [241-241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L241-L241), [244-244](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L244-L244), [251-251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L251-L251), [254-254](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L254-L254), [255-255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L255-L255), [258-258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L258-L258), [262-262](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L262-L262), [1028-1028](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1028-L1028) ):

```solidity
234:         totalSupply = 10 ** 6;

241:         s_underlyingToken = underlyingIsToken0 ? token0 : token1;

244:         s_panopticPool = panopticPool;

251:         s_poolFee = _poolFee;

254:         s_univ3token0 = token0;

255:         s_univ3token1 = token1;

258:         s_underlyingIsToken0 = underlyingIsToken0;

262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

1028:             s_poolAssets = uint128(uint256(updatedAssets));
```

- *PanopticPool.sol* ( [302-302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L302-L302), [308-314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L308-L314), [318-318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L318-L318), [319-319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L319-L319), [533-533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L533-L533), [664-664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L664-L664) ):

```solidity
302:         s_univ3pool = IUniswapV3Pool(_univ3pool);

308:             s_miniMedian =
309:                 (uint256(block.timestamp) << 216) +
310:                 // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
311:                 // see comment on s_miniMedian initialization for format of this magic number
312:                 (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4
314:                 (uint256(uint24(currentTick))); // add to slot 3

318:         s_collateralToken0 = collateralTracker0;

319:         s_collateralToken1 = collateralTracker1;

533:         if (medianData != 0) s_miniMedian = medianData;

664:         if (medianData != 0) s_miniMedian = medianData;
```

</details>

### [N-67] Whitespace in Expressions

See the [whitespace](https://docs.soliditylang.org/en/latest/style-guide.html#whitespace-in-expressions) section of the Solidity Style Guide.

<details>
<summary>There are 98 instances (click to show):</summary>

- *CollateralTracker.sol* ( [1208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/CollateralTracker.sol#L1208) ):

```solidity
/// @audit Whitespace inside parenthesis
1208:         for (uint256 i = 0; i < totalIterations; ) {
```

- *PanopticFactory.sol* ( [303](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L303), [341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticFactory.sol#L341) ):

```solidity
/// @audit Whitespace inside parenthesis
303:         for (; uint256(salt) < maxSalt; ) {

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
341:         (uint160 currentSqrtPriceX96, , , , , , ) = v3Pool.slot0();
```

- *PanopticPool.sol* ( [304](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L304), [339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L339), [387](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L387), [441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L441), [459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L459), [523](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L523), [745](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L745), [802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L802), [864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L864), [897](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L897), [901](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L901), [902](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L902), [1032](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1032), [1094](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1094), [1202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1202), [1206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1206), [1382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1382), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1518), [1598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1598), [1852](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/PanopticPool.sol#L1852) ):

```solidity
/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
339:         (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
387:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

/// @audit Whitespace inside parenthesis
441:         for (uint256 k = 0; k < pLength; ) {

/// @audit Whitespace inside parenthesis
459:             for (uint256 leg = 0; leg < numLegs; ) {

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
523:         (, , uint16 observationIndex, uint16 observationCardinality, , , ) = s_univ3pool.slot0();

/// @audit Whitespace inside parenthesis
745:         for (uint256 leg = 0; leg < numLegs; ) {

/// @audit Whitespace inside parenthesis
802:         for (uint256 i = 0; i < positionIdList.length; ) {

/// @audit Whitespace inside parenthesis
864:         for (uint256 leg = 0; leg < numLegs; ) {

/// @audit Whitespace before a comma
897:             ,

/// @audit Whitespace before a comma
901:             ,

/// @audit Whitespace before a comma
902:             ,

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
1032:             (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
1094:             (, finalTick, , , , , ) = s_univ3pool.slot0();

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
1202:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

/// @audit Whitespace inside parenthesis
1206:             (LeftRightSigned positionPremia, ) = _calculateAccumulatedPremia(

/// @audit Whitespace inside parenthesis
1382:         for (uint256 i = 0; i < pLength; ) {

/// @audit Whitespace inside parenthesis
1518:         for (uint256 leg = 0; leg < numLegs; ) {

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
1598:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

/// @audit Whitespace inside parenthesis
1852:         for (uint256 leg = 0; leg < numLegs; ) {
```

- *SemiFungiblePositionManager.sol* ( [575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L575), [601](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L601), [725](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L725), [788](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L788), [882](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L882), [1148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/SemiFungiblePositionManager.sol#L1148) ):

```solidity
/// @audit Whitespace inside parenthesis
575:         for (uint256 i = 0; i < ids.length; ) {

/// @audit Whitespace inside parenthesis
601:         for (uint256 leg = 0; leg < numLegs; ) {

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
725:         (, int24 currentTick, , , , , ) = univ3pool.slot0();

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
788:                 (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

/// @audit Whitespace inside parenthesis
882:         for (uint256 leg = 0; leg < numLegs; ) {

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
1148:         (, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, , ) = univ3pool
```

- *FeesCalc.sol* ( [51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L51), [55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L55), [142](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L142), [143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/FeesCalc.sol#L143) ):

```solidity
/// @audit Whitespace inside parenthesis
51:         for (uint256 k = 0; k < positionIdList.length; ) {

/// @audit Whitespace inside parenthesis
55:             for (uint256 leg = 0; leg < numLegs; ) {

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
142:         (, , uint256 lowerOut0, uint256 lowerOut1, , , , ) = univ3pool.ticks(tickLower);

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
/// @audit Whitespace before a comma
143:         (, , uint256 upperOut0, uint256 upperOut1, , , , ) = univ3pool.ticks(tickUpper);
```

- *PanopticMath.sol* ( [138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L138), [186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L186), [192](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L192), [253](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L253), [395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/libraries/PanopticMath.sol#L395) ):

```solidity
/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

/// @audit Whitespace inside parenthesis
/// @audit Whitespace before a comma
192:                     (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool

/// @audit Whitespace inside parenthesis
253:             (int56[] memory tickCumulatives, ) = univ3pool.observe(secondsAgos);

/// @audit Whitespace inside parenthesis
395:         for (uint256 leg = 0; leg < numLegs; ) {
```

- *Multicall.sol* ( [14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/multicall/Multicall.sol#L14) ):

```solidity
/// @audit Whitespace inside parenthesis
14:         for (uint256 i = 0; i < data.length; ) {
```

- *ERC1155Minimal.sol* ( [143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/./contracts/tokens/ERC1155Minimal.sol#L143) ):

```solidity
/// @audit Whitespace inside parenthesis
143:         for (uint256 i = 0; i < ids.length; ) {
```

</details>
