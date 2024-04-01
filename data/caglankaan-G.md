
### Excessive Gas Consumption Due to Nested Loops in Solidity
In the Solidity smart contract, there are instances where for-loops are nested within other for-loops. Nested loops in Solidity can lead to significantly increased gas consumption, especially when operating on large data sets. This is because the complexity of nested loops is multiplicative; a double nested loop results in \(O(n^2)\) complexity, and a triple nested loop leads to \(O(n^3)\) complexity. In the context of Ethereum, where each operation consumes a certain amount of gas, such complexity can make transactions prohibitively expensive and may even hit the block gas limit, causing transactions to fail.

```solidity
Path: ./contracts/PanopticPool.sol

459:            for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue: This for is under another for loop on line 441
```
[459](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L459-L459), 


```solidity
Path: ./contracts/types/TokenId.sol

520:                for (uint256 j = i + 1; j < numLegs; ++j) {	// @audit-issue: This for is under another for loop on line 507
```
[520](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/types/TokenId.sol#L520-L520), 


```solidity
Path: ./contracts/libraries/PanopticMath.sol

784:                for (uint256 leg = 0; leg < numLegs; ++leg) {	// @audit-issue: This for is under another for loop on line 781

863:                for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {	// @audit-issue: This for is under another for loop on line 860
```
[784](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L784-L784), [863](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L863-L863), 


```solidity
Path: ./contracts/libraries/FeesCalc.sol

55:            for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue: This for is under another for loop on line 51
```
[55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/FeesCalc.sol#L55-L55), 


#### Recommendation


1. **Optimize Data Structures**: Where possible, use more efficient data structures that can reduce the need for nested iterations. This might involve restructuring how data is stored and accessed.
2. **Limit Loop Operations**: Implement checks or mechanisms to limit the number of iterations in each loop. For instance, setting a hard cap on array sizes or breaking out of loops early when a certain condition is met.


### Cache Local Variable Array Length In For Loop
If not cached, the solidity compiler will always read the length of the array during each iteration. If it is a memory array, this is an extra mload operation (3 additional gas for each iteration except for the first).

```solidity
Path: ./contracts/SemiFungiblePositionManager.sol

575:        for (uint256 i = 0; i < ids.length; ) {	// @audit-issue
```
[575](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/SemiFungiblePositionManager.sol#L575-L575), 


```solidity
Path: ./contracts/PanopticPool.sol

802:        for (uint256 i = 0; i < positionIdList.length; ) {	// @audit-issue
```
[802](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L802-L802), 


```solidity
Path: ./contracts/multicall/Multicall.sol

14:        for (uint256 i = 0; i < data.length; ) {	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/multicall/Multicall.sol#L14-L14), 


```solidity
Path: ./contracts/tokens/ERC1155Minimal.sol

143:        for (uint256 i = 0; i < ids.length; ) {	// @audit-issue

187:            for (uint256 i = 0; i < owners.length; ++i) {	// @audit-issue
```
[143](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/tokens/ERC1155Minimal.sol#L143-L143), [187](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/tokens/ERC1155Minimal.sol#L187-L187), 


```solidity
Path: ./contracts/libraries/PanopticMath.sol

781:            for (uint256 i = 0; i < positionIdList.length; ++i) {	// @audit-issue

860:            for (uint256 i = 0; i < positionIdList.length; i++) {	// @audit-issue
```
[781](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L781-L781), [860](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L860-L860), 


```solidity
Path: ./contracts/libraries/FeesCalc.sol

51:        for (uint256 k = 0; k < positionIdList.length; ) {	// @audit-issue
```
[51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/FeesCalc.sol#L51-L51), 


#### Recommendation

To optimize gas consumption, cache the length of memory arrays before for loop iterations in Solidity. This reduces redundant mload operations, saving 3 gas per iteration after the first and improving overall contract efficiency.


### Do not cache constants to save gas
In Solidity, constants are a gas-efficient way to store values that don't change. They are replaced directly in the bytecode at compile-time, meaning that using a constant incurs no gas cost for reading from storage. However, some developers might cache these constants into local variables, thinking it will save gas. This practice is unnecessary and can actually increase gas consumption due to the additional storage operations for the local variables. Understanding how constants are implemented and accessed is crucial for writing gas-efficient Solidity code.

```solidity
Path: ./contracts/CollateralTracker.sol

773:        uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;	// @audit-issue: Variable `SELLER_COLLATERAL_RATIO` is defined as `immutable` in contract `CollateralTracker` on line `141`
```
[773](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/CollateralTracker.sol#L773-L773), 


#### Recommendation

Refrain from caching constant variables into local variables in your Solidity contracts. Trust the compile-time optimization of constants for gas-efficient access. By avoiding unnecessary caching, you reduce the gas cost associated with additional storage operations and maintain the inherent efficiency of using constants. Regularly review your code to ensure that constants are used directly and not redundantly cached in local variables.

### Shortcircuit rules can be be used to optimize some gas usage
Some conditions may be reordered to save an SLOAD (2100 gas), as we avoid reading state variables when the first part of the condition fails (with `&&`), or succeeds (with `||`).

```solidity
Path: ./contracts/PanopticPool.sol

460:                if (tokenId.isLong(leg) == 0 && !includePendingPremium) {	// @audit-issue: Control with `isLong` can be done after all non state variable/function call controls.

1596:        if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();	// @audit-issue: Control with `isLong` can be done after all non state variable/function call controls.
```
[460](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L460-L460), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L1596-L1596), 


#### Recommendation

Review your Solidity contracts for conditional statements that use `&&` and `||` operators. Prioritize conditions that are less gas-intensive or have a higher likelihood of determining the outcome of the entire expression. For instance, if a condition involves an `SLOAD` operation and another is a simple variable comparison, evaluate the simpler condition first:
Before optimization:
```solidity
if (contractStateVariable > value && isEligible(msg.sender)) {
    // Execution logic
}

After optimization:
```solidity
if (isEligible(msg.sender) && contractStateVariable > value) {
    // Execution logic
}

This rearrangement ensures that if `isEligible(msg.sender)` returns false, the contract avoids the gas cost associated with reading `contractStateVariable` from storage. Apply this principle across your contract's logic where applicable, especially in functions called frequently or in gas-sensitive contexts. Testing remains crucial; ensure that the reordering of conditions does not alter the intended logic or outcomes of your contract.


### It is a waste of GAS to emit variable literals
Emitting variable literals (true, false, address(0), 1 etc...) in events is inefficient, as it consumes extra gas without providing added value. These literals are fixed values that can be accessed or hardcoded elsewhere in the smart contract or application, making their inclusion in events redundant and an unnecessary drain on resources during transaction execution.

```solidity
Path: ./contracts/tokens/ERC1155Minimal.sol

220:        emit TransferSingle(msg.sender, address(0), to, id, amount);	// @audit-issue

239:        emit TransferSingle(msg.sender, from, address(0), id, amount);	// @audit-issue
```
[220](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/tokens/ERC1155Minimal.sol#L220-L220), [239](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/tokens/ERC1155Minimal.sol#L239-L239), 


```solidity
Path: ./contracts/tokens/ERC20Minimal.sol

130:        emit Transfer(address(0), to, amount);	// @audit-issue

145:        emit Transfer(from, address(0), amount);	// @audit-issue
```
[130](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/tokens/ERC20Minimal.sol#L130-L130), [145](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/tokens/ERC20Minimal.sol#L145-L145), 


#### Recommendation

Refrain from including fixed variable literals as parameters in your Solidity contract events. Evaluate your event emissions and remove literals that do not provide dynamic information about contract state or actions. For instance, instead of emitting an event with a `true` literal to indicate success, consider naming the event in a way that inherently indicates success or failure, such as `ActionSuccessful()`:
```solidity
// Before optimization
event ActionTaken(bool success);

// After optimization
event ActionSuccessful();
event ActionFailed();
```


### Unused State Variables
There are state variables which are declared but not used in any function. This might increase the contract's gas usage unnecessarily.

```solidity
Path: ./contracts/libraries/PanopticMath.sol

23:    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L23-L23), 


```solidity
Path: ./contracts/libraries/Math.sol

15:    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/Math.sol#L15-L15), 


#### Recommendation

To optimize your contract's gas usage, remove any state variables that are declared but not used in any function. Unnecessary state variables can increase gas costs and should be eliminated during code review.

### Unused `error` definition
Note that there may be cases where an error superficially appears to be used, but this is only because there are multiple definitions of the error in different files. In such cases, the error definition should be moved into a separate file. The instances below are the unused definitions.


```solidity
Path: ./contracts/libraries/Errors.sol

26:    error ExerciseeNotSolvent();	// @audit-issue

48:    error LeftRightInputError();	// @audit-issue
```
[26](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/Errors.sol#L26-L26), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/Errors.sol#L48-L48), 


#### Recommendation

Unused `error` definitions should be removed from the contract, and if needed, consolidated into a separate file to avoid duplication.


### Increments can be `unchecked` in for-loops
Newer versions of the Solidity compiler will check for integer overflows and underflows automatically. This provides safety but increases gas costs.
When an unsigned integer is guaranteed to never overflow, the unchecked feature of Solidity can be used to save gas costs.A common case for this is for-loops using a strictly-less-than comparision in their conditional statement.

```solidity
Path: ./contracts/PanopticPool.sol

1672:        for (uint256 leg = 0; leg < numLegs; ++leg) {	// @audit-issue
```
[1672](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L1672-L1672), 


#### Recommendation

Use unchecked math to block overflow / underflow check to save Gas.

### Divisions can be unchecked to save gas
The expression type(int).min/(-1) is the only case where division causes an overflow. Therefore, uncheck can be used to save gas in scenarios where it is certain that such an overflow will not occur.

```solidity
Path: ./contracts/libraries/PanopticMath.sol

376:            (width * tickSpacing) / 2,	// @audit-issue
```
[376](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L376-L376), 


#### Recommendation

Utilize 'unchecked' blocks in Solidity for divisions where overflow is impossible, such as when 'type(int).min/(-1)' is not a concern. This can save gas by bypassing overflow checks in these specific cases.


### Do not calculate constants
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

```solidity
Path: ./contracts/PanopticPool.sol

103:    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;	// @audit-issue

105:    int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;	// @audit-issue

165:    uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);	// @audit-issue
```
[103](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L103-L103), [105](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L105-L105), [165](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L165-L165), 


```solidity
Path: ./contracts/libraries/PanopticMath.sol

23:    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L23-L23), 


```solidity
Path: ./contracts/libraries/Math.sol

15:    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/Math.sol#L15-L15), 


#### Recommendation

Precompute and assign literal values to constant variables in your Solidity contracts. Avoid defining constants with expressions or calculations. By providing direct values, you ensure that the compiler replaces these constants efficiently in the bytecode, maximizing gas savings and contract performance. Review your contracts to identify any constants defined with expressions and refactor them to use precomputed literal values instead.
