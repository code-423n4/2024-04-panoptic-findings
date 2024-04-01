
### Comparison With Constant Will Always Be False or True
Comparisons against constant values that inherently result in always true or always false outcomes can lead to inefficiencies and obscure the contract's true logic. This issue spans from redundant gas consumption to critical functionality blocks, such as locking mechanisms that are permanently enabled or disabled. An example is a contract with a constant boolean state variable indicating a lock status (e.g., `bool constant public locked = true;`) and a condition that checks this variable (`require(!locked, "Transfers are locked");`). While sometimes these comparisons are intended for temporary conditions or placeholders during development, they can inadvertently become permanent, leading to misleading code or permanently disabled functionalities. Identifying and addressing these conditions is essential not only for gas optimization but also for ensuring the contract operates as intended and does not mislead developers or auditors about its capabilities.

```solidity
Path: ./contracts/PanopticPool.sol

877:        _updatePositionsHash(owner, tokenId, !ADD);	// @audit-issue
```
[877](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L877-L877), 


#### Recommendation

Conduct a thorough review of your Solidity contracts to identify any conditions that compare variables to constant values, resulting in outcomes that are predictably always true or always false. Assess the intent and impact of these conditions:
- For gas optimization, remove or simplify conditions that unnecessarily consume gas without affecting the contract's logic.

- For critical functionality, such as transfer locks, ensure that the use of constant conditions aligns with the intended contract behavior. If the condition is meant to be temporary or configurable, replace constant values with state variables that can be modified through the contract's functions, providing the flexibility required for the contract's operation.

For example, if a contract is intended to have a lock mechanism that can be toggled:

```solidity
bool public locked = true; // Change from constant to a state variable

function transferFrom(address from, address to, uint256 tokenId) public override {
    require(!locked, "Transfers are locked");
}

function toggleLock() public onlyOwner {
    locked = !locked; // Provide functionality to change lock status
}
```

### Using delegatecall inside a loop
When using the `delegatecall` opcode inside a loop, it's important to be aware that the same msg.value amount can be accredited multiple times. This can lead to unexpected behavior and potential security vulnerabilities in Solidity contracts.


```solidity
Path: ./contracts/multicall/Multicall.sol

14:        for (uint256 i = 0; i < data.length; ) {
15:            (bool success, bytes memory result) = address(this).delegatecall(data[i]);	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/multicall/Multicall.sol#L14-L15), 


#### Recommendation

Exercise caution when using 'delegatecall' within loops in Solidity. Ensure that the 'msg.value' is appropriately managed to prevent it from being erroneously accredited multiple times, which could lead to unexpected behavior and security vulnerabilities.


### Division before multiplication
When dealing with arithmetic operations, it's crucial to prioritize multiplication before division. This practice helps to reduce the risk of rounding errors and increases the precision of the calculations. By rearranging your mathematical operations to perform multiplications first, you can enhance the accuracy and efficiency of your contract's computational processes.

```solidity
Path: ./contracts/CollateralTracker.sol

202:                2230 +
203:                    (12500 * ratioTick) /
204:                    10_000 +
205:                    (7812 * ratioTick ** 2) /	// @audit-issue
206:                    10_000 ** 2 +
207:                    (6510 * ratioTick ** 3) /
208:                    10_000 ** 3
```
[205](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/CollateralTracker.sol#L202-L208), 


```solidity
Path: ./contracts/PanopticFactory.sol

392:            tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;	// @audit-issue
```
[392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticFactory.sol#L392-L392), 


```solidity
Path: ./contracts/SemiFungiblePositionManager.sol

1388:                    uint256 numerator = totalLiquidity ** 2 -
1389:                        totalLiquidity *
1390:                        removedLiquidity +
1391:                        ((removedLiquidity ** 2) / 2 ** (VEGOID));	// @audit-issue
```
[1391](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/SemiFungiblePositionManager.sol#L1388-L1391), 


```solidity
Path: ./contracts/libraries/PanopticMath.sol

346:            int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;	// @audit-issue

347:            int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;	// @audit-issue
```
[346](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L346-L346), [347](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L347-L347), 


#### Recommendation

Review your smart contract code to identify instances where division precedes multiplication. Refactor these calculations by rearranging the order, ensuring multiplication is performed first. This adjustment can significantly improve the precision of your results, especially in environments where every decimal point matters, like financial or token-related contracts.



### Do not allow fees to be set to `100%`
It is recommended from a risk perspective to disallow setting 100% fees at all. A reasonable fee maximum should be checked for instead.

```solidity
Path: ./contracts/CollateralTracker.sol

187:        COMMISSION_FEE = _commissionFee;	// @audit-issue
```
[187](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/CollateralTracker.sol#L187-L187), 


#### Recommendation

Implement strict validation checks in your smart contract's fee-setting functions to ensure that fees cannot be configured to 100%. Define a maximum allowable fee percentage that preserves the contract's functionality and user experience, such as 10% or 20%, depending on your project's specific requirements and economic model. For example:
```solidity
function setTransactionFee(uint256 newFeePercentage) public onlyOwner {
    require(newFeePercentage <= 20, "Fee cannot exceed 20%");
    transactionFee = newFeePercentage;
}
```


### `decimals()` is not a part of the `ERC-20` standard
The `decimals()` function is not a part of the [ERC-20](https://eips.ethereum.org/EIPS/eip-20) standard, and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid `ERC20` tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.


```solidity
Path: ./contracts/libraries/InteractionHelper.sol

110:        try IERC20Metadata(token).decimals() returns (uint8 _decimals) {	// @audit-issue
```
[110](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/InteractionHelper.sol#L110-L110), 


#### Recommendation

When working with ERC-20 tokens in your Solidity code, be aware that the `decimals()` function is not a part of the ERC-20 standard and is considered an optional extension. Not all valid ERC-20 tokens implement this interface, so avoid blindly casting all tokens to this interface and calling the `decimals()` function. Instead, check the token's documentation or contract to determine whether it supports this extension before using it.

### `symbol()` is not a part of the `ERC-20` standard
The `symbol()` function is not a part of the [ERC-20](https://eips.ethereum.org/EIPS/eip-20) standard, and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid `ERC20` tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.


```solidity
Path: ./contracts/libraries/InteractionHelper.sol

60:        try IERC20Metadata(token0).symbol() returns (string memory _symbol) {	// @audit-issue

65:        try IERC20Metadata(token1).symbol() returns (string memory _symbol) {	// @audit-issue

97:        try IERC20Metadata(token).symbol() returns (string memory tokenSymbol) {	// @audit-issue
```
[60](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/InteractionHelper.sol#L60-L60), [65](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/InteractionHelper.sol#L65-L65), [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/InteractionHelper.sol#L97-L97), 


#### Recommendation

When working with ERC-20 tokens in your Solidity code, be aware that the `symbol()` function is not a part of the ERC-20 standard and is considered an optional extension. Not all valid ERC-20 tokens implement this interface, so avoid blindly casting all tokens to this interface and calling the `symbol()` function. Instead, check the token's documentation or contract to determine whether it supports this extension before using it.


### Initializers can be front-run
Initializers could be front-run, allowing an attacker to either set their own values, take ownership of the contract, and in the best case forcing a re-deployment.


```solidity
Path: ./contracts/PanopticFactory.sol

134:    function initialize(address _owner) public {	// @audit-issue
```
[134](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticFactory.sol#L134-L134), 


#### Recommendation

To mitigate the risk of initializers being front-run, ensure that they are only callable by a trusted entity, such as the deployer, or through a secure, multi-step initialization process. One approach is to use a constructor for initial setup, which is inherently protected against front-running. If a separate initializer is necessary, consider using a modifier that restricts the initializer function to be called only once by a predefined address, typically the deployer's address. Additionally, implement robust checks within the initializer to validate inputs and reject suspicious or unauthorized initialization attempts.



### Missing Reentrancy Modifier
A reentrancy attack is a common vulnerability in smart contracts, particularly when a contract makes an external call to another untrusted contract and then continues to execute code afterwards. If the called contract is malicious, it can call back into the original contract in a way that causes the original function to run again, potentially leading to effects like multiple withdrawals and other unintended actions.

The absence of reentrancy guards, such as the `nonReentrant` modifier provided by OpenZeppelin's ReentrancyGuard contract, makes a function susceptible to reentrancy attacks. This modifier prevents a function from being called again until it has finished executing.

```solidity
Path: ./contracts/multicall/Multicall.sol

15:            (bool success, bytes memory result) = address(this).delegatecall(data[i]);	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/multicall/Multicall.sol#L15-L15), 


#### Recommendation

Consider adding `nonReentrant` modifier to given functions.


### Library function isn't `internal` or `private`
In a library, using an external or public visibility means that we won't be going through the library with a DELEGATECALL but with a CALL. This changes the context and should be done carefully.

```solidity
Path: ./contracts/libraries/InteractionHelper.sol

24:    function doApprovals(	// @audit-issue

48:    function computeName(	// @audit-issue

91:    function computeSymbol(	// @audit-issue

107:    function computeDecimals(address token) external view returns (uint8) {	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/InteractionHelper.sol#L24-L24), [48](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/InteractionHelper.sol#L48-L48), [91](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/InteractionHelper.sol#L91-L91), [107](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/InteractionHelper.sol#L107-L107), 


```solidity
Path: ./contracts/libraries/PanopticMath.sol

75:    function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {	// @audit-issue

125:    function computeMedianObservedPrice(	// @audit-issue

168:    function computeInternalMedian(	// @audit-issue

241:    function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {	// @audit-issue

651:    function getLiquidationBonus(	// @audit-issue

768:    function haircutPremia(	// @audit-issue

917:    function getRefundAmounts(	// @audit-issue
```
[75](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L75-L75), [125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L125-L125), [168](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L168-L168), [241](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L241-L241), [651](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L651-L651), [768](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L768-L768), [917](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L917-L917), 


```solidity
Path: ./contracts/libraries/FeesCalc.sol

46:    function getPortfolioValue(	// @audit-issue

97:    function calculateAMMSwapFees(	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/FeesCalc.sol#L46-L46), [97](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/FeesCalc.sol#L97-L97), 


#### Recommendation

Carefully assess the intended use of functions within your libraries and opt for `internal` or `private` visibility unless there's a specific reason to expose them via `external` or `public`. This practice encourages the use of `DELEGATECALL` where appropriate, maintaining the execution context of the calling contract and ensuring consistent access to storage variables.


### Unneeded initializations of bool variable to `false`.
In Solidity, it is common practice to initialize variables with default values when declaring them. However, initializing `bool`variables to `false` when they are not subsequently used in the code can lead to unnecessary gas consumption and code clutter. This issue points out instances where such initializations are present but serve no functional purpose.

```solidity
Path: ./contracts/SemiFungiblePositionManager.sol

125:    bool internal constant MINT = false;	// @audit-issue
```
[125](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/SemiFungiblePositionManager.sol#L125-L125), 


```solidity
Path: ./contracts/PanopticPool.sol

111:    bool internal constant COMPUTE_LONG_PREMIA = false;	// @audit-issue

114:    bool internal constant ONLY_AVAILABLE_PREMIUM = false;	// @audit-issue

120:    bool internal constant DONOT_COMMIT_LONG_SETTLED = false;	// @audit-issue

133:    bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;	// @audit-issue
```
[111](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L111-L111), [114](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L114-L114), [120](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L120-L120), [133](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L133-L133), 


#### Recommendation


It is recommended not to initialize boolean variables to `false` to save some Gas.


### Unneeded initializations of integer variable to `0`.
In Solidity, it is common practice to initialize variables with default values when declaring them. However, initializing integer variables to `0` when they are not subsequently used in the code can lead to unnecessary gas consumption and code clutter. This issue points out instances where such initializations are present but serve no functional purpose.

```solidity
Path: ./contracts/CollateralTracker.sol

662:            for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {	// @audit-issue

1208:        for (uint256 i = 0; i < totalIterations; ) {	// @audit-issue

1255:            for (uint256 index = 0; index < numLegs; ++index) {	// @audit-issue
```
[662](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/CollateralTracker.sol#L662-L662), [1208](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/CollateralTracker.sol#L1208-L1208), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/CollateralTracker.sol#L1255-L1255), 


```solidity
Path: ./contracts/SemiFungiblePositionManager.sol

575:        for (uint256 i = 0; i < ids.length; ) {	// @audit-issue

601:        for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue

882:        for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue
```
[575](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/SemiFungiblePositionManager.sol#L575-L575), [601](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/SemiFungiblePositionManager.sol#L601-L601), [882](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/SemiFungiblePositionManager.sol#L882-L882), 


```solidity
Path: ./contracts/PanopticPool.sol

459:            for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue

441:        for (uint256 k = 0; k < pLength; ) {	// @audit-issue

745:        for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue

802:        for (uint256 i = 0; i < positionIdList.length; ) {	// @audit-issue

864:        for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue

1382:        for (uint256 i = 0; i < pLength; ) {	// @audit-issue

1518:        for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue

1672:        for (uint256 leg = 0; leg < numLegs; ++leg) {	// @audit-issue

1852:        for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue
```
[459](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L459-L459), [441](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L441-L441), [745](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L745-L745), [802](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L802-L802), [864](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L864-L864), [1382](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L1382-L1382), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L1518-L1518), [1672](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L1672-L1672), [1852](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/PanopticPool.sol#L1852-L1852), 


```solidity
Path: ./contracts/types/TokenId.sol

507:            for (uint256 i = 0; i < 4; ++i) {	// @audit-issue

581:            for (uint256 i = 0; i < numLegs; ++i) {	// @audit-issue
```
[507](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/types/TokenId.sol#L507-L507), [581](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/types/TokenId.sol#L581-L581), 


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

137:            for (uint256 i = 0; i < cardinality + 1; ++i) {	// @audit-issue

148:            for (uint256 i = 0; i < cardinality; ++i) {	// @audit-issue

248:            for (uint256 i = 0; i < 20; ++i) {	// @audit-issue

256:            for (uint256 i = 0; i < 19; ++i) {	// @audit-issue

395:        for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue

784:                for (uint256 leg = 0; leg < numLegs; ++leg) {	// @audit-issue

781:            for (uint256 i = 0; i < positionIdList.length; ++i) {	// @audit-issue

863:                for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {	// @audit-issue

860:            for (uint256 i = 0; i < positionIdList.length; i++) {	// @audit-issue
```
[137](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L137-L137), [148](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L148-L148), [248](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L248-L248), [256](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L256-L256), [395](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L395-L395), [784](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L784-L784), [781](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L781-L781), [863](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L863-L863), [860](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/PanopticMath.sol#L860-L860), 


```solidity
Path: ./contracts/libraries/FeesCalc.sol

55:            for (uint256 leg = 0; leg < numLegs; ) {	// @audit-issue

51:        for (uint256 k = 0; k < positionIdList.length; ) {	// @audit-issue
```
[55](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/FeesCalc.sol#L55-L55), [51](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/libraries/FeesCalc.sol#L51-L51), 


#### Recommendation


It is recommended not to initialize integer variables to `0` to save some Gas.


### Use transfer libraries instead of low level calls
Consider using `SafeTransferLib.safeTransferETH` or `Address.sendValue` for clearer semantic meaning instead of using a low level call.

```solidity
Path: ./contracts/multicall/Multicall.sol

15:            (bool success, bytes memory result) = address(this).delegatecall(data[i]);	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/multicall/Multicall.sol#L15-L15), 


#### Recommendation

To improve code readability and safety, consider using higher-level transfer libraries like `SafeTransferLib.safeTransferETH` or `Address.sendValue` instead of low-level calls for handling Ether transfers. These libraries provide clearer semantic meaning and help prevent common pitfalls associated with low-level calls.

### Unused arguments should be removed or implemented
In Solidity, functions often have arguments that are intended for specific operations or logic within the function. However, sometimes these arguments remain unused in the function body, either due to changes during development or oversight. Unused arguments in functions can lead to confusion, making the code less readable and potentially misleading for other developers who might use or audit the contract. Moreover, they can create a false impression of the function's purpose and behavior. It's crucial to either implement these arguments in the function's logic as originally intended or remove them to ensure clarity and efficiency of the code.

```solidity
Path: ./contracts/CollateralTracker.sol

392:    function maxDeposit(address) external pure returns (uint256 maxAssets) {	// @audit-issue: None

444:    function maxMint(address) external view returns (uint256 maxShares) {	// @audit-issue: None
```
[392](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/CollateralTracker.sol#L392-L392), [444](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/CollateralTracker.sol#L444-L444), 


#### Recommendation

Eliminate unused arguments in Solidity function definitions to enhance code clarity and efficiency. If an argument is currently not utilized in the function's logic, assess its potential future utility. If it serves no purpose, removing it simplifies the function signature and aligns the code more closely with its actual operation, contributing to a cleaner and more understandable contract structure.

### Unused import
The identifier is imported but never used within the file.

```solidity
Path: ./contracts/types/LiquidityChunk.sol

5:import {TokenId} from "@types/TokenId.sol";	// @audit-issue: TokenId not used in the contract.
```
[5](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/./contracts/types/LiquidityChunk.sol#L5-L5), 


#### Recommendation

Regularly review your Solidity code to remove unused imports. This practice declutters the codebase, making it easier to understand and maintain. In addition, consider using tools or IDE features that can automatically detect and highlight unused imports for cleanup. Keeping imports limited to only what is necessary helps maintain a clear understanding of the contract's dependencies and reduces potential confusion for developers working on or reviewing the code.