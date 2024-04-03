**Note:** I've removed the specific instances flagged by the 4naly3er report

## Summary

### Low Risk Issues

| |Issue|Instances|
|-|:-|:-:|
| [[L&#x2011;01](#l01-events-may-be-emitted-out-of-order-due-to-reentrancy)] | Events may be emitted out of order due to reentrancy | 71 | 
| [[L&#x2011;02](#l02-file-allows-a-version-of-solidity-that-is-susceptible-to-selector-related-optimizer-bug)] | File allows a version of solidity that is susceptible to `.selector`-related optimizer bug | 1 | 
| [[L&#x2011;03](#l03-input-array-lengths-may-differ)] | Input array lengths may differ | 4 | 

Total: 76 instances over 3 issues

### Non-critical Issues

| |Issue|Instances|
|-|:-|:-:|
| [[N&#x2011;01](#n01-2n---1-should-be-re-written-as-typeuintnmaxnn)] | `2**<n> - 1` should be re-written as `type(uint<n>).max` | 23 | 
| [[N&#x2011;02](#n02-constants-should-be-defined-rather-than-using-magic-numbers)] | `constant`s should be defined rather than using magic numbers | 2 | 
| [[N&#x2011;03](#n03-else-block-not-required)] | `else`-block not required | 1 | 
| [[N&#x2011;04](#n04-if-statement-can-be-converted-to-a-ternary)] | `if`-statement can be converted to a ternary | 5 | 
| [[N&#x2011;05](#n05-public-functions-not-called-by-the-contract-should-be-declared-external-instead)] | `public` functions not called by the contract should be declared `external` instead | 2 | 
| [[N&#x2011;06](#n06-add-inline-comments-for-unnamed-variables)] | Add inline comments for unnamed variables | 2 | 
| [[N&#x2011;07](#n07-assembly-blocks-should-have-extensive-comments)] | Assembly blocks should have extensive comments | 21 | 
| [[N&#x2011;08](#n08-avoid-mutating-functionmodifier-parameters-of-non-utility-functions)] | Avoid mutating `function`/`modifier` parameters of non-utility functions | 9 | 
| [[N&#x2011;09](#n09-common-functions-should-be-refactored-to-a-common-base-contract)] | Common functions should be refactored to a common base contract | 2 | 
| [[N&#x2011;10](#n10-consider-defining-system-wide-constants-in-a-single-file)] | Consider defining system-wide constants in a single file | 28 | 
| [[N&#x2011;11](#n11-consider-emitting-an-event-at-the-end-of-the-constructor)] | Consider emitting an event at the end of the constructor | 4 | 
| [[N&#x2011;12](#n12-consider-making-contracts-upgradeable)] | Consider making contracts `Upgradeable` | 4 | 
| [[N&#x2011;13](#n13-consider-returning-a-struct-rather-than-having-multiple-return-values)] | Consider returning a `struct` rather than having multiple `return` values | 7 | 
| [[N&#x2011;14](#n14-consider-splitting-complex-checks-into-multiple-steps)] | Consider splitting complex checks into multiple steps | 1 | 
| [[N&#x2011;15](#n15-consider-using-delete-rather-than-assigning-zerofalse-to-clear-values)] | Consider using `delete` rather than assigning zero/false to clear values | 5 | 
| [[N&#x2011;16](#n16-consider-using-a-struct-rather-than-having-many-function-input-parameters)] | Consider using a `struct` rather than having many function input parameters | 37 | 
| [[N&#x2011;17](#n17-consider-using-descriptive-constants-when-passing-zero-as-a-function-argument)] | Consider using descriptive `constant`s when passing zero as a function argument | 77 | 
| [[N&#x2011;18](#n18-consider-using-named-function-arguments)] | Consider using named function arguments | 47 | 
| [[N&#x2011;19](#n19-consider-using-named-returns)] | Consider using named returns | 89 | 
| [[N&#x2011;20](#n20-consider-using-the-using-for-syntax)] | Consider using the `using`-`for` syntax | 193 | 
| [[N&#x2011;21](#n21-constants-in-comparisons-should-appear-on-the-left-side)] | Constants in comparisons should appear on the left side | 178 | 
| [[N&#x2011;22](#n22-contract-uses-both-requirerevert-as-well-as-custom-errors)] | Contract uses both `require()`/`revert()` as well as custom errors | 1 | 
| [[N&#x2011;23](#n23-contracts-should-have-all-publicexternal-functions-exposed-by-interfaces)] | Contracts should have all `public`/`external` functions exposed by `interface`s | 4 | 
| [[N&#x2011;24](#n24-custom-error-has-no-parameters-showing-error-details)] | Custom error has no parameters showing error details | 2 | 
| [[N&#x2011;25](#n25-custom-errors-should-be-used-rather-than-revertrequire)] | Custom errors should be used rather than `revert()`/`require()` | 9 | 
| [[N&#x2011;26](#n26-duplicated-requirerevert-checks-should-be-refactored-to-a-modifier-or-function)] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function | 3 | 
| [[N&#x2011;27](#n27-expressions-for-constant-values-should-use-immutable-rather-than-constant)] | Expressions for constant values should use `immutable` rather than `constant` | 7 | 
| [[N&#x2011;28](#n28-imports-could-be-organized-more-systematically)] | Imports could be organized more systematically | 1 | 
| [[N&#x2011;29](#n29-inconsistent-spacing-in-comments)] | Inconsistent spacing in comments | 5 | 
| [[N&#x2011;30](#n30-large-multiples-of-ten-should-use-scientific-notation)] | Large multiples of ten should use scientific notation | 8 | 
| [[N&#x2011;31](#n31-memory-safe-annotation-unnecessary)] | Memory-safe annotation unnecessary | 28 | 
| [[N&#x2011;32](#n32-missing-event-for-critical-parameter-change)] | Missing event for critical parameter change | 7 | 
| [[N&#x2011;33](#n33-multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct-for-readability)] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability | 12 | 
| [[N&#x2011;34](#n34-natspec-contract-declarations-should-have-author-tags)] | NatSpec: Contract declarations should have `@author` tags | 3 | 
| [[N&#x2011;35](#n35-natspec-contract-declarations-should-have-dev-tags)] | NatSpec: Contract declarations should have `@dev` tags | 12 | 
| [[N&#x2011;36](#n36-natspec-contract-declarations-should-have-notice-tags)] | NatSpec: Contract declarations should have `@notice` tags | 1 | 
| [[N&#x2011;37](#n37-natspec-contract-declarations-should-have-title-tags)] | NatSpec: Contract declarations should have `@title` tags | 5 | 
| [[N&#x2011;38](#n38-natspec-contract-declarations-should-have-descriptions)] | NatSpec: Contract declarations should have descriptions | 1 | 
| [[N&#x2011;39](#n39-natspec-error-declarations-should-have-dev-tags)] | NatSpec: Error declarations should have `@dev` tags | 33 | 
| [[N&#x2011;40](#n40-natspec-event-param-tag-is-missing)] | NatSpec: Event `@param` tag is missing | 62 | 
| [[N&#x2011;41](#n41-natspec-event-declarations-should-have-dev-tags)] | NatSpec: Event declarations should have `@dev` tags | 11 | 
| [[N&#x2011;42](#n42-natspec-function-param-tag-is-missing)] | NatSpec: Function `@param` tag is missing | 2 | 
| [[N&#x2011;43](#n43-natspec-function-return-tag-is-missing)] | NatSpec: Function `@return` tag is missing | 10 | 
| [[N&#x2011;44](#n44-natspec-function-declarations-should-have-dev-tags)] | NatSpec: Function declarations should have `@dev` tags | 147 | 
| [[N&#x2011;45](#n45-natspec-function-declarations-should-have-notice-tags)] | NatSpec: Function declarations should have `@notice` tags | 1 | 
| [[N&#x2011;46](#n46-natspec-function-declarations-should-have-descriptions)] | NatSpec: Function declarations should have descriptions | 1 | 
| [[N&#x2011;47](#n47-natspec-modifier-declarations-should-have-dev-tags)] | NatSpec: Modifier declarations should have `@dev` tags | 1 | 
| [[N&#x2011;48](#n48-natspec-non-public-state-variable-declarations-should-use-dev-tags)] | NatSpec: Non-public state variable declarations should use `@dev` tags | 52 | 
| [[N&#x2011;49](#n49-natspec-state-variable-declarations-should-have-descriptions)] | NatSpec: State variable declarations should have descriptions | 9 | 
| [[N&#x2011;50](#n50-natspec-use-inheritdoc-rather-than-using-a-non-standard-tags)] | NatSpec: Use `@inheritdoc` rather than using a non-standard tags | 2 | 
| [[N&#x2011;51](#n51-non-libraryinterface-files-should-use-fixed-compiler-versions-not-floating-ones)] | Non-library/interface files should use fixed compiler versions, not floating ones | 7 | 
| [[N&#x2011;52](#n52-not-using-the-named-return-variables-anywhere-in-the-function-is-confusing)] | Not using the named return variables anywhere in the function is confusing | 18 | 
| [[N&#x2011;53](#n53-numeric-values-having-to-do-with-time-should-use-time-units-for-readability)] | Numeric values having to do with time should use time units for readability | 3 | 
| [[N&#x2011;54](#n54-overflows-in-unchecked-blocks)] | Overflows in unchecked blocks | 3 | 
| [[N&#x2011;55](#n55-style-guide-extraneous-whitespace)] | Style guide: Extraneous whitespace | 18 | 
| [[N&#x2011;56](#n56-style-guide-lines-are-too-long)] | Style guide: Lines are too long | 334 | 
| [[N&#x2011;57](#n57-style-guide-local-and-state-variables-should-be-named-using-lowercamelcase)] | Style guide: Local and state variables should be named using lowerCamelCase | 3 | 
| [[N&#x2011;58](#n58-style-guide-non-externalpublic-function-names-should-begin-with-an-underscore)] | Style guide: Non-`external`/`public` function names should begin with an underscore | 5 | 
| [[N&#x2011;59](#n59-style-guide-top-level-declarations-should-be-separated-by-at-least-two-lines)] | Style guide: Top-level declarations should be separated by at least two lines | 1 | 
| [[N&#x2011;60](#n60-style-guide-variable-names-that-consist-of-all-capital-letters-should-be-reserved-for-constantimmutable-variables)] | Style guide: Variable names that consist of all capital letters should be reserved for `constant`/`immutable` variables | 1 | 
| [[N&#x2011;61](#n61-unnecessary-cast)] | Unnecessary cast | 15 | 
| [[N&#x2011;62](#n62-unused-contract-variables)] | Unused contract variables | 2 | 
| [[N&#x2011;63](#n63-unused-import)] | Unused import | 1 | 
| [[N&#x2011;64](#n64-use-bit-shifts-to-represent-powers-of-two)] | Use bit shifts to represent powers of two | 28 | 
| [[N&#x2011;65](#n65-use-of-override-is-unnecessary)] | Use of `override` is unnecessary | 4 | 
| [[N&#x2011;66](#n66-use-the-latest-solidity-prior-to-0820-if-on-l2s-for-deployment)] | Use the latest solidity (prior to 0.8.20 if on L2s) for deployment | 7 | 
| [[N&#x2011;67](#n67-variables-need-not-be-initialized-to-false)] | Variables need not be initialized to false | 5 | 
| [[N&#x2011;68](#n68-visibility-should-be-set-explicitly-rather-than-defaulting-to-internal)] | Visibility should be set explicitly rather than defaulting to `internal` | 8 | 

Total: 1640 instances over 68 issues





## Low Risk Issues


### [L&#x2011;01] Events may be emitted out of order due to reentrancy
Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls

*There are 71 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit numberOfPositions() called prior to this emission in withdraw(), via: withdraw(), maxWithdraw()
563:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

/// @audit numberOfPositions() called prior to this emission in redeem(), via: redeem(), maxRedeem()
623:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

```
*GitHub*: [563](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L563-L563), [623](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L623-L623)

```solidity
File: contracts/PanopticFactory.sol

/// @audit issueNFT() called prior to this emission in deployNewPool(), via: deployNewPool()
/// @audit slot0() called prior to this emission in deployNewPool(), via: deployNewPool(), _mintFullRange()
/// @audit mint() called prior to this emission in deployNewPool(), via: deployNewPool(), _mintFullRange()
/// @audit tickSpacing() called prior to this emission in deployNewPool(), via: deployNewPool(), _mintFullRange()
/// @audit increaseObservationCardinalityNext() called prior to this emission in deployNewPool(), via: deployNewPool()
/// @audit startPool() called prior to this emission in deployNewPool(), via: deployNewPool()
/// @audit startToken() called prior to this emission in deployNewPool(), via: deployNewPool()
/// @audit initializeAMMPool() called prior to this emission in deployNewPool(), via: deployNewPool()
/// @audit getPool() called prior to this emission in deployNewPool(), via: deployNewPool()
268          emit PoolDeployed(
269              newPoolContract,
270              v3Pool,
271              collateralTracker0,
272              collateralTracker1,
273              amount0,
274              amount1
275:         );

```
*GitHub*: [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L268-L275)

```solidity
File: contracts/PanopticPool.sol

/// @audit slot0() called prior to this emission in _mintOptions(), via: _mintOptions(), _validateSolvency()
/// @audit getAccountMarginDetails() called prior to this emission in _mintOptions(), via: _mintOptions(), _validateSolvency(), _checkSolvencyAtTick()
/// @audit observations() called prior to this emission in _mintOptions(), via: _mintOptions(), _validateSolvency(), computeMedianObservedPrice()
/// @audit observations() called prior to this emission in _mintOptions(), via: _mintOptions(), _validateSolvency(), computeInternalMedian()
/// @audit getAccountPremium() called prior to this emission in _mintOptions(), via: _mintOptions(), _validateSolvency(), _checkSolvencyAtTick(), _calculateAccumulatedPremia(), _getPremia()
/// @audit getAccountLiquidity() called prior to this emission in _mintOptions(), via: _mintOptions(), _validateSolvency(), _checkSolvencyAtTick(), _calculateAccumulatedPremia(), _getTotalLiquidity()
/// @audit getAccountPremium() called prior to this emission in _mintOptions(), via: _mintOptions(), _addUserOption()
/// @audit getAccountLiquidity() called prior to this emission in _mintOptions(), via: _mintOptions(), _addUserOption(), _checkLiquiditySpread()
/// @audit mintTokenizedPosition() called prior to this emission in _mintOptions(), via: _mintOptions(), _mintInSFPMAndUpdateCollateral()
/// @audit takeCommissionAddData() called prior to this emission in _mintOptions(), via: _mintOptions(), _mintInSFPMAndUpdateCollateral(), _payCommissionAndWriteData()
/// @audit getAccountPremium() called prior to this emission in _mintOptions(), via: _mintOptions(), _mintInSFPMAndUpdateCollateral(), _updateSettlementPostMint()
/// @audit getAccountLiquidity() called prior to this emission in _mintOptions(), via: _mintOptions(), _mintInSFPMAndUpdateCollateral(), _updateSettlementPostMint(), _getTotalLiquidity()
/// @audit getPoolId() called prior to this emission in _mintOptions(), via: _mintOptions()
666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);

/// @audit getAccountLiquidity() called prior to this emission in _burnOptions(), via: _burnOptions(), _updatePositionDataBurn(), _checkLiquiditySpread()
/// @audit burnTokenizedPosition() called prior to this emission in _burnOptions(), via: _burnOptions(), _burnAndHandleExercise()
/// @audit exercise() called prior to this emission in _burnOptions(), via: _burnOptions(), _burnAndHandleExercise()
/// @audit getAccountPremium() called prior to this emission in _burnOptions(), via: _burnOptions(), _burnAndHandleExercise(), _updateSettlementPostBurn(), _getPremia()
/// @audit getAccountLiquidity() called prior to this emission in _burnOptions(), via: _burnOptions(), _burnAndHandleExercise(), _updateSettlementPostBurn(), _getTotalLiquidity()
853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

/// @audit getAccountMarginDetails() called prior to this emission in liquidate(), via: liquidate(), _checkSolvencyAtTick()
/// @audit getAccountPremium() called prior to this emission in liquidate(), via: liquidate(), _checkSolvencyAtTick(), _calculateAccumulatedPremia(), _getPremia()
/// @audit getAccountLiquidity() called prior to this emission in liquidate(), via: liquidate(), _checkSolvencyAtTick(), _calculateAccumulatedPremia(), _getTotalLiquidity()
/// @audit revoke() called prior to this emission in liquidate(), via: liquidate()
/// @audit slot0() called prior to this emission in liquidate(), via: liquidate()
/// @audit exercise() called prior to this emission in liquidate(), via: liquidate(), haircutPremia()
/// @audit burnTokenizedPosition() called prior to this emission in liquidate(), via: liquidate(), _burnAllOptionsFrom(), _burnOptions(), _burnAndHandleExercise()
/// @audit exercise() called prior to this emission in liquidate(), via: liquidate(), _burnAllOptionsFrom(), _burnOptions(), _burnAndHandleExercise()
/// @audit getAccountLiquidity() called prior to this emission in liquidate(), via: liquidate(), _burnAllOptionsFrom(), _burnOptions(), _updatePositionDataBurn(), _checkLiquiditySpread()
/// @audit getAccountPremium() called prior to this emission in liquidate(), via: liquidate(), _burnAllOptionsFrom(), _burnOptions(), _burnAndHandleExercise(), _updateSettlementPostBurn(), _getPremia()
/// @audit getAccountLiquidity() called prior to this emission in liquidate(), via: liquidate(), _burnAllOptionsFrom(), _burnOptions(), _burnAndHandleExercise(), _updateSettlementPostBurn(), _getTotalLiquidity()
/// @audit delegate() called prior to this emission in liquidate(), via: liquidate()
/// @audit getAccountMarginDetails() called prior to this emission in liquidate(), via: liquidate()
/// @audit getAccountPremium() called prior to this emission in liquidate(), via: liquidate(), _calculateAccumulatedPremia(), _getPremia()
/// @audit getAccountLiquidity() called prior to this emission in liquidate(), via: liquidate(), _calculateAccumulatedPremia(), _getTotalLiquidity()
/// @audit observe() called prior to this emission in liquidate(), via: liquidate(), getUniV3TWAP(), twapFilter()
1170:        emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

/// @audit slot0() called prior to this emission in forceExercise(), via: forceExercise(), _validateSolvency()
/// @audit getAccountMarginDetails() called prior to this emission in forceExercise(), via: forceExercise(), _validateSolvency(), _checkSolvencyAtTick()
/// @audit observations() called prior to this emission in forceExercise(), via: forceExercise(), _validateSolvency(), computeMedianObservedPrice()
/// @audit observations() called prior to this emission in forceExercise(), via: forceExercise(), _validateSolvency(), computeInternalMedian()
/// @audit getAccountPremium() called prior to this emission in forceExercise(), via: forceExercise(), _validateSolvency(), _checkSolvencyAtTick(), _calculateAccumulatedPremia(), _getPremia()
/// @audit getAccountLiquidity() called prior to this emission in forceExercise(), via: forceExercise(), _validateSolvency(), _checkSolvencyAtTick(), _calculateAccumulatedPremia(), _getTotalLiquidity()
/// @audit refund() called prior to this emission in forceExercise(), via: forceExercise()
/// @audit convertToAssets() called prior to this emission in forceExercise(), via: forceExercise(), getRefundAmounts()
/// @audit balanceOf() called prior to this emission in forceExercise(), via: forceExercise(), getRefundAmounts()
/// @audit exerciseCost() called prior to this emission in forceExercise(), via: forceExercise()
/// @audit burnTokenizedPosition() called prior to this emission in forceExercise(), via: forceExercise(), _burnAllOptionsFrom(), _burnOptions(), _burnAndHandleExercise()
/// @audit exercise() called prior to this emission in forceExercise(), via: forceExercise(), _burnAllOptionsFrom(), _burnOptions(), _burnAndHandleExercise()
/// @audit getAccountLiquidity() called prior to this emission in forceExercise(), via: forceExercise(), _burnAllOptionsFrom(), _burnOptions(), _updatePositionDataBurn(), _checkLiquiditySpread()
/// @audit getAccountPremium() called prior to this emission in forceExercise(), via: forceExercise(), _burnAllOptionsFrom(), _burnOptions(), _burnAndHandleExercise(), _updateSettlementPostBurn(), _getPremia()
/// @audit getAccountLiquidity() called prior to this emission in forceExercise(), via: forceExercise(), _burnAllOptionsFrom(), _burnOptions(), _burnAndHandleExercise(), _updateSettlementPostBurn(), _getTotalLiquidity()
/// @audit delegate() called prior to this emission in forceExercise(), via: forceExercise()
/// @audit getAccountPremium() called prior to this emission in forceExercise(), via: forceExercise(), _calculateAccumulatedPremia(), _getPremia()
/// @audit getAccountLiquidity() called prior to this emission in forceExercise(), via: forceExercise(), _calculateAccumulatedPremia(), _getTotalLiquidity()
/// @audit slot0() called prior to this emission in forceExercise(), via: forceExercise()
/// @audit observe() called prior to this emission in forceExercise(), via: forceExercise(), getUniV3TWAP(), twapFilter()
1277:        emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

/// @audit getAccountPremium() called prior to this emission in settleLongPremium(), via: settleLongPremium()
/// @audit slot0() called prior to this emission in settleLongPremium(), via: settleLongPremium()
/// @audit exercise() called prior to this emission in settleLongPremium(), via: settleLongPremium()
1654:            emit PremiumSettled(owner, tokenId, realizedPremia);

```
*GitHub*: [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L666-L666), [853](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L853-L853), [853](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L853-L853), [853](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L853-L853), [853](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L853-L853), [853](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L853-L853), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1170-L1170), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1277-L1277), [1654](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1654-L1654), [1654](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1654-L1654), [1654](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1654-L1654)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit tickSpacing() called prior to this emission in initializeAMMPool(), via: initializeAMMPool(), getPoolId()
/// @audit getPool() called prior to this emission in initializeAMMPool(), via: initializeAMMPool()
390:         emit PoolInitialized(univ3pool, poolId);

/// @audit onERC1155Received() called prior to this emission in mintTokenizedPosition(), via: mintTokenizedPosition(), _mint()
517:         emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);

```
*GitHub*: [390](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L390-L390), [390](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L390-L390), [517](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L517-L517)



### [L&#x2011;02] File allows a version of solidity that is susceptible to `.selector`-related optimizer bug
In solidity versions prior to 0.8.21, there is a legacy code generation [bug](https://soliditylang.org/blog/2023/07/19/missing-side-effects-on-selector-access-bug/) where if `foo().selector` is called, `foo()` doesn't actually get evaluated. It is listed as low-severity, because projects usually use the contract name rather than a function call to look up the selector. I've flagged all files using `.selector` where the version is vulnerable.

*There is one instance of this issue:*

```solidity
File: contracts/tokens/ERC1155Minimal.sol

2:   pragma solidity ^0.8.0;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L2-L2)



### [L&#x2011;03] Input array lengths may differ
If the caller makes a copy-paste error, the lengths may be mismatched and an operation believed to have been completed may not in fact have been completed (e.g. if the array being iterated over is shorter than the one being indexed into).

*There are 4 instances of this issue:*

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit amounts[]
577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);

```
*GitHub*: [577](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L577-L577)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit premiasByLeg[]
786:                         longPremium = longPremium.sub(premiasByLeg[i][leg]);

```
*GitHub*: [786](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L786-L786)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit amounts[]
145:             amount = amounts[i];

/// @audit ids[]
188:                 balances[i] = balanceOf[owners[i]][ids[i]];

```
*GitHub*: [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L145-L145), [188](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L188-L188)


## Non-critical Issues


### [N&#x2011;01] `2**<n> - 1` should be re-written as `type(uint<n>).max`
Earlier versions of solidity can use `uint<n>(-1)` instead. Expressions not including the `- 1` can often be re-written to accommodate the change (e.g. by using a `>` rather than a `>=`, which will also save some gas)

*There are 23 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

1348:                Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

1353:                Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

1487:            effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

1552:                                        (liquidityChunk.liquidity())) / 2 ** 64

1561:                                        (liquidityChunk.liquidity())) / 2 ** 64

1635:                .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1636:                .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1769:                totalLiquidity) / 2 ** 64;

1771:                totalLiquidity) / 2 ** 64;

1942:                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),

1959:                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,

```
*GitHub*: [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L165-L165), [1348](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1348-L1348), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1353-L1353), [1487](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1487-L1487), [1552](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1552-L1552), [1561](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1561-L1561), [1635](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1635-L1635), [1636](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1636-L1636), [1769](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1769-L1769), [1771](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1771-L1771), [1942](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1942-L1942), [1959](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1959-L1959)

```solidity
File: contracts/SemiFungiblePositionManager.sol

1352:                    totalLiquidity * 2 ** 64,

1357:                    totalLiquidity * 2 ** 64,

```
*GitHub*: [1352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1352-L1352), [1357](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1357-L1357)

```solidity
File: contracts/types/TokenId.sol

98:              return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

376:             if (optionRatios < 2 ** 64) {

378:             } else if (optionRatios < 2 ** 112) {

380:             } else if (optionRatios < 2 ** 160) {

382:             } else if (optionRatios < 2 ** 208) {

439:         if (optionRatios < 2 ** 64) {

441:         } else if (optionRatios < 2 ** 112) {

443:         } else if (optionRatios < 2 ** 160) {

445:         } else if (optionRatios < 2 ** 208) {

```
*GitHub*: [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L98-L98), [376](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L376-L376), [378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L378-L378), [380](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L380-L380), [382](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L382-L382), [439](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L439-L439), [441](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L441-L441), [443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L443-L443), [445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L445-L445)



### [N&#x2011;02] `constant`s should be defined rather than using magic numbers
Even [assembly](https://github.com/code-423n4/2022-05-opensea-seaport/blob/9d7ce4d08bf3c3010304a0476a785c70c0e90ae7/contracts/lib/TokenTransferrer.sol#L35-L39) can benefit from using readable constants instead of hex/numeric literals

*There are 2 instances of this issue:*

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit 0x01ffc9a7
202:             interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

/// @audit 0xd9b67a26
203:             interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

```
*GitHub*: [202](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L202-L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L203-L203)



### [N&#x2011;03] `else`-block not required
One level of nesting can be removed by not having an `else` block when the `if`-block returns, and `if (foo) { return 1; } else { return 2; }` becomes `if (foo) { return 1; } return 2;`. A following `else if` can become `if`

*There is one instance of this issue:*

```solidity
File: contracts/SemiFungiblePositionManager.sol

1013                 if (startingLiquidity < chunkLiquidity) {
1014                     // the amount we want to move (liquidityChunk.legLiquidity()) out of uniswap is greater than
1015                     // what the account that owns the liquidity in uniswap has (startingLiquidity)
1016:                    // we must ensure that an account can only move its own liquidity out of uniswap

```
*GitHub*: [1013](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1013-L1028)



### [N&#x2011;04] `if`-statement can be converted to a ternary
The code can be made more compact while also increasing readability by converting the following `if`-statements to ternaries (e.g. `foo += (x > y) ? a : b`)

*There are 5 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

1544                 if (tokenType == 0) {
1545                     spreadRequirement = movedRight < movedPartnerRight
1546                         ? movedPartnerRight - movedRight
1547                         : movedRight - movedPartnerRight;
1548                 } else {
1549                     spreadRequirement = movedLeft < movedPartnerLeft
1550                         ? movedPartnerLeft - movedLeft
1551                         : movedLeft - movedPartnerLeft;
1552:                }

```
*GitHub*: [1544](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1544-L1552)

```solidity
File: contracts/libraries/PanopticMath.sol

325          if (tokenId.asset(legIndex) == 0) {
326              return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
327          } else {
328              return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
329:         }

425          if (tokenType == 0) {
426              return (
427                  tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
428                  tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
429              );
430          } else {
431              return (
432                  tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
433                  tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
434              );
435:         }

494              if (sqrtPriceX96 < type(uint128).max) {
495                  return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
496              } else {
497                  return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
498:             }

511              if (sqrtPriceX96 < type(uint128).max) {
512                  return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
513              } else {
514                  return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
515:             }

```
*GitHub*: [325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L325-L329), [425](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L425-L435), [494](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L494-L498), [511](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L511-L515)



### [N&#x2011;05] `public` functions not called by the contract should be declared `external` instead
Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`.

*There are 2 instances of this issue:*

```solidity
File: contracts/SemiFungiblePositionManager.sol

540       function safeTransferFrom(
541           address from,
542           address to,
543           uint256 id,
544           uint256 amount,
545:          bytes calldata data

566       function safeBatchTransferFrom(
567           address from,
568           address to,
569           uint256[] calldata ids,
570           uint256[] calldata amounts,
571:          bytes calldata data

```
*GitHub*: [540](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L540-L545), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L566-L571)



### [N&#x2011;06] Add inline comments for unnamed variables
`function foo(address x, address)` -> `function foo(address x, address /* y */)`

*There are 2 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

391       /// @return maxAssets The maximum amount of assets that can be deposited.
392:      function maxDeposit(address) external pure returns (uint256 maxAssets) {

443       /// @return maxShares The maximum amount of shares that can be minted.
444:      function maxMint(address) external view returns (uint256 maxShares) {

```
*GitHub*: [391](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L391-L392), [443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L443-L444)



### [N&#x2011;07] Assembly blocks should have extensive comments
Assembly blocks take a lot more time to audit than normal Solidity code, and often have gotchas and side-effects that the Solidity versions of the same code do not. Consider adding more comments explaining what is being done in every step of the assembly code, and describe why assembly is being used instead of Solidity.

*There are 21 instances of this issue:*

```solidity
File: contracts/libraries/Math.sol

353               assembly ("memory-safe") {
354                   let mm := mulmod(a, b, not(0))
355                   prod0 := mul(a, b)
356                   prod1 := sub(sub(mm, prod0), lt(mm, prod0))
357:              }

362                   assembly ("memory-safe") {
363                       result := div(prod0, denominator)
364:                  }

379               assembly ("memory-safe") {
380                   remainder := mulmod(a, b, denominator)
381:              }

383               assembly ("memory-safe") {
384                   prod1 := sub(prod1, gt(remainder, prod0))
385                   prod0 := sub(prod0, remainder)
386:              }

393               assembly ("memory-safe") {
394                   denominator := div(denominator, twos)
395:              }

398               assembly ("memory-safe") {
399                   prod0 := div(prod0, twos)
400:              }

404               assembly ("memory-safe") {
405                   twos := add(div(sub(0, twos), twos), 1)
406:              }

467               assembly ("memory-safe") {
468                   let mm := mulmod(a, b, not(0))
469                   prod0 := mul(a, b)
470                   prod1 := sub(sub(mm, prod0), lt(mm, prod0))
471:              }

493               assembly ("memory-safe") {
494                   remainder := mulmod(a, b, 0x10000000000000000)
495:              }

497               assembly ("memory-safe") {
498                   prod1 := sub(prod1, gt(remainder, prod0))
499                   prod0 := sub(prod0, remainder)
500:              }

530               assembly ("memory-safe") {
531                   let mm := mulmod(a, b, not(0))
532                   prod0 := mul(a, b)
533                   prod1 := sub(sub(mm, prod0), lt(mm, prod0))
534:              }

556               assembly ("memory-safe") {
557                   remainder := mulmod(a, b, 0x1000000000000000000000000)
558:              }

560               assembly ("memory-safe") {
561                   prod1 := sub(prod1, gt(remainder, prod0))
562                   prod0 := sub(prod0, remainder)
563:              }

607               assembly ("memory-safe") {
608                   let mm := mulmod(a, b, not(0))
609                   prod0 := mul(a, b)
610                   prod1 := sub(sub(mm, prod0), lt(mm, prod0))
611:              }

633               assembly ("memory-safe") {
634                   remainder := mulmod(a, b, 0x100000000000000000000000000000000)
635:              }

637               assembly ("memory-safe") {
638                   prod1 := sub(prod1, gt(remainder, prod0))
639                   prod0 := sub(prod0, remainder)
640:              }

684               assembly ("memory-safe") {
685                   let mm := mulmod(a, b, not(0))
686                   prod0 := mul(a, b)
687                   prod1 := sub(sub(mm, prod0), lt(mm, prod0))
688:              }

710               assembly ("memory-safe") {
711                   remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)
712:              }

714               assembly ("memory-safe") {
715                   prod1 := sub(prod1, gt(remainder, prod0))
716                   prod0 := sub(prod0, remainder)
717:              }

739           assembly ("memory-safe") {
740               result := add(div(a, b), gt(mod(a, b), 0))
741:          }

```
*GitHub*: [353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L353-L357), [362](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L362-L364), [379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L379-L381), [383](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L383-L386), [393](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L393-L395), [398](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L398-L400), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L404-L406), [467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L467-L471), [493](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L493-L495), [497](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L497-L500), [530](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L530-L534), [556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L556-L558), [560](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L560-L563), [607](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L607-L611), [633](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L633-L635), [637](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L637-L640), [684](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L684-L688), [710](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L710-L712), [714](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L714-L717), [739](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L739-L741)

```solidity
File: contracts/multicall/Multicall.sol

25                    assembly ("memory-safe") {
26                        revert(add(result, 32), mload(result))
27:                   }

```
*GitHub*: [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L25-L27)



### [N&#x2011;08] Avoid mutating `function`/`modifier` parameters of non-utility functions
Use a local variable instead

*There are 9 instances of this issue:*

```solidity
File: contracts/PanopticFactory.sol

217:         (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);

217:         (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);

```
*GitHub*: [217](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L211-L211), [217](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L212-L212)

```solidity
File: contracts/PanopticPool.sol

630:         (tickLimitLow, tickLimitHigh) = _getSlippageLimits(tickLimitLow, tickLimitHigh);

630:         (tickLimitLow, tickLimitHigh) = _getSlippageLimits(tickLimitLow, tickLimitHigh);

834:         (tickLimitLow, tickLimitHigh) = _getSlippageLimits(tickLimitLow, tickLimitHigh);

834:         (tickLimitLow, tickLimitHigh) = _getSlippageLimits(tickLimitLow, tickLimitHigh);

```
*GitHub*: [630](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L618-L618), [630](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L619-L619), [834](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L830-L830), [834](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L831-L831)

```solidity
File: contracts/SemiFungiblePositionManager.sol

692:             tokenId = tokenId.flipToBurnToken();

721:             (tickLimitLow, tickLimitHigh) = (tickLimitHigh, tickLimitLow);

721:             (tickLimitLow, tickLimitHigh) = (tickLimitHigh, tickLimitLow);

```
*GitHub*: [692](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L681-L681), [721](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L683-L683), [721](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L684-L684)



### [N&#x2011;09] Common functions should be refactored to a common base contract
The functions below have the same implementation as is seen in other files. The functions should be refactored into functions of a common base contract

*There are 2 instances of this issue:*

```solidity
File: contracts/libraries/Math.sol

41       function min(uint256 a, uint256 b) internal pure returns (uint256) {
42           return a < b ? a : b;
43:      }

57       function max(uint256 a, uint256 b) internal pure returns (uint256) {
58           return a > b ? a : b;
59:      }

```
*GitHub*: [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L41-L43), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L57-L59)



### [N&#x2011;10] Consider defining system-wide constants in a single file
`ContA.X = 0`, `ContB.Y = 1`, `ContC.Z = 2` -> `ContConstants.X = 0`, `ContConstants.Y = 1`, `ContConstants.Z = 2`; `ContA.X = X`, `ContB.Y = Y`, `ContC.Z = Z`,

*There are 28 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

70:      string internal constant TICKER_PREFIX = "po";

73:      string internal constant NAME_PREFIX = "POPT-V1";

77:      uint256 internal constant DECIMALS = 10_000;

81:      int128 internal constant DECIMALS_128 = 10_000;

```
*GitHub*: [70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L70-L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L73-L73), [77](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L77-L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L81-L81)

```solidity
File: contracts/PanopticFactory.sol

82:      uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;

86:      uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

89:      uint16 internal constant CARDINALITY_INCREASE = 100;

```
*GitHub*: [82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L82-L82), [86](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L86-L86), [89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L89-L89)

```solidity
File: contracts/PanopticPool.sol

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

168:     uint64 internal constant MAX_POSITIONS = 32;

171:     uint256 internal constant BP_DECREASE_BUFFER = 13_333;

174:     uint256 internal constant NO_BUFFER = 10_000;

```
*GitHub*: [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L109-L109), [111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L111-L111), [114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L114-L114), [119](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L119-L119), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L120-L120), [123](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L123-L123), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L128-L128), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L133-L133), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L136-L136), [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L139-L139), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L145-L145), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L148-L148), [152](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L152-L152), [156](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L156-L156), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L160-L160), [168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L168-L168), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L171-L171), [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L174-L174)

```solidity
File: contracts/SemiFungiblePositionManager.sol

125:     bool internal constant MINT = false;

126:     bool internal constant BURN = true;

133:     uint128 private constant VEGOID = 2;

```
*GitHub*: [125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L125-L125), [126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L126-L126), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L133-L133)



### [N&#x2011;11] Consider emitting an event at the end of the constructor
This will allow users to easily exactly pinpoint when and by whom a contract was constructed

*There are 4 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

178      constructor(
179          uint256 _commissionFee,
180          uint256 _sellerCollateralRatio,
181          uint256 _buyerCollateralRatio,
182          int256 _forceExerciseCost,
183          uint256 _targetPoolUtilization,
184          uint256 _saturatedPoolUtilization,
185          uint256 _ITMSpreadMultiplier
186:     ) {

```
*GitHub*: [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L178-L186)

```solidity
File: contracts/PanopticFactory.sol

115      constructor(
116          address _WETH9,
117          SemiFungiblePositionManager _SFPM,
118          IUniswapV3Factory _univ3Factory,
119          IDonorNFT _donorNFT,
120          address _poolReference,
121          address _collateralReference
122:     ) {

```
*GitHub*: [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L115-L122)

```solidity
File: contracts/PanopticPool.sol

280:     constructor(SemiFungiblePositionManager _sfpm) {

```
*GitHub*: [280](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L280-L280)

```solidity
File: contracts/SemiFungiblePositionManager.sol

341:     constructor(IUniswapV3Factory _factory) {

```
*GitHub*: [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L341-L341)



### [N&#x2011;12] Consider making contracts `Upgradeable`
This allows for bugs to be fixed in production, at the expense of _significantly_ increasing centralization.

*There are 4 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

36   contract CollateralTracker is ERC20Minimal, Multicall {
37:      // Used for safecasting

```
*GitHub*: [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L36-L37)

```solidity
File: contracts/PanopticFactory.sol

26   contract PanopticFactory is Multicall {
27       /*//////////////////////////////////////////////////////////////
28                                    EVENTS
29       //////////////////////////////////////////////////////////////*/
30   
31       /// @notice Emitted when the ownership of the factory is transferred.
32       /// @param oldOwner The previous owner of the factory
33:      /// @param newOwner The new owner of the factory

```
*GitHub*: [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L26-L33)

```solidity
File: contracts/PanopticPool.sol

27   contract PanopticPool is ERC1155Holder, Multicall {
28       /*//////////////////////////////////////////////////////////////
29                                   EVENTS
30       //////////////////////////////////////////////////////////////*/
31   
32       /// @notice Emitted when an account is liquidated.
33       /// @dev Need to unpack bonusAmounts to get raw numbers, which are always positive.
34       /// @param liquidator Address of the caller whom is liquidating the distressed account.
35       /// @param liquidatee Address of the distressed/liquidatable account.
36       /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.
37:      /// The token0 bonus is in the right slot, and token1 bonus is in the left slot.

```
*GitHub*: [27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L27-L37)

```solidity
File: contracts/SemiFungiblePositionManager.sol

72   contract SemiFungiblePositionManager is ERC1155, Multicall {
73       /*//////////////////////////////////////////////////////////////
74                                    EVENTS
75       //////////////////////////////////////////////////////////////*/
76   
77       /// @notice Emitted when a UniswapV3Pool is initialized.
78       /// @param uniswapPool Address of the underlying Uniswap v3 pool
79:      /// @param poolId The SFPM's pool identifier for the pool, including the 16-bit tick spacing and 48-bit pool pattern

```
*GitHub*: [72](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L72-L79)



### [N&#x2011;13] Consider returning a `struct` rather than having multiple `return` values


*There are 7 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

277      function getPoolData()
278          external
279          view
280          returns (uint256 poolAssets, uint256 insideAMM, int256 currentPoolUtilization)
281:     {

```
*GitHub*: [277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L277-L281)

```solidity
File: contracts/PanopticPool.sol

352      function optionPositionBalance(
353          address user,
354          TokenId tokenId
355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

381      function calculateAccumulatedFeesBatch(
382          address user,
383          bool includePendingPremium,
384          TokenId[] calldata positionIdList
385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

955      function _burnAndHandleExercise(
956          bool commitLongSettled,
957          int24 tickLimitLow,
958          int24 tickLimitHigh,
959          TokenId tokenId,
960          uint128 positionSize,
961          address owner
962      )
963          internal
964          returns (
965              LeftRightSigned realizedPremia,
966              LeftRightSigned[4] memory premiaByLeg,
967              LeftRightSigned paidAmounts
968          )
969:     {

```
*GitHub*: [352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L352-L355), [381](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L381-L385), [955](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L955-L969)

```solidity
File: contracts/SemiFungiblePositionManager.sol

863      function _createPositionInAMM(
864          IUniswapV3Pool univ3pool,
865          TokenId tokenId,
866          uint128 positionSize,
867          bool isBurn
868      )
869          internal
870          returns (
871              LeftRightSigned totalMoved,
872              LeftRightUnsigned[4] memory collectedByLeg,
873              LeftRightSigned itmAmounts
874          )
875:     {

958      function _createLegInAMM(
959          IUniswapV3Pool univ3pool,
960          TokenId tokenId,
961          uint256 leg,
962          LiquidityChunk liquidityChunk,
963          bool isBurn
964      )
965          internal
966          returns (
967              LeftRightSigned moved,
968              LeftRightSigned itmAmounts,
969              LeftRightUnsigned collectedSingleLeg
970          )
971:     {

```
*GitHub*: [863](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L863-L875), [958](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L958-L971)

```solidity
File: contracts/libraries/PanopticMath.sol

651      function getLiquidationBonus(
652          LeftRightUnsigned tokenData0,
653          LeftRightUnsigned tokenData1,
654          uint160 sqrtPriceX96Twap,
655          uint160 sqrtPriceX96Final,
656          LeftRightSigned netExchanged,
657          LeftRightSigned premia
658:     ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

```
*GitHub*: [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651-L658)



### [N&#x2011;14] Consider splitting complex checks into multiple steps
Assign the expression's parts to intermediate local variables, and check against those instead

*There is one instance of this issue:*

```solidity
File: contracts/types/TokenId.sol

566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

```
*GitHub*: [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L566-L566)



### [N&#x2011;15] Consider using `delete` rather than assigning zero/false to clear values
The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic

*There are 5 instances of this issue:*

```solidity
File: contracts/SemiFungiblePositionManager.sol

332:         s_poolContext[poolId].locked = false;

```
*GitHub*: [332](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L332-L332)

```solidity
File: contracts/libraries/PanopticMath.sol

220:                         below = false;

850:                 collateralDelta0 = 0;

851:                 collateralDelta1 = 0;

```
*GitHub*: [220](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L220-L220), [850](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L850-L850), [851](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L851-L851)

```solidity
File: contracts/types/TokenId.sol

377:                 optionRatios = 0;

```
*GitHub*: [377](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L377-L377)



### [N&#x2011;16] Consider using a `struct` rather than having many function input parameters
Often times, a subset of the parameters would be more clear if they were passed as a struct

*There are 37 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

178      constructor(
179          uint256 _commissionFee,
180          uint256 _sellerCollateralRatio,
181          uint256 _buyerCollateralRatio,
182          int256 _forceExerciseCost,
183          uint256 _targetPoolUtilization,
184          uint256 _saturatedPoolUtilization,
185          uint256 _ITMSpreadMultiplier
186:     ) {

221      function startToken(
222          bool underlyingIsToken0,
223          address token0,
224          address token1,
225          uint24 fee,
226          PanopticPool panopticPool
227:     ) external {

650      function exerciseCost(
651          int24 currentTick,
652          int24 oracleTick,
653          TokenId positionId,
654          uint128 positionBalance,
655          LeftRightSigned longAmounts
656      ) external view returns (LeftRightSigned exerciseFees) {
657:         // find the leg furthest to the strike price 'currentTick'; this will have the lowest exercise cost

1043     function exercise(
1044         address optionOwner,
1045         int128 longAmount,
1046         int128 shortAmount,
1047         int128 swappedAmount,
1048         int128 realizedPremium
1049:    ) external onlyPanopticPool returns (int128) {

1278     function _getRequiredCollateralSingleLeg(
1279         TokenId tokenId,
1280         uint256 index,
1281         uint128 positionSize,
1282         int24 atTick,
1283         uint128 poolUtilization
1284:    ) internal view returns (uint256 required) {

1311     function _getRequiredCollateralSingleLegNoPartner(
1312         TokenId tokenId,
1313         uint256 index,
1314         uint128 positionSize,
1315         int24 atTick,
1316         uint128 poolUtilization
1317:    ) internal view returns (uint256 required) {

1439     function _getRequiredCollateralSingleLegPartner(
1440         TokenId tokenId,
1441         uint256 index,
1442         uint128 positionSize,
1443         int24 atTick,
1444         uint128 poolUtilization
1445:    ) internal view returns (uint256 required) {

1510     function _computeSpread(
1511         TokenId tokenId,
1512         uint128 positionSize,
1513         uint256 index,
1514         uint256 partnerIndex,
1515         uint128 poolUtilization
1516:    ) internal view returns (uint256 spreadRequirement) {

1600     function _computeStrangle(
1601         TokenId tokenId,
1602         uint256 index,
1603         uint128 positionSize,
1604         int24 atTick,
1605         uint128 poolUtilization
1606:    ) internal view returns (uint256 strangleRequired) {

```
*GitHub*: [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L178-L186), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L221-L227), [650](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L650-L657), [1043](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1043-L1049), [1278](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1278-L1284), [1311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1311-L1317), [1439](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1439-L1445), [1510](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1510-L1516), [1600](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1600-L1606)

```solidity
File: contracts/PanopticFactory.sol

115      constructor(
116          address _WETH9,
117          SemiFungiblePositionManager _SFPM,
118          IUniswapV3Factory _univ3Factory,
119          IDonorNFT _donorNFT,
120          address _poolReference,
121          address _collateralReference
122:     ) {

```
*GitHub*: [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L115-L122)

```solidity
File: contracts/PanopticPool.sol

291      function startPool(
292          IUniswapV3Pool _univ3pool,
293          address token0,
294          address token1,
295          CollateralTracker collateralTracker0,
296          CollateralTracker collateralTracker1
297:     ) external {

429      function _calculateAccumulatedPremia(
430          address user,
431          TokenId[] calldata positionIdList,
432          bool computeAllPremia,
433          bool includePendingPremium,
434          int24 atTick
435:     ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

547      function mintOptions(
548          TokenId[] calldata positionIdList,
549          uint128 positionSize,
550          uint64 effectiveLiquidityLimitX32,
551          int24 tickLimitLow,
552          int24 tickLimitHigh
553:     ) external {

614      function _mintOptions(
615          TokenId[] calldata positionIdList,
616          uint128 positionSize,
617          uint64 effectiveLiquidityLimitX32,
618          int24 tickLimitLow,
619          int24 tickLimitHigh
620:     ) internal {

794      function _burnAllOptionsFrom(
795          address owner,
796          int24 tickLimitLow,
797          int24 tickLimitHigh,
798          bool commitLongSettled,
799          TokenId[] calldata positionIdList
800:     ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

826      function _burnOptions(
827          bool commitLongSettled,
828          TokenId tokenId,
829          address owner,
830          int24 tickLimitLow,
831          int24 tickLimitHigh
832:     ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

955      function _burnAndHandleExercise(
956          bool commitLongSettled,
957          int24 tickLimitLow,
958          int24 tickLimitHigh,
959          TokenId tokenId,
960          uint128 positionSize,
961          address owner
962      )
963          internal
964          returns (
965              LeftRightSigned realizedPremia,
966              LeftRightSigned[4] memory premiaByLeg,
967              LeftRightSigned paidAmounts
968          )
969:     {

1290     function _checkSolvencyAtTick(
1291         address account,
1292         TokenId[] calldata positionIdList,
1293         int24 currentTick,
1294         int24 atTick,
1295         uint256 buffer
1296:    ) internal view returns (bool) {

1465     function _checkLiquiditySpread(
1466         TokenId tokenId,
1467         uint256 leg,
1468         int24 tickLower,
1469         int24 tickUpper,
1470         uint64 effectiveLiquidityLimitX32
1471:    ) internal view {

1503     function _getPremia(
1504         TokenId tokenId,
1505         uint128 positionSize,
1506         address owner,
1507         bool computeAllPremia,
1508         int24 atTick
1509     )
1510         internal
1511         view
1512         returns (
1513             LeftRightSigned[4] memory premiaByLeg,
1514             uint256[2][4] memory premiumAccumulatorsByLeg
1515         )
1516:    {

1757     function _getAvailablePremium(
1758         uint256 totalLiquidity,
1759         LeftRightUnsigned settledTokens,
1760         LeftRightUnsigned grossPremiumLast,
1761         LeftRightUnsigned premiumOwed,
1762         uint256[2] memory premiumAccumulators
1763:    ) internal pure returns (LeftRightUnsigned) {

1833     function _updateSettlementPostBurn(
1834         address owner,
1835         TokenId tokenId,
1836         LeftRightUnsigned[4] memory collectedByLeg,
1837         uint128 positionSize,
1838         bool commitLongSettled
1839:    ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {

```
*GitHub*: [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L291-L297), [429](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L429-L435), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L547-L553), [614](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L614-L620), [794](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L794-L800), [826](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L826-L832), [955](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L955-L969), [1290](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1290-L1296), [1465](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1465-L1471), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1503-L1516), [1757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1757-L1763), [1833](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1833-L1839)

```solidity
File: contracts/SemiFungiblePositionManager.sol

680      function _validateAndForwardToAMM(
681          TokenId tokenId,
682          uint128 positionSize,
683          int24 tickLimitLow,
684          int24 tickLimitHigh,
685          bool isBurn
686:     ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

958      function _createLegInAMM(
959          IUniswapV3Pool univ3pool,
960          TokenId tokenId,
961          uint256 leg,
962          LiquidityChunk liquidityChunk,
963          bool isBurn
964      )
965          internal
966          returns (
967              LeftRightSigned moved,
968              LeftRightSigned itmAmounts,
969              LeftRightUnsigned collectedSingleLeg
970          )
971:     {

1255     function _collectAndWritePositionData(
1256         LiquidityChunk liquidityChunk,
1257         IUniswapV3Pool univ3pool,
1258         LeftRightUnsigned currentLiquidity,
1259         bytes32 positionKey,
1260         LeftRightSigned movedInLeg,
1261         uint256 isLong
1262:    ) internal returns (LeftRightUnsigned collectedChunk) {

1421     function getAccountLiquidity(
1422         address univ3pool,
1423         address owner,
1424         uint256 tokenType,
1425         int24 tickLower,
1426         int24 tickUpper
1427:    ) external view returns (LeftRightUnsigned accountLiquidities) {

1449     function getAccountPremium(
1450         address univ3pool,
1451         address owner,
1452         uint256 tokenType,
1453         int24 tickLower,
1454         int24 tickUpper,
1455         int24 atTick,
1456         uint256 isLong
1457:    ) external view returns (uint128, uint128) {

1535     function getAccountFeesBase(
1536         address univ3pool,
1537         address owner,
1538         uint256 tokenType,
1539         int24 tickLower,
1540         int24 tickUpper
1541:    ) external view returns (int128 feesBase0, int128 feesBase1) {

```
*GitHub*: [680](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L680-L686), [958](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L958-L971), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1255-L1262), [1421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1421-L1427), [1449](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1449-L1457), [1535](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1535-L1541)

```solidity
File: contracts/libraries/FeesCalc.sol

97       function calculateAMMSwapFees(
98           IUniswapV3Pool univ3pool,
99           int24 currentTick,
100          int24 tickLower,
101          int24 tickUpper,
102          uint128 liquidity
103      ) public view returns (LeftRightSigned) {
104          // extract the amount of AMM fees collected within the liquidity chunk`
105:         // note: the fee variables are *per unit of liquidity*; so more "rate" variables

```
*GitHub*: [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L97-L105)

```solidity
File: contracts/libraries/InteractionHelper.sol

24       function doApprovals(
25           SemiFungiblePositionManager sfpm,
26           CollateralTracker ct0,
27           CollateralTracker ct1,
28           address token0,
29           address token1
30:      ) external {

48       function computeName(
49           address token0,
50           address token1,
51           bool isToken0,
52           uint24 fee,
53           string memory prefix
54:      ) external view returns (string memory) {

```
*GitHub*: [24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L24-L30), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L48-L54)

```solidity
File: contracts/libraries/PanopticMath.sol

125      function computeMedianObservedPrice(
126          IUniswapV3Pool univ3pool,
127          uint256 observationIndex,
128          uint256 observationCardinality,
129          uint256 cardinality,
130          uint256 period
131:     ) external view returns (int24) {

168      function computeInternalMedian(
169          uint256 observationIndex,
170          uint256 observationCardinality,
171          uint256 period,
172          uint256 medianData,
173          IUniswapV3Pool univ3pool
174:     ) external view returns (int24 medianTick, uint256 updatedMedianData) {

651      function getLiquidationBonus(
652          LeftRightUnsigned tokenData0,
653          LeftRightUnsigned tokenData1,
654          uint160 sqrtPriceX96Twap,
655          uint160 sqrtPriceX96Final,
656          LeftRightSigned netExchanged,
657          LeftRightSigned premia
658:     ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

768      function haircutPremia(
769          address liquidatee,
770          TokenId[] memory positionIdList,
771          LeftRightSigned[4][] memory premiasByLeg,
772          LeftRightSigned collateralRemaining,
773          CollateralTracker collateral0,
774          CollateralTracker collateral1,
775          uint160 sqrtPriceX96Final,
776          mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777:     ) external returns (int256, int256) {

917      function getRefundAmounts(
918          address refunder,
919          LeftRightSigned refundValues,
920          int24 atTick,
921          CollateralTracker collateral0,
922          CollateralTracker collateral1
923:     ) external view returns (LeftRightSigned) {

```
*GitHub*: [125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L125-L131), [168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L168-L174), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651-L658), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768-L777), [917](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L917-L923)

```solidity
File: contracts/types/TokenId.sol

336      function addLeg(
337          TokenId self,
338          uint256 legIndex,
339          uint256 _optionRatio,
340          uint256 _asset,
341          uint256 _isLong,
342          uint256 _tokenType,
343          uint256 _riskPartner,
344          int24 _strike,
345          int24 _width
346:     ) internal pure returns (TokenId tokenId) {

```
*GitHub*: [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L336-L346)

</details>





### [N&#x2011;17] Consider using descriptive `constant`s when passing zero as a function argument
Passing zero as a function argument can sometimes result in a security issue (e.g. passing zero as the slippage parameter). Consider using a `constant` variable with a descriptive name, so it's clear that the argument is intentionally being used, and for the right reasons.

*There are 77 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

713:                             .wrap(0)

```
*GitHub*: [713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L713-L713)

```solidity
File: contracts/PanopticPool.sol

634:             revert Errors.InvalidTokenIdParameter(0);

655:             .wrap(0)

763:                     .wrap(0)

861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);

893:         _validatePositionList(user, positionIdList, 0);

1023:        _validatePositionList(liquidatee, positionIdList, 0);

1153:        _validatePositionList(msg.sender, positionIdListLiquidator, 0);

1166:            .wrap(0)

1191:        _validatePositionList(msg.sender, positionIdListExercisor, 0);

1227:        _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

1227:        _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

1546:                        .wrap(0)

1567:                        premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

1592:        _validatePositionList(owner, positionIdList, 0);

1615:                .wrap(0)

1634:                .wrap(0)

1639:            s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1639:            s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1639:            s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1640:            s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

1640:            s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

1640:            s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

1714:                    0

1726:                        .wrap(0)

1775:                    .wrap(0)

1930:                                .wrap(0)

1943:                                                0

1960:                                                0

1966:                                .wrap(0)

```
*GitHub*: [634](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L634-L634), [655](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L655-L655), [763](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L763-L763), [861](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L861-L861), [870](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L870-L870), [893](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L893-L893), [1023](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1023-L1023), [1153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1153-L1153), [1166](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1166-L1166), [1191](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1191-L1191), [1227](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1227-L1227), [1227](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1227-L1227), [1546](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1546-L1546), [1567](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1567-L1567), [1592](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1592-L1592), [1615](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1615-L1615), [1634](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1634-L1634), [1639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1639-L1639), [1639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1639-L1639), [1639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1639-L1639), [1640](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1640-L1640), [1640](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1640-L1640), [1640](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1640-L1640), [1714](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1714-L1714), [1726](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1726-L1726), [1775](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1775-L1775), [1930](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1930-L1930), [1943](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1943-L1943), [1960](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1960-L1960), [1966](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1966-L1966)

```solidity
File: contracts/SemiFungiblePositionManager.sol

645:             s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

648:             s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

848:             totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(

1039:                .wrap(0)

1167:                .wrap(0)

1175:                .wrap(0)

1214:        movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

1241:            movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

1306:            collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(

1377:                        .wrap(0)

1401:                        .wrap(0)

```
*GitHub*: [645](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L645-L645), [648](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L648-L648), [833](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L833-L833), [848](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L848-L848), [1039](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1039-L1039), [1167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1167-L1167), [1175](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1175-L1175), [1214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1214-L1214), [1241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1241-L1241), [1306](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1306-L1306), [1377](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1377-L1377), [1401](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1401-L1401)

```solidity
File: contracts/libraries/FeesCalc.sol

116:                 .wrap(0)

```
*GitHub*: [116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L116-L116)

```solidity
File: contracts/libraries/Math.sol

778:             quickSort(data, int256(0), int256(data.length - 1));

```
*GitHub*: [778](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L778-L778)

```solidity
File: contracts/libraries/PanopticMath.sol

598:         return LeftRightUnsigned.wrap(0).toRightSlot(amount0).toLeftSlot(amount1);

674:                     0,

694:                 Math.max(premia.rightSlot(), 0);

696:                 Math.max(premia.leftSlot(), 0);

749:                 LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(

791:             int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);

792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

880:                                 tokenId.strike(0),

881:                                 tokenId.width(0),

882:                                 tokenId.tokenType(0)

889:                             0,

893:                             0,

898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(

934:                         .wrap(0)

952:                         .wrap(0)

```
*GitHub*: [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L598-L598), [674](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L674-L674), [694](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L694-L694), [696](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L696-L696), [749](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L749-L749), [791](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L791-L791), [792](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L792-L792), [856](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L856-L856), [856](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L856-L856), [856](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L856-L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L857-L857), [857](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L857-L857), [857](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L857-L857), [880](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L880-L880), [881](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L881-L881), [882](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L882-L882), [889](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L889-L889), [893](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L893-L893), [898](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L898-L898), [934](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L934-L934), [952](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L952-L952)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

220:         emit TransferSingle(msg.sender, address(0), to, id, amount);

224:                 ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=

239:         emit TransferSingle(msg.sender, from, address(0), id, amount);

```
*GitHub*: [220](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L220-L220), [224](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L224-L224), [239](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L239-L239)

```solidity
File: contracts/tokens/ERC20Minimal.sol

130:         emit Transfer(address(0), to, amount);

145:         emit Transfer(from, address(0), amount);

```
*GitHub*: [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L130-L130), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L145-L145)

```solidity
File: contracts/types/LeftRight.sol

265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

266:                     int128(Math.max(left128, 0))

294:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(

297:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(

```
*GitHub*: [265](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L265-L265), [266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L266-L266), [294](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L294-L294), [297](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L297-L297)

```solidity
File: contracts/types/TokenId.sol

406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

```
*GitHub*: [406](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L406-L406), [501](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L501-L501)

</details>





### [N&#x2011;18] Consider using named function arguments
When calling functions in external contracts with multiple arguments, consider using [named](https://docs.soliditylang.org/en/latest/control-structures.html#function-calls-with-named-parameters) function parameters, rather than positional ones.

*There are 47 instances of this issue:*

```solidity
File: contracts/PanopticFactory.sol

226:         IUniswapV3Pool v3Pool = IUniswapV3Pool(UNIV3_FACTORY.getPool(token0, token1, fee));

233:         SFPM.initializeAMMPool(token0, token1, fee);

248:         collateralTracker0.startToken(true, token0, token1, fee, newPoolContract);

249:         collateralTracker1.startToken(false, token0, token1, fee, newPoolContract);

251:         newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);

266:         DONOR_NFT.issueNFT(msg.sender, newPoolContract, token0, token1, fee);

404              IUniswapV3Pool(v3Pool).mint(
405                  address(this),
406                  tickLower,
407                  tickUpper,
408                  fullRangeLiquidity,
409                  mintCallback
410:             );

```
*GitHub*: [226](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L226-L226), [233](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L233-L233), [248](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L248-L248), [249](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L249-L249), [251](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L251-L251), [266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L266-L266), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L404-L410)

```solidity
File: contracts/PanopticPool.sol

685          (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
686:             .mintTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);

715          int256 utilization0 = s_collateralToken0.takeCommissionAddData(
716              msg.sender,
717              longAmounts.rightSlot(),
718              shortAmounts.rightSlot(),
719              totalSwapped.rightSlot()
720:         );

721          int256 utilization1 = s_collateralToken1.takeCommissionAddData(
722              msg.sender,
723              longAmounts.leftSlot(),
724              shortAmounts.leftSlot(),
725              totalSwapped.leftSlot()
726:         );

751                  (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
752                      address(s_univ3pool),
753                      address(this),
754                      tokenId.tokenType(leg),
755                      tickLower,
756                      tickUpper,
757                      type(int24).max,
758                      isLong
759:                 );

970          (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);

985              int128 paid0 = s_collateralToken0.exercise(
986                  owner,
987                  longAmounts.rightSlot(),
988                  shortAmounts.rightSlot(),
989                  totalSwapped.rightSlot(),
990                  realizedPremia.rightSlot()
991:             );

996              int128 paid1 = s_collateralToken1.exercise(
997                  owner,
998                  longAmounts.leftSlot(),
999                  shortAmounts.leftSlot(),
1000                 totalSwapped.leftSlot(),
1001                 realizedPremia.leftSlot()
1002:            );

1046             tokenData0 = s_collateralToken0.getAccountMarginDetails(
1047                 liquidatee,
1048                 twapTick,
1049                 positionBalanceArray,
1050                 premia.rightSlot()
1051:            );

1053             tokenData1 = s_collateralToken1.getAccountMarginDetails(
1054                 liquidatee,
1055                 twapTick,
1056                 positionBalanceArray,
1057                 premia.leftSlot()
1058:            );

1072:        s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());

1073:        s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());

1141         s_collateralToken0.revoke(
1142             msg.sender,
1143             liquidatee,
1144             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)
1145:        );

1146         s_collateralToken1.revoke(
1147             msg.sender,
1148             liquidatee,
1149             uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)
1150:        );

1222:        s_collateralToken0.delegate(account, uint128(delegatedAmounts.rightSlot()));

1223:        s_collateralToken1.delegate(account, uint128(delegatedAmounts.leftSlot()));

1231         LeftRightSigned exerciseFees = s_collateralToken0.exerciseCost(
1232             currentTick,
1233             twapTick,
1234             touchedId[0],
1235             positionBalance,
1236             longAmounts
1237:        );

1252             s_collateralToken0.refund(
1253                 account,
1254                 msg.sender,
1255                 refundAmounts.rightSlot() - delegatedAmounts.rightSlot()
1256:            );

1257             s_collateralToken1.refund(
1258                 account,
1259                 msg.sender,
1260                 refundAmounts.leftSlot() - delegatedAmounts.leftSlot()
1261:            );

1265:        s_collateralToken0.refund(account, uint128(delegatedAmounts.rightSlot()));

1266:        s_collateralToken1.refund(account, uint128(delegatedAmounts.leftSlot()));

1308         LeftRightUnsigned tokenData0 = s_collateralToken0.getAccountMarginDetails(
1309             account,
1310             atTick,
1311             positionBalanceArray,
1312             portfolioPremium.rightSlot()
1313:        );

1314         LeftRightUnsigned tokenData1 = s_collateralToken1.getAccountMarginDetails(
1315             account,
1316             atTick,
1317             positionBalanceArray,
1318             portfolioPremium.leftSlot()
1319:        );

1472         LeftRightUnsigned accountLiquidities = SFPM.getAccountLiquidity(
1473             address(s_univ3pool),
1474             address(this),
1475             tokenId.tokenType(leg),
1476             tickLower,
1477             tickUpper
1478:        );

1528                 (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM
1529                     .getAccountPremium(
1530                         address(s_univ3pool),
1531                         address(this),
1532                         tokenType,
1533                         liquidityChunk.tickLower(),
1534                         liquidityChunk.tickUpper(),
1535                         atTick,
1536                         isLong
1537:                    );

1605             (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
1606                 address(s_univ3pool),
1607                 address(this),
1608                 tokenType,
1609                 tickLower,
1610                 tickUpper,
1611                 currentTick,
1612                 1
1613:            );

1639:            s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1640:            s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

1707                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1708                     address(s_univ3pool),
1709                     address(this),
1710                     tokenId.tokenType(leg),
1711                     liquidityChunk.tickLower(),
1712                     liquidityChunk.tickUpper(),
1713                     type(int24).max,
1714                     0
1715:                );

1811             LeftRightUnsigned accountLiquidities = SFPM.getAccountLiquidity(
1812                 address(s_univ3pool),
1813                 address(this),
1814                 tokenType,
1815                 tickLower,
1816                 tickUpper
1817:            );

```
*GitHub*: [685](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L685-L686), [715](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L715-L720), [721](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L721-L726), [751](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L751-L759), [970](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L970-L971), [985](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L985-L991), [996](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L996-L1002), [1046](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1046-L1051), [1053](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1053-L1058), [1072](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1072-L1072), [1073](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1073-L1073), [1141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1141-L1145), [1146](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1146-L1150), [1222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1222-L1222), [1223](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1223-L1223), [1231](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1231-L1237), [1252](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1252-L1256), [1257](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1257-L1261), [1265](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1265-L1265), [1266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1266-L1266), [1308](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1308-L1313), [1314](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1314-L1319), [1472](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1472-L1478), [1528](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1528-L1537), [1605](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1605-L1613), [1639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1639-L1639), [1640](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1640-L1640), [1707](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1707-L1715), [1811](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1811-L1817)

```solidity
File: contracts/SemiFungiblePositionManager.sol

352:         address univ3pool = FACTORY.getPool(token0, token1, fee);

837              (int256 swap0, int256 swap1) = _univ3pool.swap(
838                  msg.sender,
839                  zeroForOne,
840                  swapAmount,
841                  zeroForOne
842                      ? Constants.MIN_V3POOL_SQRT_RATIO + 1
843                      : Constants.MAX_V3POOL_SQRT_RATIO - 1,
844                  data
845:             );

1203         (uint256 amount0, uint256 amount1) = univ3pool.mint(
1204             address(this),
1205             liquidityChunk.tickLower(),
1206             liquidityChunk.tickUpper(),
1207             liquidityChunk.liquidity(),
1208             mintdata
1209:        );

1230         (uint256 amount0, uint256 amount1) = univ3pool.burn(
1231             liquidityChunk.tickLower(),
1232             liquidityChunk.tickUpper(),
1233             liquidityChunk.liquidity()
1234:        );

1284             (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(
1285                 msg.sender,
1286                 liquidityChunk.tickLower(),
1287                 liquidityChunk.tickUpper(),
1288                 uint128(amountToCollect.rightSlot()),
1289                 uint128(amountToCollect.leftSlot())
1290:            );

```
*GitHub*: [352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L352-L352), [837](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L837-L845), [1203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1203-L1209), [1230](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1230-L1234), [1284](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1284-L1290)

```solidity
File: contracts/libraries/CallbackLib.sol

36:          if (factory.getPool(features.token0, features.token1, features.fee) != sender)

```
*GitHub*: [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L36-L36)

```solidity
File: contracts/libraries/PanopticMath.sol

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

```
*GitHub*: [856](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L856-L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L857-L857)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

114:                 ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=

165:                 ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=

224:                 ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=

```
*GitHub*: [114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L114-L114), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L165-L165), [224](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L224-L224)



### [N&#x2011;19] Consider using named returns
Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is ideal for named returns.

*There are 89 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

289:     function name() external view returns (string memory) {

303:     function symbol() external view returns (string memory) {

310:     function decimals() external view returns (uint8) {

323      function transfer(
324          address recipient,
325          uint256 amount
326:     ) public override(ERC20Minimal) returns (bool) {

341      function transferFrom(
342          address from,
343          address to,
344          uint256 amount
345:     ) public override(ERC20Minimal) returns (bool) {

1043     function exercise(
1044         address optionOwner,
1045         int128 longAmount,
1046         int128 shortAmount,
1047         int128 swappedAmount,
1048         int128 realizedPremium
1049:    ) external onlyPanopticPool returns (int128) {

```
*GitHub*: [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L289-L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L303-L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L310-L310), [323](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323-L326), [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341-L345), [1043](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1043-L1049)

```solidity
File: contracts/PanopticFactory.sol

159:     function owner() external view returns (address) {

335      function _mintFullRange(
336          IUniswapV3Pool v3Pool,
337          address token0,
338          address token1,
339          uint24 fee
340:     ) internal returns (uint256, uint256) {

420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {

```
*GitHub*: [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L159-L159), [335](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L335-L340), [420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L420-L420)

```solidity
File: contracts/PanopticPool.sol

381      function calculateAccumulatedFeesBatch(
382          address user,
383          bool includePendingPremium,
384          TokenId[] calldata positionIdList
385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

677      function _mintInSFPMAndUpdateCollateral(
678          TokenId tokenId,
679          uint128 positionSize,
680          int24 tickLimitLow,
681          int24 tickLimitHigh
682:     ) internal returns (uint128) {

706      function _payCommissionAndWriteData(
707          TokenId tokenId,
708          uint128 positionSize,
709          LeftRightSigned totalSwapped
710:     ) internal returns (uint128) {

1290     function _checkSolvencyAtTick(
1291         address account,
1292         TokenId[] calldata positionIdList,
1293         int24 currentTick,
1294         int24 atTick,
1295         uint256 buffer
1296:    ) internal view returns (bool) {

1425:    function univ3pool() external view returns (IUniswapV3Pool) {

1437:    function collateralToken1() external view returns (CollateralTracker) {

1757     function _getAvailablePremium(
1758         uint256 totalLiquidity,
1759         LeftRightUnsigned settledTokens,
1760         LeftRightUnsigned grossPremiumLast,
1761         LeftRightUnsigned premiumOwed,
1762         uint256[2] memory premiumAccumulators
1763:    ) internal pure returns (LeftRightUnsigned) {

```
*GitHub*: [381](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L381-L385), [677](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L677-L682), [706](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L706-L710), [1290](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1290-L1296), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1425-L1425), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1437-L1437), [1757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1757-L1763)

```solidity
File: contracts/SemiFungiblePositionManager.sol

1449     function getAccountPremium(
1450         address univ3pool,
1451         address owner,
1452         uint256 tokenType,
1453         int24 tickLower,
1454         int24 tickUpper,
1455         int24 atTick,
1456         uint256 isLong
1457:    ) external view returns (uint128, uint128) {

```
*GitHub*: [1449](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1449-L1457)

```solidity
File: contracts/libraries/FeesCalc.sol

97       function calculateAMMSwapFees(
98           IUniswapV3Pool univ3pool,
99           int24 currentTick,
100          int24 tickLower,
101          int24 tickUpper,
102          uint128 liquidity
103      ) public view returns (LeftRightSigned) {
104          // extract the amount of AMM fees collected within the liquidity chunk`
105:         // note: the fee variables are *per unit of liquidity*; so more "rate" variables

```
*GitHub*: [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L97-L105)

```solidity
File: contracts/libraries/InteractionHelper.sol

48       function computeName(
49           address token0,
50           address token1,
51           bool isToken0,
52           uint24 fee,
53           string memory prefix
54:      ) external view returns (string memory) {

```
*GitHub*: [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L48-L54)

```solidity
File: contracts/libraries/Math.sol

25:      function min24(int24 a, int24 b) internal pure returns (int24) {

33:      function max24(int24 a, int24 b) internal pure returns (int24) {

41:      function min(uint256 a, uint256 b) internal pure returns (uint256) {

49:      function min(int256 a, int256 b) internal pure returns (int256) {

57:      function max(uint256 a, uint256 b) internal pure returns (uint256) {

65:      function max(int256 a, int256 b) internal pure returns (int256) {

73:      function abs(int256 x) internal pure returns (int256) {

81:      function absUint(int256 x) internal pure returns (uint256) {

128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {

191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

241      function getLiquidityForAmount0(
242          int24 tickLower,
243          int24 tickUpper,
244          uint256 amount0
245:     ) internal pure returns (LiquidityChunk) {

271      function getLiquidityForAmount1(
272          int24 tickLower,
273          int24 tickUpper,
274          uint256 amount1
275:     ) internal pure returns (LiquidityChunk) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

776:     function sort(int256[] memory data) internal pure returns (int256[] memory) {

```
*GitHub*: [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L25-L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L33-L33), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L41-L41), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L49-L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L57-L57), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L65-L65), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L73-L73), [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L81-L81), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L128-L128), [191](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L191-L191), [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L207-L207), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L241-L245), [271](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L271-L275), [325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L325-L325), [776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L776-L776)

```solidity
File: contracts/libraries/PanopticMath.sol

47:      function getPoolId(address univ3pool) internal view returns (uint64) {

59:      function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

75:      function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

92       function updatePositionsHash(
93           uint256 existingHash,
94           TokenId tokenId,
95           bool addFlag
96:      ) internal pure returns (uint256) {

125      function computeMedianObservedPrice(
126          IUniswapV3Pool univ3pool,
127          uint256 observationIndex,
128          uint256 observationCardinality,
129          uint256 cardinality,
130          uint256 period
131:     ) external view returns (int24) {

241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

371      function getRangesFromStrike(
372          int24 width,
373          int24 tickSpacing
374:     ) internal pure returns (int24, int24) {

445      function convertCollateralData(
446          LeftRightUnsigned tokenData0,
447          LeftRightUnsigned tokenData1,
448          uint256 tokenType,
449          int24 tick
450:     ) internal pure returns (uint256, uint256) {

468      function convertNotional(
469          uint128 contractSize,
470          int24 tickLower,
471          int24 tickUpper,
472          uint256 asset
473:     ) internal pure returns (uint128) {

574      function getAmountsMoved(
575          TokenId tokenId,
576          uint128 positionSize,
577          uint256 legIndex
578:     ) internal pure returns (LeftRightUnsigned) {

651      function getLiquidationBonus(
652          LeftRightUnsigned tokenData0,
653          LeftRightUnsigned tokenData1,
654          uint160 sqrtPriceX96Twap,
655          uint160 sqrtPriceX96Final,
656          LeftRightSigned netExchanged,
657          LeftRightSigned premia
658:     ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

768      function haircutPremia(
769          address liquidatee,
770          TokenId[] memory positionIdList,
771          LeftRightSigned[4][] memory premiasByLeg,
772          LeftRightSigned collateralRemaining,
773          CollateralTracker collateral0,
774          CollateralTracker collateral1,
775          uint160 sqrtPriceX96Final,
776          mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777:     ) external returns (int256, int256) {

```
*GitHub*: [47](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L47-L47), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L59-L59), [75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L75-L75), [92](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L92-L96), [125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L125-L131), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L241-L241), [371](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L371-L374), [445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L445-L450), [468](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L468-L473), [574](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L574-L578), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651-L658), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768-L777)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

```
*GitHub*: [200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L200-L200)

```solidity
File: contracts/tokens/ERC20Minimal.sol

49:      function approve(address spender, uint256 amount) public returns (bool) {

61:      function transfer(address to, uint256 amount) public virtual returns (bool) {

81:      function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

```
*GitHub*: [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L49-L49), [61](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L61-L61), [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L81-L81)

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

16:      function balanceOf(address account) external view returns (uint256);

```
*GitHub*: [16](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L16-L16)

```solidity
File: contracts/types/LeftRight.sol

39:      function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46:      function rightSlot(LeftRightSigned self) internal pure returns (int128) {

59       function toRightSlot(
60           LeftRightUnsigned self,
61           uint128 right
62:      ) internal pure returns (LeftRightUnsigned) {

78       function toRightSlot(
79           LeftRightSigned self,
80           int128 right
81:      ) internal pure returns (LeftRightSigned) {

101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

121      function toLeftSlot(
122          LeftRightUnsigned self,
123          uint128 left
124:     ) internal pure returns (LeftRightUnsigned) {

134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

279      function addCapped(
280          LeftRightUnsigned x,
281          LeftRightUnsigned dx,
282          LeftRightUnsigned y,
283          LeftRightUnsigned dy
284:     ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {

```
*GitHub*: [39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L39-L39), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L46-L46), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L59-L62), [78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L78-L81), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L101-L101), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L108-L108), [121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L121-L124), [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L134-L134), [279](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L279-L284)

```solidity
File: contracts/types/LiquidityChunk.sol

70       function createChunk(
71           int24 _tickLower,
72           int24 _tickUpper,
73           uint128 amount
74:      ) internal pure returns (LiquidityChunk) {

89       function addLiquidity(
90           LiquidityChunk self,
91           uint128 amount
92:      ) internal pure returns (LiquidityChunk) {

102      function addTickLower(
103          LiquidityChunk self,
104          int24 _tickLower
105:     ) internal pure returns (LiquidityChunk) {

118      function addTickUpper(
119          LiquidityChunk self,
120          int24 _tickUpper
121:     ) internal pure returns (LiquidityChunk) {

135      function updateTickLower(
136          LiquidityChunk self,
137          int24 _tickLower
138:     ) internal pure returns (LiquidityChunk) {

151      function updateTickUpper(
152          LiquidityChunk self,
153          int24 _tickUpper
154:     ) internal pure returns (LiquidityChunk) {

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```
*GitHub*: [70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L70-L74), [89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L89-L92), [102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L102-L105), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L118-L121), [135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L135-L138), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L151-L154), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L171-L171), [180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L180-L180), [189](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L189-L189)

```solidity
File: contracts/types/TokenId.sol

87:      function poolId(TokenId self) internal pure returns (uint64) {

96:      function tickSpacing(TokenId self) internal pure returns (int24) {

108:     function asset(TokenId self, uint256 legIndex) internal pure returns (uint256) {

118:     function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {

128:     function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {

138:     function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {

148:     function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {

158:     function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

169:     function width(TokenId self, uint256 legIndex) internal pure returns (int24) {

183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

205      function addAsset(
206          TokenId self,
207          uint256 _asset,
208          uint256 legIndex
209:     ) internal pure returns (TokenId) {

221      function addOptionRatio(
222          TokenId self,
223          uint256 _optionRatio,
224          uint256 legIndex
225:     ) internal pure returns (TokenId) {

240      function addIsLong(
241          TokenId self,
242          uint256 _isLong,
243          uint256 legIndex
244:     ) internal pure returns (TokenId) {

255      function addTokenType(
256          TokenId self,
257          uint256 _tokenType,
258          uint256 legIndex
259:     ) internal pure returns (TokenId) {

273      function addRiskPartner(
274          TokenId self,
275          uint256 _riskPartner,
276          uint256 legIndex
277:     ) internal pure returns (TokenId) {

291      function addStrike(
292          TokenId self,
293          int24 _strike,
294          uint256 legIndex
295:     ) internal pure returns (TokenId) {

310      function addWidth(
311          TokenId self,
312          int24 _width,
313          uint256 legIndex
314:     ) internal pure returns (TokenId) {

366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

404:     function countLongs(TokenId self) internal pure returns (uint256) {

```
*GitHub*: [87](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L87-L87), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L96-L96), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L108-L108), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L118-L118), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L128-L128), [138](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L138-L138), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L148-L148), [158](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L158-L158), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L169-L169), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L183-L183), [193](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L193-L193), [205](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L205-L209), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L221-L225), [240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L240-L244), [255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L255-L259), [273](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L273-L277), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L291-L295), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L310-L314), [366](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L366-L366), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L404-L404)

</details>





### [N&#x2011;20] Consider using the `using`-`for` syntax
The `using`-`for` [syntax](https://docs.soliditylang.org/en/latest/contracts.html#using-for) is the more common way of calling library functions.

*There are 193 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

292              InteractionHelper.computeName(
293                  s_univ3token0,
294                  s_univ3token1,
295                  s_underlyingIsToken0,
296                  s_poolFee,
297                  NAME_PREFIX
298:             );

305:         return InteractionHelper.computeSymbol(s_underlyingToken, TICKER_PREFIX);

312:         return InteractionHelper.computeDecimals(s_underlyingToken);

380:         return Math.mulDiv(assets, totalSupply, totalAssets());

387:         return Math.mulDiv(shares, totalAssets(), totalSupply);

402              shares = Math.mulDiv(
403                  assets * (DECIMALS - COMMISSION_FEE),
404                  totalSupply,
405                  totalAssets() * DECIMALS
406:             );

424          SafeTransferLib.safeTransferFrom(
425              s_underlyingToken,
426              msg.sender,
427              address(s_panopticPool),
428              assets
429:         );

462              assets = Math.mulDivRoundingUp(
463                  shares * DECIMALS,
464                  totalAssets(),
465                  totalSupply * (DECIMALS - COMMISSION_FEE)
466:             );

484          SafeTransferLib.safeTransferFrom(
485              s_underlyingToken,
486              msg.sender,
487              address(s_panopticPool),
488              assets
489:         );

512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

521:         return Math.mulDivRoundingUp(assets, supply, totalAssets());

556          SafeTransferLib.safeTransferFrom(
557              s_underlyingToken,
558              address(s_panopticPool),
559              receiver,
560              assets
561:         );

575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

616          SafeTransferLib.safeTransferFrom(
617              s_underlyingToken,
618              address(s_panopticPool),
619              receiver,
620              assets
621:         );

669                              Math.unsafeDivRoundingUp(
670                                  uint24(positionId.width(leg) * positionId.tickSpacing()),
671                                  2
672:                             )

677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

675                      maxNumRangesFromStrike = Math.max(
676                          maxNumRangesFromStrike,
677                          uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
678:                     );

687                      LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
688                          positionId,
689                          leg,
690                          positionBalance
691:                     );

693                      (currentValue0, currentValue1) = Math.getAmountsForLiquidity(
694                          currentTick,
695                          liquidityChunk
696:                     );

698                      (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(
699                          oracleTick,
700                          liquidityChunk
701:                     );

959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

956                  Math.mulDiv(
957                      assets,
958                      totalSupply - delegateeBalance,
959                      uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
960:                 ) - delegateeBalance

1012                 uint256 sharesToBurn = Math.mulDivRoundingUp(
1013                     uint256(tokenToPay),
1014                     totalSupply,
1015                     totalAssets()
1016:                );

1069                 uint256 sharesToBurn = Math.mulDivRoundingUp(
1070                     uint256(tokenToPay),
1071                     totalSupply,
1072                     totalAssets()
1073:                );

1110:                    s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),

1109                 uint256 swapCommission = Math.unsafeDivRoundingUp(
1110                     s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),
1111                     DECIMALS
1112:                );

1120                 Math.unsafeDivRoundingUp(
1121                     uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
1122                     DECIMALS
1123:                )

1322:        LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

1364:                            Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

1363                         ? Math.getSqrtRatioAtTick(
1364                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)
1365:                        ) // puts ->  price/strike

1367:                            Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

1366                         : Math.getSqrtRatioAtTick(
1367                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)
1368:                        ); // calls -> strike/price

1401:                        required += Math.mulDiv96RoundingUp(amountMoved, c2);

1408                         uint160 scaleFactor = Math.getSqrtRatioAtTick(
1409                             (tickUpper - strike) + (strike - tickLower)
1410:                        );

1411                         uint256 c3 = Math.mulDivRoundingUp(
1412                             amountMoved,
1413                             scaleFactor - ratio,
1414                             scaleFactor + Constants.FP96
1415:                        );

1486:                required = Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS);

1496:                required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);

1518:        LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

1521         LeftRightUnsigned amountsMovedPartner = PanopticMath.getAmountsMoved(
1522             tokenId,
1523             positionSize,
1524             partnerIndex
1525:        );

1571:                    ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)

1572:                    : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

1579         spreadRequirement = Math.max(
1580             spreadRequirement,
1581             _getRequiredCollateralAtUtilization(
1582                 tokenType == 0 ? movedRight : movedLeft,
1583                 1,
1584                 tokenType == 0
1585                     ? int64(uint64(poolUtilization))
1586                     : int64(uint64(poolUtilization >> 64))
1587             )
1588:        );

```
*GitHub*: [292](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L292-L298), [305](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L305-L305), [312](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L312-L312), [380](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L380-L380), [387](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L387-L387), [402](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L402-L406), [424](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L424-L429), [462](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L462-L466), [484](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L484-L489), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L512-L512), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L521-L521), [556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L556-L561), [575](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L575-L575), [616](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L616-L621), [669](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L669-L672), [677](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L677-L677), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L675-L678), [687](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L687-L691), [693](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L693-L696), [698](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L698-L701), [959](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L959-L959), [956](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L956-L960), [1012](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1012-L1016), [1069](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1069-L1073), [1110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1110-L1110), [1109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1109-L1112), [1120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1120-L1123), [1322](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1322-L1322), [1364](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1364-L1364), [1363](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1363-L1365), [1367](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1367-L1367), [1366](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1366-L1368), [1401](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1401-L1401), [1408](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1408-L1410), [1411](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1411-L1415), [1486](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1486-L1486), [1496](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1496-L1496), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1518-L1518), [1521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1521-L1525), [1571](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1571-L1571), [1572](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1572-L1572), [1579](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1579-L1588)

```solidity
File: contracts/PanopticFactory.sol

179:         CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);

182              SafeTransferLib.safeTransferFrom(
183                  decoded.poolFeatures.token0,
184                  decoded.payer,
185                  msg.sender,
186                  amount0Owed
187:             );

189              SafeTransferLib.safeTransferFrom(
190                  decoded.poolFeatures.token1,
191                  decoded.payer,
192                  msg.sender,
193                  amount1Owed
194:             );

241:             Clones.clone(COLLATERAL_REFERENCE)

244:             Clones.clone(COLLATERAL_REFERENCE)

304              uint256 rarity = PanopticMath.numberOfLeadingHexZeros(
305                  POOL_REFERENCE.predictDeterministicAddress(salt)
306:             );

353:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)

357                      Math.mulDivRoundingUp(
358                          FULL_RANGE_LIQUIDITY_AMOUNT_WETH,
359                          Constants.FP96,
360                          currentSqrtPriceX96
361:                     )

366:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)

369                      Math.mulDivRoundingUp(
370                          FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,
371                          Constants.FP96,
372                          currentSqrtPriceX96
373:                     )

```
*GitHub*: [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L179-L179), [182](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L182-L187), [189](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L189-L194), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L241-L241), [244](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L244-L244), [304](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L304-L306), [353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L353-L353), [357](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L357-L361), [366](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L366-L366), [369](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L369-L373)

```solidity
File: contracts/PanopticPool.sol

326:         InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);

415          (value0, value1) = FeesCalc.getPortfolioValue(
416              atTick,
417              s_positionBalance[user],
418              positionIdList
419:         );

525          (, uint256 medianData) = PanopticMath.computeInternalMedian(
526              observationIndex,
527              observationCardinality,
528              MEDIAN_PERIOD,
529              s_miniMedian,
530              s_univ3pool
531:         );

712          (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath
713:             .computeExercisedAmounts(tokenId, positionSize);

775:                     uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))

905          int24 fastOracleTick = PanopticMath.computeMedianObservedPrice(
906              _univ3pool,
907              observationIndex,
908              observationCardinality,
909              FAST_ORACLE_CARDINALITY,
910              FAST_ORACLE_PERIOD
911:         );

915              slowOracleTick = PanopticMath.computeMedianObservedPrice(
916                  _univ3pool,
917                  observationIndex,
918                  observationCardinality,
919                  SLOW_ORACLE_CARDINALITY,
920                  SLOW_ORACLE_PERIOD
921:             );

923              (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(
924                  observationIndex,
925                  observationCardinality,
926                  MEDIAN_PERIOD,
927                  s_miniMedian,
928                  _univ3pool
929:             );

943:         if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

981          (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath
982:             .computeExercisedAmounts(tokenId, positionSize);

1035:            if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

1063:                Math.getSqrtRatioAtTick(twapTick)

1102:                    Math.getSqrtRatioAtTick(twapTick),

1103:                    Math.getSqrtRatioAtTick(finalTick),

1098             (liquidationBonus0, liquidationBonus1, collateralRemaining) = PanopticMath
1099                 .getLiquidationBonus(
1100                     tokenData0,
1101                     tokenData1,
1102                     Math.getSqrtRatioAtTick(twapTick),
1103                     Math.getSqrtRatioAtTick(finalTick),
1104                     netExchanged,
1105                     premia
1106:                );

1129:                Math.getSqrtRatioAtTick(_finalTick),

1122             (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(
1123                 _liquidatee,
1124                 _positionIdList,
1125                 premiasByLeg,
1126                 collateralRemaining,
1127                 s_collateralToken0,
1128                 s_collateralToken1,
1129                 Math.getSqrtRatioAtTick(_finalTick),
1130                 s_settledTokens
1131:            );

1197         (LeftRightSigned longAmounts, LeftRightSigned delegatedAmounts) = PanopticMath
1198:            .computeExercisedAmounts(touchedId[0], positionBalance);

1242         refundAmounts = PanopticMath.getRefundAmounts(
1243             account,
1244             refundAmounts,
1245             twapTick,
1246             s_collateralToken0,
1247             s_collateralToken1
1248:        );

1324:            Math.getSqrtRatioAtTick(atTick)

1329:            return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

1348:                Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

1349:                Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);

1353:                Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

1354:                Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);

1383             fingerprintIncomingList = PanopticMath.updatePositionsHash(
1384                 fingerprintIncomingList,
1385                 positionIdList[i],
1386                 ADD
1387:            );

1410         uint256 newHash = PanopticMath.updatePositionsHash(
1411             s_positionsHash[account],
1412             tokenId,
1413             addFlag
1414:        );

1451:        twapTick = PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW);

1521                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1522                     tokenId,
1523                     leg,
1524                     positionSize
1525:                );

1627         uint256 liquidity = PanopticMath
1628:            .getLiquidityChunk(tokenId, legIndex, s_positionBalance[owner][tokenId].rightSlot())

1680                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1681                     tokenId,
1682                     leg,
1683                     positionSize
1684:                );

1778                             Math.min(
1779                                 (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /
1780                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),
1781                                 premiumOwed.rightSlot()
1782:                            )

1787                             Math.min(
1788                                 (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /
1789                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),
1790                                 premiumOwed.leftSlot()
1791:                            )

1877                     uint256 positionLiquidity = PanopticMath
1878:                        .getLiquidityChunk(tokenId, leg, positionSize)

1934                                             Math.max(
1935                                                 (int256(
1936                                                     grossPremiumLast.rightSlot() *
1937                                                         totalLiquidityBefore
1938                                                 ) -
1939                                                     int256(
1940                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941                                                             positionLiquidity
1942                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),
1943                                                 0
1944:                                            )

1951                                             Math.max(
1952                                                 (int256(
1953                                                     grossPremiumLast.leftSlot() *
1954                                                         totalLiquidityBefore
1955                                                 ) -
1956                                                     int256(
1957                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958                                                             positionLiquidity
1959                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960                                                 0
1961:                                            )

```
*GitHub*: [326](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L326-L326), [415](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L415-L419), [525](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L525-L531), [712](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L712-L713), [775](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L775-L775), [905](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L905-L911), [915](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L915-L921), [923](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L923-L929), [943](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L943-L943), [981](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L981-L982), [1035](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1035-L1035), [1063](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1063-L1063), [1102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1102-L1102), [1103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1103-L1103), [1098](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1098-L1106), [1129](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1129-L1129), [1122](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1122-L1131), [1197](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1197-L1198), [1242](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1242-L1248), [1324](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1324-L1324), [1329](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1329-L1329), [1348](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1348-L1348), [1349](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1349-L1349), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1353-L1353), [1354](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1354-L1354), [1383](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1383-L1387), [1410](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1410-L1414), [1451](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1451-L1451), [1521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1521-L1525), [1627](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1627-L1628), [1680](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1680-L1684), [1778](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1778-L1782), [1787](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1787-L1791), [1877](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1877-L1878), [1934](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1934-L1944), [1951](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1951-L1961)

```solidity
File: contracts/SemiFungiblePositionManager.sol

367:         uint64 poolId = PanopticMath.getPoolId(univ3pool);

373:             poolId = PanopticMath.incrementPoolPattern(poolId);

410:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

413              SafeTransferLib.safeTransferFrom(
414                  decoded.poolFeatures.token0,
415                  decoded.payer,
416                  msg.sender,
417                  amount0Owed
418:             );

420              SafeTransferLib.safeTransferFrom(
421                  decoded.poolFeatures.token1,
422                  decoded.payer,
423                  msg.sender,
424                  amount1Owed
425:             );

443:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

604              LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
605                  id,
606                  leg,
607                  uint128(amount)
608:             );

817:                 int256 net0 = itm0 - PanopticMath.convert1to0(itm1, sqrtPriceX96);

904                  LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
905                      _tokenId,
906                      _leg,
907                      _positionSize
908:                 );

922:                     amount0 += Math.getAmount0ForLiquidity(liquidityChunk);

924:                     amount1 += Math.getAmount1ForLiquidity(liquidityChunk);

1123         (s_accountPremiumOwed[positionKey], s_accountPremiumGross[positionKey]) = LeftRightLibrary
1124             .addCapped(
1125                 s_accountPremiumOwed[positionKey],
1126                 deltaPremiumOwed,
1127                 s_accountPremiumGross[positionKey],
1128                 deltaPremiumGross
1129:            );

1169:                    int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

1172:                    int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

1176:                .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

1177:                .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

1350                 premium0X64_base = Math.mulDiv(
1351                     collected0,
1352                     totalLiquidity * 2 ** 64,
1353                     netLiquidity ** 2
1354:                );

1355                 premium1X64_base = Math.mulDiv(
1356                     collected1,
1357                     totalLiquidity * 2 ** 64,
1358                     netLiquidity ** 2
1359:                );

1369                     premium0X64_owed = Math
1370:                        .mulDiv(premium0X64_base, numerator, totalLiquidity)

1372                     premium1X64_owed = Math
1373:                        .mulDiv(premium1X64_base, numerator, totalLiquidity)

1393                     premium0X64_gross = Math
1394:                        .mulDiv(premium0X64_base, numerator, totalLiquidity ** 2)

1396                     premium1X64_gross = Math
1397:                        .mulDiv(premium1X64_base, numerator, totalLiquidity ** 2)

1480                     LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(
1481                         _univ3pool,
1482                         atTick,
1483                         _tickLower,
1484                         _tickUpper,
1485                         netLiquidity
1486:                    );

1507                 (premiumOwed, premiumGross) = LeftRightLibrary.addCapped(
1508                     s_accountPremiumOwed[positionKey],
1509                     premiumOwed,
1510                     s_accountPremiumGross[positionKey],
1511                     premiumGross
1512:                );

```
*GitHub*: [367](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L367-L367), [373](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L373-L373), [410](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L410-L410), [413](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L413-L418), [420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L420-L425), [443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L443-L443), [456](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L456-L456), [604](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L604-L608), [817](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L817-L817), [904](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L904-L908), [922](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L922-L922), [924](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L924-L924), [1123](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1123-L1129), [1169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1169-L1169), [1172](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1172-L1172), [1176](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1176-L1176), [1177](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1177-L1177), [1350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1350-L1354), [1355](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1355-L1359), [1369](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1369-L1370), [1372](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1372-L1373), [1393](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1393-L1394), [1396](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1396-L1397), [1480](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1480-L1486), [1507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1507-L1512)

```solidity
File: contracts/libraries/FeesCalc.sol

56                   LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
57                       tokenId,
58                       leg,
59                       positionSize
60:                  );

62                   (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
63                       atTick,
64                       liquidityChunk
65:                  );

117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

```
*GitHub*: [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L56-L60), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L62-L65), [117](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L117-L117), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L118-L118)

```solidity
File: contracts/libraries/InteractionHelper.sol

81:                      Strings.toString(fee),

```
*GitHub*: [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L81-L81)

```solidity
File: contracts/libraries/Math.sol

251                  LiquidityChunkLibrary.createChunk(
252                      tickLower,
253                      tickUpper,
254                      toUint128(
255                          mulDiv(
256                              amount0,
257                              mulDiv96(highPriceX96, lowPriceX96),
258                              highPriceX96 - lowPriceX96
259                          )
260                      )
261:                 );

281                  LiquidityChunkLibrary.createChunk(
282                      tickLower,
283                      tickUpper,
284                      toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))
285:                 );

```
*GitHub*: [251](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L251-L261), [281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L281-L285)

```solidity
File: contracts/libraries/PanopticMath.sol

77:              return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

155:             return int24(Math.sort(ticks)[cardinality / 2]);

263:             int256[] memory sortedTicks = Math.sort(twapMeasurement);

326:             return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);

328:             return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);

349:             (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(width, tickSpacing);

377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

452:             convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));

476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);

497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)

529                  int256 absResult = Math
530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)

535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

534                  int256 absResult = Math
535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

552                  int256 absResult = Math
553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

559:                         Math.absUint(amount),

561:                         Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)

557                  int256 absResult = Math
558                      .mulDiv(
559                          Math.absUint(amount),
560                          2 ** 128,
561                          Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
562:                     )

588:                 .getAmount1ForLiquidity(Math.getLiquidityForAmount0(tickLower, tickUpper, amount0))

587              amount1 = Math
588:                 .getAmount1ForLiquidity(Math.getLiquidityForAmount0(tickLower, tickUpper, amount0))

594:                 .getAmount0ForLiquidity(Math.getLiquidityForAmount1(tickLower, tickUpper, amount1))

593              amount0 = Math
594:                 .getAmount0ForLiquidity(Math.getLiquidityForAmount1(tickLower, tickUpper, amount1))

621:                 shorts = shorts.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

624:                 longs = longs.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

629:                 shorts = shorts.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

632:                 longs = longs.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

664                  uint256 required0 = PanopticMath.convert0to1(
665                      tokenData0.leftSlot(),
666                      sqrtPriceX96Twap
667:                 );

671                  (uint256 balanceCross, uint256 thresholdCross) = PanopticMath.convertCollateralData(
672                      tokenData0,
673                      tokenData1,
674                      0,
675                      sqrtPriceX96Twap
676:                 );

678:                 uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));

685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

684                      PanopticMath.convert0to1(
685                          Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
686                          sqrtPriceX96Final
687:                     )

694:                 Math.max(premia.rightSlot(), 0);

696:                 Math.max(premia.leftSlot(), 0);

717:                         PanopticMath.convert0to1(paid0 - balance0, sqrtPriceX96Final)

715                      bonus1 += Math.min(
716                          balance1 - paid1,
717                          PanopticMath.convert0to1(paid0 - balance0, sqrtPriceX96Final)
718:                     );

720:                         PanopticMath.convert1to0(balance1 - paid1, sqrtPriceX96Final),

719                      bonus0 -= Math.min(
720                          PanopticMath.convert1to0(balance1 - paid1, sqrtPriceX96Final),
721                          paid0 - balance0
722:                     );

735:                         PanopticMath.convert1to0(paid1 - balance1, sqrtPriceX96Final)

733                      bonus0 += Math.min(
734                          balance0 - paid0,
735                          PanopticMath.convert1to0(paid1 - balance1, sqrtPriceX96Final)
736:                     );

738:                         PanopticMath.convert0to1(balance0 - paid0, sqrtPriceX96Final),

737                      bonus1 -= Math.min(
738                          PanopticMath.convert0to1(balance0 - paid0, sqrtPriceX96Final),
739                          paid1 - balance1
740:                     );

791:             int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);

792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

805                          PanopticMath.convert1to0(
806                              longPremium.leftSlot() - collateralDelta1,
807                              sqrtPriceX96Final
808:                         )

803                      -Math.min(
804                          collateralDelta0 - longPremium.rightSlot(),
805                          PanopticMath.convert1to0(
806                              longPremium.leftSlot() - collateralDelta1,
807                              sqrtPriceX96Final
808                          )
809:                     ),

812                          PanopticMath.convert0to1(
813                              collateralDelta0 - longPremium.rightSlot(),
814                              sqrtPriceX96Final
815:                         )

810                      Math.min(
811                          longPremium.leftSlot() - collateralDelta1,
812                          PanopticMath.convert0to1(
813                              collateralDelta0 - longPremium.rightSlot(),
814                              sqrtPriceX96Final
815                          )
816:                     )

829                          PanopticMath.convert1to0(
830                              collateralDelta1 - longPremium.leftSlot(),
831                              sqrtPriceX96Final
832:                         )

827                      Math.min(
828                          longPremium.rightSlot() - collateralDelta0,
829                          PanopticMath.convert1to0(
830                              collateralDelta1 - longPremium.leftSlot(),
831                              sqrtPriceX96Final
832                          )
833:                     ),

836                          PanopticMath.convert0to1(
837                              longPremium.rightSlot() - collateralDelta0,
838                              sqrtPriceX96Final
839:                         )

834                      -Math.min(
835                          collateralDelta1 - longPremium.leftSlot(),
836                          PanopticMath.convert0to1(
837                              longPremium.rightSlot() - collateralDelta0,
838                              sqrtPriceX96Final
839                          )
840:                     )

847:                 haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());

848:                 haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());

869                          uint256 settled0 = Math.unsafeDivRoundingUp(
870                              uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871                              uint128(longPremium.rightSlot())
872:                         );

873                          uint256 settled1 = Math.unsafeDivRoundingUp(
874                              uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875                              uint128(longPremium.leftSlot())
876:                         );

888                          settled0 = Math.max(
889                              0,
890                              uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891:                         );

892                          settled1 = Math.max(
893                              0,
894                              uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895:                         );

924:         uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);

939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)

957:                                     PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)

```
*GitHub*: [77](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L77-L77), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L155-L155), [263](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L263-L263), [326](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L326-L326), [328](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L328-L328), [349](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L349-L349), [377](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L377-L377), [452](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L452-L452), [476](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L476-L476), [477](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L477-L477), [495](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L495-L495), [497](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L497-L497), [497](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L497-L497), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L512-L512), [514](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L514-L514), [514](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L514-L514), [530](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L530-L530), [529](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L529-L530), [535](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L535-L535), [535](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L535-L535), [534](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L534-L535), [553](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L553-L553), [552](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L552-L553), [559](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L559-L559), [561](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L561-L561), [557](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L557-L562), [588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L588-L588), [587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L587-L588), [594](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L594-L594), [593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L593-L594), [621](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L621-L621), [624](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L624-L624), [629](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L629-L629), [632](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L632-L632), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L664-L667), [671](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L671-L676), [678](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L678-L678), [681](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L681-L681), [685](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L685-L685), [684](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L684-L687), [694](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L694-L694), [696](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L696-L696), [717](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L717-L717), [715](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L715-L718), [720](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L720-L720), [719](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L719-L722), [735](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L735-L735), [733](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L733-L736), [738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L738-L738), [737](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L737-L740), [791](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L791-L791), [792](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L792-L792), [805](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L805-L808), [803](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L803-L809), [812](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L812-L815), [810](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L810-L816), [829](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L829-L832), [827](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L827-L833), [836](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L836-L839), [834](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L834-L840), [847](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L847-L847), [848](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L848-L848), [869](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L869-L872), [873](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L873-L876), [888](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L888-L891), [892](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L892-L895), [924](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L924-L924), [939](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L939-L939), [957](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L957-L957)

```solidity
File: contracts/types/LeftRight.sol

265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

266:                     int128(Math.max(left128, 0))

```
*GitHub*: [265](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L265-L265), [266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L266-L266)

```solidity
File: contracts/types/TokenId.sol

420          (legLowerTick, legUpperTick) = PanopticMath.getTicks(
421              self.strike(legIndex),
422              self.width(legIndex),
423              self.tickSpacing()
424:         );

582                  (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(
583                      self.width(i),
584                      self.tickSpacing()
585:                 );

```
*GitHub*: [420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L420-L424), [582](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L582-L585)

</details>





### [N&#x2011;21] Constants in comparisons should appear on the left side
Doing so will prevent [typo bugs](https://www.moserware.com/2008/01/constants-on-left-are-better-but-this.html) where the first '!', '>', '<', or '=' at the beginning of the operator is missing.

*There are 178 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

664:                 if (positionId.isLong(leg) == 0) continue;

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

709:                     (tokenType == 1 && currentValue0 < oracleValue0)

776:         if (utilization < 0) {

784:         if (uint256(utilization) < TARGET_POOL_UTIL) {

790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {

835:         if (utilization < TARGET_POOL_UTIL) {

841:         if (utilization > SATURATED_POOL_UTIL) {

976:         if (assets > 0) {

1010:            if (tokenToPay > 0) {

1018:            } else if (tokenToPay < 0) {

1060:            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1060:            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1060:            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1067:            if (tokenToPay > 0) {

1075:            } else if (tokenToPay < 0) {

1107:            if (intrinsicValue != 0) {

1168:        if (positionBalanceArray.length > 0) {

1173:            if (premiumAllPositions < 0) {

1182:        if (premiumAllPositions > 0) {

1325:        uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();

1328:        int64 utilization = tokenType == 0

1339:            if (isLong == 0) {

1346:                    ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1

1347:                    ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1362:                    uint160 ratio = tokenType == 1 // tokenType

1374:                        ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1375:                        ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1451:            if (isLong == 1) {

1479:        if (isLong == 0) {

1488:        } else if (isLong == 1) {

1544:                if (tokenType == 0) {

1559:                if (tokenType == 1) {

1582:                tokenType == 0 ? movedRight : movedLeft,

1584:                tokenType == 0

1637:                uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638:                (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```
*GitHub*: [331](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L331-L331), [350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L350-L350), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L512-L512), [575](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L575-L575), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L664-L664), [708](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L708-L708), [709](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L709-L709), [776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L776-L776), [784](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L784-L784), [790](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L790-L790), [835](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L835-L835), [841](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L841-L841), [976](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L976-L976), [1010](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1010-L1010), [1018](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1018-L1018), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1060-L1060), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1060-L1060), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1060-L1060), [1067](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1067-L1067), [1075](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1075-L1075), [1107](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1107-L1107), [1168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1168-L1168), [1173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1173-L1173), [1182](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1182-L1182), [1325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1325-L1325), [1328](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1328-L1328), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1339-L1339), [1346](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1346-L1346), [1347](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1347-L1347), [1362](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1362-L1362), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1374-L1374), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1375-L1375), [1451](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1451-L1451), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1479-L1479), [1488](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1488-L1488), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1544-L1544), [1559](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1559-L1559), [1582](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1582-L1582), [1584](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1584-L1584), [1637](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1637-L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1638-L1638)

```solidity
File: contracts/PanopticFactory.sol

181:         if (amount0Owed > 0)

188:         if (amount1Owed > 0)

351:             if (token0 == WETH) {

355:             } else if (token1 == WETH) {

```
*GitHub*: [181](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L181-L181), [188](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L188-L188), [351](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L351-L351), [355](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L355-L355)

```solidity
File: contracts/PanopticPool.sol

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

533:         if (medianData != 0) s_miniMedian = medianData;

638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

664:         if (medianData != 0) s_miniMedian = medianData;

768:             if (isLong == 1) {

865:             if (tokenId.isLong(leg) == 0) {

943:         if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

1035:            if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

1188:        if (touchedId.length != 1) revert Errors.InputListFail();

1274:        if (positionIdListExercisor.length > 0)

1415:        if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

1483:        if (netLiquidity == 0) return;

1520:            if ((isLong == 1) || computeAllPremia) {

1566:                    if (isLong == 1) {

1596:        if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1596:        if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1679:            if (tokenId.isLong(leg) == 0) {

1780:                                    (accumulated0 == 0 ? type(uint256).max : accumulated0),

1789:                                    (accumulated1 == 0 ? type(uint256).max : accumulated1),

1862:            if (LeftRightSigned.unwrap(legPremia) != 0) {

1864:                if (tokenId.isLong(leg) == 1) {

1928:                        s_grossPremiumLast[chunkKey] = totalLiquidity != 0

```
*GitHub*: [460](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L460-L460), [533](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L533-L533), [638](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L638-L638), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L664-L664), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L768-L768), [865](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L865-L865), [943](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L943-L943), [1035](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1035-L1035), [1188](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1188-L1188), [1274](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1274-L1274), [1415](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1415-L1415), [1483](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1483-L1483), [1520](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1520-L1520), [1566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1566-L1566), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1596-L1596), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1596-L1596), [1679](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1679-L1679), [1780](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1780-L1780), [1789](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1789-L1789), [1862](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1862-L1862), [1864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1864-L1864), [1928](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1928-L1928)

```solidity
File: contracts/SemiFungiblePositionManager.sol

362:         if (s_AddrToPoolIdData[univ3pool] != 0) return;

412:         if (amount0Owed > 0)

419:         if (amount1Owed > 0)

446:         address token = amount0Delta > 0

453:         uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);

632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

787:             if ((itm0 != 0) && (itm1 != 0)) {

787:             if ((itm0 != 0) && (itm1 != 0)) {

819:                 zeroForOne = net0 < 0;

823:             } else if (itm0 != 0) {

824:                 zeroForOne = itm0 < 0;

827:                 zeroForOne = itm1 > 0;

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

999:             if (isLong == 0) {

1066:            moved = isLong == 0

1073:            if (tokenType == 1) {

1078:            if (tokenType == 0) {

1085:        if (currentLiquidity.rightSlot() > 0) {

1275:        if (isLong == 1) {

1279:        if (LeftRightSigned.unwrap(amountToCollect) != 0) {

1296:                collected0 = movedInLeg.rightSlot() < 0

1299:                collected1 = movedInLeg.leftSlot() < 0

1469:            if (netLiquidity != 0) {

1514:                acctPremia = isLong == 1 ? premiumOwed : premiumGross;

1518:            acctPremia = isLong == 1

```
*GitHub*: [362](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L362-L362), [412](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L412-L412), [419](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L419-L419), [446](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L446-L446), [453](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L453-L453), [632](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L632-L632), [633](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L633-L633), [688](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L688-L688), [717](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L717-L717), [787](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L787-L787), [787](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L787-L787), [819](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L819-L819), [823](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L823-L823), [824](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L824-L824), [827](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L827-L827), [833](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L833-L833), [999](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L999-L999), [1066](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1066-L1066), [1073](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1073-L1073), [1078](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1078-L1078), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1085-L1085), [1275](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1275-L1275), [1279](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1279-L1279), [1296](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1296-L1296), [1299](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1299-L1299), [1469](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1469-L1469), [1514](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1514-L1514), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1518-L1518)

```solidity
File: contracts/libraries/FeesCalc.sol

67:                  if (tokenId.isLong(leg) == 0) {

```
*GitHub*: [67](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L67-L67)

```solidity
File: contracts/libraries/Math.sol

74:          return x > 0 ? x : -x;

83:              return x > 0 ? uint256(x) : uint256(-x);

93:              if (x >= 0x100000000000000000000000000000000) {

97:              if (x >= 0x10000000000000000) {

101:             if (x >= 0x100000000) {

105:             if (x >= 0x10000) {

109:             if (x >= 0x100) {

113:             if (x >= 0x10) {

130:             uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));

133:             uint256 sqrtR = absTick & 0x1 != 0

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

176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

360:             if (prod1 == 0) {

361:                 require(denominator > 0);

447:             if (mulmod(a, b, denominator) > 0) {

474:             if (prod1 == 0) {

537:             if (prod1 == 0) {

587:             if (mulmod(a, b, 2 ** 96) > 0) {

614:             if (prod1 == 0) {

664:             if (mulmod(a, b, 2 ** 128) > 0) {

691:             if (prod1 == 0) {

```
*GitHub*: [74](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L74-L74), [83](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L83-L83), [93](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L93-L93), [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L97-L97), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L101-L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L105-L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L109-L109), [113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L113-L113), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L130-L130), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L133-L133), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L137-L137), [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L139-L139), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L141-L141), [143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L143-L143), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L145-L145), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L147-L147), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L149-L149), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L151-L151), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L153-L153), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L155-L155), [157](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L157-L157), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L159-L159), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L161-L161), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L163-L163), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L165-L165), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L167-L167), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L169-L169), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L171-L171), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L173-L173), [176](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L176-L176), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L179-L179), [312](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L312-L312), [360](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L360-L360), [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L361-L361), [447](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L447-L447), [474](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L474-L474), [537](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L537-L537), [587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L587-L587), [614](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L614-L614), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L664-L664), [691](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L691-L691)

```solidity
File: contracts/libraries/PanopticMath.sol

207:                 for (uint8 i; i < 8; ++i) {

211:                     if (rank == 7) {

248:             for (uint256 i = 0; i < 20; ++i) {

256:             for (uint256 i = 0; i < 19; ++i) {

325:         if (tokenId.asset(legIndex) == 0) {

357:                 tickLower % tickSpacing != 0 ||

358:                 tickUpper % tickSpacing != 0 ||

425:         if (tokenType == 0) {

475:             uint256 notional = asset == 0

479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

532:                 return amount < 0 ? -absResult : absResult;

537:                 return amount < 0 ? -absResult : absResult;

555:                 return amount < 0 ? -absResult : absResult;

564:                 return amount < 0 ? -absResult : absResult;

584:         if (tokenId.asset(legIndex) == 0) {

615:         bool isShort = tokenId.isLong(legIndex) == 0;

618:         if (tokenId.tokenType(legIndex) == 0) {

785:                     if (tokenId.isLong(leg) == 1) {

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

864:                     if (tokenId.isLong(leg) == 1) {

931:             if (balanceShortage > 0) {

949:             if (balanceShortage > 0) {

```
*GitHub*: [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L207-L207), [211](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L211-L211), [248](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L248-L248), [256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L256-L256), [325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L325-L325), [357](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L357-L357), [358](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L358-L358), [425](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L425-L425), [475](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L475-L475), [479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L479-L479), [532](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L532-L532), [537](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L537-L537), [555](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L555-L555), [564](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L564-L564), [584](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L584-L584), [615](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L615-L615), [618](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L618-L618), [785](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L785-L785), [856](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L856-L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L857-L857), [864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L864-L864), [931](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L931-L931), [949](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L949-L949)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

112:         if (to.code.length != 0) {

163:         if (to.code.length != 0) {

202:             interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

203:             interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

222:         if (to.code.length != 0) {

```
*GitHub*: [112](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L112-L112), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L163-L163), [202](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L202-L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L203-L203), [222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L222-L222)

```solidity
File: contracts/types/TokenId.sol

465:         if (i == 0)

471:         if (i == 1)

477:         if (i == 2)

483:         if (i == 3)

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

507:             for (uint256 i = 0; i < 4; ++i) {

508:                 if (self.optionRatio(i) == 0) {

512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

531:                     (self.strike(i) == Constants.MIN_V3POOL_TICK) ||

532:                     (self.strike(i) == Constants.MAX_V3POOL_TICK)

566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

592:                     if (self.isLong(i) == 1) return; // validated

```
*GitHub*: [465](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L465-L465), [471](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L471-L471), [477](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L477-L477), [483](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L483-L483), [501](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L501-L501), [507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L507-L507), [508](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L508-L508), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L512-L512), [528](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L528-L528), [531](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L531-L531), [532](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L532-L532), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L566-L566), [592](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L592-L592)

</details>





### [N&#x2011;22] Contract uses both `require()`/`revert()` as well as custom errors
Consider using just one method in a single file

*There is one instance of this issue:*

```solidity
File: contracts/libraries/Math.sol

13   library Math {
14:      /// @notice This is equivalent to type(uint256).max — used in assembly blocks as a replacement.

```
*GitHub*: [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L13-L14)



### [N&#x2011;23] Contracts should have all `public`/`external` functions exposed by `interface`s
The `contract`s should expose an `interface` so that other projects can more easily integrate with it, without having to develop their own non-standard variants.

*There are 4 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit  startToken(), getPoolData(), name(), symbol(), decimals(), asset(), totalAssets(), convertToShares(), convertToAssets(), maxDeposit(), previewDeposit(), deposit(), maxMint(), previewMint(), mint(), maxWithdraw(), previewWithdraw(), withdraw(), maxRedeem(), previewRedeem(), redeem(), exerciseCost(), delegate(), delegate(), refund(), refund(), revoke(), takeCommissionAddData(), exercise(), getAccountMarginDetails()
36   contract CollateralTracker is ERC20Minimal, Multicall {
37:      // Used for safecasting

```
*GitHub*: [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L36-L37)

```solidity
File: contracts/PanopticFactory.sol

/// @audit  initialize(), transferOwnership(), owner(), uniswapV3MintCallback(), deployNewPool(), minePoolAddress(), getPanopticPool()
26   contract PanopticFactory is Multicall {
27       /*//////////////////////////////////////////////////////////////
28                                    EVENTS
29       //////////////////////////////////////////////////////////////*/
30   
31       /// @notice Emitted when the ownership of the factory is transferred.
32       /// @param oldOwner The previous owner of the factory
33:      /// @param newOwner The new owner of the factory

```
*GitHub*: [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L26-L33)

```solidity
File: contracts/PanopticPool.sol

/// @audit  startPool(), assertPriceWithinBounds(), optionPositionBalance(), calculateAccumulatedFeesBatch(), calculatePortfolioValue(), pokeMedian(), mintOptions(), burnOptions(), burnOptions(), liquidate(), forceExercise(), univ3pool(), collateralToken0(), collateralToken1(), numberOfPositions(), settleLongPremium()
27   contract PanopticPool is ERC1155Holder, Multicall {
28       /*//////////////////////////////////////////////////////////////
29                                   EVENTS
30       //////////////////////////////////////////////////////////////*/
31   
32       /// @notice Emitted when an account is liquidated.
33       /// @dev Need to unpack bonusAmounts to get raw numbers, which are always positive.
34       /// @param liquidator Address of the caller whom is liquidating the distressed account.
35       /// @param liquidatee Address of the distressed/liquidatable account.
36       /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.
37:      /// The token0 bonus is in the right slot, and token1 bonus is in the left slot.

```
*GitHub*: [27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L27-L37)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit  initializeAMMPool(), uniswapV3MintCallback(), uniswapV3SwapCallback(), burnTokenizedPosition(), mintTokenizedPosition(), getAccountLiquidity(), getAccountPremium(), getAccountFeesBase(), getUniswapV3PoolFromId(), getPoolId()
72   contract SemiFungiblePositionManager is ERC1155, Multicall {
73       /*//////////////////////////////////////////////////////////////
74                                    EVENTS
75       //////////////////////////////////////////////////////////////*/
76   
77       /// @notice Emitted when a UniswapV3Pool is initialized.
78       /// @param uniswapPool Address of the underlying Uniswap v3 pool
79:      /// @param poolId The SFPM's pool identifier for the pool, including the 16-bit tick spacing and 48-bit pool pattern

```
*GitHub*: [72](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L72-L79)



### [N&#x2011;24] Custom error has no parameters showing error details
Consider adding parameters to the error to indicate which user or values caused the failure

*There are 2 instances of this issue:*

```solidity
File: contracts/libraries/Errors.sol

26:      error ExerciseeNotSolvent();

48:      error LeftRightInputError();

```
*GitHub*: [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L26-L26), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L48-L48)



### [N&#x2011;25] Custom errors should be used rather than `revert()`/`require()`
Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in `try`-`catch` blocks, and are easier to re-use and maintain.

*There are 9 instances of this issue:*

```solidity
File: contracts/libraries/Math.sol

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
*GitHub*: [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L361-L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L370-L370), [448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L448-L448), [484](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L484-L484), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L547-L547), [588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L588-L588), [624](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L624-L624), [665](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L665-L665), [701](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L701-L701)



### [N&#x2011;26] Duplicated `require()`/`revert()` checks should be refactored to a modifier or function


*There are 3 instances of this issue:*

```solidity
File: contracts/libraries/Math.sol

448:                 require(result < type(uint256).max);

588:                 require(result < type(uint256).max);

665:                 require(result < type(uint256).max);

```
*GitHub*: [448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L448-L448), [588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L588-L588), [665](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L665-L665)



### [N&#x2011;27] Expressions for constant values should use `immutable` rather than `constant`
While it does not save gas for some simple binary expressions because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor. As is the case with [const correctness](https://web.archive.org/web/20050611030410/http://www.parashift.com/c++-faq-lite/const-correctness.html), the code will still work, but the source code is more standard if the proper types are used. The compiler has included a lot of special-cased expression-in-constant-related handling code, and at the very least, by using `immutable`s rather than `constant`s, you can avoid any sub-optimial optimizations/bugs related to this less-frequently-used code.

*There are 7 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

```
*GitHub*: [103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L103-L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L105-L105), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L165-L165)

```solidity
File: contracts/libraries/Constants.sol

12:      int24 internal constant MIN_V3POOL_TICK = -887272;

```
*GitHub*: [12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L12-L12)

```solidity
File: contracts/libraries/Math.sol

15:      uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*GitHub*: [15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L15-L15)

```solidity
File: contracts/libraries/PanopticMath.sol

23:      uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*GitHub*: [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L23-L23)

```solidity
File: contracts/types/LeftRight.sol

26       int256 internal constant LEFT_HALF_BIT_MASK_INT =
27:          int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

```
*GitHub*: [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L26-L27)



### [N&#x2011;28] Imports could be organized more systematically
The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

*There is one instance of this issue:*

```solidity
File: contracts/PanopticFactory.sol

8:   import {IDonorNFT} from "@contracts/tokens/interfaces/IDonorNFT.sol";

```
*GitHub*: [8](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L8-L8)



### [N&#x2011;29] Inconsistent spacing in comments
Some lines use `// x` and some use `//x`. The instances below point out the usages that don't follow the majority, within each file

*There are 5 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

1118:             //compute total commission amount = commission rate + spread fee

```
*GitHub*: [1118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1118)

```solidity
File: contracts/SemiFungiblePositionManager.sol

610:              //construct the positionKey for the from and to addresses

643:              //update+store liquidity and fee values between accounts

821:                  //compute the swap amount, set as positive (exact input)

988:          LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache

```
*GitHub*: [610](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L610), [643](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L643), [821](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L821), [988](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L988)



### [N&#x2011;30] Large multiples of ten should use scientific notation
Large multiples of ten should use scientific notation (e.g. `1e6`) rather than decimal literals (e.g. `1000000`), for readability

*There are 8 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit 10_000
77:      uint256 internal constant DECIMALS = 10_000;

/// @audit 10_000
81:      int128 internal constant DECIMALS_128 = 10_000;

/// @audit 2000
200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

/// @audit 10_000
203                      (12500 * ratioTick) /
204:                     10_000 +

/// @audit 10_000
206:                     10_000 ** 2 +

/// @audit 10_000
208:                     10_000 ** 3

```
*GitHub*: [77](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L77-L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L81-L81), [200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L200-L200), [203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L203-L204), [206](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L206-L206), [208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L208-L208)

```solidity
File: contracts/PanopticPool.sol

/// @audit 10_000
174:     uint256 internal constant NO_BUFFER = 10_000;

/// @audit 10_000
1329:            return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

```
*GitHub*: [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L174-L174), [1329](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1329-L1329)



### [N&#x2011;31] Memory-safe annotation unnecessary
The [documentation](https://docs.soliditylang.org/en/latest/assembly.html#memory-safety) states that `Inline assembly that neither involves any operations that access memory nor assigns to any Solidity variables in memory is automatically considered memory-safe and does not need to be annotated`, and the blocks do none of those operations.

*There are 28 instances of this issue:*

```solidity
File: contracts/libraries/Math.sol

352              uint256 prod1; // Most significant 256 bits of the product
353              assembly ("memory-safe") {
354                  let mm := mulmod(a, b, not(0))
355                  prod0 := mul(a, b)
356                  prod1 := sub(sub(mm, prod0), lt(mm, prod0))
357:             }

361                  require(denominator > 0);
362                  assembly ("memory-safe") {
363                      result := div(prod0, denominator)
364:                 }

378              uint256 remainder;
379              assembly ("memory-safe") {
380                  remainder := mulmod(a, b, denominator)
381:             }

382              // Subtract 256 bit number from 512 bit number
383              assembly ("memory-safe") {
384                  prod1 := sub(prod1, gt(remainder, prod0))
385                  prod0 := sub(prod0, remainder)
386:             }

392              // Divide denominator by power of two
393              assembly ("memory-safe") {
394                  denominator := div(denominator, twos)
395:             }

397              // Divide [prod1 prod0] by the factors of two
398              assembly ("memory-safe") {
399                  prod0 := div(prod0, twos)
400:             }

403              // If twos is zero, then it becomes one
404              assembly ("memory-safe") {
405                  twos := add(div(sub(0, twos), twos), 1)
406:             }

466              uint256 prod1; // Most significant 256 bits of the product
467              assembly ("memory-safe") {
468                  let mm := mulmod(a, b, not(0))
469                  prod0 := mul(a, b)
470                  prod1 := sub(sub(mm, prod0), lt(mm, prod0))
471:             }

475                  uint256 res;
476                  assembly ("memory-safe") {
477                      // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
478                      res := shr(64, prod0)
479:                 }

492              uint256 remainder;
493              assembly ("memory-safe") {
494                  remainder := mulmod(a, b, 0x10000000000000000)
495:             }

496              // Subtract 256 bit number from 512 bit number
497              assembly ("memory-safe") {
498                  prod1 := sub(prod1, gt(remainder, prod0))
499                  prod0 := sub(prod0, remainder)
500:             }

502              // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)
503              assembly ("memory-safe") {
504                  // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
505                  prod0 := shr(64, prod0)
506:             }

529              uint256 prod1; // Most significant 256 bits of the product
530              assembly ("memory-safe") {
531                  let mm := mulmod(a, b, not(0))
532                  prod0 := mul(a, b)
533                  prod1 := sub(sub(mm, prod0), lt(mm, prod0))
534:             }

538                  uint256 res;
539                  assembly ("memory-safe") {
540                      // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
541                      res := shr(96, prod0)
542:                 }

555              uint256 remainder;
556              assembly ("memory-safe") {
557                  remainder := mulmod(a, b, 0x1000000000000000000000000)
558:             }

559              // Subtract 256 bit number from 512 bit number
560              assembly ("memory-safe") {
561                  prod1 := sub(prod1, gt(remainder, prod0))
562                  prod0 := sub(prod0, remainder)
563:             }

565              // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)
566              assembly ("memory-safe") {
567                  // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
568                  prod0 := shr(96, prod0)
569:             }

606              uint256 prod1; // Most significant 256 bits of the product
607              assembly ("memory-safe") {
608                  let mm := mulmod(a, b, not(0))
609                  prod0 := mul(a, b)
610                  prod1 := sub(sub(mm, prod0), lt(mm, prod0))
611:             }

615                  uint256 res;
616                  assembly ("memory-safe") {
617                      // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
618                      res := shr(128, prod0)
619:                 }

632              uint256 remainder;
633              assembly ("memory-safe") {
634                  remainder := mulmod(a, b, 0x100000000000000000000000000000000)
635:             }

636              // Subtract 256 bit number from 512 bit number
637              assembly ("memory-safe") {
638                  prod1 := sub(prod1, gt(remainder, prod0))
639                  prod0 := sub(prod0, remainder)
640:             }

642              // Divide [prod1 prod0] by the factors of two (note that this is just 2**128 since the denominator is a power of 2 itself)
643              assembly ("memory-safe") {
644                  // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
645                  prod0 := shr(128, prod0)
646:             }

683              uint256 prod1; // Most significant 256 bits of the product
684              assembly ("memory-safe") {
685                  let mm := mulmod(a, b, not(0))
686                  prod0 := mul(a, b)
687                  prod1 := sub(sub(mm, prod0), lt(mm, prod0))
688:             }

692                  uint256 res;
693                  assembly ("memory-safe") {
694                      // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
695                      res := shr(192, prod0)
696:                 }

709              uint256 remainder;
710              assembly ("memory-safe") {
711                  remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)
712:             }

713              // Subtract 256 bit number from 512 bit number
714              assembly ("memory-safe") {
715                  prod1 := sub(prod1, gt(remainder, prod0))
716                  prod0 := sub(prod0, remainder)
717:             }

719              // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)
720              assembly ("memory-safe") {
721                  // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
722                  prod0 := shr(192, prod0)
723:             }

738      function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
739          assembly ("memory-safe") {
740              result := add(div(a, b), gt(mod(a, b), 0))
741:         }

```
*GitHub*: [352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L352-L357), [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L361-L364), [378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L378-L381), [382](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L382-L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L392-L395), [397](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L397-L400), [403](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L403-L406), [466](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L466-L471), [475](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L475-L479), [492](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L492-L495), [496](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L496-L500), [502](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L502-L506), [529](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L529-L534), [538](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L538-L542), [555](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L555-L558), [559](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L559-L563), [565](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L565-L569), [606](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L606-L611), [615](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L615-L619), [632](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L632-L635), [636](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L636-L640), [642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L642-L646), [683](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L683-L688), [692](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L692-L696), [709](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L709-L712), [713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L713-L717), [719](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L719-L723), [738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L738-L741)



### [N&#x2011;32] Missing event for critical parameter change
Events help non-contract tools to track changes

*There are 7 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit s_underlyingIsToken0:  startToken()
/// @audit s_univ3token1:  startToken()
/// @audit s_univ3token0:  startToken()
/// @audit s_panopticPool:  startToken()
221      function startToken(
222          bool underlyingIsToken0,
223          address token0,
224          address token1,
225          uint24 fee,
226          PanopticPool panopticPool
227:     ) external {

```
*GitHub*: [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L221-L227), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L221-L227), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L221-L227), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L221-L227)

```solidity
File: contracts/PanopticFactory.sol

/// @audit s_owner:  initialize()
134:     function initialize(address _owner) public {

```
*GitHub*: [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L134-L134)

```solidity
File: contracts/PanopticPool.sol

/// @audit s_collateralToken1:  startPool()
/// @audit s_collateralToken0:  startPool()
291      function startPool(
292          IUniswapV3Pool _univ3pool,
293          address token0,
294          address token1,
295          CollateralTracker collateralTracker0,
296          CollateralTracker collateralTracker1
297:     ) external {

```
*GitHub*: [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L291-L297), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L291-L297)



### [N&#x2011;33] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability
Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related. The instances below refer to both mappings using the same key in the same function, so the mappings are related.

*There are 12 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit combine into a `struct`: s_grossPremiumLast,s_settledTokens
429      function _calculateAccumulatedPremia(
430          address user,
431          TokenId[] calldata positionIdList,
432          bool computeAllPremia,
433          bool includePendingPremium,
434          int24 atTick
435      ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {
436          uint256 pLength = positionIdList.length;
437          balances = new uint256[2][](pLength);
438  
439          address c_user = user;
440          // loop through each option position/tokenId
441          for (uint256 k = 0; k < pLength; ) {
442              TokenId tokenId = positionIdList[k];
443  
444              balances[k][0] = TokenId.unwrap(tokenId);
445              balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);
446  
447              (
448                  LeftRightSigned[4] memory premiaByLeg,
449                  uint256[2][4] memory premiumAccumulatorsByLeg
450              ) = _getPremia(
451                      tokenId,
452                      LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
453                      c_user,
454                      computeAllPremia,
455                      atTick
456                  );
457  
458              uint256 numLegs = tokenId.countLegs();
459              for (uint256 leg = 0; leg < numLegs; ) {
460                  if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
461                      bytes32 chunkKey = keccak256(
462                          abi.encodePacked(
463                              tokenId.strike(leg),
464                              tokenId.width(leg),
465                              tokenId.tokenType(leg)
466                          )
467                      );
468  
469                      LeftRightUnsigned availablePremium = _getAvailablePremium(
470                          _getTotalLiquidity(tokenId, leg),
471                          s_settledTokens[chunkKey],
472                          s_grossPremiumLast[chunkKey],
473                          LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
474                          premiumAccumulatorsByLeg[leg]
475                      );
476                      portfolioPremium = portfolioPremium.add(
477                          LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478                      );
479                  } else {
480                      portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
481                  }
482                  unchecked {
483                      ++leg;
484                  }
485              }
486  
487              unchecked {
488                  ++k;
489              }
490          }
491          return (portfolioPremium, balances);
492:     }

/// @audit combine into a `struct`: s_options,s_positionBalance
859      function _updatePositionDataBurn(address owner, TokenId tokenId) internal {
860          // reset balances and delete stored option data
861          s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
862  
863          uint256 numLegs = tokenId.countLegs();
864          for (uint256 leg = 0; leg < numLegs; ) {
865              if (tokenId.isLong(leg) == 0) {
866                  // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
867                  (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
868                  _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
869              }
870              s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
871              unchecked {
872                  ++leg;
873              }
874          }
875  
876          // Update the position list hash (hash = XOR of all keccak256(tokenId)). Remove hash by XOR'ing again
877          _updatePositionsHash(owner, tokenId, !ADD);
878:     }

/// @audit combine into a `struct`: s_options,s_positionBalance
1587     function settleLongPremium(
1588         TokenId[] calldata positionIdList,
1589         address owner,
1590         uint256 legIndex
1591     ) external {
1592         _validatePositionList(owner, positionIdList, 0);
1593 
1594         TokenId tokenId = positionIdList[positionIdList.length - 1];
1595 
1596         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();
1597 
1598         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
1599 
1600         LeftRightUnsigned accumulatedPremium;
1601         {
1602             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);
1603 
1604             uint256 tokenType = tokenId.tokenType(legIndex);
1605             (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
1606                 address(s_univ3pool),
1607                 address(this),
1608                 tokenType,
1609                 tickLower,
1610                 tickUpper,
1611                 currentTick,
1612                 1
1613             );
1614             accumulatedPremium = LeftRightUnsigned
1615                 .wrap(0)
1616                 .toRightSlot(premiumAccumulator0)
1617                 .toLeftSlot(premiumAccumulator1);
1618 
1619             // update the premium accumulator for the long position to the latest value
1620             // (the entire premia delta will be settled)
1621             LeftRightUnsigned premiumAccumulatorsLast = s_options[owner][tokenId][legIndex];
1622             s_options[owner][tokenId][legIndex] = accumulatedPremium;
1623 
1624             accumulatedPremium = accumulatedPremium.sub(premiumAccumulatorsLast);
1625         }
1626 
1627         uint256 liquidity = PanopticMath
1628             .getLiquidityChunk(tokenId, legIndex, s_positionBalance[owner][tokenId].rightSlot())
1629             .liquidity();
1630 
1631         unchecked {
1632             // update the realized premia
1633             LeftRightSigned realizedPremia = LeftRightSigned
1634                 .wrap(0)
1635                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))
1636                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));
1637 
1638             // deduct the paid premium tokens from the owner's balance and add them to the cumulative settled token delta
1639             s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());
1640             s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());
1641 
1642             bytes32 chunkKey = keccak256(
1643                 abi.encodePacked(
1644                     tokenId.strike(legIndex),
1645                     tokenId.width(legIndex),
1646                     tokenId.tokenType(legIndex)
1647                 )
1648             );
1649             // commit the delta in settled tokens (all of the premium paid by long chunks in the tokenIds list) to storage
1650             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(
1651                 LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))
1652             );
1653 
1654             emit PremiumSettled(owner, tokenId, realizedPremia);
1655         }
1656 
1657         // ensure the owner is solvent (insolvent accounts are not permitted to pay premium unless they are being liquidated)
1658         _validateSolvency(owner, positionIdList, NO_BUFFER);
1659:    }

/// @audit combine into a `struct`: s_grossPremiumLast,s_settledTokens
1666     function _updateSettlementPostMint(
1667         TokenId tokenId,
1668         LeftRightUnsigned[4] memory collectedByLeg,
1669         uint128 positionSize
1670     ) internal {
1671         uint256 numLegs = tokenId.countLegs();
1672         for (uint256 leg = 0; leg < numLegs; ++leg) {
1673             bytes32 chunkKey = keccak256(
1674                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1675             );
1676             // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers
1677             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1678 
1679             if (tokenId.isLong(leg) == 0) {
1680                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1681                     tokenId,
1682                     leg,
1683                     positionSize
1684                 );
1685 
1686                 // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (R + N)
1687                 uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1688 
1689                 // We need to adjust the grossPremiumLast value such that the result of
1690                 // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64
1691                 // G: total gross premium
1692                 // T: totalLiquidityBeforeMint
1693                 // R: positionLiquidity
1694                 // C: current grossPremium value
1695                 // L: current grossPremiumLast value
1696                 // Ln: updated grossPremiumLast value
1697                 // T * (C - L) = G
1698                 // (T + R) * (C - Ln) = G
1699                 //
1700                 // T * (C - L) = (T + R) * (C - Ln)
1701                 // (TC - TL) / (T + R) = C - Ln
1702                 // Ln = C - (TC - TL)/(T + R)
1703                 // Ln = (CT + CR - TC + TL)/(T+R)
1704                 // Ln = (CR + TL)/(T+R)
1705 
1706                 uint256[2] memory grossCurrent;
1707                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1708                     address(s_univ3pool),
1709                     address(this),
1710                     tokenId.tokenType(leg),
1711                     liquidityChunk.tickLower(),
1712                     liquidityChunk.tickUpper(),
1713                     type(int24).max,
1714                     0
1715                 );
1716 
1717                 unchecked {
1718                     // L
1719                     LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1720                     // R
1721                     uint256 positionLiquidity = liquidityChunk.liquidity();
1722                     // T (totalLiquidity is (T + R) after minting)
1723                     uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
1724 
1725                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1726                         .wrap(0)
1727                         .toRightSlot(
1728                             uint128(
1729                                 (grossCurrent[0] *
1730                                     positionLiquidity +
1731                                     grossPremiumLast.rightSlot() *
1732                                     totalLiquidityBefore) / (totalLiquidity)
1733                             )
1734                         )
1735                         .toLeftSlot(
1736                             uint128(
1737                                 (grossCurrent[1] *
1738                                     positionLiquidity +
1739                                     grossPremiumLast.leftSlot() *
1740                                     totalLiquidityBefore) / (totalLiquidity)
1741                             )
1742                         );
1743                 }
1744             }
1745         }
1746:    }

/// @audit combine into a `struct`: s_grossPremiumLast,s_settledTokens
1833     function _updateSettlementPostBurn(
1834         address owner,
1835         TokenId tokenId,
1836         LeftRightUnsigned[4] memory collectedByLeg,
1837         uint128 positionSize,
1838         bool commitLongSettled
1839     ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
1840         uint256 numLegs = tokenId.countLegs();
1841         uint256[2][4] memory premiumAccumulatorsByLeg;
1842 
1843         // compute accumulated fees
1844         (premiaByLeg, premiumAccumulatorsByLeg) = _getPremia(
1845             tokenId,
1846             positionSize,
1847             owner,
1848             COMPUTE_ALL_PREMIA,
1849             type(int24).max
1850         );
1851 
1852         for (uint256 leg = 0; leg < numLegs; ) {
1853             LeftRightSigned legPremia = premiaByLeg[leg];
1854 
1855             bytes32 chunkKey = keccak256(
1856                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1857             );
1858 
1859             // collected from Uniswap
1860             LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1861 
1862             if (LeftRightSigned.unwrap(legPremia) != 0) {
1863                 // (will be) paid by long legs
1864                 if (tokenId.isLong(leg) == 1) {
1865                     if (commitLongSettled)
1866                         settledTokens = LeftRightUnsigned.wrap(
1867                             uint256(
1868                                 LeftRightSigned.unwrap(
1869                                     LeftRightSigned
1870                                         .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1871                                         .sub(legPremia)
1872                                 )
1873                             )
1874                         );
1875                     realizedPremia = realizedPremia.add(legPremia);
1876                 } else {
1877                     uint256 positionLiquidity = PanopticMath
1878                         .getLiquidityChunk(tokenId, leg, positionSize)
1879                         .liquidity();
1880 
1881                     // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (T - R)
1882                     uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1883                     // T (totalLiquidity is (T - R) after burning)
1884                     uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;
1885 
1886                     LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1887 
1888                     LeftRightUnsigned availablePremium = _getAvailablePremium(
1889                         totalLiquidity + positionLiquidity,
1890                         settledTokens,
1891                         grossPremiumLast,
1892                         LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
1893                         premiumAccumulatorsByLeg[leg]
1894                     );
1895 
1896                     // subtract settled tokens sent to seller
1897                     settledTokens = settledTokens.sub(availablePremium);
1898 
1899                     // add available premium to amount that should be settled
1900                     realizedPremia = realizedPremia.add(
1901                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1902                     );
1903 
1904                     // We need to adjust the grossPremiumLast value such that the result of
1905                     // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostBurn/2**64 is equal to
1906                     // (grossPremium - grossPremiumLast)*totalLiquidityBeforeBurn/2**64 - premiumOwedToPosition
1907                     // G: total gross premium (- premiumOwedToPosition)
1908                     // T: totalLiquidityBeforeMint
1909                     // R: positionLiquidity
1910                     // C: current grossPremium value
1911                     // L: current grossPremiumLast value
1912                     // Ln: updated grossPremiumLast value
1913                     // T * (C - L) = G
1914                     // (T - R) * (C - Ln) = G - P
1915                     //
1916                     // T * (C - L) = (T - R) * (C - Ln) + P
1917                     // (TC - TL - P) / (T - R) = C - Ln
1918                     // Ln = C - (TC - TL - P) / (T - R)
1919                     // Ln = (TC - CR - TC + LT + P) / (T-R)
1920                     // Ln = (LT - CR + P) / (T-R)
1921 
1922                     unchecked {
1923                         uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
1924                         uint256 _leg = leg;
1925 
1926                         // if there's still liquidity, compute the new grossPremiumLast
1927                         // otherwise, we just reset grossPremiumLast to the current grossPremium
1928                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929                             ? LeftRightUnsigned
1930                                 .wrap(0)
1931                                 .toRightSlot(
1932                                     uint128(
1933                                         uint256(
1934                                             Math.max(
1935                                                 (int256(
1936                                                     grossPremiumLast.rightSlot() *
1937                                                         totalLiquidityBefore
1938                                                 ) -
1939                                                     int256(
1940                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941                                                             positionLiquidity
1942                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),
1943                                                 0
1944                                             )
1945                                         ) / totalLiquidity
1946                                     )
1947                                 )
1948                                 .toLeftSlot(
1949                                     uint128(
1950                                         uint256(
1951                                             Math.max(
1952                                                 (int256(
1953                                                     grossPremiumLast.leftSlot() *
1954                                                         totalLiquidityBefore
1955                                                 ) -
1956                                                     int256(
1957                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958                                                             positionLiquidity
1959                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960                                                 0
1961                                             )
1962                                         ) / totalLiquidity
1963                                     )
1964                                 )
1965                             : LeftRightUnsigned
1966                                 .wrap(0)
1967                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1969                     }
1970                 }
1971             }
1972 
1973             // update settled tokens in storage with all local deltas
1974             s_settledTokens[chunkKey] = settledTokens;
1975 
1976             unchecked {
1977                 ++leg;
1978             }
1979         }
1980:    }

```
*GitHub*: [429](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L429-L492), [859](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L859-L878), [1587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1587-L1659), [1666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1666-L1746), [1833](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit combine into a `struct`: s_accountFeesBase,s_accountLiquidity
593      function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {
594          // Validate tokenId
595          id.validate();
596  
597          // Extract univ3pool from the poolId map to Uniswap Pool
598          IUniswapV3Pool univ3pool = s_poolContext[id.poolId()].pool;
599  
600          uint256 numLegs = id.countLegs();
601          for (uint256 leg = 0; leg < numLegs; ) {
602              // for this leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
603              // @dev see `contracts/types/LiquidityChunk.sol`
604              LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
605                  id,
606                  leg,
607                  uint128(amount)
608              );
609  
610              //construct the positionKey for the from and to addresses
611              bytes32 positionKey_from = keccak256(
612                  abi.encodePacked(
613                      address(univ3pool),
614                      from,
615                      id.tokenType(leg),
616                      liquidityChunk.tickLower(),
617                      liquidityChunk.tickUpper()
618                  )
619              );
620              bytes32 positionKey_to = keccak256(
621                  abi.encodePacked(
622                      address(univ3pool),
623                      to,
624                      id.tokenType(leg),
625                      liquidityChunk.tickLower(),
626                      liquidityChunk.tickUpper()
627                  )
628              );
629  
630              // Revert if recipient already has that position
631              if (
632                  (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
633                  (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)
634              ) revert Errors.TransferFailed();
635  
636              // Revert if sender has long positions in that chunk or the entire liquidity is not being transferred
637              LeftRightUnsigned fromLiq = s_accountLiquidity[positionKey_from];
638              if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity())
639                  revert Errors.TransferFailed();
640  
641              LeftRightSigned fromBase = s_accountFeesBase[positionKey_from];
642  
643              //update+store liquidity and fee values between accounts
644              s_accountLiquidity[positionKey_to] = fromLiq;
645              s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);
646  
647              s_accountFeesBase[positionKey_to] = fromBase;
648              s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);
649              unchecked {
650                  ++leg;
651              }
652          }
653:     }

/// @audit combine into a `struct`: s_accountFeesBase,s_accountLiquidity
958      function _createLegInAMM(
959          IUniswapV3Pool univ3pool,
960          TokenId tokenId,
961          uint256 leg,
962          LiquidityChunk liquidityChunk,
963          bool isBurn
964      )
965          internal
966          returns (
967              LeftRightSigned moved,
968              LeftRightSigned itmAmounts,
969              LeftRightUnsigned collectedSingleLeg
970          )
971      {
972          uint256 tokenType = tokenId.tokenType(leg);
973          // unique key to identify the liquidity chunk in this uniswap pool
974          bytes32 positionKey = keccak256(
975              abi.encodePacked(
976                  address(univ3pool),
977                  msg.sender,
978                  tokenType,
979                  liquidityChunk.tickLower(),
980                  liquidityChunk.tickUpper()
981              )
982          );
983  
984          // update our internal bookkeeping of how much liquidity we have deployed in the AMM
985          // for example: if this _leg is short, we add liquidity to the amm, make sure to add that to our tracking
986          uint128 updatedLiquidity;
987          uint256 isLong = tokenId.isLong(leg);
988          LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache
989          {
990              // did we have liquidity already deployed in Uniswap for this chunk range from some past mint?
991  
992              // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user
993              // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller
994              // the reason why it is called "removedLiquidity" is because long options are created by removing -ie.short selling LP positions
995              uint128 startingLiquidity = currentLiquidity.rightSlot();
996              uint128 removedLiquidity = currentLiquidity.leftSlot();
997              uint128 chunkLiquidity = liquidityChunk.liquidity();
998  
999              if (isLong == 0) {
1000                 // selling/short: so move from msg.sender *to* uniswap
1001                 // we're minting more liquidity in uniswap: so add the incoming liquidity chunk to the existing liquidity chunk
1002                 updatedLiquidity = startingLiquidity + chunkLiquidity;
1003 
1004                 /// @dev If the isLong flag is 0=short but the position was burnt, then this is closing a long position
1005                 /// @dev so the amount of removed liquidity should decrease.
1006                 if (isBurn) {
1007                     removedLiquidity -= chunkLiquidity;
1008                 }
1009             } else {
1010                 // the _leg is long (buying: moving *from* uniswap to msg.sender)
1011                 // so we seek to move the incoming liquidity chunk *out* of uniswap - but was there sufficient liquidity sitting in uniswap
1012                 // in the first place?
1013                 if (startingLiquidity < chunkLiquidity) {
1014                     // the amount we want to move (liquidityChunk.legLiquidity()) out of uniswap is greater than
1015                     // what the account that owns the liquidity in uniswap has (startingLiquidity)
1016                     // we must ensure that an account can only move its own liquidity out of uniswap
1017                     // so we revert in this case
1018                     revert Errors.NotEnoughLiquidity();
1019                 } else {
1020                     // startingLiquidity is >= chunkLiquidity, so no possible underflow
1021                     unchecked {
1022                         // we want to move less than what already sits in uniswap, no problem:
1023                         updatedLiquidity = startingLiquidity - chunkLiquidity;
1024                     }
1025                 }
1026 
1027                 /// @dev If the isLong flag is 1=long and the position is minted, then this is opening a long position
1028                 /// @dev so the amount of removed liquidity should increase.
1029                 if (!isBurn) {
1030                     // we can't remove more liquidity than we add in the first place, so this can't overflow
1031                     unchecked {
1032                         removedLiquidity += chunkLiquidity;
1033                     }
1034                 }
1035             }
1036 
1037             // update the starting liquidity for this position for next time around
1038             s_accountLiquidity[positionKey] = LeftRightUnsigned
1039                 .wrap(0)
1040                 .toLeftSlot(removedLiquidity)
1041                 .toRightSlot(updatedLiquidity);
1042         }
1043 
1044         // track how much liquidity we need to collect from uniswap
1045         // add the fees that accumulated in uniswap within the liquidityChunk:
1046         {
1047             /** if the position is NOT long (selling a put or a call), then _mintLiquidity to move liquidity
1048                 from the msg.sender to the uniswap v3 pool:
1049                 Selling(isLong=0): Mint chunk of liquidity in Uniswap (defined by upper tick, lower tick, and amount)
1050                        ┌─────────────────────────────────┐
1051                 ▲     ┌▼┐ liquidityChunk                 │
1052                 │  ┌──┴─┴──┐                         ┌───┴──┐
1053                 │  │       │                         │      │
1054                 └──┴───────┴──►                      └──────┘
1055                    Uniswap v3                      msg.sender
1056             
1057              else: the position is long (buying a put or a call), then _burnLiquidity to remove liquidity from univ3
1058                 Buying(isLong=1): Burn in Uniswap
1059                        ┌─────────────────┐
1060                 ▲     ┌┼┐                │
1061                 │  ┌──┴─┴──┐         ┌───▼──┐
1062                 │  │       │         │      │
1063                 └──┴───────┴──►      └──────┘
1064                     Uniswap v3      msg.sender 
1065             */
1066             moved = isLong == 0
1067                 ? _mintLiquidity(liquidityChunk, univ3pool)
1068                 : _burnLiquidity(liquidityChunk, univ3pool); // from msg.sender to Uniswap
1069             // add the moved liquidity chunk to amount we need to collect from uniswap:
1070 
1071             // Is this _leg ITM?
1072             // if tokenType is 1, and we transacted some token0: then this leg is ITM!
1073             if (tokenType == 1) {
1074                 // extract amount moved out of UniswapV3 pool
1075                 itmAmounts = itmAmounts.toRightSlot(moved.rightSlot());
1076             }
1077             // if tokenType is 0, and we transacted some token1: then this leg is ITM
1078             if (tokenType == 0) {
1079                 // Add this in-the-money amount transacted.
1080                 itmAmounts = itmAmounts.toLeftSlot(moved.leftSlot());
1081             }
1082         }
1083 
1084         // if there was liquidity at that tick before the transaction, collect any accumulated fees
1085         if (currentLiquidity.rightSlot() > 0) {
1086             collectedSingleLeg = _collectAndWritePositionData(
1087                 liquidityChunk,
1088                 univ3pool,
1089                 currentLiquidity,
1090                 positionKey,
1091                 moved,
1092                 isLong
1093             );
1094         }
1095 
1096         // position has been touched, update s_accountFeesBase with the latest values from the pool.positions
1097         // round up the stored feesbase to minimize Δfeesbase when we next calculate it
1098         s_accountFeesBase[positionKey] = _getFeesBase(
1099             univ3pool,
1100             updatedLiquidity,
1101             liquidityChunk,
1102             true
1103         );
1104:    }

/// @audit combine into a `struct`: s_accountPremiumGross,s_accountPremiumOwed
1110     function _updateStoredPremia(
1111         bytes32 positionKey,
1112         LeftRightUnsigned currentLiquidity,
1113         LeftRightUnsigned collectedAmounts
1114     ) private {
1115         (
1116             LeftRightUnsigned deltaPremiumOwed,
1117             LeftRightUnsigned deltaPremiumGross
1118         ) = _getPremiaDeltas(currentLiquidity, collectedAmounts);
1119 
1120         // add deltas to accumulators and freeze both accumulators (for a token) if one of them overflows
1121         // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)
1122         // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing
1123         (s_accountPremiumOwed[positionKey], s_accountPremiumGross[positionKey]) = LeftRightLibrary
1124             .addCapped(
1125                 s_accountPremiumOwed[positionKey],
1126                 deltaPremiumOwed,
1127                 s_accountPremiumGross[positionKey],
1128                 deltaPremiumGross
1129             );
1130:    }

/// @audit combine into a `struct`: s_accountFeesBase,s_accountLiquidity,s_accountPremiumGross,s_accountPremiumOwed
1449     function getAccountPremium(
1450         address univ3pool,
1451         address owner,
1452         uint256 tokenType,
1453         int24 tickLower,
1454         int24 tickUpper,
1455         int24 atTick,
1456         uint256 isLong
1457     ) external view returns (uint128, uint128) {
1458         bytes32 positionKey = keccak256(
1459             abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)
1460         );
1461 
1462         LeftRightUnsigned acctPremia;
1463 
1464         // Compute the premium up to the current block (ie. after last touch until now). Do not proceed if atTick == type(int24).max = 8388608
1465         if (atTick < type(int24).max) {
1466             // unique key to identify the liquidity chunk in this uniswap pool
1467             LeftRightUnsigned accountLiquidities = s_accountLiquidity[positionKey];
1468             uint128 netLiquidity = accountLiquidities.rightSlot();
1469             if (netLiquidity != 0) {
1470                 LeftRightUnsigned amountToCollect;
1471                 {
1472                     IUniswapV3Pool _univ3pool = IUniswapV3Pool(univ3pool);
1473                     int24 _tickLower = tickLower;
1474                     int24 _tickUpper = tickUpper;
1475 
1476                     // how much fees have been accumulated within the liquidity chunk since last time we updated this chunk?
1477                     // Compute (currentFeesGrowth - oldFeesGrowth), the amount to collect
1478                     // currentFeesGrowth (calculated from FeesCalc.calculateAMMSwapFeesLiquidityChunk) is (ammFeesCollectedPerLiquidity * liquidityChunk.liquidity())
1479                     // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])
1480                     LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(
1481                         _univ3pool,
1482                         atTick,
1483                         _tickLower,
1484                         _tickUpper,
1485                         netLiquidity
1486                     );
1487 
1488                     // If the current feesBase is close or identical to the stored one, the amountToCollect can be negative.
1489                     // This is because the stored feesBase is rounded up, and the current feesBase is rounded down.
1490                     // When this is the case, we want to behave as if there are 0 fees, so we just rectify the values.
1491                     // Guaranteed to be positive, so swap to unsigned type
1492                     amountToCollect = LeftRightUnsigned.wrap(
1493                         uint256(
1494                             LeftRightSigned.unwrap(feesBase.subRect(s_accountFeesBase[positionKey]))
1495                         )
1496                     );
1497                 }
1498 
1499                 (LeftRightUnsigned premiumOwed, LeftRightUnsigned premiumGross) = _getPremiaDeltas(
1500                     accountLiquidities,
1501                     amountToCollect
1502                 );
1503 
1504                 // add deltas to accumulators and freeze both accumulators (for a token) if one of them overflows
1505                 // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)
1506                 // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing
1507                 (premiumOwed, premiumGross) = LeftRightLibrary.addCapped(
1508                     s_accountPremiumOwed[positionKey],
1509                     premiumOwed,
1510                     s_accountPremiumGross[positionKey],
1511                     premiumGross
1512                 );
1513 
1514                 acctPremia = isLong == 1 ? premiumOwed : premiumGross;
1515             }
1516         } else {
1517             // Extract the account liquidity for a given uniswap pool, owner, token type, and ticks
1518             acctPremia = isLong == 1
1519                 ? s_accountPremiumOwed[positionKey]
1520                 : s_accountPremiumGross[positionKey];
1521         }
1522         return (acctPremia.rightSlot(), acctPremia.leftSlot());
1523:    }

```
*GitHub*: [593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L593-L653), [958](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L958-L1104), [1110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1110-L1130), [1449](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1449-L1523)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit combine into a `struct`: balanceOf,isApprovedForAll
94       function safeTransferFrom(
95           address from,
96           address to,
97           uint256 id,
98           uint256 amount,
99           bytes calldata data
100      ) public virtual {
101          if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
102  
103          balanceOf[from][id] -= amount;
104  
105          // balance will never overflow
106          unchecked {
107              balanceOf[to][id] += amount;
108          }
109  
110          emit TransferSingle(msg.sender, from, to, id, amount);
111  
112          if (to.code.length != 0) {
113              if (
114                  ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=
115                  ERC1155Holder.onERC1155Received.selector
116              ) {
117                  revert UnsafeRecipient();
118              }
119          }
120:     }

/// @audit combine into a `struct`: balanceOf,isApprovedForAll
130      function safeBatchTransferFrom(
131          address from,
132          address to,
133          uint256[] calldata ids,
134          uint256[] calldata amounts,
135          bytes calldata data
136      ) public virtual {
137          if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
138  
139          // Storing these outside the loop saves ~15 gas per iteration.
140          uint256 id;
141          uint256 amount;
142  
143          for (uint256 i = 0; i < ids.length; ) {
144              id = ids[i];
145              amount = amounts[i];
146  
147              balanceOf[from][id] -= amount;
148  
149              // balance will never overflow
150              unchecked {
151                  balanceOf[to][id] += amount;
152              }
153  
154              // An array can't have a total length
155              // larger than the max uint256 value.
156              unchecked {
157                  ++i;
158              }
159          }
160  
161          emit TransferBatch(msg.sender, from, to, ids, amounts);
162  
163          if (to.code.length != 0) {
164              if (
165                  ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
166                  ERC1155Holder.onERC1155BatchReceived.selector
167              ) {
168                  revert UnsafeRecipient();
169              }
170          }
171:     }

```
*GitHub*: [94](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L94-L120), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L130-L171)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit combine into a `struct`: allowance,balanceOf
81       function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
82           uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.
83   
84           if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
85   
86           balanceOf[from] -= amount;
87   
88           // Cannot overflow because the sum of all user
89           // balances can't exceed the max uint256 value.
90           unchecked {
91               balanceOf[to] += amount;
92           }
93   
94           emit Transfer(from, to, amount);
95   
96           return true;
97:      }

```
*GitHub*: [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L81-L97)



### [N&#x2011;34] NatSpec: Contract declarations should have `@author` tags


*There are 3 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

36   contract CollateralTracker is ERC20Minimal, Multicall {
37:      // Used for safecasting

```
*GitHub*: [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L36-L37)

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6    interface IDonorNFT {
7        /// @notice Called to issue reward NFT to the deployer of a new `PanopticPool` through `PanopticFactory`.
8        /// @param deployer The address that deployed `newPoolContract` and donated funds for full-range liquidity
9        /// @param newPoolContract The address of the `PanopticPool` that was deployed
10       /// @param token0 Token0 of the Uniswap pool `newPoolContract` was deployed on
11       /// @param token1 Token1 of the Uniswap pool `newPoolContract` was deployed on
12:      /// @param fee The fee tier, in hundredths of bips, of the Uniswap pool `newPoolContract` was deployed on

```
*GitHub*: [6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6-L12)

```solidity
File: contracts/types/LiquidityChunk.sol

52   library LiquidityChunkLibrary {
53:      /// @notice AND mask to strip the `tickLower` value from a packed LiquidityChunk

```
*GitHub*: [52](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L52-L53)



### [N&#x2011;35] NatSpec: Contract declarations should have `@dev` tags
`@dev` is used to explain extra details to developers

*There are 12 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

36   contract CollateralTracker is ERC20Minimal, Multicall {
37:      // Used for safecasting

```
*GitHub*: [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L36-L37)

```solidity
File: contracts/PanopticFactory.sol

26   contract PanopticFactory is Multicall {
27       /*//////////////////////////////////////////////////////////////
28                                    EVENTS
29       //////////////////////////////////////////////////////////////*/
30   
31       /// @notice Emitted when the ownership of the factory is transferred.
32       /// @param oldOwner The previous owner of the factory
33:      /// @param newOwner The new owner of the factory

```
*GitHub*: [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L26-L33)

```solidity
File: contracts/libraries/CallbackLib.sol

12   library CallbackLib {
13:      /// @notice Defining characteristics of a Uni V3 pool

```
*GitHub*: [12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L12-L13)

```solidity
File: contracts/libraries/Constants.sol

7    library Constants {
8:       /// @notice Fixed point multiplier: 2**96

```
*GitHub*: [7](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L7-L8)

```solidity
File: contracts/libraries/Errors.sol

7    library Errors {
8        /// @notice Casting error
9:       /// @dev e.g. uint128(uint256(a)) fails

```
*GitHub*: [7](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L7-L9)

```solidity
File: contracts/libraries/InteractionHelper.sol

17   library InteractionHelper {
18       /// @notice Function that performs approvals on behalf of the PanopticPool for CollateralTracker and SemiFungiblePositionManager.
19       /// @param sfpm The SemiFungiblePositionManager being approved for both token0 and token1
20       /// @param ct0 The CollateralTracker (token0) being approved for token0
21       /// @param ct1 The CollateralTracker (token1) being approved for token1
22       /// @param token0 The token0 (in Uniswap) being approved for
23:      /// @param token1 The token1 (in Uniswap) being approved for

```
*GitHub*: [17](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L17-L23)

```solidity
File: contracts/libraries/Math.sol

13   library Math {
14:      /// @notice This is equivalent to type(uint256).max — used in assembly blocks as a replacement.

```
*GitHub*: [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L13-L14)

```solidity
File: contracts/libraries/PanopticMath.sol

18   library PanopticMath {
19:      // Used for safecasting

```
*GitHub*: [18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L18-L19)

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6    interface IDonorNFT {
7        /// @notice Called to issue reward NFT to the deployer of a new `PanopticPool` through `PanopticFactory`.
8        /// @param deployer The address that deployed `newPoolContract` and donated funds for full-range liquidity
9        /// @param newPoolContract The address of the `PanopticPool` that was deployed
10       /// @param token0 Token0 of the Uniswap pool `newPoolContract` was deployed on
11       /// @param token1 Token1 of the Uniswap pool `newPoolContract` was deployed on
12:      /// @param fee The fee tier, in hundredths of bips, of the Uniswap pool `newPoolContract` was deployed on

```
*GitHub*: [6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6-L12)

```solidity
File: contracts/types/LeftRight.sol

17   library LeftRightLibrary {
18:      // Used for safecasting

```
*GitHub*: [17](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L17-L18)

```solidity
File: contracts/types/LiquidityChunk.sol

52   library LiquidityChunkLibrary {
53:      /// @notice AND mask to strip the `tickLower` value from a packed LiquidityChunk

```
*GitHub*: [52](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L52-L53)

```solidity
File: contracts/types/TokenId.sol

60   library TokenIdLibrary {
61:      /// @notice AND mask to extract all `isLong` bits for each leg from a TokenId

```
*GitHub*: [60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L60-L61)

</details>





### [N&#x2011;36] NatSpec: Contract declarations should have `@notice` tags
`@notice` is used to explain to end users what the contract does, and the compiler interprets `///` or `/**` comments (but not `//` or `/*`) as this tag if one wasn't explicitly provided. Note that the NatSpec comment must be _above_ the contract definition.

*There is one instance of this issue:*

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6    interface IDonorNFT {
7        /// @notice Called to issue reward NFT to the deployer of a new `PanopticPool` through `PanopticFactory`.
8        /// @param deployer The address that deployed `newPoolContract` and donated funds for full-range liquidity
9        /// @param newPoolContract The address of the `PanopticPool` that was deployed
10       /// @param token0 Token0 of the Uniswap pool `newPoolContract` was deployed on
11       /// @param token1 Token1 of the Uniswap pool `newPoolContract` was deployed on
12:      /// @param fee The fee tier, in hundredths of bips, of the Uniswap pool `newPoolContract` was deployed on

```
*GitHub*: [6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6-L12)



### [N&#x2011;37] NatSpec: Contract declarations should have `@title` tags


*There are 5 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

36   contract CollateralTracker is ERC20Minimal, Multicall {
37:      // Used for safecasting

```
*GitHub*: [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L36-L37)

```solidity
File: contracts/libraries/InteractionHelper.sol

17   library InteractionHelper {
18       /// @notice Function that performs approvals on behalf of the PanopticPool for CollateralTracker and SemiFungiblePositionManager.
19       /// @param sfpm The SemiFungiblePositionManager being approved for both token0 and token1
20       /// @param ct0 The CollateralTracker (token0) being approved for token0
21       /// @param ct1 The CollateralTracker (token1) being approved for token1
22       /// @param token0 The token0 (in Uniswap) being approved for
23:      /// @param token1 The token1 (in Uniswap) being approved for

```
*GitHub*: [17](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L17-L23)

```solidity
File: contracts/libraries/SafeTransferLib.sol

11   library SafeTransferLib {
12       /*//////////////////////////////////////////////////////////////
13                               ERC20 OPERATIONS
14       //////////////////////////////////////////////////////////////*/
15   
16       /// @notice Safely transfers ERC20 tokens from one address to another.
17       /// @param token The address of the ERC20 token
18       /// @param from The address to transfer tokens from
19       /// @param to The address to transfer tokens to
20:      /// @param amount The amount of tokens to transfer

```
*GitHub*: [11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L11-L20)

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6    interface IDonorNFT {
7        /// @notice Called to issue reward NFT to the deployer of a new `PanopticPool` through `PanopticFactory`.
8        /// @param deployer The address that deployed `newPoolContract` and donated funds for full-range liquidity
9        /// @param newPoolContract The address of the `PanopticPool` that was deployed
10       /// @param token0 Token0 of the Uniswap pool `newPoolContract` was deployed on
11       /// @param token1 Token1 of the Uniswap pool `newPoolContract` was deployed on
12:      /// @param fee The fee tier, in hundredths of bips, of the Uniswap pool `newPoolContract` was deployed on

```
*GitHub*: [6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6-L12)

```solidity
File: contracts/types/LiquidityChunk.sol

52   library LiquidityChunkLibrary {
53:      /// @notice AND mask to strip the `tickLower` value from a packed LiquidityChunk

```
*GitHub*: [52](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L52-L53)



### [N&#x2011;38] NatSpec: Contract declarations should have descriptions
e.g. `@dev` or `@notice`, and it must appear above the contract definition braces in order to be identified by the compiler as NatSpec

*There is one instance of this issue:*

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6    interface IDonorNFT {
7        /// @notice Called to issue reward NFT to the deployer of a new `PanopticPool` through `PanopticFactory`.
8        /// @param deployer The address that deployed `newPoolContract` and donated funds for full-range liquidity
9        /// @param newPoolContract The address of the `PanopticPool` that was deployed
10       /// @param token0 Token0 of the Uniswap pool `newPoolContract` was deployed on
11       /// @param token1 Token1 of the Uniswap pool `newPoolContract` was deployed on
12:      /// @param fee The fee tier, in hundredths of bips, of the Uniswap pool `newPoolContract` was deployed on

```
*GitHub*: [6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6-L12)



### [N&#x2011;39] NatSpec: Error declarations should have `@dev` tags
`@dev` is used to explain extra details to developers

*There are 33 instances of this issue:*

```solidity
File: contracts/libraries/Errors.sol

13:      error CollateralTokenAlreadyInitialized();

16:      error DepositTooLarge();

20:      error EffectiveLiquidityAboveThreshold();

23:      error ExceedsMaximumRedemption();

26:      error ExerciseeNotSolvent();

29:      error InputListFail();

32:      error InvalidSalt();

35:      error InvalidTick();

38:      error InvalidNotionalValue();

42:      error InvalidTokenIdParameter(uint256 parameterType);

45:      error InvalidUniswapCallback();

48:      error LeftRightInputError();

51:      error NoLegsExercisable();

54:      error NotEnoughCollateral();

57:      error PositionTooLarge();

60:      error NotALongLeg();

63:      error NotEnoughLiquidity();

66:      error NotMarginCalled();

73:      error NotPanopticPool();

76:      error OptionsBalanceZero();

79:      error PoolAlreadyInitialized();

82:      error PositionAlreadyMinted();

85:      error PositionCountNotZero();

88:      error PriceBoundFail();

91:      error ReentrantCall();

95:      error StaleTWAP();

98:      error TooManyPositionsOpen();

101:     error TransferFailed();

105:     error TicksNotInitializable();

108:     error UnderOverFlow();

111:     error UniswapPoolNotInitialized();

```
*GitHub*: [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L13-L13), [16](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L16-L16), [20](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L20-L20), [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L23-L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L26-L26), [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L29-L29), [32](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L32-L32), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L35-L35), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L38-L38), [42](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L42-L42), [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L45-L45), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L48-L48), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L51-L51), [54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L54-L54), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L57-L57), [60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L60-L60), [63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L63-L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L66-L66), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L73-L73), [76](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L76-L76), [79](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L79-L79), [82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L82-L82), [85](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L85-L85), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L88-L88), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L91-L91), [95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L95-L95), [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L98-L98), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L101-L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L105-L105), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L108-L108), [111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L111-L111)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

55:      error NotAuthorized();

58:      error UnsafeRecipient();

```
*GitHub*: [55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L55-L55), [58](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L58-L58)



### [N&#x2011;40] NatSpec: Event `@param` tag is missing


*There are 62 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit Missing '@param sender'
/// @audit Missing '@param owner'
/// @audit Missing '@param assets'
/// @audit Missing '@param shares'
44       /// @notice Emitted when assets are deposited into the Collateral Tracker.
45       /// @param sender The address of the caller (and depositor)
46       /// @param owner The address of the recipient of the newly minted shares
47       /// @param assets The amount of assets deposited by 'sender' in exchange for 'shares'
48       /// @param shares The amount of shares minted to 'owner'
49:      event Deposit(address indexed sender, address indexed owner, uint256 assets, uint256 shares);

/// @audit Missing '@param sender'
53       /// @param receiver The address of the recipient of the withdrawn assets
54       /// @param owner The address of the owner of the shares being burned
55       /// @param assets The amount of assets withdrawn to 'receiver'
56       /// @param shares The amount of shares burned by 'owner' in exchange for 'assets'
57       event Withdraw(
58:          address indexed sender,

/// @audit Missing '@param receiver'
54       /// @param owner The address of the owner of the shares being burned
55       /// @param assets The amount of assets withdrawn to 'receiver'
56       /// @param shares The amount of shares burned by 'owner' in exchange for 'assets'
57       event Withdraw(
58           address indexed sender,
59:          address indexed receiver,

/// @audit Missing '@param owner'
55       /// @param assets The amount of assets withdrawn to 'receiver'
56       /// @param shares The amount of shares burned by 'owner' in exchange for 'assets'
57       event Withdraw(
58           address indexed sender,
59           address indexed receiver,
60:          address indexed owner,

/// @audit Missing '@param assets'
56       /// @param shares The amount of shares burned by 'owner' in exchange for 'assets'
57       event Withdraw(
58           address indexed sender,
59           address indexed receiver,
60           address indexed owner,
61:          uint256 assets,

/// @audit Missing '@param shares'
57       event Withdraw(
58           address indexed sender,
59           address indexed receiver,
60           address indexed owner,
61           uint256 assets,
62:          uint256 shares

```
*GitHub*: [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L44-L49), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L44-L49), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L44-L49), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L44-L49), [53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L53-L58), [54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L54-L59), [55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L55-L60), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L56-L61), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L57-L62)

```solidity
File: contracts/PanopticFactory.sol

/// @audit Missing '@param oldOwner'
/// @audit Missing '@param newOwner'
29       //////////////////////////////////////////////////////////////*/
30   
31       /// @notice Emitted when the ownership of the factory is transferred.
32       /// @param oldOwner The previous owner of the factory
33       /// @param newOwner The new owner of the factory
34:      event OwnershipTransferred(address indexed oldOwner, address indexed newOwner);

/// @audit Missing '@param poolAddress'
39       /// @param collateralTracker0 Address of the collateral tracker contract for token0
40       /// @param collateralTracker1 Address of the collateral tracker contract for token1
41       /// @param amount0 The amount of token0 deployed at full range
42       /// @param amount1 The amount of token1 deployed at full range
43       event PoolDeployed(
44:          PanopticPool indexed poolAddress,

/// @audit Missing '@param uniswapPool'
40       /// @param collateralTracker1 Address of the collateral tracker contract for token1
41       /// @param amount0 The amount of token0 deployed at full range
42       /// @param amount1 The amount of token1 deployed at full range
43       event PoolDeployed(
44           PanopticPool indexed poolAddress,
45:          IUniswapV3Pool indexed uniswapPool,

/// @audit Missing '@param collateralTracker0'
41       /// @param amount0 The amount of token0 deployed at full range
42       /// @param amount1 The amount of token1 deployed at full range
43       event PoolDeployed(
44           PanopticPool indexed poolAddress,
45           IUniswapV3Pool indexed uniswapPool,
46:          CollateralTracker collateralTracker0,

/// @audit Missing '@param collateralTracker1'
42       /// @param amount1 The amount of token1 deployed at full range
43       event PoolDeployed(
44           PanopticPool indexed poolAddress,
45           IUniswapV3Pool indexed uniswapPool,
46           CollateralTracker collateralTracker0,
47:          CollateralTracker collateralTracker1,

/// @audit Missing '@param amount0'
43       event PoolDeployed(
44           PanopticPool indexed poolAddress,
45           IUniswapV3Pool indexed uniswapPool,
46           CollateralTracker collateralTracker0,
47           CollateralTracker collateralTracker1,
48:          uint256 amount0,

/// @audit Missing '@param amount1'
44           PanopticPool indexed poolAddress,
45           IUniswapV3Pool indexed uniswapPool,
46           CollateralTracker collateralTracker0,
47           CollateralTracker collateralTracker1,
48           uint256 amount0,
49:          uint256 amount1

```
*GitHub*: [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L29-L34), [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L29-L34), [39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L39-L44), [40](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L40-L45), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L41-L46), [42](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L42-L47), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L43-L48), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L44-L49)

```solidity
File: contracts/PanopticPool.sol

/// @audit Missing '@param liquidator'
34       /// @param liquidator Address of the caller whom is liquidating the distressed account.
35       /// @param liquidatee Address of the distressed/liquidatable account.
36       /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.
37       /// The token0 bonus is in the right slot, and token1 bonus is in the left slot.
38       event AccountLiquidated(
39:          address indexed liquidator,

/// @audit Missing '@param liquidatee'
35       /// @param liquidatee Address of the distressed/liquidatable account.
36       /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.
37       /// The token0 bonus is in the right slot, and token1 bonus is in the left slot.
38       event AccountLiquidated(
39           address indexed liquidator,
40:          address indexed liquidatee,

/// @audit Missing '@param bonusAmounts'
36       /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.
37       /// The token0 bonus is in the right slot, and token1 bonus is in the left slot.
38       event AccountLiquidated(
39           address indexed liquidator,
40           address indexed liquidatee,
41:          LeftRightSigned bonusAmounts

/// @audit Missing '@param exercisor'
47       /// @param user Address of the owner of the liquidated position
48       /// @param tokenId TokenId of the liquidated position.
49       /// @param exerciseFee LeftRight encoding for the cost paid by the exercisor to force the exercise of the token.
50       /// The token0 fee is in the right slot, and token1 fee is in the left slot.
51       event ForcedExercised(
52:          address indexed exercisor,

/// @audit Missing '@param user'
48       /// @param tokenId TokenId of the liquidated position.
49       /// @param exerciseFee LeftRight encoding for the cost paid by the exercisor to force the exercise of the token.
50       /// The token0 fee is in the right slot, and token1 fee is in the left slot.
51       event ForcedExercised(
52           address indexed exercisor,
53:          address indexed user,

/// @audit Missing '@param tokenId'
49       /// @param exerciseFee LeftRight encoding for the cost paid by the exercisor to force the exercise of the token.
50       /// The token0 fee is in the right slot, and token1 fee is in the left slot.
51       event ForcedExercised(
52           address indexed exercisor,
53           address indexed user,
54:          TokenId indexed tokenId,

/// @audit Missing '@param exerciseFee'
50       /// The token0 fee is in the right slot, and token1 fee is in the left slot.
51       event ForcedExercised(
52           address indexed exercisor,
53           address indexed user,
54           TokenId indexed tokenId,
55:          LeftRightSigned exerciseFee

/// @audit Missing '@param user'
58       /// @notice Emitted when premium is settled independent of a mint/burn (e.g. during `settleLongPremium`)
59       /// @param user Address of the owner of the settled position.
60       /// @param tokenId TokenId of the settled position.
61       /// @param settledAmounts LeftRight encoding for the amount of premium settled for token0 (right slot) and token1 (left slot).
62       event PremiumSettled(
63:          address indexed user,

/// @audit Missing '@param tokenId'
59       /// @param user Address of the owner of the settled position.
60       /// @param tokenId TokenId of the settled position.
61       /// @param settledAmounts LeftRight encoding for the amount of premium settled for token0 (right slot) and token1 (left slot).
62       event PremiumSettled(
63           address indexed user,
64:          TokenId indexed tokenId,

/// @audit Missing '@param settledAmounts'
60       /// @param tokenId TokenId of the settled position.
61       /// @param settledAmounts LeftRight encoding for the amount of premium settled for token0 (right slot) and token1 (left slot).
62       event PremiumSettled(
63           address indexed user,
64           TokenId indexed tokenId,
65:          LeftRightSigned settledAmounts

/// @audit Missing '@param recipient'
71       /// @param positionSize The number of contracts burnt, expressed in terms of the asset.
72       /// @param tokenId TokenId of the burnt option.
73       /// @param premia LeftRight packing for the amount of premia collected for token0 and token1.
74       /// The token0 premia is in the right slot, and token1 premia is in the left slot.
75       event OptionBurnt(
76:          address indexed recipient,

/// @audit Missing '@param positionSize'
72       /// @param tokenId TokenId of the burnt option.
73       /// @param premia LeftRight packing for the amount of premia collected for token0 and token1.
74       /// The token0 premia is in the right slot, and token1 premia is in the left slot.
75       event OptionBurnt(
76           address indexed recipient,
77:          uint128 positionSize,

/// @audit Missing '@param tokenId'
73       /// @param premia LeftRight packing for the amount of premia collected for token0 and token1.
74       /// The token0 premia is in the right slot, and token1 premia is in the left slot.
75       event OptionBurnt(
76           address indexed recipient,
77           uint128 positionSize,
78:          TokenId indexed tokenId,

/// @audit Missing '@param premia'
74       /// The token0 premia is in the right slot, and token1 premia is in the left slot.
75       event OptionBurnt(
76           address indexed recipient,
77           uint128 positionSize,
78           TokenId indexed tokenId,
79:          LeftRightSigned premia

/// @audit Missing '@param recipient'
86       /// @param tokenId TokenId of the created option.
87       /// @param poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),
88       /// right 64bits for token0 and left 64bits for token1, defined as (inAMM * 10_000) / totalAssets().
89       /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.
90       event OptionMinted(
91:          address indexed recipient,

/// @audit Missing '@param positionSize'
87       /// @param poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),
88       /// right 64bits for token0 and left 64bits for token1, defined as (inAMM * 10_000) / totalAssets().
89       /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.
90       event OptionMinted(
91           address indexed recipient,
92:          uint128 positionSize,

/// @audit Missing '@param tokenId'
88       /// right 64bits for token0 and left 64bits for token1, defined as (inAMM * 10_000) / totalAssets().
89       /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.
90       event OptionMinted(
91           address indexed recipient,
92           uint128 positionSize,
93:          TokenId indexed tokenId,

/// @audit Missing '@param poolUtilizations'
89       /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.
90       event OptionMinted(
91           address indexed recipient,
92           uint128 positionSize,
93           TokenId indexed tokenId,
94:          uint128 poolUtilizations

```
*GitHub*: [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L34-L39), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L35-L40), [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L36-L41), [47](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L47-L52), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L48-L53), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L49-L54), [50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L50-L55), [58](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L58-L63), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L59-L64), [60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L60-L65), [71](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L71-L76), [72](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L72-L77), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L73-L78), [74](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L74-L79), [86](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L86-L91), [87](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L87-L92), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L88-L93), [89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L89-L94)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit Missing '@param uniswapPool'
/// @audit Missing '@param poolId'
75       //////////////////////////////////////////////////////////////*/
76   
77       /// @notice Emitted when a UniswapV3Pool is initialized.
78       /// @param uniswapPool Address of the underlying Uniswap v3 pool
79       /// @param poolId The SFPM's pool identifier for the pool, including the 16-bit tick spacing and 48-bit pool pattern
80:      event PoolInitialized(address indexed uniswapPool, uint64 poolId);

/// @audit Missing '@param recipient'
83       /// @dev Recipient is used to track whether it was burned directly by the user or through an option contract
84       /// @param recipient The address of the user who burned the position
85       /// @param tokenId The tokenId of the burned position
86       /// @param positionSize The number of contracts burnt, expressed in terms of the asset
87       event TokenizedPositionBurnt(
88:          address indexed recipient,

/// @audit Missing '@param tokenId'
84       /// @param recipient The address of the user who burned the position
85       /// @param tokenId The tokenId of the burned position
86       /// @param positionSize The number of contracts burnt, expressed in terms of the asset
87       event TokenizedPositionBurnt(
88           address indexed recipient,
89:          TokenId indexed tokenId,

/// @audit Missing '@param positionSize'
85       /// @param tokenId The tokenId of the burned position
86       /// @param positionSize The number of contracts burnt, expressed in terms of the asset
87       event TokenizedPositionBurnt(
88           address indexed recipient,
89           TokenId indexed tokenId,
90:          uint128 positionSize

/// @audit Missing '@param caller'
94       /// @dev Recipient is used to track whether it was minted directly by the user or through an option contract
95       /// @param caller the caller who created the position. In 99% of cases `caller` == `recipient`.
96       /// @param tokenId The tokenId of the minted position
97       /// @param positionSize The number of contracts minted, expressed in terms of the asset
98       event TokenizedPositionMinted(
99:          address indexed caller,

/// @audit Missing '@param tokenId'
95       /// @param caller the caller who created the position. In 99% of cases `caller` == `recipient`.
96       /// @param tokenId The tokenId of the minted position
97       /// @param positionSize The number of contracts minted, expressed in terms of the asset
98       event TokenizedPositionMinted(
99           address indexed caller,
100:         TokenId indexed tokenId,

/// @audit Missing '@param positionSize'
96       /// @param tokenId The tokenId of the minted position
97       /// @param positionSize The number of contracts minted, expressed in terms of the asset
98       event TokenizedPositionMinted(
99           address indexed caller,
100          TokenId indexed tokenId,
101:         uint128 positionSize

```
*GitHub*: [75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L75-L80), [75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L75-L80), [83](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L83-L88), [84](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L84-L89), [85](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L85-L90), [94](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L94-L99), [95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L95-L100), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L96-L101)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit Missing '@param operator'
18       /// @param from The user who sent the tokens
19       /// @param to The user who received the tokens
20       /// @param id The ERC1155 token id
21       /// @param amount The amount of tokens transferred
22       event TransferSingle(
23:          address indexed operator,

/// @audit Missing '@param from'
19       /// @param to The user who received the tokens
20       /// @param id The ERC1155 token id
21       /// @param amount The amount of tokens transferred
22       event TransferSingle(
23           address indexed operator,
24:          address indexed from,

/// @audit Missing '@param to'
20       /// @param id The ERC1155 token id
21       /// @param amount The amount of tokens transferred
22       event TransferSingle(
23           address indexed operator,
24           address indexed from,
25:          address indexed to,

/// @audit Missing '@param id'
21       /// @param amount The amount of tokens transferred
22       event TransferSingle(
23           address indexed operator,
24           address indexed from,
25           address indexed to,
26:          uint256 id,

/// @audit Missing '@param amount'
22       event TransferSingle(
23           address indexed operator,
24           address indexed from,
25           address indexed to,
26           uint256 id,
27:          uint256 amount

/// @audit Missing '@param operator'
32       /// @param from The user who sent the tokens
33       /// @param to The user who received the tokens
34       /// @param ids The ERC1155 token ids
35       /// @param amounts The amounts of tokens transferred
36       event TransferBatch(
37:          address indexed operator,

/// @audit Missing '@param from'
33       /// @param to The user who received the tokens
34       /// @param ids The ERC1155 token ids
35       /// @param amounts The amounts of tokens transferred
36       event TransferBatch(
37           address indexed operator,
38:          address indexed from,

/// @audit Missing '@param to'
34       /// @param ids The ERC1155 token ids
35       /// @param amounts The amounts of tokens transferred
36       event TransferBatch(
37           address indexed operator,
38           address indexed from,
39:          address indexed to,

/// @audit Missing '@param ids'
35       /// @param amounts The amounts of tokens transferred
36       event TransferBatch(
37           address indexed operator,
38           address indexed from,
39           address indexed to,
40:          uint256[] ids,

/// @audit Missing '@param amounts'
36       event TransferBatch(
37           address indexed operator,
38           address indexed from,
39           address indexed to,
40           uint256[] ids,
41:          uint256[] amounts

/// @audit Missing '@param owner'
/// @audit Missing '@param operator'
/// @audit Missing '@param approved'
43   
44       /// @notice Emitted when the approval status of an operator to transfer all tokens on behalf of a user is modified.
45       /// @param owner The user who approved or disapproved `operator` to transfer their tokens
46       /// @param operator The user who was approved or disapproved to transfer all tokens on behalf of `owner`
47       /// @param approved Whether `operator` is approved or disapproved to transfer all tokens on behalf of `owner`
48:      event ApprovalForAll(address indexed owner, address indexed operator, bool approved);

```
*GitHub*: [18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L18-L23), [19](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L19-L24), [20](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L20-L25), [21](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L21-L26), [22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L22-L27), [32](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L32-L37), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L33-L38), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L34-L39), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L35-L40), [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L36-L41), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L43-L48), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L43-L48), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L43-L48)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit Missing '@param from'
/// @audit Missing '@param to'
/// @audit Missing '@param amount'
13   
14       /// @notice Emitted when tokens are transferred
15       /// @param from The sender of the tokens
16       /// @param to The recipient of the tokens
17       /// @param amount The amount of tokens transferred
18:      event Transfer(address indexed from, address indexed to, uint256 amount);

/// @audit Missing '@param owner'
/// @audit Missing '@param spender'
/// @audit Missing '@param amount'
19   
20       /// @notice Emitted when a user approves another user to spend tokens on their behalf
21       /// @param owner The user who approved the spender
22       /// @param spender The user who was approved to spend tokens
23       /// @param amount The amount of tokens approved to spend
24:      event Approval(address indexed owner, address indexed spender, uint256 amount);

```
*GitHub*: [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L13-L18), [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L13-L18), [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L13-L18), [19](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L19-L24), [19](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L19-L24), [19](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L19-L24)



### [N&#x2011;41] NatSpec: Event declarations should have `@dev` tags
`@dev` is used to explain extra details to developers

*There are 11 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

49:      event Deposit(address indexed sender, address indexed owner, uint256 assets, uint256 shares);

57       event Withdraw(
58           address indexed sender,
59           address indexed receiver,
60           address indexed owner,
61           uint256 assets,
62           uint256 shares
63:      );

```
*GitHub*: [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L49-L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L57-L63)

```solidity
File: contracts/PanopticFactory.sol

34:      event OwnershipTransferred(address indexed oldOwner, address indexed newOwner);

43       event PoolDeployed(
44           PanopticPool indexed poolAddress,
45           IUniswapV3Pool indexed uniswapPool,
46           CollateralTracker collateralTracker0,
47           CollateralTracker collateralTracker1,
48           uint256 amount0,
49           uint256 amount1
50:      );

```
*GitHub*: [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L34-L34), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L43-L50)

```solidity
File: contracts/PanopticPool.sol

62       event PremiumSettled(
63           address indexed user,
64           TokenId indexed tokenId,
65           LeftRightSigned settledAmounts
66:      );

```
*GitHub*: [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L62-L66)

```solidity
File: contracts/SemiFungiblePositionManager.sol

80:      event PoolInitialized(address indexed uniswapPool, uint64 poolId);

```
*GitHub*: [80](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L80-L80)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

22       event TransferSingle(
23           address indexed operator,
24           address indexed from,
25           address indexed to,
26           uint256 id,
27           uint256 amount
28:      );

36       event TransferBatch(
37           address indexed operator,
38           address indexed from,
39           address indexed to,
40           uint256[] ids,
41           uint256[] amounts
42:      );

48:      event ApprovalForAll(address indexed owner, address indexed operator, bool approved);

```
*GitHub*: [22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L22-L28), [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L36-L42), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L48-L48)

```solidity
File: contracts/tokens/ERC20Minimal.sol

18:      event Transfer(address indexed from, address indexed to, uint256 amount);

24:      event Approval(address indexed owner, address indexed spender, uint256 amount);

```
*GitHub*: [18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L18-L18), [24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L24-L24)



### [N&#x2011;42] NatSpec: Function `@param` tag is missing


*There are 2 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit Missing '@param atTick'
429      function _calculateAccumulatedPremia(
430          address user,
431          TokenId[] calldata positionIdList,
432          bool computeAllPremia,
433          bool includePendingPremium,
434:         int24 atTick

```
*GitHub*: [429](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L429-L434)

```solidity
File: contracts/libraries/Math.sol

/// @audit Missing '@param toDowncast'
297          if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();
298      }
299  
300      /// @notice Downcast uint256 to uint128, but cap at type(uint128).max on overflow.
301      /// @return downcastedInt The downcasted uint (uint128 now)
302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

```
*GitHub*: [297](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L297-L302)



### [N&#x2011;43] NatSpec: Function `@return` tag is missing


*There are 10 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit Missing '@return netPaid'
/// @audit Missing '@return premiasByLeg'
788      /// @notice Helper to burn option during a liquidation from an account _owner.
789      /// @param owner the owner of the option position to be liquidated.
790      /// @param tickLimitLow Price slippage limit when burning an ITM option
791      /// @param tickLimitHigh Price slippage limit when burning an ITM option
792      /// @param commitLongSettled Whether to commit the long premium that will be settled to storage
793      /// @param positionIdList the option position to liquidate.
794      function _burnAllOptionsFrom(
795          address owner,
796          int24 tickLimitLow,
797          int24 tickLimitHigh,
798          bool commitLongSettled,
799          TokenId[] calldata positionIdList
800:     ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

/// @audit Missing '@return realizedPremia'
/// @audit Missing '@return paidAmounts'
/// @audit Missing '@return premiaByLeg'
948      /// @notice Burns and handles the exercise of options.
949      /// @param commitLongSettled Whether to commit the long premium that will be settled to storage
950      /// @param tickLimitLow The lower slippage limit on the tick.
951      /// @param tickLimitHigh The upper slippage limit on the tick.
952      /// @param tokenId The option position to burn.
953      /// @param positionSize The size of the option position, expressed in terms of the asset.
954      /// @param owner The owner of the option position.
955      function _burnAndHandleExercise(
956          bool commitLongSettled,
957          int24 tickLimitLow,
958          int24 tickLimitHigh,
959          TokenId tokenId,
960          uint128 positionSize,
961          address owner
962      )
963          internal
964          returns (
965              LeftRightSigned realizedPremia,
966              LeftRightSigned[4] memory premiaByLeg,
967              LeftRightSigned paidAmounts
968          )
969:     {

/// @audit Missing '@return  '
1284     /// @notice check whether an account is solvent at a given `atTick` with a collateral requirement of `buffer`/10_000 multiplied by the requirement of `positionIdList`.
1285     /// @param account The account to check solvency for.
1286     /// @param positionIdList The list of positions to check solvency for.
1287     /// @param currentTick The current tick of the Uniswap pool (needed for fee calculations).
1288     /// @param atTick The tick to check solvency at.
1289     /// @param buffer The buffer to apply to the collateral requirement.
1290     function _checkSolvencyAtTick(
1291         address account,
1292         TokenId[] calldata positionIdList,
1293         int24 currentTick,
1294         int24 atTick,
1295         uint256 buffer
1296:    ) internal view returns (bool) {

/// @audit Missing '@return premiumAccumulatorsByLeg'
/// @audit Missing '@return premiaByLeg'
1496     /// @notice Compute the premia collected for a single option position 'tokenId'.
1497     /// @param tokenId The option position.
1498     /// @param positionSize The number of contracts (size) of the option position.
1499     /// @param owner The holder of the tokenId option.
1500     /// @param computeAllPremia Whether to compute accumulated premia for all legs held by the user (true), or just owed premia for long legs (false).
1501     /// @param atTick The tick at which the premia is calculated -> use (atTick < type(int24).max) to compute it
1502     /// up to current block. atTick = type(int24).max will only consider fees as of the last on-chain transaction.
1503     function _getPremia(
1504         TokenId tokenId,
1505         uint128 positionSize,
1506         address owner,
1507         bool computeAllPremia,
1508         int24 atTick
1509     )
1510         internal
1511         view
1512         returns (
1513             LeftRightSigned[4] memory premiaByLeg,
1514             uint256[2][4] memory premiumAccumulatorsByLeg
1515         )
1516:    {

/// @audit Missing '@return totalLiquidity'
1798     /// @notice Query the total amount of liquidity sold in the corresponding chunk for a position leg
1799     /// @dev totalLiquidity (total sold) = removedLiquidity + netLiquidity (in AMM)
1800     /// @param tokenId The option position
1801     /// @param leg The leg of the option position to get `totalLiquidity for
1802     function _getTotalLiquidity(
1803         TokenId tokenId,
1804         uint256 leg
1805:    ) internal view returns (uint256 totalLiquidity) {

```
*GitHub*: [788](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L788-L800), [788](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L788-L800), [948](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L948-L969), [948](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L948-L969), [948](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L948-L969), [1284](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1284-L1296), [1496](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1496-L1516), [1496](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1496-L1516), [1798](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1798-L1805)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit Missing '@return feesBase'
1132     /// @notice Compute the feesGrowth * liquidity / 2**128 by reading feeGrowthInside0LastX128 and feeGrowthInside1LastX128 from univ3pool.positions.
1133     /// @param univ3pool the Uniswap pool.
1134     /// @param liquidity the total amount of liquidity in the AMM for the specific position
1135     /// @param liquidityChunk has lower tick, upper tick, and liquidity amount to mint
1136     /// @param roundUp if true, round up the feesBase, otherwise round down
1137     /// @dev stored fees base is rounded up and the current fees base is rounded down to minimize the amount of fees collected (Δfeesbase) in favor of the protocol
1138     function _getFeesBase(
1139         IUniswapV3Pool univ3pool,
1140         uint128 liquidity,
1141         LiquidityChunk liquidityChunk,
1142         bool roundUp
1143:    ) private view returns (LeftRightSigned feesBase) {

```
*GitHub*: [1132](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1132-L1143)



### [N&#x2011;44] NatSpec: Function declarations should have `@dev` tags
`@dev` is used to explain to developers what the potential integration issues/foot-guns are

*There are 147 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

178      constructor(
179          uint256 _commissionFee,
180          uint256 _sellerCollateralRatio,
181          uint256 _buyerCollateralRatio,
182          int256 _forceExerciseCost,
183          uint256 _targetPoolUtilization,
184          uint256 _saturatedPoolUtilization,
185          uint256 _ITMSpreadMultiplier
186:     ) {

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

591      function redeem(
592          uint256 shares,
593          address receiver,
594          address owner
595:     ) external returns (uint256 assets) {

911      function revoke(
912          address delegator,
913          address delegatee,
914          uint256 assets
915:     ) external onlyPanopticPool {

995      function takeCommissionAddData(
996          address optionOwner,
997          int128 longAmount,
998          int128 shortAmount,
999          int128 swappedAmount
1000:    ) external onlyPanopticPool returns (int256 utilization) {

1096     function _getExchangedAmount(
1097         int128 longAmount,
1098         int128 shortAmount,
1099         int128 swappedAmount
1100:    ) internal view returns (int256 exchangedAmount) {

1245     function _getRequiredCollateralAtTickSinglePosition(
1246         TokenId tokenId,
1247         uint128 positionSize,
1248         int24 atTick,
1249         uint128 poolUtilization
1250:    ) internal view returns (uint256 tokenRequired) {

```
*GitHub*: [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L178-L186), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L289-L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L303-L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L310-L310), [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L361-L361), [379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L379-L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L386-L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L392-L392), [399](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L399-L399), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L444-L444), [453](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L453-L453), [518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L518-L518), [572](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L572-L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L581-L581), [591](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L591-L595), [911](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L911-L915), [995](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L995-L1000), [1096](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1096-L1100), [1245](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1245-L1250)

```solidity
File: contracts/PanopticFactory.sol

115      constructor(
116          address _WETH9,
117          SemiFungiblePositionManager _SFPM,
118          IUniswapV3Factory _univ3Factory,
119          IDonorNFT _donorNFT,
120          address _poolReference,
121          address _collateralReference
122:     ) {

134:     function initialize(address _owner) public {

147:     function transferOwnership(address newOwner) external {

159:     function owner() external view returns (address) {

335      function _mintFullRange(
336          IUniswapV3Pool v3Pool,
337          address token0,
338          address token1,
339          uint24 fee
340:     ) internal returns (uint256, uint256) {

420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {

```
*GitHub*: [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L115-L122), [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L134-L134), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L147-L147), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L159-L159), [335](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L335-L340), [420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L420-L420)

```solidity
File: contracts/PanopticPool.sol

280:     constructor(SemiFungiblePositionManager _sfpm) {

352      function optionPositionBalance(
353          address user,
354          TokenId tokenId
355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

429      function _calculateAccumulatedPremia(
430          address user,
431          TokenId[] calldata positionIdList,
432          bool computeAllPremia,
433          bool includePendingPremium,
434          int24 atTick
435:     ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

499      function _getSlippageLimits(
500          int24 tickLimitLow,
501          int24 tickLimitHigh
502:     ) internal pure returns (int24, int24) {

522:     function pokeMedian() external {

547      function mintOptions(
548          TokenId[] calldata positionIdList,
549          uint128 positionSize,
550          uint64 effectiveLiquidityLimitX32,
551          int24 tickLimitLow,
552          int24 tickLimitHigh
553:     ) external {

614      function _mintOptions(
615          TokenId[] calldata positionIdList,
616          uint128 positionSize,
617          uint64 effectiveLiquidityLimitX32,
618          int24 tickLimitLow,
619          int24 tickLimitHigh
620:     ) internal {

794      function _burnAllOptionsFrom(
795          address owner,
796          int24 tickLimitLow,
797          int24 tickLimitHigh,
798          bool commitLongSettled,
799          TokenId[] calldata positionIdList
800:     ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

826      function _burnOptions(
827          bool commitLongSettled,
828          TokenId tokenId,
829          address owner,
830          int24 tickLimitLow,
831          int24 tickLimitHigh
832:     ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

955      function _burnAndHandleExercise(
956          bool commitLongSettled,
957          int24 tickLimitLow,
958          int24 tickLimitHigh,
959          TokenId tokenId,
960          uint128 positionSize,
961          address owner
962      )
963          internal
964          returns (
965              LeftRightSigned realizedPremia,
966              LeftRightSigned[4] memory premiaByLeg,
967              LeftRightSigned paidAmounts
968          )
969:     {

1290     function _checkSolvencyAtTick(
1291         address account,
1292         TokenId[] calldata positionIdList,
1293         int24 currentTick,
1294         int24 atTick,
1295         uint256 buffer
1296:    ) internal view returns (bool) {

1339     function _getSolvencyBalances(
1340         LeftRightUnsigned tokenData0,
1341         LeftRightUnsigned tokenData1,
1342         uint160 sqrtPriceX96
1343:    ) internal pure returns (uint256 balanceCross, uint256 thresholdCross) {

1425:    function univ3pool() external view returns (IUniswapV3Pool) {

1431:    function collateralToken0() external view returns (CollateralTracker collateralToken) {

1437:    function collateralToken1() external view returns (CollateralTracker) {

1444:    function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

1450:    function getUniV3TWAP() internal view returns (int24 twapTick) {

1465     function _checkLiquiditySpread(
1466         TokenId tokenId,
1467         uint256 leg,
1468         int24 tickLower,
1469         int24 tickUpper,
1470         uint64 effectiveLiquidityLimitX32
1471:    ) internal view {

1503     function _getPremia(
1504         TokenId tokenId,
1505         uint128 positionSize,
1506         address owner,
1507         bool computeAllPremia,
1508         int24 atTick
1509     )
1510         internal
1511         view
1512         returns (
1513             LeftRightSigned[4] memory premiaByLeg,
1514             uint256[2][4] memory premiumAccumulatorsByLeg
1515         )
1516:    {

```
*GitHub*: [280](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L280-L280), [352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L352-L355), [429](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L429-L435), [499](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L499-L502), [522](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L522-L522), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L547-L553), [614](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L614-L620), [794](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L794-L800), [826](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L826-L832), [859](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L859-L859), [955](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L955-L969), [1290](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1290-L1296), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1339-L1343), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1425-L1425), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1431-L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1437-L1437), [1444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1444-L1444), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1450-L1450), [1465](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1465-L1471), [1503](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1503-L1516)

```solidity
File: contracts/SemiFungiblePositionManager.sol

330:     function endReentrancyLock(uint64 poolId) internal {

341:     constructor(IUniswapV3Factory _factory) {

504      function mintTokenizedPosition(
505          TokenId tokenId,
506          uint128 positionSize,
507          int24 slippageTickLimitLow,
508          int24 slippageTickLimitHigh
509      )
510          external
511          ReentrancyLock(tokenId.poolId())
512          returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
513:     {

680      function _validateAndForwardToAMM(
681          TokenId tokenId,
682          uint128 positionSize,
683          int24 tickLimitLow,
684          int24 tickLimitHigh,
685          bool isBurn
686:     ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

756      function swapInAMM(
757          IUniswapV3Pool univ3pool,
758          LeftRightSigned itmAmounts
759:     ) internal returns (LeftRightSigned totalSwapped) {

1110     function _updateStoredPremia(
1111         bytes32 positionKey,
1112         LeftRightUnsigned currentLiquidity,
1113         LeftRightUnsigned collectedAmounts
1114:    ) private {

1255     function _collectAndWritePositionData(
1256         LiquidityChunk liquidityChunk,
1257         IUniswapV3Pool univ3pool,
1258         LeftRightUnsigned currentLiquidity,
1259         bytes32 positionKey,
1260         LeftRightSigned movedInLeg,
1261         uint256 isLong
1262:    ) internal returns (LeftRightUnsigned collectedChunk) {

```
*GitHub*: [330](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L330-L330), [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L341-L341), [504](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L504-L513), [680](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L680-L686), [756](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L756-L759), [1110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1110-L1114), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1255-L1262)

```solidity
File: contracts/libraries/CallbackLib.sol

30       function validateCallback(
31           address sender,
32           IUniswapV3Factory factory,
33           PoolFeatures memory features
34:      ) internal view {

```
*GitHub*: [30](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L30-L34)

```solidity
File: contracts/libraries/FeesCalc.sol

46       function getPortfolioValue(
47           int24 atTick,
48           mapping(TokenId tokenId => LeftRightUnsigned balance) storage userBalance,
49           TokenId[] calldata positionIdList
50:      ) external view returns (int256 value0, int256 value1) {

```
*GitHub*: [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L46-L50)

```solidity
File: contracts/libraries/InteractionHelper.sol

24       function doApprovals(
25           SemiFungiblePositionManager sfpm,
26           CollateralTracker ct0,
27           CollateralTracker ct1,
28           address token0,
29           address token1
30:      ) external {

91       function computeSymbol(
92           address token,
93           string memory prefix
94:      ) external view returns (string memory) {

107:     function computeDecimals(address token) external view returns (uint8) {

```
*GitHub*: [24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L24-L30), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L91-L94), [107](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L107-L107)

```solidity
File: contracts/libraries/Math.sol

25:      function min24(int24 a, int24 b) internal pure returns (int24) {

33:      function max24(int24 a, int24 b) internal pure returns (int24) {

41:      function min(uint256 a, uint256 b) internal pure returns (uint256) {

49:      function min(int256 a, int256 b) internal pure returns (int256) {

57:      function max(uint256 a, uint256 b) internal pure returns (uint256) {

65:      function max(int256 a, int256 b) internal pure returns (int256) {

91:      function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {

207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

221      function getAmountsForLiquidity(
222          int24 currentTick,
223          LiquidityChunk liquidityChunk
224:     ) internal pure returns (uint256 amount0, uint256 amount1) {

296:     function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

440      function mulDivRoundingUp(
441          uint256 a,
442          uint256 b,
443          uint256 denominator
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
*GitHub*: [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L25-L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L33-L33), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L41-L41), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L49-L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L57-L57), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L65-L65), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L91-L91), [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L207-L207), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L221-L224), [296](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L296-L296), [302](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L302-L302), [311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L311-L311), [318](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L318-L318), [325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L325-L325), [440](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L440-L444), [458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L458-L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L521-L521), [584](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L584-L584), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L598-L598), [661](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L661-L661), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L675-L675), [738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L738-L738), [753](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L753-L753), [776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L776-L776)

```solidity
File: contracts/libraries/PanopticMath.sol

59:      function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

75:      function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

289      function getLiquidityChunk(
290          TokenId tokenId,
291          uint256 legIndex,
292          uint128 positionSize
293:     ) internal pure returns (LiquidityChunk) {

338      function getTicks(
339          int24 strike,
340          int24 width,
341          int24 tickSpacing
342:     ) internal pure returns (int24 tickLower, int24 tickUpper) {

390      function computeExercisedAmounts(
391          TokenId tokenId,
392          uint128 positionSize
393:     ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {

419      function convertCollateralData(
420          LeftRightUnsigned tokenData0,
421          LeftRightUnsigned tokenData1,
422          uint256 tokenType,
423          uint160 sqrtPriceX96
424:     ) internal pure returns (uint256, uint256) {

445      function convertCollateralData(
446          LeftRightUnsigned tokenData0,
447          LeftRightUnsigned tokenData1,
448          uint256 tokenType,
449          int24 tick
450:     ) internal pure returns (uint256, uint256) {

574      function getAmountsMoved(
575          TokenId tokenId,
576          uint128 positionSize,
577          uint256 legIndex
578:     ) internal pure returns (LeftRightUnsigned) {

607      function _calculateIOAmounts(
608          TokenId tokenId,
609          uint128 positionSize,
610          uint256 legIndex
611:     ) internal pure returns (LeftRightSigned longs, LeftRightSigned shorts) {

651      function getLiquidationBonus(
652          LeftRightUnsigned tokenData0,
653          LeftRightUnsigned tokenData1,
654          uint160 sqrtPriceX96Twap,
655          uint160 sqrtPriceX96Final,
656          LeftRightSigned netExchanged,
657          LeftRightSigned premia
658:     ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

917      function getRefundAmounts(
918          address refunder,
919          LeftRightSigned refundValues,
920          int24 atTick,
921          CollateralTracker collateral0,
922          CollateralTracker collateral1
923:     ) external view returns (LeftRightSigned) {

```
*GitHub*: [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L59-L59), [75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L75-L75), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L289-L293), [338](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L338-L342), [390](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L390-L393), [419](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L419-L424), [445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L445-L450), [574](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L574-L578), [607](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L607-L611), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651-L658), [917](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L917-L923)

```solidity
File: contracts/libraries/SafeTransferLib.sol

21:      function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:      function safeTransfer(address token, address to, uint256 amount) internal {

```
*GitHub*: [21](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L21-L21), [52](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L52-L52)

```solidity
File: contracts/multicall/Multicall.sol

12:      function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {

```
*GitHub*: [12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L12-L12)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

81:      function setApprovalForAll(address operator, bool approved) public {

200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

214:     function _mint(address to, uint256 id, uint256 amount) internal {

236:     function _burn(address from, uint256 id, uint256 amount) internal {

```
*GitHub*: [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L81-L81), [200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L200-L200), [214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L214-L214), [236](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L236-L236)

```solidity
File: contracts/tokens/ERC20Minimal.sol

49:      function approve(address spender, uint256 amount) public returns (bool) {

61:      function transfer(address to, uint256 amount) public virtual returns (bool) {

103:     function _transferFrom(address from, address to, uint256 amount) internal {

122:     function _mint(address to, uint256 amount) internal {

136:     function _burn(address from, uint256 amount) internal {

```
*GitHub*: [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L49-L49), [61](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L61-L61), [103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L103-L103), [122](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L122-L122), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L136-L136)

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

13       function issueNFT(
14           address deployer,
15           PanopticPool newPoolContract,
16           address token0,
17           address token1,
18           uint24 fee
19:      ) external;

```
*GitHub*: [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L13-L19)

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

27:      function transfer(address to, uint256 amount) external;

```
*GitHub*: [27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L27-L27)

```solidity
File: contracts/types/LeftRight.sol

39:      function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46:      function rightSlot(LeftRightSigned self) internal pure returns (int128) {

59       function toRightSlot(
60           LeftRightUnsigned self,
61           uint128 right
62:      ) internal pure returns (LeftRightUnsigned) {

78       function toRightSlot(
79           LeftRightSigned self,
80           int128 right
81:      ) internal pure returns (LeftRightSigned) {

101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

121      function toLeftSlot(
122          LeftRightUnsigned self,
123          uint128 left
124:     ) internal pure returns (LeftRightUnsigned) {

134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

148      function add(
149          LeftRightUnsigned x,
150          LeftRightUnsigned y
151:     ) internal pure returns (LeftRightUnsigned z) {

171      function sub(
172          LeftRightUnsigned x,
173          LeftRightUnsigned y
174:     ) internal pure returns (LeftRightUnsigned z) {

194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

214:     function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

251      function subRect(
252          LeftRightSigned x,
253          LeftRightSigned y
254:     ) internal pure returns (LeftRightSigned z) {

```
*GitHub*: [39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L39-L39), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L46-L46), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L59-L62), [78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L78-L81), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L101-L101), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L108-L108), [121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L121-L124), [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L134-L134), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L148-L151), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L171-L174), [194](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L194-L194), [214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L214-L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L232-L232), [251](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L251-L254)

```solidity
File: contracts/types/LiquidityChunk.sol

70       function createChunk(
71           int24 _tickLower,
72           int24 _tickUpper,
73           uint128 amount
74:      ) internal pure returns (LiquidityChunk) {

89       function addLiquidity(
90           LiquidityChunk self,
91           uint128 amount
92:      ) internal pure returns (LiquidityChunk) {

102      function addTickLower(
103          LiquidityChunk self,
104          int24 _tickLower
105:     ) internal pure returns (LiquidityChunk) {

118      function addTickUpper(
119          LiquidityChunk self,
120          int24 _tickUpper
121:     ) internal pure returns (LiquidityChunk) {

135      function updateTickLower(
136          LiquidityChunk self,
137          int24 _tickLower
138:     ) internal pure returns (LiquidityChunk) {

151      function updateTickUpper(
152          LiquidityChunk self,
153          int24 _tickUpper
154:     ) internal pure returns (LiquidityChunk) {

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```
*GitHub*: [70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L70-L74), [89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L89-L92), [102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L102-L105), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L118-L121), [135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L135-L138), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L151-L154), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L171-L171), [180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L180-L180), [189](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L189-L189)

```solidity
File: contracts/types/TokenId.sol

87:      function poolId(TokenId self) internal pure returns (uint64) {

96:      function tickSpacing(TokenId self) internal pure returns (int24) {

118:     function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {

128:     function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {

138:     function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {

148:     function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {

158:     function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

221      function addOptionRatio(
222          TokenId self,
223          uint256 _optionRatio,
224          uint256 legIndex
225:     ) internal pure returns (TokenId) {

240      function addIsLong(
241          TokenId self,
242          uint256 _isLong,
243          uint256 legIndex
244:     ) internal pure returns (TokenId) {

255      function addTokenType(
256          TokenId self,
257          uint256 _tokenType,
258          uint256 legIndex
259:     ) internal pure returns (TokenId) {

273      function addRiskPartner(
274          TokenId self,
275          uint256 _riskPartner,
276          uint256 legIndex
277:     ) internal pure returns (TokenId) {

291      function addStrike(
292          TokenId self,
293          int24 _strike,
294          uint256 legIndex
295:     ) internal pure returns (TokenId) {

310      function addWidth(
311          TokenId self,
312          int24 _width,
313          uint256 legIndex
314:     ) internal pure returns (TokenId) {

336      function addLeg(
337          TokenId self,
338          uint256 legIndex,
339          uint256 _optionRatio,
340          uint256 _asset,
341          uint256 _isLong,
342          uint256 _tokenType,
343          uint256 _riskPartner,
344          int24 _strike,
345          int24 _width
346:     ) internal pure returns (TokenId tokenId) {

404:     function countLongs(TokenId self) internal pure returns (uint256) {

464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```
*GitHub*: [87](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L87-L87), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L96-L96), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L118-L118), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L128-L128), [138](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L138-L138), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L148-L148), [158](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L158-L158), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L183-L183), [193](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L193-L193), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L221-L225), [240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L240-L244), [255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L255-L259), [273](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L273-L277), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L291-L295), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L310-L314), [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L336-L346), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L404-L404), [464](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L464-L464)

</details>





### [N&#x2011;45] NatSpec: Function declarations should have `@notice` tags
`@notice` is used to explain to end users what the function does, and the compiler interprets `///` or `/**` comments (but not `//` or `/*`) as this tag if one wasn't explicitly provided

*There is one instance of this issue:*

```solidity
File: contracts/CollateralTracker.sol

178      constructor(
179          uint256 _commissionFee,
180          uint256 _sellerCollateralRatio,
181          uint256 _buyerCollateralRatio,
182          int256 _forceExerciseCost,
183          uint256 _targetPoolUtilization,
184          uint256 _saturatedPoolUtilization,
185          uint256 _ITMSpreadMultiplier
186:     ) {

```
*GitHub*: [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L178-L186)



### [N&#x2011;46] NatSpec: Function declarations should have descriptions


*There is one instance of this issue:*

```solidity
File: contracts/CollateralTracker.sol

178      constructor(
179          uint256 _commissionFee,
180          uint256 _sellerCollateralRatio,
181          uint256 _buyerCollateralRatio,
182          int256 _forceExerciseCost,
183          uint256 _targetPoolUtilization,
184          uint256 _saturatedPoolUtilization,
185          uint256 _ITMSpreadMultiplier
186:     ) {

```
*GitHub*: [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L178-L186)



### [N&#x2011;47] NatSpec: Modifier declarations should have `@dev` tags
`@dev` is used to explain extra details to developers

*There is one instance of this issue:*

```solidity
File: contracts/CollateralTracker.sol

168      /// @notice Ensure that the associated Panoptic pool is the caller. Revert if not.
169      modifier onlyPanopticPool() {
170          if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();
171          _;
172:     }

```
*GitHub*: [168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L168-L172)



### [N&#x2011;48] NatSpec: Non-public state variable declarations should use `@dev` tags
i.e. `@dev` [tags](https://docs.soliditylang.org/en/latest/natspec-format.html#tags). Note that since they're non-public, `@notice` is not the right tag to use.

*There are 52 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

70:      string internal constant TICKER_PREFIX = "po";

73:      string internal constant NAME_PREFIX = "POPT-V1";

96:      address internal s_univ3token0;

99:      address internal s_univ3token1;

102:     bool internal s_underlyingIsToken0;

136:     uint256 immutable COMMISSION_FEE;

141:     uint256 immutable SELLER_COLLATERAL_RATIO;

145:     uint256 immutable BUYER_COLLATERAL_RATIO;

149:     int256 immutable FORCE_EXERCISE_COST;

154:     uint256 immutable TARGET_POOL_UTIL;

158:     uint256 immutable SATURATED_POOL_UTIL;

162:     uint256 immutable ITM_SPREAD_MULTIPLIER;

```
*GitHub*: [70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L70-L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L73-L73), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L96-L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L99-L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L102-L102), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L136-L136), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L141-L141), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L145-L145), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L149-L149), [154](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L154-L154), [158](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L158-L158), [162](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L162-L162)

```solidity
File: contracts/PanopticFactory.sol

63:      IUniswapV3Factory internal immutable UNIV3_FACTORY;

66:      SemiFungiblePositionManager internal immutable SFPM;

69:      IDonorNFT internal immutable DONOR_NFT;

72:      address internal immutable POOL_REFERENCE;

75:      address internal immutable COLLATERAL_REFERENCE;

78:      address internal immutable WETH;

89:      uint16 internal constant CARDINALITY_INCREASE = 100;

96:      address internal s_owner;

99:      bool internal s_initialized;

102:     mapping(IUniswapV3Pool univ3pool => PanopticPool panopticPool) internal s_getPanopticPool;

```
*GitHub*: [63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L63-L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L66-L66), [69](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L69-L69), [72](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L72-L72), [75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L75-L75), [78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L78-L78), [89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L89-L89), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L96-L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L99-L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L102-L102)

```solidity
File: contracts/PanopticPool.sol

120:     bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

133:     bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;

136:     uint256 internal constant MEDIAN_PERIOD = 60;

156:     int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;

160:     int256 internal constant MAX_SLOW_FAST_DELTA = 1800;

171:     uint256 internal constant BP_DECREASE_BUFFER = 13_333;

174:     uint256 internal constant NO_BUFFER = 10_000;

179:     SemiFungiblePositionManager internal immutable SFPM;

```
*GitHub*: [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L120-L120), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L133-L133), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L136-L136), [156](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L156-L156), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L160-L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L171-L171), [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L174-L174), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L179-L179)

```solidity
File: contracts/SemiFungiblePositionManager.sol

126:     bool internal constant BURN = true;

133:     uint128 private constant VEGOID = 2;

287:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

```
*GitHub*: [126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L126-L126), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L133-L133), [287](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L287-L287), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L289-L289)

```solidity
File: contracts/libraries/Constants.sol

9:       uint256 internal constant FP96 = 0x1000000000000000000000000;

12:      int24 internal constant MIN_V3POOL_TICK = -887272;

15:      int24 internal constant MAX_V3POOL_TICK = 887272;

18:      uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

21       uint160 internal constant MAX_V3POOL_SQRT_RATIO =
22:          1461446703485210103287273052203988822378723970342;

```
*GitHub*: [9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L9-L9), [12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L12-L12), [15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L15-L15), [18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L18-L18), [21](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L21-L22)

```solidity
File: contracts/libraries/Math.sol

15:      uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*GitHub*: [15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L15-L15)

```solidity
File: contracts/libraries/PanopticMath.sol

23:      uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

26:      uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

```
*GitHub*: [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L23-L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L26-L26)

```solidity
File: contracts/types/LeftRight.sol

22       uint256 internal constant LEFT_HALF_BIT_MASK =
23:          0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000;

26       int256 internal constant LEFT_HALF_BIT_MASK_INT =
27:          int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

30:      int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```
*GitHub*: [22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L22-L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L26-L27), [30](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L30-L30)

```solidity
File: contracts/types/LiquidityChunk.sol

54       uint256 internal constant CLEAR_TL_MASK =
55:          0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

58       uint256 internal constant CLEAR_TU_MASK =
59:          0xFFFFFF000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```
*GitHub*: [54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L54-L55), [58](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L58-L59)

```solidity
File: contracts/types/TokenId.sol

62       uint256 internal constant LONG_MASK =
63:          0x100_000000000100_000000000100_000000000100_0000000000000000;

66       uint256 internal constant CLEAR_POOLID_MASK =
67:          0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF_0000000000000000;

70       uint256 internal constant OPTION_RATIO_MASK =
71:          0x0000000000FE_0000000000FE_0000000000FE_0000000000FE_0000000000000000;

74       uint256 internal constant CHUNK_MASK =
75:          0xFFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_0000000000000000;

78:      int256 internal constant BITMASK_INT24 = 0xFFFFFF;

```
*GitHub*: [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L62-L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L66-L67), [70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L70-L71), [74](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L74-L75), [78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L78-L78)

</details>





### [N&#x2011;49] NatSpec: State variable declarations should have descriptions
e.g. `@notice` [tags](https://docs.soliditylang.org/en/latest/natspec-format.html#tags)

*There are 9 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

120:     bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

133:     bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;

136:     uint256 internal constant MEDIAN_PERIOD = 60;

156:     int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;

171:     uint256 internal constant BP_DECREASE_BUFFER = 13_333;

174:     uint256 internal constant NO_BUFFER = 10_000;

```
*GitHub*: [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L120-L120), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L133-L133), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L136-L136), [156](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L156-L156), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L171-L171), [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L174-L174)

```solidity
File: contracts/SemiFungiblePositionManager.sol

126:     bool internal constant BURN = true;

133:     uint128 private constant VEGOID = 2;

289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

```
*GitHub*: [126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L126-L126), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L133-L133), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L289-L289)



### [N&#x2011;50] NatSpec: Use `@inheritdoc` rather than using a non-standard tags


*There are 2 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

319      /// @dev See {IERC20-transfer}.
320      /// Requirements:
321      /// - the caller must have a balance of at least 'amount'.
322      /// - the msg.sender must not have any position on the panoptic pool
323      function transfer(
324          address recipient,
325          uint256 amount
326:     ) public override(ERC20Minimal) returns (bool) {

336      /// @dev See {IERC20-transferFrom}.
337      /// Requirements:
338      /// - the 'from' must have a balance of at least 'amount'.
339      /// - the caller must have allowance for 'from' of at least 'amount' tokens.
340      /// - 'from' must not have any open positions on the panoptic pool.
341      function transferFrom(
342          address from,
343          address to,
344          uint256 amount
345:     ) public override(ERC20Minimal) returns (bool) {

```
*GitHub*: [319](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L319-L326), [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L336-L345)



### [N&#x2011;51] Non-library/interface files should use fixed compiler versions, not floating ones
Note that some file names may indicate an interface, but actually contain abstract contracts

*There are 7 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L2-L2)

```solidity
File: contracts/PanopticFactory.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L2-L2)

```solidity
File: contracts/PanopticPool.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L2-L2)

```solidity
File: contracts/SemiFungiblePositionManager.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L2-L2)

```solidity
File: contracts/multicall/Multicall.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L2-L2)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

2:   pragma solidity ^0.8.0;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L2-L2)

```solidity
File: contracts/tokens/ERC20Minimal.sol

2:   pragma solidity ^0.8.0;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L2-L2)

</details>





### [N&#x2011;52] Not using the named return variables anywhere in the function is confusing
Consider changing the variable to be an unnamed one, since the variable is never assigned, nor is it returned by name. If the optimizer is not turned on, leaving the code as it is will also waste gas for the stack variable.

*There are 18 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

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
751      function _sellCollateralRatio(
752          int256 utilization
753:     ) internal view returns (uint256 sellCollateralRatio) {

/// @audit buyCollateralRatio
806      function _buyCollateralRatio(
807          uint256 utilization
808      ) internal view returns (uint256 buyCollateralRatio) {
809          // linear from BUY to BUY/2 between 50% and 90%
810          // the buy ratio is on a straight line defined between two points (x0,y0) and (x1,y1):
811          //   (x0,y0) = (targetPoolUtilization,buyCollateralRatio) and
812          //   (x1,y1) = (saturatedPoolUtilization,buyCollateralRatio / 2)
813          // note that y1<y0 so the slope is negative:
814:         // aka the buy ratio starts high and drops to a lower value with increased utilization; the sell ratio does the opposite (slope is positive)

/// @audit required
1278     function _getRequiredCollateralSingleLeg(
1279         TokenId tokenId,
1280         uint256 index,
1281         uint128 positionSize,
1282         int24 atTick,
1283         uint128 poolUtilization
1284:    ) internal view returns (uint256 required) {

```
*GitHub*: [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L361-L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L370-L370), [379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L379-L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L386-L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L392-L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L444-L444), [507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L507-L507), [518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L518-L518), [572](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L572-L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L581-L581), [741](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L741-L741), [751](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L751-L753), [806](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L806-L814), [1278](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1278-L1284)

```solidity
File: contracts/PanopticPool.sol

/// @audit premium1
/// @audit premium0
381      function calculateAccumulatedFeesBatch(
382          address user,
383          bool includePendingPremium,
384          TokenId[] calldata positionIdList
385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

/// @audit collateralToken
1431:    function collateralToken0() external view returns (CollateralTracker collateralToken) {

```
*GitHub*: [381](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L381-L385), [381](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L381-L385), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1431-L1431)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit UniswapV3Pool
1555     function getUniswapV3PoolFromId(
1556         uint64 poolId
1557:    ) external view returns (IUniswapV3Pool UniswapV3Pool) {

```
*GitHub*: [1555](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1555-L1557)



### [N&#x2011;53] Numeric values having to do with time should use time units for readability
There are [units](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#time-units) for seconds, minutes, hours, days, and weeks, and since they're defined, they should be used

*There are 3 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit 600
128:     uint32 internal constant TWAP_WINDOW = 600;

/// @audit 60
136:     uint256 internal constant MEDIAN_PERIOD = 60;

/// @audit 1800
160:     int256 internal constant MAX_SLOW_FAST_DELTA = 1800;

```
*GitHub*: [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L128-L128), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L136-L136), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L160-L160)



### [N&#x2011;54] Overflows in unchecked blocks
While integers with a large number of bits are unlikely to overflow on human time scales, it is not strictly correct to use an `unchecked` block around them, because _eventually_ they will overflow, and `unchecked` blocks are meant for cases where it's mathematically impossible for an operation to trigger an overflow (e.g. a prior `require()` statement prevents the overflow case)

*There are 3 instances of this issue:*

```solidity
File: contracts/libraries/Math.sol

449:                 result++;

589:                 result++;

666:                 result++;

```
*GitHub*: [449](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L449-L449), [589](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L589-L589), [666](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L666-L666)



### [N&#x2011;55] Style guide: Extraneous whitespace
See the [whitespace](https://docs.soliditylang.org/en/v0.8.16/style-guide.html#whitespace-in-expressions) section of the Solidity Style Guide

*There are 18 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

1206          // (a potentially newly minted position)
1207          uint256 totalIterations = positionBalanceArray.length;
1208:         for (uint256 i = 0; i < totalIterations; ) {

```
*GitHub*: [1206](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1206-L1208)

```solidity
File: contracts/PanopticFactory.sol

297           // Runs until 'bestSalt' reaches 'minTargetRarity' or for 'loops', whichever comes first
298           uint256 maxSalt;
299           unchecked {
300               maxSalt = uint256(salt) + loops;
301           }
302   
303:          for (; uint256(salt) < maxSalt; ) {

```
*GitHub*: [297](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L297-L303)

```solidity
File: contracts/PanopticPool.sol

1206:             (LeftRightSigned positionPremia, ) = _calculateAccumulatedPremia(

440           // loop through each option position/tokenId
441           for (uint256 k = 0; k < pLength; ) {
442               TokenId tokenId = positionIdList[k];
443   
444               balances[k][0] = TokenId.unwrap(tokenId);
445               balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);
446   
447               (
448                   LeftRightSigned[4] memory premiaByLeg,
449                   uint256[2][4] memory premiumAccumulatorsByLeg
450               ) = _getPremia(
451                       tokenId,
452                       LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
453                       c_user,
454                       computeAllPremia,
455                       atTick
456                   );
457   
458               uint256 numLegs = tokenId.countLegs();
459:              for (uint256 leg = 0; leg < numLegs; ) {

744           // compute upper and lower tick and liquidity
745:          for (uint256 leg = 0; leg < numLegs; ) {

793       /// @param positionIdList the option position to liquidate.
794       function _burnAllOptionsFrom(
795           address owner,
796           int24 tickLimitLow,
797           int24 tickLimitHigh,
798           bool commitLongSettled,
799           TokenId[] calldata positionIdList
800       ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {
801           premiasByLeg = new LeftRightSigned[4][](positionIdList.length);
802:          for (uint256 i = 0; i < positionIdList.length; ) {

860           // reset balances and delete stored option data
861           s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
862   
863           uint256 numLegs = tokenId.countLegs();
864:          for (uint256 leg = 0; leg < numLegs; ) {

1379          // Check that position hash (the fingerprint of option positions) matches the one stored for the '_account'
1380          uint256 fingerprintIncomingList;
1381  
1382:         for (uint256 i = 0; i < pLength; ) {

1502      /// up to current block. atTick = type(int24).max will only consider fees as of the last on-chain transaction.
1503      function _getPremia(
1504          TokenId tokenId,
1505          uint128 positionSize,
1506          address owner,
1507          bool computeAllPremia,
1508          int24 atTick
1509      )
1510          internal
1511          view
1512          returns (
1513              LeftRightSigned[4] memory premiaByLeg,
1514              uint256[2][4] memory premiumAccumulatorsByLeg
1515          )
1516      {
1517          uint256 numLegs = tokenId.countLegs();
1518:         for (uint256 leg = 0; leg < numLegs; ) {

1843          // compute accumulated fees
1844          (premiaByLeg, premiumAccumulatorsByLeg) = _getPremia(
1845              tokenId,
1846              positionSize,
1847              owner,
1848              COMPUTE_ALL_PREMIA,
1849              type(int24).max
1850          );
1851  
1852:         for (uint256 leg = 0; leg < numLegs; ) {

```
*GitHub*: [1206](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1206), [440](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L440-L459), [744](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L744-L745), [793](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L793-L802), [860](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L860-L864), [1379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1379-L1382), [1502](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1502-L1518), [1843](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1843-L1852)

```solidity
File: contracts/SemiFungiblePositionManager.sol

574           // so just check if there is an active reentrancy lock for the relevant pool on each token
575:          for (uint256 i = 0; i < ids.length; ) {

597           // Extract univ3pool from the poolId map to Uniswap Pool
598           IUniswapV3Pool univ3pool = s_poolContext[id.poolId()].pool;
599   
600           uint256 numLegs = id.countLegs();
601:          for (uint256 leg = 0; leg < numLegs; ) {

881           // loop through up to the 4 potential legs in the tokenId
882:          for (uint256 leg = 0; leg < numLegs; ) {

```
*GitHub*: [574](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L574-L575), [597](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L597-L601), [881](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L881-L882)

```solidity
File: contracts/libraries/FeesCalc.sol

45        /// @return value1 The amount of token1 owned by portfolio
46        function getPortfolioValue(
47            int24 atTick,
48            mapping(TokenId tokenId => LeftRightUnsigned balance) storage userBalance,
49            TokenId[] calldata positionIdList
50        ) external view returns (int256 value0, int256 value1) {
51            for (uint256 k = 0; k < positionIdList.length; ) {
52                TokenId tokenId = positionIdList[k];
53                uint128 positionSize = userBalance[tokenId].rightSlot();
54                uint256 numLegs = tokenId.countLegs();
55:               for (uint256 leg = 0; leg < numLegs; ) {

```
*GitHub*: [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L45-L55)

```solidity
File: contracts/libraries/PanopticMath.sol

253:              (int56[] memory tickCumulatives, ) = univ3pool.observe(secondsAgos);

389       /// @return shortAmounts Left-right packed word where the right contains the total contract size and the left total notional
390       function computeExercisedAmounts(
391           TokenId tokenId,
392           uint128 positionSize
393       ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {
394           uint256 numLegs = tokenId.countLegs();
395:          for (uint256 leg = 0; leg < numLegs; ) {

```
*GitHub*: [253](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L253), [389](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L389-L395)

```solidity
File: contracts/multicall/Multicall.sol

11        /// @return results The data returned by each call
12        function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
13            results = new bytes[](data.length);
14:           for (uint256 i = 0; i < data.length; ) {

```
*GitHub*: [11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L11-L14)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

139           // Storing these outside the loop saves ~15 gas per iteration.
140           uint256 id;
141           uint256 amount;
142   
143:          for (uint256 i = 0; i < ids.length; ) {

```
*GitHub*: [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L139-L143)

</details>





### [N&#x2011;56] Style guide: Lines are too long
Usually lines in source code are limited to [80](https://softwareengineering.stackexchange.com/questions/148677/why-is-80-characters-the-standard-limit-for-code-width) characters. Today's screens are much larger so it's reasonable to stretch this in some cases. The solidity style guide recommends a maximumum line length of [120 characters](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#maximum-line-length), so the lines below should be split when they reach that length.

*There are 334 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/PanopticFactory.sol

101:      /// @notice Mapping from address(UniswapV3Pool) to address(PanopticPool) that stores the address of all deployed Panoptic Pools

201:      /// @notice Create a new Panoptic Pool linked to the given Uniswap pool identified uniquely by the incoming parameters.

256:          // If this is not the case, we increase the next cardinality during deployment so the cardinality can catch up over time

285:      /// @param salt Salt value ([160-bit deployer address][96-bit nonce]) to start from, useful as a checkpoint across multiple calls

287:      /// @param minTargetRarity The minimum target rarity to mine for. The internal loop stops when this is reached *or* when no more iterations

347:          // In this case, the `fullRangeLiquidity` will always be an underestimate in respect to the token amounts required to mint.

```
*GitHub*: [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L101), [201](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L201), [256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L256), [285](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L285), [287](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L287), [347](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L347)

```solidity
File: contracts/PanopticPool.sol

36:       /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.

61:       /// @param settledAmounts LeftRight encoding for the amount of premium settled for token0 (right slot) and token1 (left slot).

87:       /// @param poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),

89:       /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.

113:      /// @dev Only include the share of (settled) premium that is available to collect when calling `_calculateAccumulatedPremia`

131:      // This oracle is updated with the last Uniswap observation during `mintOptions` if MEDIAN_PERIOD has elapsed past the last observation

132:      // If true, the "slow" oracle price is instead computed on-the-fly from 7 Uniswap observations (spaced 5 observations apart) irrespective of the frequency of `mintOptions` calls

142:      /// Note that the *minimum* total observation time is determined by the blocktime and may need to be adjusted by chain

144:      /// In this case, if there is an interaction every block, the "fast" oracle can consider 3 consecutive block end prices (min=36 seconds on Ethereum)

151:      /// @dev Structured such that the minimum total observation time is 7 minutes on Ethereum (similar to internal median mode)

154:      // The maximum allowed delta between the currentTick and the Uniswap TWAP tick during a liquidation (~5% down, ~5.26% up)

159:      /// Falls back on the more conservative (less solvent) tick during times of extreme volatility (to ensure the account is always solvent)

170:      // multiplier (x10k) for the collateral requirement in the event of a buying power decrease, such as minting or force exercising

237:      // collected for every chunk per unit of liquidity (net or short, depending on the isLong value of the specific leg index)

241:      /// @dev Per-chunk `last` value that gives the aggregate amount of premium owed to all sellers when multiplied by the total amount of liquidity `totalLiquidity`

253:      /// @dev Tracks the amount of liquidity for a user+tokenId (right slot) and the initial pool utilizations when that position was minted (left slot)

267:      /// The accumulator also tracks the total number of positions (ie. makes sure the length of the provided positionIdList matches);

270:      /// this hash can be cheaply verified on every operation with a user provided positionIdList - and we can use that for operations

278:      /// @notice During construction: sets the address of the panoptic factory smart contract and the SemiFungiblePositionMananger (SFPM).

310:                  // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2

368:          // the 64 most significant bits are the utilization of token1, so we can shift the number to the right by 64 to extract it

377:      /// @param includePendingPremium true = include premium that is owed to the user but has not yet settled, false = only include premium that is available to collect.

380:      /// @return balances A list of balances and pool utilization for each position, of the form [[tokenId0, balances0], [tokenId1, balances1], ...].

425:      /// @param computeAllPremia Whether to compute accumulated premia for all legs held by the user (true), or just owed premia for long legs (false).

426:      /// @param includePendingPremium true = include premium that is owed to the user but has not yet settled, false = only include premium that is available to collect.

427:      /// @return portfolioPremium The computed premia of the user's positions, where premia contains the accumulated premia for token0 in the right slot and for token1 in the left slot.

428:      /// @return balances A list of balances and pool utilization for each position, of the form [[tokenId0, balances0], [tokenId1, balances1], ...].

494:      /// @notice Disable slippage checks if tickLimitLow == tickLimitHigh and reverses ticks if given in correct order to enable ITM swaps

541:      /// @param positionIdList the list of currently held positions by the user, where the newly minted position(token) will be the last element in 'positionIdList'.

543:      /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position.

608:      /// @param positionIdList the list of currently held positions by the user, where the newly minted position(token) will be the last element in 'positionIdList'.

610:      /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position.

660:          // Add an initial buffer to the collateral requirement to prevent users from minting their account close to insolvency

663:          // Update `s_miniMedian` with a new observation if the last observation is old enough (returned medianData is nonzero)

675:      /// @return poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool) at the time of minting,

703:      /// @return poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),

705:      /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.

737:      /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position

881:      /// @notice Falls back to the more conservative tick if the delta between the fast and slow oracle exceeds `MAX_SLOW_FAST_DELTA`.

882:      /// @dev Effectively, this means that the users must be solvent at both the fast and slow oracle ticks if one of them is stale to mint or burn options.

886:      /// @return medianData If nonzero (enough time has passed since last observation), the updated value for `s_miniMedian` with a new observation

942:          // If one of the ticks is too stale, we fall back to the more conservative tick, i.e, the user must be solvent at both the fast and slow oracle ticks.

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
*GitHub*: [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L36), [61](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L61), [87](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L87), [89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L89), [113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L113), [131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L131), [132](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L132), [142](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L142), [144](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L144), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L151), [154](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L154), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L159), [170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L170), [237](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L237), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L241), [253](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L253), [267](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L267), [270](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L270), [278](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L278), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L310), [368](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L368), [377](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L377), [380](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L380), [425](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L425), [426](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L426), [427](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L427), [428](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L428), [494](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L494), [541](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L541), [543](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L543), [608](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L608), [610](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L610), [660](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L660), [663](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L663), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L675), [703](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L703), [705](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L705), [737](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L737), [881](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L881), [882](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L882), [886](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L886), [942](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L942), [1012](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1012), [1015](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1015), [1070](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1070), [1083](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1083), [1084](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1084), [1112](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1112), [1113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1113), [1115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1115), [1187](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1187), [1190](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1190), [1284](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1284), [1334](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1334), [1335](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1335), [1350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1350), [1363](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1363), [1366](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1366), [1378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1378), [1397](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1397), [1400](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1400), [1401](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1401), [1404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1404), [1463](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1463), [1491](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1491), [1500](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1500), [1542](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1542), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1544), [1582](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1582), [1584](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1584), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1638), [1649](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1649), [1657](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1657), [1676](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1676), [1690](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1690), [1753](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1753)

```solidity
File: contracts/SemiFungiblePositionManager.sol

24:   //                       ,.                                   .,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.                                    ,,

25:   //                    ,,,,,,,                           ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                            ,,,,,,

26:   //                  .,,,,,,,,,,.                   ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                     ,,,,,,,,,,,

27:   //                .,,,,,,,,,,,,,,,             ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.              ,,,,,,,,,,,,,,,

28:   //               ,,,,,,,,,,,,,,.            ,,,,,,,,,,,,,,,,,,,,,,,,,,,                ,,,,,,,,,,,,,,,,,,,,,,,,,,.             ,,,,,,,,,,,,,,,

29:   //             ,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,,,,,,                                ,,,,,,,,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,,

30:   //            ,,,,,,,,,,,,,.           ,,,,,,,,,,,,,,,,,,                                           .,,,,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,

31:   //          ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,,,.                                                  ,,,,,,,,,,,,,,,,,           .,,,,,,,,,,,,,

32:   //         ,,,,,,,,,,,,,.         .,,,,,,,,,,,,,,,.                                                        ,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,.

33:   //        ,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,                                                              ,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

34:   //       ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,.                                                                  ,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

35:   //      ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,                                                                      ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,

36:   //     ,,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                         ,,,,,,,,,,,,,,          ,,,,,,,,,,,,.

37:   //    .,,,,,,,,,,,,        .,,,,,,,,,,,,,                                                                            ,,,,,,,,,,,,,          ,,,,,,,,,,,,

38:   //    ,,,,,,,,,,,,         ,,,,,,,,,,,,                                                                               ,,,,,,,,,,,,,         .,,,,,,,,,,,,

39:   //   ,,,,,,,,,,,,         ,,,,,,,,,,,,                                                                                 ,,,,,,,,,,,,.         ,,,,,,,,,,,,

40:   //   ,,,,,,,,,,,,        ,,,,,,,,,,,,.                █████████  ███████████ ███████████  ██████   ██████               ,,,,,,,,,,,,          ,,,,,,,,,,,,

41:   //  .,,,,,,,,,,,,        ,,,,,,,,,,,,                ███░░░░░███░░███░░░░░░█░░███░░░░░███░░██████ ██████                .,,,,,,,,,,,,         ,,,,,,,,,,,,

42:   //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░███    ░░░  ░███   █ ░  ░███    ░███ ░███░█████░███                 ,,,,,,,,,,,,         ,,,,,,,,,,,,.

43:   //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░░█████████  ░███████    ░██████████  ░███░░███ ░███                 .,,,,,,,,,,,          ,,,,,,,,,,,.

44:   //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ░░░░░░░░███ ░███░░░█    ░███░░░░░░   ░███ ░░░  ░███                  ,,,,,,,,,,,.         ,,,,,,,,,,,,

45:   //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ███    ░███ ░███  ░     ░███         ░███      ░███                  ,,,,,,,,,,,,         ,,,,,,,,,,,,

46:   //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░░█████████  █████       █████        █████     █████                 ,,,,,,,,,,,          ,,,,,,,,,,,,

47:   //  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ░░░░░░░░░  ░░░░░       ░░░░░        ░░░░░     ░░░░░                 ,,,,,,,,,,,,          ,,,,,,,,,,,.

48:   //  ,,,,,,,,,,,,        .,,,,,,,,,,,.                                                                                    ,,,,,,,,,,,,         ,,,,,,,,,,,,

49:   //  .,,,,,,,,,,,,        ,,,,,,,,,,,,                                                                                   .,,,,,,,,,,,,         ,,,,,,,,,,,,

50:   //   ,,,,,,,,,,,,        ,,,,,,,,,,,,,                                                                                  ,,,,,,,,,,,,          ,,,,,,,,,,,,

51:   //   ,,,,,,,,,,,,.        ,,,,,,,,,,,,.                                                                                ,,,,,,,,,,,,.         ,,,,,,,,,,,,

52:   //    ,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                              ,,,,,,,,,,,,,         .,,,,,,,,,,,,

53:   //     ,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                            ,,,,,,,,,,,,,         .,,,,,,,,,,,,

54:   //     .,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                         ,,,,,,,,,,,,,.          ,,,,,,,,,,,,

55:   //      ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,                                                                     .,,,,,,,,,,,,,.          ,,,,,,,,,,,,

56:   //       ,,,,,,,,,,,,,         .,,,,,,,,,,,,,,                                                                 .,,,,,,,,,,,,,,          .,,,,,,,,,,,,

57:   //        ,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,                                                             ,,,,,,,,,,,,,,,.          ,,,,,,,,,,,,,.

58:   //         ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,,                                                       .,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

59:   //          .,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,                                                 .,,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,

60:   //            ,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,,,.                                        ,,,,,,,,,,,,,,,,,,,.            ,,,,,,,,,,,,,,

61:   //             ,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,,,,,,,,,                             .,,,,,,,,,,,,,,,,,,,,,,             ,,,,,,,,,,,,,,

62:   //               ,,,,,,,,,,,,,,,            .,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.        ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,             .,,,,,,,,,,,,,,.

63:   //                 ,,,,,,,,,,,,,,.              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,               ,,,,,,,,,,,,,,,

64:   //                   ,,,,,,,,,,                     ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                     .,,,,,,,,,,

65:   //                     ,,,,,.                            ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                             ,,,,,,

129:      // Similar to vega in options because the liquidity utilization is somewhat reflective of the implied volatility (IV),

132:      // The effect of vegoid on the long premium multiplier can be explored here: https://www.desmos.com/calculator/mdeqob2m04

173:      /// @dev mapping that stores the liquidity data of keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))

174:      // liquidityData is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user

175:      // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller

176:      // the reason why it is called "removedLiquidity" is because long options are created by removed liquidity -ie. short selling LP positions

219:          For an arbitrary parameter 0 <= ν <= 1 (ν = 1/2^VEGOID). This way, the gross_feesCollectedX128 will be given by: 

291:      /// @dev mapping that stores a LeftRight packing of feesBase of  keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))

292:      /// @dev Base fees is stored as int128((feeGrowthInside0LastX128 * liquidity) / 2**128), which allows us to store the accumulated fees as int128 instead of uint256

294:      /// feesBase represents the baseline fees collected by the position last time it was updated - this is recalculated every time the position is collected from with the new value

378:          // note: we preserve the state of `locked` to prevent reentering a pool by initializing it during the reentrant call

467:      /// @param slippageTickLimitLow The lower price slippage limit when minting an ITM position (set to larger than slippageTickLimitHigh for swapping when minting)

468:      /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)

469:      /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

470:      /// @return totalSwapped A LeftRight encoded word containing the total amount of token0 and token1 swapped if minting ITM

500:      /// @param slippageTickLimitLow The lower price slippage limit when minting an ITM position (set to larger than slippageTickLimitHigh for swapping when minting)

501:      /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)

502:      /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

503:      /// @return totalSwapped A LeftRight encoded word containing the total amount of token0 and token1 swapped if minting ITM

547:          // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call

554:          // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)

573:          // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call

588:      /// @dev token transfers are only allowed if you transfer your entire liquidity of a given chunk and the recipient has none

602:              // for this leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick

659:      /// @notice Helper that checks the proposed option position and size and forwards the minting and potential swapping tasks.

664:      /// @notice and then forwards the minting/burning/swapping to another internal helper functions which perform the AMM pool actions.

678:      /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

716:              // if the in-the-money amount is not zero (i.e. positions were minted ITM) and the user did provide tick limits LOW > HIGH, then swap necessary amounts

731:      /// @notice When a position is minted or burnt in-the-money (ITM) we are *not* 100% token0 or 100% token1: we have a mix of both tokens.

732:      /// @notice The swapping for ITM options is needed because only one of the tokens are "borrowed" by a user to create the position.

750:      ///   If we take token0 as an example, we deploy it to the AMM pool and *then* swap to get the right mix of token0 and token1

752:      ///   It that position is burnt, then we remove a mix of the two tokens and swap one of them so that the user receives only one.

784:              // note: upstream users of this function such as the Panoptic Pool should ensure users always compensate for the ITM amount delta

785:              // the netting swap is not perfectly accurate, and it is possible for swaps to run out of liquidity, so we do not want to rely on it

791:                  // note: negative ITM amounts denote a surplus of tokens (burning liquidity), while positive amounts denote a shortage of tokens (minting liquidity)

793:                  // we do this by flipping the signs on the token1 ITM amount converting+deducting it against the token0 ITM amount

861:      /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

897:                      // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,

902:                  // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick

921:                      // increment accumulators of the upper bound on tokens contained across all legs of the position at any given tick

936:          // Ensure upper bound on amount of tokens contained across all legs of the position on any given tick does not exceed a maximum of (2**127-1).

937:          // This is the maximum value of the `int128` type we frequently use to hold token amounts, so a given position's size should be guaranteed to

992:              // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user

993:              // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller

994:              // the reason why it is called "removedLiquidity" is because long options are created by removing -ie.short selling LP positions

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
*GitHub*: [24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L24), [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L25), [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L26), [27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L27), [28](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L28), [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L29), [30](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L30), [31](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L31), [32](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L34), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L35), [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L38), [39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L39), [40](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L40), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L41), [42](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L42), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L43), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L44), [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L45), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L46), [47](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L47), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L48), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L49), [50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L50), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L51), [52](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L52), [53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L53), [54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L54), [55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L55), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L56), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L57), [58](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L58), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L59), [60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L60), [61](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L61), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L62), [63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L63), [64](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L64), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L65), [129](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L129), [132](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L132), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L173), [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L174), [175](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L175), [176](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L176), [219](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L219), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L291), [292](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L292), [294](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L294), [378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L378), [467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L467), [468](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L468), [469](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L469), [470](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L470), [500](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L500), [501](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L501), [502](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L502), [503](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L503), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L547), [554](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L554), [573](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L573), [588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L588), [602](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L602), [659](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L659), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L664), [678](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L678), [716](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L716), [731](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L731), [732](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L732), [750](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L750), [752](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L752), [784](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L784), [785](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L785), [791](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L791), [793](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L793), [861](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L861), [897](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L897), [902](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L902), [921](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L921), [936](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L936), [937](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L937), [992](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L992), [993](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L993), [994](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L994), [1001](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1001), [1011](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1011), [1121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1121), [1122](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1122), [1132](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1132), [1137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1137), [1160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1160), [1161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1161), [1162](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1162), [1164](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1164), [1219](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1219), [1247](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1247), [1250](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1250), [1254](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1254), [1281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1281), [1319](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1319), [1320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1320), [1334](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1334), [1420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1420), [1429](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1429), [1435](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1435), [1436](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1436), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1437), [1438](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1438), [1445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1445), [1447](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1447), [1448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1448), [1464](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1464), [1476](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1476), [1478](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1478), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1479), [1488](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1488), [1505](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1505), [1506](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1506)

```solidity
File: contracts/libraries/CallbackLib.sol

11:   /// @notice This library provides functions to verify that a callback came from a canonical Uniswap V3 pool with a claimed set of features.

35:           // Call getPool on the factory to verify that the sender corresponds to the canonical pool with the claimed features

```
*GitHub*: [11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L11), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L35)

```solidity
File: contracts/libraries/Errors.sol

18:       /// @notice PanopticPool: the effective liquidity (X32) is greater than min(`MAX_SPREAD`, `USER_PROVIDED_THRESHOLD`) during a long mint or short burn

22:       /// @notice CollateralTracker: attempted to withdraw/redeem more than available liquidity, owned shares, or open positions would allow for

25:       /// @notice PanopticPool: force exercisee is insolvent - liquidatable accounts are not permitted to open or close positions outside of a liquidation

41:       /// @param parameterType poolId=0, ratio=1, tokenType=2, risk_partner=3 , strike=4, width=5, two identical strike/width/tokenType chunks=6

44:       /// @notice A mint or swap callback was attempted from an address that did not match the canonical Uniswap V3 pool with the claimed features

50:       /// @notice PanopticPool: one of the legs in a position are force-exercisable (they are all either short or ITM long)

```
*GitHub*: [18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L18), [22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L22), [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L25), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L41), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L44), [50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L50)

```solidity
File: contracts/libraries/FeesCalc.sol

17:   /// @dev Some options positions involve moving liquidity chunks to the AMM/Uniswap. Those chunks can then earn AMM swap fees.

96:       /// @return The fees collected from the AMM for each token (LeftRight-packed) with token0 in the right slot and token1 in the left slot

137:          // lowerOut0: For token0: fee growth per unit of liquidity on the _other_ side of tickLower (relative to currentTick)

```
*GitHub*: [17](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L17), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L96), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L137)

```solidity
File: contracts/libraries/InteractionHelper.sol

18:       /// @notice Function that performs approvals on behalf of the PanopticPool for CollateralTracker and SemiFungiblePositionManager.

40:       /// @notice Computes the name of a CollateralTracker based on the token composition and fee of the underlying Uniswap Pool.

41:       /// @dev Some tokens do not have proper symbols so error handling is required - this logic takes up significant bytecode size, which is why it is in a library.

```
*GitHub*: [18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L18), [40](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L40), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L41)

```solidity
File: contracts/libraries/Math.sol

124:      /// @dev Implemented using Uniswap's "incorrect" constants. Supplying commented-out real values for an accurate calculation.

216:      /// @notice Calculates the amount of token0 and token1 received for a given LiquidityChunk at the provided currentTick.

334:      /// @notice Calculates floor(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0.

435:      /// @notice Calculates ceil(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0.

502:              // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

565:              // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

642:              // Divide [prod1 prod0] by the factors of two (note that this is just 2**128 since the denominator is a power of 2 itself)

719:              // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

748:      /// @notice QuickSort is a sorting algorithm that employs the Divide and Conquer strategy. It selects a pivot element and arranges the given array around

```
*GitHub*: [124](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L124), [216](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L216), [334](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L334), [435](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L435), [502](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L502), [565](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L565), [642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L642), [719](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L719), [748](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L748)

```solidity
File: contracts/libraries/PanopticMath.sol

34:       ///      the 64 bits are the 48 *last* (most significant) bits - and thus corresponds to the *first* 12 hex characters (reading left to right)

35:       ///      of the Uniswap v3 pool address, with the tickSpacing written in the highest 16 bits (i.e, max tickSpacing is 32768)

86:       /// @notice The positions hash contains a single fingerprint of all positions created by an account/user as well as a tally of the positions.

88:       /// @param existingHash The existing position hash containing all historical N positions created and the count of the positions

89:       /// @param tokenId The new position to add to the existing hash: existingHash = uint248(existingHash) ^ hashOf(tokenId)

90:       /// @param addFlag Whether to mint (add) the tokenId to the count of positions or burn (subtract) it from the count (existingHash >> 248) +/- 1

114:      /// @dev Uniswap observations snapshot the closing price of the last block before the first interaction of a given block.

115:      /// @dev The maximum frequency of observations is 1 per block, but there is no guarantee that the pool will be observed at every block.

116:      /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.

117:      /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).

136:              // get the last 4 timestamps/tickCumulatives (if observationIndex < cardinality, the index will wrap back from observationCardinality)

147:              // use cardinality periods given by cardinality + 1 accumulator observations to compute the last cardinality observed ticks spaced by period

159:      /// @notice Takes a packed structure representing a sorted 7-slot ring buffer of ticks and returns the median of those values.

160:      /// @dev Also inserts the latest Uniswap observation into the buffer, resorts, and returns if the last entry is at least `period` seconds old.

163:      /// @param period The minimum time in seconds that must have passed since the last observation was inserted into the buffer

167:      /// @return updatedMedianData The updated 7-slot ring buffer of ticks with the latest observation inserted if the last entry is at least `period` seconds old (returns 0 otherwise)

237:      /// @dev We instead observe the average price over a series of time intervals, and define the TWAP as the median of those averages.

274:      /// @notice For a given option position (`tokenId`), leg index within that position (`legIndex`), and `positionSize` get the tick range spanned and its

310:          //  Because Uni v3 chooses token0 and token1 from the alphanumeric order, there is no consistency as to whether token0 is

311:          //  stablecoin, ETH, or an ERC20. Some pools may want ETH to be the asset (e.g. ETH-DAI) and some may wish the stablecoin to

315:          //  To solve this, we encode the asset value in tokenId. This parameter specifies which of token0 or token1 is the

344:              // The max/min ticks that can be initialized are the closest multiple of tickSpacing to the actual max/min tick abs()=887272

365:      /// @notice Returns the distances of the upper and lower ticks from the strike for a position with the given width and tickSpacing.

385:      /// @notice Compute the amount of funds that are underlying this option position. This is useful when exercising a position.

388:      /// @return longAmounts Left-right packed word where the right contains the total contract size and the left total notional

389:      /// @return shortAmounts Left-right packed word where the right contains the total contract size and the left total notional

412:      /// @notice Adds required collateral and collateral balance from collateralTracker0 and collateralTracker1 and converts to single values in terms of `tokenType`.

413:      /// @param tokenData0 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token0)

414:      /// @param tokenData1 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token1)

438:      /// @notice Adds required collateral and collateral balance from collateralTracker0 and collateralTracker1 and converts to single values in terms of `tokenType`.

439:      /// @param tokenData0 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token0)

440:      /// @param tokenData1 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token1)

455:      /// @notice Compute the notional amount given an incoming total number of `contracts` deployed between `tickLower` and `tickUpper`.

456:      /// @dev The notional value of an option is the value of the crypto assets that are controlled (rather than the cost of the transaction).

461:      /// @dev Thus, `contracts` refer to "100" in this example. The $20 is the strike price. We get the strike price from `tickLower` and `tickUpper`.

462:      /// @dev From TradFi: [https://www.investopedia.com/terms/n/notionalvalue.asp](https://www.investopedia.com/terms/n/notionalvalue.asp).

485:      /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

502:      /// @notice Convert an amount of token1 into an amount of token0 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

519:      /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

542:      /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

569:      /// @notice Compute the amount of token0 and token1 moved. Given an option position `tokenId`, leg index `legIndex`, and how many contracts are in the leg `positionSize`.

571:      /// @param positionSize The number of option contracts held in this position (each contract can control multiple tokens)

573:      /// @return A LeftRight encoded variable containing the amount0 and the amount1 value controlled by this option position's leg

642:      /// @param tokenData0 Leftright encoded word with balance of token0 in the right slot, and required balance in left slot

643:      /// @param tokenData1 Leftright encoded word with balance of token1 in the right slot, and required balance in left slot

650:      /// @return The LeftRight-packed protocol loss for both tokens, i.e., the delta between the user's balance and expended tokens

692:              // this is already present in the netExchanged amount, so to avoid double-counting we remove it from the balance

701:              // note that "balance0" and "balance1" are the liquidatee's original balances before token delegation by a liquidator

702:              // their actual balances at the time of computation may be higher, but these are a buffer representing the amount of tokens we

707:                      // liquidatee has insufficient token0 but some token1 left over, so we use what they have left to mitigate token0 losses

708:                      // we do this by substituting an equivalent value of token1 in our refund to the liquidator, plus a bonus, for the token0 we convert

709:                      // we want to convert the minimum amount of tokens required to achieve the lowest possible protocol loss (to avoid overpaying on the conversion bonus)

710:                      // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token1 balance: balance1 - paid1

711:                      // and paid0 - balance0 is the amount of token0 that the liquidatee is missing, i.e the protocol loss

712:                      // if the protocol loss is lower than the excess token1 balance, then we can fully mitigate the loss and we should only convert the loss amount

713:                      // if the protocol loss is higher than the excess token1 balance, we can only mitigate part of the loss, so we should convert only the excess token1 balance

725:                      // liquidatee has insufficient token1 but some token0 left over, so we use what they have left to mitigate token1 losses

726:                      // we do this by substituting an equivalent value of token0 in our refund to the liquidator, plus a bonus, for the token1 we convert

727:                      // we want to convert the minimum amount of tokens required to achieve the lowest possible protocol loss (to avoid overpaying on the conversion bonus)

728:                      // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token0 balance: balance0 - paid0

729:                      // and paid1 - balance1 is the amount of token1 that the liquidatee is missing, i.e the protocol loss

730:                      // if the protocol loss is lower than the excess token0 balance, then we can fully mitigate the loss and we should only convert the loss amount

731:                      // if the protocol loss is higher than the excess token0 balance, we can only mitigate part of the loss, so we should convert only the excess token0 balance

756:      /// @notice Haircut/clawback any premium paid by `liquidatee` on `positionIdList` over the protocol loss threshold during a liquidation.

757:      /// @dev Note that the storage mapping provided as the `settledTokens` parameter WILL be modified on the caller by this function.

765:      /// @param settledTokens The per-chunk accumulator of settled tokens in storage from which to subtract the haircut premium

790:              // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token

795:              // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,

796:              // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token

886:                          // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount

910:      /// @notice Returns the original delegated value to a user at a certain tick based on the available collateral from the exercised user.

926:              // if the refunder lacks sufficient token0 to pay back the refundee, have them pay back the equivalent value in token1

927:              // note: it is possible for refunds to be negative when the exercise fee is higher than the delegated amounts. This is expected behavior

```
*GitHub*: [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L34), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L35), [86](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L86), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L88), [89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L89), [90](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L90), [114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L114), [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L115), [116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L116), [117](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L117), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L136), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L147), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L159), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L160), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L163), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L167), [237](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L237), [274](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L274), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L310), [311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L311), [315](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L315), [344](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L344), [365](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L365), [385](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L385), [388](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L388), [389](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L389), [412](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L412), [413](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L413), [414](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L414), [438](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L438), [439](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L439), [440](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L440), [455](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L455), [456](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L456), [461](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L461), [462](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L462), [485](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L485), [502](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L502), [519](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L519), [542](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L542), [569](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L569), [571](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L571), [573](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L573), [642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L642), [643](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L643), [650](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L650), [692](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L692), [701](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L701), [702](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L702), [707](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L707), [708](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L708), [709](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L709), [710](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L710), [711](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L711), [712](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L712), [713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L713), [725](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L725), [726](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L726), [727](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L727), [728](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L728), [729](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L729), [730](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L730), [731](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L731), [756](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L756), [757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L757), [765](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L765), [790](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L790), [795](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L795), [796](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L796), [886](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L886), [910](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L910), [926](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L926), [927](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L927)

```solidity
File: contracts/libraries/SafeTransferLib.sol

25:               // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.

56:               // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.

```
*GitHub*: [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L25), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L56)

```solidity
File: contracts/multicall/Multicall.sol

22:                   // Other solutions will do work to differentiate the revert reasons and provide paranthetical information

24:                   // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)

```
*GitHub*: [22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L22), [24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L24)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

57:       /// @notice Emitted when an attempt is made to initiate a transfer to a contract recipient that fails to signal support for ERC1155.

```
*GitHub*: [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L57)

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

8:    /// @dev However, we cannot productively handle a failed approval and such a situation would surely cause a revert later in execution.

9:    /// @dev In addition, no notable instances exist of tokens that both i) contain a failure case for `approve` and ii) return `false` instead of reverting.

```
*GitHub*: [8](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L8), [9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L9)

```solidity
File: contracts/types/LeftRight.sol

51:       // Typically, the slot is already clear when writing to it, but if it is not, the bits will be added to the existing bits

53:       // Note that the values *within* the slots are allowed to overflow, but overflows are contained and will not leak into the other slot

113:      // Typically, the slot is already clear when writing to it, but if it is not, the bits will be added to the existing bits

115:      // Note that the values *within* the slots are allowed to overflow, but overflows are contained and will not leak into the other slot

181:              // type cast z to uint128 to isolate the right slot and if it's higher than a value that was subtracted from (x)

272:      /// @dev Used for linked accumulators, so if the accumulator for one side overflows for a token, both cease to accumulate.

```
*GitHub*: [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L51), [53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L53), [113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L113), [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L115), [181](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L181), [272](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L272)

```solidity
File: contracts/types/LiquidityChunk.sol

10:   /// @title A Panoptic Liquidity Chunk. Tracks Tick Range and Liquidity Information for a "chunk." Used to track movement of chunks.

13:   /// @notice A liquidity chunk is an amount of `liquidity` (an amount of WETH, e.g.) deployed between two ticks: `tickLower` and `tickUpper`

```
*GitHub*: [10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L10), [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L13)

```solidity
File: contracts/types/TokenId.sol

24:   // (0) univ3pool        48bits     0bits      : first 6 bytes of the Uniswap v3 pool address (first 48 bits; little-endian), plus a pseudorandom number in the event of a collision

43:   //  <---- 48 bits ---->    <---- 48 bits ---->    <---- 48 bits ---->     <---- 48 bits ---->   <- 16 bits ->   <- 48 bits ->

44:   //         Leg 4                  Leg 3                  Leg 2                   Leg 1          tickSpacing    Univ3 Pool Address

46:   //  <--- most significant bit                                                                             least significant bit --->

51:   //   - if a leg is active (e.g. leg 1) there can be no gaps in other legs meaning: if leg 1 is active then leg 3 cannot be active if leg 2 is inactive.

55:   //  We also refer to the legs via their index, so leg number 2 has leg index 1 (legIndex) (counting from zero), and in general leg number N has leg index N-1.

56:   //  - the underlying strike price of the 2nd leg (leg index = 1) in this option position starts at bit index  (64 + 12 + 48 * (leg index=1))=123

73:       /// @notice AND mask to clear all bits except for the components of the chunk key (strike, width, tokenType) for each leg

86:       /// @return The `poolId` (Panoptic's pool fingerprint, contains the whole 64 bit sequence with the tickSpacing) of the Uniswap V3 pool

144:      /// @notice Get the associated risk partner of the leg index (generally another leg index in the position if enabled or the same leg index if no partner).

164:      /// @notice Get the width of the nth leg (index `legIndex`). This is half the tick-range covered by the leg (tickUpper - tickLower)/2.

369:              // We copy the logic from the countLegs function, using it here adds 5K to the contract size with IR for some reason

375:              // Since only the option ratios remain, we can be sure that no bits above the start of the inactive legs will be 1

390:              // i.e the whole mask is used to flip all legs with 4 legs, but only the first leg is flipped with 1 leg so we shift by 3 legs

391:              // We also clear the poolId area of the mask to ensure the bits that are shifted right into the area don't flip and cause issues

430:      /// @dev ASSUMPTION: For any leg, the option ratio is always > 0 (the leg always has a number of contracts associated with it).

438:          // Since only the option ratios remain, we can be sure that no bits above the start of the inactive legs will be 1

563:                      // if the two token long-types and the tokenTypes are both different (one is a short call, the other a long put, e.g.), this is a synthetic position

564:                      // A synthetic long or short is more capital efficient than each leg separated because the long+short premia accumulate proportionally

565:                      // unlike short stranlges, long strangles also cannot be partnered, because there is no reduction in risk (both legs can earn premia simultaneously)

```
*GitHub*: [24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L24), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L43), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L44), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L46), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L51), [55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L55), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L56), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L73), [86](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L86), [144](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L144), [164](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L164), [369](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L369), [375](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L375), [390](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L390), [391](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L391), [430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L430), [438](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L438), [563](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L563), [564](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L564), [565](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L565)

</details>





### [N&#x2011;57] Style guide: Local and state variables should be named using lowerCamelCase
The Solidity style guide [says](https://docs.soliditylang.org/en/latest/style-guide.html#function-argument-names) to use mixedCase for function argument names

*There are 3 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

185:         uint256 _ITMSpreadMultiplier

```
*GitHub*: [185](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L185-L185)

```solidity
File: contracts/PanopticFactory.sol

116:         address _WETH9,

117:         SemiFungiblePositionManager _SFPM,

```
*GitHub*: [116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L116-L116), [117](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L117-L117)



### [N&#x2011;58] Style guide: Non-`external`/`public` function names should begin with an underscore
According to the Solidity Style Guide, non-`external`/`public` function names should begin with an [underscore](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

*There are 5 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

1450:    function getUniV3TWAP() internal view returns (int24 twapTick) {

```
*GitHub*: [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1450-L1450)

```solidity
File: contracts/SemiFungiblePositionManager.sol

320:     function beginReentrancyLock(uint64 poolId) internal {

330:     function endReentrancyLock(uint64 poolId) internal {

593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

756      function swapInAMM(
757          IUniswapV3Pool univ3pool,
758          LeftRightSigned itmAmounts
759:     ) internal returns (LeftRightSigned totalSwapped) {

```
*GitHub*: [320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L320-L320), [330](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L330-L330), [593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L593-L593), [756](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L756-L759)



### [N&#x2011;59] Style guide: Top-level declarations should be separated by at least two lines
And functions within contracts should be separate by a [single](https://docs.soliditylang.org/en/latest/style-guide.html#blank-lines) line

*There is one instance of this issue:*

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

4     import {PanopticPool} from "@contracts/PanopticPool.sol";
5     
6:    interface IDonorNFT {

```
*GitHub*: [4](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L4-L6)



### [N&#x2011;60] Style guide: Variable names that consist of all capital letters should be reserved for `constant`/`immutable` variables
If the variable needs to be different based on which class it comes from, a `view`/`pure` _function_ should be used instead (e.g. like [this](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59)).

*There is one instance of this issue:*

```solidity
File: contracts/PanopticFactory.sol

116:         address _WETH9,

```
*GitHub*: [116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L116-L116)



### [N&#x2011;61] Unnecessary cast
The variable is being cast to its own type

*There are 15 instances of this issue:*

```solidity
File: contracts/PanopticFactory.sol

/// @audit contract IUniswapV3Pool
404:             IUniswapV3Pool(v3Pool).mint(

```
*GitHub*: [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L404-L404)

```solidity
File: contracts/PanopticPool.sol

/// @audit contract IUniswapV3Pool
302:         s_univ3pool = IUniswapV3Pool(_univ3pool);

/// @audit contract IUniswapV3Pool
304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

/// @audit uint256
309:                 (uint256(block.timestamp) << 216) +

```
*GitHub*: [302](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L302-L302), [304](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L304-L304), [309](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L309-L309)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit address
447:             ? address(decoded.poolFeatures.token0)

/// @audit address
448:             : address(decoded.poolFeatures.token1);

```
*GitHub*: [447](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L447-L447), [448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L448-L448)

```solidity
File: contracts/types/TokenId.sol

/// @audit uint256
110:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

/// @audit uint256
120:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

/// @audit uint256
130:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

/// @audit uint256
140:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

/// @audit uint256
150:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

/// @audit uint256
212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

/// @audit uint256
229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

/// @audit uint256
263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

/// @audit uint256
281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

```
*GitHub*: [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L110-L110), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L120-L120), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L130-L130), [140](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L140-L140), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L150-L150), [212](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L212-L212), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L229-L229), [263](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L263-L263), [281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L281-L281)



### [N&#x2011;62] Unused contract variables
Note that there may be cases where a variable appears to be used, but this is only because there are multiple definitions of the varible in different files. In such cases, the variable definition should be moved into a separate file. The instances below are the unused variables.

*There are 2 instances of this issue:*

```solidity
File: contracts/libraries/Math.sol

15:      uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*GitHub*: [15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L15-L15)

```solidity
File: contracts/libraries/PanopticMath.sol

23:      uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
*GitHub*: [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L23-L23)



### [N&#x2011;63] Unused import
The identifier is imported but never used within the file

*There is one instance of this issue:*

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit TokenId
5:   import {TokenId} from "@types/TokenId.sol";

```
*GitHub*: [5](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L5-L5)



### [N&#x2011;64] Use bit shifts to represent powers of two
Use bit shifts in an immutable variable rather than long hex strings for powers of two, for readability (e.g. `0x1000000000000000000000000` -> `1 << 96`)

*There are 28 instances of this issue:*

```solidity
File: contracts/libraries/Constants.sol

9:       uint256 internal constant FP96 = 0x1000000000000000000000000;

```
*GitHub*: [9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L9-L9)

```solidity
File: contracts/libraries/Math.sol

93:              if (x >= 0x100000000000000000000000000000000) {

97:              if (x >= 0x10000000000000000) {

101:             if (x >= 0x100000000) {

105:             if (x >= 0x10000) {

109:             if (x >= 0x100) {

113:             if (x >= 0x10) {

133:             uint256 sqrtR = absTick & 0x1 != 0

135:                 : 0x100000000000000000000000000000000;

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

```
*GitHub*: [93](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L93-L93), [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L97-L97), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L101-L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L105-L105), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L109-L109), [113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L113-L113), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L133-L133), [135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L135-L135), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L137-L137), [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L139-L139), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L141-L141), [143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L143-L143), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L145-L145), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L147-L147), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L149-L149), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L151-L151), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L153-L153), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L155-L155), [157](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L157-L157), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L159-L159), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L161-L161), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L163-L163), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L165-L165), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L167-L167), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L169-L169), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L171-L171), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L173-L173)



### [N&#x2011;65] Use of `override` is unnecessary
Starting with Solidity version [0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), using the `override` keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.

*There are 4 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

323      function transfer(
324          address recipient,
325          uint256 amount
326:     ) public override(ERC20Minimal) returns (bool) {

341      function transferFrom(
342          address from,
343          address to,
344          uint256 amount
345:     ) public override(ERC20Minimal) returns (bool) {

```
*GitHub*: [323](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323-L326), [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341-L345)

```solidity
File: contracts/SemiFungiblePositionManager.sol

540      function safeTransferFrom(
541          address from,
542          address to,
543          uint256 id,
544          uint256 amount,
545          bytes calldata data
546:     ) public override {

566      function safeBatchTransferFrom(
567          address from,
568          address to,
569          uint256[] calldata ids,
570          uint256[] calldata amounts,
571          bytes calldata data
572:     ) public override {

```
*GitHub*: [540](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L540-L546), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L566-L572)



### [N&#x2011;66] Use the latest solidity (prior to 0.8.20 if on L2s) for deployment
```
When deploying contracts, you should use the latest released version of Solidity. Apart from exceptional cases, only the latest version receives security fixes.
```
https://docs.soliditylang.org/en/v0.8.20/

Since deployed contracts should not use floating pragmas, I've flagged all instances where a version prior to 0.8.19 is allowed by the version pragma

*There are 7 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/CollateralTracker.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L2-L2)

```solidity
File: contracts/PanopticFactory.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L2-L2)

```solidity
File: contracts/PanopticPool.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L2-L2)

```solidity
File: contracts/SemiFungiblePositionManager.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L2-L2)

```solidity
File: contracts/multicall/Multicall.sol

2:   pragma solidity ^0.8.18;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L2-L2)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

2:   pragma solidity ^0.8.0;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L2-L2)

```solidity
File: contracts/tokens/ERC20Minimal.sol

2:   pragma solidity ^0.8.0;

```
*GitHub*: [2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L2-L2)

</details>





### [N&#x2011;67] Variables need not be initialized to false
The default value for boolean variables is `false`, so initializing them to `false` is superfluous.

*There are 5 instances of this issue:*

```solidity
File: contracts/PanopticPool.sol

111:     bool internal constant COMPUTE_LONG_PREMIA = false;

114:     bool internal constant ONLY_AVAILABLE_PREMIUM = false;

120:     bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

133:     bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;

```
*GitHub*: [111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L111-L111), [114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L114-L114), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L120-L120), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L133-L133)

```solidity
File: contracts/SemiFungiblePositionManager.sol

125:     bool internal constant MINT = false;

```
*GitHub*: [125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L125-L125)



### [N&#x2011;68] Visibility should be set explicitly rather than defaulting to `internal`


*There are 8 instances of this issue:*

```solidity
File: contracts/CollateralTracker.sol

131:      uint256 immutable TICK_DEVIATION;

136:      uint256 immutable COMMISSION_FEE;

141:      uint256 immutable SELLER_COLLATERAL_RATIO;

145:      uint256 immutable BUYER_COLLATERAL_RATIO;

149:      int256 immutable FORCE_EXERCISE_COST;

154:      uint256 immutable TARGET_POOL_UTIL;

158:      uint256 immutable SATURATED_POOL_UTIL;

162:      uint256 immutable ITM_SPREAD_MULTIPLIER;

```
*GitHub*: [131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L131), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L136), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L141), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L145), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L149), [154](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L154), [158](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L158), [162](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L162)
