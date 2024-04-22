## Summary

---

### Low Risk Issues
|Id|Title|Instances|
|:--:|:------|:--:|
|[[L-01]](#l-01-some-parts-of-the-codebase-contain-unreachable-code)| Some parts of the codebase contain unreachable code | 1 |
|[[L-02]](#l-02-wrong-median-calculation)| Wrong median calculation | 1 |
|[[L-03]](#l-03-lack-of-deadline-when-swapping)| Lack of deadline when swapping | 1 |
|[[L-04]](#l-04-approve-will-always-revert-as-the-ierc20-interface-mismatch)| `approve` will always revert as the `IERC20` interface mismatch | 4 |
|[[L-05]](#l-05-some-tokens-do-not-consider-typeuint256max-as-an-infinite-approval)| Some tokens do not consider `type(uint256).max` as an infinite approval | 4 |
|[[L-06]](#l-06-contracts-use-infinite-approvals-with-no-means-to-revoke)| Contracts use infinite approvals with no means to revoke | 4 |
|[[L-07]](#l-07-return-values-of-approve-not-checked)| Return values of `approve` not checked | 4 |
|[[L-08]](#l-08-file-allows-a-version-of-solidity-that-is-susceptible-to-selector-related-optimizer-bug)| File allows a version of solidity that is susceptible to .selector-related optimizer bug | 3 |
|[[L-09]](#l-09-low-level-calls-with-solidity-before-0814-result-in-an-optimiser-bug)| Low level calls with Solidity before `0.8.14` result in an optimiser bug | 30 |
|[[L-10]](#l-10-using-delegatecall-inside-a-loop-may-cause-issues-with-payable-functions)| Using `delegatecall` inside a loop may cause issues with `payable` functions | 1 |
|[[L-11]](#l-11-missing-checks-in-constructorinitialize)| Missing checks in constructor/initialize | 2 |
|[[L-12]](#l-12-missing-checks-for-state-variable-assignments)| Missing checks for state variable assignments | 23 |
|[[L-13]](#l-13-vulnerability-to-storage-write-removal)| Vulnerability to storage write removal | 30 |
|[[L-14]](#l-14-payable-function-does-not-transfer-eth)| `payable` function does not transfer ETH | 1 |
|[[L-15]](#l-15-functions-calling-contracts-with-transfer-hooks-are-missing-reentrancy-guards)| Functions calling contracts with transfer hooks are missing reentrancy guards | 2 |
|[[L-16]](#l-16-large-approvals-may-not-work-with-some-erc20-tokens)| Large approvals may not work with some `ERC20` tokens | 4 |
|[[L-17]](#l-17-initializers-could-be-front-run)| Initializers could be front-run | 2 |
|[[L-18]](#l-18-array-lengths-not-checked)| Array lengths not checked | 4 |
|[[L-19]](#l-19-possible-division-by-0-is-not-prevented)| Possible division by 0 is not prevented | 2 |
|[[L-20]](#l-20-missing-limits-when-setting-minmax-amounts)| Missing limits when setting min/max amounts | 2 |
|[[L-21]](#l-21-external-calls-in-an-unbounded-loop-can-result-in-a-dos)| External calls in an unbounded loop can result in a DoS | 22 |
|[[L-22]](#l-22-solidity-version-0820-may-not-work-on-other-chains-due-to-push0)| Solidity version `0.8.20` may not work on other chains due to `PUSH0` | 20 |
|[[L-23]](#l-23-use-of-abiencodepacked-with-dynamic-types-inside-keccak256)| Use of `abi.encodePacked` with dynamic types inside `keccak256` | 9 |
|[[L-24]](#l-24-loss-of-precision-on-division)| Loss of precision on division | 35 |
|[[L-25]](#l-25-use-increaseallowancedecreaseallowance-instead-of-approvesafeapprove)| Use `increaseAllowance/decreaseAllowance` instead of `approve/safeApprove` | 4 |
|[[L-26]](#l-26-using-a-vulnerable-dependency-from-some-libraries)| Using a vulnerable dependency from some libraries | 5 |
|[[L-27]](#l-27-missing-checks-for-address0-in-constructorinitializers)| Missing checks for `address(0)` in constructor/initializers | 9 |
|[[L-28]](#l-28-missing-checks-for-address0-when-updating-state-variables)| Missing checks for `address(0)` when updating state variables | 20 |

Total: 249 instances over 28 issues.

### Non Critical Issues
|Id|Title|Instances|
|:--:|:------|:--:|
|[[N-01]](#n-01-custom-error-should-be-used-rather-than-requireassert)| Custom `error` should be used rather than `require`/`assert` | 9 |
|[[N-02]](#n-02-use-of-transfer-instead-of-safetransfer-is-not-recommended)| Use of `transfer` instead of `safeTransfer` is not recommended | 2 |
|[[N-03]](#n-03-high-cyclomatic-complexity)| High cyclomatic complexity | 33 |
|[[N-04]](#n-04-missing-events-in-sensitive-functions)| Missing events in sensitive functions | 8 |
|[[N-05]](#n-05-missing-events-in-initializers)| Missing events in initializers | 1 |
|[[N-06]](#n-06-consider-emitting-an-event-at-the-end-of-the-constructor)| Consider emitting an event at the end of the constructor | 4 |
|[[N-07]](#n-07-setters-should-prevent-re-setting-the-same-value)| Setters should prevent re-setting the same value | 6 |
|[[N-08]](#n-08-using-zero-as-a-parameter)| Using zero as a parameter | 63 |
|[[N-09]](#n-09-unused-named-return)| Unused named `return` | 20 |
|[[N-10]](#n-10-unused-error-definition)| Unused `error` definition | 2 |
|[[N-11]](#n-11-unused-arguments-should-be-removed-or-implemented)| Unused arguments should be removed or implemented | 8 |
|[[N-12]](#n-12-unused-state-variables)| Unused state variables | 2 |
|[[N-13]](#n-13-openzeppelin-libraries-should-be-upgraded-to-a-newer-version)| OpenZeppelin libraries should be upgraded to a newer version | 5 |
|[[N-14]](#n-14-same-constant-is-redefined-elsewhere)| Same `constant` is redefined elsewhere | 4 |
|[[N-15]](#n-15-enum-values-should-be-used-in-place-of-constant-array-indexes)| Enum values should be used in place of constant array indexes | 26 |
|[[N-16]](#n-16-variable-initialization-with-zero-value)| Variable initialization with zero value | 31 |
|[[N-17]](#n-17-duplicated-requireif-statements-should-be-refactored)| Duplicated `require/if` statements should be refactored | 5 |
|[[N-18]](#n-18-inconsistent-usage-of-requireerror)| Inconsistent usage of `require`/`error` | 1 |
|[[N-19]](#n-19-some-functions-contain-the-same-exact-logic)| Some functions contain the same exact logic | 2 |
|[[N-20]](#n-20-unbounded-loop-may-run-out-of-gas)| Unbounded loop may run out of gas | 34 |
|[[N-21]](#n-21-public-functions-not-called-internally)| Public functions not called internally | 13 |
|[[N-22]](#n-22-large-multiples-of-ten-should-use-scientific-notation)| Large multiples of ten should use scientific notation | 7 |
|[[N-23]](#n-23-use-of-exponentiation-instead-of-scientific-notation)| Use of exponentiation instead of scientific notation | 1 |
|[[N-24]](#n-24-missingmalformed-underscores-for-large-numeric-literals)| Missing/malformed underscores for large numeric literals | 5 |
|[[N-25]](#n-25-avoid-complex-casting)| Avoid complex casting | 67 |
|[[N-26]](#n-26-consider-using-the-using-for-syntax)| Consider using the `using-for` syntax | 460 |
|[[N-27]](#n-27-consider-making-contracts-upgradeable)| Consider making contracts `Upgradeable` | 20 |
|[[N-28]](#n-28-dependence-on-external-protocols)| Dependence on external protocols | 19 |
|[[N-29]](#n-29-debug-imports-in-production-code)| Debug imports in production code | 1 |
|[[N-30]](#n-30-2n---1-should-be-re-written-as-typeuintnmax)| `2**<n> - 1` should be re-written as `type(uint<n>).max` | 44 |
|[[N-31]](#n-31-use-of-non-named-numeric-constants)| Use of non-named numeric constants | 285 |
|[[N-32]](#n-32-consider-splitting-complex-checks-into-multiple-steps)| Consider splitting complex checks into multiple steps | 23 |
|[[N-33]](#n-33-complex-math-should-be-split-into-multiple-steps)| Complex math should be split into multiple steps | 53 |
|[[N-34]](#n-34-time-related-variables-should-use-time-units-instead-of-numbers)| Time related variables should use time units instead of numbers | 3 |
|[[N-35]](#n-35-control-structures-do-not-comply-with-best-practices)| Control structures do not comply with best practices | 120 |
|[[N-36]](#n-36-use-a-single-file-for-system-wide-constants)| Use a single file for system wide constants | 10 |
|[[N-37]](#n-37-old-solidity-version)| Old Solidity version | 20 |
|[[N-38]](#n-38-use-of-floating-pragma)| Use of floating pragma | 9 |
|[[N-39]](#n-39-no-checks-for-empty-bytes)| No checks for empty bytes | 1 |
|[[N-40]](#n-40-use-of-abiencodepacked-instead-of-bytesconcat)| Use of `abi.encodePacked` instead of `bytes.concat` | 5 |
|[[N-41]](#n-41-contract-functions-should-use-an-interface)| Contract functions should use an `interface` | 85 |
|[[N-42]](#n-42-requirerevert-without-any-message)| `require`/`revert` without any message | 9 |
|[[N-43]](#n-43-else-block-is-not-required)| `else` block is not required | 5 |
|[[N-44]](#n-44-multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct-for-readability)| Multiple `address`/ID mappings can be combined into a single mapping of an `address`/ID to a `struct`, for readability | 4 |
|[[N-45]](#n-45-lack-of-specific-import-identifier)| Lack of specific `import` identifier | 1 |
|[[N-46]](#n-46-imports-should-be-organized-more-systematically)| Imports should be organized more systematically | 4 |
|[[N-47]](#n-47-long-bitmasks-are-hard-to-read)| Long bitmasks are hard to read | 1 |
|[[N-48]](#n-48-use-a-struct-to-encapsulate-multiple-function-parameters)| Use a struct to encapsulate multiple function parameters | 42 |
|[[N-49]](#n-49-event-is-missing-msgsender-parameter)| Event is missing `msg.sender` parameter | 9 |
|[[N-50]](#n-50-events-should-emit-both-new-and-old-values)| Events should emit both new and old values | 2 |
|[[N-51]](#n-51-events-may-be-emitted-out-of-order-due-to-reentrancy)| Events may be emitted out of order due to reentrancy | 8 |
|[[N-52]](#n-52-use-of-polymorphism-is-discouraged-for-security-audits)| Use of polymorphism is discouraged for security audits | 15 |
|[[N-53]](#n-53-avoid-external-calls-in-modifiers)| Avoid external calls in modifiers | 1 |
|[[N-54]](#n-54-custom-error-without-details)| Custom `error` without details | 34 |
|[[N-55]](#n-55-dont-use-uppercase-for-non-constantimmutable-variables)| Don't use uppercase for non `constant`/`immutable` variables | 2 |
|[[N-56]](#n-56-constants-in-comparisons-should-appear-on-the-left-side)| Constants in comparisons should appear on the left side | 119 |
|[[N-57]](#n-57-consider-using-delete-instead-of-assigning-zerofalse-to-clear-values)| Consider using `delete` instead of assigning zero/false to clear values | 5 |
|[[N-58]](#n-58-consider-disallowing-transfers-to-addressthis)| Consider disallowing transfers to `address(this)` | 3 |
|[[N-59]](#n-59-use-a-ternary-statement-instead-of-ifelse-when-appropriate)| Use a ternary statement instead of `if`/`else` when appropriate | 3 |
|[[N-60]](#n-60-consider-using-named-returns)| Consider using named returns | 103 |
|[[N-61]](#n-61-layout-order-does-not-comply-with-best-practices)| Layout order does not comply with best practices | 6 |
|[[N-62]](#n-62-function-visibility-order-does-not-comply-with-best-practices)| Function visibility order does not comply with best practices | 56 |
|[[N-63]](#n-63-long-functions-should-be-refactored-into-multiple-functions)| Long functions should be refactored into multiple functions | 33 |
|[[N-64]](#n-64-consider-moving-duplicated-strings-to-constants)| Consider moving duplicated strings to constants | 5 |
|[[N-65]](#n-65-lines-are-too-long)| Lines are too long | 346 |
|[[N-66]](#n-66-some-variables-have-a-implicit-default-visibility)| Some variables have a implicit default visibility | 8 |
|[[N-67]](#n-67-consider-adding-a-blockdeny-list)| Consider adding a block/deny-list | 3 |
|[[N-68]](#n-68-use-of-override-is-unnecessary)| Use of `override` is unnecessary | 4 |
|[[N-69]](#n-69-missing-variable-names)| Missing variable names | 2 |
|[[N-70]](#n-70-typos-in-comments)| Typos in comments | 86 |
|[[N-71]](#n-71-contracts-should-have-full-test-coverage)| Contracts should have full test coverage | - |
|[[N-72]](#n-72-large-or-complicated-code-bases-should-implement-invariant-tests)| Large or complicated code bases should implement invariant tests | - |
|[[N-73]](#n-73-codebase-should-implement-formal-verification-testing)| Codebase should implement formal verification testing | - |
|[[N-74]](#n-74-inconsistent-spacing-in-comments)| Inconsistent spacing in comments | 105 |
|[[N-75]](#n-75-state-variables-should-include-comments)| State variables should include comments | 3 |
|[[N-76]](#n-76-complex-functions-should-have-explicit-comments)| Complex functions should have explicit comments | 24 |
|[[N-77]](#n-77-assembly-code-should-have-explicit-comments)| Assembly code should have explicit comments | 3 |
|[[N-78]](#n-78-use-inheritdoc-for-overridden-functions)| Use `@inheritdoc` for overridden functions | 4 |
|[[N-79]](#n-79-modifier-names-dont-follow-the-solidity-naming-convention)| Modifier names don't follow the Solidity naming convention | 1 |
|[[N-80]](#n-80-variable-names-dont-follow-the-solidity-naming-convention)| Variable names don't follow the Solidity naming convention | 52 |
|[[N-81]](#n-81-missing-underscore-prefix-for-non-external-functions)| Missing underscore prefix for non-external functions | 104 |
|[[N-82]](#n-82-missing-underscore-prefix-for-non-external-variables)| Missing underscore prefix for non-external variables | 36 |
|[[N-83]](#n-83-invalid-natspec-comment-style)| Invalid NatSpec comment style | 3 |
|[[N-84]](#n-84-missing-natspec-from-contract-declarations)| Missing NatSpec from contract declarations | 1 |
|[[N-85]](#n-85-missing-natspec-author-from-contract-declaration)| Missing NatSpec `@author` from contract declaration | 1 |
|[[N-86]](#n-86-missing-natspec-dev-from-contract-declaration)| Missing NatSpec `@dev` from contract declaration | 11 |
|[[N-87]](#n-87-missing-natspec-notice-from-contract-declaration)| Missing NatSpec `@notice` from contract declaration | 5 |
|[[N-88]](#n-88-missing-natspec-title-from-contract-declaration)| Missing NatSpec `@title` from contract declaration | 2 |
|[[N-89]](#n-89-missing-natspec-dev-from-error-declaration)| Missing NatSpec `@dev` from error declaration | 33 |
|[[N-90]](#n-90-missing-natspec-param-from-error-declaration)| Missing NatSpec `@param` from error declaration | 34 |
|[[N-91]](#n-91-missing-natspec-dev-from-event-declaration)| Missing NatSpec `@dev` from event declaration | 11 |
|[[N-92]](#n-92-missing-natspec-dev-from-modifier-declaration)| Missing NatSpec `@dev` from modifier declaration | 1 |
|[[N-93]](#n-93-missing-natspec-param-from-modifier-declaration)| Missing NatSpec `@param` from modifier declaration | 1 |
|[[N-94]](#n-94-missing-natspec-dev-from-function-declaration)| Missing NatSpec `@dev` from function declaration | 142 |
|[[N-95]](#n-95-missing-natspec-notice-from-function-declaration)| Missing NatSpec `@notice` from function declaration | 3 |
|[[N-96]](#n-96-missing-natspec-param-from-function-declaration)| Missing NatSpec `@param` from function declaration | 19 |
|[[N-97]](#n-97-incomplete-natspec-return-from-function-declaration)| Incomplete NatSpec `@return` from function declaration | 8 |

Total: 3043 instances over 97 issues.

---

## Low Risk Issues

---

### [L-01] Some parts of the codebase contain unreachable code

Some branches are hard-coded with constants: for example, in the following case `SLOW_ORACLE_UNISWAP_MODE` is hardcoded to false, so the first part of the branch can never execute.

*There is 1 instance of this issue.*


```solidity
File: contracts/PanopticPool.sol

914:             if (SLOW_ORACLE_UNISWAP_MODE) {
915:                 slowOracleTick = PanopticMath.computeMedianObservedPrice(
916:                     _univ3pool,
917:                     observationIndex,
918:                     observationCardinality,
919:                     SLOW_ORACLE_CARDINALITY,
920:                     SLOW_ORACLE_PERIOD
921:                 );
922:             } else { 
923:                 (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(
924:                     observationIndex,
925:                     observationCardinality,
926:                     MEDIAN_PERIOD,
927:                     s_miniMedian, //@audit-info does not update?
928:                     _univ3pool
929:                 );
930:             }
```
[[914-L930](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L914-L930)]


---

### [L-02] Wrong median calculation

The median calculation is wrong, it always assumes an odd length, but the math is different if the length is even.

In that case, it should be:

```solidity
return int24((sortedTicks[9] + sortedTicks[10]) / 2);
```

*There is 1 instance of this issue.*


```solidity
File: contracts/libraries/PanopticMath.sol

266:             return int24(sortedTicks[10]);
```
[[266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L266)]


---

### [L-03] Lack of deadline when swapping

The inclusion of a transaction expiration check provides a safeguard for users against swapping tokens at a price that is lower than the current market price, but there isn't a check for a deadline, so users can be sandwiched by a MEV bot.

This can happen when the transaction remains in the mempool for a period of time because the gas cost paid by the transaction is lower than the current gas price.

*There is 1 instance of this issue.*


```solidity
File: contracts/SemiFungiblePositionManager.sol

838: 		            (int256 swap0, int256 swap1) = _univ3pool.swap(
839: 		                msg.sender,
840: 		                zeroForOne,
841: 		                swapAmount,
842: 		                zeroForOne
843: 		                    ? Constants.MIN_V3POOL_SQRT_RATIO + 1
844: 		                    : Constants.MAX_V3POOL_SQRT_RATIO - 1,
845: 		                data
846: 		            );
```
[[838-846](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L838-L846)]


---

### [L-04] `approve` will always revert as the `IERC20` interface mismatch

Some tokens, such as [USDT](https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7#code#L199), have a different implementation for the approve function: when the address is cast to a compliant `IERC20` interface and the approve function is used, it will always revert due to the interface mismatch.

*There are 4 instances of this issue.*


```solidity
File: contracts/libraries/InteractionHelper.sol

33: 		        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

34: 		        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

37: 		        IERC20Partial(token0).approve(address(ct0), type(uint256).max);

38: 		        IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```
[[33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L34), [37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L38)]


---

### [L-05] Some tokens do not consider `type(uint256).max` as an infinite approval

Some tokens such as [COMP](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L89-L91) downcast such approvals to uint96 and use that as a raw value rather than interpreting it as an infinite approval. Eventually these approvals will reach zero, at which point the calling contract will no longer function properly.

*There are 4 instances of this issue.*


```solidity
File: contracts/libraries/InteractionHelper.sol

33: 		        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

34: 		        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

37: 		        IERC20Partial(token0).approve(address(ct0), type(uint256).max);

38: 		        IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```
[[33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L34), [37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L38)]


---

### [L-06] Contracts use infinite approvals with no means to revoke

Infinite approvals on external contracts can be dangerous if the target becomes compromised. See [here](https://revoke.cash/exploits) for a list of approval exploits.  The following contracts are vulnerable to such attacks since they have no functionality to revoke the approval (call `approve` with amount `0`). Consider enabling the contract to revoke approval in emergency situations.

*There are 4 instances of this issue.*


```solidity
File: contracts/libraries/InteractionHelper.sol

33: 		        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

34: 		        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

37: 		        IERC20Partial(token0).approve(address(ct0), type(uint256).max);

38: 		        IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```
[[33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L34), [37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L38)]


---

### [L-07] Return values of `approve` not checked

Not all `IERC20` implementations (e.g. USDT, KNC) `revert` when there's a failure in `approve`. The function signature has a boolean return value and they indicate errors that way instead.

By not checking the return value, operations that should have marked as failed, may potentially go through without actually approving anything.

*There are 4 instances of this issue.*


```solidity
File: contracts/libraries/InteractionHelper.sol

33: 		        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

34: 		        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

37: 		        IERC20Partial(token0).approve(address(ct0), type(uint256).max);

38: 		        IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```
[[33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L34), [37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L38)]


---

### [L-08] File allows a version of solidity that is susceptible to .selector-related optimizer bug

In solidity versions prior to 0.8.21, there is a legacy code generation [bug](https://soliditylang.org/blog/2023/07/19/missing-side-effects-on-selector-access-bug/) where if `foo().selector` is called, `foo()` doesn't actually get evaluated. It is listed as low-severity, because projects usually use the contract name rather than a function call to look up the selector.

*There are 3 instances of this issue.*


```solidity
File: contracts/tokens/ERC1155Minimal.sol

115: 		                ERC1155Holder.onERC1155Received.selector

166: 		                ERC1155Holder.onERC1155BatchReceived.selector

225: 		                ERC1155Holder.onERC1155Received.selector
```
[[115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L115), [166](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L166), [225](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L225)]


---

### [L-09] Low level calls with Solidity before `0.8.14` result in an optimiser bug

The project contracts in scope are using low level calls with solidity version before 0.8.14 which can result in an [optimizer bug](https://medium.com/certora/overly-optimistic-optimizer-certora-bug-disclosure-2101e3f7994d).

> This bug causes the optimizer to consider some memory operations in inline assembly as being 'dead' and remove them.

> Later operations that would read the values written by these improperly removed memory operations will instead observe the old version of memory.

*There are 30 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/libraries/Math.sol

353: 		            assembly ("memory-safe") {

362: 		                assembly ("memory-safe") {

379: 		            assembly ("memory-safe") {

383: 		            assembly ("memory-safe") {

393: 		            assembly ("memory-safe") {

398: 		            assembly ("memory-safe") {

404: 		            assembly ("memory-safe") {

467: 		            assembly ("memory-safe") {

476: 		                assembly ("memory-safe") {

493: 		            assembly ("memory-safe") {

497: 		            assembly ("memory-safe") {

503: 		            assembly ("memory-safe") {

530: 		            assembly ("memory-safe") {

539: 		                assembly ("memory-safe") {

556: 		            assembly ("memory-safe") {

560: 		            assembly ("memory-safe") {

566: 		            assembly ("memory-safe") {

607: 		            assembly ("memory-safe") {

616: 		                assembly ("memory-safe") {

633: 		            assembly ("memory-safe") {

637: 		            assembly ("memory-safe") {

643: 		            assembly ("memory-safe") {

684: 		            assembly ("memory-safe") {

693: 		                assembly ("memory-safe") {

710: 		            assembly ("memory-safe") {

714: 		            assembly ("memory-safe") {

720: 		            assembly ("memory-safe") {

739: 		        assembly ("memory-safe") {
```
[[353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L353), [362](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L362), [379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L379), [383](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L383), [393](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L393), [398](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L398), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L404), [467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L467), [476](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L476), [493](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L493), [497](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L497), [503](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L503), [530](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L530), [539](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L539), [556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L556), [560](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L560), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L566), [607](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L607), [616](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L616), [633](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L633), [637](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L637), [643](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L643), [684](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L684), [693](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L693), [710](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L710), [714](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L714), [720](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L720), [739](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L739)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

25: 		        assembly ("memory-safe") {

56: 		        assembly ("memory-safe") {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L25), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L56)]

</details>

---

### [L-10] Using `delegatecall` inside a loop may cause issues with `payable` functions

If one of the `delegatecall` consumes part of the `msg.value`, other calls might fail, if they expect the full `msg.value`. Consider using a different design, or fully document this decision to avoid potential issues.

*There is 1 instance of this issue.*


```solidity
File: contracts/multicall/Multicall.sol

15: 		            (bool success, bytes memory result) = address(this).delegatecall(data[i]);
```
[[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L15)]


---

### [L-11] Missing checks in constructor/initialize

There are some missing checks in these functions, and this could lead to unexpected scenarios. Consider always adding a sanity check for state variables.

*There are 2 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

// @audit _commissionFee, _sellerCollateralRatio, _buyerCollateralRatio, _forceExerciseCost, _targetPoolUtilization, _saturatedPoolUtilization, _ITMSpreadMultiplier
178: 		    constructor(
179: 		        uint256 _commissionFee,
180: 		        uint256 _sellerCollateralRatio,
181: 		        uint256 _buyerCollateralRatio,
182: 		        int256 _forceExerciseCost,
183: 		        uint256 _targetPoolUtilization,
184: 		        uint256 _saturatedPoolUtilization,
185: 		        uint256 _ITMSpreadMultiplier
```
[[178-185](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L178-L185)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit fee
350: 		    function initializeAMMPool(address token0, address token1, uint24 fee) external {
```
[[350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L350)]


---

### [L-12] Missing checks for state variable assignments

There are some missing checks in these functions, and this could lead to unexpected scenarios. Consider always adding a sanity check for state variables.

*There are 23 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

241: 		        s_underlyingToken = underlyingIsToken0 ? token0 : token1;

244: 		        s_panopticPool = panopticPool;

251: 		        s_poolFee = _poolFee;

254: 		        s_univ3token0 = token0;

255: 		        s_univ3token1 = token1;

258: 		        s_underlyingIsToken0 = underlyingIsToken0;

262: 		            s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

1028: 		            s_poolAssets = uint128(uint256(updatedAssets));

1029: 		            s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

1084: 		            s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));

1085: 		            s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));
```
[[241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L241), [244](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L244), [251](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L251), [254](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L254), [255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L255), [258](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L258), [262](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L262), [1028](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1028), [1029](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1029), [1084](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1084), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1085)]



```solidity
File: contracts/PanopticPool.sol

665: 		        if (medianData != 0) s_miniMedian = medianData;

763: 		                s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
764: 		                    .wrap(0)
765: 		                    .toRightSlot(premiumAccumulator0)
766: 		                    .toLeftSlot(premiumAccumulator1);

1628: 		            s_options[owner][tokenId][legIndex] = accumulatedPremium; //@audit-ok can't be lower than before

1656: 		            s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(
1657: 		                LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))
1658: 		            );

1683: 		            s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);

1731: 		                    s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1732: 		                        .wrap(0)
1733: 		                        .toRightSlot(
1734: 		                            uint128(
1735: 		                                (grossCurrent[0] *
1736: 		                                    positionLiquidity +
1737: 		                                    grossPremiumLast.rightSlot() *
1738: 		                                    totalLiquidityBefore) / (totalLiquidity)
1739: 		                            )
1740: 		                        )
1741: 		                        .toLeftSlot(
1742: 		                            uint128(
1743: 		                                (grossCurrent[1] *
1744: 		                                    positionLiquidity +
1745: 		                                    grossPremiumLast.leftSlot() *
1746: 		                                    totalLiquidityBefore) / (totalLiquidity)
1747: 		                            )
1748: 		                        );

1934: 		                        s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1935: 		                            ? LeftRightUnsigned
1936: 		                                .wrap(0)
1937: 		                                .toRightSlot(
1938: 		                                    uint128(
1939: 		                                        uint256(
1940: 		                                            Math.max(
1941: 		                                                (int256(
1942: 		                                                    grossPremiumLast.rightSlot() *
1943: 		                                                        totalLiquidityBefore
1944: 		                                                ) -
1945: 		                                                    int256(
1946: 		                                                        _premiumAccumulatorsByLeg[_leg][0] *
1947: 		                                                            positionLiquidity
1948: 		                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
1949: 		                                                0
1950: 		                                            )
1951: 		                                        ) / totalLiquidity
1952: 		                                    )
1953: 		                                )
1954: 		                                .toLeftSlot(
1955: 		                                    uint128(
1956: 		                                        uint256(
1957: 		                                            Math.max(
1958: 		                                                (int256(
1959: 		                                                    grossPremiumLast.leftSlot() *
1960: 		                                                        totalLiquidityBefore
1961: 		                                                ) -
1962: 		                                                    int256(
1963: 		                                                        _premiumAccumulatorsByLeg[_leg][1] *
1964: 		                                                            positionLiquidity
1965: 		                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
1966: 		                                                0
1967: 		                                            )
1968: 		                                        ) / totalLiquidity
1969: 		                                    )
1970: 		                                )
1971: 		                            : LeftRightUnsigned
1972: 		                                .wrap(0)
1973: 		                                .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1974: 		                                .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));

1980: 		            s_settledTokens[chunkKey] = settledTokens;
```
[[665](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L665), [763-766](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L763-L766), [1628](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1628), [1656-1658](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1656-L1658), [1683](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1683), [1731-1748](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1731-L1748), [1934-1974](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1934-L1974), [1980](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1980)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

1039: 		            s_accountLiquidity[positionKey] = LeftRightUnsigned
1040: 		                .wrap(0)
1041: 		                .toLeftSlot(removedLiquidity)
1042: 		                .toRightSlot(updatedLiquidity);

1099: 		        s_accountFeesBase[positionKey] = _getFeesBase(
1100: 		            univ3pool,
1101: 		            updatedLiquidity,
1102: 		            liquidityChunk,
1103: 		            true
1104: 		        );
```
[[1039-1042](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1039-L1042), [1099-1104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1099-L1104)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

51: 		        allowance[msg.sender][spender] = amount;

85: 		        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
```
[[51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L51), [85](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L85)]

</details>

---

### [L-13] Vulnerability to storage write removal

This bug was introduced in Solidity version 0.8.13, and it was fixed in version 0.8.17. This bug is significantly easier to trigger with optimized via-IR code generation, but can theoretically also occur in optimized legacy code generation.. More info can be read in this [post](https://blog.soliditylang.org/2022/09/08/storage-write-removal-before-conditional-termination/).

*There are 30 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/libraries/Math.sol

353: 		            assembly ("memory-safe") {

362: 		                assembly ("memory-safe") {

379: 		            assembly ("memory-safe") {

383: 		            assembly ("memory-safe") {

393: 		            assembly ("memory-safe") {

398: 		            assembly ("memory-safe") {

404: 		            assembly ("memory-safe") {

467: 		            assembly ("memory-safe") {

476: 		                assembly ("memory-safe") {

493: 		            assembly ("memory-safe") {

497: 		            assembly ("memory-safe") {

503: 		            assembly ("memory-safe") {

530: 		            assembly ("memory-safe") {

539: 		                assembly ("memory-safe") {

556: 		            assembly ("memory-safe") {

560: 		            assembly ("memory-safe") {

566: 		            assembly ("memory-safe") {

607: 		            assembly ("memory-safe") {

616: 		                assembly ("memory-safe") {

633: 		            assembly ("memory-safe") {

637: 		            assembly ("memory-safe") {

643: 		            assembly ("memory-safe") {

684: 		            assembly ("memory-safe") {

693: 		                assembly ("memory-safe") {

710: 		            assembly ("memory-safe") {

714: 		            assembly ("memory-safe") {

720: 		            assembly ("memory-safe") {

739: 		        assembly ("memory-safe") {
```
[[353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L353), [362](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L362), [379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L379), [383](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L383), [393](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L393), [398](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L398), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L404), [467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L467), [476](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L476), [493](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L493), [497](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L497), [503](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L503), [530](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L530), [539](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L539), [556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L556), [560](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L560), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L566), [607](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L607), [616](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L616), [633](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L633), [637](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L637), [643](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L643), [684](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L684), [693](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L693), [710](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L710), [714](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L714), [720](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L720), [739](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L739)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

25: 		        assembly ("memory-safe") {

56: 		        assembly ("memory-safe") {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L25), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L56)]

</details>

---

### [L-14] `payable` function does not transfer ETH

The following functions can be called by any user, who may also send some funds by mistake. In that case, those funds will be lost (this also applies to delegatecalls, in case they don't use the transferred ETH).

*There is 1 instance of this issue.*


```solidity
File: contracts/multicall/Multicall.sol

12: 		    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L12)]


---

### [L-15] Functions calling contracts with transfer hooks are missing reentrancy guards

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks will open the users of this protocol up to read-only reentrancies with no way to protect against it, except by block-listing the whole protocol.

*There are 2 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

333: 		        return ERC20Minimal.transfer(recipient, amount);

352: 		        return ERC20Minimal.transferFrom(from, to, amount);
```
[[333](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L333), [352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L352)]


---

### [L-16] Large approvals may not work with some `ERC20` tokens

Not all `IERC20` implementations are totally compliant, and some (e.g `UNI`, `COMP`) may fail if the valued passed to `approve` is larger than `uint96`. If the approval amount is `type(uint256).max`, which may cause issues with systems that expect the value passed to approve to be reflected in the allowances mapping.

*There are 4 instances of this issue.*


```solidity
File: contracts/libraries/InteractionHelper.sol

33: 		        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

34: 		        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

37: 		        IERC20Partial(token0).approve(address(ct0), type(uint256).max);

38: 		        IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```
[[33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L34), [37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L38)]


---

### [L-17] Initializers could be front-run

Initializers could be front-run, allowing an attacker to either set their own values, take ownership of the contract, and in the best case forcing a re-deployment.

*There are 2 instances of this issue.*


```solidity
File: contracts/PanopticFactory.sol

135: 		    function initialize(address _owner) public {
```
[[135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L135)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

350: 		    function initializeAMMPool(address token0, address token1, uint24 fee) external {
```
[[350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L350)]


---

### [L-18] Array lengths not checked

If the length of the arrays are not required to be of the same length, user operations may not be fully executed.

*There are 4 instances of this issue.*


```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit ids, amounts
566: 		    function safeBatchTransferFrom(
```
[[566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L566)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit positionIdList, premiasByLeg
768: 		    function haircutPremia(
```
[[768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

// @audit ids, amounts
130: 		    function safeBatchTransferFrom(

// @audit owners, ids
178: 		    function balanceOfBatch(
```
[[130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L130), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L178)]


---

### [L-19] Possible division by 0 is not prevented

These functions can be called with 0 value in the input and this value is not checked for being bigger than 0, that means in some scenarios this can potentially trigger a division by zero.

*There are 2 instances of this issue.*


```solidity
File: contracts/libraries/PanopticMath.sol

// @audit tickSpacing
346: 		            int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

// @audit tickSpacing
347: 		            int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;
```
[[346](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L346), [347](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L347)]


---

### [L-20] Missing limits when setting min/max amounts

There are some missing limits in these functions, and this could lead to unexpected scenarios. Consider adding a min/max limit for the following values, when appropriate.

*There are 2 instances of this issue.*


```solidity
File: contracts/PanopticPool.sol

// @audit missing both checks -> positionSize
1672: 		    function _updateSettlementPostMint(
1673: 		        TokenId tokenId,
1674: 		        LeftRightUnsigned[4] memory collectedByLeg,
1675: 		        uint128 positionSize

// @audit missing both checks -> positionSize
1839: 		    function _updateSettlementPostBurn(
1840: 		        address owner,
1841: 		        TokenId tokenId,
1842: 		        LeftRightUnsigned[4] memory collectedByLeg,
1843: 		        uint128 positionSize,
1844: 		        bool commitLongSettled
```
[[1672-1675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1672-L1675), [1839-1844](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1839-L1844)]


---

### [L-21] External calls in an unbounded loop can result in a DoS

Consider limiting the number of iterations in loops that make external calls, as just a single one of them failing will result in a revert.

*There are 22 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

// @audit countLegs (662), isLong (664), unsafeDivRoundingUp (669), width (670), tickSpacing (670), max (675), abs (677), strike (677), getLiquidityChunk (687), getAmountsForLiquidity (693), getAmountsForLiquidity (698), tokenType (704), toLeftSlot (712), toRightSlot (712), wrap (712)
662: 		            for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

// @audit wrap (1210), rightSlot (1213), wrap (1213), leftSlot (1216), wrap (1216)
1208: 		        for (uint256 i = 0; i < totalIterations; ) {

// @audit tokenType (1257)
1255: 		            for (uint256 index = 0; index < numLegs; ++index) {
```
[[662](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L662), [1208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1208), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1255)]



```solidity
File: contracts/PanopticFactory.sol

// @audit numberOfLeadingHexZeros (305), predictDeterministicAddress (306)
304: 		        for (; uint256(salt) < maxSalt; ) {
```
[[304](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L304)]



```solidity
File: contracts/PanopticPool.sol

// @audit unwrap (445), unwrap (446), rightSlot (453), wrap (453), countLegs (459), isLong (461), strike (464), width (465), tokenType (466), wrap (474), unwrap (474), wrap (478), unwrap (478)
442: 		        for (uint256 k = 0; k < pLength; ) { //@audit H - uncapped positions -> unliquidable

// @audit asTicks (749), isLong (750), getAccountPremium (752), tokenType (755), toLeftSlot (763), toRightSlot (763), wrap (763), min (776)
746: 		        for (uint256 leg = 0; leg < numLegs; ) {

// @audit isLong (866), asTicks (868), wrap (871)
865: 		        for (uint256 leg = 0; leg < numLegs; ) {

// @audit updatePositionsHash (1389)
1388: 		        for (uint256 i = 0; i < pLength; ) {

// @audit isLong (1525), getLiquidityChunk (1527), tokenType (1532), getAccountPremium (1534), tickLower (1539), tickUpper (1540), toLeftSlot (1551), toRightSlot (1551), wrap (1551), rightSlot (1557), liquidity (1558), leftSlot (1566), liquidity (1567), wrap (1573)
1524: 		        for (uint256 leg = 0; leg < numLegs; ) {

// @audit strike (1680), width (1680), tokenType (1680), isLong (1685), getLiquidityChunk (1686), getAccountPremium (1713), tokenType (1716), tickLower (1717), tickUpper (1718), liquidity (1727), toLeftSlot (1731), toRightSlot (1731), wrap (1731), rightSlot (1737), leftSlot (1745)
1678: 		        for (uint256 leg = 0; leg < numLegs; ++leg) {

// @audit strike (1862), width (1862), tokenType (1862), unwrap (1868), isLong (1870), wrap (1872), unwrap (1874), wrap (1875), unwrap (1876), liquidity (1883), getLiquidityChunk (1883), wrap (1898), unwrap (1898), wrap (1907), unwrap (1907), toLeftSlot (1935), toRightSlot (1935), wrap (1935), max (1940), rightSlot (1942), rightSlot (1948), max (1957), leftSlot (1959), leftSlot (1965), toLeftSlot (1971), toRightSlot (1971), wrap (1971)
1858: 		        for (uint256 leg = 0; leg < numLegs; ) {
```
[[442](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L442), [746](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L746), [865](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L865), [1388](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1388), [1524](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1524), [1678](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1678), [1858](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1858)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit incrementPoolPattern (373)
372: 		        while (address(s_poolContext[poolId].pool) != address(0)) {

// @audit poolId (576), wrap (576), ReentrantCall (576), wrap (577)
575: 		        for (uint256 i = 0; i < ids.length; ) {

// @audit getLiquidityChunk (604), tokenType (615), tickLower (616), tickUpper (617), tokenType (624), tickLower (625), tickUpper (626), unwrap (632), unwrap (633), TransferFailed (634), unwrap (639), liquidity (639), TransferFailed (640), wrap (646), wrap (649)
601: 		        for (uint256 leg = 0; leg < numLegs; ) {

// @audit getLiquidityChunk (905), getAmount0ForLiquidity (923), getAmount1ForLiquidity (925)
883: 		        for (uint256 leg = 0; leg < numLegs; ) {
```
[[372](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L372), [575](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L575), [601](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L601), [883](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L883)]



```solidity
File: contracts/libraries/FeesCalc.sol

// @audit rightSlot (53), countLegs (54), getLiquidityChunk (56), getAmountsForLiquidity (62), isLong (67)
51: 		        for (uint256 k = 0; k < positionIdList.length; ) {
```
[[51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L51)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit observations (138)
137: 		            for (uint256 i = 0; i < cardinality + 1; ++i) {

// @audit countLegs (783), isLong (785)
781: 		            for (uint256 i = 0; i < positionIdList.length; ++i) {

// @audit countLegs (863), isLong (864), unsafeDivRoundingUp (869), rightSlot (870), rightSlot (871), unsafeDivRoundingUp (873), leftSlot (874), leftSlot (875), strike (880), width (881), tokenType (882), max (888), rightSlot (890), max (892), leftSlot (894), toLeftSlot (898), toRightSlot (898), wrap (898)
860: 		            for (uint256 i = 0; i < positionIdList.length; i++) {
```
[[137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L137), [781](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L781), [860](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L860)]



```solidity
File: contracts/multicall/Multicall.sol

// @audit delegatecall (15)
14: 		        for (uint256 i = 0; i < data.length; ) {
```
[[14](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L14)]



```solidity
File: contracts/types/TokenId.sol

// @audit optionRatio (508), unwrap (512), InvalidTokenIdParameter (513), countLegs (519), InvalidTokenIdParameter (522), width (528), InvalidTokenIdParameter (528), strike (531), strike (532), InvalidTokenIdParameter (533), riskPartner (538), riskPartner (541), InvalidTokenIdParameter (542), asset (546), asset (546), optionRatio (547), optionRatio (547), InvalidTokenIdParameter (548), isLong (551), isLong (552), tokenType (555), tokenType (556), InvalidTokenIdParameter (561), InvalidTokenIdParameter (567)
507: 		            for (uint256 i = 0; i < 4; ++i) {

// @audit getRangesFromStrike (582), width (583), tickSpacing (584), strike (587), isLong (592)
581: 		            for (uint256 i = 0; i < numLegs; ++i) {
```
[[507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L507), [581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L581)]

</details>

---

### [L-22] Solidity version `0.8.20` may not work on other chains due to `PUSH0`

In Solidity `0.8.20`'s compiler, the default target EVM version has been changed to Shanghai. This version introduces a new op code called `PUSH0`.

However, not all Layer 2 solutions have implemented this op code yet, leading to deployment failures on these chains. To overcome this problem, it is recommended to utilize an earlier EVM version.

*There are 20 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L2)]



```solidity
File: contracts/PanopticFactory.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L2)]



```solidity
File: contracts/PanopticPool.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L2)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L2)]



```solidity
File: contracts/libraries/CallbackLib.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L2)]



```solidity
File: contracts/libraries/Constants.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L2)]



```solidity
File: contracts/libraries/Errors.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L2)]



```solidity
File: contracts/libraries/FeesCalc.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L2)]



```solidity
File: contracts/libraries/InteractionHelper.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L2)]



```solidity
File: contracts/libraries/Math.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L2)]



```solidity
File: contracts/libraries/PanopticMath.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L2)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L2)]



```solidity
File: contracts/multicall/Multicall.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L2)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L2)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L2)]



```solidity
File: contracts/types/LeftRight.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L2)]



```solidity
File: contracts/types/LiquidityChunk.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L2)]



```solidity
File: contracts/types/TokenId.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L2)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L2)]



```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L2)]

</details>

---

### [L-23] Use of `abi.encodePacked` with dynamic types inside `keccak256`

`abi.encodePacked` should not be used with dynamic types when passing the result to a hash function such as `keccak256`. Use `abi.encode` instead, which will pad items to 32 bytes, to [prevent any hash collisions](https://docs.soliditylang.org/en/latest/abi-spec.html#non-standard-packed-mode).

*There are 9 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/PanopticPool.sol

462: 		                    bytes32 chunkKey = keccak256(
463: 		                        abi.encodePacked(
464: 		                            tokenId.strike(leg),
465: 		                            tokenId.width(leg),
466: 		                            tokenId.tokenType(leg)
467: 		                        ) //@audit-info collision between two legs? (isLong or riskPartner)
468: 		                    );

1648: 		            bytes32 chunkKey = keccak256(
1649: 		                abi.encodePacked(
1650: 		                    tokenId.strike(legIndex),
1651: 		                    tokenId.width(legIndex),
1652: 		                    tokenId.tokenType(legIndex)
1653: 		                )
1654: 		            );

1679: 		            bytes32 chunkKey = keccak256(
1680: 		                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1681: 		            );

1861: 		            bytes32 chunkKey = keccak256(
1862: 		                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1863: 		            );
```
[[462-468](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L462-L468), [1648-1654](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1648-L1654), [1679-1681](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1679-L1681), [1861-1863](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1861-L1863)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

611: 		            bytes32 positionKey_from = keccak256(
612: 		                abi.encodePacked(
613: 		                    address(univ3pool),
614: 		                    from,
615: 		                    id.tokenType(leg),
616: 		                    liquidityChunk.tickLower(),
617: 		                    liquidityChunk.tickUpper()
618: 		                )
619: 		            );

620: 		            bytes32 positionKey_to = keccak256(
621: 		                abi.encodePacked(
622: 		                    address(univ3pool),
623: 		                    to,
624: 		                    id.tokenType(leg),
625: 		                    liquidityChunk.tickLower(),
626: 		                    liquidityChunk.tickUpper()
627: 		                )
628: 		            );

975: 		        bytes32 positionKey = keccak256(
976: 		            abi.encodePacked(
977: 		                address(univ3pool),
978: 		                msg.sender,
979: 		                tokenType,
980: 		                liquidityChunk.tickLower(),
981: 		                liquidityChunk.tickUpper()
982: 		            )
983: 		        );

1151: 		                keccak256(
1152: 		                    abi.encodePacked(
1153: 		                        address(this),
1154: 		                        liquidityChunk.tickLower(),
1155: 		                        liquidityChunk.tickUpper()
1156: 		                    )
1157: 		                )
```
[[611-619](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L611-L619), [620-628](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L620-L628), [975-983](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L975-L983), [1151-1157](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1151-L1157)]



```solidity
File: contracts/libraries/PanopticMath.sol

878: 		                        bytes32 chunkKey = keccak256(
879: 		                            abi.encodePacked(
880: 		                                tokenId.strike(0),
881: 		                                tokenId.width(0),
882: 		                                tokenId.tokenType(0)
883: 		                            )
884: 		                        );
```
[[878-884](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L878-L884)]

</details>

---

### [L-24] Loss of precision on division

Solidity doesn't support fractions, so divisions by large numbers could result in the quotient being zero.

To avoid this, it's recommended to require a minimum numerator amount to ensure that it is always greater than the denominator.

*There are 35 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

205: 		                    (7812 * ratioTick ** 2) /
206: 		                    10_000 ** 2 +

207: 		                    (6510 * ratioTick ** 3) /
208: 		                    10_000 ** 3

249: 		            _poolFee = fee / 100;

262: 		            s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

446: 		            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

677: 		                        uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

731: 		                .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))

732: 		                .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

743: 		            return int256((s_inAMM * DECIMALS) / totalAssets());

797: 		                ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798: 		                (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);

850: 		                    (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851: 		                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2
```
[[205-206](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L205-L206), [207-208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L207-L208), [249](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L249), [262](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L262), [446](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L446), [677](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L677), [731](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L731), [732](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L732), [743](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L743), [797-798](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L797-L798), [850-851](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L850-L851)]



```solidity
File: contracts/PanopticFactory.sol

393: 		            tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;
```
[[393](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L393)]



```solidity
File: contracts/PanopticPool.sol

1493: 		            effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

1556: 		                                    ((premiumAccumulatorsByLeg[leg][0] -
1557: 		                                        premiumAccumulatorLast.rightSlot()) *
1558: 		                                        (liquidityChunk.liquidity())) / 2 ** 64

1565: 		                                    ((premiumAccumulatorsByLeg[leg][1] -
1566: 		                                        premiumAccumulatorLast.leftSlot()) *
1567: 		                                        (liquidityChunk.liquidity())) / 2 ** 64

1641: 		                .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1642: 		                .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1735: 		                                (grossCurrent[0] *
1736: 		                                    positionLiquidity +
1737: 		                                    grossPremiumLast.rightSlot() *
1738: 		                                    totalLiquidityBefore) / (totalLiquidity)

1743: 		                                (grossCurrent[1] *
1744: 		                                    positionLiquidity +
1745: 		                                    grossPremiumLast.leftSlot() *
1746: 		                                    totalLiquidityBefore) / (totalLiquidity)

1774: 		            uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *
1775: 		                totalLiquidity) / 2 ** 64;

1776: 		            uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *
1777: 		                totalLiquidity) / 2 ** 64;

1785: 		                                (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /
1786: 		                                    (accumulated0 == 0 ? type(uint256).max : accumulated0),

1794: 		                                (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /
1795: 		                                    (accumulated1 == 0 ? type(uint256).max : accumulated1),

1939: 		                                        uint256(
1940: 		                                            Math.max(
1941: 		                                                (int256(
1942: 		                                                    grossPremiumLast.rightSlot() *
1943: 		                                                        totalLiquidityBefore
1944: 		                                                ) -
1945: 		                                                    int256(
1946: 		                                                        _premiumAccumulatorsByLeg[_leg][0] *
1947: 		                                                            positionLiquidity
1948: 		                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
1949: 		                                                0
1950: 		                                            )
1951: 		                                        ) / totalLiquidity

1956: 		                                        uint256(
1957: 		                                            Math.max(
1958: 		                                                (int256(
1959: 		                                                    grossPremiumLast.leftSlot() *
1960: 		                                                        totalLiquidityBefore
1961: 		                                                ) -
1962: 		                                                    int256(
1963: 		                                                        _premiumAccumulatorsByLeg[_leg][1] *
1964: 		                                                            positionLiquidity
1965: 		                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
1966: 		                                                0
1967: 		                                            )
1968: 		                                        ) / totalLiquidity
```
[[1493](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1493), [1556-1558](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1556-L1558), [1565-1567](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1565-L1567), [1641](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1641), [1642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1642), [1735-1738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1735-L1738), [1743-1746](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1743-L1746), [1774-1775](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1774-L1775), [1776-1777](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1776-L1777), [1785-1786](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1785-L1786), [1794-1795](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1794-L1795), [1939-1951](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1939-L1951), [1956-1968](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1956-L1968)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

1368: 		                    uint256 numerator = netLiquidity + (removedLiquidity / 2 ** VEGOID);

1392: 		                        ((removedLiquidity ** 2) / 2 ** (VEGOID));
```
[[1368](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1368), [1392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1392)]



```solidity
File: contracts/libraries/Math.sol

176: 		            if (tick > 0) sqrtR = type(uint256).max / sqrtR;

196: 		                mulDiv(
197: 		                    uint256(liquidityChunk.liquidity()) << 96,
198: 		                    highPriceX96 - lowPriceX96,
199: 		                    highPriceX96
200: 		                ) / lowPriceX96;
```
[[176](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L176), [196-200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L196-L200)]



```solidity
File: contracts/libraries/PanopticMath.sol

150: 		                    (tickCumulatives[i] - tickCumulatives[i + 1]) /
151: 		                    int256(timestamps[i] - timestamps[i + 1]);

195: 		                        (tickCumulative_last - tickCumulative_old) /
196: 		                            int256(timestamp_last - timestamp_old)

258: 		                    (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

346: 		            int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

347: 		            int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

669: 		                uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);
```
[[150-151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L150-L151), [195-196](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L195-L196), [258](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L258), [346](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L346), [347](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L347), [669](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L669)]

</details>

---

### [L-25] Use `increaseAllowance/decreaseAllowance` instead of `approve/safeApprove`

Changing an allowance with `approve` brings the risk that someone may use both the old and the new allowance by unfortunate transaction ordering. Refer to [ERC20 API: An Attack Vector on the Approve/TransferFrom Methods](https://docs.google.com/document/d/1YLPtQxZu1UAvO9cZ1O2RPXBbT0mooh4DYKjA_jp-RLM/edit).

It is recommended to use the `increaseAllowance/decreaseAllowance` to avoid ths problem.

*There are 4 instances of this issue.*


```solidity
File: contracts/libraries/InteractionHelper.sol

33: 		        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

34: 		        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

37: 		        IERC20Partial(token0).approve(address(ct0), type(uint256).max);

38: 		        IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```
[[33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L34), [37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L38)]


---

### [L-26] Using a vulnerable dependency from some libraries

This project is using a vulnerable version of some libraries, which have the following issues:



Current `@openzeppelin/contracts` version: 4.6.0

|Risk|Title|Min Version|Max Version|
|------|-------|-------------|-------------|
|LOW|[Denial of Service (DoS)](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-5425827)|>=3.2.0|<4.8.3|
|MEDIUM|[Improper Input Validation](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-5425051)|>=3.3.0|<4.9.2|
|MEDIUM|[Improper Encoding or Escaping of Output](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-5838352)|>=4.0.0|<4.9.3|
|HIGH|[Improper Verification of Cryptographic Signature](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-2980279)|>=0.0.0|<4.7.3|
|MEDIUM|[Denial of Service (DoS)](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-2965798)|>=2.3.0|<4.7.2|
|LOW|[Incorrect Resource Transfer Between Spheres](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-2965580)|>=4.6.0|<4.7.2|
|HIGH|[Incorrect Calculation](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-2964946)|>=4.3.0|<4.7.2|
|HIGH|[Information Exposure](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-2958050)|>=4.1.0|<4.7.1|
|HIGH|[Information Exposure](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-2958047)|>=4.0.0|<4.7.1|
|LOW|[Missing Authorization](https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-5672116)|>=4.3.0|<4.9.1|

*There are 5 instances of this issue.*


```solidity
File: contracts/PanopticFactory.sol

14: 		import {Clones} from "@openzeppelin/contracts/proxy/Clones.sol";
```
[[14](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L14)]



```solidity
File: contracts/PanopticPool.sol

9: 		import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```
[[9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L9)]



```solidity
File: contracts/libraries/InteractionHelper.sol

6: 		import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

10: 		import {Strings} from "@openzeppelin/contracts/utils/Strings.sol";
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L6), [10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L10)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

5: 		import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```
[[5](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L5)]


---

### [L-27] Missing checks for `address(0)` in constructor/initializers

Check for zero-address to avoid the risk of setting `address(0)` for state variables when deploying.

*There are 9 instances of this issue.*


```solidity
File: contracts/PanopticFactory.sol

// @audit _WETH9
124: 		        WETH = _WETH9;

// @audit _SFPM
125: 		        SFPM = _SFPM;

// @audit _univ3Factory
128: 		        UNIV3_FACTORY = _univ3Factory;

// @audit _donorNFT
126: 		        DONOR_NFT = _donorNFT;

// @audit _poolReference
129: 		        POOL_REFERENCE = _poolReference;

// @audit _collateralReference
130: 		        COLLATERAL_REFERENCE = _collateralReference;

// @audit _owner
137: 		            s_owner = _owner;
```
[[124](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L124), [125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L125), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L128), [126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L126), [129](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L129), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L130), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L137)]



```solidity
File: contracts/PanopticPool.sol

// @audit _sfpm
282: 		        SFPM = _sfpm;
```
[[282](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L282)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit _factory
342: 		        FACTORY = _factory;
```
[[342](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L342)]


---

### [L-28] Missing checks for `address(0)` when updating state variables

Check for zero-address to avoid the risk of setting `address(0)` for state variables after an update.

*There are 20 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

// @audit token0
241: 		        s_underlyingToken = underlyingIsToken0 ? token0 : token1;

// @audit token1
241: 		        s_underlyingToken = underlyingIsToken0 ? token0 : token1;

// @audit panopticPool
244: 		        s_panopticPool = panopticPool;
```
[[241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L241), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L241), [244](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L244)]



```solidity
File: contracts/PanopticFactory.sol

// @audit newOwner
153: 		        s_owner = newOwner;
```
[[153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L153)]



```solidity
File: contracts/PanopticPool.sol

// @audit _univ3pool
303: 		        s_univ3pool = IUniswapV3Pool(_univ3pool);

// @audit collateralTracker0
319: 		        s_collateralToken0 = collateralTracker0;

// @audit collateralTracker1
320: 		        s_collateralToken1 = collateralTracker1;

// @audit tokenId
763: 		                s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
764: 		                    .wrap(0)
765: 		                    .toRightSlot(premiumAccumulator0)
766: 		                    .toLeftSlot(premiumAccumulator1);

// @audit owner
862: 		        s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

// @audit tokenId
862: 		        s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

// @audit account
1422: 		        s_positionsHash[account] = newHash;

// @audit owner
1628: 		            s_options[owner][tokenId][legIndex] = accumulatedPremium; //@audit-ok can't be lower than before
```
[[303](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L303), [319](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L319), [320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L320), [763-766](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L763-L766), [862](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L862), [862](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L862), [1422](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1422), [1628](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1628)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit from
645: 		            s_accountLiquidity[positionKey_to] = fromLiq;

// @audit to
645: 		            s_accountLiquidity[positionKey_to] = fromLiq;

// @audit id
645: 		            s_accountLiquidity[positionKey_to] = fromLiq;

// @audit univ3pool
1099: 		        s_accountFeesBase[positionKey] = _getFeesBase(
1100: 		            univ3pool,
1101: 		            updatedLiquidity,
1102: 		            liquidityChunk,
1103: 		            true
1104: 		        );

// @audit liquidityChunk
1099: 		        s_accountFeesBase[positionKey] = _getFeesBase(
1100: 		            univ3pool,
1101: 		            updatedLiquidity,
1102: 		            liquidityChunk,
1103: 		            true
1104: 		        );
```
[[645](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L645), [645](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L645), [645](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L645), [1099-1104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1099-L1104), [1099-1104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1099-L1104)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

// @audit operator
82: 		        isApprovedForAll[msg.sender][operator] = approved;
```
[[82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L82)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

// @audit spender
51: 		        allowance[msg.sender][spender] = amount;

// @audit from
85: 		        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
```
[[51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L51), [85](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L85)]

</details>

---

## Non Critical Issues

---

### [N-01] Custom `error` should be used rather than `require`/`assert`

Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in try-catch blocks, and are easier to re-use and maintain.

*There are 9 instances of this issue.*


```solidity
File: contracts/libraries/Math.sol

361: 		                require(denominator > 0);

370: 		            require(denominator > prod1);

448: 		                require(result < type(uint256).max);

484: 		            require(2 ** 64 > prod1);

547: 		            require(2 ** 96 > prod1);

588: 		                require(result < type(uint256).max);

624: 		            require(2 ** 128 > prod1);

665: 		                require(result < type(uint256).max);

701: 		            require(2 ** 192 > prod1);
```
[[361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L370), [448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L448), [484](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L484), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L547), [588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L588), [624](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L624), [665](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L665), [701](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L701)]


---

### [N-02] Use of `transfer` instead of `safeTransfer` is not recommended

It is good to add a `require` statement that checks the return value of token transfers, or to use something like OpenZeppelin's `safeTransfer`/`safeTransferFrom`, even if one is sure that the given token reverts in case of a failure.

This reduces the risk to zero even if these contracts are upgreadable, and it also helps with security reviews, as the auditor will not have to check this specific edge case.

*There are 2 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

333: 		        return ERC20Minimal.transfer(recipient, amount);

352: 		        return ERC20Minimal.transferFrom(from, to, amount);
```
[[333](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L333), [352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L352)]


---

### [N-03] High cyclomatic complexity

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

*There are 33 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

650: 		    function exerciseCost(

911: 		    function revoke(

1311: 		    function _getRequiredCollateralSingleLegNoPartner(

1510: 		    function _computeSpread(
```
[[650](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L650), [911](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L911), [1311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1311), [1510](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1510)]



```solidity
File: contracts/PanopticFactory.sol

211: 		    function deployNewPool(

336: 		    function _mintFullRange(
```
[[211](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L211), [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L336)]



```solidity
File: contracts/PanopticPool.sol

430: 		    function _calculateAccumulatedPremia( //@audit-info positive premia???

615: 		    function _mintOptions(

888: 		    function _validateSolvency(

1018: 		    function liquidate(

1180: 		    function forceExercise(

1509: 		    function _getPremia(

1593: 		    function settleLongPremium(

1672: 		    function _updateSettlementPostMint(

1839: 		    function _updateSettlementPostBurn(
```
[[430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L430), [615](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L615), [888](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L888), [1018](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1018), [1180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1180), [1509](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1509), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1593), [1672](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1672), [1839](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1839)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

593: 		    function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

757: 		    function swapInAMM(

864: 		    function _createPositionInAMM(

959: 		    function _createLegInAMM(

1256: 		    function _collectAndWritePositionData(

1322: 		    function _getPremiaDeltas(

1450: 		    function getAccountPremium(
```
[[593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L593), [757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L757), [864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L864), [959](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L959), [1256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1256), [1322](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1322), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1450)]



```solidity
File: contracts/libraries/FeesCalc.sol

130: 		    function _getAMMSwapFeesPerLiquidityCollected(
```
[[130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L130)]



```solidity
File: contracts/libraries/Math.sol

128: 		    function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) { //@audit-ok

340: 		    function mulDiv(

458: 		    function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521: 		    function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

598: 		    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

675: 		    function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {
```
[[128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L128), [340](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L340), [458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L521), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L598), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L675)]



```solidity
File: contracts/libraries/PanopticMath.sol

168: 		    function computeInternalMedian(

651: 		    function getLiquidationBonus(

768: 		    function haircutPremia(
```
[[168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L168), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768)]



```solidity
File: contracts/types/TokenId.sol

500: 		    function validate(TokenId self) internal pure {
```
[[500](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L500)]

</details>

---

### [N-04] Missing events in sensitive functions

Events should be emitted when sensitive changes are made to the contracts, but some functions lack them.

*There are 8 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/PanopticPool.sol

860: 		    function _updatePositionDataBurn(address owner, TokenId tokenId) internal {
861: 		        // reset balances and delete stored option data
862: 		        s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
863: 		
864: 		        uint256 numLegs = tokenId.countLegs();
865: 		        for (uint256 leg = 0; leg < numLegs; ) {
866: 		            if (tokenId.isLong(leg) == 0) {
867: 		                // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
868: 		                (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
869: 		                _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
870: 		            }
871: 		            s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
872: 		            unchecked {
873: 		                ++leg;
874: 		            }
875: 		        }
876: 		
877: 		        // Update the position list hash (hash = XOR of all keccak256(tokenId)). Remove hash by XOR'ing again
878: 		        _updatePositionsHash(owner, tokenId, !ADD);
879: 		    }

1411: 		    function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {
1412: 		        // Get the current position hash value (fingerprint of all pre-existing positions created by '_account')
1413: 		        // Add the current tokenId to the positionsHash as XOR'd
1414: 		        // since 0 ^ x = x, no problem on first mint
1415: 		        // Store values back into the user option details with the updated hash (leaves the other parameters unchanged)
1416: 		        uint256 newHash = PanopticMath.updatePositionsHash(
1417: 		            s_positionsHash[account],
1418: 		            tokenId,
1419: 		            addFlag
1420: 		        );
1421: 		        if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();
1422: 		        s_positionsHash[account] = newHash;
1423: 		    }

1672: 		    function _updateSettlementPostMint(
1673: 		        TokenId tokenId,
1674: 		        LeftRightUnsigned[4] memory collectedByLeg,
1675: 		        uint128 positionSize
1676: 		    ) internal {
1677: 		        uint256 numLegs = tokenId.countLegs();
1678: 		        for (uint256 leg = 0; leg < numLegs; ++leg) {
1679: 		            bytes32 chunkKey = keccak256(
1680: 		                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1681: 		            );
1682: 		            // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers
1683: 		            s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1684: 		
1685: 		            if (tokenId.isLong(leg) == 0) {
1686: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1687: 		                    tokenId,
1688: 		                    leg,
1689: 		                    positionSize
1690: 		                );
1691: 		
1692: 		                // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (R + N)
1693: 		                uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1694: 		
1695: 		                // We need to adjust the grossPremiumLast value such that the result of
1696: 		                // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64
1697: 		                // G: total gross premium
1698: 		                // T: totalLiquidityBeforeMint
1699: 		                // R: positionLiquidity
1700: 		                // C: current grossPremium value
1701: 		                // L: current grossPremiumLast value
1702: 		                // Ln: updated grossPremiumLast value
1703: 		                // T * (C - L) = G
1704: 		                // (T + R) * (C - Ln) = G
1705: 		                //
1706: 		                // T * (C - L) = (T + R) * (C - Ln)
1707: 		                // (TC - TL) / (T + R) = C - Ln
1708: 		                // Ln = C - (TC - TL)/(T + R)
1709: 		                // Ln = (CT + CR - TC + TL)/(T+R)
1710: 		                // Ln = (CR + TL)/(T+R)
1711: 		
1712: 		                uint256[2] memory grossCurrent;
1713: 		                (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1714: 		                    address(s_univ3pool),
1715: 		                    address(this),
1716: 		                    tokenId.tokenType(leg),
1717: 		                    liquidityChunk.tickLower(),
1718: 		                    liquidityChunk.tickUpper(),
1719: 		                    type(int24).max,
1720: 		                    0
1721: 		                );
1722: 		
1723: 		                unchecked {
1724: 		                    // L
1725: 		                    LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1726: 		                    // R
1727: 		                    uint256 positionLiquidity = liquidityChunk.liquidity();
1728: 		                    // T (totalLiquidity is (T + R) after minting)
1729: 		                    uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
1730: 		
1731: 		                    s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1732: 		                        .wrap(0)
1733: 		                        .toRightSlot(
1734: 		                            uint128(
1735: 		                                (grossCurrent[0] *
1736: 		                                    positionLiquidity +
1737: 		                                    grossPremiumLast.rightSlot() *
1738: 		                                    totalLiquidityBefore) / (totalLiquidity)
1739: 		                            )
1740: 		                        )
1741: 		                        .toLeftSlot(
1742: 		                            uint128(
1743: 		                                (grossCurrent[1] *
1744: 		                                    positionLiquidity +
1745: 		                                    grossPremiumLast.leftSlot() *
1746: 		                                    totalLiquidityBefore) / (totalLiquidity)
1747: 		                            )
1748: 		                        );
1749: 		                }
1750: 		            }
1751: 		        }
1752: 		    }

1839: 		    function _updateSettlementPostBurn(
1840: 		        address owner,
1841: 		        TokenId tokenId,
1842: 		        LeftRightUnsigned[4] memory collectedByLeg,
1843: 		        uint128 positionSize,
1844: 		        bool commitLongSettled
1845: 		    ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
1846: 		        uint256 numLegs = tokenId.countLegs();
1847: 		        uint256[2][4] memory premiumAccumulatorsByLeg;
1848: 		
1849: 		        // compute accumulated fees
1850: 		        (premiaByLeg, premiumAccumulatorsByLeg) = _getPremia(
1851: 		            tokenId,
1852: 		            positionSize,
1853: 		            owner,
1854: 		            COMPUTE_ALL_PREMIA,
1855: 		            type(int24).max
1856: 		        );
1857: 		
1858: 		        for (uint256 leg = 0; leg < numLegs; ) {
1859: 		            LeftRightSigned legPremia = premiaByLeg[leg];
1860: 		
1861: 		            bytes32 chunkKey = keccak256(
1862: 		                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1863: 		            );
1864: 		
1865: 		            // collected from Uniswap
1866: 		            LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1867: 		
1868: 		            if (LeftRightSigned.unwrap(legPremia) != 0) {
1869: 		                // (will be) paid by long legs
1870: 		                if (tokenId.isLong(leg) == 1) {
1871: 		                    if (commitLongSettled)
1872: 		                        settledTokens = LeftRightUnsigned.wrap(
1873: 		                            uint256(
1874: 		                                LeftRightSigned.unwrap(
1875: 		                                    LeftRightSigned
1876: 		                                        .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1877: 		                                        .sub(legPremia)
1878: 		                                )
1879: 		                            )
1880: 		                        );
1881: 		                    realizedPremia = realizedPremia.add(legPremia);
1882: 		                } else {
1883: 		                    uint256 positionLiquidity = PanopticMath
1884: 		                        .getLiquidityChunk(tokenId, leg, positionSize)
1885: 		                        .liquidity();
1886: 		
1887: 		                    // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (T - R)
1888: 		                    uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1889: 		                    // T (totalLiquidity is (T - R) after burning)
1890: 		                    uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;
1891: 		
1892: 		                    LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1893: 		
1894: 		                    LeftRightUnsigned availablePremium = _getAvailablePremium(
1895: 		                        totalLiquidity + positionLiquidity,
1896: 		                        settledTokens,
1897: 		                        grossPremiumLast,
1898: 		                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
1899: 		                        premiumAccumulatorsByLeg[leg]
1900: 		                    );
1901: 		
1902: 		                    // subtract settled tokens sent to seller
1903: 		                    settledTokens = settledTokens.sub(availablePremium);
1904: 		
1905: 		                    // add available premium to amount that should be settled
1906: 		                    realizedPremia = realizedPremia.add(
1907: 		                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1908: 		                    );
1909: 		
1910: 		                    // We need to adjust the grossPremiumLast value such that the result of
1911: 		                    // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostBurn/2**64 is equal to
1912: 		                    // (grossPremium - grossPremiumLast)*totalLiquidityBeforeBurn/2**64 - premiumOwedToPosition
1913: 		                    // G: total gross premium (- premiumOwedToPosition)
1914: 		                    // T: totalLiquidityBeforeMint
1915: 		                    // R: positionLiquidity
1916: 		                    // C: current grossPremium value
1917: 		                    // L: current grossPremiumLast value
1918: 		                    // Ln: updated grossPremiumLast value
1919: 		                    // T * (C - L) = G
1920: 		                    // (T - R) * (C - Ln) = G - P
1921: 		                    //
1922: 		                    // T * (C - L) = (T - R) * (C - Ln) + P
1923: 		                    // (TC - TL - P) / (T - R) = C - Ln
1924: 		                    // Ln = C - (TC - TL - P) / (T - R)
1925: 		                    // Ln = (TC - CR - TC + LT + P) / (T-R)
1926: 		                    // Ln = (LT - CR + P) / (T-R)
1927: 		
1928: 		                    unchecked {
1929: 		                        uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
1930: 		                        uint256 _leg = leg;
1931: 		
1932: 		                        // if there's still liquidity, compute the new grossPremiumLast
1933: 		                        // otherwise, we just reset grossPremiumLast to the current grossPremium
1934: 		                        s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1935: 		                            ? LeftRightUnsigned
1936: 		                                .wrap(0)
1937: 		                                .toRightSlot(
1938: 		                                    uint128(
1939: 		                                        uint256(
1940: 		                                            Math.max(
1941: 		                                                (int256(
1942: 		                                                    grossPremiumLast.rightSlot() *
1943: 		                                                        totalLiquidityBefore
1944: 		                                                ) -
1945: 		                                                    int256(
1946: 		                                                        _premiumAccumulatorsByLeg[_leg][0] *
1947: 		                                                            positionLiquidity
1948: 		                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
1949: 		                                                0
1950: 		                                            )
1951: 		                                        ) / totalLiquidity
1952: 		                                    )
1953: 		                                )
1954: 		                                .toLeftSlot(
1955: 		                                    uint128(
1956: 		                                        uint256(
1957: 		                                            Math.max(
1958: 		                                                (int256(
1959: 		                                                    grossPremiumLast.leftSlot() *
1960: 		                                                        totalLiquidityBefore
1961: 		                                                ) -
1962: 		                                                    int256(
1963: 		                                                        _premiumAccumulatorsByLeg[_leg][1] *
1964: 		                                                            positionLiquidity
1965: 		                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
1966: 		                                                0
1967: 		                                            )
1968: 		                                        ) / totalLiquidity
1969: 		                                    )
1970: 		                                )
1971: 		                            : LeftRightUnsigned
1972: 		                                .wrap(0)
1973: 		                                .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1974: 		                                .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1975: 		                    }
1976: 		                }
1977: 		            }
1978: 		
1979: 		            // update settled tokens in storage with all local deltas
1980: 		            s_settledTokens[chunkKey] = settledTokens;
1981: 		
1982: 		            unchecked {
1983: 		                ++leg;
1984: 		            }
1985: 		        }
1986: 		    }
```
[[860-879](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L860-L879), [1411-1423](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1411-L1423), [1672-1752](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1672-L1752), [1839-1986](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1839-L1986)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

1111: 		    function _updateStoredPremia(
1112: 		        bytes32 positionKey,
1113: 		        LeftRightUnsigned currentLiquidity,
1114: 		        LeftRightUnsigned collectedAmounts //@audit-ok was signed
1115: 		    ) private {
1116: 		        (
1117: 		            LeftRightUnsigned deltaPremiumOwed,
1118: 		            LeftRightUnsigned deltaPremiumGross
1119: 		        ) = _getPremiaDeltas(currentLiquidity, collectedAmounts);
1120: 		
1121: 		        // add deltas to accumulators and freeze both accumulators (for a token) if one of them overflows
1122: 		        // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)
1123: 		        // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing
1124: 		        (s_accountPremiumOwed[positionKey], s_accountPremiumGross[positionKey]) = LeftRightLibrary
1125: 		            .addCapped( //@audit-ok wasn't capped, but both were 256, they are unsigned now
1126: 		                s_accountPremiumOwed[positionKey],
1127: 		                deltaPremiumOwed,
1128: 		                s_accountPremiumGross[positionKey],
1129: 		                deltaPremiumGross
1130: 		            );
1131: 		    }
```
[[1111-1131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1111-L1131)]



```solidity
File: contracts/libraries/PanopticMath.sol

92: 		    function updatePositionsHash(
93: 		        uint256 existingHash,
94: 		        TokenId tokenId,
95: 		        bool addFlag
96: 		    ) internal pure returns (uint256) {
97: 		        // add the XOR`ed hash of the single option position `tokenId` to the `existingHash`
98: 		        // @dev 0 ^ x = x
99: 		
100: 		        unchecked {
101: 		            // update hash by taking the XOR of the new tokenId
102: 		            uint248 updatedHash = uint248(existingHash) ^
103: 		                (uint248(uint256(keccak256(abi.encode(tokenId)))));
104: 		            // increment the top 8 bit if addflag=true, decrement otherwise
105: 		            return
106: 		                addFlag
107: 		                    ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)
108: 		                    : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);
109: 		        }
110: 		    }
```
[[92-110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L92-L110)]



```solidity
File: contracts/types/LiquidityChunk.sol

136: 		    function updateTickLower(
137: 		        LiquidityChunk self,
138: 		        int24 _tickLower
139: 		    ) internal pure returns (LiquidityChunk) {
140: 		        unchecked {
141: 		            return
142: 		                LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TL_MASK).addTickLower(
143: 		                    _tickLower
144: 		                );
145: 		        }
146: 		    }

152: 		    function updateTickUpper(
153: 		        LiquidityChunk self,
154: 		        int24 _tickUpper
155: 		    ) internal pure returns (LiquidityChunk) {
156: 		        unchecked {
157: 		            // convert tick upper to uint24 as explicit conversion from int24 to uint256 is not allowed
158: 		            return
159: 		                LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TU_MASK).addTickUpper(
160: 		                    _tickUpper
161: 		                );
162: 		        }
163: 		    }
```
[[136-146](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L136-L146), [152-163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L152-L163)]

</details>

---

### [N-05] Missing events in initializers

As a best practice, consider emitting an event when the contract is initialized. In this way, it's easy for the user to track the exact point in time when the contract was initialized, by filtering the emitted events.

*There is 1 instance of this issue.*


```solidity
File: contracts/PanopticFactory.sol

135: 		    function initialize(address _owner) public {
```
[[135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L135)]


---

### [N-06] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

*There are 4 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

178: 		    constructor(
```
[[178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L178)]



```solidity
File: contracts/PanopticFactory.sol

116: 		    constructor(
```
[[116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L116)]



```solidity
File: contracts/PanopticPool.sol

281: 		    constructor(SemiFungiblePositionManager _sfpm) {
```
[[281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L281)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

341: 		    constructor(IUniswapV3Factory _factory) {
```
[[341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L341)]


---

### [N-07] Setters should prevent re-setting the same value

Not only is wasteful in terms of gas, but this is especially problematic when an event is emitted and the old and new values set are the same, as listeners might not expect this kind of scenario.

*There are 6 instances of this issue.*


```solidity
File: contracts/PanopticPool.sol

// @audit s_positionBalance, s_options
860: 		    function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

// @audit s_positionsHash
1411: 		    function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {

// @audit s_options, s_settledTokens
1593: 		    function settleLongPremium(

// @audit s_settledTokens, s_grossPremiumLast
1672: 		    function _updateSettlementPostMint(

// @audit s_grossPremiumLast, s_settledTokens
1839: 		    function _updateSettlementPostBurn(
```
[[860](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L860), [1411](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1411), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1593), [1672](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1672), [1839](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1839)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

// @audit isApprovedForAll
81: 		    function setApprovalForAll(address operator, bool approved) public {
```
[[81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L81)]


---

### [N-08] Using zero as a parameter

Taking zero as a valid argument without checks can lead to severe security issues in some cases.

If using a zero argument is mandatory, consider using descriptive constants or an enum instead of passing zero directly on function calls, as that might be error-prone, to fully describe the caller's intention.

*There are 63 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

712: 		                        LeftRightSigned
713: 		                            .wrap(0)
```
[[712-713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L712-L713)]



```solidity
File: contracts/PanopticPool.sol

635: 		            revert Errors.InvalidTokenIdParameter(0);

655: 		        s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
656: 		            .wrap(0)

763: 		                s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
764: 		                    .wrap(0)

862: 		        s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

871: 		            s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);

894: 		        _validatePositionList(user, positionIdList, 0);

1024: 		        _validatePositionList(liquidatee, positionIdList, 0);

1154: 		        _validatePositionList(msg.sender, positionIdListLiquidator, 0);

1166: 		        LeftRightSigned bonusAmounts = LeftRightSigned
1167: 		            .wrap(0)

1192: 		        _validatePositionList(msg.sender, positionIdListExercisor, 0);

1233: 		        _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

1551: 		                    premiaByLeg[leg] = LeftRightSigned
1552: 		                        .wrap(0)

1573: 		                        premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

1598: 		        _validatePositionList(owner, positionIdList, 0);

1620: 		            accumulatedPremium = LeftRightUnsigned
1621: 		                .wrap(0)

1639: 		            LeftRightSigned realizedPremia = LeftRightSigned
1640: 		                .wrap(0)

1645: 		            s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1646: 		            s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

1713: 		                (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1714: 		                    address(s_univ3pool),
1715: 		                    address(this),
1716: 		                    tokenId.tokenType(leg),
1717: 		                    liquidityChunk.tickLower(),
1718: 		                    liquidityChunk.tickUpper(),
1719: 		                    type(int24).max,
1720: 		                    0
1721: 		                );

1731: 		                    s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1732: 		                        .wrap(0)

1780: 		                LeftRightUnsigned
1781: 		                    .wrap(0)

1935: 		                            ? LeftRightUnsigned
1936: 		                                .wrap(0)

1940: 		                                            Math.max(
1941: 		                                                (int256(
1942: 		                                                    grossPremiumLast.rightSlot() *
1943: 		                                                        totalLiquidityBefore
1944: 		                                                ) -
1945: 		                                                    int256(
1946: 		                                                        _premiumAccumulatorsByLeg[_leg][0] *
1947: 		                                                            positionLiquidity
1948: 		                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
1949: 		                                                0
1950: 		                                            )

1957: 		                                            Math.max(
1958: 		                                                (int256(
1959: 		                                                    grossPremiumLast.leftSlot() *
1960: 		                                                        totalLiquidityBefore
1961: 		                                                ) -
1962: 		                                                    int256(
1963: 		                                                        _premiumAccumulatorsByLeg[_leg][1] *
1964: 		                                                            positionLiquidity
1965: 		                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
1966: 		                                                0
1967: 		                                            )

1971: 		                            : LeftRightUnsigned
1972: 		                                .wrap(0)
```
[[635](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L635), [655-656](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L655-L656), [763-764](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L763-L764), [862](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L862), [871](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L871), [894](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L894), [1024](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1024), [1154](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1154), [1166-1167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1166-L1167), [1192](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1192), [1233](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1233), [1551-1552](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1551-L1552), [1573](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1573), [1598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1598), [1620-1621](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1620-L1621), [1639-1640](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1639-L1640), [1645](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1645), [1646](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1646), [1713-1721](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1713-L1721), [1731-1732](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1731-L1732), [1780-1781](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1780-L1781), [1935-1936](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1935-L1936), [1940-1950](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1940-L1950), [1957-1967](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1957-L1967), [1971-1972](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1971-L1972)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

646: 		            s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

649: 		            s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

834: 		            if (swapAmount == 0) return LeftRightSigned.wrap(0);

849: 		            totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(

1039: 		            s_accountLiquidity[positionKey] = LeftRightUnsigned
1040: 		                .wrap(0)

1167: 		            ? LeftRightSigned
1168: 		                .wrap(0)

1175: 		            : LeftRightSigned
1176: 		                .wrap(0)

1215: 		        movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

1242: 		            movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

1307: 		            collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(

1377: 		                    deltaPremiumOwed = LeftRightUnsigned
1378: 		                        .wrap(0)

1401: 		                    deltaPremiumGross = LeftRightUnsigned
1402: 		                        .wrap(0)
```
[[646](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L646), [649](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L649), [834](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L834), [849](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L849), [1039-1040](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1039-L1040), [1167-1168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1167-L1168), [1175-1176](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1175-L1176), [1215](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1215), [1242](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1242), [1307](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1307), [1377-1378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1377-L1378), [1401-1402](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1401-L1402)]



```solidity
File: contracts/libraries/FeesCalc.sol

115: 		            LeftRightSigned
116: 		                .wrap(0)
```
[[115-116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L115-L116)]



```solidity
File: contracts/libraries/Math.sol

778: 		            quickSort(data, int256(0), int256(data.length - 1));
```
[[778](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L778)]



```solidity
File: contracts/libraries/PanopticMath.sol

598: 		        return LeftRightUnsigned.wrap(0).toRightSlot(amount0).toLeftSlot(amount1);

671: 		                (uint256 balanceCross, uint256 thresholdCross) = PanopticMath.convertCollateralData(
672: 		                    tokenData0,
673: 		                    tokenData1,
674: 		                    0,
675: 		                    sqrtPriceX96Twap
676: 		                );

694: 		                Math.max(premia.rightSlot(), 0);

696: 		                Math.max(premia.leftSlot(), 0);

749: 		                LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(

791: 		            int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);

792: 		            int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

856: 		                if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857: 		                if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

880: 		                                tokenId.strike(0),

881: 		                                tokenId.width(0),

882: 		                                tokenId.tokenType(0)

888: 		                        settled0 = Math.max(
889: 		                            0,
890: 		                            uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891: 		                        );

892: 		                        settled1 = Math.max(
893: 		                            0,
894: 		                            uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895: 		                        );

898: 		                            LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(

933: 		                    LeftRightSigned
934: 		                        .wrap(0)

951: 		                    LeftRightSigned
952: 		                        .wrap(0)
```
[[598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L598), [671-676](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L671-L676), [694](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L694), [696](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L696), [749](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L749), [791](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L791), [792](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L792), [856](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L857), [880](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L880), [881](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L881), [882](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L882), [888-891](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L888-L891), [892-895](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L892-L895), [898](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L898), [933-934](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L933-L934), [951-952](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L951-L952)]



```solidity
File: contracts/types/LeftRight.sol

265: 		                z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

266: 		                    int128(Math.max(left128, 0))

294: 		            LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(

297: 		            LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(
```
[[265](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L265), [266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L266), [294](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L294), [297](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L297)]



```solidity
File: contracts/types/TokenId.sol

406: 		            return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

501: 		        if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);
```
[[406](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L406), [501](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L501)]

</details>

---

### [N-09] Unused named `return`

Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment.

This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

*There are 20 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

361: 		    function asset() external view returns (address assetTokenAddress) {
362: 		        return s_underlyingToken;

370: 		    function totalAssets() public view returns (uint256 totalManagedAssets) {

372: 		            return s_poolAssets + s_inAMM;

379: 		    function convertToShares(uint256 assets) public view returns (uint256 shares) {
380: 		        return Math.mulDiv(assets, totalSupply, totalAssets());

386: 		    function convertToAssets(uint256 shares) public view returns (uint256 assets) {
387: 		        return Math.mulDiv(shares, totalAssets(), totalSupply);

392: 		    function maxDeposit(address) external pure returns (uint256 maxAssets) {
393: 		        return type(uint104).max;

444: 		    function maxMint(address) external view returns (uint256 maxShares) {

446: 		            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

507: 		    function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

512: 		        return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

518: 		    function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

521: 		        return Math.mulDivRoundingUp(assets, supply, totalAssets());

572: 		    function maxRedeem(address owner) public view returns (uint256 maxShares) {

575: 		        return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

581: 		    function previewRedeem(uint256 shares) public view returns (uint256 assets) {
582: 		        return convertToAssets(shares);

741: 		    function _poolUtilization() internal view returns (int256 poolUtilization) {

743: 		            return int256((s_inAMM * DECIMALS) / totalAssets());

753: 		    ) internal view returns (uint256 sellCollateralRatio) {

785: 		            return min_sell_ratio;

791: 		            return DECIMALS;

795: 		            return
796: 		                min_sell_ratio +
797: 		                ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798: 		                (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);

808: 		    ) internal view returns (uint256 buyCollateralRatio) {

836: 		            return BUYER_COLLATERAL_RATIO;

843: 		                return BUYER_COLLATERAL_RATIO / 2;

848: 		            return
849: 		                (BUYER_COLLATERAL_RATIO +
850: 		                    (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851: 		                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

1284: 		    ) internal view returns (uint256 required) {
1285: 		        return
1286: 		            tokenId.riskPartner(index) == index // does this leg have a risk partner? Affects required collateral
1287: 		                ? _getRequiredCollateralSingleLegNoPartner(
1288: 		                    tokenId,
1289: 		                    index,
1290: 		                    positionSize,
1291: 		                    atTick,
1292: 		                    poolUtilization
1293: 		                )
1294: 		                : _getRequiredCollateralSingleLegPartner(
1295: 		                    tokenId,
1296: 		                    index,
1297: 		                    positionSize,
1298: 		                    atTick,
1299: 		                    poolUtilization
1300: 		                );
```
[[361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L370), [379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L444), [507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L507), [518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L518), [572](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L581), [741](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L741), [753](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L753), [808](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L808), [1284](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1284)]



```solidity
File: contracts/PanopticPool.sol

386: 		    ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

400: 		        return (premia.rightSlot(), premia.leftSlot(), balances);

1437: 		    function collateralToken0() external view returns (CollateralTracker collateralToken) {
1438: 		        return s_collateralToken0;

1519: 		            LeftRightSigned[4] memory premiaByLeg,
```
[[386](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L386), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1437), [1519](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1519)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

872: 		            LeftRightSigned totalMoved,

1558: 		    ) external view returns (IUniswapV3Pool UniswapV3Pool) {
1559: 		        return s_poolContext[poolId].pool;
```
[[872](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L872), [1558](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1558)]



```solidity
File: contracts/libraries/Math.sol

738: 		    function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
```
[[738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L738)]

</details>

---

### [N-10] Unused `error` definition

The following errors are never used, consider to remove them.

*There are 2 instances of this issue.*


```solidity
File: contracts/libraries/Errors.sol

26: 		    error ExerciseeNotSolvent();

48: 		    error LeftRightInputError();
```
[[26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L26), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L48)]


---

### [N-11] Unused arguments should be removed or implemented

Some arguments are never used: if this is intentional, consider removing these arguments from the function. Otherwise, implement the missing logic accordingly.

*There are 8 instances of this issue.*


```solidity
File: contracts/libraries/Math.sol

// @audit a, b
340: 		    function mulDiv(
341: 		        uint256 a,
342: 		        uint256 b,
343: 		        uint256 denominator

// @audit a, b
458: 		    function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

// @audit a, b
521: 		    function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

// @audit a, b
598: 		    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

// @audit a, b
675: 		    function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

// @audit a, b
738: 		    function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
```
[[340-343](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L340-L343), [458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L521), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L598), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L675), [738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L738)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

// @audit token, from, to, amount
22: 		    function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

// @audit token, to, amount
53: 		    function safeTransfer(address token, address to, uint256 amount) internal {
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L22), [53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L53)]


---

### [N-12] Unused state variables

Consider removing any unusued state variable to improve the readability of the codebase.

*There are 2 instances of this issue.*


```solidity
File: contracts/libraries/Math.sol

15: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```
[[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L15)]



```solidity
File: contracts/libraries/PanopticMath.sol

23: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```
[[23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L23)]


---

### [N-13] OpenZeppelin libraries should be upgraded to a newer version

These contracts import some OpenZeppelin libraries, but they are using an old version.

*There are 5 instances of this issue.*


```solidity
File: contracts/PanopticFactory.sol

14: 		import {Clones} from "@openzeppelin/contracts/proxy/Clones.sol";
```
[[14](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L14)]



```solidity
File: contracts/PanopticPool.sol

9: 		import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```
[[9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L9)]



```solidity
File: contracts/libraries/InteractionHelper.sol

6: 		import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

10: 		import {Strings} from "@openzeppelin/contracts/utils/Strings.sol";
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L6), [10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L10)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

5: 		import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```
[[5](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L5)]


---

### [N-14] Same `constant` is redefined elsewhere

Keeping the same constants in different files may cause some problems, as the values could become out of sync when only one location is updated; reading constants from a single file is preferable. This should also be preferred for gas optimizations.

*There are 4 instances of this issue.*


```solidity
File: contracts/PanopticFactory.sol

// @audit seen in contracts/PanopticPool.sol
67: 		    SemiFungiblePositionManager internal immutable SFPM;
```
[[67](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L67)]



```solidity
File: contracts/PanopticPool.sol

// @audit seen in contracts/PanopticFactory.sol
180: 		    SemiFungiblePositionManager internal immutable SFPM;
```
[[180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L180)]



```solidity
File: contracts/libraries/Math.sol

// @audit seen in contracts/libraries/PanopticMath.sol
15: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```
[[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L15)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit seen in contracts/libraries/Math.sol
23: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```
[[23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L23)]


---

### [N-15] Enum values should be used in place of constant array indexes

Consider using an enum instead of hardcoding an index access to make the code easier to understand.

*There are 26 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

1210: 		            TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);

1213: 		            uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();

1216: 		            uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();
```
[[1210](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1210), [1213](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1213), [1216](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1216)]



```solidity
File: contracts/PanopticPool.sol

445: 		            balances[k][0] = TokenId.unwrap(tokenId);

446: 		            balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);

453: 		                    LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),

1194: 		        uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();

1199: 		            .computeExercisedAmounts(touchedId[0], positionBalance);

1225: 		        touchedId[0].validateIsExercisable(twapTick);

1240: 		            touchedId[0],

1283: 		        emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

1534: 		                (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM

1534: 		                (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM

1556: 		                                    ((premiumAccumulatorsByLeg[leg][0] -

1565: 		                                    ((premiumAccumulatorsByLeg[leg][1] -

1713: 		                (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(

1713: 		                (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(

1735: 		                                (grossCurrent[0] *

1743: 		                                (grossCurrent[1] *

1774: 		            uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *

1776: 		            uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *

1946: 		                                                        _premiumAccumulatorsByLeg[_leg][0] *

1963: 		                                                        _premiumAccumulatorsByLeg[_leg][1] *

1973: 		                                .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))

1974: 		                                .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
```
[[445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L445), [446](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L446), [453](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L453), [1194](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1194), [1199](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1199), [1225](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1225), [1240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1240), [1283](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1283), [1534](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1534), [1534](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1534), [1556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1556), [1565](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1565), [1713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1713), [1713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1713), [1735](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1735), [1743](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1743), [1774](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1774), [1776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1776), [1946](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1946), [1963](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1963), [1973](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1973), [1974](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1974)]



```solidity
File: contracts/libraries/PanopticMath.sol

266: 		            return int24(sortedTicks[10]); //@audit-issue L - median should be (sortedTicks[9] + sortedTicks[10]) / 2
```
[[266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L266)]

</details>

---

### [N-16] Variable initialization with zero value

It's not necessary to initialize a variable with a zero value, as it's the default behaviour, and it's actually worse in gas terms as it adds an overhead.

*There are 31 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

662: 		            for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

1208: 		        for (uint256 i = 0; i < totalIterations; ) {

1255: 		            for (uint256 index = 0; index < numLegs; ++index) {
```
[[662](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L662), [1208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1208), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1255)]



```solidity
File: contracts/PanopticPool.sol

442: 		        for (uint256 k = 0; k < pLength; ) { //@audit H - uncapped positions -> unliquidable

460: 		            for (uint256 leg = 0; leg < numLegs; ) {

746: 		        for (uint256 leg = 0; leg < numLegs; ) {

803: 		        for (uint256 i = 0; i < positionIdList.length; ) {

865: 		        for (uint256 leg = 0; leg < numLegs; ) {

1388: 		        for (uint256 i = 0; i < pLength; ) {

1524: 		        for (uint256 leg = 0; leg < numLegs; ) {

1678: 		        for (uint256 leg = 0; leg < numLegs; ++leg) {

1858: 		        for (uint256 leg = 0; leg < numLegs; ) {
```
[[442](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L442), [460](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L460), [746](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L746), [803](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L803), [865](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L865), [1388](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1388), [1524](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1524), [1678](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1678), [1858](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1858)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

575: 		        for (uint256 i = 0; i < ids.length; ) {

601: 		        for (uint256 leg = 0; leg < numLegs; ) {

883: 		        for (uint256 leg = 0; leg < numLegs; ) {
```
[[575](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L575), [601](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L601), [883](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L883)]



```solidity
File: contracts/libraries/FeesCalc.sol

51: 		        for (uint256 k = 0; k < positionIdList.length; ) {

55: 		            for (uint256 leg = 0; leg < numLegs; ) {
```
[[51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L51), [55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L55)]



```solidity
File: contracts/libraries/PanopticMath.sol

137: 		            for (uint256 i = 0; i < cardinality + 1; ++i) {

148: 		            for (uint256 i = 0; i < cardinality; ++i) {

248: 		            for (uint256 i = 0; i < 20; ++i) {

256: 		            for (uint256 i = 0; i < 19; ++i) {

395: 		        for (uint256 leg = 0; leg < numLegs; ) {

781: 		            for (uint256 i = 0; i < positionIdList.length; ++i) {

784: 		                for (uint256 leg = 0; leg < numLegs; ++leg) {

860: 		            for (uint256 i = 0; i < positionIdList.length; i++) {

863: 		                for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
```
[[137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L137), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L148), [248](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L248), [256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L256), [395](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L395), [781](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L781), [784](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L784), [860](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L860), [863](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L863)]



```solidity
File: contracts/multicall/Multicall.sol

14: 		        for (uint256 i = 0; i < data.length; ) {
```
[[14](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L14)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

143: 		        for (uint256 i = 0; i < ids.length; ) {

187: 		            for (uint256 i = 0; i < owners.length; ++i) {
```
[[143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L143), [187](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L187)]



```solidity
File: contracts/types/TokenId.sol

507: 		            for (uint256 i = 0; i < 4; ++i) {

581: 		            for (uint256 i = 0; i < numLegs; ++i) {
```
[[507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L507), [581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L581)]

</details>

---

### [N-17] Duplicated `require/if` statements should be refactored

These statements should be refactored to a separate function, as there are multiple parts of the codebase that use the same logic, to improve the code readability and reduce code duplication.

*There are 5 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

// @audit this if condition is duplicated on line 480
418: 		        if (assets > type(uint104).max) revert Errors.DepositTooLarge();
```
[[418](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L418)]



```solidity
File: contracts/libraries/Math.sol

// @audit this require is duplicated on line 588, 665
448: 		                require(result < type(uint256).max);
```
[[448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L448)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

// @audit this if condition is duplicated on line 76
46: 		        if (!success) revert Errors.TransferFailed();
```
[[46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L46)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

// @audit this if condition is duplicated on line 137
101: 		        if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
```
[[101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L101)]



```solidity
File: contracts/types/LeftRight.sol

// @audit this if condition is duplicated on line 240, 262
222: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
```
[[222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L222)]


---

### [N-18] Inconsistent usage of `require`/`error`

Some parts of the codebase use `require` statements, while others use custom `error`s. Consider refactoring the code to use the same approach: the following findings represent the minority of `require` vs `error`, and they show the first occurance in each file, for brevity.

*There is 1 instance of this issue.*


```solidity
File: contracts/libraries/Math.sol

361: 		                require(denominator > 0);
```
[[361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L361)]


---

### [N-19] Some functions contain the same exact logic

These functions might be a problem if the logic changes before the contract is deployed, as the developer must remember to syncronize the logic between all the function instances.

Consider using a single function instead of duplicating the code, for example by using a `library`, or through inheritance.

*There are 2 instances of this issue.*


```solidity
File: contracts/libraries/Math.sol

// @audit duplicated logic in contracts/libraries/Math.sol -> min24, contracts/libraries/Math.sol -> min, contracts/libraries/Math.sol -> min
25: 		    function min24(int24 a, int24 b) internal pure returns (int24) {

// @audit duplicated logic in contracts/libraries/Math.sol -> max24, contracts/libraries/Math.sol -> max, contracts/libraries/Math.sol -> max
33: 		    function max24(int24 a, int24 b) internal pure returns (int24) {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L33)]


---

### [N-20] Unbounded loop may run out of gas

Consider limiting the number of iterations in loops with an explicit revert reason to avoid iterating an array that is too large.

The function would eventually revert if out of gas anyway, but by limiting it the user avoids wasting too much gas, as the loop doesn't execute if an excessive value is provided.

*There are 34 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

662: 		            for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {
663: 		                // short legs are not counted - exercise is intended to be based on long legs
664: 		                if (positionId.isLong(leg) == 0) continue;
665: 		
666: 		                {
667: 		                    int24 range = int24(
668: 		                        int256(
669: 		                            Math.unsafeDivRoundingUp(
670: 		                                uint24(positionId.width(leg) * positionId.tickSpacing()),
671: 		                                2
672: 		                            )
673: 		                        )
674: 		                    );
675: 		                    maxNumRangesFromStrike = Math.max(
676: 		                        maxNumRangesFromStrike,
677: 		                        uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
678: 		                    );
679: 		                }
680: 		
681: 		                uint256 currentValue0;
682: 		                uint256 currentValue1;
683: 		                uint256 oracleValue0;
684: 		                uint256 oracleValue1;
685: 		
686: 		                {
687: 		                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
688: 		                        positionId,
689: 		                        leg,
690: 		                        positionBalance
691: 		                    );
692: 		
693: 		                    (currentValue0, currentValue1) = Math.getAmountsForLiquidity(
694: 		                        currentTick,
695: 		                        liquidityChunk
696: 		                    );
697: 		
698: 		                    (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(
699: 		                        oracleTick,
700: 		                        liquidityChunk
701: 		                    );
702: 		                }
703: 		
704: 		                uint256 tokenType = positionId.tokenType(leg);
705: 		                // compensate user for loss in value if chunk has lost money between current and median tick
706: 		                // note: the delta for one token will be positive and the other will be negative. This cancels out any moves in their positions
707: 		                if (
708: 		                    (tokenType == 0 && currentValue1 < oracleValue1) ||
709: 		                    (tokenType == 1 && currentValue0 < oracleValue0)
710: 		                )
711: 		                    exerciseFees = exerciseFees.sub(
712: 		                        LeftRightSigned
713: 		                            .wrap(0)
714: 		                            .toRightSlot(
715: 		                                int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
716: 		                            )
717: 		                            .toLeftSlot(
718: 		                                int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
719: 		                            )
720: 		                    );
721: 		            }

1208: 		        for (uint256 i = 0; i < totalIterations; ) {
1209: 		            // read the ith tokenId from the account
1210: 		            TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);
1211: 		
1212: 		            // read the position size and the pool utilization at mint
1213: 		            uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();
1214: 		
1215: 		            // read the pool utilization at mint
1216: 		            uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();
1217: 		
1218: 		            // Get tokens required for the current tokenId (a single active position)
1219: 		            uint256 _tokenRequired = _getRequiredCollateralAtTickSinglePosition(
1220: 		                tokenId,
1221: 		                positionSize,
1222: 		                atTick,
1223: 		                poolUtilization
1224: 		            );
1225: 		
1226: 		            // add to the tokenRequired accumulator
1227: 		            unchecked {
1228: 		                tokenRequired += _tokenRequired;
1229: 		            }
1230: 		            unchecked {
1231: 		                ++i;
1232: 		            }
1233: 		        }

1255: 		            for (uint256 index = 0; index < numLegs; ++index) {
1256: 		                // revert if the tokenType does not match the current collateral token
1257: 		                if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;
1258: 		                // Increment the tokenRequired accumulator
1259: 		                tokenRequired += _getRequiredCollateralSingleLeg(
1260: 		                    tokenId,
1261: 		                    index,
1262: 		                    positionSize,
1263: 		                    atTick,
1264: 		                    poolUtilization
1265: 		                );
1266: 		            }
```
[[662-721](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L662-L721), [1208-1233](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1208-L1233), [1255-1266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1255-L1266)]



```solidity
File: contracts/PanopticPool.sol

442: 		        for (uint256 k = 0; k < pLength; ) { //@audit H - uncapped positions -> unliquidable
443: 		            TokenId tokenId = positionIdList[k];
444: 		
445: 		            balances[k][0] = TokenId.unwrap(tokenId);
446: 		            balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);
447: 		
448: 		            (
449: 		                LeftRightSigned[4] memory premiaByLeg, //@audit-info positive premia
450: 		                uint256[2][4] memory premiumAccumulatorsByLeg
451: 		            ) = _getPremia(
452: 		                    tokenId,
453: 		                    LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
454: 		                    c_user,
455: 		                    computeAllPremia,
456: 		                    atTick
457: 		                );
458: 		
459: 		            uint256 numLegs = tokenId.countLegs();
460: 		            for (uint256 leg = 0; leg < numLegs; ) {
461: 		                if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
462: 		                    bytes32 chunkKey = keccak256(
463: 		                        abi.encodePacked(
464: 		                            tokenId.strike(leg),
465: 		                            tokenId.width(leg),
466: 		                            tokenId.tokenType(leg)
467: 		                        ) //@audit-info collision between two legs? (isLong or riskPartner)
468: 		                    );
469: 		
470: 		                    LeftRightUnsigned availablePremium = _getAvailablePremium(
471: 		                        _getTotalLiquidity(tokenId, leg),
472: 		                        s_settledTokens[chunkKey],
473: 		                        s_grossPremiumLast[chunkKey],
474: 		                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
475: 		                        premiumAccumulatorsByLeg[leg]
476: 		                    );
477: 		                    portfolioPremium = portfolioPremium.add(
478: 		                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
479: 		                    );
480: 		                } else {
481: 		                    portfolioPremium = portfolioPremium.add(premiaByLeg[leg]); //@audit-info adds it if is long or includePendingPremium = true
482: 		                }
483: 		                unchecked {
484: 		                    ++leg;
485: 		                }
486: 		            }
487: 		
488: 		            unchecked {
489: 		                ++k;
490: 		            }
491: 		        }

460: 		            for (uint256 leg = 0; leg < numLegs; ) {
461: 		                if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
462: 		                    bytes32 chunkKey = keccak256(
463: 		                        abi.encodePacked(
464: 		                            tokenId.strike(leg),
465: 		                            tokenId.width(leg),
466: 		                            tokenId.tokenType(leg)
467: 		                        ) //@audit-info collision between two legs? (isLong or riskPartner)
468: 		                    );
469: 		
470: 		                    LeftRightUnsigned availablePremium = _getAvailablePremium(
471: 		                        _getTotalLiquidity(tokenId, leg),
472: 		                        s_settledTokens[chunkKey],
473: 		                        s_grossPremiumLast[chunkKey],
474: 		                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
475: 		                        premiumAccumulatorsByLeg[leg]
476: 		                    );
477: 		                    portfolioPremium = portfolioPremium.add(
478: 		                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
479: 		                    );
480: 		                } else {
481: 		                    portfolioPremium = portfolioPremium.add(premiaByLeg[leg]); //@audit-info adds it if is long or includePendingPremium = true
482: 		                }
483: 		                unchecked {
484: 		                    ++leg;
485: 		                }
486: 		            }

746: 		        for (uint256 leg = 0; leg < numLegs; ) {
747: 		            // Extract base fee (AMM swap/trading fees) for the position and add it to s_options
748: 		            // (ie. the (feeGrowth * liquidity) / 2**128 for each token)
749: 		            (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
750: 		            uint256 isLong = tokenId.isLong(leg);
751: 		            {
752: 		                (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
753: 		                    address(s_univ3pool),
754: 		                    address(this),
755: 		                    tokenId.tokenType(leg),
756: 		                    tickLower,
757: 		                    tickUpper,
758: 		                    type(int24).max,
759: 		                    isLong
760: 		                );
761: 		
762: 		                // update the premium accumulators
763: 		                s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
764: 		                    .wrap(0)
765: 		                    .toRightSlot(premiumAccumulator0)
766: 		                    .toLeftSlot(premiumAccumulator1);
767: 		            }
768: 		            // verify base Liquidity limit only if new position is long
769: 		            if (isLong == 1) {
770: 		                // Move this into a new function
771: 		                _checkLiquiditySpread(
772: 		                    tokenId,
773: 		                    leg,
774: 		                    tickLower,
775: 		                    tickUpper,
776: 		                    uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))
777: 		                );
778: 		            }
779: 		            unchecked {
780: 		                ++leg;
781: 		            }
782: 		        }

803: 		        for (uint256 i = 0; i < positionIdList.length; ) {
804: 		            LeftRightSigned paidAmounts;
805: 		            (paidAmounts, premiasByLeg[i]) = _burnOptions(
806: 		                commitLongSettled,
807: 		                positionIdList[i],
808: 		                owner,
809: 		                tickLimitLow,
810: 		                tickLimitHigh
811: 		            );
812: 		            netPaid = netPaid.add(paidAmounts);
813: 		            unchecked {
814: 		                ++i;
815: 		            }
816: 		        }

865: 		        for (uint256 leg = 0; leg < numLegs; ) {
866: 		            if (tokenId.isLong(leg) == 0) {
867: 		                // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
868: 		                (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
869: 		                _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
870: 		            }
871: 		            s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
872: 		            unchecked {
873: 		                ++leg;
874: 		            }
875: 		        }

1388: 		        for (uint256 i = 0; i < pLength; ) {
1389: 		            fingerprintIncomingList = PanopticMath.updatePositionsHash(
1390: 		                fingerprintIncomingList,
1391: 		                positionIdList[i],
1392: 		                ADD
1393: 		            );
1394: 		            unchecked {
1395: 		                ++i;
1396: 		            }
1397: 		        }

1524: 		        for (uint256 leg = 0; leg < numLegs; ) {
1525: 		            uint256 isLong = tokenId.isLong(leg);
1526: 		            if ((isLong == 1) || computeAllPremia) {
1527: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1528: 		                    tokenId,
1529: 		                    leg,
1530: 		                    positionSize
1531: 		                );
1532: 		                uint256 tokenType = tokenId.tokenType(leg);
1533: 		
1534: 		                (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM
1535: 		                    .getAccountPremium(
1536: 		                        address(s_univ3pool),
1537: 		                        address(this),
1538: 		                        tokenType,
1539: 		                        liquidityChunk.tickLower(),
1540: 		                        liquidityChunk.tickUpper(),
1541: 		                        atTick,
1542: 		                        isLong
1543: 		                    );
1544: 		
1545: 		                unchecked {
1546: 		                    LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];
1547: 		
1548: 		                    // if the premium accumulatorLast is higher than current, it means the premium accumulator has overflowed and rolled over at least once
1549: 		                    // we can account for one rollover by doing (acc_cur + (acc_max - acc_last))
1550: 		                    // if there are multiple rollovers or the rollover goes past the last accumulator, rolled over fees will just remain unclaimed
1551: 		                    premiaByLeg[leg] = LeftRightSigned
1552: 		                        .wrap(0)
1553: 		                        .toRightSlot(
1554: 		                            int128(
1555: 		                                int256(
1556: 		                                    ((premiumAccumulatorsByLeg[leg][0] -
1557: 		                                        premiumAccumulatorLast.rightSlot()) *
1558: 		                                        (liquidityChunk.liquidity())) / 2 ** 64
1559: 		                                )
1560: 		                            )
1561: 		                        )
1562: 		                        .toLeftSlot(
1563: 		                            int128(
1564: 		                                int256(
1565: 		                                    ((premiumAccumulatorsByLeg[leg][1] -
1566: 		                                        premiumAccumulatorLast.leftSlot()) *
1567: 		                                        (liquidityChunk.liquidity())) / 2 ** 64
1568: 		                                )
1569: 		                            )
1570: 		                        );
1571: 		
1572: 		                    if (isLong == 1) {
1573: 		                        premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);
1574: 		                    }
1575: 		                }
1576: 		            }
1577: 		            unchecked {
1578: 		                ++leg;
1579: 		            }
1580: 		        }

1678: 		        for (uint256 leg = 0; leg < numLegs; ++leg) {
1679: 		            bytes32 chunkKey = keccak256(
1680: 		                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1681: 		            );
1682: 		            // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers
1683: 		            s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1684: 		
1685: 		            if (tokenId.isLong(leg) == 0) {
1686: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1687: 		                    tokenId,
1688: 		                    leg,
1689: 		                    positionSize
1690: 		                );
1691: 		
1692: 		                // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (R + N)
1693: 		                uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1694: 		
1695: 		                // We need to adjust the grossPremiumLast value such that the result of
1696: 		                // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64
1697: 		                // G: total gross premium
1698: 		                // T: totalLiquidityBeforeMint
1699: 		                // R: positionLiquidity
1700: 		                // C: current grossPremium value
1701: 		                // L: current grossPremiumLast value
1702: 		                // Ln: updated grossPremiumLast value
1703: 		                // T * (C - L) = G
1704: 		                // (T + R) * (C - Ln) = G
1705: 		                //
1706: 		                // T * (C - L) = (T + R) * (C - Ln)
1707: 		                // (TC - TL) / (T + R) = C - Ln
1708: 		                // Ln = C - (TC - TL)/(T + R)
1709: 		                // Ln = (CT + CR - TC + TL)/(T+R)
1710: 		                // Ln = (CR + TL)/(T+R)
1711: 		
1712: 		                uint256[2] memory grossCurrent;
1713: 		                (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1714: 		                    address(s_univ3pool),
1715: 		                    address(this),
1716: 		                    tokenId.tokenType(leg),
1717: 		                    liquidityChunk.tickLower(),
1718: 		                    liquidityChunk.tickUpper(),
1719: 		                    type(int24).max,
1720: 		                    0
1721: 		                );
1722: 		
1723: 		                unchecked {
1724: 		                    // L
1725: 		                    LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1726: 		                    // R
1727: 		                    uint256 positionLiquidity = liquidityChunk.liquidity();
1728: 		                    // T (totalLiquidity is (T + R) after minting)
1729: 		                    uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
1730: 		
1731: 		                    s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1732: 		                        .wrap(0)
1733: 		                        .toRightSlot(
1734: 		                            uint128(
1735: 		                                (grossCurrent[0] *
1736: 		                                    positionLiquidity +
1737: 		                                    grossPremiumLast.rightSlot() *
1738: 		                                    totalLiquidityBefore) / (totalLiquidity)
1739: 		                            )
1740: 		                        )
1741: 		                        .toLeftSlot(
1742: 		                            uint128(
1743: 		                                (grossCurrent[1] *
1744: 		                                    positionLiquidity +
1745: 		                                    grossPremiumLast.leftSlot() *
1746: 		                                    totalLiquidityBefore) / (totalLiquidity)
1747: 		                            )
1748: 		                        );
1749: 		                }
1750: 		            }
1751: 		        }

1858: 		        for (uint256 leg = 0; leg < numLegs; ) {
1859: 		            LeftRightSigned legPremia = premiaByLeg[leg];
1860: 		
1861: 		            bytes32 chunkKey = keccak256(
1862: 		                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1863: 		            );
1864: 		
1865: 		            // collected from Uniswap
1866: 		            LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1867: 		
1868: 		            if (LeftRightSigned.unwrap(legPremia) != 0) {
1869: 		                // (will be) paid by long legs
1870: 		                if (tokenId.isLong(leg) == 1) {
1871: 		                    if (commitLongSettled)
1872: 		                        settledTokens = LeftRightUnsigned.wrap(
1873: 		                            uint256(
1874: 		                                LeftRightSigned.unwrap(
1875: 		                                    LeftRightSigned
1876: 		                                        .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1877: 		                                        .sub(legPremia)
1878: 		                                )
1879: 		                            )
1880: 		                        );
1881: 		                    realizedPremia = realizedPremia.add(legPremia);
1882: 		                } else {
1883: 		                    uint256 positionLiquidity = PanopticMath
1884: 		                        .getLiquidityChunk(tokenId, leg, positionSize)
1885: 		                        .liquidity();
1886: 		
1887: 		                    // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (T - R)
1888: 		                    uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1889: 		                    // T (totalLiquidity is (T - R) after burning)
1890: 		                    uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;
1891: 		
1892: 		                    LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1893: 		
1894: 		                    LeftRightUnsigned availablePremium = _getAvailablePremium(
1895: 		                        totalLiquidity + positionLiquidity,
1896: 		                        settledTokens,
1897: 		                        grossPremiumLast,
1898: 		                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
1899: 		                        premiumAccumulatorsByLeg[leg]
1900: 		                    );
1901: 		
1902: 		                    // subtract settled tokens sent to seller
1903: 		                    settledTokens = settledTokens.sub(availablePremium);
1904: 		
1905: 		                    // add available premium to amount that should be settled
1906: 		                    realizedPremia = realizedPremia.add(
1907: 		                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1908: 		                    );
1909: 		
1910: 		                    // We need to adjust the grossPremiumLast value such that the result of
1911: 		                    // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostBurn/2**64 is equal to
1912: 		                    // (grossPremium - grossPremiumLast)*totalLiquidityBeforeBurn/2**64 - premiumOwedToPosition
1913: 		                    // G: total gross premium (- premiumOwedToPosition)
1914: 		                    // T: totalLiquidityBeforeMint
1915: 		                    // R: positionLiquidity
1916: 		                    // C: current grossPremium value
1917: 		                    // L: current grossPremiumLast value
1918: 		                    // Ln: updated grossPremiumLast value
1919: 		                    // T * (C - L) = G
1920: 		                    // (T - R) * (C - Ln) = G - P
1921: 		                    //
1922: 		                    // T * (C - L) = (T - R) * (C - Ln) + P
1923: 		                    // (TC - TL - P) / (T - R) = C - Ln
1924: 		                    // Ln = C - (TC - TL - P) / (T - R)
1925: 		                    // Ln = (TC - CR - TC + LT + P) / (T-R)
1926: 		                    // Ln = (LT - CR + P) / (T-R)
1927: 		
1928: 		                    unchecked {
1929: 		                        uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
1930: 		                        uint256 _leg = leg;
1931: 		
1932: 		                        // if there's still liquidity, compute the new grossPremiumLast
1933: 		                        // otherwise, we just reset grossPremiumLast to the current grossPremium
1934: 		                        s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1935: 		                            ? LeftRightUnsigned
1936: 		                                .wrap(0)
1937: 		                                .toRightSlot(
1938: 		                                    uint128(
1939: 		                                        uint256(
1940: 		                                            Math.max(
1941: 		                                                (int256(
1942: 		                                                    grossPremiumLast.rightSlot() *
1943: 		                                                        totalLiquidityBefore
1944: 		                                                ) -
1945: 		                                                    int256(
1946: 		                                                        _premiumAccumulatorsByLeg[_leg][0] *
1947: 		                                                            positionLiquidity
1948: 		                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
1949: 		                                                0
1950: 		                                            )
1951: 		                                        ) / totalLiquidity
1952: 		                                    )
1953: 		                                )
1954: 		                                .toLeftSlot(
1955: 		                                    uint128(
1956: 		                                        uint256(
1957: 		                                            Math.max(
1958: 		                                                (int256(
1959: 		                                                    grossPremiumLast.leftSlot() *
1960: 		                                                        totalLiquidityBefore
1961: 		                                                ) -
1962: 		                                                    int256(
1963: 		                                                        _premiumAccumulatorsByLeg[_leg][1] *
1964: 		                                                            positionLiquidity
1965: 		                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
1966: 		                                                0
1967: 		                                            )
1968: 		                                        ) / totalLiquidity
1969: 		                                    )
1970: 		                                )
1971: 		                            : LeftRightUnsigned
1972: 		                                .wrap(0)
1973: 		                                .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1974: 		                                .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1975: 		                    }
1976: 		                }
1977: 		            }
1978: 		
1979: 		            // update settled tokens in storage with all local deltas
1980: 		            s_settledTokens[chunkKey] = settledTokens;
1981: 		
1982: 		            unchecked {
1983: 		                ++leg;
1984: 		            }
1985: 		        }
```
[[442-491](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L442-L491), [460-486](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L460-L486), [746-782](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L746-L782), [803-816](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L803-L816), [865-875](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L865-L875), [1388-1397](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1388-L1397), [1524-1580](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1524-L1580), [1678-1751](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1678-L1751), [1858-1985](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1858-L1985)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

575: 		        for (uint256 i = 0; i < ids.length; ) {
576: 		            if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
577: 		            registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
578: 		            unchecked {
579: 		                ++i;
580: 		            }
581: 		        }

601: 		        for (uint256 leg = 0; leg < numLegs; ) {
602: 		            // for this leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
603: 		            // @dev see `contracts/types/LiquidityChunk.sol`
604: 		            LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
605: 		                id,
606: 		                leg,
607: 		                uint128(amount)
608: 		            );
609: 		
610: 		            //construct the positionKey for the from and to addresses
611: 		            bytes32 positionKey_from = keccak256(
612: 		                abi.encodePacked(
613: 		                    address(univ3pool),
614: 		                    from,
615: 		                    id.tokenType(leg),
616: 		                    liquidityChunk.tickLower(),
617: 		                    liquidityChunk.tickUpper()
618: 		                )
619: 		            );
620: 		            bytes32 positionKey_to = keccak256(
621: 		                abi.encodePacked(
622: 		                    address(univ3pool),
623: 		                    to,
624: 		                    id.tokenType(leg),
625: 		                    liquidityChunk.tickLower(),
626: 		                    liquidityChunk.tickUpper()
627: 		                )
628: 		            );
629: 		
630: 		            // Revert if recipient already has that position
631: 		            if (
632: 		                (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
633: 		                (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)
634: 		            ) revert Errors.TransferFailed();
635: 		
636: 		            // Revert if sender has long positions in that chunk or the entire liquidity is not being transferred
637: 		            LeftRightUnsigned fromLiq = s_accountLiquidity[positionKey_from];
638: 		            //@audit-ok before: if (fromLiq.rightSlot() != liquidityChunk.liquidity()) revert Errors.TransferFailed();
639: 		            if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity()) //@audit-ok before it checked only the rightSlot
640: 		                revert Errors.TransferFailed();
641: 		
642: 		            LeftRightSigned fromBase = s_accountFeesBase[positionKey_from];
643: 		
644: 		            //update+store liquidity and fee values between accounts
645: 		            s_accountLiquidity[positionKey_to] = fromLiq;
646: 		            s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);
647: 		
648: 		            s_accountFeesBase[positionKey_to] = fromBase;
649: 		            s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);
650: 		            unchecked {
651: 		                ++leg;
652: 		            }
653: 		        }

883: 		        for (uint256 leg = 0; leg < numLegs; ) {
884: 		            LeftRightSigned _moved;
885: 		            LeftRightSigned _itmAmounts;
886: 		            LeftRightUnsigned _collectedSingleLeg;
887: 		
888: 		            {
889: 		                // cache the univ3pool, tokenId, isBurn, and _positionSize variables to get rid of stack too deep error
890: 		                IUniswapV3Pool _univ3pool = univ3pool;
891: 		                TokenId _tokenId = tokenId;
892: 		                bool _isBurn = isBurn;
893: 		                uint128 _positionSize = positionSize;
894: 		                uint256 _leg;
895: 		
896: 		                unchecked {
897: 		                    // Reverse the order of the legs if this call is burning a position (LIFO)
898: 		                    // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,
899: 		                    // allowing the corresponding short liquidity to be removed
900: 		                    _leg = _isBurn ? numLegs - leg - 1 : leg;
901: 		                }
902: 		
903: 		                // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
904: 		                // @dev see `contracts/types/LiquidityChunk.sol`
905: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
906: 		                    _tokenId,
907: 		                    _leg,
908: 		                    _positionSize
909: 		                );
910: 		
911: 		                (_moved, _itmAmounts, _collectedSingleLeg) = _createLegInAMM(
912: 		                    _univ3pool,
913: 		                    _tokenId,
914: 		                    _leg,
915: 		                    liquidityChunk,
916: 		                    _isBurn
917: 		                );
918: 		
919: 		                collectedByLeg[_leg] = _collectedSingleLeg;
920: 		
921: 		                unchecked {
922: 		                    // increment accumulators of the upper bound on tokens contained across all legs of the position at any given tick
923: 		                    amount0 += Math.getAmount0ForLiquidity(liquidityChunk);
924: 		
925: 		                    amount1 += Math.getAmount1ForLiquidity(liquidityChunk);
926: 		                }
927: 		            }
928: 		
929: 		            totalMoved = totalMoved.add(_moved);
930: 		            itmAmounts = itmAmounts.add(_itmAmounts);
931: 		
932: 		            unchecked {
933: 		                ++leg;
934: 		            }
935: 		        }

372: 		        while (address(s_poolContext[poolId].pool) != address(0)) {
373: 		            poolId = PanopticMath.incrementPoolPattern(poolId);
374: 		        }
```
[[575-581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L575-L581), [601-653](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L601-L653), [883-935](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L883-L935), [372-374](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L372-L374)]



```solidity
File: contracts/libraries/FeesCalc.sol

51: 		        for (uint256 k = 0; k < positionIdList.length; ) {
52: 		            TokenId tokenId = positionIdList[k];
53: 		            uint128 positionSize = userBalance[tokenId].rightSlot();
54: 		            uint256 numLegs = tokenId.countLegs();
55: 		            for (uint256 leg = 0; leg < numLegs; ) {
56: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
57: 		                    tokenId,
58: 		                    leg,
59: 		                    positionSize
60: 		                );
61: 		
62: 		                (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
63: 		                    atTick,
64: 		                    liquidityChunk
65: 		                );
66: 		
67: 		                if (tokenId.isLong(leg) == 0) {
68: 		                    unchecked {
69: 		                        value0 += int256(amount0);
70: 		                        value1 += int256(amount1);
71: 		                    }
72: 		                } else {
73: 		                    unchecked {
74: 		                        value0 -= int256(amount0);
75: 		                        value1 -= int256(amount1);
76: 		                    }
77: 		                }
78: 		
79: 		                unchecked {
80: 		                    ++leg;
81: 		                }
82: 		            }
83: 		            unchecked {
84: 		                ++k;
85: 		            }
86: 		        }

55: 		            for (uint256 leg = 0; leg < numLegs; ) {
56: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
57: 		                    tokenId,
58: 		                    leg,
59: 		                    positionSize
60: 		                );
61: 		
62: 		                (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
63: 		                    atTick,
64: 		                    liquidityChunk
65: 		                );
66: 		
67: 		                if (tokenId.isLong(leg) == 0) {
68: 		                    unchecked {
69: 		                        value0 += int256(amount0);
70: 		                        value1 += int256(amount1);
71: 		                    }
72: 		                } else {
73: 		                    unchecked {
74: 		                        value0 -= int256(amount0);
75: 		                        value1 -= int256(amount1);
76: 		                    }
77: 		                }
78: 		
79: 		                unchecked {
80: 		                    ++leg;
81: 		                }
82: 		            }
```
[[51-86](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L51-L86), [55-82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L55-L82)]



```solidity
File: contracts/libraries/Math.sol

759: 		            while (i < j) {
760: 		                while (arr[uint256(i)] < pivot) i++;
761: 		                while (pivot < arr[uint256(j)]) j--;
762: 		                if (i <= j) {
763: 		                    (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);
764: 		                    i++;
765: 		                    j--;
766: 		                }
767: 		            }

760: 		                while (arr[uint256(i)] < pivot) i++;

761: 		                while (pivot < arr[uint256(j)]) j--;
```
[[759-767](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L759-L767), [760](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L760), [761](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L761)]



```solidity
File: contracts/libraries/PanopticMath.sol

137: 		            for (uint256 i = 0; i < cardinality + 1; ++i) {
138: 		                (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
139: 		                    uint256(
140: 		                        (int256(observationIndex) - int256(i * period)) +
141: 		                            int256(observationCardinality)
142: 		                    ) % observationCardinality
143: 		                );
144: 		            }

148: 		            for (uint256 i = 0; i < cardinality; ++i) {
149: 		                ticks[i] =
150: 		                    (tickCumulatives[i] - tickCumulatives[i + 1]) /
151: 		                    int256(timestamps[i] - timestamps[i + 1]);
152: 		            }

207: 		                for (uint8 i; i < 8; ++i) {
208: 		                    // read the rank from the existing ordering
209: 		                    rank = (orderMap >> (3 * i)) % 8;
210: 		
211: 		                    if (rank == 7) {
212: 		                        shift -= 1;
213: 		                        continue;
214: 		                    }
215: 		
216: 		                    // read the corresponding entry
217: 		                    entry = int24(uint24(medianData >> (rank * 24)));
218: 		                    if ((below) && (lastObservedTick > entry)) {
219: 		                        shift += 1;
220: 		                        below = false;
221: 		                    }
222: 		
223: 		                    newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));
224: 		                }

248: 		            for (uint256 i = 0; i < 20; ++i) {
249: 		                secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);
250: 		            }

256: 		            for (uint256 i = 0; i < 19; ++i) {
257: 		                twapMeasurement[i] = int24(
258: 		                    (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
259: 		                );
260: 		            }

395: 		        for (uint256 leg = 0; leg < numLegs; ) {
396: 		            // Compute the amount of funds that have been removed from the Panoptic Pool
397: 		            (LeftRightSigned longs, LeftRightSigned shorts) = _calculateIOAmounts(
398: 		                tokenId,
399: 		                positionSize,
400: 		                leg
401: 		            );
402: 		
403: 		            longAmounts = longAmounts.add(longs);
404: 		            shortAmounts = shortAmounts.add(shorts);
405: 		
406: 		            unchecked {
407: 		                ++leg;
408: 		            }
409: 		        }

781: 		            for (uint256 i = 0; i < positionIdList.length; ++i) {
782: 		                TokenId tokenId = positionIdList[i];
783: 		                uint256 numLegs = tokenId.countLegs();
784: 		                for (uint256 leg = 0; leg < numLegs; ++leg) {
785: 		                    if (tokenId.isLong(leg) == 1) {
786: 		                        longPremium = longPremium.sub(premiasByLeg[i][leg]);
787: 		                    }
788: 		                }
789: 		            }

784: 		                for (uint256 leg = 0; leg < numLegs; ++leg) {
785: 		                    if (tokenId.isLong(leg) == 1) {
786: 		                        longPremium = longPremium.sub(premiasByLeg[i][leg]);
787: 		                    }
788: 		                }

860: 		            for (uint256 i = 0; i < positionIdList.length; i++) {
861: 		                TokenId tokenId = positionIdList[i];
862: 		                LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
863: 		                for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864: 		                    if (tokenId.isLong(leg) == 1) {
865: 		                        mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
866: 		                            storage _settledTokens = settledTokens;
867: 		
868: 		                        // calculate amounts to revoke from settled and subtract from haircut req
869: 		                        uint256 settled0 = Math.unsafeDivRoundingUp(
870: 		                            uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871: 		                            uint128(longPremium.rightSlot())
872: 		                        );
873: 		                        uint256 settled1 = Math.unsafeDivRoundingUp(
874: 		                            uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875: 		                            uint128(longPremium.leftSlot())
876: 		                        );
877: 		
878: 		                        bytes32 chunkKey = keccak256(
879: 		                            abi.encodePacked(
880: 		                                tokenId.strike(0),
881: 		                                tokenId.width(0),
882: 		                                tokenId.tokenType(0)
883: 		                            )
884: 		                        );
885: 		
886: 		                        // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
887: 		                        // for the haircut directly to the accumulator
888: 		                        settled0 = Math.max(
889: 		                            0,
890: 		                            uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891: 		                        );
892: 		                        settled1 = Math.max(
893: 		                            0,
894: 		                            uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895: 		                        );
896: 		
897: 		                        _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
898: 		                            LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
899: 		                                uint128(settled1)
900: 		                            )
901: 		                        );
902: 		                    }
903: 		                }
904: 		            }

863: 		                for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864: 		                    if (tokenId.isLong(leg) == 1) {
865: 		                        mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
866: 		                            storage _settledTokens = settledTokens;
867: 		
868: 		                        // calculate amounts to revoke from settled and subtract from haircut req
869: 		                        uint256 settled0 = Math.unsafeDivRoundingUp(
870: 		                            uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871: 		                            uint128(longPremium.rightSlot())
872: 		                        );
873: 		                        uint256 settled1 = Math.unsafeDivRoundingUp(
874: 		                            uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875: 		                            uint128(longPremium.leftSlot())
876: 		                        );
877: 		
878: 		                        bytes32 chunkKey = keccak256(
879: 		                            abi.encodePacked(
880: 		                                tokenId.strike(0),
881: 		                                tokenId.width(0),
882: 		                                tokenId.tokenType(0)
883: 		                            )
884: 		                        );
885: 		
886: 		                        // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
887: 		                        // for the haircut directly to the accumulator
888: 		                        settled0 = Math.max(
889: 		                            0,
890: 		                            uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891: 		                        );
892: 		                        settled1 = Math.max(
893: 		                            0,
894: 		                            uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895: 		                        );
896: 		
897: 		                        _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
898: 		                            LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
899: 		                                uint128(settled1)
900: 		                            )
901: 		                        );
902: 		                    }
903: 		                }
```
[[137-144](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L137-L144), [148-152](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L148-L152), [207-224](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L207-L224), [248-250](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L248-L250), [256-260](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L256-L260), [395-409](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L395-L409), [781-789](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L781-L789), [784-788](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L784-L788), [860-904](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L860-L904), [863-903](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L863-L903)]



```solidity
File: contracts/multicall/Multicall.sol

14: 		        for (uint256 i = 0; i < data.length; ) {
15: 		            (bool success, bytes memory result) = address(this).delegatecall(data[i]);
16: 		
17: 		            if (!success) {
18: 		                // Bubble up the revert reason
19: 		                // The bytes type is ABI encoded as a length-prefixed byte array
20: 		                // So we simply need to add 32 to the pointer to get the start of the data
21: 		                // And then revert with the size loaded from the first 32 bytes
22: 		                // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
23: 		                // However, we have chosen to simply replicate the the normal behavior of the call
24: 		                // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
25: 		                assembly ("memory-safe") {
26: 		                    revert(add(result, 32), mload(result))
27: 		                }
28: 		            }
29: 		
30: 		            results[i] = result;
31: 		
32: 		            unchecked {
33: 		                ++i;
34: 		            }
35: 		        }
```
[[14-35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L14-L35)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

143: 		        for (uint256 i = 0; i < ids.length; ) {
144: 		            id = ids[i];
145: 		            amount = amounts[i];
146: 		
147: 		            balanceOf[from][id] -= amount;
148: 		
149: 		            // balance will never overflow
150: 		            unchecked {
151: 		                balanceOf[to][id] += amount;
152: 		            }
153: 		
154: 		            // An array can't have a total length
155: 		            // larger than the max uint256 value.
156: 		            unchecked {
157: 		                ++i;
158: 		            }
159: 		        }

187: 		            for (uint256 i = 0; i < owners.length; ++i) {
188: 		                balances[i] = balanceOf[owners[i]][ids[i]];
189: 		            }
```
[[143-159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L143-L159), [187-189](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L187-L189)]

</details>

---

### [N-21] Public functions not called internally

Those functions should be declared as `external` instead of `public`, as they are never called internally by the contract.

Contracts are allowed to override their parents' functions and change the visibility from external to public.

*There are 13 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

1141: 		    function getAccountMarginDetails(
```
[[1141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1141)]



```solidity
File: contracts/PanopticFactory.sol

135: 		    function initialize(address _owner) public {
```
[[135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L135)]



```solidity
File: contracts/PanopticPool.sol

1450: 		    function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {
```
[[1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1450)]



```solidity
File: contracts/libraries/FeesCalc.sol

97: 		    function calculateAMMSwapFees(
```
[[97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L97)]



```solidity
File: contracts/multicall/Multicall.sol

12: 		    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L12)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

81: 		    function setApprovalForAll(address operator, bool approved) public {

94: 		    function safeTransferFrom(

130: 		    function safeBatchTransferFrom(

178: 		    function balanceOfBatch(

200: 		    function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
```
[[81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L81), [94](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L94), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L130), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L178), [200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L200)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

50: 		    function approve(address spender, uint256 amount) public returns (bool) {

62: 		    function transfer(address to, uint256 amount) public virtual returns (bool) {

82: 		    function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
```
[[50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L50), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L62), [82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L82)]

</details>

---

### [N-22] Large multiples of ten should use scientific notation

Use a scientific notation rather than decimal literals (e.g. `1e6` instead of `1000000`), for better code readability.

*There are 7 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

// @audit 10_000 -> 1e4
77: 		    uint256 internal constant DECIMALS = 10_000;

// @audit 10_000 -> 1e4
81: 		    int128 internal constant DECIMALS_128 = 10_000;

// @audit 10_000 -> 1e4
204: 		                    10_000 +

// @audit 10_000 -> 1e4
206: 		                    10_000 ** 2 +

// @audit 10_000 -> 1e4
208: 		                    10_000 ** 3
```
[[77](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L77), [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L81), [204](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L204), [206](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L206), [208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L208)]



```solidity
File: contracts/PanopticPool.sol

// @audit 10_000 -> 1e4
175: 		    uint256 internal constant NO_BUFFER = 10_000;

// @audit 10_000 -> 1e4
1335: 		            return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);
```
[[175](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L175), [1335](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1335)]


---

### [N-23] Use of exponentiation instead of scientific notation

Use a scientific notation rather than exponentiation (e.g. `1e18` instead of `10**18`): although the compiler is capable of optimizing it, it is considered good coding practice to utilize idioms that don't rely on compiler optimization, whenever possible.

*There is 1 instance of this issue.*


```solidity
File: contracts/CollateralTracker.sol

234: 		        totalSupply = 10 ** 6;
```
[[234](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L234)]


---

### [N-24] Missing/malformed underscores for large numeric literals

Large hardcoded numbers in code can be difficult to read. Consider using underscores for number literals to improve readability (e.g `1234567` -> `1_234_567`). Consider using an underscore for every third digit from the right.

*There are 5 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

203: 		                    (12500 * ratioTick) /
```
[[203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L203)]



```solidity
File: contracts/libraries/Constants.sol

13: 		    int24 internal constant MIN_V3POOL_TICK = -887272;

16: 		    int24 internal constant MAX_V3POOL_TICK = 887272;

19: 		    uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

23: 		        1461446703485210103287273052203988822378723970342;
```
[[13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L13), [16](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L16), [19](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L19), [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L23)]


---

### [N-25] Avoid complex casting

Consider refactoring the following code, as double casting is confusing, and, in some scenarios, it may introduce unexpected truncations or rounding issues.

Furthermore, double type casting can make the code less readable and harder to maintain, increasing the likelihood of errors and misunderstandings during development and debugging.

*There are 67 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

// @audit int24(int256)
667: 		                    int24 range = int24(
668: 		                        int256(
669: 		                            Math.unsafeDivRoundingUp(
670: 		                                uint24(positionId.width(leg) * positionId.tickSpacing()),
671: 		                                2
672: 		                            )
673: 		                        )
674: 		                    );

// @audit int128(uint128)
715: 		                                int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

// @audit int128(uint128)
715: 		                                int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

// @audit int128(uint128)
718: 		                                int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

// @audit int128(uint128)
718: 		                                int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

// @audit int256(uint256)
1003: 		            int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

// @audit uint128(uint256)
1028: 		            s_poolAssets = uint128(uint256(updatedAssets));

// @audit uint128(uint256)
1029: 		            s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

// @audit int256(uint256)
1029: 		            s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

// @audit int256(uint256)
1052: 		            int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

// @audit uint128(uint256)
1084: 		            s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));

// @audit uint128(uint256)
1085: 		            s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

// @audit int256(uint256)
1085: 		            s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

// @audit uint256(uint128)
1121: 		                    uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,

// @audit uint256(uint128)
1184: 		                netBalance += uint256(uint128(premiumAllPositions));

// @audit int64(uint64)
1329: 		            ? int64(uint64(poolUtilization))

// @audit int64(uint64)
1330: 		            : int64(uint64(poolUtilization >> 64));

// @audit int64(uint64)
1585: 		                    ? int64(uint64(poolUtilization))

// @audit int64(uint64)
1586: 		                    : int64(uint64(poolUtilization >> 64))

// @audit uint128(uint64)
1637: 		                uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

// @audit uint128(uint64)
1638: 		                (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
```
[[667-674](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L667-L674), [715](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L715), [715](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L715), [718](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L718), [718](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L718), [1003](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1003), [1028](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1028), [1029](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1029), [1029](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1029), [1052](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1052), [1084](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1084), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1085), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1085), [1121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1121), [1184](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1184), [1329](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1329), [1330](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1330), [1585](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1585), [1586](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1586), [1637](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1638)]



```solidity
File: contracts/PanopticPool.sol

// @audit uint256(uint24)
314: 		                (uint256(uint24(currentTick)) << 24) + // add to slot 4

// @audit uint256(uint24)
315: 		                (uint256(uint24(currentTick))); // add to slot 3

// @audit int256(uint256)
1145: 		            uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)

// @audit int256(uint256)
1150: 		            uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)

// @audit int128(int256)
1554: 		                            int128(
1555: 		                                int256(
1556: 		                                    ((premiumAccumulatorsByLeg[leg][0] -
1557: 		                                        premiumAccumulatorLast.rightSlot()) *
1558: 		                                        (liquidityChunk.liquidity())) / 2 ** 64
1559: 		                                )
1560: 		                            )

// @audit int128(int256)
1563: 		                            int128(
1564: 		                                int256(
1565: 		                                    ((premiumAccumulatorsByLeg[leg][1] -
1566: 		                                        premiumAccumulatorLast.leftSlot()) *
1567: 		                                        (liquidityChunk.liquidity())) / 2 ** 64
1568: 		                                )
1569: 		                            )

// @audit int128(int256)
1641: 		                .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

// @audit int128(int256)
1642: 		                .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));
```
[[314](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L314), [315](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L315), [1145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1145), [1150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1150), [1554-1560](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1554-L1560), [1563-1569](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1563-L1569), [1641](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1641), [1642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1642)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit int128(int256)
1170: 		                    int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

// @audit int128(int256)
1173: 		                    int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

// @audit int128(int256)
1177: 		                .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

// @audit int128(int256)
1178: 		                .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

// @audit int128(int256)
1215: 		        movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

// @audit int128(int256)
1216: 		            int128(int256(amount1))

// @audit int128(int256)
1242: 		            movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

// @audit int128(int256)
1243: 		                -int128(int256(amount1))
```
[[1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1170), [1173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1173), [1177](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1177), [1178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1178), [1215](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1215), [1216](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1216), [1242](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1242), [1243](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1243)]



```solidity
File: contracts/libraries/FeesCalc.sol

// @audit int128(int256)
117: 		                .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

// @audit int128(int256)
118: 		                .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));
```
[[117](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L117), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L118)]



```solidity
File: contracts/libraries/Math.sol

// @audit uint256(int256)
130: 		            uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));

// @audit uint256(int256)
131: 		            if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();
```
[[130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L130), [131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L131)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit uint64(uint24)
51: 		            poolId += uint64(uint24(tickSpacing)) << 48;

// @audit uint248(uint256)
103: 		                (uint248(uint256(keccak256(abi.encode(tokenId)))));

// @audit int24(uint24)
178: 		                (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

// @audit int24(uint24)
179: 		                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

// @audit uint256(uint40)
183: 		            if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

// @audit int24(uint24)
217: 		                    entry = int24(uint24(medianData >> (rank * 24)));

// @audit uint256(uint192)
229: 		                    uint256(uint192(medianData << 24)) +

// @audit uint256(uint24)
230: 		                    uint256(uint24(lastObservedTick));

// @audit int56(uint56)
258: 		                    (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

// @audit int24(int256)
377: 		            int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

// @audit int256(uint256)
693: 		            int256 balance0 = int256(uint256(tokenData0.rightSlot())) -

// @audit int256(uint256)
695: 		            int256 balance1 = int256(uint256(tokenData1.rightSlot())) -
```
[[51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L51), [103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L103), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L178), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L179), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L183), [217](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L217), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L229), [230](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L230), [258](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L258), [377](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L377), [693](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L693), [695](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L695)]



```solidity
File: contracts/types/LeftRight.sol

// @audit int256(uint256)
27: 		        int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

// @audit int256(uint256)
27: 		        int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

// @audit int256(uint256)
196: 		            int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();

// @audit int256(uint256)
201: 		            int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();
```
[[27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L27), [27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L27), [196](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L196), [201](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L201)]



```solidity
File: contracts/types/LiquidityChunk.sol

// @audit uint256(uint24)
79: 		                    (uint256(uint24(_tickLower)) << 232) +

// @audit uint256(uint24)
80: 		                        (uint256(uint24(_tickUpper)) << 208) +

// @audit uint256(uint24)
110: 		                    LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

// @audit uint256(uint24)
127: 		                    LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

// @audit int24(int256)
174: 		            return int24(int256(LiquidityChunk.unwrap(self) >> 232));

// @audit int24(int256)
183: 		            return int24(int256(LiquidityChunk.unwrap(self) >> 208));
```
[[79](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L79), [80](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L80), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L110), [127](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L127), [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L174), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L183)]



```solidity
File: contracts/types/TokenId.sol

// @audit int24(uint24)
98: 		            return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

// @audit int24(int256)
160: 		            return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

// @audit int24(int256)
171: 		            return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

// @audit uint256(uint24)
195: 		            return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));
```
[[98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L98), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L171), [195](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L195)]

</details>

---

### [N-26] Consider using the `using-for` syntax

The `using-for` [syntax](https://docs.soliditylang.org/en/latest/contracts.html#using-for) is the more common way of calling library functions.

*There are 460 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

170: 		        if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

229: 		        if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();

292: 		            InteractionHelper.computeName(

305: 		        return InteractionHelper.computeSymbol(s_underlyingToken, TICKER_PREFIX);

312: 		        return InteractionHelper.computeDecimals(s_underlyingToken);

331: 		        if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

333: 		        return ERC20Minimal.transfer(recipient, amount);

350: 		        if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

352: 		        return ERC20Minimal.transferFrom(from, to, amount);

380: 		        return Math.mulDiv(assets, totalSupply, totalAssets());

387: 		        return Math.mulDiv(shares, totalAssets(), totalSupply);

402: 		            shares = Math.mulDiv(

418: 		        if (assets > type(uint104).max) revert Errors.DepositTooLarge();

424: 		        SafeTransferLib.safeTransferFrom(

462: 		            assets = Math.mulDivRoundingUp(

480: 		        if (assets > type(uint104).max) revert Errors.DepositTooLarge();

484: 		        SafeTransferLib.safeTransferFrom(

512: 		        return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

521: 		        return Math.mulDivRoundingUp(assets, supply, totalAssets());

536: 		        if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

556: 		        SafeTransferLib.safeTransferFrom(

575: 		        return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

596: 		        if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

616: 		        SafeTransferLib.safeTransferFrom(

669: 		                            Math.unsafeDivRoundingUp(

675: 		                    maxNumRangesFromStrike = Math.max(

677: 		                        uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

687: 		                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

693: 		                    (currentValue0, currentValue1) = Math.getAmountsForLiquidity(

698: 		                    (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(

712: 		                        LeftRightSigned

956: 		                Math.mulDiv(

959: 		                    uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

1012: 		                uint256 sharesToBurn = Math.mulDivRoundingUp(

1069: 		                uint256 sharesToBurn = Math.mulDivRoundingUp(

1109: 		                uint256 swapCommission = Math.unsafeDivRoundingUp(

1110: 		                    s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),

1120: 		                Math.unsafeDivRoundingUp(

1210: 		            TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);

1213: 		            uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();

1216: 		            uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

1322: 		        LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

1363: 		                        ? Math.getSqrtRatioAtTick(

1364: 		                            Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

1364: 		                            Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

1366: 		                        : Math.getSqrtRatioAtTick(

1367: 		                            Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

1367: 		                            Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

1397: 		                        uint256 c2 = Constants.FP96 - ratio;

1401: 		                        required += Math.mulDiv96RoundingUp(amountMoved, c2);

1408: 		                        uint160 scaleFactor = Math.getSqrtRatioAtTick(

1411: 		                        uint256 c3 = Math.mulDivRoundingUp(

1414: 		                            scaleFactor + Constants.FP96

1486: 		                required = Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS);

1496: 		                required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);

1518: 		        LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

1521: 		        LeftRightUnsigned amountsMovedPartner = PanopticMath.getAmountsMoved(

1571: 		                    ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)

1572: 		                    : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

1579: 		        spreadRequirement = Math.max(
```
[[170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L170), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L229), [292](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L292), [305](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L305), [312](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L312), [331](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L331), [333](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L333), [350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L350), [352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L352), [380](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L380), [387](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L387), [402](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L402), [418](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L418), [424](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L424), [462](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L462), [480](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L480), [484](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L484), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L512), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L521), [536](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L536), [556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L556), [575](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L575), [596](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L596), [616](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L616), [669](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L669), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L675), [677](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L677), [687](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L687), [693](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L693), [698](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L698), [712](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L712), [956](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L956), [959](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L959), [1012](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1012), [1069](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1069), [1109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1109), [1110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1110), [1120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1120), [1210](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1210), [1213](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1213), [1216](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1216), [1322](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1322), [1363](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1363), [1364](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1364), [1364](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1364), [1366](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1366), [1367](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1367), [1367](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1367), [1397](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1397), [1401](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1401), [1408](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1408), [1411](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1411), [1414](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1414), [1486](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1486), [1496](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1496), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1518), [1521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1521), [1571](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1571), [1572](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1572), [1579](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1579)]



```solidity
File: contracts/PanopticFactory.sol

151: 		        if (msg.sender != currentOwner) revert Errors.NotOwner();

178: 		        CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

180: 		        CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);

183: 		            SafeTransferLib.safeTransferFrom(

190: 		            SafeTransferLib.safeTransferFrom(

221: 		        if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

225: 		        if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

227: 		        IUniswapV3Pool v3Pool = IUniswapV3Pool(UNIV3_FACTORY.getPool(token0, token1, fee));

228: 		        if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

231: 		            revert Errors.PoolAlreadyInitialized();

234: 		        SFPM.initializeAMMPool(token0, token1, fee);

238: 		        newPoolContract = PanopticPool(POOL_REFERENCE.cloneDeterministic(salt));

242: 		            Clones.clone(COLLATERAL_REFERENCE)

245: 		            Clones.clone(COLLATERAL_REFERENCE)

267: 		        DONOR_NFT.issueNFT(msg.sender, newPoolContract, token0, token1, fee);

305: 		            uint256 rarity = PanopticMath.numberOfLeadingHexZeros(

306: 		                POOL_REFERENCE.predictDeterministicAddress(salt)

354: 		                    Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)

358: 		                    Math.mulDivRoundingUp(

360: 		                        Constants.FP96,

367: 		                    Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)

370: 		                    Math.mulDivRoundingUp(

372: 		                        Constants.FP96,

393: 		            tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

398: 		            CallbackLib.CallbackData({

399: 		                poolFeatures: CallbackLib.PoolFeatures({token0: token0, token1: token1, fee: fee}),
```
[[151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L151), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L178), [180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L180), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L183), [190](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L190), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L221), [225](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L225), [227](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L227), [228](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L228), [231](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L231), [234](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L234), [238](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L238), [242](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L242), [245](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L245), [267](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L267), [305](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L305), [306](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L306), [354](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L354), [358](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L358), [360](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L360), [367](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L367), [370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L370), [372](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L372), [393](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L393), [398](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L398), [399](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L399)]



```solidity
File: contracts/PanopticPool.sol

104: 		    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

104: 		    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

106: 		    int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

106: 		    int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

300: 		        if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

327: 		        InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);

343: 		            revert Errors.PriceBoundFail();

416: 		        (value0, value1) = FeesCalc.getPortfolioValue(

445: 		            balances[k][0] = TokenId.unwrap(tokenId);

446: 		            balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);

453: 		                    LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),

474: 		                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),

474: 		                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),

478: 		                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

478: 		                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

526: 		        (, uint256 medianData) = PanopticMath.computeInternalMedian(

634: 		        if (tokenId.poolId() != SFPM.getPoolId(address(s_univ3pool)))

635: 		            revert Errors.InvalidTokenIdParameter(0);

639: 		        if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

640: 		            revert Errors.PositionAlreadyMinted();

655: 		        s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned

686: 		        (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM

713: 		        (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath

752: 		                (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

763: 		                s_options[msg.sender][tokenId][leg] = LeftRightUnsigned

776: 		                    uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))

862: 		        s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

871: 		            s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);

906: 		        int24 fastOracleTick = PanopticMath.computeMedianObservedPrice(

916: 		            slowOracleTick = PanopticMath.computeMedianObservedPrice(

924: 		            (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(

941: 		        if (!solventAtFast) revert Errors.NotEnoughCollateral();

944: 		        if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

946: 		                revert Errors.NotEnoughCollateral();

971: 		        (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM

982: 		        (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath

1036: 		            if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

1037: 		                revert Errors.StaleTWAP();

1064: 		                Math.getSqrtRatioAtTick(twapTick)

1067: 		            if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();

1089: 		                Constants.MIN_V3POOL_TICK,

1090: 		                Constants.MAX_V3POOL_TICK,

1099: 		            (liquidationBonus0, liquidationBonus1, collateralRemaining) = PanopticMath

1103: 		                    Math.getSqrtRatioAtTick(twapTick),

1104: 		                    Math.getSqrtRatioAtTick(finalTick),

1123: 		            (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(

1130: 		                Math.getSqrtRatioAtTick(_finalTick),

1164: 		        ) revert Errors.NotEnoughCollateral();

1166: 		        LeftRightSigned bonusAmounts = LeftRightSigned

1189: 		        if (touchedId.length != 1) revert Errors.InputListFail();

1198: 		        (LeftRightSigned longAmounts, LeftRightSigned delegatedAmounts) = PanopticMath

1248: 		        refundAmounts = PanopticMath.getRefundAmounts(

1330: 		            Math.getSqrtRatioAtTick(atTick)

1335: 		            return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

1354: 		                Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

1355: 		                Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);

1359: 		                Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

1360: 		                Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);

1389: 		            fingerprintIncomingList = PanopticMath.updatePositionsHash(

1400: 		        if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();

1416: 		        uint256 newHash = PanopticMath.updatePositionsHash(

1421: 		        if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

1457: 		        twapTick = PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW);

1478: 		        LeftRightUnsigned accountLiquidities = SFPM.getAccountLiquidity(

1499: 		            revert Errors.EffectiveLiquidityAboveThreshold();

1527: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

1534: 		                (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM

1551: 		                    premiaByLeg[leg] = LeftRightSigned

1573: 		                        premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

1602: 		        if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1611: 		            (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

1620: 		            accumulatedPremium = LeftRightUnsigned

1633: 		        uint256 liquidity = PanopticMath

1639: 		            LeftRightSigned realizedPremia = LeftRightSigned

1657: 		                LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))

1657: 		                LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))

1686: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

1713: 		                (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(

1731: 		                    s_grossPremiumLast[chunkKey] = LeftRightUnsigned

1780: 		                LeftRightUnsigned

1784: 		                            Math.min(

1793: 		                            Math.min(

1817: 		            LeftRightUnsigned accountLiquidities = SFPM.getAccountLiquidity(

1868: 		            if (LeftRightSigned.unwrap(legPremia) != 0) {

1872: 		                        settledTokens = LeftRightUnsigned.wrap(

1874: 		                                LeftRightSigned.unwrap(

1875: 		                                    LeftRightSigned

1876: 		                                        .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))

1883: 		                    uint256 positionLiquidity = PanopticMath

1898: 		                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),

1898: 		                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),

1907: 		                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

1907: 		                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

1935: 		                            ? LeftRightUnsigned

1940: 		                                            Math.max(

1957: 		                                            Math.max(

1971: 		                            : LeftRightUnsigned
```
[[104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L104), [104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L104), [106](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L106), [106](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L106), [300](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L300), [327](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L327), [343](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L343), [416](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L416), [445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L445), [446](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L446), [453](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L453), [474](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L474), [474](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L474), [478](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L478), [478](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L478), [526](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L526), [634](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L634), [635](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L635), [639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L639), [640](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L640), [655](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L655), [686](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L686), [713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L713), [752](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L752), [763](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L763), [776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L776), [862](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L862), [871](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L871), [906](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L906), [916](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L916), [924](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L924), [941](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L941), [944](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L944), [946](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L946), [971](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L971), [982](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L982), [1036](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1036), [1037](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1037), [1064](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1064), [1067](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1067), [1089](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1089), [1090](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1090), [1099](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1099), [1103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1103), [1104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1104), [1123](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1123), [1130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1130), [1164](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1164), [1166](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1166), [1189](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1189), [1198](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1198), [1248](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1248), [1330](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1330), [1335](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1335), [1354](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1354), [1355](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1355), [1359](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1359), [1360](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1360), [1389](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1389), [1400](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1400), [1416](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1416), [1421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1421), [1457](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1457), [1478](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1478), [1499](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1499), [1527](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1527), [1534](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1534), [1551](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1551), [1573](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1573), [1602](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1602), [1611](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1611), [1620](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1620), [1633](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1633), [1639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1639), [1657](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1657), [1657](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1657), [1686](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1686), [1713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1713), [1731](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1731), [1780](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1780), [1784](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1784), [1793](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1793), [1817](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1817), [1868](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1868), [1872](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1872), [1874](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1874), [1875](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1875), [1876](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1876), [1883](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1883), [1898](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1898), [1898](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1898), [1907](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1907), [1907](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1907), [1935](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1935), [1940](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1940), [1957](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1957), [1971](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1971)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

322: 		        if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();

352: 		        address univ3pool = FACTORY.getPool(token0, token1, fee);

355: 		        if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

367: 		        uint64 poolId = PanopticMath.getPoolId(univ3pool);

373: 		            poolId = PanopticMath.incrementPoolPattern(poolId);

408: 		        CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

410: 		        CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

413: 		            SafeTransferLib.safeTransferFrom(

420: 		            SafeTransferLib.safeTransferFrom(

441: 		        CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

443: 		        CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

456: 		        SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

482: 		        _burn(msg.sender, TokenId.unwrap(tokenId), positionSize);

515: 		        _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);

549: 		        if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

549: 		        if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

552: 		        registerTokenTransfer(from, to, TokenId.wrap(id), amount);

576: 		            if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

576: 		            if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

577: 		            registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);

604: 		            LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

632: 		                (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

633: 		                (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

634: 		            ) revert Errors.TransferFailed();

639: 		            if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity()) //@audit-ok before it checked only the rightSlot

640: 		                revert Errors.TransferFailed();

646: 		            s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

649: 		            s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

689: 		        if (positionSize == 0) revert Errors.OptionsBalanceZero();

703: 		        if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

718: 		            if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

729: 		            revert Errors.PriceBoundFail();

775: 		                CallbackLib.CallbackData({

776: 		                    poolFeatures: CallbackLib.PoolFeatures({

818: 		                int256 net0 = itm0 - PanopticMath.convert1to0(itm1, sqrtPriceX96);

834: 		            if (swapAmount == 0) return LeftRightSigned.wrap(0);

843: 		                    ? Constants.MIN_V3POOL_SQRT_RATIO + 1

844: 		                    : Constants.MAX_V3POOL_SQRT_RATIO - 1,

849: 		            totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(

905: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

923: 		                    amount0 += Math.getAmount0ForLiquidity(liquidityChunk);

925: 		                    amount1 += Math.getAmount1ForLiquidity(liquidityChunk);

941: 		            revert Errors.PositionTooLarge();

1019: 		                    revert Errors.NotEnoughLiquidity();

1039: 		            s_accountLiquidity[positionKey] = LeftRightUnsigned

1124: 		        (s_accountPremiumOwed[positionKey], s_accountPremiumGross[positionKey]) = LeftRightLibrary

1167: 		            ? LeftRightSigned

1170: 		                    int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

1173: 		                    int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

1175: 		            : LeftRightSigned

1177: 		                .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

1178: 		                .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

1192: 		            CallbackLib.CallbackData({ // compute by reading values from univ3pool every time

1193: 		                    poolFeatures: CallbackLib.PoolFeatures({

1215: 		        movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

1242: 		            movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

1280: 		        if (LeftRightSigned.unwrap(amountToCollect) != 0) {

1307: 		            collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(

1351: 		                premium0X64_base = Math.mulDiv(

1356: 		                premium1X64_base = Math.mulDiv(

1370: 		                    premium0X64_owed = Math

1373: 		                    premium1X64_owed = Math

1377: 		                    deltaPremiumOwed = LeftRightUnsigned

1394: 		                    premium0X64_gross = Math

1397: 		                    premium1X64_gross = Math

1401: 		                    deltaPremiumGross = LeftRightUnsigned

1481: 		                    LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(

1493: 		                    amountToCollect = LeftRightUnsigned.wrap(

1495: 		                            LeftRightSigned.unwrap(feesBase.subRect(s_accountFeesBase[positionKey]))

1508: 		                (premiumOwed, premiumGross) = LeftRightLibrary.addCapped(
```
[[322](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L322), [352](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L352), [355](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L355), [367](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L367), [373](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L373), [408](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L408), [410](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L410), [413](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L413), [420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L420), [441](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L441), [443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L443), [456](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L456), [482](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L482), [515](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L515), [549](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L549), [549](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L549), [552](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L552), [576](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L576), [576](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L576), [577](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L577), [604](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L604), [632](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L632), [633](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L633), [634](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L634), [639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L639), [640](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L640), [646](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L646), [649](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L649), [689](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L689), [703](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L703), [718](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L718), [729](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L729), [775](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L775), [776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L776), [818](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L818), [834](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L834), [843](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L843), [844](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L844), [849](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L849), [905](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L905), [923](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L923), [925](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L925), [941](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L941), [1019](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1019), [1039](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1039), [1124](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1124), [1167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1167), [1170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1170), [1173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1173), [1175](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1175), [1177](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1177), [1178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1178), [1192](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1192), [1193](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1193), [1215](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1215), [1242](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1242), [1280](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1280), [1307](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1307), [1351](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1351), [1356](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1356), [1370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1370), [1373](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1373), [1377](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1377), [1394](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1394), [1397](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1397), [1401](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1401), [1481](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1481), [1493](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1493), [1495](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1495), [1508](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1508)]



```solidity
File: contracts/libraries/CallbackLib.sol

38: 		            revert Errors.InvalidUniswapCallback();
```
[[38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L38)]



```solidity
File: contracts/libraries/FeesCalc.sol

56: 		                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

62: 		                (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(

115: 		            LeftRightSigned

117: 		                .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

118: 		                .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));
```
[[56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L56), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L62), [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L115), [117](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L117), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L118)]



```solidity
File: contracts/libraries/InteractionHelper.sol

82: 		                    Strings.toString(fee),
```
[[82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L82)]



```solidity
File: contracts/libraries/Math.sol

131: 		            if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

131: 		            if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

251: 		                LiquidityChunkLibrary.createChunk(

281: 		                LiquidityChunkLibrary.createChunk(

284: 		                    toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))

297: 		        if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

312: 		        if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

319: 		        if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

326: 		        if (toCast > uint256(type(int256).max)) revert Errors.CastingError();
```
[[131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L131), [131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L131), [251](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L251), [281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L281), [284](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L284), [297](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L297), [312](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L312), [319](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L319), [326](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L326)]



```solidity
File: contracts/libraries/PanopticMath.sol

77: 		            return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

155: 		            return int24(Math.sort(ticks)[cardinality / 2]);

263: 		            int256[] memory sortedTicks = Math.sort(twapMeasurement);

326: 		            return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);

328: 		            return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);

346: 		            int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

347: 		            int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

349: 		            (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(width, tickSpacing);

361: 		            ) revert Errors.TicksNotInitializable();

377: 		            int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

452: 		            convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));

476: 		                ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

477: 		                : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

479: 		            if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

495: 		                return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);

497: 		                return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

497: 		                return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

512: 		                return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

514: 		                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

514: 		                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

529: 		                int256 absResult = Math

530: 		                    .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)

534: 		                int256 absResult = Math

535: 		                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

535: 		                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

552: 		                int256 absResult = Math

553: 		                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

557: 		                int256 absResult = Math

559: 		                        Math.absUint(amount),

561: 		                        Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)

587: 		            amount1 = Math

588: 		                .getAmount1ForLiquidity(Math.getLiquidityForAmount0(tickLower, tickUpper, amount0))

593: 		            amount0 = Math

594: 		                .getAmount0ForLiquidity(Math.getLiquidityForAmount1(tickLower, tickUpper, amount1))

598: 		        return LeftRightUnsigned.wrap(0).toRightSlot(amount0).toLeftSlot(amount1);

621: 		                shorts = shorts.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

624: 		                longs = longs.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

629: 		                shorts = shorts.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

632: 		                longs = longs.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

664: 		                uint256 required0 = PanopticMath.convert0to1(

671: 		                (uint256 balanceCross, uint256 thresholdCross) = PanopticMath.convertCollateralData(

678: 		                uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

681: 		                bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));

684: 		                    PanopticMath.convert0to1(

685: 		                        Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

694: 		                Math.max(premia.rightSlot(), 0);

696: 		                Math.max(premia.leftSlot(), 0);

715: 		                    bonus1 += Math.min(

717: 		                        PanopticMath.convert0to1(paid0 - balance0, sqrtPriceX96Final)

719: 		                    bonus0 -= Math.min(

720: 		                        PanopticMath.convert1to0(balance1 - paid1, sqrtPriceX96Final),

733: 		                    bonus0 += Math.min(

735: 		                        PanopticMath.convert1to0(paid1 - balance1, sqrtPriceX96Final)

737: 		                    bonus1 -= Math.min(

738: 		                        PanopticMath.convert0to1(balance0 - paid0, sqrtPriceX96Final),

749: 		                LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(

791: 		            int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);

792: 		            int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

803: 		                    -Math.min(

805: 		                        PanopticMath.convert1to0(

810: 		                    Math.min(

812: 		                        PanopticMath.convert0to1(

827: 		                    Math.min(

829: 		                        PanopticMath.convert1to0(

834: 		                    -Math.min(

836: 		                        PanopticMath.convert0to1(

847: 		                haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());

848: 		                haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());

869: 		                        uint256 settled0 = Math.unsafeDivRoundingUp(

873: 		                        uint256 settled1 = Math.unsafeDivRoundingUp(

888: 		                        settled0 = Math.max(

892: 		                        settled1 = Math.max(

898: 		                            LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(

924: 		        uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);

933: 		                    LeftRightSigned

939: 		                                    PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)

951: 		                    LeftRightSigned

957: 		                                    PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
```
[[77](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L77), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L155), [263](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L263), [326](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L326), [328](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L328), [346](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L346), [347](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L347), [349](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L349), [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L361), [377](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L377), [452](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L452), [476](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L476), [477](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L477), [479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L479), [495](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L495), [497](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L497), [497](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L497), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L512), [514](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L514), [514](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L514), [529](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L529), [530](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L530), [534](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L534), [535](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L535), [535](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L535), [552](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L552), [553](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L553), [557](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L557), [559](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L559), [561](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L561), [587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L587), [588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L588), [593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L593), [594](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L594), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L598), [621](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L621), [624](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L624), [629](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L629), [632](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L632), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L664), [671](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L671), [678](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L678), [681](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L681), [684](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L684), [685](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L685), [694](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L694), [696](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L696), [715](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L715), [717](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L717), [719](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L719), [720](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L720), [733](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L733), [735](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L735), [737](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L737), [738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L738), [749](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L749), [791](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L791), [792](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L792), [803](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L803), [805](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L805), [810](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L810), [812](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L812), [827](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L827), [829](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L829), [834](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L834), [836](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L836), [847](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L847), [848](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L848), [869](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L869), [873](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L873), [888](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L888), [892](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L892), [898](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L898), [924](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L924), [933](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L933), [939](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L939), [951](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L951), [957](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L957)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

46: 		        if (!success) revert Errors.TransferFailed();

76: 		        if (!success) revert Errors.TransferFailed();
```
[[46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L46), [76](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L76)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

115: 		                ERC1155Holder.onERC1155Received.selector

166: 		                ERC1155Holder.onERC1155BatchReceived.selector

225: 		                ERC1155Holder.onERC1155Received.selector
```
[[115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L115), [166](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L166), [225](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L225)]



```solidity
File: contracts/types/LeftRight.sol

40: 		        return uint128(LeftRightUnsigned.unwrap(self));

47: 		        return int128(LeftRightSigned.unwrap(self));

67: 		                LeftRightUnsigned.wrap(

68: 		                    (LeftRightUnsigned.unwrap(self) & LEFT_HALF_BIT_MASK) +

69: 		                        uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)

87: 		                LeftRightSigned.wrap(

88: 		                    (LeftRightSigned.unwrap(self) & LEFT_HALF_BIT_MASK_INT) +

89: 		                        (int256(int128(LeftRightSigned.unwrap(self)) + right) & RIGHT_HALF_BIT_MASK)

102: 		        return uint128(LeftRightUnsigned.unwrap(self) >> 128);

109: 		        return int128(LeftRightSigned.unwrap(self) >> 128);

126: 		            return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));

126: 		            return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));

136: 		            return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));

136: 		            return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));

155: 		            z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));

155: 		            z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));

155: 		            z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));

161: 		                LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||

161: 		                LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||

162: 		                (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))

162: 		                (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))

163: 		            ) revert Errors.UnderOverFlow();

178: 		            z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));

178: 		            z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));

178: 		            z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));

184: 		                LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||

184: 		                LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||

185: 		                (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))

185: 		                (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))

186: 		            ) revert Errors.UnderOverFlow();

199: 		            if (left128 != left) revert Errors.UnderOverFlow();

204: 		            if (right128 != right) revert Errors.UnderOverFlow();

222: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

240: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

262: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

265: 		                z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

266: 		                    int128(Math.max(left128, 0))

294: 		            LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(

297: 		            LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(
```
[[40](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L40), [47](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L47), [67](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L67), [68](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L68), [69](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L69), [87](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L87), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L88), [89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L89), [102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L109), [126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L126), [126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L126), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L136), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L136), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L155), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L155), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L155), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L161), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L161), [162](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L162), [162](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L162), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L163), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L178), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L178), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L178), [184](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L184), [184](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L184), [185](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L185), [185](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L185), [186](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L186), [199](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L199), [204](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L204), [222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L222), [240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L240), [262](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L262), [265](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L265), [266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L266), [294](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L294), [297](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L297)]



```solidity
File: contracts/types/LiquidityChunk.sol

78: 		                LiquidityChunk.wrap(

95: 		            return LiquidityChunk.wrap(LiquidityChunk.unwrap(self) + amount);

95: 		            return LiquidityChunk.wrap(LiquidityChunk.unwrap(self) + amount);

109: 		                LiquidityChunk.wrap(

110: 		                    LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

126: 		                LiquidityChunk.wrap(

127: 		                    LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

142: 		                LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TL_MASK).addTickLower(

142: 		                LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TL_MASK).addTickLower(

159: 		                LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TU_MASK).addTickUpper(

159: 		                LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TU_MASK).addTickUpper(

174: 		            return int24(int256(LiquidityChunk.unwrap(self) >> 232));

183: 		            return int24(int256(LiquidityChunk.unwrap(self) >> 208));

192: 		            return uint128(LiquidityChunk.unwrap(self));
```
[[78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L78), [95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L95), [95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L95), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L109), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L110), [126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L126), [127](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L127), [142](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L142), [142](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L142), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L159), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L159), [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L174), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L183), [192](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L192)]



```solidity
File: contracts/types/TokenId.sol

89: 		            return uint64(TokenId.unwrap(self));

98: 		            return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

110: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

120: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

130: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

140: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

150: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

160: 		            return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

171: 		            return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

185: 		            return TokenId.wrap(TokenId.unwrap(self) + _poolId);

185: 		            return TokenId.wrap(TokenId.unwrap(self) + _poolId);

195: 		            return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

195: 		            return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

212: 		                TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

212: 		                TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

228: 		                TokenId.wrap(

229: 		                    TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

246: 		            return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

246: 		            return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

262: 		                TokenId.wrap(

263: 		                    TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

280: 		                TokenId.wrap(

281: 		                    TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

298: 		                TokenId.wrap(

299: 		                    TokenId.unwrap(self) +

318: 		                TokenId.wrap(

319: 		                    TokenId.unwrap(self) +

371: 		            uint256 optionRatios = TokenId.unwrap(self) & OPTION_RATIO_MASK;

393: 		                TokenId.wrap(

394: 		                    TokenId.unwrap(self) ^

420: 		        (legLowerTick, legUpperTick) = PanopticMath.getTicks(

434: 		        uint256 optionRatios = TokenId.unwrap(self) & OPTION_RATIO_MASK;

467: 		                TokenId.wrap(

468: 		                    TokenId.unwrap(self) &

473: 		                TokenId.wrap(

474: 		                    TokenId.unwrap(self) &

479: 		                TokenId.wrap(

480: 		                    TokenId.unwrap(self) &

485: 		                TokenId.wrap(

486: 		                    TokenId.unwrap(self) &

501: 		        if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

506: 		            uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;

512: 		                    if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

513: 		                        revert Errors.InvalidTokenIdParameter(1);

522: 		                        revert Errors.InvalidTokenIdParameter(6);

528: 		                if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

531: 		                    (self.strike(i) == Constants.MIN_V3POOL_TICK) ||

532: 		                    (self.strike(i) == Constants.MAX_V3POOL_TICK)

533: 		                ) revert Errors.InvalidTokenIdParameter(4); //@audit-info what if is > or < tick?

542: 		                        revert Errors.InvalidTokenIdParameter(3);

548: 		                    ) revert Errors.InvalidTokenIdParameter(3);

561: 		                        revert Errors.InvalidTokenIdParameter(4);

567: 		                        revert Errors.InvalidTokenIdParameter(5);

582: 		                (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(

598: 		        revert Errors.NoLegsExercisable();
```
[[89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L89), [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L98), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L110), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L120), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L130), [140](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L140), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L150), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L171), [185](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L185), [185](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L185), [195](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L195), [195](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L195), [212](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L212), [212](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L212), [228](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L228), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L229), [246](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L246), [246](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L246), [262](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L262), [263](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L263), [280](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L280), [281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L281), [298](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L298), [299](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L299), [318](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L318), [319](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L319), [371](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L371), [393](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L393), [394](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L394), [420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L420), [434](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L434), [467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L467), [468](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L468), [473](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L473), [474](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L474), [479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L479), [480](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L480), [485](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L485), [486](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L486), [501](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L501), [506](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L506), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L512), [513](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L513), [522](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L522), [528](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L528), [531](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L531), [532](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L532), [533](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L533), [542](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L542), [548](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L548), [561](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L561), [567](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L567), [582](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L582), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L598)]

</details>

---

### [N-27] Consider making contracts `Upgradeable`

This allows for bugs to be fixed in production, at the expense of **significantly** increasing centralization.

*There are 20 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

36: 		contract CollateralTracker is ERC20Minimal, Multicall {
```
[[36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L36)]



```solidity
File: contracts/PanopticFactory.sol

27: 		contract PanopticFactory is Multicall {
```
[[27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L27)]



```solidity
File: contracts/PanopticPool.sol

28: 		contract PanopticPool is ERC1155Holder, Multicall {
```
[[28](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L28)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

72: 		contract SemiFungiblePositionManager is ERC1155, Multicall {
```
[[72](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L72)]



```solidity
File: contracts/libraries/CallbackLib.sol

13: 		library CallbackLib {
```
[[13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L13)]



```solidity
File: contracts/libraries/Constants.sol

8: 		library Constants {
```
[[8](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L8)]



```solidity
File: contracts/libraries/Errors.sol

7: 		library Errors {
```
[[7](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L7)]



```solidity
File: contracts/libraries/FeesCalc.sol

39: 		library FeesCalc {
```
[[39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L39)]



```solidity
File: contracts/libraries/InteractionHelper.sol

18: 		library InteractionHelper {
```
[[18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L18)]



```solidity
File: contracts/libraries/Math.sol

13: 		library Math {
```
[[13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L13)]



```solidity
File: contracts/libraries/PanopticMath.sol

18: 		library PanopticMath {
```
[[18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L18)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

12: 		library SafeTransferLib {
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L12)]



```solidity
File: contracts/multicall/Multicall.sol

8: 		abstract contract Multicall {
```
[[8](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L8)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

11: 		abstract contract ERC1155 {
```
[[11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L11)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

10: 		abstract contract ERC20Minimal {
```
[[10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L10)]



```solidity
File: contracts/types/LeftRight.sol

17: 		library LeftRightLibrary {
```
[[17](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L17)]



```solidity
File: contracts/types/LiquidityChunk.sol

53: 		library LiquidityChunkLibrary {
```
[[53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L53)]



```solidity
File: contracts/types/TokenId.sol

60: 		library TokenIdLibrary {
```
[[60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L60)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: 		interface IDonorNFT {
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6)]



```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

11: 		interface IERC20Partial {
```
[[11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L11)]

</details>

---

### [N-28] Dependence on external protocols

External protocols should be monitored as such dependencies may introduce vulnerabilities if a vulnerability is found in the external protocol.

*There are 19 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/PanopticFactory.sol

9: 		import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

10: 		import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";

14: 		import {Clones} from "@openzeppelin/contracts/proxy/Clones.sol";
```
[[9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L9), [10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L10), [14](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L14)]



```solidity
File: contracts/PanopticPool.sol

7: 		import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";

9: 		import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```
[[7](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L7), [9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L9)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

5: 		import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

6: 		import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";
```
[[5](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L5), [6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L6)]



```solidity
File: contracts/libraries/CallbackLib.sol

5: 		import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

33: 		        IUniswapV3Factory factory,

38: 		            revert Errors.InvalidUniswapCallback();
```
[[5](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L5), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L33), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L38)]



```solidity
File: contracts/libraries/Errors.sol

45: 		    error InvalidUniswapCallback();

111: 		    error UniswapPoolNotInitialized();
```
[[45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L45), [111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L111)]



```solidity
File: contracts/libraries/FeesCalc.sol

5: 		import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";

98: 		        IUniswapV3Pool univ3pool,

131: 		        IUniswapV3Pool univ3pool,
```
[[5](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L5), [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L98), [131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L131)]



```solidity
File: contracts/libraries/InteractionHelper.sol

6: 		import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

10: 		import {Strings} from "@openzeppelin/contracts/utils/Strings.sol";
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L6), [10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L10)]



```solidity
File: contracts/libraries/PanopticMath.sol

6: 		import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L6)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

5: 		import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```
[[5](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L5)]

</details>

---

### [N-29] Debug imports in production code

Remove debug imports, as they increase the contract size, and they are useful only for local tests.

*There is 1 instance of this issue.*


```solidity
File: contracts/PanopticPool.sol

22: 		import "forge-std/console.sol";
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L22)]


---

### [N-30] `2**<n> - 1` should be re-written as `type(uint<n>).max`

Earlier versions of solidity can use `uint<n>(-1)` instead. Expressions not including the `- 1` can often be re-written to accomodate the change (e.g. by using a `>` rather than a `>=`, which will also save some gas).

*There are 44 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/PanopticPool.sol

166: 		    uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

166: 		    uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

1354: 		                Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

1359: 		                Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

1493: 		            effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

1558: 		                                        (liquidityChunk.liquidity())) / 2 ** 64

1567: 		                                        (liquidityChunk.liquidity())) / 2 ** 64

1641: 		                .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1642: 		                .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1775: 		                totalLiquidity) / 2 ** 64;

1777: 		                totalLiquidity) / 2 ** 64;

1948: 		                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),

1965: 		                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
```
[[166](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L166), [166](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L166), [1354](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1354), [1359](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1359), [1493](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1493), [1558](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1558), [1567](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1567), [1641](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1641), [1642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1642), [1775](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1775), [1777](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1777), [1948](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1948), [1965](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1965)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

388: 		            s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;

1353: 		                    totalLiquidity * 2 ** 64,

1358: 		                    totalLiquidity * 2 ** 64,
```
[[388](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L388), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1353), [1358](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1358)]



```solidity
File: contracts/libraries/Math.sol

15: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

15: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

484: 		            require(2 ** 64 > prod1);

511: 		            prod0 |= prod1 * 2 ** 192;

547: 		            require(2 ** 96 > prod1);

574: 		            prod0 |= prod1 * 2 ** 160;

587: 		            if (mulmod(a, b, 2 ** 96) > 0) {

624: 		            require(2 ** 128 > prod1);

651: 		            prod0 |= prod1 * 2 ** 128;

664: 		            if (mulmod(a, b, 2 ** 128) > 0) {

701: 		            require(2 ** 192 > prod1);

728: 		            prod0 |= prod1 * 2 ** 64;
```
[[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L15), [15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L15), [484](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L484), [511](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L511), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L547), [574](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L574), [587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L587), [624](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L624), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L651), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L664), [701](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L701), [728](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L728)]



```solidity
File: contracts/libraries/PanopticMath.sol

23: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

23: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

512: 		                return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

514: 		                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

553: 		                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

560: 		                        2 ** 128,

685: 		                        Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
```
[[23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L23), [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L23), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L512), [514](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L514), [553](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L553), [560](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L560), [685](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L685)]



```solidity
File: contracts/types/TokenId.sol

98: 		            return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

376: 		            if (optionRatios < 2 ** 64) {

378: 		            } else if (optionRatios < 2 ** 112) {

380: 		            } else if (optionRatios < 2 ** 160) {

382: 		            } else if (optionRatios < 2 ** 208) {

439: 		        if (optionRatios < 2 ** 64) {

441: 		        } else if (optionRatios < 2 ** 112) {

443: 		        } else if (optionRatios < 2 ** 160) {

445: 		        } else if (optionRatios < 2 ** 208) {
```
[[98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L98), [376](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L376), [378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L378), [380](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L380), [382](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L382), [439](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L439), [441](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L441), [443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L443), [445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L445)]

</details>

---

### [N-31] Use of non-named numeric constants

Constants should be defined instead of using magic numbers.

*There are 285 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

// @audit 2000
200: 		            int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

// @audit 2230
202: 		                2230 +

// @audit 12500
203: 		                    (12500 * ratioTick) /

// @audit 10_000
204: 		                    10_000 +

// @audit 7812
205: 		                    (7812 * ratioTick ** 2) /

// @audit 10_000
206: 		                    10_000 ** 2 +

// @audit 6510
207: 		                    (6510 * ratioTick ** 3) /

// @audit 3
207: 		                    (6510 * ratioTick ** 3) /

// @audit 10_000
208: 		                    10_000 ** 3

// @audit 3
208: 		                    10_000 ** 3

// @audit 10
234: 		        totalSupply = 10 ** 6;

// @audit 6
234: 		        totalSupply = 10 ** 6;

// @audit 100
249: 		            _poolFee = fee / 100;

// @audit 64
1330: 		            : int64(uint64(poolUtilization >> 64));

// @audit 64
1586: 		                    : int64(uint64(poolUtilization >> 64))

// @audit 64
1632: 		            uint64 poolUtilization1 = uint64(poolUtilization >> 64);

// @audit 64
1638: 		                (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
```
[[200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L200), [202](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L203), [204](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L204), [205](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L205), [206](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L206), [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L207), [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L207), [208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L208), [208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L208), [234](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L234), [234](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L234), [249](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L249), [1330](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1330), [1586](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1586), [1632](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1632), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1638)]



```solidity
File: contracts/PanopticPool.sol

// @audit 216
310: 		                (uint256(block.timestamp) << 216) +

// @audit 0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000
313: 		                (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +

// @audit 24
314: 		                (uint256(uint24(currentTick)) << 24) + // add to slot 4

// @audit 64
371: 		        poolUtilization1 = uint64(balanceData.leftSlot() >> 64);

// @audit 4
449: 		                LeftRightSigned[4] memory premiaByLeg, //@audit-info positive premia

// @audit 4
450: 		                uint256[2][4] memory premiumAccumulatorsByLeg

// @audit 4
686: 		        (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM

// @audit 64
731: 		            return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

// @audit 4
801: 		    ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

// @audit 4
802: 		        premiasByLeg = new LeftRightSigned[4][](positionIdList.length);

// @audit 4
833: 		    ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

// @audit 4
967: 		            LeftRightSigned[4] memory premiaByLeg,

// @audit 4
971: 		        (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM

// @audit 4
1081: 		            LeftRightSigned[4][] memory premiasByLeg;

// @audit 10_000
1335: 		            return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

// @audit 96
1354: 		                Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

// @audit 96
1359: 		                Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

// @audit 248
1421: 		        if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

// @audit 248
1451: 		        _numberOfPositions = (s_positionsHash[user] >> 248);

// @audit 32
1493: 		            effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

// @audit 4
1519: 		            LeftRightSigned[4] memory premiaByLeg,

// @audit 4
1520: 		            uint256[2][4] memory premiumAccumulatorsByLeg

// @audit 64
1558: 		                                        (liquidityChunk.liquidity())) / 2 ** 64

// @audit 64
1567: 		                                        (liquidityChunk.liquidity())) / 2 ** 64

// @audit 3
1602: 		        if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

// @audit 64
1641: 		                .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

// @audit 64
1642: 		                .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

// @audit 4
1674: 		        LeftRightUnsigned[4] memory collectedByLeg,

// @audit 64
1775: 		                totalLiquidity) / 2 ** 64;

// @audit 64
1777: 		                totalLiquidity) / 2 ** 64;

// @audit 4
1842: 		        LeftRightUnsigned[4] memory collectedByLeg,

// @audit 4
1845: 		    ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {

// @audit 4
1847: 		        uint256[2][4] memory premiumAccumulatorsByLeg;

// @audit 4
1929: 		                        uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;

// @audit 64
1948: 		                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),

// @audit 64
1965: 		                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
```
[[310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L310), [313](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L313), [314](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L314), [371](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L371), [449](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L449), [450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L450), [686](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L686), [731](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L731), [801](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L801), [802](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L802), [833](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L833), [967](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L967), [971](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L971), [1081](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1081), [1335](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1335), [1354](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1354), [1359](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1359), [1421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1421), [1451](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1451), [1493](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1493), [1519](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1519), [1520](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1520), [1558](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1558), [1567](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1567), [1602](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1602), [1641](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1641), [1642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1642), [1674](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1674), [1775](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1775), [1777](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1777), [1842](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1842), [1845](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1845), [1847](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1847), [1929](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1929), [1948](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1948), [1965](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1965)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit 255
388: 		            s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;

// @audit 4
479: 		        returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)

// @audit 4
512: 		        returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)

// @audit 4
687: 		    ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

// @audit 4
873: 		            LeftRightUnsigned[4] memory collectedByLeg,

// @audit 64
1353: 		                    totalLiquidity * 2 ** 64,

// @audit 64
1358: 		                    totalLiquidity * 2 ** 64,
```
[[388](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L388), [479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L479), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L512), [687](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L687), [873](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L873), [1353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1353), [1358](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1358)]



```solidity
File: contracts/libraries/Math.sol

// @audit 0x100000000000000000000000000000000
93: 		            if (x >= 0x100000000000000000000000000000000) {

// @audit 128
94: 		                x >>= 128;

// @audit 32
95: 		                r += 32;

// @audit 0x10000000000000000
97: 		            if (x >= 0x10000000000000000) {

// @audit 64
98: 		                x >>= 64;

// @audit 16
99: 		                r += 16;

// @audit 0x100000000
101: 		            if (x >= 0x100000000) {

// @audit 32
102: 		                x >>= 32;

// @audit 8
103: 		                r += 8;

// @audit 0x10000
105: 		            if (x >= 0x10000) {

// @audit 16
106: 		                x >>= 16;

// @audit 4
107: 		                r += 4;

// @audit 0x100
109: 		            if (x >= 0x100) {

// @audit 8
110: 		                x >>= 8;

// @audit 0x10
113: 		            if (x >= 0x10) {

// @audit 0x1
133: 		            uint256 sqrtR = absTick & 0x1 != 0

// @audit 0xfffcb933bd6fad37aa2d162d1a594001
134: 		                ? 0xfffcb933bd6fad37aa2d162d1a594001

// @audit 0x100000000000000000000000000000000
135: 		                : 0x100000000000000000000000000000000;

// @audit 0x2
137: 		            if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

// @audit 0xfff97272373d413259a46990580e213a
137: 		            if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

// @audit 128
137: 		            if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

// @audit 0x4
139: 		            if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

// @audit 0xfff2e50f5f656932ef12357cf3c7fdcc
139: 		            if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

// @audit 128
139: 		            if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

// @audit 0x8
141: 		            if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

// @audit 0xffe5caca7e10e4e61c3624eaa0941cd0
141: 		            if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

// @audit 128
141: 		            if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

// @audit 0x10
143: 		            if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;

// @audit 0xffcb9843d60f6159c9db58835c926644
143: 		            if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;

// @audit 128
143: 		            if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;

// @audit 0x20
145: 		            if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

// @audit 0xff973b41fa98c081472e6896dfb254c0
145: 		            if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

// @audit 128
145: 		            if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

// @audit 0x40
147: 		            if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;

// @audit 0xff2ea16466c96a3843ec78b326b52861
147: 		            if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;

// @audit 128
147: 		            if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;

// @audit 0x80
149: 		            if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;

// @audit 0xfe5dee046a99a2a811c461f1969c3053
149: 		            if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;

// @audit 128
149: 		            if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;

// @audit 0x100
151: 		            if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;

// @audit 0xfcbe86c7900a88aedcffc83b479aa3a4
151: 		            if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;

// @audit 128
151: 		            if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;

// @audit 0x200
153: 		            if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

// @audit 0xf987a7253ac413176f2b074cf7815e54
153: 		            if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

// @audit 128
153: 		            if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

// @audit 0x400
155: 		            if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

// @audit 0xf3392b0822b70005940c7a398e4b70f3
155: 		            if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

// @audit 128
155: 		            if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

// @audit 0x800
157: 		            if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

// @audit 0xe7159475a2c29b7443b29c7fa6e889d9
157: 		            if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

// @audit 128
157: 		            if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

// @audit 0x1000
159: 		            if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;

// @audit 0xd097f3bdfd2022b8845ad8f792aa5825
159: 		            if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;

// @audit 128
159: 		            if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;

// @audit 0x2000
161: 		            if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

// @audit 0xa9f746462d870fdf8a65dc1f90e061e5
161: 		            if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

// @audit 128
161: 		            if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

// @audit 0x4000
163: 		            if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;

// @audit 0x70d869a156d2a1b890bb3df62baf32f7
163: 		            if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;

// @audit 128
163: 		            if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;

// @audit 0x8000
165: 		            if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;

// @audit 0x31be135f97d08fd981231505542fcfa6
165: 		            if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;

// @audit 128
165: 		            if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;

// @audit 0x10000
167: 		            if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

// @audit 0x9aa508b5b7a84e1c677de54f3e99bc9
167: 		            if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

// @audit 128
167: 		            if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

// @audit 0x20000
169: 		            if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;

// @audit 0x5d6af8dedb81196699c329225ee604
169: 		            if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;

// @audit 128
169: 		            if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;

// @audit 0x40000
171: 		            if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

// @audit 0x2216e584f5fa1ea926041bedfe98
171: 		            if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

// @audit 128
171: 		            if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

// @audit 0x80000
173: 		            if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

// @audit 0x48a170391f7dc42444e8fa2
173: 		            if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

// @audit 128
173: 		            if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

// @audit 32
179: 		            return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

// @audit 32
179: 		            return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

// @audit 96
197: 		                    uint256(liquidityChunk.liquidity()) << 96,

// @audit 3
414: 		            uint256 inv = (3 * denominator) ^ 2;

// @audit 64
484: 		            require(2 ** 64 > prod1);

// @audit 192
511: 		            prod0 |= prod1 * 2 ** 192;

// @audit 96
547: 		            require(2 ** 96 > prod1);

// @audit 160
574: 		            prod0 |= prod1 * 2 ** 160;

// @audit 96
587: 		            if (mulmod(a, b, 2 ** 96) > 0) {

// @audit 128
624: 		            require(2 ** 128 > prod1);

// @audit 128
651: 		            prod0 |= prod1 * 2 ** 128;

// @audit 128
664: 		            if (mulmod(a, b, 2 ** 128) > 0) {

// @audit 192
701: 		            require(2 ** 192 > prod1);

// @audit 64
728: 		            prod0 |= prod1 * 2 ** 64;
```
[[93](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L93), [94](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L94), [95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L95), [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L97), [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L98), [99](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L99), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L101), [102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L102), [103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L105), [106](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L106), [107](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L107), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L109), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L110), [113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L113), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L133), [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L134), [135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L135), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L137), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L137), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L137), [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L139), [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L139), [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L139), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L141), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L141), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L141), [143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L143), [143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L143), [143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L143), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L145), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L145), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L145), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L147), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L147), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L147), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L149), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L149), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L149), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L151), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L151), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L151), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L153), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L153), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L153), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L155), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L155), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L155), [157](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L157), [157](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L157), [157](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L157), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L159), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L159), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L159), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L161), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L161), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L161), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L163), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L163), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L163), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L165), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L165), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L165), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L167), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L167), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L167), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L169), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L169), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L169), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L171), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L171), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L171), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L173), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L173), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L173), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L179), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L179), [197](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L197), [414](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L414), [484](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L484), [511](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L511), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L547), [574](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L574), [587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L587), [624](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L624), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L651), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L664), [701](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L701), [728](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L728)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit 112
50: 		            uint64 poolId = uint64(uint160(univ3pool) >> 112);

// @audit 48
51: 		            poolId += uint64(uint24(tickSpacing)) << 48;

// @audit 40
77: 		            return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

// @audit 39
77: 		            return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

// @audit 248
107: 		                    ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)

// @audit 248
107: 		                    ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)

// @audit 248
108: 		                    : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);

// @audit 248
108: 		                    : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);

// @audit 192
178: 		                (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

// @audit 3
178: 		                (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

// @audit 3
178: 		                (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

// @audit 8
178: 		                (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

// @audit 24
178: 		                (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

// @audit 192
179: 		                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

// @audit 3
179: 		                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

// @audit 4
179: 		                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

// @audit 8
179: 		                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

// @audit 24
179: 		                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

// @audit 216
183: 		            if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

// @audit 192
200: 		                uint24 orderMap = uint24(medianData >> 192);

// @audit 8
207: 		                for (uint8 i; i < 8; ++i) {

// @audit 3
209: 		                    rank = (orderMap >> (3 * i)) % 8;

// @audit 8
209: 		                    rank = (orderMap >> (3 * i)) % 8;

// @audit 7
211: 		                    if (rank == 7) {

// @audit 24
217: 		                    entry = int24(uint24(medianData >> (rank * 24)));

// @audit 3
223: 		                    newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));

// @audit 216
227: 		                    (block.timestamp << 216) +

// @audit 192
228: 		                    (uint256(newOrderMap) << 192) +

// @audit 24
229: 		                    uint256(uint192(medianData << 24)) +

// @audit 20
242: 		        uint32[] memory secondsAgos = new uint32[](20);

// @audit 19
244: 		        int256[] memory twapMeasurement = new int256[](19);

// @audit 20
248: 		            for (uint256 i = 0; i < 20; ++i) {

// @audit 20
249: 		                secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);

// @audit 19
256: 		            for (uint256 i = 0; i < 19; ++i) {

// @audit 20
258: 		                    (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

// @audit 10
266: 		            return int24(sortedTicks[10]); //@audit-issue L - median should be (sortedTicks[9] + sortedTicks[10]) / 2

// @audit 192
512: 		                return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

// @audit 128
514: 		                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

// @audit 192
553: 		                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

// @audit 128
560: 		                        2 ** 128,

// @audit 128
669: 		                uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);

// @audit 128
685: 		                        Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

// @audit 4
771: 		        LeftRightSigned[4][] memory premiasByLeg, //@audit pos or neg?

// @audit 4
862: 		                LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
```
[[50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L50), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L51), [77](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L77), [77](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L77), [107](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L107), [107](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L107), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L108), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L108), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L178), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L178), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L178), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L178), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L178), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L179), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L179), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L179), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L179), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L179), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L183), [200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L200), [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L207), [209](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L209), [209](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L209), [211](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L211), [217](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L217), [223](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L223), [227](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L227), [228](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L228), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L229), [242](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L242), [244](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L244), [248](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L248), [249](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L249), [256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L256), [258](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L258), [266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L266), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L512), [514](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L514), [553](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L553), [560](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L560), [669](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L669), [685](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L685), [771](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L771), [862](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L862)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

// @audit 0x01ffc9a7
202: 		            interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

// @audit 0xd9b67a26
203: 		            interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155
```
[[202](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L203)]



```solidity
File: contracts/types/LeftRight.sol

// @audit 128
102: 		        return uint128(LeftRightUnsigned.unwrap(self) >> 128);

// @audit 128
109: 		        return int128(LeftRightSigned.unwrap(self) >> 128);

// @audit 128
126: 		            return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));

// @audit 128
136: 		            return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));
```
[[102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L109), [126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L126), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L136)]



```solidity
File: contracts/types/LiquidityChunk.sol

// @audit 232
79: 		                    (uint256(uint24(_tickLower)) << 232) +

// @audit 208
80: 		                        (uint256(uint24(_tickUpper)) << 208) +

// @audit 232
110: 		                    LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

// @audit 208
127: 		                    LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

// @audit 232
174: 		            return int24(int256(LiquidityChunk.unwrap(self) >> 232));

// @audit 208
183: 		            return int24(int256(LiquidityChunk.unwrap(self) >> 208));
```
[[79](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L79), [80](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L80), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L110), [127](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L127), [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L174), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L183)]



```solidity
File: contracts/types/TokenId.sol

// @audit 48
98: 		            return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

// @audit 16
98: 		            return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

// @audit 64
110: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

// @audit 48
110: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

// @audit 64
120: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

// @audit 48
120: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

// @audit 128
120: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

// @audit 64
130: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

// @audit 48
130: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

// @audit 8
130: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

// @audit 64
140: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

// @audit 48
140: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

// @audit 9
140: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

// @audit 64
150: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

// @audit 48
150: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

// @audit 10
150: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

// @audit 4
150: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

// @audit 64
160: 		            return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

// @audit 48
160: 		            return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

// @audit 12
160: 		            return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

// @audit 64
171: 		            return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

// @audit 48
171: 		            return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

// @audit 36
171: 		            return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

// @audit 4096
171: 		            return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

// @audit 48
195: 		            return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

// @audit 64
212: 		                TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

// @audit 48
212: 		                TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

// @audit 128
229: 		                    TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

// @audit 64
229: 		                    TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

// @audit 48
229: 		                    TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

// @audit 64
246: 		            return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

// @audit 48
246: 		            return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

// @audit 8
246: 		            return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

// @audit 64
263: 		                    TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

// @audit 48
263: 		                    TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

// @audit 9
263: 		                    TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

// @audit 4
281: 		                    TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

// @audit 64
281: 		                    TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

// @audit 48
281: 		                    TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

// @audit 10
281: 		                    TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

// @audit 64
300: 		                        uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))

// @audit 48
300: 		                        uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))

// @audit 12
300: 		                        uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))

// @audit 4096
320: 		                        (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

// @audit 64
320: 		                        (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

// @audit 48
320: 		                        (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

// @audit 36
320: 		                        (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

// @audit 64
376: 		            if (optionRatios < 2 ** 64) {

// @audit 112
378: 		            } else if (optionRatios < 2 ** 112) {

// @audit 160
380: 		            } else if (optionRatios < 2 ** 160) {

// @audit 208
382: 		            } else if (optionRatios < 2 ** 208) {

// @audit 3
383: 		                optionRatios = 3;

// @audit 4
385: 		                optionRatios = 4;

// @audit 48
395: 		                        ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)

// @audit 4
395: 		                        ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)

// @audit 3
406: 		            return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

// @audit 64
439: 		        if (optionRatios < 2 ** 64) {

// @audit 112
441: 		        } else if (optionRatios < 2 ** 112) {

// @audit 160
443: 		        } else if (optionRatios < 2 ** 160) {

// @audit 208
445: 		        } else if (optionRatios < 2 ** 208) {

// @audit 3
446: 		            return 3;

// @audit 4
448: 		        return 4;

// @audit 0xFFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFFFFFF
469: 		                        0xFFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFFFFFF

// @audit 0xFFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
475: 		                        0xFFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF

// @audit 0xFFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
481: 		                        0xFFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF

// @audit 3
483: 		        if (i == 3)

// @audit 0x000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
487: 		                        0x000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF

// @audit 64
506: 		            uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;

// @audit 4
507: 		            for (uint256 i = 0; i < 4; ++i) {

// @audit 64
512: 		                    if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

// @audit 48
512: 		                    if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

// @audit 48
521: 		                    if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {

// @audit 48
521: 		                    if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {

// @audit 6
522: 		                        revert Errors.InvalidTokenIdParameter(6);

// @audit 5
528: 		                if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

// @audit 4
533: 		                ) revert Errors.InvalidTokenIdParameter(4); //@audit-info what if is > or < tick?

// @audit 3
542: 		                        revert Errors.InvalidTokenIdParameter(3);

// @audit 3
548: 		                    ) revert Errors.InvalidTokenIdParameter(3);

// @audit 4
561: 		                        revert Errors.InvalidTokenIdParameter(4);

// @audit 5
567: 		                        revert Errors.InvalidTokenIdParameter(5);
```
[[98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L98), [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L98), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L110), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L110), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L120), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L120), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L120), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L130), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L130), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L130), [140](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L140), [140](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L140), [140](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L140), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L150), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L150), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L150), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L150), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L160), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L160), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L171), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L171), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L171), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L171), [195](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L195), [212](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L212), [212](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L212), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L229), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L229), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L229), [246](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L246), [246](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L246), [246](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L246), [263](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L263), [263](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L263), [263](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L263), [281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L281), [281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L281), [281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L281), [281](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L281), [300](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L300), [300](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L300), [300](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L300), [320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L320), [320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L320), [320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L320), [320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L320), [376](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L376), [378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L378), [380](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L380), [382](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L382), [383](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L383), [385](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L385), [395](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L395), [395](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L395), [406](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L406), [439](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L439), [441](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L441), [443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L443), [445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L445), [446](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L446), [448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L448), [469](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L469), [475](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L475), [481](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L481), [483](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L483), [487](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L487), [506](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L506), [507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L507), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L512), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L512), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L521), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L521), [522](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L522), [528](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L528), [533](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L533), [542](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L542), [548](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L548), [561](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L561), [567](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L567)]

</details>

---

### [N-32] Consider splitting complex checks into multiple steps

Assign the expression's parts to intermediate local variables, and check against those instead.

*There are 23 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

708: 		                    (tokenType == 0 && currentValue1 < oracleValue1) ||
709: 		                    (tokenType == 1 && currentValue0 < oracleValue0)

1060: 		            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1060: 		            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1346: 		                    ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1
1347: 		                    ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1374: 		                        ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1
1375: 		                        ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0
```
[[708-709](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L708-L709), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1060), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1060), [1346-1347](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1346-L1347), [1374-1375](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1374-L1375)]



```solidity
File: contracts/PanopticFactory.sol

225: 		        if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();
```
[[225](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L225)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

632: 		                (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
633: 		                (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

788: 		            if ((itm0 != 0) && (itm1 != 0)) {
```
[[632-633](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L632-L633), [788](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L788)]



```solidity
File: contracts/libraries/PanopticMath.sol

357: 		                tickLower % tickSpacing != 0 ||
358: 		                tickUpper % tickSpacing != 0 ||
359: 		                tickLower < minTick ||
360: 		                tickUpper > maxTick

357: 		                tickLower % tickSpacing != 0 ||
358: 		                tickUpper % tickSpacing != 0 ||
359: 		                tickLower < minTick ||

357: 		                tickLower % tickSpacing != 0 ||
358: 		                tickUpper % tickSpacing != 0 ||
```
[[357-360](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L357-L360), [357-359](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L357-L359), [357-358](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L357-L358)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

202: 		            interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165
203: 		            interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

201: 		        return
202: 		            interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165
203: 		            interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155
```
[[202-203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L202-L203), [201-203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L201-L203)]



```solidity
File: contracts/types/LeftRight.sol

222: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

240: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

262: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

290: 		        bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);

291: 		        bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);
```
[[222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L222), [240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L240), [262](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L262), [290](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L290), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L291)]



```solidity
File: contracts/types/TokenId.sol

531: 		                    (self.strike(i) == Constants.MIN_V3POOL_TICK) ||
532: 		                    (self.strike(i) == Constants.MAX_V3POOL_TICK)

546: 		                        (self.asset(riskPartnerIndex) != self.asset(i)) ||
547: 		                        (self.optionRatio(riskPartnerIndex) != self.optionRatio(i))

560: 		                    if ((_isLong == isLongP) && (_tokenType == tokenTypeP))

566: 		                    if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

566: 		                    if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))
```
[[531-532](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L531-L532), [546-547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L546-L547), [560](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L560), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L566), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L566)]

</details>

---

### [N-33] Complex math should be split into multiple steps

Consider splitting long arithmetic calculations into multiple steps to improve the code readability.

*There are 53 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

201: 		            TICK_DEVIATION = uint256(
202: 		                2230 +
203: 		                    (12500 * ratioTick) /
204: 		                    10_000 +
205: 		                    (7812 * ratioTick ** 2) /
206: 		                    10_000 ** 2 +
207: 		                    (6510 * ratioTick ** 3) /
208: 		                    10_000 ** 3
209: 		            );

402: 		            shares = Math.mulDiv(
403: 		                assets * (DECIMALS - COMMISSION_FEE),
404: 		                totalSupply,
405: 		                totalAssets() * DECIMALS
406: 		            );

446: 		            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

795: 		            return
796: 		                min_sell_ratio +
797: 		                ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798: 		                (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);

848: 		            return
849: 		                (BUYER_COLLATERAL_RATIO +
850: 		                    (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851: 		                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

1119: 		            exchangedAmount += int256(
1120: 		                Math.unsafeDivRoundingUp(
1121: 		                    uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
1122: 		                    DECIMALS
1123: 		                )
1124: 		            );

1408: 		                        uint160 scaleFactor = Math.getSqrtRatioAtTick(
1409: 		                            (tickUpper - strike) + (strike - tickLower)
1410: 		                        );
```
[[201-209](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L201-L209), [402-406](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L402-L406), [446](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L446), [795-798](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L795-L798), [848-851](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L848-L851), [1119-1124](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1119-L1124), [1408-1410](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1408-L1410)]



```solidity
File: contracts/PanopticPool.sol

309: 		            s_miniMedian =
310: 		                (uint256(block.timestamp) << 216) +
311: 		                // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
312: 		                // see comment on s_miniMedian initialization for format of this magic number
313: 		                (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
314: 		                (uint256(uint24(currentTick)) << 24) + // add to slot 4
315: 		                (uint256(uint24(currentTick))); // add to slot 3

1493: 		            effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

1551: 		                    premiaByLeg[leg] = LeftRightSigned
1552: 		                        .wrap(0)
1553: 		                        .toRightSlot(
1554: 		                            int128(
1555: 		                                int256(
1556: 		                                    ((premiumAccumulatorsByLeg[leg][0] -
1557: 		                                        premiumAccumulatorLast.rightSlot()) *
1558: 		                                        (liquidityChunk.liquidity())) / 2 ** 64
1559: 		                                )
1560: 		                            )
1561: 		                        )
1562: 		                        .toLeftSlot(
1563: 		                            int128(
1564: 		                                int256(
1565: 		                                    ((premiumAccumulatorsByLeg[leg][1] -
1566: 		                                        premiumAccumulatorLast.leftSlot()) *
1567: 		                                        (liquidityChunk.liquidity())) / 2 ** 64
1568: 		                                )
1569: 		                            )
1570: 		                        );

1639: 		            LeftRightSigned realizedPremia = LeftRightSigned
1640: 		                .wrap(0)
1641: 		                .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))
1642: 		                .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1731: 		                    s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1732: 		                        .wrap(0)
1733: 		                        .toRightSlot(
1734: 		                            uint128(
1735: 		                                (grossCurrent[0] *
1736: 		                                    positionLiquidity +
1737: 		                                    grossPremiumLast.rightSlot() *
1738: 		                                    totalLiquidityBefore) / (totalLiquidity)
1739: 		                            )
1740: 		                        )
1741: 		                        .toLeftSlot(
1742: 		                            uint128(
1743: 		                                (grossCurrent[1] *
1744: 		                                    positionLiquidity +
1745: 		                                    grossPremiumLast.leftSlot() *
1746: 		                                    totalLiquidityBefore) / (totalLiquidity)
1747: 		                            )
1748: 		                        );

1774: 		            uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *
1775: 		                totalLiquidity) / 2 ** 64;

1776: 		            uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *
1777: 		                totalLiquidity) / 2 ** 64;
```
[[309-315](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L309-L315), [1493](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1493), [1551-1570](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1551-L1570), [1639-1642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1639-L1642), [1731-1748](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1731-L1748), [1774-1775](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1774-L1775), [1776-1777](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1776-L1777)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

1368: 		                    uint256 numerator = netLiquidity + (removedLiquidity / 2 ** VEGOID);

1389: 		                    uint256 numerator = totalLiquidity ** 2 -
1390: 		                        totalLiquidity *
1391: 		                        removedLiquidity +
1392: 		                        ((removedLiquidity ** 2) / 2 ** (VEGOID));
```
[[1368](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1368), [1389-1392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1389-L1392)]



```solidity
File: contracts/libraries/Math.sol

418: 		            inv *= 2 - denominator * inv; // inverse mod 2**8

419: 		            inv *= 2 - denominator * inv; // inverse mod 2**16

420: 		            inv *= 2 - denominator * inv; // inverse mod 2**32

421: 		            inv *= 2 - denominator * inv; // inverse mod 2**64

422: 		            inv *= 2 - denominator * inv; // inverse mod 2**128

423: 		            inv *= 2 - denominator * inv; // inverse mod 2**256

758: 		            int256 pivot = arr[uint256(left + (right - left) / 2)];
```
[[418](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L418), [419](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L419), [420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L420), [421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L421), [422](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L422), [423](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L423), [758](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L758)]



```solidity
File: contracts/libraries/PanopticMath.sol

138: 		                (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
139: 		                    uint256(
140: 		                        (int256(observationIndex) - int256(i * period)) +
141: 		                            int256(observationCardinality)
142: 		                    ) % observationCardinality
143: 		                );

149: 		                ticks[i] =
150: 		                    (tickCumulatives[i] - tickCumulatives[i + 1]) /
151: 		                    int256(timestamps[i] - timestamps[i + 1]);

186: 		                    (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(
187: 		                        uint256(
188: 		                            int256(observationIndex) - int256(1) + int256(observationCardinality)
189: 		                        ) % observationCardinality
190: 		                    );

177: 		            medianTick =
178: 		                (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
179: 		                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
180: 		                2;

194: 		                    lastObservedTick = int24(
195: 		                        (tickCumulative_last - tickCumulative_old) /
196: 		                            int256(timestamp_last - timestamp_old)
197: 		                    );

209: 		                    rank = (orderMap >> (3 * i)) % 8;

223: 		                    newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));

226: 		                updatedMedianData =
227: 		                    (block.timestamp << 216) +
228: 		                    (uint256(newOrderMap) << 192) +
229: 		                    uint256(uint192(medianData << 24)) +
230: 		                    uint256(uint24(lastObservedTick));

249: 		                secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);

257: 		                twapMeasurement[i] = int24(
258: 		                    (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
259: 		                );

375: 		        return (
376: 		            (width * tickSpacing) / 2,
377: 		            int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))
378: 		        );

669: 		                uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);
```
[[138-143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L138-L143), [149-151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L149-L151), [186-190](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L186-L190), [177-180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L177-L180), [194-197](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L194-L197), [209](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L209), [223](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L223), [226-230](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L226-L230), [249](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L249), [257-259](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L257-L259), [375-378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L375-L378), [669](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L669)]



```solidity
File: contracts/types/LiquidityChunk.sol

77: 		            return
78: 		                LiquidityChunk.wrap(
79: 		                    (uint256(uint24(_tickLower)) << 232) +
80: 		                        (uint256(uint24(_tickUpper)) << 208) +
81: 		                        uint256(amount)
82: 		                );
```
[[77-82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L77-L82)]



```solidity
File: contracts/types/TokenId.sol

98: 		            return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

110: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

120: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

130: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

140: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

150: 		            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

160: 		            return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

171: 		            return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

211: 		            return
212: 		                TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

227: 		            return
228: 		                TokenId.wrap(
229: 		                    TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))
230: 		                );

246: 		            return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

261: 		            return
262: 		                TokenId.wrap(
263: 		                    TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))
264: 		                );

279: 		            return
280: 		                TokenId.wrap(
281: 		                    TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))
282: 		                );

297: 		            return
298: 		                TokenId.wrap(
299: 		                    TokenId.unwrap(self) +
300: 		                        uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))
301: 		                );

317: 		            return
318: 		                TokenId.wrap(
319: 		                    TokenId.unwrap(self) +
320: 		                        (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))
321: 		                );

392: 		            return
393: 		                TokenId.wrap(
394: 		                    TokenId.unwrap(self) ^
395: 		                        ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)
396: 		                );

406: 		            return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);
```
[[98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L98), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L110), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L120), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L130), [140](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L140), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L150), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L171), [211-212](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L211-L212), [227-230](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L227-L230), [246](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L246), [261-264](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L261-L264), [279-282](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L279-L282), [297-301](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L297-L301), [317-321](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L317-L321), [392-396](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L392-L396), [406](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L406)]

</details>

---

### [N-34] Time related variables should use time units instead of numbers

There are [units](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#time-units) for seconds, minutes, hours, days, and weeks, and since they're defined, they should be used

*There are 3 instances of this issue.*


```solidity
File: contracts/PanopticPool.sol

137: 		    uint256 internal constant MEDIAN_PERIOD = 60;

146: 		    uint256 internal constant FAST_ORACLE_PERIOD = 1;

153: 		    uint256 internal constant SLOW_ORACLE_PERIOD = 5;
```
[[137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L137), [146](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L146), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L153)]


---

### [N-35] Control structures do not comply with best practices

This is a [best practice](https://docs.soliditylang.org/en/latest/style-guide.html#control-structures) that should be followed. 

*There are 120 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

170: 		        if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

229: 		        if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();

331: 		        if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

350: 		        if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

418: 		        if (assets > type(uint104).max) revert Errors.DepositTooLarge();

480: 		        if (assets > type(uint104).max) revert Errors.DepositTooLarge();

536: 		        if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

544: 		            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

596: 		        if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

602: 		            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

664: 		                if (positionId.isLong(leg) == 0) continue;

707: 		                if (

1257: 		                if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;

1345: 		                if (

1373: 		                    if (
```
[[170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L170), [229](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L229), [331](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L331), [350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L350), [418](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L418), [480](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L480), [536](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L536), [544](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L544), [596](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L596), [602](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L602), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L664), [707](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L707), [1257](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1257), [1345](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1345), [1373](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1373)]



```solidity
File: contracts/PanopticFactory.sol

151: 		        if (msg.sender != currentOwner) revert Errors.NotOwner();

182: 		        if (amount0Owed > 0)

189: 		        if (amount1Owed > 0)

221: 		        if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

225: 		        if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

228: 		        if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

230: 		        if (address(s_getPanopticPool[v3Pool]) != address(0))
```
[[151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L151), [182](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L182), [189](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L189), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L221), [225](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L225), [228](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L228), [230](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L230)]



```solidity
File: contracts/PanopticPool.sol

300: 		        if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

534: 		        if (medianData != 0) s_miniMedian = medianData;

634: 		        if (tokenId.poolId() != SFPM.getPoolId(address(s_univ3pool)))

639: 		        if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

665: 		        if (medianData != 0) s_miniMedian = medianData;

941: 		        if (!solventAtFast) revert Errors.NotEnoughCollateral();

944: 		        if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

945: 		            if (!_checkSolvencyAtTick(user, positionIdList, currentTick, slowOracleTick, buffer))

1036: 		            if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

1067: 		            if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();

1156: 		        if (

1189: 		        if (touchedId.length != 1) revert Errors.InputListFail();

1280: 		        if (positionIdListExercisor.length > 0)

1400: 		        if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();

1421: 		        if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

1489: 		        if (netLiquidity == 0) return;

1498: 		        if (effectiveLiquidityFactorX32 > uint256(effectiveLiquidityLimitX32))

1602: 		        if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1871: 		                    if (commitLongSettled)
```
[[300](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L300), [534](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L534), [634](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L634), [639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L639), [665](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L665), [941](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L941), [944](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L944), [945](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L945), [1036](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1036), [1067](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1067), [1156](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1156), [1189](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1189), [1280](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1280), [1400](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1400), [1421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1421), [1489](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1489), [1498](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1498), [1602](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1602), [1871](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1871)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

322: 		        if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();

355: 		        if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

362: 		        if (s_AddrToPoolIdData[univ3pool] != 0) return;

412: 		        if (amount0Owed > 0)

419: 		        if (amount1Owed > 0)

549: 		        if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

576: 		            if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

631: 		            if (

639: 		            if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity()) //@audit-ok before it checked only the rightSlot

689: 		        if (positionSize == 0) revert Errors.OptionsBalanceZero();

703: 		        if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

728: 		        if ((currentTick >= tickLimitHigh) || (currentTick <= tickLimitLow)) //@audit-issue L off by one

834: 		            if (swapAmount == 0) return LeftRightSigned.wrap(0);

940: 		        if (amount0 > uint128(type(int128).max) || amount1 > uint128(type(int128).max))
```
[[322](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L322), [355](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L355), [362](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L362), [412](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L412), [419](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L419), [549](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L549), [576](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L576), [631](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L631), [639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L639), [689](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L689), [703](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L703), [728](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L728), [834](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L834), [940](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L940)]



```solidity
File: contracts/libraries/CallbackLib.sol

37: 		        if (factory.getPool(features.token0, features.token1, features.fee) != sender)
```
[[37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L37)]



```solidity
File: contracts/libraries/Math.sol

131: 		            if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

137: 		            if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

139: 		            if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

141: 		            if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

143: 		            if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;

145: 		            if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

147: 		            if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;

149: 		            if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;

151: 		            if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;

153: 		            if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

155: 		            if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

157: 		            if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

159: 		            if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;

161: 		            if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

163: 		            if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;

165: 		            if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;

167: 		            if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

169: 		            if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;

171: 		            if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

173: 		            if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

176: 		            if (tick > 0) sqrtR = type(uint256).max / sqrtR;

297: 		        if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

312: 		        if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

319: 		        if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

326: 		        if (toCast > uint256(type(int256).max)) revert Errors.CastingError();

757: 		            if (i == j) return;

768: 		            if (left < j) quickSort(arr, left, j);

769: 		            if (i < right) quickSort(arr, i, right);

760: 		                while (arr[uint256(i)] < pivot) i++;

761: 		                while (pivot < arr[uint256(j)]) j--;
```
[[131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L131), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L137), [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L139), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L141), [143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L143), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L145), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L147), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L149), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L151), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L153), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L155), [157](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L157), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L159), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L161), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L163), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L165), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L167), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L169), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L171), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L173), [176](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L176), [297](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L297), [312](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L312), [319](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L319), [326](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L326), [757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L757), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L768), [769](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L769), [760](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L760), [761](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L761)]



```solidity
File: contracts/libraries/PanopticMath.sol

356: 		            if (

479: 		            if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

797: 		            if (

821: 		            } else if (

856: 		                if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857: 		                if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
```
[[356](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L356), [479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L479), [797](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L797), [821](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L821), [856](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L857)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

46: 		        if (!success) revert Errors.TransferFailed();

76: 		        if (!success) revert Errors.TransferFailed();
```
[[46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L46), [76](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L76)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

101: 		        if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

113: 		            if (

137: 		        if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

164: 		            if (

223: 		            if (
```
[[101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L101), [113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L113), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L137), [164](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L164), [223](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L223)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

85: 		        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
```
[[85](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L85)]



```solidity
File: contracts/types/LeftRight.sol

160: 		            if (

183: 		            if (

199: 		            if (left128 != left) revert Errors.UnderOverFlow();

204: 		            if (right128 != right) revert Errors.UnderOverFlow();

222: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

240: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

262: 		            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
```
[[160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L160), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L183), [199](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L199), [204](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L204), [222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L222), [240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L240), [262](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L262)]



```solidity
File: contracts/types/TokenId.sol

465: 		        if (i == 0)

471: 		        if (i == 1)

477: 		        if (i == 2)

483: 		        if (i == 3)

501: 		        if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

512: 		                    if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

528: 		                if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

530: 		                if (

541: 		                    if (self.riskPartner(riskPartnerIndex) != i)

545: 		                    if (

560: 		                    if ((_isLong == isLongP) && (_tokenType == tokenTypeP))

566: 		                    if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

592: 		                    if (self.isLong(i) == 1) return; // validated
```
[[465](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L465), [471](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L471), [477](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L477), [483](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L483), [501](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L501), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L512), [528](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L528), [530](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L530), [541](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L541), [545](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L545), [560](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L560), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L566), [592](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L592)]

</details>

---

### [N-36] Use a single file for system wide constants

Consider grouping all the system constants under a single file. This finding shows only the first constant for each file, for brevity.

*There are 10 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

70: 		    string internal constant TICKER_PREFIX = "po";
```
[[70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L70)]



```solidity
File: contracts/PanopticFactory.sol

83: 		    uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;
```
[[83](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L83)]



```solidity
File: contracts/PanopticPool.sol

104: 		    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;
```
[[104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L104)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

125: 		    bool internal constant MINT = false;
```
[[125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L125)]



```solidity
File: contracts/libraries/Constants.sol

10: 		    uint256 internal constant FP96 = 0x1000000000000000000000000;
```
[[10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L10)]



```solidity
File: contracts/libraries/Math.sol

15: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```
[[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L15)]



```solidity
File: contracts/libraries/PanopticMath.sol

23: 		    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```
[[23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L23)]



```solidity
File: contracts/types/LeftRight.sol

22: 		    uint256 internal constant LEFT_HALF_BIT_MASK =
23: 		        0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000;
```
[[22-23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L22-L23)]



```solidity
File: contracts/types/LiquidityChunk.sol

55: 		    uint256 internal constant CLEAR_TL_MASK =
56: 		        0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;
```
[[55-56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L55-L56)]



```solidity
File: contracts/types/TokenId.sol

62: 		    uint256 internal constant LONG_MASK =
63: 		        0x100_000000000100_000000000100_000000000100_0000000000000000;
```
[[62-63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L62-L63)]

</details>

---

### [N-37] Old Solidity version

Use a more recent version of Solidity: it's safer to use at least the version 0.8.19 to get the latest bugfixes and features when deploying on L2.

*There are 20 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L2)]



```solidity
File: contracts/PanopticFactory.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L2)]



```solidity
File: contracts/PanopticPool.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L2)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L2)]



```solidity
File: contracts/libraries/CallbackLib.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L2)]



```solidity
File: contracts/libraries/Constants.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L2)]



```solidity
File: contracts/libraries/Errors.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L2)]



```solidity
File: contracts/libraries/FeesCalc.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L2)]



```solidity
File: contracts/libraries/InteractionHelper.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L2)]



```solidity
File: contracts/libraries/Math.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L2)]



```solidity
File: contracts/libraries/PanopticMath.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L2)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L2)]



```solidity
File: contracts/multicall/Multicall.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L2)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L2)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L2)]



```solidity
File: contracts/types/LeftRight.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L2)]



```solidity
File: contracts/types/LiquidityChunk.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L2)]



```solidity
File: contracts/types/TokenId.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L2)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L2)]



```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L2)]

</details>

---

### [N-38] Use of floating pragma

Locking the pragma helps avoid accidental deploys with an outdated compiler version that may introduce bugs and unexpected vulnerabilities.

Floating pragma is meant to be used for libraries and contracts that have external users and need backward compatibility.

*There are 9 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L2)]



```solidity
File: contracts/PanopticFactory.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L2)]



```solidity
File: contracts/PanopticPool.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L2)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L2)]



```solidity
File: contracts/multicall/Multicall.sol

2: 		pragma solidity ^0.8.18;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L2)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L2)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L2)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L2)]



```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

2: 		pragma solidity ^0.8.0;
```
[[2](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L2)]

</details>

---

### [N-39] No checks for empty bytes

Like the zero-address check, an empty bytes assignment might be undesiderable, but the following functions don't have it.

*There is 1 instance of this issue.*


```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit positionKey
1111: 		    function _updateStoredPremia(
1112: 		        bytes32 positionKey,
1113: 		        LeftRightUnsigned currentLiquidity,
1114: 		        LeftRightUnsigned collectedAmounts //@audit-ok was signed
```
[[1111-1114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1111-L1114)]


---

### [N-40] Use of `abi.encodePacked` instead of `bytes.concat`

Starting from version `0.8.4`, the recommended approach for appending bytes is to use `bytes.concat` instead of `abi.encodePacked`.

*There are 5 instances of this issue.*


```solidity
File: contracts/PanopticPool.sol

463: 		                        abi.encodePacked(
464: 		                            tokenId.strike(leg),
465: 		                            tokenId.width(leg),
466: 		                            tokenId.tokenType(leg)
467: 		                        ) //@audit-info collision between two legs? (isLong or riskPartner)

1649: 		                abi.encodePacked(
1650: 		                    tokenId.strike(legIndex),
1651: 		                    tokenId.width(legIndex),
1652: 		                    tokenId.tokenType(legIndex)
1653: 		                )

1680: 		                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

1862: 		                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
```
[[463-467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L463-L467), [1649-1653](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1649-L1653), [1680](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1680), [1862](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1862)]



```solidity
File: contracts/libraries/PanopticMath.sol

879: 		                            abi.encodePacked(
880: 		                                tokenId.strike(0),
881: 		                                tokenId.width(0),
882: 		                                tokenId.tokenType(0)
883: 		                            )
```
[[879-883](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L879-L883)]


---

### [N-41] Contract functions should use an `interface`

All `external`/`public` functions should override an `interface`. This is useful to make sure that the whole API is extracted.

*There are 85 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

221: 		    function startToken(

277: 		    function getPoolData()

289: 		    function name() external view returns (string memory) {

303: 		    function symbol() external view returns (string memory) {

310: 		    function decimals() external view returns (uint8) {

361: 		    function asset() external view returns (address assetTokenAddress) {

370: 		    function totalAssets() public view returns (uint256 totalManagedAssets) {

379: 		    function convertToShares(uint256 assets) public view returns (uint256 shares) {

386: 		    function convertToAssets(uint256 shares) public view returns (uint256 assets) {

392: 		    function maxDeposit(address) external pure returns (uint256 maxAssets) {

399: 		    function previewDeposit(uint256 assets) public view returns (uint256 shares) {

417: 		    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {

444: 		    function maxMint(address) external view returns (uint256 maxShares) {

453: 		    function previewMint(uint256 shares) public view returns (uint256 assets) {

477: 		    function mint(uint256 shares, address receiver) external returns (uint256 assets) {

507: 		    function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

518: 		    function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

531: 		    function withdraw(

572: 		    function maxRedeem(address owner) public view returns (uint256 maxShares) {

581: 		    function previewRedeem(uint256 shares) public view returns (uint256 assets) {

591: 		    function redeem(

650: 		    function exerciseCost(

864: 		    function delegate(

894: 		    function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

903: 		    function refund(address delegatee, uint256 assets) external onlyPanopticPool {

911: 		    function revoke(

975: 		    function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

995: 		    function takeCommissionAddData(

1043: 		    function exercise(

1141: 		    function getAccountMarginDetails(
```
[[221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L221), [277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L277), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L310), [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L370), [379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L392), [399](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L399), [417](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L417), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L444), [453](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L453), [477](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L477), [507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L507), [518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L518), [531](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L531), [572](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L581), [591](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L591), [650](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L650), [864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L864), [894](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L894), [903](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L903), [911](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L911), [975](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L975), [995](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L995), [1043](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1043), [1141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1141)]



```solidity
File: contracts/PanopticFactory.sol

135: 		    function initialize(address _owner) public {

148: 		    function transferOwnership(address newOwner) external {

160: 		    function owner() external view returns (address) {

173: 		    function uniswapV3MintCallback(

211: 		    function deployNewPool(

291: 		    function minePoolAddress(

421: 		    function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {
```
[[135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L135), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L148), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L160), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L173), [211](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L211), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L291), [421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L421)]



```solidity
File: contracts/PanopticPool.sol

292: 		    function startPool(

339: 		    function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {

353: 		    function optionPositionBalance(

382: 		    function calculateAccumulatedFeesBatch(

411: 		    function calculatePortfolioValue(

523: 		    function pokeMedian() external {

548: 		    function mintOptions(

570: 		    function burnOptions(

587: 		    function burnOptions(

1018: 		    function liquidate(

1180: 		    function forceExercise(

1431: 		    function univ3pool() external view returns (IUniswapV3Pool) {

1437: 		    function collateralToken0() external view returns (CollateralTracker collateralToken) {

1443: 		    function collateralToken1() external view returns (CollateralTracker) {

1450: 		    function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

1593: 		    function settleLongPremium(
```
[[292](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L292), [339](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L339), [353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L353), [382](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L382), [411](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L411), [523](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L523), [548](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L548), [570](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L570), [587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L587), [1018](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1018), [1180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1180), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1437), [1443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1443), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1450), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1593)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

350: 		    function initializeAMMPool(address token0, address token1, uint24 fee) external {

402: 		    function uniswapV3MintCallback(

435: 		    function uniswapV3SwapCallback(

471: 		    function burnTokenizedPosition(

504: 		    function mintTokenizedPosition(

1422: 		    function getAccountLiquidity(

1450: 		    function getAccountPremium(

1536: 		    function getAccountFeesBase(

1556: 		    function getUniswapV3PoolFromId(

1567: 		    function getPoolId(address univ3pool) external view returns (uint64 poolId) {
```
[[350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L350), [402](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L402), [435](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L435), [471](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L471), [504](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L504), [1422](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1422), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1450), [1536](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1536), [1556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1556), [1567](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1567)]



```solidity
File: contracts/libraries/FeesCalc.sol

46: 		    function getPortfolioValue(

97: 		    function calculateAMMSwapFees(
```
[[46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L46), [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L97)]



```solidity
File: contracts/libraries/InteractionHelper.sol

25: 		    function doApprovals(

49: 		    function computeName(

92: 		    function computeSymbol(

108: 		    function computeDecimals(address token) external view returns (uint8) {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L25), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L49), [92](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L92), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L108)]



```solidity
File: contracts/libraries/PanopticMath.sol

75: 		    function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

125: 		    function computeMedianObservedPrice(

168: 		    function computeInternalMedian(

241: 		    function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

651: 		    function getLiquidationBonus(

768: 		    function haircutPremia(

917: 		    function getRefundAmounts(
```
[[75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L75), [125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L125), [168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L168), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L241), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768), [917](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L917)]



```solidity
File: contracts/multicall/Multicall.sol

12: 		    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L12)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

81: 		    function setApprovalForAll(address operator, bool approved) public {

94: 		    function safeTransferFrom(

130: 		    function safeBatchTransferFrom(

178: 		    function balanceOfBatch(

200: 		    function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
```
[[81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L81), [94](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L94), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L130), [178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L178), [200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L200)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

50: 		    function approve(address spender, uint256 amount) public returns (bool) {

62: 		    function transfer(address to, uint256 amount) public virtual returns (bool) {

82: 		    function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
```
[[50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L50), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L62), [82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L82)]

</details>

---

### [N-42] `require`/`revert` without any message

If a transaction reverts, it can be confusing to debug if there aren't any messages. Add a descriptive message to all `require`/`revert` statements.

*There are 9 instances of this issue.*


```solidity
File: contracts/libraries/Math.sol

361: 		                require(denominator > 0);

370: 		            require(denominator > prod1);

448: 		                require(result < type(uint256).max);

484: 		            require(2 ** 64 > prod1);

547: 		            require(2 ** 96 > prod1);

588: 		                require(result < type(uint256).max);

624: 		            require(2 ** 128 > prod1);

665: 		                require(result < type(uint256).max);

701: 		            require(2 ** 192 > prod1);
```
[[361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L370), [448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L448), [484](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L484), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L547), [588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L588), [624](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L624), [665](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L665), [701](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L701)]


---

### [N-43] `else` block is not required

Consider moving the logic outside the `else` block, and then removing it (it's not required, as the function is returning a value). There will be one less level of nesting, which will improve the quality of the codebase.

*There are 5 instances of this issue.*


```solidity
File: contracts/SemiFungiblePositionManager.sol

1517: 		        } else {
1518: 		            // Extract the account liquidity for a given uniswap pool, owner, token type, and ticks
1519: 		            acctPremia = isLong == 1
1520: 		                ? s_accountPremiumOwed[positionKey]
1521: 		                : s_accountPremiumGross[positionKey];
1522: 		        }
```
[[1517-1522](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1517-L1522)]



```solidity
File: contracts/libraries/PanopticMath.sol

327: 		        } else {
328: 		            return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
329: 		        }

430: 		        } else {
431: 		            return (
432: 		                tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
433: 		                tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
434: 		            );
435: 		        }

496: 		            } else {
497: 		                return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
498: 		            }

513: 		            } else {
514: 		                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
515: 		            }
```
[[327-329](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L327-L329), [430-435](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L430-L435), [496-498](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L496-L498), [513-515](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L513-L515)]


---

### [N-44] Multiple `address`/ID mappings can be combined into a single mapping of an `address`/ID to a `struct`, for readability

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related.

*There are 4 instances of this issue.*


```solidity
File: contracts/PanopticPool.sol

// @audit consider merging s_positionBalance, s_positionsHash
259: 		    mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
260: 		        internal s_positionBalance;

273: 		    mapping(address account => uint256 positionsHash) internal s_positionsHash;
```
[[259-260](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L259-L260)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit consider merging s_accountLiquidity, s_accountFeesBase
177: 		    mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
178: 		        internal s_accountLiquidity;

295: 		    mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;

// @audit consider merging s_accountPremiumOwed, s_accountPremiumGross
287: 		    mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

289: 		    mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;
```
[[177-178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L177-L178), [287](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L287)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

// @audit consider merging balanceOf, allowance
36: 		    mapping(address account => uint256 balance) public balanceOf;

40: 		    mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;
```
[[36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L36)]


---

### [N-45] Lack of specific `import` identifier

It is better to use `import {<identifier>} from "<file.sol>"` instead of `import "<file.sol>"` to improve readability and speed up the compilation time.

*There is 1 instance of this issue.*


```solidity
File: contracts/PanopticPool.sol

22: 		import "forge-std/console.sol";
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L22)]


---

### [N-46] Imports should be organized more systematically

The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

*There are 4 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

7: 		import {ERC20Minimal} from "@tokens/ERC20Minimal.sol";
```
[[7](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L7)]



```solidity
File: contracts/PanopticFactory.sol

12: 		import {Multicall} from "@multicall/Multicall.sol";
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L12)]



```solidity
File: contracts/PanopticPool.sol

9: 		import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";
```
[[9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L9)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

9: 		import {Multicall} from "@multicall/Multicall.sol";
```
[[9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L9)]


---

### [N-47] Long bitmasks are hard to read

Consider using bitshifts instead of a bitmap if the value is a power of 2 and the variable is constant, to improve the code readability.

*There is 1 instance of this issue.*


```solidity
File: contracts/libraries/Constants.sol

10: 		    uint256 internal constant FP96 = 0x1000000000000000000000000;
```
[[10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L10)]


---

### [N-48] Use a struct to encapsulate multiple function parameters

If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

*There are 42 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

178: 		    constructor(
179: 		        uint256 _commissionFee,
180: 		        uint256 _sellerCollateralRatio,
181: 		        uint256 _buyerCollateralRatio,
182: 		        int256 _forceExerciseCost,
183: 		        uint256 _targetPoolUtilization,
184: 		        uint256 _saturatedPoolUtilization,
185: 		        uint256 _ITMSpreadMultiplier

221: 		    function startToken(
222: 		        bool underlyingIsToken0,
223: 		        address token0,
224: 		        address token1,
225: 		        uint24 fee,
226: 		        PanopticPool panopticPool

650: 		    function exerciseCost(
651: 		        int24 currentTick,
652: 		        int24 oracleTick,
653: 		        TokenId positionId,
654: 		        uint128 positionBalance,
655: 		        LeftRightSigned longAmounts

1043: 		    function exercise(
1044: 		        address optionOwner,
1045: 		        int128 longAmount,
1046: 		        int128 shortAmount,
1047: 		        int128 swappedAmount,
1048: 		        int128 realizedPremium

1278: 		    function _getRequiredCollateralSingleLeg(
1279: 		        TokenId tokenId,
1280: 		        uint256 index,
1281: 		        uint128 positionSize,
1282: 		        int24 atTick,
1283: 		        uint128 poolUtilization

1311: 		    function _getRequiredCollateralSingleLegNoPartner(
1312: 		        TokenId tokenId,
1313: 		        uint256 index,
1314: 		        uint128 positionSize,
1315: 		        int24 atTick,
1316: 		        uint128 poolUtilization

1439: 		    function _getRequiredCollateralSingleLegPartner(
1440: 		        TokenId tokenId,
1441: 		        uint256 index,
1442: 		        uint128 positionSize,
1443: 		        int24 atTick,
1444: 		        uint128 poolUtilization

1510: 		    function _computeSpread(
1511: 		        TokenId tokenId,
1512: 		        uint128 positionSize,
1513: 		        uint256 index,
1514: 		        uint256 partnerIndex,
1515: 		        uint128 poolUtilization

1600: 		    function _computeStrangle(
1601: 		        TokenId tokenId,
1602: 		        uint256 index,
1603: 		        uint128 positionSize,
1604: 		        int24 atTick,
1605: 		        uint128 poolUtilization
```
[[178-185](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L178-L185), [221-226](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L221-L226), [650-655](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L650-L655), [1043-1048](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1043-L1048), [1278-1283](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1278-L1283), [1311-1316](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1311-L1316), [1439-1444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1439-L1444), [1510-1515](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1510-L1515), [1600-1605](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1600-L1605)]



```solidity
File: contracts/PanopticFactory.sol

116: 		    constructor(
117: 		        address _WETH9,
118: 		        SemiFungiblePositionManager _SFPM,
119: 		        IUniswapV3Factory _univ3Factory,
120: 		        IDonorNFT _donorNFT,
121: 		        address _poolReference,
122: 		        address _collateralReference
```
[[116-122](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L116-L122)]



```solidity
File: contracts/PanopticPool.sol

292: 		    function startPool(
293: 		        IUniswapV3Pool _univ3pool,
294: 		        address token0,
295: 		        address token1,
296: 		        CollateralTracker collateralTracker0,
297: 		        CollateralTracker collateralTracker1

430: 		    function _calculateAccumulatedPremia( //@audit-info positive premia???
431: 		        address user,
432: 		        TokenId[] calldata positionIdList,
433: 		        bool computeAllPremia,
434: 		        bool includePendingPremium,
435: 		        int24 atTick

548: 		    function mintOptions(
549: 		        TokenId[] calldata positionIdList,
550: 		        uint128 positionSize,
551: 		        uint64 effectiveLiquidityLimitX32,
552: 		        int24 tickLimitLow,
553: 		        int24 tickLimitHigh

615: 		    function _mintOptions(
616: 		        TokenId[] calldata positionIdList,
617: 		        uint128 positionSize,
618: 		        uint64 effectiveLiquidityLimitX32,
619: 		        int24 tickLimitLow,
620: 		        int24 tickLimitHigh

795: 		    function _burnAllOptionsFrom(
796: 		        address owner,
797: 		        int24 tickLimitLow,
798: 		        int24 tickLimitHigh,
799: 		        bool commitLongSettled,
800: 		        TokenId[] calldata positionIdList

827: 		    function _burnOptions(
828: 		        bool commitLongSettled,
829: 		        TokenId tokenId,
830: 		        address owner,
831: 		        int24 tickLimitLow,
832: 		        int24 tickLimitHigh

956: 		    function _burnAndHandleExercise(
957: 		        bool commitLongSettled,
958: 		        int24 tickLimitLow,
959: 		        int24 tickLimitHigh,
960: 		        TokenId tokenId,
961: 		        uint128 positionSize,
962: 		        address owner

1296: 		    function _checkSolvencyAtTick(
1297: 		        address account,
1298: 		        TokenId[] calldata positionIdList,
1299: 		        int24 currentTick,
1300: 		        int24 atTick,
1301: 		        uint256 buffer

1471: 		    function _checkLiquiditySpread(
1472: 		        TokenId tokenId,
1473: 		        uint256 leg,
1474: 		        int24 tickLower,
1475: 		        int24 tickUpper,
1476: 		        uint64 effectiveLiquidityLimitX32

1509: 		    function _getPremia(
1510: 		        TokenId tokenId,
1511: 		        uint128 positionSize,
1512: 		        address owner,
1513: 		        bool computeAllPremia,
1514: 		        int24 atTick

1763: 		    function _getAvailablePremium(
1764: 		        uint256 totalLiquidity,
1765: 		        LeftRightUnsigned settledTokens,
1766: 		        LeftRightUnsigned grossPremiumLast,
1767: 		        LeftRightUnsigned premiumOwed,
1768: 		        uint256[2] memory premiumAccumulators

1839: 		    function _updateSettlementPostBurn(
1840: 		        address owner,
1841: 		        TokenId tokenId,
1842: 		        LeftRightUnsigned[4] memory collectedByLeg,
1843: 		        uint128 positionSize,
1844: 		        bool commitLongSettled
```
[[292-297](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L292-L297), [430-435](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L430-L435), [548-553](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L548-L553), [615-620](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L615-L620), [795-800](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L795-L800), [827-832](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L827-L832), [956-962](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L956-L962), [1296-1301](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1296-L1301), [1471-1476](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1471-L1476), [1509-1514](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1509-L1514), [1763-1768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1763-L1768), [1839-1844](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1839-L1844)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

540: 		    function safeTransferFrom( //@audit-info new function
541: 		        address from,
542: 		        address to,
543: 		        uint256 id,
544: 		        uint256 amount,
545: 		        bytes calldata data //@audit-issue L - allows zero address transfer?

566: 		    function safeBatchTransferFrom(
567: 		        address from,
568: 		        address to,
569: 		        uint256[] calldata ids,
570: 		        uint256[] calldata amounts,
571: 		        bytes calldata data

681: 		    function _validateAndForwardToAMM(
682: 		        TokenId tokenId,
683: 		        uint128 positionSize,
684: 		        int24 tickLimitLow,
685: 		        int24 tickLimitHigh,
686: 		        bool isBurn

959: 		    function _createLegInAMM(
960: 		        IUniswapV3Pool univ3pool,
961: 		        TokenId tokenId,
962: 		        uint256 leg,
963: 		        LiquidityChunk liquidityChunk,
964: 		        bool isBurn

1256: 		    function _collectAndWritePositionData(
1257: 		        LiquidityChunk liquidityChunk,
1258: 		        IUniswapV3Pool univ3pool,
1259: 		        LeftRightUnsigned currentLiquidity,
1260: 		        bytes32 positionKey,
1261: 		        LeftRightSigned movedInLeg,
1262: 		        uint256 isLong

1422: 		    function getAccountLiquidity(
1423: 		        address univ3pool,
1424: 		        address owner,
1425: 		        uint256 tokenType,
1426: 		        int24 tickLower,
1427: 		        int24 tickUpper

1450: 		    function getAccountPremium(
1451: 		        address univ3pool,
1452: 		        address owner,
1453: 		        uint256 tokenType,
1454: 		        int24 tickLower,
1455: 		        int24 tickUpper,
1456: 		        int24 atTick,
1457: 		        uint256 isLong

1536: 		    function getAccountFeesBase(
1537: 		        address univ3pool,
1538: 		        address owner,
1539: 		        uint256 tokenType,
1540: 		        int24 tickLower,
1541: 		        int24 tickUpper
```
[[540-545](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L540-L545), [566-571](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L566-L571), [681-686](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L681-L686), [959-964](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L959-L964), [1256-1262](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1256-L1262), [1422-1427](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1422-L1427), [1450-1457](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1450-L1457), [1536-1541](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1536-L1541)]



```solidity
File: contracts/libraries/FeesCalc.sol

97: 		    function calculateAMMSwapFees(
98: 		        IUniswapV3Pool univ3pool,
99: 		        int24 currentTick,
100: 		        int24 tickLower,
101: 		        int24 tickUpper,
102: 		        uint128 liquidity
```
[[97-102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L97-L102)]



```solidity
File: contracts/libraries/InteractionHelper.sol

25: 		    function doApprovals(
26: 		        SemiFungiblePositionManager sfpm,
27: 		        CollateralTracker ct0,
28: 		        CollateralTracker ct1,
29: 		        address token0,
30: 		        address token1

49: 		    function computeName(
50: 		        address token0,
51: 		        address token1,
52: 		        bool isToken0,
53: 		        uint24 fee,
54: 		        string memory prefix
```
[[25-30](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L25-L30), [49-54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L49-L54)]



```solidity
File: contracts/libraries/PanopticMath.sol

125: 		    function computeMedianObservedPrice(
126: 		        IUniswapV3Pool univ3pool,
127: 		        uint256 observationIndex,
128: 		        uint256 observationCardinality,
129: 		        uint256 cardinality,
130: 		        uint256 period

168: 		    function computeInternalMedian(
169: 		        uint256 observationIndex,
170: 		        uint256 observationCardinality,
171: 		        uint256 period,
172: 		        uint256 medianData,
173: 		        IUniswapV3Pool univ3pool

651: 		    function getLiquidationBonus(
652: 		        LeftRightUnsigned tokenData0,
653: 		        LeftRightUnsigned tokenData1,
654: 		        uint160 sqrtPriceX96Twap,
655: 		        uint160 sqrtPriceX96Final,
656: 		        LeftRightSigned netExchanged,
657: 		        LeftRightSigned premia

768: 		    function haircutPremia(
769: 		        address liquidatee,
770: 		        TokenId[] memory positionIdList,
771: 		        LeftRightSigned[4][] memory premiasByLeg, //@audit pos or neg?
772: 		        LeftRightSigned collateralRemaining,
773: 		        CollateralTracker collateral0,
774: 		        CollateralTracker collateral1,
775: 		        uint160 sqrtPriceX96Final,
776: 		        mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens

917: 		    function getRefundAmounts(
918: 		        address refunder,
919: 		        LeftRightSigned refundValues,
920: 		        int24 atTick,
921: 		        CollateralTracker collateral0,
922: 		        CollateralTracker collateral1
```
[[125-130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L125-L130), [168-173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L168-L173), [651-657](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651-L657), [768-776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768-L776), [917-922](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L917-L922)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

94: 		    function safeTransferFrom(
95: 		        address from,
96: 		        address to,
97: 		        uint256 id,
98: 		        uint256 amount,
99: 		        bytes calldata data

130: 		    function safeBatchTransferFrom(
131: 		        address from,
132: 		        address to,
133: 		        uint256[] calldata ids,
134: 		        uint256[] calldata amounts,
135: 		        bytes calldata data
```
[[94-99](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L94-L99), [130-135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L130-L135)]



```solidity
File: contracts/types/TokenId.sol

336: 		    function addLeg(
337: 		        TokenId self,
338: 		        uint256 legIndex,
339: 		        uint256 _optionRatio,
340: 		        uint256 _asset,
341: 		        uint256 _isLong,
342: 		        uint256 _tokenType,
343: 		        uint256 _riskPartner,
344: 		        int24 _strike,
345: 		        int24 _width
```
[[336-345](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L336-L345)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

13: 		    function issueNFT(
14: 		        address deployer,
15: 		        PanopticPool newPoolContract,
16: 		        address token0,
17: 		        address token1,
18: 		        uint24 fee
```
[[13-18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L13-L18)]

</details>

---

### [N-49] Event is missing `msg.sender` parameter

The following functions are missing some parameters when emitting an event: when dealing with a source address which uses the value of `msg.sender`, the `msg.sender` value should be specified in every event.

Otherwise, a contract or web page listening to events cannot react to connected users: basically, those events cannot be used properly.

*There are 9 instances of this issue.*


```solidity
File: contracts/PanopticFactory.sol

155: 		        emit OwnershipTransferred(currentOwner, newOwner);

269: 		        emit PoolDeployed(
270: 		            newPoolContract,
271: 		            v3Pool,
272: 		            collateralTracker0,
273: 		            collateralTracker1,
274: 		            amount0,
275: 		            amount1
276: 		        );
```
[[155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L155), [269-276](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L269-L276)]



```solidity
File: contracts/PanopticPool.sol

854: 		        emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

1660: 		            emit PremiumSettled(owner, tokenId, realizedPremia);
```
[[854](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L854), [1660](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1660)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

390: 		        emit PoolInitialized(univ3pool, poolId);
```
[[390](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L390)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

95: 		        emit Transfer(from, to, amount);

113: 		        emit Transfer(from, to, amount);

131: 		        emit Transfer(address(0), to, amount);

146: 		        emit Transfer(from, address(0), amount);
```
[[95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L95), [113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L113), [131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L131), [146](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L146)]


---

### [N-50] Events should emit both new and old values

Events are generally emitted when sensitive changes are made to the contracts.

However, some are missing important parameters, as they should include both the new value and old value where possible.

*There are 2 instances of this issue.*


```solidity
File: contracts/PanopticPool.sol

1660: 		            emit PremiumSettled(owner, tokenId, realizedPremia);
```
[[1660](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1660)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

84: 		        emit ApprovalForAll(msg.sender, operator, approved);
```
[[84](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L84)]


---

### [N-51] Events may be emitted out of order due to reentrancy

If a reentrancy occurs, some events may be emitted in an unexpected order, and this may be a problem if a third party expects a specific order for these events. Ensure that events follow the best practice of CEI.

*There are 8 instances of this issue.*


```solidity
File: contracts/PanopticFactory.sol

// @audit collateralTracker0.startToken(true, token0, token1, fee, newPoolContract)
269: 		        emit PoolDeployed(
270: 		            newPoolContract,
271: 		            v3Pool,
272: 		            collateralTracker0,
273: 		            collateralTracker1,
274: 		            amount0,
275: 		            amount1
276: 		        );
```
[[269-276](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L269-L276)]



```solidity
File: contracts/PanopticPool.sol

// @audit tokenId.poolId()
667: 		        emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);

// @audit s_positionBalance[owner][tokenId].rightSlot()
854: 		        emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

// @audit s_univ3pool.slot0()
1171: 		        emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

// @audit s_positionBalance[account][touchedId[0]].rightSlot()
1283: 		        emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

// @audit tokenId.isLong(legIndex)
1660: 		            emit PremiumSettled(owner, tokenId, realizedPremia);
```
[[667](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L667), [854](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L854), [1171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1171), [1283](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1283), [1660](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1660)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit tokenId.poolId()
485: 		        emit TokenizedPositionBurnt(msg.sender, tokenId, positionSize);

// @audit tokenId.poolId()
517: 		        emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);
```
[[485](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L485), [517](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L517)]


---

### [N-52] Use of polymorphism is discouraged for security audits

A duplicated function name in the same contract might have problems with automated auditing tools, so it should be avoided. Consider always using a different name for functions to improve the readability of the code.

*There are 15 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

// @audit found also on line 864
894: 		    function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

// @audit found also on line 903
975: 		    function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {
```
[[894](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L894), [975](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L975)]



```solidity
File: contracts/PanopticPool.sol

// @audit found also on line 570
587: 		    function burnOptions(
```
[[587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L587)]



```solidity
File: contracts/libraries/Math.sol

// @audit found also on line 41
49: 		    function min(int256 a, int256 b) internal pure returns (int256) {

// @audit found also on line 57
65: 		    function max(int256 a, int256 b) internal pure returns (int256) {

// @audit found also on line 311
318: 		    function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {
```
[[49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L49), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L65), [318](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L318)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit found also on line 419
445: 		    function convertCollateralData(

// @audit found also on line 490
524: 		    function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

// @audit found also on line 507
547: 		    function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
```
[[445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L445), [524](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L524), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L547)]



```solidity
File: contracts/types/LeftRight.sol

// @audit found also on line 39
46: 		    function rightSlot(LeftRightSigned self) internal pure returns (int128) {

// @audit found also on line 59
78: 		    function toRightSlot(

// @audit found also on line 101
108: 		    function leftSlot(LeftRightSigned self) internal pure returns (int128) {

// @audit found also on line 121
134: 		    function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

// @audit found also on lines 148, 194
214: 		    function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

// @audit found also on line 171
232: 		    function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
```
[[46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L46), [78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L78), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L108), [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L134), [214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L232)]

</details>

---

### [N-53] Avoid external calls in modifiers

It is unusual to have external calls in modifiers, and doing so will make reviewers more likely to miss important external interactions. Consider moving the external call to an internal function, and calling that function from the modifier.

*There is 1 instance of this issue.*


```solidity
File: contracts/CollateralTracker.sol

170: 		        if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();
```
[[170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L170)]


---

### [N-54] Custom `error` without details

Consider adding some parameters to the error to indicate which user or values caused the failure.

*There are 34 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/libraries/Errors.sol

10: 		    error CastingError();

13: 		    error CollateralTokenAlreadyInitialized();

16: 		    error DepositTooLarge();

20: 		    error EffectiveLiquidityAboveThreshold();

23: 		    error ExceedsMaximumRedemption();

26: 		    error ExerciseeNotSolvent();

29: 		    error InputListFail();

32: 		    error InvalidSalt();

35: 		    error InvalidTick();

38: 		    error InvalidNotionalValue();

45: 		    error InvalidUniswapCallback();

48: 		    error LeftRightInputError();

51: 		    error NoLegsExercisable();

54: 		    error NotEnoughCollateral();

57: 		    error PositionTooLarge();

60: 		    error NotALongLeg();

63: 		    error NotEnoughLiquidity();

66: 		    error NotMarginCalled();

70: 		    error NotOwner();

73: 		    error NotPanopticPool();

76: 		    error OptionsBalanceZero();

79: 		    error PoolAlreadyInitialized();

82: 		    error PositionAlreadyMinted();

85: 		    error PositionCountNotZero();

88: 		    error PriceBoundFail();

91: 		    error ReentrantCall();

95: 		    error StaleTWAP();

98: 		    error TooManyPositionsOpen();

101: 		    error TransferFailed();

105: 		    error TicksNotInitializable();

108: 		    error UnderOverFlow();

111: 		    error UniswapPoolNotInitialized();
```
[[10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L10), [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L13), [16](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L16), [20](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L20), [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L26), [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L29), [32](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L32), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L35), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L38), [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L45), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L48), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L51), [54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L54), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L57), [60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L60), [63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L73), [76](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L76), [79](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L79), [82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L82), [85](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L85), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L88), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L91), [95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L95), [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L98), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L105), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L108), [111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L111)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

55: 		    error NotAuthorized();

58: 		    error UnsafeRecipient();
```
[[55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L55), [58](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L58)]

</details>

---

### [N-55] Don't use uppercase for non `constant`/`immutable` variables

Variables which are not constants or immutable should **not** be declared in all uppercase.

*There are 2 instances of this issue.*


```solidity
File: contracts/PanopticFactory.sol

117: 		        address _WETH9,

118: 		        SemiFungiblePositionManager _SFPM,
```
[[117](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L117), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L118)]


---

### [N-56] Constants in comparisons should appear on the left side

This is useful to avoid doing some [typo bugs](https://www.moserware.com/2008/01/constants-on-left-are-better-but-this.html).

*There are 119 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

331: 		        if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

350: 		        if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

512: 		        return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

575: 		        return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

664: 		                if (positionId.isLong(leg) == 0) continue;

708: 		                    (tokenType == 0 && currentValue1 < oracleValue1) ||

709: 		                    (tokenType == 1 && currentValue0 < oracleValue0)

1060: 		            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1060: 		            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1060: 		            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1107: 		            if (intrinsicValue != 0) {

1325: 		        uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();

1328: 		        int64 utilization = tokenType == 0

1339: 		            if (isLong == 0) {

1346: 		                    ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1

1347: 		                    ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1362: 		                    uint160 ratio = tokenType == 1 // tokenType

1374: 		                        ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1375: 		                        ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1451: 		            if (isLong == 1) {

1479: 		        if (isLong == 0) {

1488: 		        } else if (isLong == 1) {

1544: 		                if (tokenType == 0) {

1559: 		                if (tokenType == 1) {

1582: 		                tokenType == 0 ? movedRight : movedLeft,

1584: 		                tokenType == 0

1637: 		                uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638: 		                (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
```
[[331](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L331), [350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L350), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L512), [575](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L575), [664](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L664), [708](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L708), [709](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L709), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1060), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1060), [1060](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1060), [1107](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1107), [1325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1325), [1328](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1328), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1339), [1346](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1346), [1347](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1347), [1362](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1362), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1374), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1375), [1451](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1451), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1479), [1488](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1488), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1544), [1559](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1559), [1582](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1582), [1584](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1584), [1637](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1638)]



```solidity
File: contracts/PanopticPool.sol

461: 		                if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

534: 		        if (medianData != 0) s_miniMedian = medianData;

639: 		        if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

665: 		        if (medianData != 0) s_miniMedian = medianData;

769: 		            if (isLong == 1) {

866: 		            if (tokenId.isLong(leg) == 0) {

1189: 		        if (touchedId.length != 1) revert Errors.InputListFail();

1489: 		        if (netLiquidity == 0) return;

1526: 		            if ((isLong == 1) || computeAllPremia) {

1572: 		                    if (isLong == 1) {

1602: 		        if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1685: 		            if (tokenId.isLong(leg) == 0) {

1786: 		                                    (accumulated0 == 0 ? type(uint256).max : accumulated0),

1795: 		                                    (accumulated1 == 0 ? type(uint256).max : accumulated1),

1868: 		            if (LeftRightSigned.unwrap(legPremia) != 0) {

1870: 		                if (tokenId.isLong(leg) == 1) {

1934: 		                        s_grossPremiumLast[chunkKey] = totalLiquidity != 0
```
[[461](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L461), [534](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L534), [639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L639), [665](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L665), [769](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L769), [866](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L866), [1189](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1189), [1489](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1489), [1526](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1526), [1572](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1572), [1602](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1602), [1685](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1685), [1786](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1786), [1795](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1795), [1868](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1868), [1870](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1870), [1934](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1934)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

362: 		        if (s_AddrToPoolIdData[univ3pool] != 0) return;

632: 		                (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

633: 		                (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

689: 		        if (positionSize == 0) revert Errors.OptionsBalanceZero();

718: 		            if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

788: 		            if ((itm0 != 0) && (itm1 != 0)) {

788: 		            if ((itm0 != 0) && (itm1 != 0)) {

824: 		            } else if (itm0 != 0) {

834: 		            if (swapAmount == 0) return LeftRightSigned.wrap(0);

1000: 		            if (isLong == 0) {

1067: 		            moved = isLong == 0

1074: 		            if (tokenType == 1) {

1079: 		            if (tokenType == 0) {

1276: 		        if (isLong == 1) {

1280: 		        if (LeftRightSigned.unwrap(amountToCollect) != 0) {

1470: 		            if (netLiquidity != 0) {

1515: 		                acctPremia = isLong == 1 ? premiumOwed : premiumGross;

1519: 		            acctPremia = isLong == 1
```
[[362](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L362), [632](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L632), [633](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L633), [689](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L689), [718](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L718), [788](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L788), [788](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L788), [824](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L824), [834](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L834), [1000](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1000), [1067](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1067), [1074](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1074), [1079](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1079), [1276](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1276), [1280](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1280), [1470](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1470), [1515](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1515), [1519](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1519)]



```solidity
File: contracts/libraries/FeesCalc.sol

67: 		                if (tokenId.isLong(leg) == 0) {
```
[[67](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L67)]



```solidity
File: contracts/libraries/Math.sol

133: 		            uint256 sqrtR = absTick & 0x1 != 0

137: 		            if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

139: 		            if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

141: 		            if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

143: 		            if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;

145: 		            if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

147: 		            if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;

149: 		            if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;

151: 		            if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;

153: 		            if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

155: 		            if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

157: 		            if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

159: 		            if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;

161: 		            if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

163: 		            if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;

165: 		            if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;

167: 		            if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

169: 		            if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;

171: 		            if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

173: 		            if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

179: 		            return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

360: 		            if (prod1 == 0) {

474: 		            if (prod1 == 0) {

537: 		            if (prod1 == 0) {

614: 		            if (prod1 == 0) {

691: 		            if (prod1 == 0) {
```
[[133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L133), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L137), [139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L139), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L141), [143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L143), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L145), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L147), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L149), [151](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L151), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L153), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L155), [157](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L157), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L159), [161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L161), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L163), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L165), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L167), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L169), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L171), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L173), [179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L179), [360](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L360), [474](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L474), [537](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L537), [614](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L614), [691](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L691)]



```solidity
File: contracts/libraries/PanopticMath.sol

211: 		                    if (rank == 7) {

325: 		        if (tokenId.asset(legIndex) == 0) {

357: 		                tickLower % tickSpacing != 0 ||

358: 		                tickUpper % tickSpacing != 0 ||

425: 		        if (tokenType == 0) {

475: 		            uint256 notional = asset == 0

479: 		            if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

584: 		        if (tokenId.asset(legIndex) == 0) {

615: 		        bool isShort = tokenId.isLong(legIndex) == 0;

618: 		        if (tokenId.tokenType(legIndex) == 0) {

785: 		                    if (tokenId.isLong(leg) == 1) {

856: 		                if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857: 		                if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

864: 		                    if (tokenId.isLong(leg) == 1) {
```
[[211](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L211), [325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L325), [357](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L357), [358](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L358), [425](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L425), [475](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L475), [479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L479), [584](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L584), [615](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L615), [618](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L618), [785](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L785), [856](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L856), [857](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L857), [864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L864)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

112: 		        if (to.code.length != 0) {

163: 		        if (to.code.length != 0) {

202: 		            interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

203: 		            interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

222: 		        if (to.code.length != 0) {
```
[[112](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L112), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L163), [202](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L203), [222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L222)]



```solidity
File: contracts/types/TokenId.sol

465: 		        if (i == 0)

471: 		        if (i == 1)

477: 		        if (i == 2)

483: 		        if (i == 3)

501: 		        if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

508: 		                if (self.optionRatio(i) == 0) {

512: 		                    if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

528: 		                if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

566: 		                    if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

592: 		                    if (self.isLong(i) == 1) return; // validated
```
[[465](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L465), [471](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L471), [477](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L477), [483](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L483), [501](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L501), [508](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L508), [512](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L512), [528](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L528), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L566), [592](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L592)]

</details>

---

### [N-57] Consider using `delete` instead of assigning zero/false to clear values

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

*There are 5 instances of this issue.*


```solidity
File: contracts/SemiFungiblePositionManager.sol

332: 		        s_poolContext[poolId].locked = false;
```
[[332](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L332)]



```solidity
File: contracts/libraries/PanopticMath.sol

220: 		                        below = false;

850: 		                collateralDelta0 = 0;

851: 		                collateralDelta1 = 0;
```
[[220](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L220), [850](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L850), [851](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L851)]



```solidity
File: contracts/types/TokenId.sol

377: 		                optionRatios = 0;
```
[[377](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L377)]


---

### [N-58] Consider disallowing transfers to `address(this)`

Consider preventing a contract's tokens from being transferred to the contract itself.

*There are 3 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

323: 		    function transfer(
324: 		        address recipient,
325: 		        uint256 amount
326: 		    ) public override(ERC20Minimal) returns (bool) {
327: 		        // make sure the caller does not have any open option positions
328: 		        // if they do: we don't want them sending panoptic pool shares to others
329: 		        // since that's like reducing collateral
330: 		
331: 		        if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();
332: 		
333: 		        return ERC20Minimal.transfer(recipient, amount);
334: 		    }

341: 		    function transferFrom(
342: 		        address from,
343: 		        address to,
344: 		        uint256 amount
345: 		    ) public override(ERC20Minimal) returns (bool) {
346: 		        // make sure the caller does not have any open option positions
347: 		        // if they do: we don't want them sending panoptic pool shares to others
348: 		        // as this would reduce their amount of collateral against the opened positions
349: 		
350: 		        if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();
351: 		
352: 		        return ERC20Minimal.transferFrom(from, to, amount);
353: 		    }
```
[[323-334](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323-L334), [341-353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341-L353)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

540: 		    function safeTransferFrom( //@audit-info new function
541: 		        address from,
542: 		        address to,
543: 		        uint256 id,
544: 		        uint256 amount,
545: 		        bytes calldata data //@audit-issue L - allows zero address transfer?
546: 		    ) public override { //@audit-ok has callback on transfer
547: 		        // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
548: 		        // so just check if there is an active reentrancy lock for the relevant pool on the token we're transferring
549: 		        if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();
550: 		
551: 		        // update the position data
552: 		        registerTokenTransfer(from, to, TokenId.wrap(id), amount);
553: 		
554: 		        // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)
555: 		        super.safeTransferFrom(from, to, id, amount, data);
556: 		    }
```
[[540-556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L540-L556)]


---

### [N-59] Use a ternary statement instead of `if`/`else` when appropriate

The `if`/`else` statement can be written in a shorthand way using the ternary operator, as it increases readability and reduces the number of lines of code.

*There are 3 instances of this issue.*


```solidity
File: contracts/libraries/PanopticMath.sol

325: 		        if (tokenId.asset(legIndex) == 0) {
326: 		            return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
327: 		        } else {
328: 		            return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
329: 		        }

494: 		            if (sqrtPriceX96 < type(uint128).max) {
495: 		                return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
496: 		            } else {
497: 		                return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
498: 		            }

511: 		            if (sqrtPriceX96 < type(uint128).max) {
512: 		                return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
513: 		            } else {
514: 		                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
515: 		            }
```
[[325-329](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L325-L329), [494-498](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L494-L498), [511-515](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L511-L515)]


---

### [N-60] Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is ideal for named returns.

*There are 103 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

289: 		    function name() external view returns (string memory) {

303: 		    function symbol() external view returns (string memory) {

310: 		    function decimals() external view returns (uint8) {

323: 		    function transfer(
324: 		        address recipient,
325: 		        uint256 amount
326: 		    ) public override(ERC20Minimal) returns (bool) {

341: 		    function transferFrom(
342: 		        address from,
343: 		        address to,
344: 		        uint256 amount
345: 		    ) public override(ERC20Minimal) returns (bool) {

1043: 		    function exercise(
1044: 		        address optionOwner,
1045: 		        int128 longAmount,
1046: 		        int128 shortAmount,
1047: 		        int128 swappedAmount,
1048: 		        int128 realizedPremium
1049: 		    ) external onlyPanopticPool returns (int128) {
```
[[289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L310), [323-326](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323-L326), [341-345](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341-L345), [1043-1049](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1043-L1049)]



```solidity
File: contracts/PanopticFactory.sol

160: 		    function owner() external view returns (address) {

336: 		    function _mintFullRange(
337: 		        IUniswapV3Pool v3Pool,
338: 		        address token0,
339: 		        address token1,
340: 		        uint24 fee
341: 		    ) internal returns (uint256, uint256) {

421: 		    function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {
```
[[160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L160), [336-341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L336-L341), [421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L421)]



```solidity
File: contracts/PanopticPool.sol

500: 		    function _getSlippageLimits(
501: 		        int24 tickLimitLow,
502: 		        int24 tickLimitHigh
503: 		    ) internal pure returns (int24, int24) {

678: 		    function _mintInSFPMAndUpdateCollateral(
679: 		        TokenId tokenId,
680: 		        uint128 positionSize,
681: 		        int24 tickLimitLow,
682: 		        int24 tickLimitHigh
683: 		    ) internal returns (uint128) {

707: 		    function _payCommissionAndWriteData(
708: 		        TokenId tokenId,
709: 		        uint128 positionSize,
710: 		        LeftRightSigned totalSwapped
711: 		    ) internal returns (uint128) {

1296: 		    function _checkSolvencyAtTick(
1297: 		        address account,
1298: 		        TokenId[] calldata positionIdList,
1299: 		        int24 currentTick,
1300: 		        int24 atTick,
1301: 		        uint256 buffer
1302: 		    ) internal view returns (bool) {

1431: 		    function univ3pool() external view returns (IUniswapV3Pool) {

1443: 		    function collateralToken1() external view returns (CollateralTracker) {

1763: 		    function _getAvailablePremium(
1764: 		        uint256 totalLiquidity,
1765: 		        LeftRightUnsigned settledTokens,
1766: 		        LeftRightUnsigned grossPremiumLast,
1767: 		        LeftRightUnsigned premiumOwed,
1768: 		        uint256[2] memory premiumAccumulators
1769: 		    ) internal pure returns (LeftRightUnsigned) {
```
[[500-503](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L500-L503), [678-683](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L678-L683), [707-711](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L707-L711), [1296-1302](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1296-L1302), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1431), [1443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1443), [1763-1769](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1763-L1769)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

1450: 		    function getAccountPremium(
1451: 		        address univ3pool,
1452: 		        address owner,
1453: 		        uint256 tokenType,
1454: 		        int24 tickLower,
1455: 		        int24 tickUpper,
1456: 		        int24 atTick,
1457: 		        uint256 isLong
1458: 		    ) external view returns (uint128, uint128) {
```
[[1450-1458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1450-L1458)]



```solidity
File: contracts/libraries/FeesCalc.sol

97: 		    function calculateAMMSwapFees(
98: 		        IUniswapV3Pool univ3pool,
99: 		        int24 currentTick,
100: 		        int24 tickLower,
101: 		        int24 tickUpper,
102: 		        uint128 liquidity
103: 		    ) public view returns (LeftRightSigned) {
```
[[97-103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L97-L103)]



```solidity
File: contracts/libraries/InteractionHelper.sol

49: 		    function computeName(
50: 		        address token0,
51: 		        address token1,
52: 		        bool isToken0,
53: 		        uint24 fee,
54: 		        string memory prefix
55: 		    ) external view returns (string memory) {

92: 		    function computeSymbol(
93: 		        address token,
94: 		        string memory prefix
95: 		    ) external view returns (string memory) {

108: 		    function computeDecimals(address token) external view returns (uint8) {
```
[[49-55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L49-L55), [92-95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L92-L95), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L108)]



```solidity
File: contracts/libraries/Math.sol

25: 		    function min24(int24 a, int24 b) internal pure returns (int24) {

33: 		    function max24(int24 a, int24 b) internal pure returns (int24) {

41: 		    function min(uint256 a, uint256 b) internal pure returns (uint256) {

49: 		    function min(int256 a, int256 b) internal pure returns (int256) {

57: 		    function max(uint256 a, uint256 b) internal pure returns (uint256) {

65: 		    function max(int256 a, int256 b) internal pure returns (int256) {

73: 		    function abs(int256 x) internal pure returns (int256) {

81: 		    function absUint(int256 x) internal pure returns (uint256) {

128: 		    function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) { //@audit-ok

191: 		    function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

207: 		    function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

241: 		    function getLiquidityForAmount0( //@audit-info price is new: https://github.com/Uniswap/v3-periphery/blob/main/contracts/libraries/LiquidityAmounts.sol#L23
242: 		        int24 tickLower,
243: 		        int24 tickUpper,
244: 		        uint256 amount0
245: 		    ) internal pure returns (LiquidityChunk) {

271: 		    function getLiquidityForAmount1(
272: 		        int24 tickLower,
273: 		        int24 tickUpper,
274: 		        uint256 amount1
275: 		    ) internal pure returns (LiquidityChunk) {

325: 		    function toInt256(uint256 toCast) internal pure returns (int256) {

458: 		    function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521: 		    function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

598: 		    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

675: 		    function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

776: 		    function sort(int256[] memory data) internal pure returns (int256[] memory) {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L33), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L41), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L57), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L65), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L73), [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L81), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L128), [191](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L191), [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L207), [241-245](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L241-L245), [271-275](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L271-L275), [325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L325), [458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L521), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L598), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L675), [776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L776)]



```solidity
File: contracts/libraries/PanopticMath.sol

47: 		    function getPoolId(address univ3pool) internal view returns (uint64) {

59: 		    function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

75: 		    function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

92: 		    function updatePositionsHash(
93: 		        uint256 existingHash,
94: 		        TokenId tokenId,
95: 		        bool addFlag
96: 		    ) internal pure returns (uint256) {

125: 		    function computeMedianObservedPrice(
126: 		        IUniswapV3Pool univ3pool,
127: 		        uint256 observationIndex,
128: 		        uint256 observationCardinality,
129: 		        uint256 cardinality,
130: 		        uint256 period
131: 		    ) external view returns (int24) {

241: 		    function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

289: 		    function getLiquidityChunk(
290: 		        TokenId tokenId,
291: 		        uint256 legIndex,
292: 		        uint128 positionSize
293: 		    ) internal pure returns (LiquidityChunk) {

371: 		    function getRangesFromStrike(
372: 		        int24 width,
373: 		        int24 tickSpacing
374: 		    ) internal pure returns (int24, int24) {

419: 		    function convertCollateralData(
420: 		        LeftRightUnsigned tokenData0,
421: 		        LeftRightUnsigned tokenData1,
422: 		        uint256 tokenType,
423: 		        uint160 sqrtPriceX96
424: 		    ) internal pure returns (uint256, uint256) {

445: 		    function convertCollateralData(
446: 		        LeftRightUnsigned tokenData0,
447: 		        LeftRightUnsigned tokenData1,
448: 		        uint256 tokenType,
449: 		        int24 tick
450: 		    ) internal pure returns (uint256, uint256) {

468: 		    function convertNotional(
469: 		        uint128 contractSize,
470: 		        int24 tickLower,
471: 		        int24 tickUpper,
472: 		        uint256 asset
473: 		    ) internal pure returns (uint128) {

490: 		    function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

507: 		    function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

524: 		    function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

547: 		    function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

574: 		    function getAmountsMoved(
575: 		        TokenId tokenId,
576: 		        uint128 positionSize,
577: 		        uint256 legIndex
578: 		    ) internal pure returns (LeftRightUnsigned) {

768: 		    function haircutPremia(
769: 		        address liquidatee,
770: 		        TokenId[] memory positionIdList,
771: 		        LeftRightSigned[4][] memory premiasByLeg, //@audit pos or neg?
772: 		        LeftRightSigned collateralRemaining,
773: 		        CollateralTracker collateral0,
774: 		        CollateralTracker collateral1,
775: 		        uint160 sqrtPriceX96Final,
776: 		        mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777: 		    ) external returns (int256, int256) {

917: 		    function getRefundAmounts(
918: 		        address refunder,
919: 		        LeftRightSigned refundValues,
920: 		        int24 atTick,
921: 		        CollateralTracker collateral0,
922: 		        CollateralTracker collateral1
923: 		    ) external view returns (LeftRightSigned) {
```
[[47](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L47), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L59), [75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L75), [92-96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L92-L96), [125-131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L125-L131), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L241), [289-293](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L289-L293), [371-374](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L371-L374), [419-424](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L419-L424), [445-450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L445-L450), [468-473](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L468-L473), [490](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L490), [507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L507), [524](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L524), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L547), [574-578](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L574-L578), [768-777](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768-L777), [917-923](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L917-L923)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

200: 		    function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
```
[[200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L200)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

50: 		    function approve(address spender, uint256 amount) public returns (bool) {

62: 		    function transfer(address to, uint256 amount) public virtual returns (bool) {

82: 		    function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
```
[[50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L50), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L62), [82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L82)]



```solidity
File: contracts/types/LeftRight.sol

39: 		    function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46: 		    function rightSlot(LeftRightSigned self) internal pure returns (int128) {

59: 		    function toRightSlot(
60: 		        LeftRightUnsigned self,
61: 		        uint128 right
62: 		    ) internal pure returns (LeftRightUnsigned) {

78: 		    function toRightSlot(
79: 		        LeftRightSigned self,
80: 		        int128 right
81: 		    ) internal pure returns (LeftRightSigned) {

101: 		    function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108: 		    function leftSlot(LeftRightSigned self) internal pure returns (int128) {

121: 		    function toLeftSlot(
122: 		        LeftRightUnsigned self,
123: 		        uint128 left
124: 		    ) internal pure returns (LeftRightUnsigned) {

134: 		    function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

279: 		    function addCapped(
280: 		        LeftRightUnsigned x,
281: 		        LeftRightUnsigned dx,
282: 		        LeftRightUnsigned y,
283: 		        LeftRightUnsigned dy
284: 		    ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {
```
[[39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L39), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L46), [59-62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L59-L62), [78-81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L78-L81), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L101), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L108), [121-124](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L121-L124), [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L134), [279-284](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L279-L284)]



```solidity
File: contracts/types/LiquidityChunk.sol

71: 		    function createChunk(
72: 		        int24 _tickLower,
73: 		        int24 _tickUpper,
74: 		        uint128 amount
75: 		    ) internal pure returns (LiquidityChunk) {

90: 		    function addLiquidity(
91: 		        LiquidityChunk self,
92: 		        uint128 amount
93: 		    ) internal pure returns (LiquidityChunk) {

103: 		    function addTickLower(
104: 		        LiquidityChunk self,
105: 		        int24 _tickLower
106: 		    ) internal pure returns (LiquidityChunk) {

119: 		    function addTickUpper(
120: 		        LiquidityChunk self,
121: 		        int24 _tickUpper
122: 		    ) internal pure returns (LiquidityChunk) {

136: 		    function updateTickLower(
137: 		        LiquidityChunk self,
138: 		        int24 _tickLower
139: 		    ) internal pure returns (LiquidityChunk) {

152: 		    function updateTickUpper(
153: 		        LiquidityChunk self,
154: 		        int24 _tickUpper
155: 		    ) internal pure returns (LiquidityChunk) {

172: 		    function tickLower(LiquidityChunk self) internal pure returns (int24) {

181: 		    function tickUpper(LiquidityChunk self) internal pure returns (int24) {

190: 		    function liquidity(LiquidityChunk self) internal pure returns (uint128) {
```
[[71-75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L71-L75), [90-93](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L90-L93), [103-106](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L103-L106), [119-122](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L119-L122), [136-139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L136-L139), [152-155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L152-L155), [172](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L172), [181](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L181), [190](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L190)]



```solidity
File: contracts/types/TokenId.sol

87: 		    function poolId(TokenId self) internal pure returns (uint64) {

96: 		    function tickSpacing(TokenId self) internal pure returns (int24) {

108: 		    function asset(TokenId self, uint256 legIndex) internal pure returns (uint256) {

118: 		    function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {

128: 		    function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {

138: 		    function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {

148: 		    function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {

158: 		    function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

169: 		    function width(TokenId self, uint256 legIndex) internal pure returns (int24) {

183: 		    function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193: 		    function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

205: 		    function addAsset(
206: 		        TokenId self,
207: 		        uint256 _asset,
208: 		        uint256 legIndex
209: 		    ) internal pure returns (TokenId) {

221: 		    function addOptionRatio(
222: 		        TokenId self,
223: 		        uint256 _optionRatio,
224: 		        uint256 legIndex
225: 		    ) internal pure returns (TokenId) {

240: 		    function addIsLong(
241: 		        TokenId self,
242: 		        uint256 _isLong,
243: 		        uint256 legIndex
244: 		    ) internal pure returns (TokenId) {

255: 		    function addTokenType(
256: 		        TokenId self,
257: 		        uint256 _tokenType,
258: 		        uint256 legIndex
259: 		    ) internal pure returns (TokenId) {

273: 		    function addRiskPartner(
274: 		        TokenId self,
275: 		        uint256 _riskPartner,
276: 		        uint256 legIndex
277: 		    ) internal pure returns (TokenId) {

291: 		    function addStrike(
292: 		        TokenId self,
293: 		        int24 _strike,
294: 		        uint256 legIndex
295: 		    ) internal pure returns (TokenId) {

310: 		    function addWidth(
311: 		        TokenId self,
312: 		        int24 _width,
313: 		        uint256 legIndex
314: 		    ) internal pure returns (TokenId) {

366: 		    function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

404: 		    function countLongs(TokenId self) internal pure returns (uint256) {

432: 		    function countLegs(TokenId self) internal pure returns (uint256) {

464: 		    function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {
```
[[87](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L87), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L96), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L108), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L118), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L128), [138](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L138), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L148), [158](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L158), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L169), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L183), [193](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L193), [205-209](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L205-L209), [221-225](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L221-L225), [240-244](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L240-L244), [255-259](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L255-L259), [273-277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L273-L277), [291-295](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L291-L295), [310-314](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L310-L314), [366](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L366), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L404), [432](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L432), [464](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L464)]



```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

16: 		    function balanceOf(address account) external view returns (uint256);
```
[[16](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L16)]

</details>

---

### [N-61] Layout order does not comply with best practices

This is a [best practice](https://docs.soliditylang.org/en/latest/style-guide.html#order-of-layout) that should be followed.

Inside each contract, library or interface, use the following order:

1. Type declarations
2. State variables
3. Events
4. Errors
5. Modifiers
6. Functions

*There are 6 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

// @audit event Withdraw found on line 57
70: 		    string internal constant TICKER_PREFIX = "po";
```
[[70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L70)]



```solidity
File: contracts/PanopticFactory.sol

// @audit event PoolDeployed found on line 44
64: 		    IUniswapV3Factory internal immutable UNIV3_FACTORY;
```
[[64](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L64)]



```solidity
File: contracts/PanopticPool.sol

// @audit event OptionMinted found on line 91
104: 		    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;
```
[[104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L104)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit event TokenizedPositionMinted found on line 98
125: 		    bool internal constant MINT = false;
```
[[125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L125)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

// @audit error UnsafeRecipient found on line 58
66: 		    mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;
```
[[66](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L66)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

// @audit event Approval found on line 25
33: 		    uint256 public totalSupply;
```
[[33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L33)]


---

### [N-62] Function visibility order does not comply with best practices

This is a [best practice](https://docs.soliditylang.org/en/latest/style-guide.html#order-of-functions) that should be followed.

Functions should be grouped according to their visibility and ordered:

1. constructor
2. receive function (if exists)
3. fallback function (if exists)
4. external
5. public
6. internal
7. private

Within a grouping, place the view and pure functions last.

*There are 56 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

// @audit transferFrom on line 341, which is public
361: 		    function asset() external view returns (address assetTokenAddress) {

// @audit convertToAssets on line 386, which is public
392: 		    function maxDeposit(address) external pure returns (uint256 maxAssets) {

// @audit previewDeposit on line 399, which is public
417: 		    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {

// @audit previewDeposit on line 399, which is public
444: 		    function maxMint(address) external view returns (uint256 maxShares) {

// @audit previewMint on line 453, which is public
477: 		    function mint(uint256 shares, address receiver) external returns (uint256 assets) {

// @audit previewWithdraw on line 518, which is public
531: 		    function withdraw(

// @audit previewRedeem on line 581, which is public
591: 		    function redeem(

// @audit previewRedeem on line 581, which is public
650: 		    function exerciseCost(

// @audit _buyCollateralRatio on line 806, which is internal
864: 		    function delegate(

// @audit _buyCollateralRatio on line 806, which is internal
894: 		    function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

// @audit _buyCollateralRatio on line 806, which is internal
903: 		    function refund(address delegatee, uint256 assets) external onlyPanopticPool {

// @audit _buyCollateralRatio on line 806, which is internal
911: 		    function revoke(

// @audit _buyCollateralRatio on line 806, which is internal
975: 		    function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

// @audit _buyCollateralRatio on line 806, which is internal
995: 		    function takeCommissionAddData(

// @audit _buyCollateralRatio on line 806, which is internal
1043: 		    function exercise(

// @audit _getExchangedAmount on line 1096, which is internal
1141: 		    function getAccountMarginDetails(
```
[[361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L361), [392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L392), [417](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L417), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L444), [477](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L477), [531](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L531), [591](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L591), [650](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L650), [864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L864), [894](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L894), [903](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L903), [911](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L911), [975](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L975), [995](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L995), [1043](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1043), [1141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1141)]



```solidity
File: contracts/PanopticFactory.sol

// @audit initialize on line 135, which is public
148: 		    function transferOwnership(address newOwner) external {

// @audit initialize on line 135, which is public
160: 		    function owner() external view returns (address) {

// @audit initialize on line 135, which is public
173: 		    function uniswapV3MintCallback(

// @audit initialize on line 135, which is public
211: 		    function deployNewPool(

// @audit initialize on line 135, which is public
291: 		    function minePoolAddress(

// @audit _mintFullRange on line 336, which is internal
421: 		    function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {
```
[[148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L148), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L160), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L173), [211](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L211), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L291), [421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L421)]



```solidity
File: contracts/PanopticPool.sol

// @audit _getSlippageLimits on line 500, which is internal
523: 		    function pokeMedian() external {

// @audit _getSlippageLimits on line 500, which is internal
548: 		    function mintOptions(

// @audit _getSlippageLimits on line 500, which is internal
570: 		    function burnOptions(

// @audit _getSlippageLimits on line 500, which is internal
587: 		    function burnOptions(

// @audit _burnAndHandleExercise on line 956, which is internal
1018: 		    function liquidate(

// @audit _burnAndHandleExercise on line 956, which is internal
1180: 		    function forceExercise(

// @audit _updatePositionsHash on line 1411, which is internal
1431: 		    function univ3pool() external view returns (IUniswapV3Pool) {

// @audit _updatePositionsHash on line 1411, which is internal
1437: 		    function collateralToken0() external view returns (CollateralTracker collateralToken) {

// @audit _updatePositionsHash on line 1411, which is internal
1443: 		    function collateralToken1() external view returns (CollateralTracker) {

// @audit _updatePositionsHash on line 1411, which is internal
1450: 		    function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

// @audit _getPremia on line 1509, which is internal
1593: 		    function settleLongPremium(
```
[[523](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L523), [548](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L548), [570](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L570), [587](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L587), [1018](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1018), [1180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1180), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1437), [1443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1443), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1450), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1593)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit endReentrancyLock on line 330, which is internal
341: 		    constructor(IUniswapV3Factory _factory) {

// @audit endReentrancyLock on line 330, which is internal
350: 		    function initializeAMMPool(address token0, address token1, uint24 fee) external {

// @audit endReentrancyLock on line 330, which is internal
402: 		    function uniswapV3MintCallback(

// @audit endReentrancyLock on line 330, which is internal
435: 		    function uniswapV3SwapCallback(

// @audit endReentrancyLock on line 330, which is internal
471: 		    function burnTokenizedPosition(

// @audit endReentrancyLock on line 330, which is internal
504: 		    function mintTokenizedPosition(

// @audit endReentrancyLock on line 330, which is internal
540: 		    function safeTransferFrom( //@audit-info new function

// @audit endReentrancyLock on line 330, which is internal
566: 		    function safeBatchTransferFrom(

// @audit _getFeesBase on line 1139, which is private
1186: 		    function _mintLiquidity(

// @audit _getFeesBase on line 1139, which is private
1225: 		    function _burnLiquidity(

// @audit _getFeesBase on line 1139, which is private
1256: 		    function _collectAndWritePositionData(

// @audit _getPremiaDeltas on line 1322, which is private
1422: 		    function getAccountLiquidity(

// @audit _getPremiaDeltas on line 1322, which is private
1450: 		    function getAccountPremium(

// @audit _getPremiaDeltas on line 1322, which is private
1536: 		    function getAccountFeesBase(

// @audit _getPremiaDeltas on line 1322, which is private
1556: 		    function getUniswapV3PoolFromId(

// @audit _getPremiaDeltas on line 1322, which is private
1567: 		    function getPoolId(address univ3pool) external view returns (uint64 poolId) {
```
[[341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L341), [350](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L350), [402](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L402), [435](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L435), [471](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L471), [504](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L504), [540](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L540), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L566), [1186](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1186), [1225](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1225), [1256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1256), [1422](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1422), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1450), [1536](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1536), [1556](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1556), [1567](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1567)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit incrementPoolPattern on line 59, which is internal
75: 		    function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

// @audit updatePositionsHash on line 92, which is internal
125: 		    function computeMedianObservedPrice(

// @audit updatePositionsHash on line 92, which is internal
168: 		    function computeInternalMedian(

// @audit updatePositionsHash on line 92, which is internal
241: 		    function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

// @audit _calculateIOAmounts on line 607, which is internal
651: 		    function getLiquidationBonus(

// @audit _calculateIOAmounts on line 607, which is internal
768: 		    function haircutPremia(

// @audit _calculateIOAmounts on line 607, which is internal
917: 		    function getRefundAmounts(
```
[[75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L75), [125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L125), [168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L168), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L241), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768), [917](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L917)]

</details>

---

### [N-63] Long functions should be refactored into multiple functions

Consider splitting long functions into multiple, smaller functions to improve the code readability.

*There are 33 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

650: 		    function exerciseCost(

911: 		    function revoke(

1311: 		    function _getRequiredCollateralSingleLegNoPartner(

1510: 		    function _computeSpread(
```
[[650](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L650), [911](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L911), [1311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1311), [1510](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1510)]



```solidity
File: contracts/PanopticFactory.sol

211: 		    function deployNewPool(

336: 		    function _mintFullRange(
```
[[211](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L211), [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L336)]



```solidity
File: contracts/PanopticPool.sol

430: 		    function _calculateAccumulatedPremia( //@audit-info positive premia???

615: 		    function _mintOptions(

888: 		    function _validateSolvency(

1018: 		    function liquidate(

1180: 		    function forceExercise(

1509: 		    function _getPremia(

1593: 		    function settleLongPremium(

1672: 		    function _updateSettlementPostMint(

1839: 		    function _updateSettlementPostBurn(
```
[[430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L430), [615](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L615), [888](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L888), [1018](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1018), [1180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1180), [1509](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1509), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1593), [1672](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1672), [1839](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1839)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

593: 		    function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

757: 		    function swapInAMM(

864: 		    function _createPositionInAMM(

959: 		    function _createLegInAMM(

1256: 		    function _collectAndWritePositionData(

1322: 		    function _getPremiaDeltas(

1450: 		    function getAccountPremium(
```
[[593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L593), [757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L757), [864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L864), [959](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L959), [1256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1256), [1322](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1322), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1450)]



```solidity
File: contracts/libraries/FeesCalc.sol

130: 		    function _getAMMSwapFeesPerLiquidityCollected(
```
[[130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L130)]



```solidity
File: contracts/libraries/Math.sol

128: 		    function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) { //@audit-ok

340: 		    function mulDiv(

458: 		    function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521: 		    function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

598: 		    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

675: 		    function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {
```
[[128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L128), [340](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L340), [458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L521), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L598), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L675)]



```solidity
File: contracts/libraries/PanopticMath.sol

168: 		    function computeInternalMedian(

651: 		    function getLiquidationBonus(

768: 		    function haircutPremia(
```
[[168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L168), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768)]



```solidity
File: contracts/types/TokenId.sol

500: 		    function validate(TokenId self) internal pure {
```
[[500](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L500)]

</details>

---

### [N-64] Consider moving duplicated strings to constants

This will decrease the probability of making typos, and the code will be more readable

*There are 5 instances of this issue.*


```solidity
File: contracts/libraries/InteractionHelper.sol

64: 		            symbol0 = "???";

69: 		            symbol1 = "???";

75: 		                    " ",

81: 		                    " ",

101: 		            return string.concat(prefix, "???");
```
[[64](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L64), [69](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L69), [75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L75), [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L81), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L101)]


---

### [N-65] Lines are too long

Maximum suggested line length is 120 characters according to the [documentation](https://docs.soliditylang.org/en/latest/style-guide.html#maximum-line-length).

*There are 346 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

25: 		/// This is represented as an ERC20 share token. A Panoptic pool has 2 tokens, each issued by its own instance of a CollateralTracker.

28: 		/// @notice This contract uses the ERC4626 standard allowing the minting and burning of "shares" (represented using ERC20 inheritance) in exchange for underlying "assets".

88: 		    /// @dev Whether this is token0 or token1 depends on which collateral token is being tracked in this CollateralTracker instance.

92: 		    /// @dev As each instance is deployed via proxy clone, initial parameters must only be initalized once via startToken().

111: 		    /// @dev Cached amount of assets accounted to be held by the Panoptic Pool — ignores donations, pending fee payouts, and other untracked balance changes.

135: 		    /// We believe that this will eliminate the impact of the commission fee on the user's decision-making process when closing a position.

199: 		            /// since we're dropping the higher order terms, which are all negative, this will underestimate the number of ticks for a 20% move

213: 		    /// @notice Initialize a new collateral tracker for a specific token corresponding to the Panoptic Pool being created by the factory that called it.

214: 		    /// @dev The factory calls this function to start a new collateral tracking system for the incoming token at 'underlyingToken'.

215: 		    /// The factory will do this for each of the two tokens being tracked. Thus, the collateral tracking system does not track *both* tokens at once.

257: 		        // store whether the current collateral token is token0 (true) or token1 (false; since there's always exactly two tokens it could be)

272: 		    /// @return poolAssets cached amount of assets accounted to be held by the Panoptic Pool - ignores donations, pending fee payouts, and other untracked balance changes.

274: 		    /// @return currentPoolUtilization Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),

276: 		    /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.

290: 		        // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size

304: 		        // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size

311: 		        // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size

400: 		        // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid

410: 		    /// @notice Deposit underlying tokens (assets) to the Panoptic pool from the LP and mint corresponding amount of shares.

456: 		        // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid

635: 		    /// - The cost must be larger when the position is close to being in-range, and should be minimal when it is far from being in range. eg. Exercising a (1000, 1050)

637: 		    /// - The cost is an exponentially decaying function of the distance between the position's strike and the current price

706: 		                // note: the delta for one token will be positive and the other will be negative. This cancels out any moves in their positions

723: 		            // note: we HAVE to start with a negative number as the base exercise cost because when shifting a negative number right by n bits,

725: 		            // this divergence is observed when n (the number of half ranges) is > 10 (ensuring the floor is not zero, but -1 = 1bps at that point)

727: 		            int256 fee = (FORCE_EXERCISE_COST >> (maxNumRangesFromStrike - 1)); // exponential decay of fee based on number of half ranges away from the price

736: 		    /// @notice Get the pool utilization; it is a measure of the ratio of assets in the AMM vs the total assets managed by the pool.

774: 		        /// if utilization is less than zero, this is the calculation for a strangle, which gets 2x the capital efficiency at low pool utilization

814: 		        // aka the buy ratio starts high and drops to a lower value with increased utilization; the sell ratio does the opposite (slope is positive)

820: 		        // this denotes a situation where the median is too far away from the current price, so we need to require fully collateralized positions for safety

851: 		                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

974: 		    /// @param assets The amount of assets to refund. Positive means a transfer from refunder to refundee, vice versa for negative.

993: 		    /// @param swappedAmount The amount of tokens swapped during creation of the option position (non-zero for options minted ITM).

1005: 		            // constrict premium to only assets not belonging to PLPs (i.e premium paid by sellers or collected from the pool earlier)

1025: 		            // the inflow or outflow of pool assets is defined by the swappedAmount: it includes both the ITM swap amounts and the short/long amounts used to create the position

1026: 		            // however, any intrinsic value is paid for by the users, so we only add the portion that comes from PLPs: the short/long amounts

1095: 		    /// @return exchangedAmount The amount of funds to be exchanged for minting an option (includes commission, swapFee, and intrinsic value).

1137: 		    /// @param positionBalanceArray The list of all historical positions held by the 'optionOwner', stored as [[tokenId, balance/poolUtilizationAtMint], ...].

1155: 		    /// @param positionBalanceArray the list of all historical positions held by the 'optionOwner', stored as [[tokenId, balance/poolUtilizationAtMint], ...].

1172: 		            // If premium is negative (ie. user has to pay for their purchased options), add this long premium to the token requirement

1195: 		    /// @notice Get the total required amount of collateral tokens of a user/account across all active positions to stay above the margin requirement.

1196: 		    /// @dev Returns the token amounts required for the entire account with active positions in 'positionIdList' (list of tokenIds).

1198: 		    /// @param positionBalanceArray The list of all historical positions held by the 'optionOwner', stored as [[tokenId, balance/poolUtilizationAtMint], ...].

1199: 		    /// @return tokenRequired The amount of tokens required to stay above the margin threshold for all active positions of user.

1238: 		    /// @notice Get the required amount of collateral tokens corresponding to a specific single position 'tokenId' at a price 'tick'.

1239: 		    /// The required collateral of an account depends on the price ('tick') in the AMM pool: if in the position's favor less collateral needed, etc.

1270: 		    /// @notice Calculate the required amount of collateral for a single leg 'index' of position 'tokenId' when the leg does not have a risk partner.

1303: 		    /// @notice Calculate the required amount of collateral for leg 'index' of position 'tokenId' when the leg does not have a risk partner.

1416: 		                        // position is in-the-money, collateral requirement = amountMoved*(1-SRC)*(scaleFactor-ratio)/(scaleFactor+1) + SCR*amountMoved

1424: 		    /// @notice Calculate the required amount of collateral for leg 'index' for position 'tokenId' accounting for its partner leg.

1425: 		    /// @notice If the two token long-types are different (one is a long, the other a short, e.g.) but the tokenTypes are the same, this is a spread

1427: 		    /// @notice If the two token long-types are the same but the tokenTypes are different (one is a call, the other a put, e.g.), this is a strangle -

1430: 		    ///   1) The difference in notional value at both strikes: abs(strikeLong - strikeShort) or abs(strikeShort - strikeLong)

1432: 		    /// @dev If a position is a strangle, only one leg can be tested at a time which allows us to increase the capital efficiency.

1438: 		    /// @return required the required amount collateral needed for this leg 'index', accounting for what the leg's risk partner is.

1467: 		    /// @notice For a given incoming 'amount' - which is the size of a user position (e.g. opening a position), what is the corresponding required collateral to have.

1468: 		    /// @dev NOTE this does not depend on the price of the AMM pool. This only computes what is needed in response to the current utilization.

1593: 		    /// @dev A strangle can only have only one of its leg tested at the same time, so this reduces the total risk and collateral requirement.
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L25), [28](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L28), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L88), [92](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L92), [111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L111), [135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L135), [199](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L199), [213](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L213), [214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L214), [215](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L215), [257](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L257), [272](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L272), [274](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L274), [276](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L276), [290](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L290), [304](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L304), [311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L311), [400](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L400), [410](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L410), [456](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L456), [635](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L635), [637](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L637), [706](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L706), [723](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L723), [725](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L725), [727](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L727), [736](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L736), [774](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L774), [814](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L814), [820](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L820), [851](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L851), [974](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L974), [993](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L993), [1005](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1005), [1025](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1025), [1026](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1026), [1095](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1095), [1137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1137), [1155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1155), [1172](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1172), [1195](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1195), [1196](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1196), [1198](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1198), [1199](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1199), [1238](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1238), [1239](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1239), [1270](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1270), [1303](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1303), [1416](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1416), [1424](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1424), [1425](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1425), [1427](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1427), [1430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1430), [1432](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1432), [1438](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1438), [1467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1467), [1468](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1468), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1593)]



```solidity
File: contracts/PanopticFactory.sol

102: 		    /// @notice Mapping from address(UniswapV3Pool) to address(PanopticPool) that stores the address of all deployed Panoptic Pools

257: 		        // If this is not the case, we increase the next cardinality during deployment so the cardinality can catch up over time

286: 		    /// @param salt Salt value ([160-bit deployer address][96-bit nonce]) to start from, useful as a checkpoint across multiple calls

288: 		    /// @param minTargetRarity The minimum target rarity to mine for. The internal loop stops when this is reached *or* when no more iterations

348: 		        // In this case, the `fullRangeLiquidity` will always be an underestimate in respect to the token amounts required to mint.
```
[[102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L102), [257](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L257), [286](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L286), [288](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L288), [348](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L348)]



```solidity
File: contracts/PanopticPool.sol

37: 		    /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.

62: 		    /// @param settledAmounts LeftRight encoding for the amount of premium settled for token0 (right slot) and token1 (left slot).

88: 		    /// @param poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),

90: 		    /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.

114: 		    /// @dev Only include the share of (settled) premium that is available to collect when calling `_calculateAccumulatedPremia`

132: 		    // This oracle is updated with the last Uniswap observation during `mintOptions` if MEDIAN_PERIOD has elapsed past the last observation

133: 		    // If true, the "slow" oracle price is instead computed on-the-fly from 7 Uniswap observations (spaced 5 observations apart) irrespective of the frequency of `mintOptions` calls

145: 		    /// In this case, if there is an interaction every block, the "fast" oracle can consider 3 consecutive block end prices (min=36 seconds on Ethereum)

152: 		    /// @dev Structured such that the minimum total observation time is 7 minutes on Ethereum (similar to internal median mode)

155: 		    // The maximum allowed delta between the currentTick and the Uniswap TWAP tick during a liquidation (~5% down, ~5.26% up)

160: 		    /// Falls back on the more conservative (less solvent) tick during times of extreme volatility (to ensure the account is always solvent)

171: 		    // multiplier (x10k) for the collateral requirement in the event of a buying power decrease, such as minting or force exercising

238: 		    // collected for every chunk per unit of liquidity (net or short, depending on the isLong value of the specific leg index)

242: 		    /// @dev Per-chunk `last` value that gives the aggregate amount of premium owed to all sellers when multiplied by the total amount of liquidity `totalLiquidity`

254: 		    /// @dev Tracks the amount of liquidity for a user+tokenId (right slot) and the initial pool utilizations when that position was minted (left slot)

268: 		    /// The accumulator also tracks the total number of positions (ie. makes sure the length of the provided positionIdList matches);

271: 		    /// this hash can be cheaply verified on every operation with a user provided positionIdList - and we can use that for operations

279: 		    /// @notice During construction: sets the address of the panoptic factory smart contract and the SemiFungiblePositionMananger (SFPM).

369: 		        // the 64 most significant bits are the utilization of token1, so we can shift the number to the right by 64 to extract it

378: 		    /// @param includePendingPremium true = include premium that is owed to the user but has not yet settled, false = only include premium that is available to collect.

381: 		    /// @return balances A list of balances and pool utilization for each position, of the form [[tokenId0, balances0], [tokenId1, balances1], ...].

426: 		    /// @param computeAllPremia Whether to compute accumulated premia for all legs held by the user (true), or just owed premia for long legs (false).

427: 		    /// @param includePendingPremium true = include premium that is owed to the user but has not yet settled, false = only include premium that is available to collect.

428: 		    /// @return portfolioPremium The computed premia of the user's positions, where premia contains the accumulated premia for token0 in the right slot and for token1 in the left slot.

429: 		    /// @return balances A list of balances and pool utilization for each position, of the form [[tokenId0, balances0], [tokenId1, balances1], ...].

481: 		                    portfolioPremium = portfolioPremium.add(premiaByLeg[leg]); //@audit-info adds it if is long or includePendingPremium = true

495: 		    /// @notice Disable slippage checks if tickLimitLow == tickLimitHigh and reverses ticks if given in correct order to enable ITM swaps

542: 		    /// @param positionIdList the list of currently held positions by the user, where the newly minted position(token) will be the last element in 'positionIdList'.

544: 		    /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position.

576: 		        _burnOptions(COMMIT_LONG_SETTLED, tokenId, msg.sender, tickLimitLow, tickLimitHigh); //@audit-issue M - why no update median?

609: 		    /// @param positionIdList the list of currently held positions by the user, where the newly minted position(token) will be the last element in 'positionIdList'.

611: 		    /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position.

676: 		    /// @return poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool) at the time of minting,

704: 		    /// @return poolUtilizations Packing of the pool utilization (how much funds are in the Panoptic pool versus the AMM pool at the time of minting),

706: 		    /// Where totalAssets is the total tracked assets in the AMM and PanopticPool minus fees and donations to the Panoptic pool.

738: 		    /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position

882: 		    /// @notice Falls back to the more conservative tick if the delta between the fast and slow oracle exceeds `MAX_SLOW_FAST_DELTA`.

883: 		    /// @dev Effectively, this means that the users must be solvent at both the fast and slow oracle ticks if one of them is stale to mint or burn options.

887: 		    /// @return medianData If nonzero (enough time has passed since last observation), the updated value for `s_miniMedian` with a new observation

943: 		        // If one of the ticks is too stale, we fall back to the more conservative tick, i.e, the user must be solvent at both the fast and slow oracle ticks.

1013: 		    /// @dev Will revert if liquidated account is solvent at the TWAP tick or if TWAP tick is too far away from the current tick.

1016: 		    /// @param delegations LeftRight amounts of token0 and token1 (token0:token1 right:left) delegated to the liquidatee by the liquidator so the option can be smoothly exercised.

1071: 		        // Works like a transfer, so the liquidator must possess all the tokens they are delegating, resulting in no net supply change

1084: 		            // Do not commit any settled long premium to storage - we will do this after we determine if any long premium must be revoked

1113: 		            // thus, we haircut any premium paid by the liquidatee (converting tokens as necessary) until the protocol loss is covered or the premium is exhausted

1114: 		            // note that the haircutPremia function also commits the settled amounts (adjusted for the haircut) to storage, so it will be called even if there is no haircut

1116: 		            // if premium is haircut from a token that is not in protocol loss, some of the liquidation bonus will be converted into that token

1188: 		        // '_calculateAccumulatedPremia' expects a list of positions to be touched, and this is the only way to pass a single position

1191: 		        // validate the exercisor's position list (the exercisee's list will be evaluated after their position is force exercised)

1290: 		    /// @notice check whether an account is solvent at a given `atTick` with a collateral requirement of `buffer`/10_000 multiplied by the requirement of `positionIdList`.

1340: 		    /// @param tokenData0 Leftright encoded word with balance of token0 in the right slot, and required balance in left slot.

1341: 		    /// @param tokenData1 Leftright encoded word with balance of token1 in the right slot, and required balance in left slot.

1384: 		        // note that if pLength == 0 even if a user has existing position(s) the below will fail b/c the fingerprints will mismatch

1403: 		    /// @notice Updates the hash for all positions owned by an account. This fingerprints the list of all incoming options with a single hash.

1406: 		    /// @dev The positions hash is stored as the XOR of the keccak256 of each tokenId. Updating will XOR the existing hash with the new tokenId.

1407: 		    /// The same update can either add a new tokenId (when minting an option), or remove an existing one (when burning it) - this happens through the XOR.

1410: 		    /// @param addFlag Pass addFlag=true when this is adding a position, needed to ensure the number of positions increases or decreases.

1469: 		    /// @param effectiveLiquidityLimitX32 Maximum amount of "spread" defined as totalLiquidity/netLiquidity for a new position

1497: 		        // the effective liquidity measures how many times more the newly added liquidity is compared to the existing/base liquidity

1506: 		    /// @param computeAllPremia Whether to compute accumulated premia for all legs held by the user (true), or just owed premia for long legs (false).

1548: 		                    // if the premium accumulatorLast is higher than current, it means the premium accumulator has overflowed and rolled over at least once

1550: 		                    // if there are multiple rollovers or the rollover goes past the last accumulator, rolled over fees will just remain unclaimed

1588: 		    /// @dev Called by sellers on buyers of their chunk to increase the available premium for withdrawal (before closing their position).

1590: 		    /// @param positionIdList Exhaustive list of open positions for the `owners` used for solvency checks where the tokenId to be settled is the last element.

1696: 		                // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64

1759: 		    /// @param grossPremiumLast The `last` values used with `premiumAccumulators` to compute the total premium owed to sellers
```
[[37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L37), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L62), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L88), [90](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L90), [114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L114), [132](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L132), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L133), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L145), [152](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L152), [155](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L155), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L160), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L171), [238](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L238), [242](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L242), [254](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L254), [268](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L268), [271](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L271), [279](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L279), [369](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L369), [378](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L378), [381](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L381), [426](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L426), [427](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L427), [428](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L428), [429](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L429), [481](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L481), [495](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L495), [542](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L542), [544](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L544), [576](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L576), [609](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L609), [611](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L611), [676](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L676), [704](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L704), [706](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L706), [738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L738), [882](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L882), [883](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L883), [887](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L887), [943](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L943), [1013](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1013), [1016](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1016), [1071](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1071), [1084](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1084), [1113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1113), [1114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1114), [1116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1116), [1188](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1188), [1191](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1191), [1290](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1290), [1340](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1340), [1341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1341), [1384](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1384), [1403](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1403), [1406](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1406), [1407](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1407), [1410](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1410), [1469](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1469), [1497](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1497), [1506](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1506), [1548](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1548), [1550](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1550), [1588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1588), [1590](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1590), [1696](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1696), [1759](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1759)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

24: 		//                       ,.                                   .,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.                                    ,,

25: 		//                    ,,,,,,,                           ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                            ,,,,,,

26: 		//                  .,,,,,,,,,,.                   ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                     ,,,,,,,,,,,

27: 		//                .,,,,,,,,,,,,,,,             ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.              ,,,,,,,,,,,,,,,

28: 		//               ,,,,,,,,,,,,,,.            ,,,,,,,,,,,,,,,,,,,,,,,,,,,                ,,,,,,,,,,,,,,,,,,,,,,,,,,.             ,,,,,,,,,,,,,,,

29: 		//             ,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,,,,,,                                ,,,,,,,,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,,

30: 		//            ,,,,,,,,,,,,,.           ,,,,,,,,,,,,,,,,,,                                           .,,,,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,

31: 		//          ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,,,.                                                  ,,,,,,,,,,,,,,,,,           .,,,,,,,,,,,,,

32: 		//         ,,,,,,,,,,,,,.         .,,,,,,,,,,,,,,,.                                                        ,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,.

33: 		//        ,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,                                                              ,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

34: 		//       ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,.                                                                  ,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

35: 		//      ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,                                                                      ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,

36: 		//     ,,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                         ,,,,,,,,,,,,,,          ,,,,,,,,,,,,.

37: 		//    .,,,,,,,,,,,,        .,,,,,,,,,,,,,                                                                            ,,,,,,,,,,,,,          ,,,,,,,,,,,,

38: 		//    ,,,,,,,,,,,,         ,,,,,,,,,,,,                                                                               ,,,,,,,,,,,,,         .,,,,,,,,,,,,

39: 		//   ,,,,,,,,,,,,         ,,,,,,,,,,,,                                                                                 ,,,,,,,,,,,,.         ,,,,,,,,,,,,

40: 		//   ,,,,,,,,,,,,        ,,,,,,,,,,,,.                █████████  ███████████ ███████████  ██████   ██████               ,,,,,,,,,,,,          ,,,,,,,,,,,,

41: 		//  .,,,,,,,,,,,,        ,,,,,,,,,,,,                ███░░░░░███░░███░░░░░░█░░███░░░░░███░░██████ ██████                .,,,,,,,,,,,,         ,,,,,,,,,,,,

42: 		//  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░███    ░░░  ░███   █ ░  ░███    ░███ ░███░█████░███                 ,,,,,,,,,,,,         ,,,,,,,,,,,,.

43: 		//  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░░█████████  ░███████    ░██████████  ░███░░███ ░███                 .,,,,,,,,,,,          ,,,,,,,,,,,.

44: 		//  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ░░░░░░░░███ ░███░░░█    ░███░░░░░░   ░███ ░░░  ░███                  ,,,,,,,,,,,.         ,,,,,,,,,,,,

45: 		//  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ███    ░███ ░███  ░     ░███         ░███      ░███                  ,,,,,,,,,,,,         ,,,,,,,,,,,,

46: 		//  ,,,,,,,,,,,,        ,,,,,,,,,,,,                ░░█████████  █████       █████        █████     █████                 ,,,,,,,,,,,          ,,,,,,,,,,,,

47: 		//  ,,,,,,,,,,,,        ,,,,,,,,,,,,                 ░░░░░░░░░  ░░░░░       ░░░░░        ░░░░░     ░░░░░                 ,,,,,,,,,,,,          ,,,,,,,,,,,.

48: 		//  ,,,,,,,,,,,,        .,,,,,,,,,,,.                                                                                    ,,,,,,,,,,,,         ,,,,,,,,,,,,

49: 		//  .,,,,,,,,,,,,        ,,,,,,,,,,,,                                                                                   .,,,,,,,,,,,,         ,,,,,,,,,,,,

50: 		//   ,,,,,,,,,,,,        ,,,,,,,,,,,,,                                                                                  ,,,,,,,,,,,,          ,,,,,,,,,,,,

51: 		//   ,,,,,,,,,,,,.        ,,,,,,,,,,,,.                                                                                ,,,,,,,,,,,,.         ,,,,,,,,,,,,

52: 		//    ,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                              ,,,,,,,,,,,,,         .,,,,,,,,,,,,

53: 		//     ,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                            ,,,,,,,,,,,,,         .,,,,,,,,,,,,

54: 		//     .,,,,,,,,,,,,         ,,,,,,,,,,,,,                                                                         ,,,,,,,,,,,,,.          ,,,,,,,,,,,,

55: 		//      ,,,,,,,,,,,,,         ,,,,,,,,,,,,,,                                                                     .,,,,,,,,,,,,,.          ,,,,,,,,,,,,

56: 		//       ,,,,,,,,,,,,,         .,,,,,,,,,,,,,,                                                                 .,,,,,,,,,,,,,,          .,,,,,,,,,,,,

57: 		//        ,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,                                                             ,,,,,,,,,,,,,,,.          ,,,,,,,,,,,,,.

58: 		//         ,,,,,,,,,,,,,,          ,,,,,,,,,,,,,,,,                                                       .,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,

59: 		//          .,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,                                                 .,,,,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,

60: 		//            ,,,,,,,,,,,,,,           ,,,,,,,,,,,,,,,,,,,.                                        ,,,,,,,,,,,,,,,,,,,.            ,,,,,,,,,,,,,,

61: 		//             ,,,,,,,,,,,,,,,            ,,,,,,,,,,,,,,,,,,,,,,                             .,,,,,,,,,,,,,,,,,,,,,,             ,,,,,,,,,,,,,,

62: 		//               ,,,,,,,,,,,,,,,            .,,,,,,,,,,,,,,,,,,,,,,,,,,,,,.        ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,             .,,,,,,,,,,,,,,.

63: 		//                 ,,,,,,,,,,,,,,.              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,               ,,,,,,,,,,,,,,,

64: 		//                   ,,,,,,,,,,                     ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                     .,,,,,,,,,,

65: 		//                     ,,,,,.                            ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                             ,,,,,,

132: 		    // The effect of vegoid on the long premium multiplier can be explored here: https://www.desmos.com/calculator/mdeqob2m04

173: 		    /// @dev mapping that stores the liquidity data of keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))

174: 		    // liquidityData is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user

175: 		    // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller

176: 		    // the reason why it is called "removedLiquidity" is because long options are created by removed liquidity -ie. short selling LP positions

291: 		    /// @dev mapping that stores a LeftRight packing of feesBase of  keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))

292: 		    /// @dev Base fees is stored as int128((feeGrowthInside0LastX128 * liquidity) / 2**128), which allows us to store the accumulated fees as int128 instead of uint256

294: 		    /// feesBase represents the baseline fees collected by the position last time it was updated - this is recalculated every time the position is collected from with the new value

467: 		    /// @param slippageTickLimitLow The lower price slippage limit when minting an ITM position (set to larger than slippageTickLimitHigh for swapping when minting)

468: 		    /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)

469: 		    /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

470: 		    /// @return totalSwapped A LeftRight encoded word containing the total amount of token0 and token1 swapped if minting ITM

500: 		    /// @param slippageTickLimitLow The lower price slippage limit when minting an ITM position (set to larger than slippageTickLimitHigh for swapping when minting)

501: 		    /// @param slippageTickLimitHigh The higher slippage limit when minting an ITM position (set to lower than slippageTickLimitLow for swapping when minting)

502: 		    /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

503: 		    /// @return totalSwapped A LeftRight encoded word containing the total amount of token0 and token1 swapped if minting ITM

547: 		        // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call

554: 		        // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)

573: 		        // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call

588: 		    /// @dev token transfers are only allowed if you transfer your entire liquidity of a given chunk and the recipient has none

660: 		    /// @notice Helper that checks the proposed option position and size and forwards the minting and potential swapping tasks.

665: 		    /// @notice and then forwards the minting/burning/swapping to another internal helper functions which perform the AMM pool actions.

679: 		    /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

717: 		            // if the in-the-money amount is not zero (i.e. positions were minted ITM) and the user did provide tick limits LOW > HIGH, then swap necessary amounts

732: 		    /// @notice When a position is minted or burnt in-the-money (ITM) we are *not* 100% token0 or 100% token1: we have a mix of both tokens.

733: 		    /// @notice The swapping for ITM options is needed because only one of the tokens are "borrowed" by a user to create the position.

751: 		    ///   If we take token0 as an example, we deploy it to the AMM pool and *then* swap to get the right mix of token0 and token1

753: 		    ///   It that position is burnt, then we remove a mix of the two tokens and swap one of them so that the user receives only one.

785: 		            // note: upstream users of this function such as the Panoptic Pool should ensure users always compensate for the ITM amount delta

786: 		            // the netting swap is not perfectly accurate, and it is possible for swaps to run out of liquidity, so we do not want to rely on it

792: 		                // note: negative ITM amounts denote a surplus of tokens (burning liquidity), while positive amounts denote a shortage of tokens (minting liquidity)

862: 		    /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg

937: 		        // Ensure upper bound on amount of tokens contained across all legs of the position on any given tick does not exceed a maximum of (2**127-1).

938: 		        // This is the maximum value of the `int128` type we frequently use to hold token amounts, so a given position's size should be guaranteed to

993: 		            // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user

994: 		            // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller

995: 		            // the reason why it is called "removedLiquidity" is because long options are created by removing -ie.short selling LP positions

1012: 		                // so we seek to move the incoming liquidity chunk *out* of uniswap - but was there sufficient liquidity sitting in uniswap

1122: 		        // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)

1123: 		        // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing

1133: 		    /// @notice Compute the feesGrowth * liquidity / 2**128 by reading feeGrowthInside0LastX128 and feeGrowthInside1LastX128 from univ3pool.positions.

1138: 		    /// @dev stored fees base is rounded up and the current fees base is rounded down to minimize the amount of fees collected (Δfeesbase) in favor of the protocol

1161: 		        /// @dev here we're converting the value to an int128 even though all values (feeGrowth, liquidity, Q128) are strictly positive.

1162: 		        /// That's because of the way feeGrowthInside works in Uniswap v3, where it can underflow when stored for the first time.

1163: 		        /// This is not a problem in Uniswap v3 because the fees are always calculated by taking the difference of the feeGrowths,

1165: 		        /// So by using int128 instead of uint128, we remove the need to handle extremely large underflows and simply allow it to be negative

1220: 		    /// @notice Burn a chunk of liquidity (`liquidityChunk`) in the Uniswap v3 pool and send to msg.sender; return the amount moved.

1248: 		    /// @notice Helper to collect amounts between msg.sender and Uniswap and also to update the Uniswap fees collected to date from the AMM.

1255: 		    /// @return collectedChunk the incoming amount collected with potentially whatever is collected in this function added to it

1320: 		    /// @return deltaPremiumOwed The extra premium (per liquidity X64) to be added to the owed accumulator for token0 (right) and token1 (left)

1321: 		    /// @return deltaPremiumGross The extra premium (per liquidity X64) to be added to the gross accumulator for token0 (right) and token1 (left)

1335: 		        // explains how we get from the premium per liquidity (calculated here) to the total premia collected and the multiplier

1421: 		    /// @return accountLiquidities The amount of liquidity that has been shorted/added to the Uniswap contract (netLiquidity:removedLiquidity -> rightSlot:leftSlot)

1430: 		        /// @dev tokenType input here is the asset of the positions minted, this avoids put liquidity to be used for call, and vice-versa

1436: 		    /// @notice Return the premium associated with a given position, where Premium is an accumulator of feeGrowth for the touched position.

1437: 		    /// @dev Computes s_accountPremium{isLong ? Owed : Gross}[keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))]

1438: 		    /// @dev if an atTick parameter is provided that is different from type(int24).max, then it will update the premium up to the current

1439: 		    /// @dev block at the provided atTick value. We do this because this may be called immediately after the Uni v3 pool has been touched

1446: 		    /// @param atTick The current tick. Set atTick < type(int24).max = 8388608 to get latest premium up to the current block

1448: 		    /// @return premiumToken0 The amount of premium (per liquidity X64) for token0 = sum (feeGrowthLast0X128) over every block where the position has been touched

1449: 		    /// @return premiumToken1 The amount of premium (per liquidity X64) for token1 = sum (feeGrowthLast0X128) over every block where the position has been touched

1465: 		        // Compute the premium up to the current block (ie. after last touch until now). Do not proceed if atTick == type(int24).max = 8388608

1479: 		                    // currentFeesGrowth (calculated from FeesCalc.calculateAMMSwapFeesLiquidityChunk) is (ammFeesCollectedPerLiquidity * liquidityChunk.liquidity())

1480: 		                    // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])

1506: 		                // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)

1507: 		                // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing
```
[[24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L24), [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L25), [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L26), [27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L27), [28](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L28), [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L29), [30](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L30), [31](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L31), [32](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L32), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L33), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L34), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L35), [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L36), [37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L37), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L38), [39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L39), [40](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L40), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L41), [42](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L42), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L43), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L44), [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L45), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L46), [47](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L47), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L48), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L49), [50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L50), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L51), [52](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L52), [53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L53), [54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L54), [55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L55), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L56), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L57), [58](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L58), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L59), [60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L60), [61](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L61), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L62), [63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L63), [64](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L64), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L65), [132](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L132), [173](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L173), [174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L174), [175](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L175), [176](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L176), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L291), [292](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L292), [294](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L294), [467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L467), [468](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L468), [469](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L469), [470](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L470), [500](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L500), [501](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L501), [502](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L502), [503](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L503), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L547), [554](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L554), [573](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L573), [588](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L588), [660](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L660), [665](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L665), [679](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L679), [717](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L717), [732](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L732), [733](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L733), [751](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L751), [753](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L753), [785](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L785), [786](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L786), [792](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L792), [862](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L862), [937](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L937), [938](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L938), [993](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L993), [994](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L994), [995](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L995), [1012](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1012), [1122](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1122), [1123](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1123), [1133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1133), [1138](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1138), [1161](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1161), [1162](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1162), [1163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1163), [1165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1165), [1220](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1220), [1248](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1248), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1255), [1320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1320), [1321](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1321), [1335](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1335), [1421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1421), [1430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1430), [1436](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1436), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1437), [1438](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1438), [1439](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1439), [1446](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1446), [1448](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1448), [1449](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1449), [1465](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1465), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1479), [1480](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1480), [1506](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1506), [1507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1507)]



```solidity
File: contracts/libraries/CallbackLib.sol

11: 		/// @notice This library provides functions to verify that a callback came from a canonical Uniswap V3 pool with a claimed set of features.
```
[[11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L11)]



```solidity
File: contracts/libraries/Errors.sol

18: 		    /// @notice PanopticPool: the effective liquidity (X32) is greater than min(`MAX_SPREAD`, `USER_PROVIDED_THRESHOLD`) during a long mint or short burn

22: 		    /// @notice CollateralTracker: attempted to withdraw/redeem more than available liquidity, owned shares, or open positions would allow for

25: 		    /// @notice PanopticPool: force exercisee is insolvent - liquidatable accounts are not permitted to open or close positions outside of a liquidation

41: 		    /// @param parameterType poolId=0, ratio=1, tokenType=2, risk_partner=3 , strike=4, width=5, two identical strike/width/tokenType chunks=6

44: 		    /// @notice A mint or swap callback was attempted from an address that did not match the canonical Uniswap V3 pool with the claimed features
```
[[18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L18), [22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L22), [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L25), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L41), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L44)]



```solidity
File: contracts/libraries/FeesCalc.sol

17: 		/// @dev Some options positions involve moving liquidity chunks to the AMM/Uniswap. Those chunks can then earn AMM swap fees.

96: 		    /// @return The fees collected from the AMM for each token (LeftRight-packed) with token0 in the right slot and token1 in the left slot
```
[[17](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L17), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L96)]



```solidity
File: contracts/libraries/InteractionHelper.sol

19: 		    /// @notice Function that performs approvals on behalf of the PanopticPool for CollateralTracker and SemiFungiblePositionManager.

41: 		    /// @notice Computes the name of a CollateralTracker based on the token composition and fee of the underlying Uniswap Pool.

42: 		    /// @dev Some tokens do not have proper symbols so error handling is required - this logic takes up significant bytecode size, which is why it is in a library.
```
[[19](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L19), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L41), [42](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L42)]



```solidity
File: contracts/libraries/Math.sol

124: 		    /// @dev Implemented using Uniswap's "incorrect" constants. Supplying commented-out real values for an accurate calculation.

241: 		    function getLiquidityForAmount0( //@audit-info price is new: https://github.com/Uniswap/v3-periphery/blob/main/contracts/libraries/LiquidityAmounts.sol#L23

334: 		    /// @notice Calculates floor(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0.

435: 		    /// @notice Calculates ceil(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0.

502: 		            // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

565: 		            // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

642: 		            // Divide [prod1 prod0] by the factors of two (note that this is just 2**128 since the denominator is a power of 2 itself)

719: 		            // Divide [prod1 prod0] by the factors of two (note that this is just 2**96 since the denominator is a power of 2 itself)

748: 		    /// @notice QuickSort is a sorting algorithm that employs the Divide and Conquer strategy. It selects a pivot element and arranges the given array around
```
[[124](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L124), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L241), [334](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L334), [435](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L435), [502](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L502), [565](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L565), [642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L642), [719](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L719), [748](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L748)]



```solidity
File: contracts/libraries/PanopticMath.sol

34: 		    ///      the 64 bits are the 48 *last* (most significant) bits - and thus corresponds to the *first* 12 hex characters (reading left to right)

35: 		    ///      of the Uniswap v3 pool address, with the tickSpacing written in the highest 16 bits (i.e, max tickSpacing is 32768)

86: 		    /// @notice The positions hash contains a single fingerprint of all positions created by an account/user as well as a tally of the positions.

88: 		    /// @param existingHash The existing position hash containing all historical N positions created and the count of the positions

90: 		    /// @param addFlag Whether to mint (add) the tokenId to the count of positions or burn (subtract) it from the count (existingHash >> 248) +/- 1

114: 		    /// @dev Uniswap observations snapshot the closing price of the last block before the first interaction of a given block.

115: 		    /// @dev The maximum frequency of observations is 1 per block, but there is no guarantee that the pool will be observed at every block.

116: 		    /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.

117: 		    /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).

136: 		            // get the last 4 timestamps/tickCumulatives (if observationIndex < cardinality, the index will wrap back from observationCardinality)

147: 		            // use cardinality periods given by cardinality + 1 accumulator observations to compute the last cardinality observed ticks spaced by period

159: 		    /// @notice Takes a packed structure representing a sorted 7-slot ring buffer of ticks and returns the median of those values.

160: 		    /// @dev Also inserts the latest Uniswap observation into the buffer, resorts, and returns if the last entry is at least `period` seconds old.

163: 		    /// @param period The minimum time in seconds that must have passed since the last observation was inserted into the buffer

167: 		    /// @return updatedMedianData The updated 7-slot ring buffer of ticks with the latest observation inserted if the last entry is at least `period` seconds old (returns 0 otherwise)

237: 		    /// @dev We instead observe the average price over a series of time intervals, and define the TWAP as the median of those averages.

274: 		    /// @notice For a given option position (`tokenId`), leg index within that position (`legIndex`), and `positionSize` get the tick range spanned and its

310: 		        //  Because Uni v3 chooses token0 and token1 from the alphanumeric order, there is no consistency as to whether token0 is

311: 		        //  stablecoin, ETH, or an ERC20. Some pools may want ETH to be the asset (e.g. ETH-DAI) and some may wish the stablecoin to

344: 		            // The max/min ticks that can be initialized are the closest multiple of tickSpacing to the actual max/min tick abs()=887272

365: 		    /// @notice Returns the distances of the upper and lower ticks from the strike for a position with the given width and tickSpacing.

385: 		    /// @notice Compute the amount of funds that are underlying this option position. This is useful when exercising a position.

388: 		    /// @return longAmounts Left-right packed word where the right contains the total contract size and the left total notional

389: 		    /// @return shortAmounts Left-right packed word where the right contains the total contract size and the left total notional

412: 		    /// @notice Adds required collateral and collateral balance from collateralTracker0 and collateralTracker1 and converts to single values in terms of `tokenType`.

413: 		    /// @param tokenData0 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token0)

414: 		    /// @param tokenData1 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token1)

438: 		    /// @notice Adds required collateral and collateral balance from collateralTracker0 and collateralTracker1 and converts to single values in terms of `tokenType`.

439: 		    /// @param tokenData0 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token0)

440: 		    /// @param tokenData1 LeftRight type container holding the collateralBalance (right slot) and requiredCollateral (left slot) for a user in CollateralTracker0 (expressed in terms of token1)

455: 		    /// @notice Compute the notional amount given an incoming total number of `contracts` deployed between `tickLower` and `tickUpper`.

456: 		    /// @dev The notional value of an option is the value of the crypto assets that are controlled (rather than the cost of the transaction).

461: 		    /// @dev Thus, `contracts` refer to "100" in this example. The $20 is the strike price. We get the strike price from `tickLower` and `tickUpper`.

462: 		    /// @dev From TradFi: [https://www.investopedia.com/terms/n/notionalvalue.asp](https://www.investopedia.com/terms/n/notionalvalue.asp).

485: 		    /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

502: 		    /// @notice Convert an amount of token1 into an amount of token0 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

519: 		    /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

542: 		    /// @notice Convert an amount of token0 into an amount of token1 given the sqrtPriceX96 in a Uniswap pool defined as sqrt(1/0)*2^96.

569: 		    /// @notice Compute the amount of token0 and token1 moved. Given an option position `tokenId`, leg index `legIndex`, and how many contracts are in the leg `positionSize`.

571: 		    /// @param positionSize The number of option contracts held in this position (each contract can control multiple tokens)

573: 		    /// @return A LeftRight encoded variable containing the amount0 and the amount1 value controlled by this option position's leg

642: 		    /// @param tokenData0 Leftright encoded word with balance of token0 in the right slot, and required balance in left slot

643: 		    /// @param tokenData1 Leftright encoded word with balance of token1 in the right slot, and required balance in left slot

650: 		    /// @return The LeftRight-packed protocol loss for both tokens, i.e., the delta between the user's balance and expended tokens

702: 		            // their actual balances at the time of computation may be higher, but these are a buffer representing the amount of tokens we

707: 		                    // liquidatee has insufficient token0 but some token1 left over, so we use what they have left to mitigate token0 losses

708: 		                    // we do this by substituting an equivalent value of token1 in our refund to the liquidator, plus a bonus, for the token0 we convert

709: 		                    // we want to convert the minimum amount of tokens required to achieve the lowest possible protocol loss (to avoid overpaying on the conversion bonus)

710: 		                    // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token1 balance: balance1 - paid1

712: 		                    // if the protocol loss is lower than the excess token1 balance, then we can fully mitigate the loss and we should only convert the loss amount

713: 		                    // if the protocol loss is higher than the excess token1 balance, we can only mitigate part of the loss, so we should convert only the excess token1 balance

725: 		                    // liquidatee has insufficient token1 but some token0 left over, so we use what they have left to mitigate token1 losses

726: 		                    // we do this by substituting an equivalent value of token0 in our refund to the liquidator, plus a bonus, for the token1 we convert

727: 		                    // we want to convert the minimum amount of tokens required to achieve the lowest possible protocol loss (to avoid overpaying on the conversion bonus)

728: 		                    // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token0 balance: balance0 - paid0

730: 		                    // if the protocol loss is lower than the excess token0 balance, then we can fully mitigate the loss and we should only convert the loss amount

731: 		                    // if the protocol loss is higher than the excess token0 balance, we can only mitigate part of the loss, so we should convert only the excess token0 balance

756: 		    /// @notice Haircut/clawback any premium paid by `liquidatee` on `positionIdList` over the protocol loss threshold during a liquidation.

757: 		    /// @dev Note that the storage mapping provided as the `settledTokens` parameter WILL be modified on the caller by this function.

765: 		    /// @param settledTokens The per-chunk accumulator of settled tokens in storage from which to subtract the haircut premium

910: 		    /// @notice Returns the original delegated value to a user at a certain tick based on the available collateral from the exercised user.

927: 		            // note: it is possible for refunds to be negative when the exercise fee is higher than the delegated amounts. This is expected behavior
```
[[34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L34), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L35), [86](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L86), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L88), [90](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L90), [114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L114), [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L115), [116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L116), [117](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L117), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L136), [147](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L147), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L159), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L160), [163](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L163), [167](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L167), [237](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L237), [274](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L274), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L310), [311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L311), [344](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L344), [365](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L365), [385](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L385), [388](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L388), [389](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L389), [412](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L412), [413](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L413), [414](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L414), [438](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L438), [439](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L439), [440](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L440), [455](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L455), [456](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L456), [461](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L461), [462](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L462), [485](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L485), [502](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L502), [519](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L519), [542](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L542), [569](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L569), [571](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L571), [573](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L573), [642](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L642), [643](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L643), [650](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L650), [702](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L702), [707](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L707), [708](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L708), [709](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L709), [710](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L710), [712](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L712), [713](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L713), [725](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L725), [726](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L726), [727](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L727), [728](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L728), [730](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L730), [731](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L731), [756](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L756), [757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L757), [765](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L765), [910](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L910), [927](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L927)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

57: 		    /// @notice Emitted when an attempt is made to initiate a transfer to a contract recipient that fails to signal support for ERC1155.
```
[[57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L57)]



```solidity
File: contracts/types/LeftRight.sol

51: 		    // Typically, the slot is already clear when writing to it, but if it is not, the bits will be added to the existing bits

53: 		    // Note that the values *within* the slots are allowed to overflow, but overflows are contained and will not leak into the other slot

113: 		    // Typically, the slot is already clear when writing to it, but if it is not, the bits will be added to the existing bits

115: 		    // Note that the values *within* the slots are allowed to overflow, but overflows are contained and will not leak into the other slot

272: 		    /// @dev Used for linked accumulators, so if the accumulator for one side overflows for a token, both cease to accumulate.
```
[[51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L51), [53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L53), [113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L113), [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L115), [272](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L272)]



```solidity
File: contracts/types/LiquidityChunk.sol

10: 		/// @title A Panoptic Liquidity Chunk. Tracks Tick Range and Liquidity Information for a "chunk." Used to track movement of chunks.

13: 		/// @notice A liquidity chunk is an amount of `liquidity` (an amount of WETH, e.g.) deployed between two ticks: `tickLower` and `tickUpper`
```
[[10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L10), [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L13)]



```solidity
File: contracts/types/TokenId.sol

24: 		// (0) univ3pool        48bits     0bits      : first 6 bytes of the Uniswap v3 pool address (first 48 bits; little-endian), plus a pseudorandom number in the event of a collision

43: 		//  <---- 48 bits ---->    <---- 48 bits ---->    <---- 48 bits ---->     <---- 48 bits ---->   <- 16 bits ->   <- 48 bits ->

44: 		//         Leg 4                  Leg 3                  Leg 2                   Leg 1          tickSpacing    Univ3 Pool Address

46: 		//  <--- most significant bit                                                                             least significant bit --->

51: 		//   - if a leg is active (e.g. leg 1) there can be no gaps in other legs meaning: if leg 1 is active then leg 3 cannot be active if leg 2 is inactive.

55: 		//  We also refer to the legs via their index, so leg number 2 has leg index 1 (legIndex) (counting from zero), and in general leg number N has leg index N-1.

56: 		//  - the underlying strike price of the 2nd leg (leg index = 1) in this option position starts at bit index  (64 + 12 + 48 * (leg index=1))=123

73: 		    /// @notice AND mask to clear all bits except for the components of the chunk key (strike, width, tokenType) for each leg

86: 		    /// @return The `poolId` (Panoptic's pool fingerprint, contains the whole 64 bit sequence with the tickSpacing) of the Uniswap V3 pool

144: 		    /// @notice Get the associated risk partner of the leg index (generally another leg index in the position if enabled or the same leg index if no partner).

164: 		    /// @notice Get the width of the nth leg (index `legIndex`). This is half the tick-range covered by the leg (tickUpper - tickLower)/2.

390: 		            // i.e the whole mask is used to flip all legs with 4 legs, but only the first leg is flipped with 1 leg so we shift by 3 legs

391: 		            // We also clear the poolId area of the mask to ensure the bits that are shifted right into the area don't flip and cause issues

430: 		    /// @dev ASSUMPTION: For any leg, the option ratio is always > 0 (the leg always has a number of contracts associated with it).

563: 		                    // if the two token long-types and the tokenTypes are both different (one is a short call, the other a long put, e.g.), this is a synthetic position

564: 		                    // A synthetic long or short is more capital efficient than each leg separated because the long+short premia accumulate proportionally

565: 		                    // unlike short stranlges, long strangles also cannot be partnered, because there is no reduction in risk (both legs can earn premia simultaneously)
```
[[24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L24), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L43), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L44), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L46), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L51), [55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L55), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L56), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L73), [86](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L86), [144](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L144), [164](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L164), [390](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L390), [391](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L391), [430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L430), [563](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L563), [564](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L564), [565](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L565)]



```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

8: 		/// @dev However, we cannot productively handle a failed approval and such a situation would surely cause a revert later in execution.

9: 		/// @dev In addition, no notable instances exist of tokens that both i) contain a failure case for `approve` and ii) return `false` instead of reverting.
```
[[8](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L8), [9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L9)]

</details>

---

### [N-66] Some variables have a implicit default visibility

Consider always adding an explicit visibility modifier for variables, as the default is `internal`.

*There are 8 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

131: 		    uint256 immutable TICK_DEVIATION;

136: 		    uint256 immutable COMMISSION_FEE;

141: 		    uint256 immutable SELLER_COLLATERAL_RATIO;

145: 		    uint256 immutable BUYER_COLLATERAL_RATIO;

149: 		    int256 immutable FORCE_EXERCISE_COST;

154: 		    uint256 immutable TARGET_POOL_UTIL;

158: 		    uint256 immutable SATURATED_POOL_UTIL;

162: 		    uint256 immutable ITM_SPREAD_MULTIPLIER;
```
[[131](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L131), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L136), [141](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L141), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L145), [149](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L149), [154](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L154), [158](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L158), [162](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L162)]


---

### [N-67] Consider adding a block/deny-list

This can help to prevent hackers from using stolen tokens, but as a side effect it will increase the project centralization.

*There are 3 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

36: 		contract CollateralTracker is ERC20Minimal, Multicall {
```
[[36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L36)]



```solidity
File: contracts/PanopticPool.sol

28: 		contract PanopticPool is ERC1155Holder, Multicall {
```
[[28](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L28)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

72: 		contract SemiFungiblePositionManager is ERC1155, Multicall {
```
[[72](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L72)]


---

### [N-68] Use of `override` is unnecessary

Starting with Solidity version [0.8.8](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding), using the override keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.

*There are 4 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

323: 		    function transfer(

341: 		    function transferFrom(
```
[[323](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

540: 		    function safeTransferFrom( //@audit-info new function

566: 		    function safeBatchTransferFrom(
```
[[540](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L540), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L566)]


---

### [N-69] Missing variable names

Consider adding a comment with the variable name even if it's not used, to improve the code readability.

*There are 2 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

392: 		    function maxDeposit(address) external pure returns (uint256 maxAssets) {

444: 		    function maxMint(address) external view returns (uint256 maxShares) {
```
[[392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L444)]


---

### [N-70] Typos in comments

Avoid typos, and proper nouns should be capitalized.

*There are 86 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

// @audit safecasting
37: 		    // Used for safecasting

// @audit initalized
92: 		    /// @dev As each instance is deployed via proxy clone, initial parameters must only be initalized once via startToken().

// @audit taylor
198: 		            // taylor expand log(1-sellCollateralRatio)/log(1.0001) around sellCollateralRatio=2000 up to 3rd order

// @audit exercisee
634: 		    /// - The forceExercisor will have to *pay* the exercisee because their position will be closed "against their will"

// @audit liquidatee
946: 		            // T: transferred shares from liquidatee which are a component of N but do not contribute toward protocol loss

// @audit refundee
969: 		    /// @notice Refunds delegated tokens to 'refunder' from 'refundee', similar to 'revoke'

// @audit refundee
971: 		    /// @dev can handle negative refund amounts that go from refundee to refunder in the case of high exercise fees.

// @audit refundee
972: 		    /// @param refunder The account refunding tokens to 'refundee'.

// @audit refundee
974: 		    /// @param assets The amount of assets to refund. Positive means a transfer from refunder to refundee, vice versa for negative.

// @audit premum
1180: 		        // if premium is positive (ie. user will receive funds due to selling options), add this premum to the user's balance

// @audit ith
1209: 		            // read the ith tokenId from the account
```
[[37](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L37), [92](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L92), [198](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L198), [634](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L634), [946](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L946), [969](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L969), [971](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L971), [972](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L972), [974](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L974), [1180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1180), [1209](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1209)]



```solidity
File: contracts/PanopticFactory.sol

// @audit numeraire
78: 		    /// @notice Address of the Wrapped Ether (or other numeraire token) contract

// @audit numeraire
110: 		    /// @param _WETH9 Address of the Wrapped Ether (or other numeraire token) contract

// @audit incentivize
237: 		        // Users can specify a salt, the aim is to incentivize the mining of addresses with leading zeros
```
[[78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L78), [110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L110), [237](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L237)]



```solidity
File: contracts/PanopticPool.sol

// @audit exercisor
50: 		    /// @param exerciseFee LeftRight encoding for the cost paid by the exercisor to force the exercise of the token.

// @audit caluculation
108: 		    // Flags used as arguments to premia caluculation functions

// @audit blocktime
143: 		    /// Note that the *minimum* total observation time is determined by the blocktime and may need to be adjusted by chain

// @audit subtick
336: 		    /// @dev Can also be used for more granular subtick precision on slippage checks

// @audit unliquidable
442: 		        for (uint256 k = 0; k < pLength; ) { //@audit H - uncapped positions -> unliquidable

// @audit slippagelimit
546: 		    /// @param tickLimitLow The lower tick slippagelimit.

// @audit slippagelimit
547: 		    /// @param tickLimitHigh The upper tick slippagelimit.

// @audit slippagelimit
613: 		    /// @param tickLimitLow The lower tick slippagelimit.

// @audit slippagelimit
614: 		    /// @param tickLimitHigh The upper tick slippagelimit.

// @audit liquidatee
1016: 		    /// @param delegations LeftRight amounts of token0 and token1 (token0:token1 right:left) delegated to the liquidatee by the liquidator so the option can be smoothly exercised.

// @audit liquidatee
1070: 		        // Perform the specified delegation from `msg.sender` to `liquidatee`

// @audit liquidatee
1072: 		        // If not enough tokens are delegated for the positions of `liquidatee` to be closed, the liquidation will fail

// @audit liquidatee
1082: 		            // burn all options from the liquidatee

// @audit liquidatee
1085: 		            // This is to prevent any short positions the liquidatee has being settled with tokens that will later be revoked

// @audit liquidatee
1109: 		            // premia cannot be paid if there is protocol loss associated with the liquidatee

// @audit liquidatee
1110: 		            // otherwise, an economic exploit could occur if the liquidator and liquidatee collude to

// @audit liquidatee
1113: 		            // thus, we haircut any premium paid by the liquidatee (converting tokens as necessary) until the protocol loss is covered or the premium is exhausted

// @audit exercisee
1174: 		    /// @notice Force the exercise of a single position. Exercisor will have to pay a fee to the force exercisee.

// @audit exercisee
1178: 		    /// @param positionIdListExercisee Post-burn list of open positions in the exercisee's (account) account

// @audit exercisor
1179: 		    /// @param positionIdListExercisor List of open positions in the exercisor's (msg.sender) account

// @audit exercisor, exercisee
1191: 		        // validate the exercisor's position list (the exercisee's list will be evaluated after their position is force exercised)

// @audit twap
1222: 		        //@audit doesnt check twap?

// @audit exercisor
1232: 		        // Note: tick limits are not applied here since it is not the exercisor's position being closed

// @audit exercisor
1270: 		        // refund the protocol any virtual shares after settling the difference with the exercisor

// @audit exercisor
1276: 		        // the exercisor's position list is validated above

// @audit overstimate
1357: 		            // overstimate by rounding up
```
[[50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L50), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L108), [143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L143), [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L336), [442](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L442), [546](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L546), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L547), [613](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L613), [614](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L614), [1016](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1016), [1070](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1070), [1072](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1072), [1082](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1082), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1085), [1109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1109), [1110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1110), [1113](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1113), [1174](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1174), [1178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1178), [1179](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1179), [1191](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1191), [1222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1222), [1232](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1232), [1270](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1270), [1276](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1276), [1357](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1357)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit safecasting
108: 		    // Used for safecasting

// @audit ν
128: 		    // ν = 1/2**VEGOID = multiplicative factor for long premium (Eqns 1-5)

// @audit vegoid, streamia
130: 		    // and vegoid modifies the sensitivity of the streamia to changes in that utilization,

// @audit ν
216: 		              spread = ν*(liquidity removed from that strike)/(netLiquidity remaining at that strike)
217: 		                     = ν*R/N
218: 		
219: 		        For an arbitrary parameter 0 <= ν <= 1 (ν = 1/2^VEGOID). This way, the gross_feesCollectedX128 will be given by: 
220: 		
221: 		              gross_feesCollectedX128 = feeGrowthX128 * N + feeGrowthX128*R*(1 + ν*R/N) 
222: 		                                      = feeGrowthX128 * T + feesGrowthX128*ν*R^2/N         
223: 		                                      = feeGrowthX128 * T * (1 + ν*R^2/(N*T))                (Eqn 2)
224: 		        
225: 		        The s_accountPremiumOwed accumulator tracks the feeGrowthX128 * R * (1 + spread) term
226: 		        per unit of removed liquidity R every time the position touched:
227: 		
228: 		              s_accountPremiumOwed += feeGrowthX128 * R * (1 + ν*R/N) / R
229: 		                                   += feeGrowthX128 * (T - R + ν*R)/N
230: 		                                   += feeGrowthX128 * T/N * (1 - R/T + ν*R/T)
231: 		         
232: 		        Note that the value of feeGrowthX128 can be extracted from the amount of fees collected by
233: 		        the smart contract since the amount of feesCollected is related to feeGrowthX128 according
234: 		        to:
235: 		
236: 		             feesCollected = feesGrowthX128 * (T-R)
237: 		
238: 		        So that we get:
239: 		             
240: 		             feesGrowthX128 = feesCollected/N
241: 		
242: 		        And the accumulator is computed from the amount of collected fees according to:
243: 		             
244: 		             s_accountPremiumOwed += feesCollected * T/N^2 * (1 - R/T + ν*R/T)          (Eqn 3)     
245: 		
246: 		        So, the amount of owed premia for a position of size r minted at time t1 and burnt at 
247: 		        time t2 is:
248: 		
249: 		             owedPremia(t1, t2) = (s_accountPremiumOwed_t2-s_accountPremiumOwed_t1) * r
250: 		                                = ∆feesGrowthX128 * r * T/N * (1 - R/T + ν*R/T)
251: 		                                = ∆feesGrowthX128 * r * (T - R + ν*R)/N
252: 		                                = ∆feesGrowthX128 * r * (N + ν*R)/N
253: 		                                = ∆feesGrowthX128 * r * (1 + ν*R/N)             (same as Eqn 1)
254: 		
255: 		        This way, the amount of premia owed for a position will match Eqn 1 exactly.
256: 		
257: 		        Similarly, the amount of gross fees for the total liquidity is tracked in a similar manner
258: 		        by the s_accountPremiumGross accumulator. 
259: 		
260: 		        However, since we require that Eqn 2 holds up-- ie. the gross fees collected should be equal
261: 		        to the net fees collected plus the ower fees plus the small spread, the expression for the
262: 		        s_accountPremiumGross accumulator has to be given by (you`ll see why in a minute): 
263: 		
264: 		            s_accountPremiumGross += feesCollected * T/N^2 * (1 - R/T + ν*R^2/T^2)       (Eqn 4) 
265: 		
266: 		        This expression can be used to calculate the fees collected by a position of size t between times
267: 		        t1 and t2 according to:
268: 		             
269: 		            grossPremia(t1, t2) = ∆(s_accountPremiumGross) * t
270: 		                                = ∆feeGrowthX128 * t * T/N * (1 - R/T + ν*R^2/T^2) 
271: 		                                = ∆feeGrowthX128 * t * (T - R + ν*R^2/T) / N 
272: 		                                = ∆feeGrowthX128 * t * (N + ν*R^2/T) / N
273: 		                                = ∆feeGrowthX128 * t * (1  + ν*R^2/(N*T))   (same as Eqn 2)
274: 		            
275: 		        where the last expression matches Eqn 2 exactly.
276: 		
277: 		        In summary, the s_accountPremium accumulators allow smart contracts that need to handle 
278: 		        long+short liquidity to guarantee that liquidity deposited always receives the correct
279: 		        premia, whether that liquidity has been removed from the AMM or not.
280: 		
281: 		        Note that the expression for the spread is extremely opinionated, and may not fit the
282: 		        specific risk management profile of every smart contract. And simply setting the ν parameter

// @audit feesbase
1098: 		        // round up the stored feesbase to minimize Δfeesbase when we next calculate it

// @audit postion
1107: 		    /// @notice caches/stores the accumulated premia values for the specified postion.

// @audit feegrowth
1160: 		        // (feegrowth * liquidity) / 2 ** 128

// @audit seperated
1338: 		        // premia, and is only seperated to simplify the calculation
```
[[108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L108), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L128), [130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L130), [216-282](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L216-L282), [1098](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1098), [1107](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1107), [1160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1160), [1338](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1338)]



```solidity
File: contracts/libraries/Errors.sol

// @audit exercisee
25: 		    /// @notice PanopticPool: force exercisee is insolvent - liquidatable accounts are not permitted to open or close positions outside of a liquidation

// @audit irst
31: 		    /// @notice PanopticFactory: irst 20 bytes of provided salt does not match caller address

// @audit avaiable
62: 		    /// @notice PanopticPool: there is not enough avaiable liquidity to buy an option
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L25), [31](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L31), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L62)]



```solidity
File: contracts/libraries/InteractionHelper.sol

// @audit metadada
96: 		        // not guaranteed that token supports metadada extension

// @audit metadada
109: 		        // not guaranteed that token supports metadada extension
```
[[96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L96), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L109)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit safecasting
19: 		    // Used for safecasting

// @audit tickspacing
25: 		    /// @notice masks 16-bit tickSpacing out of 64-bit [16-bit tickspacing][48-bit poolPattern] format poolId

// @audit addflag
104: 		            // increment the top 8 bit if addflag=true, decrement otherwise

// @audit blocktime
116: 		    /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.

// @audit blocktime
118: 		    /// @dev Thus, the minimum total time window is `cardinality` * `period` * `blocktime`.

// @audit twap
235: 		    /// @notice Computes the twap of a Uniswap V3 pool using data from its oracle.

// @audit stots
247: 		            // construct the time stots

// @audit consistentcy
663: 		                // evaluate at TWAP price to keep consistentcy with solvency calculations

// @audit liquidatee
691: 		            // negative premium (owed to the liquidatee) is credited to the collateral balance

// @audit liquidatee
701: 		            // note that "balance0" and "balance1" are the liquidatee's original balances before token delegation by a liquidator

// @audit liquidatee
705: 		                // liquidatee cannot pay back the liquidator fully in either token, so no protocol loss can be avoided

// @audit liquidatee
707: 		                    // liquidatee has insufficient token0 but some token1 left over, so we use what they have left to mitigate token0 losses

// @audit liquidatee
710: 		                    // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token1 balance: balance1 - paid1

// @audit liquidatee
711: 		                    // and paid0 - balance0 is the amount of token0 that the liquidatee is missing, i.e the protocol loss

// @audit liquidatee
725: 		                    // liquidatee has insufficient token1 but some token0 left over, so we use what they have left to mitigate token1 losses

// @audit liquidatee
728: 		                    // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token0 balance: balance0 - paid0

// @audit liquidatee
729: 		                    // and paid1 - balance1 is the amount of token1 that the liquidatee is missing, i.e the protocol loss

// @audit liquidatee
756: 		    /// @notice Haircut/clawback any premium paid by `liquidatee` on `positionIdList` over the protocol loss threshold during a liquidation.

// @audit liquidatee
760: 		    /// @param premiasByLeg The premium paid (or received) by the liquidatee for each leg of each position

// @audit liquidatee
779: 		            // get the amount of premium paid by the liquidatee

// @audit liquidatee
790: 		            // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token

// @audit commited
886: 		                        // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount

// @audit exercisee
911: 		    /// @param refunder Address of the user the refund is coming from (the force exercisee)

// @audit refundee
926: 		            // if the refunder lacks sufficient token0 to pay back the refundee, have them pay back the equivalent value in token1
```
[[19](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L19), [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L25), [104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L104), [116](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L116), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L118), [235](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L235), [247](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L247), [663](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L663), [691](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L691), [701](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L701), [705](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L705), [707](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L707), [710](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L710), [711](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L711), [725](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L725), [728](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L728), [729](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L729), [756](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L756), [760](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L760), [779](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L779), [790](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L790), [886](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L886), [911](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L911), [926](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L926)]



```solidity
File: contracts/multicall/Multicall.sol

// @audit paranthetical
22: 		                // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L22)]



```solidity
File: contracts/types/LeftRight.sol

// @audit safecasting
18: 		    // Used for safecasting

// @audit explictily
153: 		            // adding leftRight packed uint128's is same as just adding the values explictily

// @audit occured
159: 		            // then an overflow has occured

// @audit explictily
176: 		            // subtracting leftRight packed uint128's is same as just subtracting the values explictily

// @audit occured
182: 		            // then an underflow has occured
```
[[18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L18), [153](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L153), [159](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L159), [176](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L176), [182](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L182)]



```solidity
File: contracts/types/TokenId.sol

// @audit ith
525: 		                // now validate this ith leg in the position:

// @audit stranlges
565: 		                    // unlike short stranlges, long strangles also cannot be partnered, because there is no reduction in risk (both legs can earn premia simultaneously)

// @audit exercisability
576: 		    /// @param self The TokenId to validate for exercisability
```
[[525](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L525), [565](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L565), [576](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L576)]

</details>

---

### [N-71] Contracts should have full test coverage

A 100% test coverage is not foolproof, but it helps immensely in reducing the amount of bugs that may occur.



---

### [N-72] Large or complicated code bases should implement invariant tests

This includes: large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts.

Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold.

Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers may help significantly.



---

### [N-73] Codebase should implement formal verification testing

Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).



---

### [N-74] Inconsistent spacing in comments

Some lines use `// x` and some use `//x`. The instances below point out the usages that don't follow the majority, within each file.

*There are 105 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

23: 		//

27: 		//

32: 		//

34: 		//

420: 		        shares = previewDeposit(assets); //@audit-issue L zero shares

1021: 		                _mint(optionOwner, sharesToMint); //@audit-issue L - can mint zero

1078: 		                _mint(optionOwner, sharesToMint); //@audit-issue L - can mint zero

1118: 		            //compute total commission amount = commission rate + spread fee
```
[[23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L23), [27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L27), [32](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L32), [34](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L34), [420](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L420), [1021](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1021), [1078](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1078), [1118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1118)]



```solidity
File: contracts/PanopticFactory.sol

26: 		//@audit-ok
```
[[26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L26)]



```solidity
File: contracts/PanopticPool.sol

194: 		    //

199: 		    //

202: 		    //

205: 		    //

208: 		    //

211: 		    //

214: 		    //

217: 		    //

220: 		    //

223: 		    //

430: 		    function _calculateAccumulatedPremia( //@audit-info positive premia???

442: 		        for (uint256 k = 0; k < pLength; ) { //@audit H - uncapped positions -> unliquidable

449: 		                LeftRightSigned[4] memory premiaByLeg, //@audit-info positive premia

467: 		                        ) //@audit-info collision between two legs? (isLong or riskPartner)

481: 		                    portfolioPremium = portfolioPremium.add(premiaByLeg[leg]); //@audit-info adds it if is long or includePendingPremium = true

576: 		        _burnOptions(COMMIT_LONG_SETTLED, tokenId, msg.sender, tickLimitLow, tickLimitHigh); //@audit-issue M - why no update median?

915: 		        if (SLOW_ORACLE_UNISWAP_MODE) { //@audit-issue L dead code?

928: 		                s_miniMedian, //@audit-info does not update?

1040: 		            (premia, positionBalanceArray) = _calculateAccumulatedPremia( //@audit-info owed premia (positive??)

1220: 		            delegatedAmounts = delegatedAmounts.sub(positionPremia); //@audit seems false?

1222: 		        //@audit doesnt check twap?

1274: 		        _validateSolvency(account, positionIdListExercisee, NO_BUFFER); //@audit-ok checks also validity

1597: 		    ) external { //@audit-ok

1606: 		        LeftRightUnsigned accumulatedPremium; //@audit-info delta premium

1628: 		            s_options[owner][tokenId][legIndex] = accumulatedPremium; //@audit-ok can't be lower than before

1705: 		                //

1921: 		                    //
```
[[194](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L194), [199](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L199), [202](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L202), [205](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L205), [208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L208), [211](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L211), [214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L214), [217](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L217), [220](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L220), [223](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L223), [430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L430), [442](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L442), [449](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L449), [467](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L467), [481](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L481), [576](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L576), [915](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L915), [928](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L928), [1040](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1040), [1220](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1220), [1222](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1222), [1274](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1274), [1597](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1597), [1606](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1606), [1628](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1628), [1705](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1705), [1921](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1921)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

172: 		    ///

540: 		    function safeTransferFrom( //@audit-info new function

545: 		        bytes calldata data //@audit-issue L - allows zero address transfer?

546: 		    ) public override { //@audit-ok has callback on transfer

610: 		            //construct the positionKey for the from and to addresses

638: 		            //@audit-ok before: if (fromLiq.rightSlot() != liquidityChunk.liquidity()) revert Errors.TransferFailed();

639: 		            if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity()) //@audit-ok before it checked only the rightSlot

644: 		            //update+store liquidity and fee values between accounts

728: 		        if ((currentTick >= tickLimitHigh) || (currentTick <= tickLimitLow)) //@audit-issue L off by one

735: 		    ///

750: 		    ///

822: 		                //compute the swap amount, set as positive (exact input)

989: 		        LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache

1022: 		                    unchecked { //@audit recheck this as it's new

1032: 		                    unchecked { //@audit recheck this as it's new

1114: 		        LeftRightUnsigned collectedAmounts //@audit-ok was signed

1125: 		            .addCapped( //@audit-ok wasn't capped, but both were 256, they are unsigned now

1274: 		        ).subRect(s_accountFeesBase[positionKey]); //@audit-info used sub before

1308: 		                collected1 //@audit was signed but now is unsigned, bug?

1396: 		                        .toUint128Capped(); //@audit-info was uncapped before

1471: 		                LeftRightUnsigned amountToCollect; //@audit was signed

1484: 		                        _tickLower, //@audit-info was calculateAMMSwapFeesLiquidityChunk with unsigned chunk made with signed values
```
[[172](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L172), [540](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L540), [545](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L545), [546](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L546), [610](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L610), [638](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L638), [639](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L639), [644](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L644), [728](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L728), [735](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L735), [750](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L750), [822](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L822), [989](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L989), [1022](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1022), [1032](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1032), [1114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1114), [1125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1125), [1274](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1274), [1308](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1308), [1396](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1396), [1471](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1471), [1484](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1484)]



```solidity
File: contracts/libraries/CallbackLib.sol

12: 		//@audit-ok
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L12)]



```solidity
File: contracts/libraries/Constants.sol

7: 		//@audit-ok
```
[[7](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L7)]



```solidity
File: contracts/libraries/FeesCalc.sol

18: 		//

38: 		//
```
[[18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L18), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L38)]



```solidity
File: contracts/libraries/InteractionHelper.sol

17: 		//@audit-ok
```
[[17](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L17)]



```solidity
File: contracts/libraries/Math.sol

128: 		    function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) { //@audit-ok

241: 		    function getLiquidityForAmount0( //@audit-info price is new: https://github.com/Uniswap/v3-periphery/blob/main/contracts/libraries/LiquidityAmounts.sol#L23

372: 		            ///////////////////////////////////////////////

374: 		            ///////////////////////////////////////////////

486: 		            ///////////////////////////////////////////////

488: 		            ///////////////////////////////////////////////

549: 		            ///////////////////////////////////////////////

551: 		            ///////////////////////////////////////////////

626: 		            ///////////////////////////////////////////////

628: 		            ///////////////////////////////////////////////

703: 		            ///////////////////////////////////////////////

705: 		            ///////////////////////////////////////////////
```
[[128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L128), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L241), [372](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L372), [374](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L374), [486](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L486), [488](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L488), [549](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L549), [551](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L551), [626](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L626), [628](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L628), [703](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L703), [705](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L705)]



```solidity
File: contracts/libraries/PanopticMath.sol

44: 		    ///

72: 		    ///

266: 		            return int24(sortedTicks[10]); //@audit-issue L - median should be (sortedTicks[9] + sortedTicks[10]) / 2

299: 		        //

305: 		        //

309: 		        //

314: 		        //

319: 		        //

322: 		        //

323: 		        //

771: 		        LeftRightSigned[4][] memory premiasByLeg, //@audit pos or neg?
```
[[44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L44), [72](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L72), [266](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L266), [299](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L299), [305](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L305), [309](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L309), [314](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L314), [319](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L319), [322](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L322), [323](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L323), [771](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L771)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

11: 		//@audit-ok
```
[[11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L11)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

100: 		    ) public virtual { //@audit-issue L - can burn with transfer to 0 address

204: 		    } //@audit-issue L - no metadata uri
```
[[100](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L100), [204](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L204)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

9: 		//@audit-ok but no permit / EIP-2612
```
[[9](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L9)]



```solidity
File: contracts/types/LiquidityChunk.sol

12: 		///

15: 		//

29: 		//

33: 		//

43: 		//

45: 		//

49: 		//

51: 		//

52: 		//@audit-ok
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L12), [15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L15), [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L29), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L33), [43](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L43), [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L45), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L49), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L51), [52](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L52)]



```solidity
File: contracts/types/TokenId.sol

36: 		//

38: 		//

45: 		//

47: 		//

52: 		//

533: 		                ) revert Errors.InvalidTokenIdParameter(4); //@audit-info what if is > or < tick?
```
[[36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L36), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L38), [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L45), [47](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L47), [52](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L52), [533](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L533)]

</details>

---

### [N-75] State variables should include comments

Consider adding some comments on critical state variables to explain what they are supposed to do: this will help for future code reviews.

*There are 3 instances of this issue.*


```solidity
File: contracts/PanopticPool.sol

121: 		    bool internal constant DONOT_COMMIT_LONG_SETTLED = false;
```
[[121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L121)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

126: 		    bool internal constant BURN = true;

289: 		    mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;
```
[[126](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L126), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L289)]


---

### [N-76] Complex functions should have explicit comments

Large and/or complex functions should have more comments to better explain the purpose of each logic step.

*There are 24 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

650: 		    function exerciseCost(

1311: 		    function _getRequiredCollateralSingleLegNoPartner(

1510: 		    function _computeSpread(
```
[[650](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L650), [1311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1311), [1510](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1510)]



```solidity
File: contracts/PanopticFactory.sol

336: 		    function _mintFullRange(
```
[[336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L336)]



```solidity
File: contracts/PanopticPool.sol

1018: 		    function liquidate(

1180: 		    function forceExercise(

1509: 		    function _getPremia(

1593: 		    function settleLongPremium(

1672: 		    function _updateSettlementPostMint(

1839: 		    function _updateSettlementPostBurn(
```
[[1018](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1018), [1180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1180), [1509](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1509), [1593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1593), [1672](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1672), [1839](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1839)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

757: 		    function swapInAMM(

864: 		    function _createPositionInAMM(

959: 		    function _createLegInAMM(

1322: 		    function _getPremiaDeltas(

1450: 		    function getAccountPremium(
```
[[757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L757), [864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L864), [959](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L959), [1322](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1322), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1450)]



```solidity
File: contracts/libraries/FeesCalc.sol

130: 		    function _getAMMSwapFeesPerLiquidityCollected(
```
[[130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L130)]



```solidity
File: contracts/libraries/Math.sol

340: 		    function mulDiv(

458: 		    function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521: 		    function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

598: 		    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

675: 		    function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {
```
[[340](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L340), [458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L521), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L598), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L675)]



```solidity
File: contracts/libraries/PanopticMath.sol

651: 		    function getLiquidationBonus(

768: 		    function haircutPremia(
```
[[651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L768)]



```solidity
File: contracts/types/TokenId.sol

500: 		    function validate(TokenId self) internal pure {
```
[[500](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L500)]

</details>

---

### [N-77] Assembly code should have explicit comments

Low-level languages like assembly should require extensive documentation and comments to clarify the purpose of each instruction.

*There are 3 instances of this issue.*


```solidity
File: contracts/libraries/Math.sol

739: 		        assembly ("memory-safe") {
```
[[739](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L739)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

25: 		        assembly ("memory-safe") {

56: 		        assembly ("memory-safe") {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L25), [56](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L56)]


---

### [N-78] Use `@inheritdoc` for overridden functions

`@inheritdoc` Copies all missing tags from the base function. [Documentation](https://docs.soliditylang.org/en/latest/natspec-format.html#tags)

*There are 4 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

323: 		    function transfer(

341: 		    function transferFrom(
```
[[323](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

540: 		    function safeTransferFrom( //@audit-info new function

566: 		    function safeBatchTransferFrom(
```
[[540](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L540), [566](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L566)]


---

### [N-79] Modifier names don't follow the Solidity naming convention

Use mixedCase. Examples: `onlyBy, onlyAfter, onlyDuringThePreSale`. [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#modifier-names)

*There is 1 instance of this issue.*


```solidity
File: contracts/SemiFungiblePositionManager.sol

305: 		    modifier ReentrancyLock(uint64 poolId) {
```
[[305](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L305)]


---

### [N-80] Variable names don't follow the Solidity naming convention

Use `mixedCase` for local and state variables that are not constants, and add a trailing underscore for non-external variables. [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#local-and-state-variable-names)

*There are 52 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

// @audit s_underlyingToken
89: 		    address internal s_underlyingToken;

// @audit s_initialized
93: 		    bool internal s_initialized;

// @audit s_univ3token0
96: 		    address internal s_univ3token0;

// @audit s_univ3token1
99: 		    address internal s_univ3token1;

// @audit s_underlyingIsToken0
102: 		    bool internal s_underlyingIsToken0;

// @audit s_panopticPool
109: 		    PanopticPool internal s_panopticPool;

// @audit s_poolAssets
112: 		    uint128 internal s_poolAssets;

// @audit s_inAMM
115: 		    uint128 internal s_inAMM;

// @audit s_ITMSpreadFee
121: 		    uint128 internal s_ITMSpreadFee;

// @audit s_poolFee
124: 		    uint24 internal s_poolFee;

// @audit _ITMSpreadMultiplier
185: 		        uint256 _ITMSpreadMultiplier

// @audit min_sell_ratio
773: 		        uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;
```
[[89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L89), [93](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L93), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L109), [112](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L112), [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L115), [121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L121), [124](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L124), [185](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L185), [773](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L773)]



```solidity
File: contracts/PanopticFactory.sol

// @audit s_owner
97: 		    address internal s_owner;

// @audit s_initialized
100: 		    bool internal s_initialized;

// @audit s_getPanopticPool
103: 		    mapping(IUniswapV3Pool univ3pool => PanopticPool panopticPool) internal s_getPanopticPool;

// @audit _WETH9
117: 		        address _WETH9,

// @audit _SFPM
118: 		        SemiFungiblePositionManager _SFPM,
```
[[97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L97), [100](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L100), [103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L103), [117](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L117), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L118)]



```solidity
File: contracts/PanopticPool.sol

// @audit s_univ3pool
187: 		    IUniswapV3Pool internal s_univ3pool;

// @audit s_miniMedian
226: 		    uint256 internal s_miniMedian;

// @audit s_collateralToken0
232: 		    CollateralTracker internal s_collateralToken0;

// @audit s_collateralToken1
234: 		    CollateralTracker internal s_collateralToken1;

// @audit s_options
239: 		    mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))
240: 		        internal s_options;

// @audit s_grossPremiumLast
246: 		    mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

// @audit s_settledTokens
252: 		    mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;

// @audit s_positionBalance
259: 		    mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
260: 		        internal s_positionBalance;

// @audit s_positionsHash
273: 		    mapping(address account => uint256 positionsHash) internal s_positionsHash;

// @audit c_user
440: 		        address c_user = user;
```
[[187](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L187), [226](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L226), [232](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L232), [234](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L234), [239-240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L239-L240), [246](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L246), [252](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L252), [259-260](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L259-L260), [273](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L273), [440](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L440)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit s_AddrToPoolIdData
145: 		    mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;

// @audit s_poolContext
150: 		    mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;

// @audit s_accountLiquidity
177: 		    mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
178: 		        internal s_accountLiquidity;

// @audit s_accountPremiumOwed
287: 		    mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

// @audit s_accountPremiumGross
289: 		    mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

// @audit s_accountFeesBase
295: 		    mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;

// @audit positionKey_from
611: 		            bytes32 positionKey_from = keccak256(

// @audit positionKey_to
620: 		            bytes32 positionKey_to = keccak256(

// @audit premium0X64_base
1343: 		            uint256 premium0X64_base;

// @audit premium1X64_base
1344: 		            uint256 premium1X64_base;

// @audit premium0X64_owed
1364: 		                uint128 premium0X64_owed;

// @audit premium1X64_owed
1365: 		                uint128 premium1X64_owed;

// @audit premium0X64_gross
1385: 		                uint128 premium0X64_gross;

// @audit premium1X64_gross
1386: 		                uint128 premium1X64_gross;

// @audit UniswapV3Pool
1558: 		    ) external view returns (IUniswapV3Pool UniswapV3Pool) {
```
[[145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L145), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L150), [177-178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L177-L178), [287](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L287), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L289), [295](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L295), [611](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L611), [620](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L620), [1343](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1343), [1344](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1344), [1364](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1364), [1365](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1365), [1385](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1385), [1386](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1386), [1558](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1558)]



```solidity
File: contracts/libraries/PanopticMath.sol

// @audit timestamp_old
186: 		                    (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

// @audit tickCumulative_old
186: 		                    (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

// @audit timestamp_last
192: 		                    (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool

// @audit tickCumulative_last
192: 		                    (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool
```
[[186](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L186), [186](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L186), [192](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L192), [192](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L192)]



```solidity
File: contracts/types/LeftRight.sol

// @audit z_xR
285: 		        uint128 z_xR = (uint256(x.rightSlot()) + dx.rightSlot()).toUint128Capped();

// @audit z_xL
286: 		        uint128 z_xL = (uint256(x.leftSlot()) + dx.leftSlot()).toUint128Capped();

// @audit z_yR
287: 		        uint128 z_yR = (uint256(y.rightSlot()) + dy.rightSlot()).toUint128Capped();

// @audit z_yL
288: 		        uint128 z_yL = (uint256(y.leftSlot()) + dy.leftSlot()).toUint128Capped();

// @audit r_Enabled
290: 		        bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);

// @audit l_Enabled
291: 		        bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);
```
[[285](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L285), [286](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L286), [287](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L287), [288](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L288), [290](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L290), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L291)]

</details>

---

### [N-81] Missing underscore prefix for non-external functions

This convention is suggested for non-external functions (private or internal). [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

*There are 104 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/PanopticPool.sol

1456: 		    function getUniV3TWAP() internal view returns (int24 twapTick) {
```
[[1456](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1456)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

320: 		    function beginReentrancyLock(uint64 poolId) internal {

330: 		    function endReentrancyLock(uint64 poolId) internal {

593: 		    function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

757: 		    function swapInAMM(
```
[[320](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L320), [330](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L330), [593](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L593), [757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L757)]



```solidity
File: contracts/libraries/CallbackLib.sol

31: 		    function validateCallback(
```
[[31](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L31)]



```solidity
File: contracts/libraries/Math.sol

25: 		    function min24(int24 a, int24 b) internal pure returns (int24) {

33: 		    function max24(int24 a, int24 b) internal pure returns (int24) {

41: 		    function min(uint256 a, uint256 b) internal pure returns (uint256) {

49: 		    function min(int256 a, int256 b) internal pure returns (int256) {

57: 		    function max(uint256 a, uint256 b) internal pure returns (uint256) {

65: 		    function max(int256 a, int256 b) internal pure returns (int256) {

73: 		    function abs(int256 x) internal pure returns (int256) {

81: 		    function absUint(int256 x) internal pure returns (uint256) {

91: 		    function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {

128: 		    function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) { //@audit-ok

191: 		    function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

207: 		    function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

221: 		    function getAmountsForLiquidity(

241: 		    function getLiquidityForAmount0( //@audit-info price is new: https://github.com/Uniswap/v3-periphery/blob/main/contracts/libraries/LiquidityAmounts.sol#L23

271: 		    function getLiquidityForAmount1(

296: 		    function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

302: 		    function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311: 		    function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318: 		    function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

325: 		    function toInt256(uint256 toCast) internal pure returns (int256) {

340: 		    function mulDiv(

440: 		    function mulDivRoundingUp(

458: 		    function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521: 		    function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

584: 		    function mulDiv96RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

598: 		    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

661: 		    function mulDiv128RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

675: 		    function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

738: 		    function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

753: 		    function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {

776: 		    function sort(int256[] memory data) internal pure returns (int256[] memory) {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L33), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L41), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L57), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L65), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L73), [81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L81), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L91), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L128), [191](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L191), [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L207), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L221), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L241), [271](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L271), [296](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L296), [302](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L302), [311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L311), [318](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L318), [325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L325), [340](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L340), [440](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L440), [458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L521), [584](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L584), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L598), [661](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L661), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L675), [738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L738), [753](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L753), [776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L776)]



```solidity
File: contracts/libraries/PanopticMath.sol

47: 		    function getPoolId(address univ3pool) internal view returns (uint64) {

59: 		    function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

92: 		    function updatePositionsHash(

289: 		    function getLiquidityChunk(

338: 		    function getTicks(

371: 		    function getRangesFromStrike(

390: 		    function computeExercisedAmounts(

419: 		    function convertCollateralData(

445: 		    function convertCollateralData(

468: 		    function convertNotional(

490: 		    function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

507: 		    function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

524: 		    function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

547: 		    function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

574: 		    function getAmountsMoved(
```
[[47](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L47), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L59), [92](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L92), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L289), [338](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L338), [371](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L371), [390](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L390), [419](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L419), [445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L445), [468](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L468), [490](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L490), [507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L507), [524](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L524), [547](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L547), [574](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L574)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

22: 		    function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

53: 		    function safeTransfer(address token, address to, uint256 amount) internal {
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L22), [53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L53)]



```solidity
File: contracts/types/LeftRight.sol

39: 		    function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46: 		    function rightSlot(LeftRightSigned self) internal pure returns (int128) {

59: 		    function toRightSlot(

78: 		    function toRightSlot(

101: 		    function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108: 		    function leftSlot(LeftRightSigned self) internal pure returns (int128) {

121: 		    function toLeftSlot(

134: 		    function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

148: 		    function add(

171: 		    function sub(

194: 		    function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

214: 		    function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

232: 		    function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

251: 		    function subRect(

279: 		    function addCapped(
```
[[39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L39), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L46), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L59), [78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L78), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L101), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L108), [121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L121), [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L134), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L148), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L171), [194](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L194), [214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L232), [251](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L251), [279](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L279)]



```solidity
File: contracts/types/LiquidityChunk.sol

71: 		    function createChunk(

90: 		    function addLiquidity(

103: 		    function addTickLower(

119: 		    function addTickUpper(

136: 		    function updateTickLower(

152: 		    function updateTickUpper(

172: 		    function tickLower(LiquidityChunk self) internal pure returns (int24) {

181: 		    function tickUpper(LiquidityChunk self) internal pure returns (int24) {

190: 		    function liquidity(LiquidityChunk self) internal pure returns (uint128) {
```
[[71](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L71), [90](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L90), [103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L103), [119](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L119), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L136), [152](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L152), [172](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L172), [181](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L181), [190](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L190)]



```solidity
File: contracts/types/TokenId.sol

87: 		    function poolId(TokenId self) internal pure returns (uint64) {

96: 		    function tickSpacing(TokenId self) internal pure returns (int24) {

108: 		    function asset(TokenId self, uint256 legIndex) internal pure returns (uint256) {

118: 		    function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {

128: 		    function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {

138: 		    function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {

148: 		    function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {

158: 		    function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

169: 		    function width(TokenId self, uint256 legIndex) internal pure returns (int24) {

183: 		    function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193: 		    function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

205: 		    function addAsset(

221: 		    function addOptionRatio(

240: 		    function addIsLong(

255: 		    function addTokenType(

273: 		    function addRiskPartner(

291: 		    function addStrike(

310: 		    function addWidth(

336: 		    function addLeg(

366: 		    function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

404: 		    function countLongs(TokenId self) internal pure returns (uint256) {

416: 		    function asTicks(

432: 		    function countLegs(TokenId self) internal pure returns (uint256) {

464: 		    function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

500: 		    function validate(TokenId self) internal pure {

578: 		    function validateIsExercisable(TokenId self, int24 currentTick) internal pure {
```
[[87](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L87), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L96), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L108), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L118), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L128), [138](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L138), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L148), [158](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L158), [169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L169), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L183), [193](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L193), [205](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L205), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L221), [240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L240), [255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L255), [273](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L273), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L291), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L310), [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L336), [366](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L366), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L404), [416](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L416), [432](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L432), [464](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L464), [500](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L500), [578](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L578)]

</details>

---

### [N-82] Missing underscore prefix for non-external variables

This convention is suggested for non-external state variables (private or internal). [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

*There are 36 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

89: 		    address internal s_underlyingToken;

93: 		    bool internal s_initialized;

96: 		    address internal s_univ3token0;

99: 		    address internal s_univ3token1;

102: 		    bool internal s_underlyingIsToken0;

109: 		    PanopticPool internal s_panopticPool;

112: 		    uint128 internal s_poolAssets;

115: 		    uint128 internal s_inAMM;

121: 		    uint128 internal s_ITMSpreadFee;

124: 		    uint24 internal s_poolFee;
```
[[89](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L89), [93](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L93), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L96), [99](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L99), [102](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L102), [109](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L109), [112](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L112), [115](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L115), [121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L121), [124](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L124)]



```solidity
File: contracts/PanopticFactory.sol

64: 		    IUniswapV3Factory internal immutable UNIV3_FACTORY;

67: 		    SemiFungiblePositionManager internal immutable SFPM;

70: 		    IDonorNFT internal immutable DONOR_NFT;

73: 		    address internal immutable POOL_REFERENCE;

76: 		    address internal immutable COLLATERAL_REFERENCE;

79: 		    address internal immutable WETH;

97: 		    address internal s_owner;

100: 		    bool internal s_initialized;

103: 		    mapping(IUniswapV3Pool univ3pool => PanopticPool panopticPool) internal s_getPanopticPool;
```
[[64](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L64), [67](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L67), [70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L73), [76](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L76), [79](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L79), [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L97), [100](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L100), [103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L103)]



```solidity
File: contracts/PanopticPool.sol

180: 		    SemiFungiblePositionManager internal immutable SFPM;

187: 		    IUniswapV3Pool internal s_univ3pool;

226: 		    uint256 internal s_miniMedian;

232: 		    CollateralTracker internal s_collateralToken0;

234: 		    CollateralTracker internal s_collateralToken1;

239: 		    mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))
240: 		        internal s_options;

246: 		    mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

252: 		    mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;

259: 		    mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
260: 		        internal s_positionBalance;

273: 		    mapping(address account => uint256 positionsHash) internal s_positionsHash;
```
[[180](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L180), [187](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L187), [226](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L226), [232](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L232), [234](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L234), [239-240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L239-L240), [246](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L246), [252](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L252), [259-260](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L259-L260), [273](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L273)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

137: 		    IUniswapV3Factory internal immutable FACTORY;

145: 		    mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;

150: 		    mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;

177: 		    mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
178: 		        internal s_accountLiquidity;

287: 		    mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

289: 		    mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

295: 		    mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;
```
[[137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L137), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L145), [150](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L150), [177-178](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L177-L178), [287](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L287), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L289), [295](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L295)]

</details>

---

### [N-83] Invalid NatSpec comment style

NatSpec [must](https://docs.soliditylang.org/en/latest/natspec-format.html#documentation-example) begin with `///`, or use the `/* ... */` syntax.

*There are 3 instances of this issue.*


```solidity
File: contracts/SemiFungiblePositionManager.sol

358: 		        // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting

603: 		            // @dev see `contracts/types/LiquidityChunk.sol`

904: 		                // @dev see `contracts/types/LiquidityChunk.sol`
```
[[358](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L358), [603](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L603), [904](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L904)]


---

### [N-84] Missing NatSpec from contract declarations

Some contracts miss a `@dev/@notice` NatSpec, which should be a [best practice](https://docs.soliditylang.org/en/latest/natspec-format.html) to add as a documentation.

*There is 1 instance of this issue.*


```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: 		interface IDonorNFT {
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6)]


---

### [N-85] Missing NatSpec `@author` from contract declaration

Some contract definitions have an incomplete NatSpec: add a `@author` notation to improve the code documentation.

*There is 1 instance of this issue.*


```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: 		interface IDonorNFT {
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6)]


---

### [N-86] Missing NatSpec `@dev` from contract declaration

Some contract definitions have an incomplete NatSpec: add a `@dev` notation to describe the contract to improve the code documentation.

*There are 11 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

36: 		contract CollateralTracker is ERC20Minimal, Multicall {
```
[[36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L36)]



```solidity
File: contracts/PanopticFactory.sol

27: 		contract PanopticFactory is Multicall {
```
[[27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L27)]



```solidity
File: contracts/libraries/CallbackLib.sol

13: 		library CallbackLib {
```
[[13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L13)]



```solidity
File: contracts/libraries/Constants.sol

8: 		library Constants {
```
[[8](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L8)]



```solidity
File: contracts/libraries/Errors.sol

7: 		library Errors {
```
[[7](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L7)]



```solidity
File: contracts/libraries/Math.sol

13: 		library Math {
```
[[13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L13)]



```solidity
File: contracts/libraries/PanopticMath.sol

18: 		library PanopticMath {
```
[[18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L18)]



```solidity
File: contracts/types/LeftRight.sol

17: 		library LeftRightLibrary {
```
[[17](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L17)]



```solidity
File: contracts/types/LiquidityChunk.sol

53: 		library LiquidityChunkLibrary {
```
[[53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L53)]



```solidity
File: contracts/types/TokenId.sol

60: 		library TokenIdLibrary {
```
[[60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L60)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: 		interface IDonorNFT {
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6)]

</details>

---

### [N-87] Missing NatSpec `@notice` from contract declaration

Some contract definitions have an incomplete NatSpec: add a `@notice` notation to describe the contract to improve the code documentation.

*There are 5 instances of this issue.*


```solidity
File: contracts/libraries/PanopticMath.sol

18: 		library PanopticMath {
```
[[18](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L18)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

11: 		abstract contract ERC1155 {
```
[[11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L11)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

10: 		abstract contract ERC20Minimal {
```
[[10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L10)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: 		interface IDonorNFT {
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6)]



```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

11: 		interface IERC20Partial {
```
[[11](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L11)]


---

### [N-88] Missing NatSpec `@title` from contract declaration

Some contract definitions have an incomplete NatSpec: add a `@title` notation to describe the contract to improve the code documentation.

*There are 2 instances of this issue.*


```solidity
File: contracts/libraries/SafeTransferLib.sol

12: 		library SafeTransferLib {
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L12)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: 		interface IDonorNFT {
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6)]


---

### [N-89] Missing NatSpec `@dev` from error declaration

Some errors have an incomplete NatSpec: add a `@dev` notation to describe the error to improve the code documentation.

*There are 33 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/libraries/Errors.sol

13: 		    error CollateralTokenAlreadyInitialized();

16: 		    error DepositTooLarge();

20: 		    error EffectiveLiquidityAboveThreshold();

23: 		    error ExceedsMaximumRedemption();

26: 		    error ExerciseeNotSolvent();

29: 		    error InputListFail();

32: 		    error InvalidSalt();

35: 		    error InvalidTick();

38: 		    error InvalidNotionalValue();

42: 		    error InvalidTokenIdParameter(uint256 parameterType);

45: 		    error InvalidUniswapCallback();

48: 		    error LeftRightInputError();

51: 		    error NoLegsExercisable();

54: 		    error NotEnoughCollateral();

57: 		    error PositionTooLarge();

60: 		    error NotALongLeg();

63: 		    error NotEnoughLiquidity();

66: 		    error NotMarginCalled();

73: 		    error NotPanopticPool();

76: 		    error OptionsBalanceZero();

79: 		    error PoolAlreadyInitialized();

82: 		    error PositionAlreadyMinted();

85: 		    error PositionCountNotZero();

88: 		    error PriceBoundFail();

91: 		    error ReentrantCall();

95: 		    error StaleTWAP();

98: 		    error TooManyPositionsOpen();

101: 		    error TransferFailed();

105: 		    error TicksNotInitializable();

108: 		    error UnderOverFlow();

111: 		    error UniswapPoolNotInitialized();
```
[[13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L13), [16](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L16), [20](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L20), [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L26), [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L29), [32](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L32), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L35), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L38), [42](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L42), [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L45), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L48), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L51), [54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L54), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L57), [60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L60), [63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L66), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L73), [76](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L76), [79](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L79), [82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L82), [85](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L85), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L88), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L91), [95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L95), [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L98), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L105), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L108), [111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L111)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

55: 		    error NotAuthorized();

58: 		    error UnsafeRecipient();
```
[[55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L55), [58](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L58)]

</details>

---

### [N-90] Missing NatSpec `@param` from error declaration

Some errors have an incomplete NatSpec: add a `@param` notation to describe the error parameters to improve the code documentation.

*There are 34 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/libraries/Errors.sol

10: 		    error CastingError();

13: 		    error CollateralTokenAlreadyInitialized();

16: 		    error DepositTooLarge();

20: 		    error EffectiveLiquidityAboveThreshold();

23: 		    error ExceedsMaximumRedemption();

26: 		    error ExerciseeNotSolvent();

29: 		    error InputListFail();

32: 		    error InvalidSalt();

35: 		    error InvalidTick();

38: 		    error InvalidNotionalValue();

45: 		    error InvalidUniswapCallback();

48: 		    error LeftRightInputError();

51: 		    error NoLegsExercisable();

54: 		    error NotEnoughCollateral();

57: 		    error PositionTooLarge();

60: 		    error NotALongLeg();

63: 		    error NotEnoughLiquidity();

66: 		    error NotMarginCalled();

70: 		    error NotOwner();

73: 		    error NotPanopticPool();

76: 		    error OptionsBalanceZero();

79: 		    error PoolAlreadyInitialized();

82: 		    error PositionAlreadyMinted();

85: 		    error PositionCountNotZero();

88: 		    error PriceBoundFail();

91: 		    error ReentrantCall();

95: 		    error StaleTWAP();

98: 		    error TooManyPositionsOpen();

101: 		    error TransferFailed();

105: 		    error TicksNotInitializable();

108: 		    error UnderOverFlow();

111: 		    error UniswapPoolNotInitialized();
```
[[10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L10), [13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L13), [16](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L16), [20](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L20), [23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L23), [26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L26), [29](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L29), [32](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L32), [35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L35), [38](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L38), [45](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L45), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L48), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L51), [54](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L54), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L57), [60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L60), [63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L63), [66](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L66), [70](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L70), [73](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L73), [76](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L76), [79](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L79), [82](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L82), [85](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L85), [88](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L88), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L91), [95](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L95), [98](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L98), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L101), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L105), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L108), [111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Errors.sol#L111)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

55: 		    error NotAuthorized();

58: 		    error UnsafeRecipient();
```
[[55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L55), [58](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L58)]

</details>

---

### [N-91] Missing NatSpec `@dev` from event declaration

Some events have an incomplete NatSpec: add a `@dev` notation to describe the event to improve the code documentation.

*There are 11 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

49: 		    event Deposit(address indexed sender, address indexed owner, uint256 assets, uint256 shares);

57: 		    event Withdraw(
```
[[49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L57)]



```solidity
File: contracts/PanopticFactory.sol

35: 		    event OwnershipTransferred(address indexed oldOwner, address indexed newOwner);

44: 		    event PoolDeployed(
```
[[35](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L35), [44](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L44)]



```solidity
File: contracts/PanopticPool.sol

63: 		    event PremiumSettled(
```
[[63](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L63)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

80: 		    event PoolInitialized(address indexed uniswapPool, uint64 poolId);
```
[[80](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L80)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

22: 		    event TransferSingle(

36: 		    event TransferBatch(

48: 		    event ApprovalForAll(address indexed owner, address indexed operator, bool approved);
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L22), [36](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L36), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L48)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

19: 		    event Transfer(address indexed from, address indexed to, uint256 amount);

25: 		    event Approval(address indexed owner, address indexed spender, uint256 amount);
```
[[19](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L19), [25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L25)]

</details>

---

### [N-92] Missing NatSpec `@dev` from modifier declaration

Some modifiers have an incomplete NatSpec: add a `@dev` notation to describe the modifier to improve the code documentation.

*There is 1 instance of this issue.*


```solidity
File: contracts/CollateralTracker.sol

169: 		    modifier onlyPanopticPool() {
```
[[169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L169)]


---

### [N-93] Missing NatSpec `@param` from modifier declaration

Some modifiers have an incomplete NatSpec: add a `@param` notation to describe the modifier parameters to improve the code documentation.

*There is 1 instance of this issue.*


```solidity
File: contracts/CollateralTracker.sol

169: 		    modifier onlyPanopticPool() {
```
[[169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L169)]


---

### [N-94] Missing NatSpec `@dev` from function declaration

Some functions have an incomplete NatSpec: add a `@dev` notation to describe the function to improve the code documentation.

*There are 142 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

289: 		    function name() external view returns (string memory) {

303: 		    function symbol() external view returns (string memory) {

310: 		    function decimals() external view returns (uint8) {

361: 		    function asset() external view returns (address assetTokenAddress) {

379: 		    function convertToShares(uint256 assets) public view returns (uint256 shares) {

386: 		    function convertToAssets(uint256 shares) public view returns (uint256 assets) {

392: 		    function maxDeposit(address) external pure returns (uint256 maxAssets) {

399: 		    function previewDeposit(uint256 assets) public view returns (uint256 shares) {

444: 		    function maxMint(address) external view returns (uint256 maxShares) {

453: 		    function previewMint(uint256 shares) public view returns (uint256 assets) {

518: 		    function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

572: 		    function maxRedeem(address owner) public view returns (uint256 maxShares) {

581: 		    function previewRedeem(uint256 shares) public view returns (uint256 assets) {

591: 		    function redeem(

911: 		    function revoke(

995: 		    function takeCommissionAddData(

1096: 		    function _getExchangedAmount(

1245: 		    function _getRequiredCollateralAtTickSinglePosition(
```
[[289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L310), [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L361), [379](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L379), [386](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L386), [392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L392), [399](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L399), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L444), [453](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L453), [518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L518), [572](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L572), [581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L581), [591](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L591), [911](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L911), [995](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L995), [1096](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1096), [1245](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L1245)]



```solidity
File: contracts/PanopticFactory.sol

135: 		    function initialize(address _owner) public {

148: 		    function transferOwnership(address newOwner) external {

160: 		    function owner() external view returns (address) {

336: 		    function _mintFullRange(

421: 		    function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {
```
[[135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L135), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L148), [160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L160), [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L336), [421](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L421)]



```solidity
File: contracts/PanopticPool.sol

353: 		    function optionPositionBalance(

430: 		    function _calculateAccumulatedPremia( //@audit-info positive premia???

500: 		    function _getSlippageLimits(

523: 		    function pokeMedian() external {

548: 		    function mintOptions(

615: 		    function _mintOptions(

795: 		    function _burnAllOptionsFrom(

827: 		    function _burnOptions(

860: 		    function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

956: 		    function _burnAndHandleExercise(

1296: 		    function _checkSolvencyAtTick(

1345: 		    function _getSolvencyBalances(

1431: 		    function univ3pool() external view returns (IUniswapV3Pool) {

1437: 		    function collateralToken0() external view returns (CollateralTracker collateralToken) {

1443: 		    function collateralToken1() external view returns (CollateralTracker) {

1450: 		    function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

1456: 		    function getUniV3TWAP() internal view returns (int24 twapTick) {

1471: 		    function _checkLiquiditySpread(

1509: 		    function _getPremia(
```
[[353](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L353), [430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L430), [500](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L500), [523](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L523), [548](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L548), [615](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L615), [795](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L795), [827](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L827), [860](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L860), [956](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L956), [1296](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1296), [1345](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1345), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1437), [1443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1443), [1450](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1450), [1456](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1456), [1471](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1471), [1509](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1509)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

330: 		    function endReentrancyLock(uint64 poolId) internal {

504: 		    function mintTokenizedPosition(

681: 		    function _validateAndForwardToAMM(

757: 		    function swapInAMM(

1111: 		    function _updateStoredPremia(

1256: 		    function _collectAndWritePositionData(
```
[[330](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L330), [504](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L504), [681](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L681), [757](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L757), [1111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1111), [1256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1256)]



```solidity
File: contracts/libraries/CallbackLib.sol

31: 		    function validateCallback(
```
[[31](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/CallbackLib.sol#L31)]



```solidity
File: contracts/libraries/FeesCalc.sol

46: 		    function getPortfolioValue(
```
[[46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/FeesCalc.sol#L46)]



```solidity
File: contracts/libraries/InteractionHelper.sol

25: 		    function doApprovals(

92: 		    function computeSymbol(

108: 		    function computeDecimals(address token) external view returns (uint8) {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L25), [92](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L92), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/InteractionHelper.sol#L108)]



```solidity
File: contracts/libraries/Math.sol

25: 		    function min24(int24 a, int24 b) internal pure returns (int24) {

33: 		    function max24(int24 a, int24 b) internal pure returns (int24) {

41: 		    function min(uint256 a, uint256 b) internal pure returns (uint256) {

49: 		    function min(int256 a, int256 b) internal pure returns (int256) {

57: 		    function max(uint256 a, uint256 b) internal pure returns (uint256) {

65: 		    function max(int256 a, int256 b) internal pure returns (int256) {

91: 		    function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {

207: 		    function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

221: 		    function getAmountsForLiquidity(

296: 		    function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

302: 		    function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311: 		    function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318: 		    function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

325: 		    function toInt256(uint256 toCast) internal pure returns (int256) {

440: 		    function mulDivRoundingUp(

458: 		    function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521: 		    function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

584: 		    function mulDiv96RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

598: 		    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

661: 		    function mulDiv128RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

675: 		    function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

738: 		    function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

753: 		    function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {

776: 		    function sort(int256[] memory data) internal pure returns (int256[] memory) {
```
[[25](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L25), [33](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L33), [41](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L41), [49](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L49), [57](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L57), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L65), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L91), [207](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L207), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L221), [296](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L296), [302](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L302), [311](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L311), [318](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L318), [325](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L325), [440](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L440), [458](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L458), [521](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L521), [584](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L584), [598](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L598), [661](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L661), [675](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L675), [738](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L738), [753](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L753), [776](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L776)]



```solidity
File: contracts/libraries/PanopticMath.sol

59: 		    function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

75: 		    function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

289: 		    function getLiquidityChunk(

338: 		    function getTicks(

390: 		    function computeExercisedAmounts(

419: 		    function convertCollateralData(

445: 		    function convertCollateralData(

574: 		    function getAmountsMoved(

607: 		    function _calculateIOAmounts(

651: 		    function getLiquidationBonus(

917: 		    function getRefundAmounts(
```
[[59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L59), [75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L75), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L289), [338](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L338), [390](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L390), [419](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L419), [445](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L445), [574](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L574), [607](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L607), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L651), [917](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/PanopticMath.sol#L917)]



```solidity
File: contracts/libraries/SafeTransferLib.sol

22: 		    function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

53: 		    function safeTransfer(address token, address to, uint256 amount) internal {
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L22), [53](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/SafeTransferLib.sol#L53)]



```solidity
File: contracts/multicall/Multicall.sol

12: 		    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L12)]



```solidity
File: contracts/tokens/ERC1155Minimal.sol

81: 		    function setApprovalForAll(address operator, bool approved) public {

200: 		    function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

214: 		    function _mint(address to, uint256 id, uint256 amount) internal {

236: 		    function _burn(address from, uint256 id, uint256 amount) internal {
```
[[81](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L81), [200](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L200), [214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L214), [236](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC1155Minimal.sol#L236)]



```solidity
File: contracts/tokens/ERC20Minimal.sol

50: 		    function approve(address spender, uint256 amount) public returns (bool) {

62: 		    function transfer(address to, uint256 amount) public virtual returns (bool) {

104: 		    function _transferFrom(address from, address to, uint256 amount) internal {

123: 		    function _mint(address to, uint256 amount) internal {

137: 		    function _burn(address from, uint256 amount) internal {
```
[[50](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L50), [62](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L62), [104](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L104), [123](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L123), [137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/ERC20Minimal.sol#L137)]



```solidity
File: contracts/types/LeftRight.sol

39: 		    function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46: 		    function rightSlot(LeftRightSigned self) internal pure returns (int128) {

59: 		    function toRightSlot(

78: 		    function toRightSlot(

101: 		    function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108: 		    function leftSlot(LeftRightSigned self) internal pure returns (int128) {

121: 		    function toLeftSlot(

134: 		    function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

148: 		    function add(

171: 		    function sub(

194: 		    function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

214: 		    function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

232: 		    function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

251: 		    function subRect(
```
[[39](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L39), [46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L46), [59](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L59), [78](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L78), [101](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L101), [108](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L108), [121](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L121), [134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L134), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L148), [171](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L171), [194](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L194), [214](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L214), [232](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L232), [251](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LeftRight.sol#L251)]



```solidity
File: contracts/types/LiquidityChunk.sol

71: 		    function createChunk(

90: 		    function addLiquidity(

103: 		    function addTickLower(

119: 		    function addTickUpper(

136: 		    function updateTickLower(

152: 		    function updateTickUpper(

172: 		    function tickLower(LiquidityChunk self) internal pure returns (int24) {

181: 		    function tickUpper(LiquidityChunk self) internal pure returns (int24) {

190: 		    function liquidity(LiquidityChunk self) internal pure returns (uint128) {
```
[[71](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L71), [90](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L90), [103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L103), [119](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L119), [136](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L136), [152](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L152), [172](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L172), [181](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L181), [190](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/LiquidityChunk.sol#L190)]



```solidity
File: contracts/types/TokenId.sol

87: 		    function poolId(TokenId self) internal pure returns (uint64) {

96: 		    function tickSpacing(TokenId self) internal pure returns (int24) {

118: 		    function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {

128: 		    function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {

138: 		    function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {

148: 		    function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {

158: 		    function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

183: 		    function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193: 		    function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

221: 		    function addOptionRatio(

240: 		    function addIsLong(

255: 		    function addTokenType(

273: 		    function addRiskPartner(

291: 		    function addStrike(

310: 		    function addWidth(

336: 		    function addLeg(

404: 		    function countLongs(TokenId self) internal pure returns (uint256) {
```
[[87](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L87), [96](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L96), [118](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L118), [128](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L128), [138](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L138), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L148), [158](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L158), [183](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L183), [193](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L193), [221](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L221), [240](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L240), [255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L255), [273](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L273), [291](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L291), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L310), [336](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L336), [404](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/types/TokenId.sol#L404)]



```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

13: 		    function issueNFT(
```
[[13](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L13)]



```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

27: 		    function transfer(address to, uint256 amount) external;
```
[[27](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IERC20Partial.sol#L27)]

</details>

---

### [N-95] Missing NatSpec `@notice` from function declaration

Some functions have an incomplete NatSpec: add a `@notice` notation to describe the function to improve the code documentation.

*There are 3 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

323: 		    function transfer(

341: 		    function transferFrom(
```
[[323](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

681: 		    function _validateAndForwardToAMM(
```
[[681](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L681)]


---

### [N-96] Missing NatSpec `@param` from function declaration

Some functions have an incomplete NatSpec: add a `@param` notation to describe the function parameters to improve the code documentation.

*There are 19 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: contracts/CollateralTracker.sol

277: 		    function getPoolData()

289: 		    function name() external view returns (string memory) {

303: 		    function symbol() external view returns (string memory) {

310: 		    function decimals() external view returns (uint8) {

// @audit missing recipient, amount
323: 		    function transfer(

// @audit missing from, to, amount
341: 		    function transferFrom(

361: 		    function asset() external view returns (address assetTokenAddress) {

370: 		    function totalAssets() public view returns (uint256 totalManagedAssets) {

392: 		    function maxDeposit(address) external pure returns (uint256 maxAssets) {

444: 		    function maxMint(address) external view returns (uint256 maxShares) {

741: 		    function _poolUtilization() internal view returns (int256 poolUtilization) {
```
[[277](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L277), [289](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L289), [303](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L303), [310](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L310), [323](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341), [361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L370), [392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L444), [741](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L741)]



```solidity
File: contracts/PanopticFactory.sol

160: 		    function owner() external view returns (address) {
```
[[160](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L160)]



```solidity
File: contracts/PanopticPool.sol

// @audit missing atTick
430: 		    function _calculateAccumulatedPremia( //@audit-info positive premia???

523: 		    function pokeMedian() external {

1431: 		    function univ3pool() external view returns (IUniswapV3Pool) {

1437: 		    function collateralToken0() external view returns (CollateralTracker collateralToken) {

1443: 		    function collateralToken1() external view returns (CollateralTracker) {

1456: 		    function getUniV3TWAP() internal view returns (int24 twapTick) {
```
[[430](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L430), [523](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L523), [1431](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1431), [1437](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1437), [1443](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1443), [1456](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1456)]



```solidity
File: contracts/libraries/Math.sol

// @audit missing toDowncast
302: 		    function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {
```
[[302](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L302)]

</details>

---

### [N-97] Incomplete NatSpec `@return` from function declaration

Some functions have an incomplete NatSpec: add a `@return` notation to describe the function return value to improve the code documentation.

*There are 8 instances of this issue.*


```solidity
File: contracts/CollateralTracker.sol

323: 		    function transfer(

341: 		    function transferFrom(
```
[[323](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L323), [341](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L341)]



```solidity
File: contracts/PanopticPool.sol

795: 		    function _burnAllOptionsFrom(

956: 		    function _burnAndHandleExercise(

1296: 		    function _checkSolvencyAtTick(

1509: 		    function _getPremia(

1808: 		    function _getTotalLiquidity(
```
[[795](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L795), [956](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L956), [1296](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1296), [1509](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1509), [1808](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L1808)]



```solidity
File: contracts/SemiFungiblePositionManager.sol

1139: 		    function _getFeesBase(
```
[[1139](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L1139)]