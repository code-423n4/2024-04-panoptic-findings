## Gas Optimizations


| |Issue|Instances|Gas Saved
|-|:-|:-:|:-:|
| [GAS-01](#GAS-01) | `abi.encode()` is less efficient than `abi.encodepacked()` for non-address arguments | 4 | - |
| [GAS-02](#GAS-02) | Argument validation should be at the top of the function/block | 91 | - |
| [GAS-03](#GAS-03) | Use `Array.unsafeAccess()` to avoid repeated array length checks | 8 | 16800 |
| [GAS-04](#GAS-04) | Avoid updating storage when the value hasn't changed | 1 | 800 |
| [GAS-05](#GAS-05) | Avoid zero transfer to save gas | 5 | 500 |
| [GAS-06](#GAS-06) | Use `calldata` instead of `memory` for immutable arguments(Not captured by 4nalyzer) | 7 | 4200 |
| [GAS-07](#GAS-07) | Constructors can be marked as `payable` to save deployment gas | 4 | 84 |
| [GAS-08](#GAS-08) | Division by powers of two should use bit shifting | 9 | 180 |
| [GAS-09](#GAS-09) | Stack variable used as a cheaper cache for a state variable is only used once(Not captured by 4nalyzer) | 1 | 3 |
| [GAS-10](#GAS-10) | Do not calculate constants | 5 | - |
| [GAS-11](#GAS-11) | `do-while` is cheaper than `for`-loops when the initial check can be skipped | 32 | - |
| [GAS-12](#GAS-12) | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function to save deployment gas | 3 | - |
| [GAS-13](#GAS-13) | Counting down in `for` statements is more gas efficient | 33 | 264 |
| [GAS-14](#GAS-14) | Function names can be optimized | 20 | 2560 |
| [GAS-15](#GAS-15) | Don't initialize variables with default value | 31 | - |
| [GAS-16](#GAS-16) | Optimize Deployment Size by Fine-tuning IPFS Hash | 20 | 30280 |
| [GAS-17](#GAS-17) | Use assembly hashing | 9 | 720 |
| [GAS-18](#GAS-18) | State variable read in a loop | 3 | 291 |
| [GAS-19](#GAS-19) | Multiple accesses of the same mapping/array key/index should be cached | 41 | 1722 |
| [GAS-20](#GAS-20) | Multiple mappings can be replaced with a single struct mapping | 15 | 630 |
| [GAS-21](#GAS-21) | State variables should be cached in stack variables rather than re-reading them from storage(Not captured by 4nalyzer) | 32 | 3104 |
| [GAS-22](#GAS-22) | Use Only Named Returns | 113 | 4972 |
| [GAS-23](#GAS-23) | Nested for loops should be avoided due to high gas costs resulting from O^2 time complexity | 5 | - |
| [GAS-24](#GAS-24) | Nesting `if`-statements is cheaper than using `&&` | 13 | 52 |
| [GAS-25](#GAS-25) | Consider using OpenZeppelin's `EnumerateSet` instead of nested mappings | 6 | 6000 |
| [GAS-26](#GAS-26) | Shorten the array rather than copying to a new one | 10 | - |
| [GAS-27](#GAS-27) | Operator `>=`/`<=` costs less gas than operator `>`/`<` | 152 | 456 |
| [GAS-28](#GAS-28) | Functions that revert when called by normal users can be marked as `payable`(Not captured by 4nalyzer) | 4 | 100 |
| [GAS-29](#GAS-29) | Using `private` for constants saves gas | 48 | 163488 |
| [GAS-30](#GAS-30) | Private functions used once can be inlined | 1 | - |
| [GAS-31](#GAS-31) | Refactor modifiers to call a local function | 2 | 2000 |
| [GAS-32](#GAS-32) | Default bool values are manually reset | 2 | - |
| [GAS-33](#GAS-33) | Use shift right/left instead of division if possible(Not captured by 4nalyzer) | 27 | - |
| [GAS-34](#GAS-34) | Usage of smaller `uint`/`int` types causes overhead | 341 | 18755 |
| [GAS-35](#GAS-35) | Consider using solady's 'FixedPointMathLib' | 133 | - |
| [GAS-36](#GAS-36) | Newer versions of solidity are more gas efficient | 20 | - |
| [GAS-37](#GAS-37) | `address(this)` can be stored in state variable that will ultimately cost less, than every time calculating this, specifically when it used multiple times in a contract | 10 | - |
| [GAS-38](#GAS-38) | Gas savings can be achieved by changing the model for assigning value to the structure | 1 | 130 |
| [GAS-39](#GAS-39) | Optimize Storage with Byte Truncation for Time Related State Variables | 7 | 14000 |
| [GAS-40](#GAS-40) | Trade-offs Between Modifiers and Internal Functions | 152 | 1596000 |
| [GAS-41](#GAS-41) | Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes | 13 | 222300 |
| [GAS-42](#GAS-42) | Divisions can be `unchecked` to save gas | 1 | 20 |
| [GAS-43](#GAS-43) | Avoid unnecessary public variables | 5 | 110000 |
| [GAS-44](#GAS-44) | Using assembly to check for `address(0)` can save gas(Not captured by 4nalyzer) | 1 | 6 |
| [GAS-45](#GAS-45) | Use assembly to `emit` events | 25 | 950 |
| [GAS-46](#GAS-46) | Use assembly to validate `msg.sender` | 8 | 96 |
| [GAS-47](#GAS-47) | Simple checks for zero can be done using assembly to save gas | 137 | 137 |
| [GAS-48](#GAS-48) | Use assembly in place of `abi.decode` to extract calldata values more efficiently | 3 | - |
| [GAS-49](#GAS-49) | Use `byte32` in place of `string` | 16 | - |
| [GAS-50](#GAS-50) | Use `x = x + y` instead of `x += y` for state variables(Not captured by 4nalyzer) | 22 | 220 |
| [GAS-51](#GAS-51) | Use solady library where possible to save gas | 5 | 5000 |
| [GAS-52](#GAS-52) | Variable declared within iteration | 102 | - |
| [GAS-53](#GAS-53) | Enable IR-based code generation | 20 | - |
| [GAS-54](#GAS-54) | Using XOR (^) and AND (&) bitwise equivalents for gas optimizations | 88 | - |

Total: 1867 instances over 54 issues with an estimate of 2206820 gas saved.


## Gas Optimizations

### <a name="GAS-01"></a>[GAS-01] `abi.encode()` is less efficient than `abi.encodepacked()` for non-address arguments

*There are 4 Instances of this issue* :
```solidity
File: contracts/PanopticFactory.sol

396:         bytes memory mintCallback = abi.encode(
                 CallbackLib.CallbackData({
                     poolFeatures: CallbackLib.PoolFeatures({token0: token0, token1: token1, fee: fee}),
                     payer: msg.sender
                 })
             );

```
([396](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L396-L401))
```solidity
File: contracts/SemiFungiblePositionManager.sol

773:             data = abi.encode(
                     CallbackLib.CallbackData({
                         poolFeatures: CallbackLib.PoolFeatures({
                             token0: _univ3pool.token0(),
                             token1: _univ3pool.token1(),
                             fee: _univ3pool.fee()
                         }),
                         payer: msg.sender
                     })
                 );

1190:         bytes memory mintdata = abi.encode(
                  CallbackLib.CallbackData({ // compute by reading values from univ3pool every time
                          poolFeatures: CallbackLib.PoolFeatures({
                              token0: univ3pool.token0(),
                              token1: univ3pool.token1(),
                              fee: univ3pool.fee()
                          }),
                          payer: msg.sender
                      })
              );

```
([773](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L773-L782),[1190](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1190-L1199))
```solidity
File: contracts/libraries/PanopticMath.sol

103:                 (uint248(uint256(keccak256(abi.encode(tokenId)))));

```
([103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L103-L103))
### <a name="GAS-02"></a>[GAS-02] Argument validation should be at the top of the function/block
Checks that involve function arguments should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting a Gcoldsload (2100 gas*) in a function that may ultimately revert in the unhappy case.

*There are 91 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

541:         if (msg.sender != owner) {

599:         if (msg.sender != owner) {

664:                 if (positionId.isLong(leg) == 0) continue;

776:         if (utilization < 0) {

784:         if (uint256(utilization) < TARGET_POOL_UTIL) {

790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {

841:         if (utilization > SATURATED_POOL_UTIL) {

1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1168:         if (positionBalanceArray.length > 0) {

1173:             if (premiumAllPositions < 0) {

1182:         if (premiumAllPositions > 0) {

1257:                 if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;

1346:                     ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1
                          ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1
                              ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1450:         if (isLong != tokenId.isLong(partnerIndex)) {

1488:         } else if (isLong == 1) {

1541:         if (tokenId.asset(index) != tokenType) {

```
([541](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L541-L541),[599](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L599-L599),[664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L664-L664),[776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L776-L776),[784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L784-L784),[790](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L790-L790),[841](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L841-L841),[1060](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1060-L1060),[1168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1168-L1168),[1173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1173-L1173),[1182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1182-L1182),[1257](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1257-L1257),[1346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1346-L1347),[1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1374-L1375),[1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1450-L1450),[1488](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1488-L1488),[1541](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1541-L1541))
```solidity
File: contracts/PanopticFactory.sol

181:         if (amount0Owed > 0)

188:         if (amount1Owed > 0)

220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

314:             if (rarity >= minTargetRarity) {

351:             if (token0 == WETH) {

355:             } else if (token1 == WETH) {

```
([181](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L181-L181),[188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L188-L188),[220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L220-L220),[314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L314-L314),[351](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L351-L351),[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L355-L355))
```solidity
File: contracts/PanopticPool.sol

341:         if (currentSqrtPriceX96 <= sqrtLowerBound || currentSqrtPriceX96 >= sqrtUpperBound) {

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

510:         if (tickLimitLow < tickLimitHigh) {

865:             if (tokenId.isLong(leg) == 0) {

944:             if (!_checkSolvencyAtTick(user, positionIdList, currentTick, slowOracleTick, buffer))

1156:             !_checkSolvencyAtTick(
                      msg.sender,
                      positionIdListLiquidator,
                      finalTick,
                      finalTick,
                      BP_DECREASE_BUFFER
                  )

1274:         if (positionIdListExercisor.length > 0)

1492:         if (effectiveLiquidityFactorX32 > uint256(effectiveLiquidityLimitX32))

1520:             if ((isLong == 1) || computeAllPremia) {

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1679:             if (tokenId.isLong(leg) == 0) {

1864:                 if (tokenId.isLong(leg) == 1) {

1865:                     if (commitLongSettled)

```
([341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L341-L341),[460](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L460-L460),[510](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L510-L510),[865](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L865-L865),[944](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L944-L944),[1156](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1156-L1162),[1274](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1274-L1274),[1492](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1492-L1492),[1520](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1520-L1520),[1596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1596-L1596),[1679](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1679-L1679),[1864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1864-L1864),[1865](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1865-L1865))
```solidity
File: contracts/SemiFungiblePositionManager.sol

412:         if (amount0Owed > 0)

419:         if (amount1Owed > 0)

576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

691:         if (isBurn) {

715:         if (tickLimitLow > tickLimitHigh) {

727:         if ((currentTick >= tickLimitHigh) || (currentTick <= tickLimitLow))

1006:                 if (isBurn) {

1029:                 if (!isBurn) {

1275:         if (isLong == 1) {

1465:         if (atTick < type(int24).max) {

```
([412](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L412-L412),[419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L419-L419),[576](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L576-L576),[691](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L691-L691),[715](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L715-L715),[727](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L727-L727),[1006](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1006-L1006),[1029](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1029-L1029),[1275](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1275-L1275),[1465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1465-L1465))
```solidity
File: contracts/libraries/FeesCalc.sol

147:             if (currentTick < tickLower) {

168:             } else if (currentTick >= tickUpper) {

```
([147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L147-L147),[168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L168-L168))
```solidity
File: contracts/libraries/Math.sol

93:             if (x >= 0x100000000000000000000000000000000) {

97:             if (x >= 0x10000000000000000) {

101:             if (x >= 0x100000000) {

105:             if (x >= 0x10000) {

109:             if (x >= 0x100) {

113:             if (x >= 0x10) {

176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

227:         } else if (currentTick >= liquidityChunk.tickUpper()) {

361:                 require(denominator > 0);

370:             require(denominator > prod1);

447:             if (mulmod(a, b, denominator) > 0) {

587:             if (mulmod(a, b, 2 ** 96) > 0) {

664:             if (mulmod(a, b, 2 ** 128) > 0) {

768:             if (left < j) quickSort(arr, left, j);

769:             if (i < right) quickSort(arr, i, right);

```
([93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L93-L93),[97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L97-L97),[101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L101-L101),[105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L105-L105),[109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L109-L109),[113](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L113-L113),[176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L176-L176),[227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L227-L227),[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L361-L361),[370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L370-L370),[447](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L447-L447),[587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L587-L587),[664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L664-L664),[768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L768-L768),[769](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L769-L769))
```solidity
File: contracts/libraries/PanopticMath.sol

183:             if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

325:         if (tokenId.asset(legIndex) == 0) {

357:                 tickLower % tickSpacing != 0 ||
                     tickUpper % tickSpacing != 0 ||
                     tickLower < minTick ||
                     tickUpper > maxTick

494:             if (sqrtPriceX96 < type(uint128).max) {

511:             if (sqrtPriceX96 < type(uint128).max) {

528:             if (sqrtPriceX96 < type(uint128).max) {

551:             if (sqrtPriceX96 < type(uint128).max) {

584:         if (tokenId.asset(legIndex) == 0) {

618:         if (tokenId.tokenType(legIndex) == 0) {

```
([183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L183-L183),[325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L325-L325),[357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L357-L360),[494](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L494-L494),[511](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L511-L511),[528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L528-L528),[551](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L551-L551),[584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L584-L584),[618](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L618-L618))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

112:         if (to.code.length != 0) {

114:                 ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=
                     ERC1155Holder.onERC1155Received.selector

163:         if (to.code.length != 0) {

165:                 ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
                     ERC1155Holder.onERC1155BatchReceived.selector

222:         if (to.code.length != 0) {

224:                 ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
                     ERC1155Holder.onERC1155Received.selector

```
([112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L112-L112),[114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L114-L115),[163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L163-L163),[165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L165-L166),[222](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L222-L222),[224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L224-L225))
```solidity
File: contracts/types/LeftRight.sol

161:                 LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||
                     (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))

184:                 LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||
                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))

```
([161](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L161-L162),[184](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L184-L185))
```solidity
File: contracts/types/TokenId.sol

471:         if (i == 1)

477:         if (i == 2)

483:         if (i == 3)

508:                 if (self.optionRatio(i) == 0) {

512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

531:                     (self.strike(i) == Constants.MIN_V3POOL_TICK) ||
                         (self.strike(i) == Constants.MAX_V3POOL_TICK)

541:                     if (self.riskPartner(riskPartnerIndex) != i)

546:                         (self.asset(riskPartnerIndex) != self.asset(i)) ||
                             (self.optionRatio(riskPartnerIndex) != self.optionRatio(i))

589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {

592:                     if (self.isLong(i) == 1) return; // validated

```
([471](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L471-L471),[477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L477-L477),[483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L483-L483),[508](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L508-L508),[512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L512-L512),[528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L528-L528),[531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L531-L532),[541](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L541-L541),[546](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L546-L547),[589](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L589-L589),[592](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L592-L592))
### <a name="GAS-03"></a>[GAS-03] Use `Array.unsafeAccess()` to avoid repeated array length checks
When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using [Array.unsafeAccess()](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/94697be8a3f0dfcd95dfb13ffbd39b5973f5c65d/contracts/utils/Arrays.sol#L57) in cases where the length has already been checked, as is the case with the instances below

*There are 8 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

802:         for (uint256 i = 0; i < positionIdList.length; ) {

```
([802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L802-L802))
```solidity
File: contracts/SemiFungiblePositionManager.sol

575:         for (uint256 i = 0; i < ids.length; ) {

```
([575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L575-L575))
```solidity
File: contracts/libraries/FeesCalc.sol

51:         for (uint256 k = 0; k < positionIdList.length; ) {

```
([51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L51-L51))
```solidity
File: contracts/libraries/PanopticMath.sol

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

```
([781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L781-L781),[860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L860-L860))
```solidity
File: contracts/multicall/Multicall.sol

14:         for (uint256 i = 0; i < data.length; ) {

```
([14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L14-L14))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {

```
([143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L143-L143),[187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L187-L187))
### <a name="GAS-04"></a>[GAS-04] Avoid updating storage when the value hasn't changed
If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (**2900 gas**), potentially at the expense of a Gcoldsload (**2100 gas**) or a Gwarmaccess (**100 gas**)

*There are 1 Instance of this issue* :
```solidity
File: contracts/PanopticFactory.sol

124:         SFPM = _SFPM;

```
([124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L124-L124))
### <a name="GAS-05"></a>[GAS-05] Avoid zero transfer to save gas
In Solidity, unnecessary operations can waste gas. For example, a transfer function without a zero amount check uses gas even if called with a zero amount, since the contract state remains unchanged. Implementing a zero amount check avoids these unnecessary function calls, saving gas and improving efficiency.

*There are 5 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

424:         SafeTransferLib.safeTransferFrom(
                 s_underlyingToken,
                 msg.sender,
                 address(s_panopticPool),
                 assets
             );

484:         SafeTransferLib.safeTransferFrom(
                 s_underlyingToken,
                 msg.sender,
                 address(s_panopticPool),
                 assets
             );

556:         SafeTransferLib.safeTransferFrom(
                 s_underlyingToken,
                 address(s_panopticPool),
                 receiver,
                 assets
             );

616:         SafeTransferLib.safeTransferFrom(
                 s_underlyingToken,
                 address(s_panopticPool),
                 receiver,
                 assets
             );

```
([424](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L424-L429),[484](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L484-L489),[556](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L556-L561),[616](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L616-L621))
```solidity
File: contracts/SemiFungiblePositionManager.sol

456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

```
([456](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L456-L456))

### <a name="GAS-06"></a>[GAS-06] Use `calldata` instead of `memory` for immutable arguments(Not captured by 4nalyzer)
Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.

*There are 7 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

// @audit  positionBalanceArray
1141:     function getAccountMarginDetails(
              address user,
              int24 currentTick,
              uint256[2][] memory positionBalanceArray,
              int128 premiumAllPositions
          ) public view returns (LeftRightUnsigned tokenData) {

// @audit  positionBalanceArray
1159:     function _getAccountMargin(
              address user,
              int24 atTick,
              uint256[2][] memory positionBalanceArray,
              int128 premiumAllPositions
          ) internal view returns (LeftRightUnsigned tokenData) {

// @audit  positionBalanceArray
1200:     function _getTotalRequiredCollateral(
              int24 atTick,
              uint256[2][] memory positionBalanceArray
          ) internal view returns (uint256 tokenRequired) {

```
([1141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1141-L1146),[1159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1159-L1164),[1200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1200-L1203))
```solidity
File: contracts/PanopticPool.sol

// @audit  collectedByLeg
1666:     function _updateSettlementPostMint(
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize
          ) internal {

// @audit  collectedByLeg
1833:     function _updateSettlementPostBurn(
              address owner,
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize,
              bool commitLongSettled
          ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {

```
([1666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1666-L1670),[1833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1833-L1839))
```solidity
File: contracts/libraries/CallbackLib.sol

// @audit  features
30:     function validateCallback(
            address sender,
            IUniswapV3Factory factory,
            PoolFeatures memory features
        ) internal view {

```
([30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L30-L34))


```solidity
File: contracts/libraries/Math.sol

// @audit  arr
753:     function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {

```
([753](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L753-L753))

### <a name="GAS-07"></a>[GAS-07] Constructors can be marked as `payable` to save deployment gas
`payable` functions cost less gas to execute, because the compiler does not have to add extra checks to ensure that no payment is provided. A constructor can be safely marked as payable, because only the deployer would be able to pass funds, and the project itself would not pass any funds.

*There are 4 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

178:     constructor(
             uint256 _commissionFee,
             uint256 _sellerCollateralRatio,
             uint256 _buyerCollateralRatio,
             int256 _forceExerciseCost,
             uint256 _targetPoolUtilization,
             uint256 _saturatedPoolUtilization,
             uint256 _ITMSpreadMultiplier
         ) {

```
([178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L178-L186))
```solidity
File: contracts/PanopticFactory.sol

115:     constructor(
             address _WETH9,
             SemiFungiblePositionManager _SFPM,
             IUniswapV3Factory _univ3Factory,
             IDonorNFT _donorNFT,
             address _poolReference,
             address _collateralReference
         ) {

```
([115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L115-L122))
```solidity
File: contracts/PanopticPool.sol

280:     constructor(SemiFungiblePositionManager _sfpm) {

```
([280](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L280-L280))
```solidity
File: contracts/SemiFungiblePositionManager.sol

341:     constructor(IUniswapV3Factory _factory) {

```
([341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L341-L341))

### <a name="GAS-08"></a>[GAS-08] Division by powers of two should use bit shifting
`<x> / 2` is the same as `<x> >> 1`. While the compiler uses the `SHR` opcode to accomplish both, the version that uses division incurs an overhead of [20 gas](https://gist.github.com/IllIllI000/ec0e4e6c4f52a6bca158f137a3afd4ff) due to `JUMP`s to and from a compiler utility function that introduces checks which can be avoided by using `unchecked {}` around the division by two.

*There are 9 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

843:                 return BUYER_COLLATERAL_RATIO / 2;

849:                 (BUYER_COLLATERAL_RATIO +
                         (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
                         (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

```
([843](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L843-L843),[849](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L849-L851))
```solidity
File: contracts/libraries/Math.sol

758:             int256 pivot = arr[uint256(left + (right - left) / 2)];

```
([758](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L758-L758))
```solidity
File: contracts/libraries/PanopticMath.sol

155:             return int24(Math.sort(ticks)[cardinality / 2]);

178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
                         int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
                     2;

376:             (width * tickSpacing) / 2,

476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

678:                 uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

```
([155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L155-L155),[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L178-L180),[376](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L376-L376),[476](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L476-L476),[477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L477-L477),[678](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L678-L678))
### <a name="GAS-09"></a>[GAS-09] Stack variable used as a cheaper cache for a state variable is only used once(Not captured by 4nalyzer)
If the variable is only accessed once, it's cheaper to use the state variable directly that one time, and save the **3 gas** the extra stack assignment would spend

*There are 1 Instance of this issue* :
```solidity
File: contracts/CollateralTracker.sol


1251:         bool underlyingIsToken0 = s_underlyingIsToken0;

```
([1251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1251-L1251))

### <a name="GAS-10"></a>[GAS-10] Do not calculate constants
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

*There are 5 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

```
([103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L103-L103),[105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L105-L105),[165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L165-L165))
```solidity
File: contracts/libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
([15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L15-L15))
```solidity
File: contracts/libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
([23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L23-L23))
### <a name="GAS-11"></a>[GAS-11] `do-while` is cheaper than `for`-loops when the initial check can be skipped
`for (uint256 i; i < len; ++i){ ... }` -> `do { ...; ++i } while (i < len);`

*There are 32 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

1208:         for (uint256 i = 0; i < totalIterations; ) {

1255:             for (uint256 index = 0; index < numLegs; ++index) {

```
([662](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L662-L662),[1208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1208-L1208),[1255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1255-L1255))
```solidity
File: contracts/PanopticPool.sol

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
([441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L441-L441),[459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L459-L459),[745](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L745-L745),[802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L802-L802),[864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L864-L864),[1382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1382-L1382),[1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1518-L1518),[1672](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1672-L1672),[1852](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1852-L1852))
```solidity
File: contracts/SemiFungiblePositionManager.sol

575:         for (uint256 i = 0; i < ids.length; ) {

601:         for (uint256 leg = 0; leg < numLegs; ) {

882:         for (uint256 leg = 0; leg < numLegs; ) {

```
([575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L575-L575),[601](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L601-L601),[882](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L882-L882))
```solidity
File: contracts/libraries/FeesCalc.sol

51:         for (uint256 k = 0; k < positionIdList.length; ) {

55:             for (uint256 leg = 0; leg < numLegs; ) {

```
([51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L51-L51),[55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L55-L55))
```solidity
File: contracts/libraries/PanopticMath.sol

137:             for (uint256 i = 0; i < cardinality + 1; ++i) {

148:             for (uint256 i = 0; i < cardinality; ++i) {

207:                 for (uint8 i; i < 8; ++i) {

248:             for (uint256 i = 0; i < 20; ++i) {

256:             for (uint256 i = 0; i < 19; ++i) {

395:         for (uint256 leg = 0; leg < numLegs; ) {

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

```
([137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L137-L137),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L148-L148),[207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L207-L207),[248](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L248-L248),[256](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L256-L256),[395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L395-L395),[781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L781-L781),[784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L784-L784),[860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L860-L860),[863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L863-L863))
```solidity
File: contracts/multicall/Multicall.sol

14:         for (uint256 i = 0; i < data.length; ) {

```
([14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L14-L14))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {

```
([143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L143-L143),[187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L187-L187))
```solidity
File: contracts/types/TokenId.sol

507:             for (uint256 i = 0; i < 4; ++i) {

581:             for (uint256 i = 0; i < numLegs; ++i) {

```
([507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L507-L507),[581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L581-L581))
### <a name="GAS-12"></a>[GAS-12] Duplicated `require()`/`revert()` checks should be refactored to a modifier or function to save deployment gas
This will cost more runtime gas, but will reduce deployment gas when the function is (optionally called via a modifier) called more than once as is the case for the examples below. Most projects do not make this trade-off, but it's available nonetheless.

*There are 3 Instances of this issue* :
```solidity
File: contracts/libraries/Math.sol

448:                 require(result < type(uint256).max);

588:                 require(result < type(uint256).max);

665:                 require(result < type(uint256).max);

```
([448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L448-L448),[588](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L588-L588),[665](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L665-L665))
### <a name="GAS-13"></a>[GAS-13] Counting down in `for` statements is more gas efficient
Counting down is more gas efficient than counting up because neither we are making zero variable to non-zero variable and also we will get gas refund in the last transaction when making non-zero to zero variable. [More info](https://solodit.xyz/issues/g-02-counting-down-in-for-statements-is-more-gas-efficient-code4rena-pooltogether-pooltogether-git)

*There are 33 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

1231:                 ++i;

1255:             for (uint256 index = 0; index < numLegs; ++index) {

```
([662](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L662-L662),[1231](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1231-L1231),[1255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1255-L1255))
```solidity
File: contracts/PanopticPool.sol

483:                     ++leg;

488:                 ++k;

779:                 ++leg;

813:                 ++i;

872:                 ++leg;

1389:                 ++i;

1572:                 ++leg;

1672:         for (uint256 leg = 0; leg < numLegs; ++leg) {

1977:                 ++leg;

```
([483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L483-L483),[488](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L488-L488),[779](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L779-L779),[813](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L813-L813),[872](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L872-L872),[1389](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1389-L1389),[1572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1572-L1572),[1672](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1672-L1672),[1977](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1977-L1977))
```solidity
File: contracts/SemiFungiblePositionManager.sol

579:                 ++i;

650:                 ++leg;

932:                 ++leg;

```
([579](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L579-L579),[650](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L650-L650),[932](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L932-L932))
```solidity
File: contracts/libraries/FeesCalc.sol

80:                     ++leg;

84:                 ++k;

```
([80](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L80-L80),[84](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L84-L84))
```solidity
File: contracts/libraries/PanopticMath.sol

137:             for (uint256 i = 0; i < cardinality + 1; ++i) {

148:             for (uint256 i = 0; i < cardinality; ++i) {

207:                 for (uint8 i; i < 8; ++i) {

248:             for (uint256 i = 0; i < 20; ++i) {

256:             for (uint256 i = 0; i < 19; ++i) {

407:                 ++leg;

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

```
([137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L137-L137),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L148-L148),[207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L207-L207),[248](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L248-L248),[256](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L256-L256),[407](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L407-L407),[781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L781-L781),[784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L784-L784),[860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L860-L860),[863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L863-L863))
```solidity
File: contracts/multicall/Multicall.sol

33:                 ++i;

```
([33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L33-L33))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

157:                 ++i;

187:             for (uint256 i = 0; i < owners.length; ++i) {

```
([157](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L157-L157),[187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L187-L187))
```solidity
File: contracts/types/TokenId.sol

507:             for (uint256 i = 0; i < 4; ++i) {

520:                 for (uint256 j = i + 1; j < numLegs; ++j) {

581:             for (uint256 i = 0; i < numLegs; ++i) {

```
([507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L507-L507),[520](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L520-L520),[581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L581-L581))
### <a name="GAS-14"></a>[GAS-14] Function names can be optimized
Function that are `public`/`external` and public state variable names can be optimized to save gas.

Method IDs that have two leading zero bytes can save **128 gas** each during deployment, and renaming functions to have lower method IDs will save **22 gas** per call, per sorted position shifted. [Reference](https://blog.emn178.cc/en/post/solidity-gas-optimization-function-name/)

*There are 20 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

```
([36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36-L36))
```solidity
File: contracts/PanopticFactory.sol

26: contract PanopticFactory is Multicall {

```
([26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L26-L26))
```solidity
File: contracts/PanopticPool.sol

27: contract PanopticPool is ERC1155Holder, Multicall {

```
([27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L27-L27))
```solidity
File: contracts/SemiFungiblePositionManager.sol

72: contract SemiFungiblePositionManager is ERC1155, Multicall {

```
([72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L72-L72))
```solidity
File: contracts/libraries/CallbackLib.sol

12: library CallbackLib {

```
([12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L12-L12))
```solidity
File: contracts/libraries/Constants.sol

7: library Constants {

```
([7](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L7-L7))
```solidity
File: contracts/libraries/Errors.sol

7: library Errors {

```
([7](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L7-L7))
```solidity
File: contracts/libraries/FeesCalc.sol

39: library FeesCalc {

```
([39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L39-L39))
```solidity
File: contracts/libraries/InteractionHelper.sol

17: library InteractionHelper {

```
([17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17-L17))
```solidity
File: contracts/libraries/Math.sol

13: library Math {

```
([13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L13-L13))
```solidity
File: contracts/libraries/PanopticMath.sol

18: library PanopticMath {

```
([18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18-L18))
```solidity
File: contracts/libraries/SafeTransferLib.sol

11: library SafeTransferLib {

```
([11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L11-L11))
```solidity
File: contracts/multicall/Multicall.sol

8: abstract contract Multicall {

```
([8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L8-L8))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

11: abstract contract ERC1155 {

```
([11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L11-L11))
```solidity
File: contracts/tokens/ERC20Minimal.sol

9: abstract contract ERC20Minimal {

```
([9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L9-L9))
```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: interface IDonorNFT {

```
([6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6-L6))
```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

11: interface IERC20Partial {

```
([11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L11-L11))
```solidity
File: contracts/types/LeftRight.sol

17: library LeftRightLibrary {

```
([17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L17-L17))
```solidity
File: contracts/types/LiquidityChunk.sol

52: library LiquidityChunkLibrary {

```
([52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52-L52))
```solidity
File: contracts/types/TokenId.sol

60: library TokenIdLibrary {

```
([60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L60-L60))
### <a name="GAS-15"></a>[GAS-15] Don't initialize variables with default value

*There are 31 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

1208:         for (uint256 i = 0; i < totalIterations; ) {

1255:             for (uint256 index = 0; index < numLegs; ++index) {

```
([662](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L662-L662),[1208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1208-L1208),[1255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1255-L1255))
```solidity
File: contracts/PanopticPool.sol

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
([441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L441-L441),[459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L459-L459),[745](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L745-L745),[802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L802-L802),[864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L864-L864),[1382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1382-L1382),[1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1518-L1518),[1672](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1672-L1672),[1852](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1852-L1852))
```solidity
File: contracts/SemiFungiblePositionManager.sol

575:         for (uint256 i = 0; i < ids.length; ) {

601:         for (uint256 leg = 0; leg < numLegs; ) {

882:         for (uint256 leg = 0; leg < numLegs; ) {

```
([575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L575-L575),[601](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L601-L601),[882](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L882-L882))
```solidity
File: contracts/libraries/FeesCalc.sol

51:         for (uint256 k = 0; k < positionIdList.length; ) {

55:             for (uint256 leg = 0; leg < numLegs; ) {

```
([51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L51-L51),[55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L55-L55))
```solidity
File: contracts/libraries/PanopticMath.sol

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
([137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L137-L137),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L148-L148),[248](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L248-L248),[256](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L256-L256),[395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L395-L395),[781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L781-L781),[784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L784-L784),[860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L860-L860),[863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L863-L863))
```solidity
File: contracts/multicall/Multicall.sol

14:         for (uint256 i = 0; i < data.length; ) {

```
([14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L14-L14)
)
```solidity
File: contracts/tokens/ERC1155Minimal.sol

143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {

```
([143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L143-L143),[187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L187-L187))
```solidity
File: contracts/types/TokenId.sol

507:             for (uint256 i = 0; i < 4; ++i) {

581:             for (uint256 i = 0; i < numLegs; ++i) {

```
([507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L507-L507),[581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L581-L581))
### <a name="GAS-16"></a>[GAS-16] Optimize Deployment Size by Fine-tuning IPFS Hash
The Solidity compiler appends 53 bytes of metadata to the smart contract code, incurring an extra cost of 10,600 gas. This additional expense arises from 200 gas per bytecode, plus calldata cost, which amounts to 16 gas for non-zero bytes and 4 gas for zero bytes. This results in a maximum of 848 extra gas in calldata cost.

Reducing this cost is crucial for the following reasons:

The metadata's 53-byte addition leads to a deployment cost increase of 10,600 gas. It can also result in an additional calldata cost of up to 848 gas. Ways to Minimize Gas Consumption:

Employ the `--no-cbor-metadata` compiler option to exclude metadata. Be cautious as this might impact contract verification. Search for code comments that yield an IPFS hash with more zeros, thereby reducing calldata costs.

*There are 20 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

1: // SPDX-License-Identifier: BUSL-1.1

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1-L1))
```solidity
File: contracts/PanopticFactory.sol

1: // SPDX-License-Identifier: BUSL-1.1

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L1-L1))
```solidity
File: contracts/PanopticPool.sol

1: // SPDX-License-Identifier: BUSL-1.1

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1-L1))
```solidity
File: contracts/SemiFungiblePositionManager.sol

1: // SPDX-License-Identifier: BUSL-1.1

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1-L1))
```solidity
File: contracts/libraries/CallbackLib.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L1-L1))
```solidity
File: contracts/libraries/Constants.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L1-L1))
```solidity
File: contracts/libraries/Errors.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L1-L1))
```solidity
File: contracts/libraries/FeesCalc.sol

1: // SPDX-License-Identifier: BUSL-1.1

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L1-L1))
```solidity
File: contracts/libraries/InteractionHelper.sol

1: // SPDX-License-Identifier: BUSL-1.1

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L1-L1))
```solidity
File: contracts/libraries/Math.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L1-L1))
```solidity
File: contracts/libraries/PanopticMath.sol

1: // SPDX-License-Identifier: BUSL-1.1

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L1-L1))
```solidity
File: contracts/libraries/SafeTransferLib.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L1-L1))
```solidity
File: contracts/multicall/Multicall.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L1-L1))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L1-L1))
```solidity
File: contracts/tokens/ERC20Minimal.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L1-L1))
```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L1-L1))
```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L1-L1))
```solidity
File: contracts/types/LeftRight.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L1-L1))
```solidity
File: contracts/types/LiquidityChunk.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L1-L1))
```solidity
File: contracts/types/TokenId.sol

1: // SPDX-License-Identifier: GPL-2.0-or-later

```
([1](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L1-L1))
### <a name="GAS-17"></a>[GAS-17] Use assembly hashing
From a gas standpoint, the assembly version of the `keccak256` hashing function can be more efficient than the high-level Solidity version. This is because Solidity has additional overhead when handling function calls and memory management, which can increase the gas cost.

*There are 9 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

461:                     bytes32 chunkKey = keccak256(
                             abi.encodePacked(
                                 tokenId.strike(leg),
                                 tokenId.width(leg),
                                 tokenId.tokenType(leg)
                             )
                         );

1642:             bytes32 chunkKey = keccak256(
                      abi.encodePacked(
                          tokenId.strike(legIndex),
                          tokenId.width(legIndex),
                          tokenId.tokenType(legIndex)
                      )
                  );

1673:             bytes32 chunkKey = keccak256(
                      abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
                  );

1855:             bytes32 chunkKey = keccak256(
                      abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
                  );

```
([461](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L461-L467),[1642](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1642-L1648),[1673](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1673-L1675),[1855](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1855-L1857))
```solidity
File: contracts/SemiFungiblePositionManager.sol

611:             bytes32 positionKey_from = keccak256(
                     abi.encodePacked(
                         address(univ3pool),
                         from,
                         id.tokenType(leg),
                         liquidityChunk.tickLower(),
                         liquidityChunk.tickUpper()
                     )
                 );

620:             bytes32 positionKey_to = keccak256(
                     abi.encodePacked(
                         address(univ3pool),
                         to,
                         id.tokenType(leg),
                         liquidityChunk.tickLower(),
                         liquidityChunk.tickUpper()
                     )
                 );

974:         bytes32 positionKey = keccak256(
                 abi.encodePacked(
                     address(univ3pool),
                     msg.sender,
                     tokenType,
                     liquidityChunk.tickLower(),
                     liquidityChunk.tickUpper()
                 )
             );

1458:         bytes32 positionKey = keccak256(
                  abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)
              );

```
([611](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L611-L619),[620](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L620-L628),[974](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L974-L982),[1458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1458-L1460))
```solidity
File: contracts/libraries/PanopticMath.sol

878:                         bytes32 chunkKey = keccak256(
                                 abi.encodePacked(
                                     tokenId.strike(0),
                                     tokenId.width(0),
                                     tokenId.tokenType(0)
                                 )
                             );

```
([878](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L878-L884))
### <a name="GAS-18"></a>[GAS-18] State variable read in a loop
The state variable should be cached in a local variable rather than reading it on every iteration of the loop, which will replace each Gwarmaccess (**100 gas**) with a much cheaper stack read.

*There are 3 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

// @audit s_univ3pool
752:                     address(s_univ3pool),

// @audit s_univ3pool
1530:                         address(s_univ3pool),

// @audit s_univ3pool
1708:                     address(s_univ3pool),

```
([752](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L752-L752),[1530](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1530-L1530),[1708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1708-L1708))
### <a name="GAS-19"></a>[GAS-19] Multiple accesses of the same mapping/array key/index should be cached
Access of a value inside a mapping/array, within a function. Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the key's `keccak256` hash (Gkeccak256 - **30 gas**) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into `memory`/`calldata`

*There are 41 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

// @audit 'allowance[owner]' also accessed on line 542
544:             if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

// @audit 'allowance[owner]' also accessed on line 600
602:             if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;


// @audit 'positionBalanceArray[i][1]' also accessed on line 1213
1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

```
([544](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L544-L544),[602](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L602-L602),[1216](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1216-L1216))
```solidity
File: contracts/PanopticFactory.sol

// @audit 's_getPanopticPool[v3Pool]' also accessed on line 229
253:         s_getPanopticPool[v3Pool] = newPoolContract;

```
([253](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L253-L253))
```solidity
File: contracts/PanopticPool.sol

// @audit 'balances[k][1]' also accessed on line 445
452:                     LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),

// @audit 'premiaByLeg[leg]' also accessed on line 473
480:                     portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);

// @audit 's_positionBalance[msg.sender][tokenId]' also accessed on line 638 
654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned

// @audit 'touchedId[0]' also accessed on line 1193, 1219, 1234, 1277
1198:             .computeExercisedAmounts(touchedId[0], positionBalance);

// @audit 's_positionsHash[account]' also accessed on line 1411
1416:         s_positionsHash[account] = newHash;

// @audit 'premiumAccumulatorsByLeg[leg][0]' also accessed on line 1528
1550:                                     ((premiumAccumulatorsByLeg[leg][0] -

// @audit 'premiumAccumulatorsByLeg[leg][1]' also accessed on line 1528
1559:                                     ((premiumAccumulatorsByLeg[leg][1] -

// @audit 'premiaByLeg[leg]' also accessed on same line
1567:                         premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

// @audit 's_options[owner][tokenId]' also accessed on line 1621
1622:             s_options[owner][tokenId][legIndex] = accumulatedPremium;

// @audit 's_settledTokens[chunkKey]' also accessed on same line
1650:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(

// @audit 's_settledTokens[chunkKey]' also accessed on same line
1677:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);

// @audit 's_grossPremiumLast[chunkKey]' also accessed on line 1719
1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned

// @audit 'grossCurrent[0]' also accessed on line 1707
1729:                                 (grossCurrent[0] *

// @audit 'grossCurrent[1]' also accessed on line 1707
1737:                                 (grossCurrent[1] *

// @audit 's_grossPremiumLast[chunkKey]' also accessed on line 1886
1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0

// @audit '_premiumAccumulatorsByLeg[_leg]' also accessed on line 1940
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *

// @audit 'premiumAccumulatorsByLeg[_leg]' also accessed on line 1967
1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));

// @audit 's_settledTokens[chunkKey]' also accessed on line 1860
1974:             s_settledTokens[chunkKey] = settledTokens;

```
([452](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L452-L452),[480](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L480-L480),[654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L654-L654),[1198](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1198-L1198),[1416](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1416-L1416),[1550](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1550-L1550),[1559](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1559-L1559),[1567](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1567-L1567),[1622](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1622-L1622),[1650](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1650-L1650),[1677](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1677-L1677),[1725](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1725-L1725),[1729](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1729-L1729),[1737](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1737-L1737),[1928](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1928-L1928),[1957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1957-L1957),[1968](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1968-L1968),[1974](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1974-L1974))
```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit 's_poolContext[poolId]' also accessed on line 322
325:         s_poolContext[poolId].locked = true;

// @audit 's_poolContext[poolId]' also accessed on line 372, 381
379:         s_poolContext[poolId] = PoolAddressAndLock({

// @audit 's_AddrToPoolIdData[univ3pool]' also accessed on line 362
388:             s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;

// @audit 'ids[i]' also accessed on line 576
577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);

// @audit 's_accountLiquidity[positionKey_to]' also accessed on line 632
644:             s_accountLiquidity[positionKey_to] = fromLiq;

// @audit 's_accountLiquidity[positionKey_from]' also accessed on line 637
645:             s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

// @audit 's_accountFeesBase[positionKey_to]' also accessed on line 633
647:             s_accountFeesBase[positionKey_to] = fromBase;

// @audit 's_accountFeesBase[positionKey_from]' also accessed on line 641
648:             s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

// @audit 's_accountLiquidity[positionKey]' also accessed on line 988
1038:             s_accountLiquidity[positionKey] = LeftRightUnsigned

// @audit 's_accountPremiumOwed[positionKey]' also accessed on line 1123
1125:                 s_accountPremiumOwed[positionKey],

// @audit 's_accountPremiumGross[positionKey]' also accessed on line 1123
1127:                 s_accountPremiumGross[positionKey],

// @audit 's_accountPremiumOwed[positionKey]' also accessed on line 1508
1519:                 ? s_accountPremiumOwed[positionKey]

// @audit 's_accountPremiumGross[positionKey]' also accessed on line 1510
1520:                 : s_accountPremiumGross[positionKey];

```
([325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L325-L325),[379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L379-L379),[388](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L388-L388),[577](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L577-L577),[644](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L644-L644),[645](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L645-L645),[647](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L647-L647),[648](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L648-L648),[1038](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1038-L1038),[1125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1125-L1125),[1127](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1127-L1127),[1519](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1519-L1519),[1520](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1520-L1520))
```solidity
File: contracts/libraries/PanopticMath.sol

// @audit 'tickCumulatives[i]' also accessed on line 138
150:                     (tickCumulatives[i] - tickCumulatives[i + 1]) /

// @audit 'timestamps[i]' also accessed on line 138
151:                     int256(timestamps[i] - timestamps[i + 1]);

// @audit 'positionIdList[i]' also accessed on line 782
861:                 TokenId tokenId = positionIdList[i];

// @audit '_premiasByLeg[i][leg]' also accessed on line 870, 890, 894
874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),

// @audit '_settledTokens[chunkKey]' also accessed on same line
897:                         _settledTokens[chunkKey] = _settledTokens[chunkKey].add(

```
([150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L150-L150),[151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L151-L151),[861](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L861-L861),[874](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L874-L874),[897](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L897-L897))
```solidity
File: contracts/tokens/ERC20Minimal.sol

// @audit 'allowance[from]' also accessed on line 82
84:         if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;

```
([84](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L84-L84))
### <a name="GAS-20"></a>[GAS-20] Multiple mappings can be replaced with a single struct mapping
Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0) (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

*There are 15 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))
             internal s_options;

245:     mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

251:     mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;

258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
             internal s_positionBalance;

272:     mapping(address account => uint256 positionsHash) internal s_positionsHash;

```
([238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L238-L239),[245](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L245-L245),[251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L251-L251),[258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L258-L259),[272](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L272-L272))
```solidity
File: contracts/SemiFungiblePositionManager.sol

177:     mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
             internal s_accountLiquidity;

287:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

295:     mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;

```
([177](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L177-L178),[287](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L287-L287),[289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L289-L289),[295](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L295-L295))
```solidity
File: contracts/libraries/PanopticMath.sol

776:         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens

865:                         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
                                 storage _settledTokens = settledTokens;

```
([776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L776-L776),[865](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L865-L866))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

66:     mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;

71:     mapping(address owner => mapping(address operator => bool approvedForAll))
            public isApprovedForAll;

```
([66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L66-L66),[71](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L71-L72))
```solidity
File: contracts/tokens/ERC20Minimal.sol

35:     mapping(address account => uint256 balance) public balanceOf;

39:     mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;

```
([35](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L35-L35),[39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L39-L39))
### <a name="GAS-21"></a>[GAS-21] State variables should be cached in stack variables rather than re-reading them from storage(Not captured by 4nalyzer)
The instances below point to the **second+** access of a state variable within a function. Caching of a state variable replaces each Gwarmaccess (**100 gas**) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

*There are 33 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

// @audit 's_initialized' also accessed on line 229
230:         s_initialized = true;

// @audit 'DECIMALS' also accessed on line 403
405:                 totalAssets() * DECIMALS

// @audit 'DECIMALS' also accessed on same line
446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

// @audit 'DECIMALS' also accessed on line 463
465:                 totalSupply * (DECIMALS - COMMISSION_FEE)

// @audit 'DECIMALS_128' also accessed on line 731
732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

// @audit 'DECIMALS' also accessed on line 791
797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

// @audit 'TARGET_POOL_UTIL' also accessed on line 784, 798
797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

// @audit 'SATURATED_POOL_UTIL' also accessed on line 790
798:                 (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);

// @audit 'BUYER_COLLATERAL_RATIO' also accessed on line 836, 849, 850
843:                 return BUYER_COLLATERAL_RATIO / 2;

// @audit 'SATURATED_POOL_UTIL' also accessed on line 841, 851
850:                     (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /

// @audit 'TARGET_POOL_UTIL' also accessed on line 835
851:                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

// @audit 's_poolAssets' also accessed on line 1003
1028:             s_poolAssets = uint128(uint256(updatedAssets));

// @audit 's_inAMM' also accessed on same line
1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

// @audit 's_poolAssets' also accessed on line 1052
1084:             s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));

// @audit 's_inAMM' also accessed on same line
1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

// @audit 'DECIMALS' also accessed on line 1111
1122:                     DECIMALS

// @audit 'DECIMALS' also accessed on line 1486
1496:                 required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);

```
([230](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L230-L230),[405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L405-L405),[446](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L446-L446),[465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L465-L465),[732](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L732-L732),[797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L797-L797),[797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L797-L797),[798](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L798-L798),[843](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L843-L843),[850](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L850-L850),[851](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L851-L851),[1028](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1028-L1028),[1029](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1029-L1029),[1084](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1084-L1084),[1085](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1085-L1085),[1122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1122-L1122),[1496](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1496-L1496))
```solidity
File: contracts/PanopticFactory.sol

// @audit 's_initialized' also accessed on line 135
137:             s_initialized = true;

// @audit 's_owner' also accessed on line 148
152:         s_owner = newOwner;

// @audit 'WETH' also accessed on line 351
355:             } else if (token1 == WETH) {

// @audit 'FULL_RANGE_LIQUIDITY_AMOUNT_WETH' also accessed on line 353
358:                         FULL_RANGE_LIQUIDITY_AMOUNT_WETH,

// @audit 'FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN' also accessed on line 366
370:                         FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,

```
([137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L137-L137),[152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L152-L152),[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L355-L355),[358](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L358-L358),[370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L370-L370))
```solidity
File: contracts/PanopticPool.sol

// @audit 's_univ3pool' also accessed on line 299
302:         s_univ3pool = IUniswapV3Pool(_univ3pool);

// @audit 's_univ3pool' also accessed on line 523
530:             s_univ3pool

// @audit 's_miniMedian' also accessed on line 529
533:         if (medianData != 0) s_miniMedian = medianData;

// @audit 's_collateralToken0' also accessed on line 1046, 1127, 1141
1072:         s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());

// @audit 's_collateralToken1' also accessed on line 1053, 1128, 1146
1073:         s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());

// @audit 's_univ3pool' also accessed on line 1032
1094:             (, finalTick, , , , , ) = s_univ3pool.slot0();

// @audit 's_collateralToken0' also accessed on line 1222, 1246, 1252, 1265
1231:         LeftRightSigned exerciseFees = s_collateralToken0.exerciseCost(

// @audit 's_collateralToken1' also accessed on line 1223, 1257, 1266
1247:             s_collateralToken1

// @audit 's_univ3pool' also accessed on line 1598
1606:                 address(s_univ3pool),

```
([302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L302-L302),[530](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L530-L530),[533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L533-L533),[1072](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1072-L1072),[1073](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1073-L1073),[1094](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1094-L1094),[1231](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1231-L1231),[1247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1247-L1247),[1606](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1606-L1606))
```solidity
File: contracts/SemiFungiblePositionManager.sol

// @audit 'VEGOID' also accessed on line 1367
1391:                         ((removedLiquidity ** 2) / 2 ** (VEGOID));

```
([1391](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1391-L1391))
### <a name="GAS-22"></a>[GAS-22] Use Only Named Returns
The Solidity compiler can generate more efficient bytecode when using named returns. It's recommended to replace anonymous returns with named returns for potential gas savings.

*There are 113 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

289:     function name() external view returns (string memory) {

303:     function symbol() external view returns (string memory) {

310:     function decimals() external view returns (uint8) {

323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

1043:     function exercise(
              address optionOwner,
              int128 longAmount,
              int128 shortAmount,
              int128 swappedAmount,
              int128 realizedPremium
          ) external onlyPanopticPool returns (int128) {

```
([289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L289-L289),[303](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L303-L303),[310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L310-L310),[323](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L323-L326),[341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L341-L345),[1043](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1043-L1049))
```solidity
File: contracts/PanopticFactory.sol

159:     function owner() external view returns (address) {

335:     function _mintFullRange(
             IUniswapV3Pool v3Pool,
             address token0,
             address token1,
             uint24 fee
         ) internal returns (uint256, uint256) {

335:     function _mintFullRange(
             IUniswapV3Pool v3Pool,
             address token0,
             address token1,
             uint24 fee
         ) internal returns (uint256, uint256) {

420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {

```
([159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L159-L159),[335](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L335-L340),[335](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L335-L340),[420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L420-L420))
```solidity
File: contracts/PanopticPool.sol

381:     function calculateAccumulatedFeesBatch(
             address user,
             bool includePendingPremium,
             TokenId[] calldata positionIdList
         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

499:     function _getSlippageLimits(
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal pure returns (int24, int24) {

499:     function _getSlippageLimits(
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal pure returns (int24, int24) {

677:     function _mintInSFPMAndUpdateCollateral(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal returns (uint128) {

706:     function _payCommissionAndWriteData(
             TokenId tokenId,
             uint128 positionSize,
             LeftRightSigned totalSwapped
         ) internal returns (uint128) {

1290:     function _checkSolvencyAtTick(
              address account,
              TokenId[] calldata positionIdList,
              int24 currentTick,
              int24 atTick,
              uint256 buffer
          ) internal view returns (bool) {

1425:     function univ3pool() external view returns (IUniswapV3Pool) {

1437:     function collateralToken1() external view returns (CollateralTracker) {

1757:     function _getAvailablePremium(
              uint256 totalLiquidity,
              LeftRightUnsigned settledTokens,
              LeftRightUnsigned grossPremiumLast,
              LeftRightUnsigned premiumOwed,
              uint256[2] memory premiumAccumulators
          ) internal pure returns (LeftRightUnsigned) {

```
([381](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L381-L385),[499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L499-L502),[499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L499-L502),[677](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L677-L682),[706](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L706-L710),[1290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1290-L1296),[1425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1425-L1425),[1437](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1437-L1437),[1757](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1757-L1763))
```solidity
File: contracts/SemiFungiblePositionManager.sol

1449:     function getAccountPremium(
              address univ3pool,
              address owner,
              uint256 tokenType,
              int24 tickLower,
              int24 tickUpper,
              int24 atTick,
              uint256 isLong
          ) external view returns (uint128, uint128) {

1449:     function getAccountPremium(
              address univ3pool,
              address owner,
              uint256 tokenType,
              int24 tickLower,
              int24 tickUpper,
              int24 atTick,
              uint256 isLong
          ) external view returns (uint128, uint128) {

```
([1449](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1449-L1457),[1449](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1449-L1457))
```solidity
File: contracts/libraries/FeesCalc.sol

97:     function calculateAMMSwapFees(
            IUniswapV3Pool univ3pool,
            int24 currentTick,
            int24 tickLower,
            int24 tickUpper,
            uint128 liquidity
        ) public view returns (LeftRightSigned) {

```
([97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L97-L103))
```solidity
File: contracts/libraries/InteractionHelper.sol

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
([48](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L48-L54),[91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L91-L94),[107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L107-L107))
```solidity
File: contracts/libraries/Math.sol

25:     function min24(int24 a, int24 b) internal pure returns (int24) {

33:     function max24(int24 a, int24 b) internal pure returns (int24) {

41:     function min(uint256 a, uint256 b) internal pure returns (uint256) {

49:     function min(int256 a, int256 b) internal pure returns (int256) {

57:     function max(uint256 a, uint256 b) internal pure returns (uint256) {

65:     function max(int256 a, int256 b) internal pure returns (int256) {

73:     function abs(int256 x) internal pure returns (int256) {

81:     function absUint(int256 x) internal pure returns (uint256) {

128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {

191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

241:     function getLiquidityForAmount0(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount0
         ) internal pure returns (LiquidityChunk) {

271:     function getLiquidityForAmount1(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount1
         ) internal pure returns (LiquidityChunk) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

458:     function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521:     function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

598:     function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

675:     function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

776:     function sort(int256[] memory data) internal pure returns (int256[] memory) {

```
([25](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L25-L25),[33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L33-L33),[41](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L41-L41),[49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L49-L49),[57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L57-L57),[65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L65-L65),[73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L73-L73),[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L81-L81),[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L128-L128),[191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L191-L191),[207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L207-L207),[241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L241-L245),[271](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L271-L275),[325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L325-L325),[458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L458-L458),[521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L521-L521),[598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L598-L598),[675](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L675-L675),[776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L776-L776))
```solidity
File: contracts/libraries/PanopticMath.sol

47:     function getPoolId(address univ3pool) internal view returns (uint64) {

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

75:     function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

92:     function updatePositionsHash(
            uint256 existingHash,
            TokenId tokenId,
            bool addFlag
        ) internal pure returns (uint256) {

125:     function computeMedianObservedPrice(
             IUniswapV3Pool univ3pool,
             uint256 observationIndex,
             uint256 observationCardinality,
             uint256 cardinality,
             uint256 period
         ) external view returns (int24) {

241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

289:     function getLiquidityChunk(
             TokenId tokenId,
             uint256 legIndex,
             uint128 positionSize
         ) internal pure returns (LiquidityChunk) {

371:     function getRangesFromStrike(
             int24 width,
             int24 tickSpacing
         ) internal pure returns (int24, int24) {

371:     function getRangesFromStrike(
             int24 width,
             int24 tickSpacing
         ) internal pure returns (int24, int24) {

419:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             uint160 sqrtPriceX96
         ) internal pure returns (uint256, uint256) {

419:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             uint160 sqrtPriceX96
         ) internal pure returns (uint256, uint256) {

445:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             int24 tick
         ) internal pure returns (uint256, uint256) {

445:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             int24 tick
         ) internal pure returns (uint256, uint256) {

468:     function convertNotional(
             uint128 contractSize,
             int24 tickLower,
             int24 tickUpper,
             uint256 asset
         ) internal pure returns (uint128) {

490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

574:     function getAmountsMoved(
             TokenId tokenId,
             uint128 positionSize,
             uint256 legIndex
         ) internal pure returns (LeftRightUnsigned) {

651:     function getLiquidationBonus(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint160 sqrtPriceX96Twap,
             uint160 sqrtPriceX96Final,
             LeftRightSigned netExchanged,
             LeftRightSigned premia
         ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

768:     function haircutPremia(
             address liquidatee,
             TokenId[] memory positionIdList,
             LeftRightSigned[4][] memory premiasByLeg,
             LeftRightSigned collateralRemaining,
             CollateralTracker collateral0,
             CollateralTracker collateral1,
             uint160 sqrtPriceX96Final,
             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
         ) external returns (int256, int256) {

768:     function haircutPremia(
             address liquidatee,
             TokenId[] memory positionIdList,
             LeftRightSigned[4][] memory premiasByLeg,
             LeftRightSigned collateralRemaining,
             CollateralTracker collateral0,
             CollateralTracker collateral1,
             uint160 sqrtPriceX96Final,
             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
         ) external returns (int256, int256) {

917:     function getRefundAmounts(
             address refunder,
             LeftRightSigned refundValues,
             int24 atTick,
             CollateralTracker collateral0,
             CollateralTracker collateral1
         ) external view returns (LeftRightSigned) {

```
([47](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L47-L47),[59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L59-L59),[75](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L75-L75),[92](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L92-L96),[125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L125-L131),[241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L241-L241),[289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L289-L293),[371](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L371-L374),[371](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L371-L374),[419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L419-L424),[419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L419-L424),[445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L445-L450),[445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L445-L450),[468](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L468-L473),[490](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L490-L490),[507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L507-L507),[524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L524-L524),[547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L547-L547),[574](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L574-L578),[651](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L651-L658),[768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L768-L777),[768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L768-L777),[917](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L917-L923))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

```
([200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L200-L200))
```solidity
File: contracts/tokens/ERC20Minimal.sol

49:     function approve(address spender, uint256 amount) public returns (bool) {

61:     function transfer(address to, uint256 amount) public virtual returns (bool) {

81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

```
([49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L49-L49),[61](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L61-L61),[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L81-L81))
```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

16:     function balanceOf(address account) external view returns (uint256);

```
([16](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L16-L16))
```solidity
File: contracts/types/LeftRight.sol

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

279:     function addCapped(
             LeftRightUnsigned x,
             LeftRightUnsigned dx,
             LeftRightUnsigned y,
             LeftRightUnsigned dy
         ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {

279:     function addCapped(
             LeftRightUnsigned x,
             LeftRightUnsigned dx,
             LeftRightUnsigned y,
             LeftRightUnsigned dy
         ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {

```
([39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L39-L39),[46](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L46-L46),[59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L59-L62),[78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L78-L81),[101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L101-L101),[108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L108-L108),[121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L121-L124),[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L134-L134),[279](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L279-L284),[279](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L279-L284))
```solidity
File: contracts/types/LiquidityChunk.sol

70:     function createChunk(
            int24 _tickLower,
            int24 _tickUpper,
            uint128 amount
        ) internal pure returns (LiquidityChunk) {

89:     function addLiquidity(
            LiquidityChunk self,
            uint128 amount
        ) internal pure returns (LiquidityChunk) {

102:     function addTickLower(
             LiquidityChunk self,
             int24 _tickLower
         ) internal pure returns (LiquidityChunk) {

118:     function addTickUpper(
             LiquidityChunk self,
             int24 _tickUpper
         ) internal pure returns (LiquidityChunk) {

135:     function updateTickLower(
             LiquidityChunk self,
             int24 _tickLower
         ) internal pure returns (LiquidityChunk) {

151:     function updateTickUpper(
             LiquidityChunk self,
             int24 _tickUpper
         ) internal pure returns (LiquidityChunk) {

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```
([70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L70-L74),[89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L89-L92),[102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L102-L105),[118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L118-L121),[135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L135-L138),[151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L151-L154),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L171-L171),[180](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L180-L180),[189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L189-L189))
```solidity
File: contracts/types/TokenId.sol

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

366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

404:     function countLongs(TokenId self) internal pure returns (uint256) {

432:     function countLegs(TokenId self) internal pure returns (uint256) {

464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```
([87](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L87-L87),[96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L96-L96),[108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L108-L108),[118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L118-L118),[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L128-L128),[138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L138-L138),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L148-L148),[158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L158-L158),[169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L169-L169),[183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L183-L183),[193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L193-L193),[205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L205-L209),[221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L221-L225),[240](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L240-L244),[255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L255-L259),[273](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L273-L277),[291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L291-L295),[310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L310-L314),[366](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L366-L366),[404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L404-L404),[432](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L432-L432),[464](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L464-L464))
### <a name="GAS-23"></a>[GAS-23] Nested for loops should be avoided due to high gas costs resulting from O^2 time complexity
In Solidity, avoiding nested for loops is a recommended practice primarily due to the high gas costs associated with them. These loops can lead to quadratic (O^2) time complexity, especially when they iterate over large data sets or perform complex computations. Since every operation in a smart contract consumes gas, and users pay for this gas, optimizing for lower gas usage is crucial. Nested loops, which inherently have higher computational complexity, can significantly increase the gas costs of a contract. To optimize for efficiency, it's advisable to minimize the use of loops, limit their range, and reduce computations within each loop iteration. Alternative patterns like map/filter/reduce might often be cheaper than traditional for loops in terms of gas usage

*There are 5 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

441:         for (uint256 k = 0; k < pLength; ) {
                 TokenId tokenId = positionIdList[k];
     
                 balances[k][0] = TokenId.unwrap(tokenId);
                 balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);
     
                 (
                     LeftRightSigned[4] memory premiaByLeg,
                     uint256[2][4] memory premiumAccumulatorsByLeg
                 ) = _getPremia(
                         tokenId,
                         LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
                         c_user,
                         computeAllPremia,
                         atTick
                     );
     
                 uint256 numLegs = tokenId.countLegs();
                 for (uint256 leg = 0; leg < numLegs; ) {
                     if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
                         bytes32 chunkKey = keccak256(
                             abi.encodePacked(
                                 tokenId.strike(leg),
                                 tokenId.width(leg),
                                 tokenId.tokenType(leg)
                             )
                         );
     
                         LeftRightUnsigned availablePremium = _getAvailablePremium(
                             _getTotalLiquidity(tokenId, leg),
                             s_settledTokens[chunkKey],
                             s_grossPremiumLast[chunkKey],
                             LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
                             premiumAccumulatorsByLeg[leg]
                         );
                         portfolioPremium = portfolioPremium.add(
                             LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
                         );
                     } else {
                         portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
                     }
                     unchecked {
                         ++leg;
                     }
                 }
     
                 unchecked {
                     ++k;
                 }
             }

```
([441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L441-L490))
```solidity
File: contracts/libraries/FeesCalc.sol

51:         for (uint256 k = 0; k < positionIdList.length; ) {
                TokenId tokenId = positionIdList[k];
                uint128 positionSize = userBalance[tokenId].rightSlot();
                uint256 numLegs = tokenId.countLegs();
                for (uint256 leg = 0; leg < numLegs; ) {
                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                        tokenId,
                        leg,
                        positionSize
                    );
    
                    (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
                        atTick,
                        liquidityChunk
                    );
    
                    if (tokenId.isLong(leg) == 0) {
                        unchecked {
                            value0 += int256(amount0);
                            value1 += int256(amount1);
                        }
                    } else {
                        unchecked {
                            value0 -= int256(amount0);
                            value1 -= int256(amount1);
                        }
                    }
    
                    unchecked {
                        ++leg;
                    }
                }
                unchecked {
                    ++k;
                }
            }

```
([51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L51-L86))
```solidity
File: contracts/libraries/PanopticMath.sol

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {
                     TokenId tokenId = positionIdList[i];
                     uint256 numLegs = tokenId.countLegs();
                     for (uint256 leg = 0; leg < numLegs; ++leg) {
                         if (tokenId.isLong(leg) == 1) {
                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
                         }
                     }
                 }

860:             for (uint256 i = 0; i < positionIdList.length; i++) {
                     TokenId tokenId = positionIdList[i];
                     LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
                         if (tokenId.isLong(leg) == 1) {
                             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
                                 storage _settledTokens = settledTokens;
     
                             // calculate amounts to revoke from settled and subtract from haircut req
                             uint256 settled0 = Math.unsafeDivRoundingUp(
                                 uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
                                 uint128(longPremium.rightSlot())
                             );
                             uint256 settled1 = Math.unsafeDivRoundingUp(
                                 uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
                                 uint128(longPremium.leftSlot())
                             );
     
                             bytes32 chunkKey = keccak256(
                                 abi.encodePacked(
                                     tokenId.strike(0),
                                     tokenId.width(0),
                                     tokenId.tokenType(0)
                                 )
                             );
     
                             // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
                             // for the haircut directly to the accumulator
                             settled0 = Math.max(
                                 0,
                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
                             );
                             settled1 = Math.max(
                                 0,
                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
                             );
     
                             _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
                                 LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
                                     uint128(settled1)
                                 )
                             );
                         }
                     }
                 }

```
([781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L781-L789),[860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L860-L904))
```solidity
File: contracts/types/TokenId.sol

507:             for (uint256 i = 0; i < 4; ++i) {
                     if (self.optionRatio(i) == 0) {
                         // final leg in this position identified;
                         // make sure any leg above this are zero as well
                         // (we don't allow gaps eg having legs 1 and 4 active without 2 and 3 is not allowed)
                         if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)
                             revert Errors.InvalidTokenIdParameter(1);
     
                         break; // we are done iterating over potential legs
                     }
     
                     // prevent legs touching the same chunks - all chunks in the position must be discrete
                     uint256 numLegs = self.countLegs();
                     for (uint256 j = i + 1; j < numLegs; ++j) {
                         if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {
                             revert Errors.InvalidTokenIdParameter(6);
                         }
                     }
                     // now validate this ith leg in the position:
     
                     // The width cannot be 0; the minimum is 1
                     if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);
                     // Strike cannot be MIN_TICK or MAX_TICK
                     if (
                         (self.strike(i) == Constants.MIN_V3POOL_TICK) ||
                         (self.strike(i) == Constants.MAX_V3POOL_TICK)
                     ) revert Errors.InvalidTokenIdParameter(4);
     
                     // In the following, we check whether the risk partner of this leg is itself
                     // or another leg in this position.
                     // Handles case where riskPartner(i) != i ==> leg i has a risk partner that is another leg
                     uint256 riskPartnerIndex = self.riskPartner(i);
                     if (riskPartnerIndex != i) {
                         // Ensures that risk partners are mutual
                         if (self.riskPartner(riskPartnerIndex) != i)
                             revert Errors.InvalidTokenIdParameter(3);
     
                         // Ensures that risk partners have 1) the same asset, and 2) the same ratio
                         if (
                             (self.asset(riskPartnerIndex) != self.asset(i)) ||
                             (self.optionRatio(riskPartnerIndex) != self.optionRatio(i))
                         ) revert Errors.InvalidTokenIdParameter(3);
     
                         // long/short status of associated legs
                         uint256 _isLong = self.isLong(i);
                         uint256 isLongP = self.isLong(riskPartnerIndex);
     
                         // token type status of associated legs (call/put)
                         uint256 _tokenType = self.tokenType(i);
                         uint256 tokenTypeP = self.tokenType(riskPartnerIndex);
     
                         // if the position is the same i.e both long calls, short put's etc.
                         // then this is a regular position, not a defined risk position
                         if ((_isLong == isLongP) && (_tokenType == tokenTypeP))
                             revert Errors.InvalidTokenIdParameter(4);
     
                         // if the two token long-types and the tokenTypes are both different (one is a short call, the other a long put, e.g.), this is a synthetic position
                         // A synthetic long or short is more capital efficient than each leg separated because the long+short premia accumulate proportionally
                         // unlike short stranlges, long strangles also cannot be partnered, because there is no reduction in risk (both legs can earn premia simultaneously)
                         if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))
                             revert Errors.InvalidTokenIdParameter(5);
                     }
                 } // end for loop over legs

```
([507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L507-L569))
### <a name="GAS-24"></a>[GAS-24] Nesting `if`-statements is cheaper than using `&&`
Using a double if statement instead of logical AND (&&) can provide similar short-circuiting behavior whereas double if is slightly more efficient.

*There are 13 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

707:                 if (
                         (tokenType == 0 && currentValue1 < oracleValue1) ||
                         (tokenType == 1 && currentValue0 < oracleValue0)

1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1345:                 if (
                          ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1
                          ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1373:                     if (
                              ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1
                              ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

```
([707](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L707-L709),[1060](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1060-L1060),[1345](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1345-L1347),[1373](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1373-L1375))
```solidity
File: contracts/PanopticFactory.sol

224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

```
([224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L224-L224))
```solidity
File: contracts/PanopticPool.sol

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

```
([460](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L460-L460))
```solidity
File: contracts/SemiFungiblePositionManager.sol

787:             if ((itm0 != 0) && (itm1 != 0)) {

```
([787](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L787-L787))
```solidity
File: contracts/libraries/PanopticMath.sol

218:                     if ((below) && (lastObservedTick > entry)) {

704:             if (!(paid0 > balance0 && paid1 > balance1)) {

797:             if (
                     longPremium.rightSlot() < collateralDelta0 &&
                     longPremium.leftSlot() > collateralDelta1

821:             } else if (
                     longPremium.leftSlot() < collateralDelta1 &&
                     longPremium.rightSlot() > collateralDelta0

```
([218](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L218-L218),[704](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L704-L704),[797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L797-L799),[821](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L821-L823))
```solidity
File: contracts/types/TokenId.sol

560:                     if ((_isLong == isLongP) && (_tokenType == tokenTypeP))

566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

```
([560](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L560-L560),[566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L566-L566))
### <a name="GAS-25"></a>[GAS-25] Consider using OpenZeppelin's `EnumerateSet` instead of nested mappings
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).
OpenZeppelin's `EnumerableSet` provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

*There are 6 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))

```
([238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L238-L238),[238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L238-L238),[258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L258-L258))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

66:     mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;

71:     mapping(address owner => mapping(address operator => bool approvedForAll))

```
([66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L66-L66),[71](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L71-L71))
```solidity
File: contracts/tokens/ERC20Minimal.sol

39:     mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;

```
([39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L39-L39))
### <a name="GAS-26"></a>[GAS-26] Shorten the array rather than copying to a new one
Leveraging inline assembly in Solidity provides the ability to directly manipulate the length slot of an array, thereby altering its length without the need to copy the elements to a new array of the desired size. This technique is more gas-efficient as it avoids the computational expense associated with array duplication. However, this method circumvents the type-checking and safety mechanisms of high-level Solidity and should be used judiciously. Always ensure that the array doesn't contain vital data beyond the revised length, as this data will become unreachable yet still consume storage space.

*There are 10 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

437:         balances = new uint256[2][](pLength);

801:         premiasByLeg = new LeftRightSigned[4][](positionIdList.length);

1038:             uint256[2][] memory positionBalanceArray = new uint256[2][](positionIdList.length);

```
([437](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L437-L437),[801](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L801-L801),[1038](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1038-L1038))
```solidity
File: contracts/libraries/PanopticMath.sol

133:             int256[] memory tickCumulatives = new int256[](cardinality + 1);

135:             uint256[] memory timestamps = new uint256[](cardinality + 1);

146:             int256[] memory ticks = new int256[](cardinality);

242:         uint32[] memory secondsAgos = new uint32[](20);

244:         int256[] memory twapMeasurement = new int256[](19);

```
([133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L133-L133),[135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L135-L135),[146](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L146-L146),[242](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L242-L242),[244](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L244-L244))
```solidity
File: contracts/multicall/Multicall.sol

13:         results = new bytes[](data.length);

```
([13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L13-L13))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

182:         balances = new uint256[](owners.length);

```
([182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L182-L182))
### <a name="GAS-27"></a>[GAS-27] Operator `>=`/`<=` costs less gas than operator `>`/`<`
The compiler uses opcodes `GT` and `ISZERO` for code that uses `>`, but only requires `LT` for `>=`. A similar behavior applies for `>`, which uses opcodes `LT` and `ISZERO`, but only requires `GT` for `<=`. It can [save 3 gas](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde) for each. It should be converted to the `<=`/`>=` equivalent when comparing against integer literals.

*There are 152 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) 

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

709:                     (tokenType == 1 && currentValue0 < oracleValue0)

776:         if (utilization < 0) {

784:         if (uint256(utilization) < TARGET_POOL_UTIL) {

790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {

835:         if (utilization < TARGET_POOL_UTIL) {

841:         if (utilization > SATURATED_POOL_UTIL) {

937:         if (shares > delegateeBalance) {

976:         if (assets > 0) {

1010:             if (tokenToPay > 0) {

1018:             } else if (tokenToPay < 0) {

1067:             if (tokenToPay > 0) {

1075:             } else if (tokenToPay < 0) {

1168:         if (positionBalanceArray.length > 0) {

1173:             if (premiumAllPositions < 0) {

1182:         if (premiumAllPositions > 0) {

1208:         for (uint256 i = 0; i < totalIterations; ) {

1255:             for (uint256 index = 0; index < numLegs; ++index) {

1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1545:                     spreadRequirement = movedRight < movedPartnerRight

1549:                     spreadRequirement = movedLeft < movedPartnerLeft

1570:                 spreadRequirement = (notional < notionalP)

```
([418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L418-L418),[480](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L480-L480),[536](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L536-L536),[596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L596-L596),[662](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L662-L662),[708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L708-L708),[709](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L709-L709),[776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L776-L776),[784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L784-L784),[790](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L790-L790),[835](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L835-L835),[841](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L841-L841),[937](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L937-L937),[976](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L976-L976),[1010](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1010-L1010),[1018](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1018-L1018),[1067](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1067-L1067),[1075](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1075-L1075),[1168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1168-L1168),[1173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1173-L1173),[1182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1182-L1182),[1208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1208-L1208),[1255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1255-L1255),[1347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1347-L1347),[1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1374-L1374),[1545](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1545-L1545),[1549](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1549-L1549),[1570](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1570-L1570))
```solidity
File: contracts/PanopticFactory.sol

181:         if (amount0Owed > 0)

188:         if (amount1Owed > 0)

217:         (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);

303:         for (; uint256(salt) < maxSalt; ) {

308:             if (rarity > highestRarity) {

378:                 fullRangeLiquidity = liquidity0 > liquidity1 ? liquidity0 : liquidity1;

```
([181](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L181-L181),[188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L188-L188),[217](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L217-L217),[303](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L303-L303),[308](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L308-L308),[378](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L378-L378))
```solidity
File: contracts/PanopticPool.sol

441:         for (uint256 k = 0; k < pLength; ) {

459:             for (uint256 leg = 0; leg < numLegs; ) {

510:         if (tickLimitLow < tickLimitHigh) {

745:         for (uint256 leg = 0; leg < numLegs; ) {

802:         for (uint256 i = 0; i < positionIdList.length; ) {

864:         for (uint256 leg = 0; leg < numLegs; ) {

943:         if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

1035:             if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

1274:         if (positionIdListExercisor.length > 0)

1382:         for (uint256 i = 0; i < pLength; ) {

1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

1492:         if (effectiveLiquidityFactorX32 > uint256(effectiveLiquidityLimitX32))

1518:         for (uint256 leg = 0; leg < numLegs; ) {

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1672:         for (uint256 leg = 0; leg < numLegs; ++leg) {

1852:         for (uint256 leg = 0; leg < numLegs; ) {

```
([441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L441-L441),[459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L459-L459),[510](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L510-L510),[745](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L745-L745),[802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L802-L802),[864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L864-L864),[943](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L943-L943),[1035](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1035-L1035),[1274](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1274-L1274),[1382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1382-L1382),[1415](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1415-L1415),[1492](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1492-L1492),[1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1518-L1518),[1596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1596-L1596),[1672](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1672-L1672),[1852](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1852-L1852))
```solidity
File: contracts/SemiFungiblePositionManager.sol

412:         if (amount0Owed > 0)

419:         if (amount1Owed > 0)

446:         address token = amount0Delta > 0

453:         uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);

575:         for (uint256 i = 0; i < ids.length; ) {

601:         for (uint256 leg = 0; leg < numLegs; ) {

715:         if (tickLimitLow > tickLimitHigh) {

819:                 zeroForOne = net0 < 0;

824:                 zeroForOne = itm0 < 0;

827:                 zeroForOne = itm1 > 0;

882:         for (uint256 leg = 0; leg < numLegs; ) {

939:         if (amount0 > uint128(type(int128).max) || amount1 > uint128(type(int128).max))

939:         if (amount0 > uint128(type(int128).max) || amount1 > uint128(type(int128).max))

1013:                 if (startingLiquidity < chunkLiquidity) {

1085:         if (currentLiquidity.rightSlot() > 0) {

1296:                 collected0 = movedInLeg.rightSlot() < 0

1299:                 collected1 = movedInLeg.leftSlot() < 0

1465:         if (atTick < type(int24).max) {

```
([412](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L412-L412),[419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L419-L419),[446](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L446-L446),[453](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L453-L453),[575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L575-L575),[601](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L601-L601),[715](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L715-L715),[819](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L819-L819),[824](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L824-L824),[827](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L827-L827),[882](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L882-L882),[939](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L939-L939),[939](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L939-L939),[1013](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1013-L1013),[1085](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1085-L1085),[1296](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1296-L1296),[1299](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1299-L1299),[1465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1465-L1465))
```solidity
File: contracts/libraries/FeesCalc.sol

51:         for (uint256 k = 0; k < positionIdList.length; ) {

55:             for (uint256 leg = 0; leg < numLegs; ) {

147:             if (currentTick < tickLower) {

```
([51](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L51-L51),[55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L55-L55),[147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L147-L147))
```solidity
File: contracts/libraries/Math.sol

26:         return a < b ? a : b;

34:         return a > b ? a : b;

42:         return a < b ? a : b;

50:         return a < b ? a : b;

58:         return a > b ? a : b;

66:         return a > b ? a : b;

74:         return x > 0 ? x : -x;

83:             return x > 0 ? uint256(x) : uint256(-x);

130:             uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));

131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

326:         if (toCast > uint256(type(int256).max)) revert Errors.CastingError();

361:                 require(denominator > 0);

370:             require(denominator > prod1);

447:             if (mulmod(a, b, denominator) > 0) {

448:                 require(result < type(uint256).max);

484:             require(2 ** 64 > prod1);

547:             require(2 ** 96 > prod1);

587:             if (mulmod(a, b, 2 ** 96) > 0) {

588:                 require(result < type(uint256).max);

624:             require(2 ** 128 > prod1);

664:             if (mulmod(a, b, 2 ** 128) > 0) {

665:                 require(result < type(uint256).max);

701:             require(2 ** 192 > prod1);

759:             while (i < j) {

760:                 while (arr[uint256(i)] < pivot) i++;

761:                 while (pivot < arr[uint256(j)]) j--;

768:             if (left < j) quickSort(arr, left, j);

769:             if (i < right) quickSort(arr, i, right);

```
([26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L26-L26),[34](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L34-L34),[42](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L42-L42),[50](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L50-L50),[58](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L58-L58),[66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L66-L66),[74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L74-L74),[83](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L83-L83),[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L130-L130),[131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L131-L131),[176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L176-L176),[312](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L312-L312),[326](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L326-L326),[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L361-L361),[370](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L370-L370),[447](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L447-L447),[448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L448-L448),[484](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L484-L484),[547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L547-L547),[587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L587-L587),[588](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L588-L588),[624](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L624-L624),[664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L664-L664),[665](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L665-L665),[701](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L701-L701),[759](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L759-L759),[760](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L760-L760),[761](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L761-L761),[768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L768-L768),[769](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L769-L769))
```solidity
File: contracts/libraries/PanopticMath.sol

137:             for (uint256 i = 0; i < cardinality + 1; ++i) {

148:             for (uint256 i = 0; i < cardinality; ++i) {

207:                 for (uint8 i; i < 8; ++i) {

218:                     if ((below) && (lastObservedTick > entry)) {

248:             for (uint256 i = 0; i < 20; ++i) {

256:             for (uint256 i = 0; i < 19; ++i) {

359:                 tickLower < minTick ||

360:                 tickUpper > maxTick

395:         for (uint256 leg = 0; leg < numLegs; ) {

479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

494:             if (sqrtPriceX96 < type(uint128).max) {

511:             if (sqrtPriceX96 < type(uint128).max) {

528:             if (sqrtPriceX96 < type(uint128).max) {

532:                 return amount < 0 ? -absResult : absResult;

537:                 return amount < 0 ? -absResult : absResult;

551:             if (sqrtPriceX96 < type(uint128).max) {

555:                 return amount < 0 ? -absResult : absResult;

564:                 return amount < 0 ? -absResult : absResult;

704:             if (!(paid0 > balance0 && paid1 > balance1)) {

704:             if (!(paid0 > balance0 && paid1 > balance1)) {

706:                 if ((paid0 > balance0)) {

724:                 if ((paid1 > balance1)) {

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {

798:                 longPremium.rightSlot() < collateralDelta0 &&

799:                 longPremium.leftSlot() > collateralDelta1

822:                 longPremium.leftSlot() < collateralDelta1 &&

823:                 longPremium.rightSlot() > collateralDelta0

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

931:             if (balanceShortage > 0) {

949:             if (balanceShortage > 0) {

```
([137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L137-L137),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L148-L148),[207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L207-L207),[218](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L218-L218),[248](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L248-L248),[256](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L256-L256),[359](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L359-L359),[360](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L360-L360),[395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L395-L395),[479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L479-L479),[494](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L494-L494),[511](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L511-L511),[528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L528-L528),[532](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L532-L532),[537](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L537-L537),[551](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L551-L551),[555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L555-L555),[564](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L564-L564),[704](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L704-L704),[704](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L704-L704),[706](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L706-L706),[724](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L724-L724),[781](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L781-L781),[784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L784-L784),[798](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L798-L798),[799](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L799-L799),[822](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L822-L822),[823](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L823-L823),[860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L860-L860),[863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L863-L863),[931](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L931-L931),[949](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L949-L949))
```solidity
File: contracts/multicall/Multicall.sol

14:         for (uint256 i = 0; i < data.length; ) {

```
([14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L14-L14))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {

```
([143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L143-L143),[187](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L187-L187))
```solidity
File: contracts/types/LeftRight.sol

161:                 LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||

162:                 (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))

184:                 LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||

185:                 (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))

```
([161](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L161-L161),[162](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L162-L162),[184](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L184-L184),[185](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L185-L185))
```solidity
File: contracts/types/TokenId.sol

376:             if (optionRatios < 2 ** 64) {

378:             } else if (optionRatios < 2 ** 112) {

380:             } else if (optionRatios < 2 ** 160) {

382:             } else if (optionRatios < 2 ** 208) {

439:         if (optionRatios < 2 ** 64) {

441:         } else if (optionRatios < 2 ** 112) {

443:         } else if (optionRatios < 2 ** 160) {

445:         } else if (optionRatios < 2 ** 208) 

507:             for (uint256 i = 0; i < 4; ++i) {

520:                 for (uint256 j = i + 1; j < numLegs; ++j) {

581:             for (uint256 i = 0; i < numLegs; ++i) {

589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {

```
([376](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L376-L376),[378](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L378-L378),[380](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L380-L380),[382](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L382-L382),[439](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L439-L439),[441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L441-L441),[443](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L443-L443),[445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L445-L445),[507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L507-L507),[520](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L520-L520),[581](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L581-L581),[589](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L589-L589))
### <a name="GAS-28"></a>[GAS-28] Functions that revert when called by normal users can be marked as `payable`(Not captured by 4nalyzer)
If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. The extra opcodes avoided are: `CALLVALUE(2), DUP1(3), ISZERO(3), PUSH2(3), JUMPI(10), PUSH1(3), DUP1(3), REVERT(0), JUMPDEST(1), POP(2)` which cost an average of about 21 gas per call to the function, in addition to the extra deployment cost.

*There are 4 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

864:     function delegate(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {


911:     function revoke(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {


995:     function takeCommissionAddData(
             address optionOwner,
             int128 longAmount,
             int128 shortAmount,
             int128 swappedAmount
         ) external onlyPanopticPool returns (int256 utilization) {

1043:     function exercise(
              address optionOwner,
              int128 longAmount,
              int128 shortAmount,
              int128 swappedAmount,
              int128 realizedPremium
          ) external onlyPanopticPool returns (int128) {

```
([864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L864-L868),[911](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L911-L915),[995](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L995-L1000),[1043](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1043-L1049))

### <a name="GAS-29"></a>[GAS-29] Using `private` for constants saves gas
If needed, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that [returns a tuple](https://github.com/code-423n4/2022-08-frax/blob/90f55a9ce4e25bceed3a74290b854341d8de6afa/src/contracts/FraxlendPair.sol#L156-L178) of the values of all currently-public constants. Saves **3406-3606 gas** in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table

*There are 48 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

70:     string internal constant TICKER_PREFIX = "po";

73:     string internal constant NAME_PREFIX = "POPT-V1";

77:     uint256 internal constant DECIMALS = 10_000;

81:     int128 internal constant DECIMALS_128 = 10_000;

```
([70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L70-L70),[73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L73-L73),[77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L77-L77),[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L81-L81))
```solidity
File: contracts/PanopticFactory.sol

82:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;

86:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

89:     uint16 internal constant CARDINALITY_INCREASE = 100;

```
([82](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L82-L82),[86](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L86-L86),[89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L89-L89))
```solidity
File: contracts/PanopticPool.sol

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
([103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L103-L103),[105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L105-L105),[109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L109-L109),[111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L111-L111),[114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L114-L114),[119](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L119-L119),[120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L120-L120),[123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L123-L123),[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L128-L128),[133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L133-L133),[136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L136-L136),[139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L139-L139),[145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L145-L145),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L148-L148),[152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L152-L152),[156](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L156-L156),[160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L160-L160),[165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L165-L165),[168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L168-L168),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L171-L171),[174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L174-L174))
```solidity
File: contracts/SemiFungiblePositionManager.sol

125:     bool internal constant MINT = false;

126:     bool internal constant BURN = true;

```
([125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L125-L125),[126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L126-L126))
```solidity
File: contracts/libraries/Constants.sol

9:     uint256 internal constant FP96 = 0x1000000000000000000000000;

12:     int24 internal constant MIN_V3POOL_TICK = -887272;

15:     int24 internal constant MAX_V3POOL_TICK = 887272;

18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

21:     uint160 internal constant MAX_V3POOL_SQRT_RATIO =
            1461446703485210103287273052203988822378723970342;

```
([9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L9-L9),[12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L12-L12),[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L15-L15),[18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L18-L18),[21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L21-L22))
```solidity
File: contracts/libraries/Math.sol

15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
([15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L15-L15))
```solidity
File: contracts/libraries/PanopticMath.sol

23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

26:     uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

```
([23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L23-L23),[26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L26-L26))
```solidity
File: contracts/types/LeftRight.sol

22:     uint256 internal constant LEFT_HALF_BIT_MASK =
            0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000;

26:     int256 internal constant LEFT_HALF_BIT_MASK_INT =
            int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

30:     int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```
([22](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L22-L23),[26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L26-L27),[30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L30-L30))
```solidity
File: contracts/types/LiquidityChunk.sol

54:     uint256 internal constant CLEAR_TL_MASK =
            0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

58:     uint256 internal constant CLEAR_TU_MASK =
            0xFFFFFF000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```
([54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L54-L55),[58](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L58-L59))
```solidity
File: contracts/types/TokenId.sol

62:     uint256 internal constant LONG_MASK =
            0x100_000000000100_000000000100_000000000100_0000000000000000;

66:     uint256 internal constant CLEAR_POOLID_MASK =
            0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF_0000000000000000;

70:     uint256 internal constant OPTION_RATIO_MASK =
            0x0000000000FE_0000000000FE_0000000000FE_0000000000FE_0000000000000000;

74:     uint256 internal constant CHUNK_MASK =
            0xFFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_0000000000000000;

78:     int256 internal constant BITMASK_INT24 = 0xFFFFFF;

```
([62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L62-L63),[66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L66-L67),[70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L70-L71),[74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L74-L75),[78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L78-L78))
### <a name="GAS-30"></a>[GAS-30] Private functions used once can be inlined
Private functions which are only called once can be inlined to save GAS.

*There are 1 Instance of this issue* :
```solidity
File: contracts/SemiFungiblePositionManager.sol

1110:     function _updateStoredPremia(
              bytes32 positionKey,
              LeftRightUnsigned currentLiquidity,
              LeftRightUnsigned collectedAmounts
          ) private {

```
([1110](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1110-L1114))
### <a name="GAS-31"></a>[GAS-31] Refactor modifiers to call a local function
Modifiers code is copied in all instances where it's used, increasing bytecode size. By doing a refractor to the internal function, one can reduce bytecode size significantly at the cost of one JUMP.

*There are 2 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

169:     modifier onlyPanopticPool() {
             if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();
             _;
         

```
([169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L169-L172))
```solidity
File: contracts/SemiFungiblePositionManager.sol

305:     modifier ReentrancyLock(uint64 poolId) {
             // check if the pool is already locked
             // init lock if not
             beginReentrancyLock(poolId);
     
             // execute function
             _;
     
             // remove lock
             endReentrancyLock(poolId);
         }

```
([305](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L305-L315))
### <a name="GAS-32"></a>[GAS-32] Default bool values are manually reset
Using .delete is better than resetting a Solidity variable to its default value manually because it frees up storage space on the Ethereum blockchain, resulting in gas cost savings.

*There are 2 Instances of this issue* :
```solidity
File: contracts/SemiFungiblePositionManager.sol

332:         s_poolContext[poolId].locked = false;

```
([332](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L332-L332))
```solidity
File: contracts/libraries/PanopticMath.sol

220:                         below = false;

```
([220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L220-L220))

### <a name="GAS-33"></a>[GAS-33] Use shift right/left instead of division if possible(Not captured by 4nalyzer)
While the `DIV` opcode uses 5 gas, the `SHR` / `SHL` opcode only uses 3 gas. Furthermore, beware that Solidity's division operation also includes a division-by-0 prevention which is bypassed using shifting. Eventually, overflow checks are never performed for shift operations as they are done for arithmetic operations. Instead, the result is always truncated, so the calculation can be unchecked in Solidity version `0.8+`
- Use `>> 1` instead of `/ 2`
- Use `>> 2` instead of `/ 4`
- Use `<< 3` instead of `* 8`
- ...
- Use `>> 5` instead of `/ 2^5 == / 32`
- Use `<< 6` instead of `* 2^6 == * 64`

TL;DR:
- Shifting left by N is like multiplying by 2^N (Each bits to the left is an increased power of 2)
- Shifting right by N is like dividing by 2^N (Each bits to the right is a decreased power of 2)

*Saves around 2 gas + 20 for unchecked per instance*

*There are 27 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

203:                     (12500 * ratioTick) /
                         10_000 +

205:                     (7812 * ratioTick ** 2) /
                         10_000 ** 2 +

207:                     (6510 * ratioTick ** 3) /
                         10_000 ** 3

249:             _poolFee = fee / 100;

262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

731:                 .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))

732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

743:             return int256((s_inAMM * DECIMALS) / totalAssets());

778:                 min_sell_ratio /= 2;

797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);



849:                 (BUYER_COLLATERAL_RATIO +
                         (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
                         (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2



```
([203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L203-L204),[205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L205-L206),[207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L207-L208),[249](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L249-L249),[262](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L262-L262),[446](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L446-L446),[677](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L677-L677),[731](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L731-L731),[732](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L732-L732),[743](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L743-L743),[778](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L778-L778),[797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L797-L798),[849](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L849-L851))
```solidity
File: contracts/PanopticFactory.sol

392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```
([392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L392-L392))
```solidity
File: contracts/PanopticPool.sol




1729:                                 (grossCurrent[0] *
                                          positionLiquidity +
                                          grossPremiumLast.rightSlot() *
                                          totalLiquidityBefore) / (totalLiquidity)

1737:                                 (grossCurrent[1] *
                                          positionLiquidity +
                                          grossPremiumLast.leftSlot() *
                                          totalLiquidityBefore) / (totalLiquidity)




1779:                                 (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /
                                          (accumulated0 == 0 ? type(uint256).max : accumulated0),

1788:                                 (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /
                                          (accumulated1 == 0 ? type(uint256).max : accumulated1),

```
([1729](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1729-L1732),[1737](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1737-L1740),[1779](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1779-L1780),[1788](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1788-L1789))

```solidity
File: contracts/libraries/Math.sol

176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

196:                 mulDiv(
                         uint256(liquidityChunk.liquidity()) << 96,
                         highPriceX96 - lowPriceX96,
                         highPriceX96
                     ) / lowPriceX96;

```
([176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L176-L176),[196](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L196-L200))

```solidity
File: contracts/libraries/PanopticMath.sol

150:                     (tickCumulatives[i] - tickCumulatives[i + 1]) /
                         int256(timestamps[i] - timestamps[i + 1]);


195:                         (tickCumulative_last - tickCumulative_old) /
                                 int256(timestamp_last - timestamp_old)

249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);

258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))


346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

669:                 uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);

```
([150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L150-L151),[195](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L195-L196),[249](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L249-L249),[258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L258-L258),[346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L346-L346),[347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L347-L347),[669](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L669-L669))
### <a name="GAS-34"></a>[GAS-34] Usage of smaller `uint`/`int` types causes overhead
When using a smaller int/uint type it first needs to be converted to it's 258 bit counterpart to be operated, this increases the gass cost and thus should be avoided. However it does make sense to use smaller int/uint values within structs provided you pack the struct properly.

*There are 341 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

81:     int128 internal constant DECIMALS_128 = 10_000;

112:     uint128 internal s_poolAssets;

115:     uint128 internal s_inAMM;

121:     uint128 internal s_ITMSpreadFee;

124:     uint24 internal s_poolFee;

225:         uint24 fee,

247:         uint24 _poolFee;

310:     function decimals() external view returns (uint8) {

651:         int24 currentTick,

652:         int24 oracleTick,

654:         uint128 positionBalance,

667:                     int24 range = int24(

997:         int128 longAmount,

998:         int128 shortAmount,

999:         int128 swappedAmount

1045:         int128 longAmount,

1046:         int128 shortAmount,

1047:         int128 swappedAmount,

1048:         int128 realizedPremium

1049:     ) external onlyPanopticPool returns (int128) {

1097:         int128 longAmount,

1098:         int128 shortAmount,

1099:         int128 swappedAmount

1143:         int24 currentTick,

1145:         int128 premiumAllPositions

1161:         int24 atTick,

1163:         int128 premiumAllPositions

1201:         int24 atTick,

1213:             uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();

1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

1247:         uint128 positionSize,

1248:         int24 atTick,

1249:         uint128 poolUtilization

1281:         uint128 positionSize,

1282:         int24 atTick,

1283:         uint128 poolUtilization

1314:         uint128 positionSize,

1315:         int24 atTick,

1316:         uint128 poolUtilization

1325:         uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();

1328:         int64 utilization = tokenType == 0

1342:                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(index);

1352:                     int24 strike = tokenId.strike(index);

1362:                     uint160 ratio = tokenType == 1 // tokenType

1408:                         uint160 scaleFactor = Math.getSqrtRatioAtTick(

1442:         uint128 positionSize,

1443:         int24 atTick,

1444:         uint128 poolUtilization

1474:         uint128 amount,

1512:         uint128 positionSize,

1515:         uint128 poolUtilization

1528:         uint128 movedRight = amountsMoved.rightSlot();

1529:         uint128 movedLeft = amountsMoved.leftSlot();

1532:         uint128 movedPartnerRight = amountsMovedPartner.rightSlot();

1533:         uint128 movedPartnerLeft = amountsMovedPartner.leftSlot();

1558:                 uint128 contracts;

1603:         uint128 positionSize,

1604:         int24 atTick,

1605:         uint128 poolUtilization

1631:             uint64 poolUtilization0 = uint64(poolUtilization);

1632:             uint64 poolUtilization1 = uint64(poolUtilization >> 64);

```
([81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L81-L81),[112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L112-L112),[115](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L115-L115),[121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L121-L121),[124](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L124-L124),[225](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L225-L225),[247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L247-L247),[310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L310-L310),[651](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L651-L651),[652](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L652-L652),[654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L654-L654),[667](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L667-L667),[997](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L997-L997),[998](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L998-L998),[999](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L999-L999),[1045](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1045-L1045),[1046](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1046-L1046),[1047](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1047-L1047),[1048](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1048-L1048),[1049](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1049-L1049),[1097](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1097-L1097),[1098](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1098-L1098),[1099](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1099-L1099),[1143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1143-L1143),[1145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1145-L1145),[1161](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1161-L1161),[1163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1163-L1163),[1201](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1201-L1201),[1213](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1213-L1213),[1216](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1216-L1216),[1247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1247-L1247),[1248](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1248-L1248),[1249](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1249-L1249),[1281](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1281-L1281),[1282](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1282-L1282),[1283](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1283-L1283),[1314](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1314-L1314),[1315](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1315-L1315),[1316](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1316-L1316),[1325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1325-L1325),[1328](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1328-L1328),[1342](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1342-L1342),[1352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1352-L1352),[1362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1362-L1362),[1408](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1408-L1408),[1442](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1442-L1442),[1443](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1443-L1443),[1444](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1444-L1444),[1474](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1474-L1474),[1512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1512-L1512),[1515](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1515-L1515),[1528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1528-L1528),[1529](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1529-L1529),[1532](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1532-L1532),[1533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1533-L1533),[1558](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1558-L1558),[1603](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1603-L1603),[1604](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1604-L1604),[1605](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1605-L1605),[1631](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1631-L1631),[1632](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1632-L1632))
```solidity
File: contracts/PanopticFactory.sol

89:     uint16 internal constant CARDINALITY_INCREASE = 100;

213:         uint24 fee,

339:         uint24 fee

341:         (uint160 currentSqrtPriceX96, , , , , , ) = v3Pool.slot0();

348:         uint128 fullRangeLiquidity;

365:                 uint128 liquidity0 = uint128(

368:                 uint128 liquidity1 = uint128(

388:         int24 tickLower;

389:         int24 tickUpper;

391:             int24 tickSpacing = v3Pool.tickSpacing();

```
([89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L89-L89),[213](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L213-L213),[339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L339-L339),[341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L341-L341),[348](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L348-L348),[365](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L365-L365),[368](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L368-L368),[388](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L388-L388),[389](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L389-L389),[391](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L391-L391))
```solidity
File: contracts/PanopticPool.sol

77:         uint128 positionSize,

92:         uint128 positionSize,

94:         uint128 poolUtilizations

103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

128:     uint32 internal constant TWAP_WINDOW = 600;

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

168:     uint64 internal constant MAX_POSITIONS = 32;

304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

338:     function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {

339:         (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();

355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

387:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

412:         int24 atTick,

434:         int24 atTick

500:         int24 tickLimitLow,

501:         int24 tickLimitHigh

502:     ) internal pure returns (int24, int24) {

523:         (, , uint16 observationIndex, uint16 observationCardinality, , , ) = s_univ3pool.slot0();

549:         uint128 positionSize,

550:         uint64 effectiveLiquidityLimitX32,

551:         int24 tickLimitLow,

552:         int24 tickLimitHigh

572:         int24 tickLimitLow,

573:         int24 tickLimitHigh

589:         int24 tickLimitLow,

590:         int24 tickLimitHigh

616:         uint128 positionSize,

617:         uint64 effectiveLiquidityLimitX32,

618:         int24 tickLimitLow,

619:         int24 tickLimitHigh

642:         uint128 poolUtilizations = _mintInSFPMAndUpdateCollateral(

679:         uint128 positionSize,

680:         int24 tickLimitLow,

681:         int24 tickLimitHigh

682:     ) internal returns (uint128) {

693:         uint128 poolUtilizations = _payCommissionAndWriteData(tokenId, positionSize, totalSwapped);

708:         uint128 positionSize,

710:     ) internal returns (uint128) {

739:     function _addUserOption(TokenId tokenId, uint64 effectiveLiquidityLimitX32) internal {

748:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);

751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

796:         int24 tickLimitLow,

797:         int24 tickLimitHigh,

830:         int24 tickLimitLow,

831:         int24 tickLimitHigh

836:         uint128 positionSize = s_positionBalance[owner][tokenId].rightSlot();

867:                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);

898:             int24 currentTick,

899:             uint16 observationIndex,

900:             uint16 observationCardinality,

905:         int24 fastOracleTick = PanopticMath.computeMedianObservedPrice(

913:         int24 slowOracleTick;

957:         int24 tickLimitLow,

958:         int24 tickLimitHigh,

960:         uint128 positionSize,

985:             int128 paid0 = s_collateralToken0.exercise(

996:             int128 paid1 = s_collateralToken1.exercise(

1026:         int24 twapTick = getUniV3TWAP();

1032:             (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

1077:         int24 finalTick;

1119:             int24 _finalTick = finalTick;

1193:         uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();

1200:         int24 twapTick = getUniV3TWAP();

1202:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

1293:         int24 currentTick,

1294:         int24 atTick,

1342:         uint160 sqrtPriceX96

1450:     function getUniV3TWAP() internal view returns (int24 twapTick) {

1468:         int24 tickLower,

1469:         int24 tickUpper,

1470:         uint64 effectiveLiquidityLimitX32

1480:         uint128 netLiquidity = accountLiquidities.rightSlot();

1481:         uint128 totalLiquidity = accountLiquidities.leftSlot();

1505:         uint128 positionSize,

1508:         int24 atTick

1598:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

1602:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);

1605:             (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

1669:         uint128 positionSize

1809:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);

1837:         uint128 positionSize,

```
([77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L77-L77),[92](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L92-L92),[94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L94-L94),[103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L103-L103),[105](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L105-L105),[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L128-L128),[165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L165-L165),[168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L168-L168),[304](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L304-L304),[338](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L338-L338),[339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L339-L339),[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L355-L355),[385](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L385-L385),[387](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L387-L387),[412](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L412-L412),[434](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L434-L434),[500](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L500-L500),[501](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L501-L501),[502](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L502-L502),[523](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L523-L523),[549](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L549-L549),[550](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L550-L550),[551](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L551-L551),[552](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L552-L552),[572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L572-L572),[573](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L573-L573),[589](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L589-L589),[590](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L590-L590),[616](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L616-L616),[617](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L617-L617),[618](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L618-L618),[619](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L619-L619),[642](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L642-L642),[679](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L679-L679),[680](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L680-L680),[681](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L681-L681),[682](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L682-L682),[693](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L693-L693),[708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L708-L708),[710](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L710-L710),[739](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L739-L739),[748](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L748-L748),[751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L751-L751),[796](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L796-L796),[797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L797-L797),[830](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L830-L830),[831](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L831-L831),[836](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L836-L836),[867](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L867-L867),[898](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L898-L898),[899](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L899-L899),[900](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L900-L900),[905](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L905-L905),[913](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L913-L913),[957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L957-L957),[958](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L958-L958),[960](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L960-L960),[985](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L985-L985),[996](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L996-L996),[1026](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1026-L1026),[1032](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1032-L1032),[1077](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1077-L1077),[1119](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1119-L1119),[1193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1193-L1193),[1200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1200-L1200),[1202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1202-L1202),[1293](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1293-L1293),[1294](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1294-L1294),[1342](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1342-L1342),[1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1450-L1450),[1468](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1468-L1468),[1469](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1469-L1469),[1470](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1470-L1470),[1480](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1480-L1480),[1481](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1481-L1481),[1505](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1505-L1505),[1508](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1508-L1508),[1598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1598-L1598),[1602](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1602-L1602),[1605](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1605-L1605),[1669](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1669-L1669),[1809](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1809-L1809),[1837](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1837-L1837))
```solidity
File: contracts/SemiFungiblePositionManager.sol

80:     event PoolInitialized(address indexed uniswapPool, uint64 poolId);

90:         uint128 positionSize

101:         uint128 positionSize

133:     uint128 private constant VEGOID = 2;

305:     modifier ReentrancyLock(uint64 poolId) {

320:     function beginReentrancyLock(uint64 poolId) internal {

330:     function endReentrancyLock(uint64 poolId) internal {

350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

367:         uint64 poolId = PanopticMath.getPoolId(univ3pool);

473:         uint128 positionSize,

474:         int24 slippageTickLimitLow,

475:         int24 slippageTickLimitHigh

506:         uint128 positionSize,

507:         int24 slippageTickLimitLow,

508:         int24 slippageTickLimitHigh

682:         uint128 positionSize,

683:         int24 tickLimitLow,

684:         int24 tickLimitHigh,

725:         (, int24 currentTick, , , , , ) = univ3pool.slot0();

769:             int128 itm0 = itmAmounts.rightSlot();

770:             int128 itm1 = itmAmounts.leftSlot();

788:                 (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

866:         uint128 positionSize,

892:                 uint128 _positionSize = positionSize;

986:         uint128 updatedLiquidity;

995:             uint128 startingLiquidity = currentLiquidity.rightSlot();

996:             uint128 removedLiquidity = currentLiquidity.leftSlot();

997:             uint128 chunkLiquidity = liquidityChunk.liquidity();

1140:         uint128 liquidity,

1263:         uint128 startingLiquidity = currentLiquidity.rightSlot();

1284:             (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(

1293:             uint128 collected0;

1294:             uint128 collected1;

1346:                 uint128 collected0 = collectedAmounts.rightSlot();

1347:                 uint128 collected1 = collectedAmounts.leftSlot();

1363:                 uint128 premium0X64_owed;

1364:                 uint128 premium1X64_owed;

1384:                 uint128 premium0X64_gross;

1385:                 uint128 premium1X64_gross;

1425:         int24 tickLower,

1426:         int24 tickUpper

1453:         int24 tickLower,

1454:         int24 tickUpper,

1455:         int24 atTick,

1457:     ) external view returns (uint128, uint128) {

1468:             uint128 netLiquidity = accountLiquidities.rightSlot();

1473:                     int24 _tickLower = tickLower;

1474:                     int24 _tickUpper = tickUpper;

1539:         int24 tickLower,

1540:         int24 tickUpper

1541:     ) external view returns (int128 feesBase0, int128 feesBase1) {

1556:         uint64 poolId

1566:     function getPoolId(address univ3pool) external view returns (uint64 poolId) {

```
([80](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L80-L80),[90](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L90-L90),[101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L101-L101),[133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L133-L133),[305](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L305-L305),[320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L320-L320),[330](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L330-L330),[350](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350-L350),[367](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L367-L367),[473](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L473-L473),[474](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L474-L474),[475](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L475-L475),[506](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L506-L506),[507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L507-L507),[508](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L508-L508),[682](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L682-L682),[683](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L683-L683),[684](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L684-L684),[725](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L725-L725),[769](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L769-L769),[770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L770-L770),[788](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L788-L788),[866](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L866-L866),[892](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L892-L892),[986](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L986-L986),[995](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L995-L995),[996](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L996-L996),[997](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L997-L997),[1140](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1140-L1140),[1263](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1263-L1263),[1284](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1284-L1284),[1293](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1293-L1293),[1294](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1294-L1294),[1346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1346-L1346),[1347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1347-L1347),[1363](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1363-L1363),[1364](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1364-L1364),[1384](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1384-L1384),[1385](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1385-L1385),[1425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1425-L1425),[1426](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1426-L1426),[1453](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1453-L1453),[1454](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1454-L1454),[1455](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1455-L1455),[1457](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1457-L1457),[1468](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1468-L1468),[1473](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1473-L1473),[1474](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1474-L1474),[1539](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1539-L1539),[1540](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1540-L1540),[1541](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1541-L1541),[1556](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1556-L1556),[1566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1566-L1566))
```solidity
File: contracts/libraries/Constants.sol

12:     int24 internal constant MIN_V3POOL_TICK = -887272;

15:     int24 internal constant MAX_V3POOL_TICK = 887272;

18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;

21:     uint160 internal constant MAX_V3POOL_SQRT_RATIO =
            1461446703485210103287273052203988822378723970342;

```
([12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L12-L12),[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L15-L15),[18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L18-L18),[21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L21-L22))
```solidity
File: contracts/libraries/FeesCalc.sol

47:         int24 atTick,

53:             uint128 positionSize = userBalance[tokenId].rightSlot();

99:         int24 currentTick,

100:         int24 tickLower,

101:         int24 tickUpper,

102:         uint128 liquidity

132:         int24 currentTick,

133:         int24 tickLower,

134:         int24 tickUpper

```
([47](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L47-L47),[53](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L53-L53),[99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L99-L99),[100](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L100-L100),[101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L101-L101),[102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L102-L102),[132](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L132-L132),[133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L133-L133),[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L134-L134))
```solidity
File: contracts/libraries/InteractionHelper.sol

52:         uint24 fee,

107:     function computeDecimals(address token) external view returns (uint8) {

110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {

```
([52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L52-L52),[107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L107-L107),[110](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L110-L110))
```solidity
File: contracts/libraries/Math.sol

25:     function min24(int24 a, int24 b) internal pure returns (int24) {

33:     function max24(int24 a, int24 b) internal pure returns (int24) {

91:     function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {

128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {

192:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());

193:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());

208:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());

209:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());

222:         int24 currentTick,

242:         int24 tickLower,

243:         int24 tickUpper,

246:         uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);

247:         uint160 highPriceX96 = getSqrtRatioAtTick(tickUpper);

272:         int24 tickLower,

273:         int24 tickUpper,

276:         uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);

277:         uint160 highPriceX96 = getSqrtRatioAtTick(tickUpper);

296:     function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

```
([25](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L25-L25),[33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L33-L33),[91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L91-L91),[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L128-L128),[192](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L192-L192),[193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L193-L193),[208](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L208-L208),[209](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L209-L209),[222](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L222-L222),[242](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L242-L242),[243](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L243-L243),[246](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L246-L246),[247](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L247-L247),[272](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L272-L272),[273](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L273-L273),[276](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L276-L276),[277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L277-L277),[296](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L296-L296),[302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L302-L302),[311](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L311-L311),[318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L318-L318))

```solidity
File: contracts/libraries/PanopticMath.sol

26:     uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

47:     function getPoolId(address univ3pool) internal view returns (uint64) {

49:             int24 tickSpacing = IUniswapV3Pool(univ3pool).tickSpacing();

50:             uint64 poolId = uint64(uint160(univ3pool) >> 112);

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

102:             uint248 updatedHash = uint248(existingHash) ^

131:     ) external view returns (int24) {

174:     ) external view returns (int24 medianTick, uint256 updatedMedianData) {

184:                 int24 lastObservedTick;

186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

192:                     (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool

200:                 uint24 orderMap = uint24(medianData >> 192);

202:                 uint24 newOrderMap;

203:                 uint24 shift = 1;

205:                 uint24 rank;

206:                 int24 entry;

207:                 for (uint8 i; i < 8; ++i) {

241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

292:         uint128 positionSize

295:         (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);

339:         int24 strike,

340:         int24 width,

341:         int24 tickSpacing

342:     ) internal pure returns (int24 tickLower, int24 tickUpper) {

346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

349:             (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(width, tickSpacing);

372:         int24 width,

373:         int24 tickSpacing

374:     ) internal pure returns (int24, int24) {

392:         uint128 positionSize

423:         uint160 sqrtPriceX96

449:         int24 tick

469:         uint128 contractSize,

470:         int24 tickLower,

471:         int24 tickUpper,

473:     ) internal pure returns (uint128) {

490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

576:         uint128 positionSize,

580:         (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);

582:         uint128 amount0;

583:         uint128 amount1;

609:         uint128 positionSize,

654:         uint160 sqrtPriceX96Twap,

655:         uint160 sqrtPriceX96Final,

775:         uint160 sqrtPriceX96Final,

920:         int24 atTick,

924:         uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);

```
([26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L26-L26),[47](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L47-L47),[49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L49-L49),[50](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L50-L50),[59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L59-L59),[102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L102-L102),[131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L131-L131),[174](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L174-L174),[184](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L184-L184),[186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L186-L186),[192](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L192-L192),[200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L200-L200),[202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L202-L202),[203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L203-L203),[205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L205-L205),[206](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L206-L206),[207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L207-L207),[241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L241-L241),[292](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L292-L292),[295](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L295-L295),[339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L339-L339),[340](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L340-L340),[341](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L341-L341),[342](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L342-L342),[346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L346-L346),[347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L347-L347),[349](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L349-L349),[372](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L372-L372),[373](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L373-L373),[374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L374-L374),[392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L392-L392),[423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L423-L423),[449](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L449-L449),[469](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L469-L469),[470](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L470-L470),[471](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L471-L471),[473](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L473-L473),[490](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L490-L490),[507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L507-L507),[524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L524-L524),[547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L547-L547),[576](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L576-L576),[580](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L580-L580),[582](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L582-L582),[583](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L583-L583),[609](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L609-L609),[654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L654-L654),[655](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L655-L655),[775](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L775-L775),[920](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L920-L920),[924](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L924-L924))
```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

18:         uint24 fee

```
([18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L18-L18)
)
```solidity
File: contracts/types/LeftRight.sol

39:     function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46:     function rightSlot(LeftRightSigned self) internal pure returns (int128) {

61:         uint128 right

80:         int128 right

101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

123:         uint128 left

134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

197:             int128 left128 = int128(left);

202:             int128 right128 = int128(right);

217:             int128 left128 = int128(left256);

220:             int128 right128 = int128(right256);

235:             int128 left128 = int128(left256);

238:             int128 right128 = int128(right256);

257:             int128 left128 = int128(left256);

260:             int128 right128 = int128(right256);

285:         uint128 z_xR = (uint256(x.rightSlot()) + dx.rightSlot()).toUint128Capped();

286:         uint128 z_xL = (uint256(x.leftSlot()) + dx.leftSlot()).toUint128Capped();

287:         uint128 z_yR = (uint256(y.rightSlot()) + dy.rightSlot()).toUint128Capped();

288:         uint128 z_yL = (uint256(y.leftSlot()) + dy.leftSlot()).toUint128Capped();

```
([39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L39-L39),[46](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L46-L46),[61](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L61-L61),[80](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L80-L80),[101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L101-L101),[108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L108-L108),[123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L123-L123),[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L134-L134),[197](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L197-L197),[202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L202-L202),[217](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L217-L217),[220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L220-L220),[235](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L235-L235),[238](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L238-L238),[257](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L257-L257),[260](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L260-L260),[285](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L285-L285),[286](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L286-L286),[287](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L287-L287),[288](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L288-L288))
```solidity
File: contracts/types/LiquidityChunk.sol

71:         int24 _tickLower,

72:         int24 _tickUpper,

73:         uint128 amount

91:         uint128 amount

104:         int24 _tickLower

120:         int24 _tickUpper

137:         int24 _tickLower

153:         int24 _tickUpper

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```
([71](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L71-L71),[72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L72-L72),[73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L73-L73),[91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L91-L91),[104](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L104-L104),[120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L120-L120),[137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L137-L137),[153](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L153-L153),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L171-L171),[180](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L180-L180),[189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L189-L189))
```solidity
File: contracts/types/TokenId.sol

87:     function poolId(TokenId self) internal pure returns (uint64) {

96:     function tickSpacing(TokenId self) internal pure returns (int24) {

158:     function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

169:     function width(TokenId self, uint256 legIndex) internal pure returns (int24) {

183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

293:         int24 _strike,

312:         int24 _width,

344:         int24 _strike,

345:         int24 _width

419:     ) internal pure returns (int24 legLowerTick, int24 legUpperTick) {

578:     function validateIsExercisable(TokenId self, int24 currentTick) internal pure {

582:                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(

587:                 int24 _strike = self.strike(i);

```
([87](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L87-L87),[96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L96-L96),[158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L158-L158),[169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L169-L169),[183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L183-L183),[193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L193-L193),[293](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L293-L293),[312](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L312-L312),[344](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L344-L344),[345](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L345-L345),[419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L419-L419),[578](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L578-L578),[582](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L582-L582),[587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L587-L587))
### <a name="GAS-35"></a>[GAS-35] Consider using solady's 'FixedPointMathLib'
Using Solady's 'FixedPointMathLib' for multiplication or division operations in Solidity can lead to significant gas savings. This library is designed to optimize fixed-point arithmetic operations, which are common in financial calculations involving tokens or currencies. By implementing more efficient algorithms and assembly optimizations, 'FixedPointMathLib' minimizes the computational resources required for these operations. For contracts that frequently perform such calculations, integrating this library can reduce transaction costs, thereby enhancing overall performance and cost-effectiveness. However, developers must ensure compatibility with their existing codebase and thoroughly test for accuracy and expected behavior to avoid any unintended consequences.

*There are 133 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

203:                     (12500 * ratioTick) /
                         10_000 +

205:                     (7812 * ratioTick ** 2) /
                         10_000 ** 2 +

207:                     (6510 * ratioTick ** 3) /
                         10_000 ** 3

249:             _poolFee = fee / 100;

262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

403:                 assets * (DECIMALS - COMMISSION_FEE),

405:                 totalAssets() * DECIMALS

446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

463:                 shares * DECIMALS,

465:                 totalSupply * (DECIMALS - COMMISSION_FEE)

670:                                 uint24(positionId.width(leg) * positionId.tickSpacing()),

677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

731:                 .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))

732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

743:             return int256((s_inAMM * DECIMALS) / totalAssets());

778:                 min_sell_ratio /= 2;

797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);

843:                 return BUYER_COLLATERAL_RATIO / 2;

849:                 (BUYER_COLLATERAL_RATIO +
                         (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
                         (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

850:                     (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
                         (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

1110:                     s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),

1121:                     uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,

1364:                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

1486:                 required = Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS);

1496:                 required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);

1571:                     ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)

1572:                     : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

```
([203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L203-L204),[205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L205-L206),[207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L207-L208),[249](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L249-L249),[262](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L262-L262),[403](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L403-L403),[405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L405-L405),[446](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L446-L446),[463](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L463-L463),[465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L465-L465),[670](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L670-L670),[677](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L677-L677),[731](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L731-L731),[732](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L732-L732),[743](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L743-L743),[778](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L778-L778),[797](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L797-L798),[843](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L843-L843),[849](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L849-L851),[850](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L850-L851),[1110](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1110-L1110),[1121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1121-L1121),[1364](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1364-L1364),[1367](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1367-L1367),[1486](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1486-L1486),[1496](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1496-L1496),[1571](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1571-L1571),[1572](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1572-L1572))
```solidity
File: contracts/PanopticFactory.sol

392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```
([392](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L392-L392))
```solidity
File: contracts/PanopticPool.sol

165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

1550:                                     ((premiumAccumulatorsByLeg[leg][0] -
                                              premiumAccumulatorLast.rightSlot()) *
                                              (liquidityChunk.liquidity())) / 2 ** 64

1559:                                     ((premiumAccumulatorsByLeg[leg][1] -
                                              premiumAccumulatorLast.leftSlot()) *
                                              (liquidityChunk.liquidity())) / 2 ** 64

1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

1729:                                 (grossCurrent[0] *
                                          positionLiquidity +
                                          grossPremiumLast.rightSlot() *
                                          totalLiquidityBefore) / (totalLiquidity)

1731:                                     grossPremiumLast.rightSlot() *
                                          totalLiquidityBefore) / (totalLiquidity)

1737:                                 (grossCurrent[1] *
                                          positionLiquidity +
                                          grossPremiumLast.leftSlot() *
                                          totalLiquidityBefore) / (totalLiquidity)

1739:                                     grossPremiumLast.leftSlot() *
                                          totalLiquidityBefore) / (totalLiquidity)

1768:             uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *
                      totalLiquidity) / 2 ** 64;

1770:             uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *
                      totalLiquidity) / 2 ** 64;

1779:                                 (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /
                                          (accumulated0 == 0 ? type(uint256).max : accumulated0),

1788:                                 (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /
                                          (accumulated1 == 0 ? type(uint256).max : accumulated1),

1933:                                         uint256(
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

1936:                                                     grossPremiumLast.rightSlot() *
                                                              totalLiquidityBefore

1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *
                                                                  positionLiquidity

1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),

1950:                                         uint256(
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

1953:                                                     grossPremiumLast.leftSlot() *
                                                              totalLiquidityBefore

1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *
                                                                  positionLiquidity

1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,

```
([165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L165-L165),[1329](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1329-L1329),[1487](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1487-L1487),[1550](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1550-L1552),[1559](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1559-L1561),[1635](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1635-L1635),[1636](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1636-L1636),[1729](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1729-L1732),[1731](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1731-L1732),[1737](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1737-L1740),[1739](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1739-L1740),[1768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1768-L1769),[1770](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1770-L1771),[1779](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1779-L1780),[1788](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1788-L1789),[1933](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1933-L1945),[1936](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1936-L1937),[1940](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1940-L1941),[1942](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1942-L1942),[1950](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1950-L1962),[1953](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1953-L1954),[1957](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1957-L1958),[1959](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1959-L1959))
```solidity
File: contracts/SemiFungiblePositionManager.sol

1352:                     totalLiquidity * 2 ** 64,

1357:                     totalLiquidity * 2 ** 64,

1367:                     uint256 numerator = netLiquidity + (removedLiquidity / 2 ** VEGOID);

1389:                         totalLiquidity *
                              removedLiquidity +

1391:                         ((removedLiquidity ** 2) / 2 ** (VEGOID));

```
([1352](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1352-L1352),[1357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1357-L1357),[1367](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1367-L1367),[1389](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1389-L1390),[1391](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1391-L1391))
```solidity
File: contracts/libraries/Math.sol

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

196:                 mulDiv(
                         uint256(liquidityChunk.liquidity()) << 96,
                         highPriceX96 - lowPriceX96,
                         highPriceX96
                     ) / lowPriceX96;

407:             prod0 |= prod1 * twos;

414:             uint256 inv = (3 * denominator) ^ 2;

418:             inv *= 2 - denominator * inv; // inverse mod 2**8

419:             inv *= 2 - denominator * inv; // inverse mod 2**16

420:             inv *= 2 - denominator * inv; // inverse mod 2**32

421:             inv *= 2 - denominator * inv; // inverse mod 2**64

422:             inv *= 2 - denominator * inv; // inverse mod 2**128

423:             inv *= 2 - denominator * inv; // inverse mod 2**256

431:             result = prod0 * inv;

511:             prod0 |= prod1 * 2 ** 192;

574:             prod0 |= prod1 * 2 ** 160;

651:             prod0 |= prod1 * 2 ** 128;

728:             prod0 |= prod1 * 2 ** 64;

758:             int256 pivot = arr[uint256(left + (right - left) / 2)];

```
([137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L137-L137),[139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L139-L139),[141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L141-L141),[143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L143-L143),[145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L145-L145),[147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L147-L147),[149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L149-L149),[151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L151-L151),[153](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L153-L153),[155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L155-L155),[157](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L157-L157),[159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L159-L159),[161](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L161-L161),[163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L163-L163),[165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L165-L165),[167](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L167-L167),[169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L169-L169),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L171-L171),[173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L173-L173),[176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L176-L176),[196](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L196-L200),[407](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L407-L407),[414](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L414-L414),[418](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L418-L418),[419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L419-L419),[420](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L420-L420),[421](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L421-L421),[422](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L422-L422),[423](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L423-L423),[431](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L431-L431),[511](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L511-L511),[574](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L574-L574),[651](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L651-L651),[728](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L728-L728),[758](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L758-L758))
```solidity
File: contracts/libraries/PanopticMath.sol

140:                         (int256(observationIndex) - int256(i * period)) +

150:                     (tickCumulatives[i] - tickCumulatives[i + 1]) /
                         int256(timestamps[i] - timestamps[i + 1]);

155:             return int24(Math.sort(ticks)[cardinality / 2]);

178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
                         int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
                     2;

179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

195:                         (tickCumulative_last - tickCumulative_old) /
                                 int256(timestamp_last - timestamp_old)

209:                     rank = (orderMap >> (3 * i)) % 8;

217:                     entry = int24(uint24(medianData >> (rank * 24)));

223:                     newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));

249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);

258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

324:         uint256 amount = uint256(positionSize) * tokenId.optionRatio(legIndex);

346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

376:             (width * tickSpacing) / 2,

377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

585:             amount0 = positionSize * uint128(tokenId.optionRatio(legIndex));

591:             amount1 = positionSize * uint128(tokenId.optionRatio(legIndex));

669:                 uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);

678:                 uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),

874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),

```
([140](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L140-L140),[150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L150-L151),[155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L155-L155),[178](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L178-L180),[179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L179-L179),[195](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L195-L196),[209](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L209-L209),[217](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L217-L217),[223](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L223-L223),[249](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L249-L249),[258](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L258-L258),[324](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L324-L324),[346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L346-L346),[347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L347-L347),[376](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L376-L376),[377](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L377-L377),[476](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L476-L476),[477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L477-L477),[585](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L585-L585),[591](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L591-L591),[669](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L669-L669),[678](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L678-L678),[870](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L870-L870),[874](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L874-L874))
```solidity
File: contracts/types/TokenId.sol

110:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

120:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

130:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

140:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

150:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

300:                         uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))

320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

395:                         ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)

512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

521:                     if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {

```
([110](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L110-L110),[120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L120-L120),[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L130-L130),[140](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L140-L140),[150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L150-L150),[160](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L160-L160),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L171-L171),[212](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L212-L212),[229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L229-L229),[246](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L246-L246),[263](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L263-L263),[281](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L281-L281),[300](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L300-L300),[320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L320-L320),[395](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L395-L395),[512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L512-L512),[521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L521-L521))

### <a name="GAS-36"></a>[GAS-36] Newer versions of solidity are more gas efficient
he solidity language continues to pursue more efficient gas optimization schemes. Adopting a [newer version of solidity](https://github.com/ethereum/solc-js/tags) can be more gas efficient.

*There are 20 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

2: pragma solidity ^0.8.18;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L2-L2))
```solidity
File: contracts/PanopticFactory.sol

2: pragma solidity ^0.8.18;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L2-L2))
```solidity
File: contracts/PanopticPool.sol

2: pragma solidity ^0.8.18;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L2-L2))
```solidity
File: contracts/SemiFungiblePositionManager.sol

2: pragma solidity ^0.8.18;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L2-L2))
```solidity
File: contracts/libraries/CallbackLib.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L2-L2))
```solidity
File: contracts/libraries/Constants.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L2-L2))
```solidity
File: contracts/libraries/Errors.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L2-L2))
```solidity
File: contracts/libraries/FeesCalc.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L2-L2))
```solidity
File: contracts/libraries/InteractionHelper.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L2-L2))
```solidity
File: contracts/libraries/Math.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L2-L2))
```solidity
File: contracts/libraries/PanopticMath.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L2-L2))
```solidity
File: contracts/libraries/SafeTransferLib.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L2-L2))
```solidity
File: contracts/multicall/Multicall.sol

2: pragma solidity ^0.8.18;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L2-L2))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L2-L2))
```solidity
File: contracts/tokens/ERC20Minimal.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L2-L2))
```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L2-L2))
```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L2-L2))
```solidity
File: contracts/types/LeftRight.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L2-L2))
```solidity
File: contracts/types/LiquidityChunk.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L2-L2))
```solidity
File: contracts/types/TokenId.sol

2: pragma solidity ^0.8.0;

```
([2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L2-L2))
### <a name="GAS-37"></a>[GAS-37] `address(this)` can be stored in state variable that will ultimately cost less, than every time calculating this, specifically when it used multiple times in a contract

*There are 10 Instances of this issue* :
```solidity
File: contracts/PanopticFactory.sol

405:                 address(this),

```
([405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L405-L405))
```solidity
File: contracts/PanopticPool.sol

753:                     address(this),

1474:             address(this),

1531:                         address(this),

1607:                 address(this),

1709:                     address(this),

1813:                 address(this),

```
([753](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L753-L753),[1474](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1474-L1474),[1531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1531-L1531),[1607](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1607-L1607),[1709](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1709-L1709),[1813](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1813-L1813))
```solidity
File: contracts/SemiFungiblePositionManager.sol

1152:                         address(this),

1204:             address(this),

```
([1152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1152-L1152),[1204](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1204-L1204))
```solidity
File: contracts/multicall/Multicall.sol

15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);

```
([15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L15-L15))
### <a name="GAS-38"></a>[GAS-38] Gas savings can be achieved by changing the model for assigning value to the structure
Here's an example to illustrate this:

```solidity
struct MyStruct {
  uint256 a;
  uint256 b;
  uint256 c;
}

function assignValuesToStruct(uint256 _a, uint256 _b, uint256 _c) public {
  MyStruct memory myStruct = MyStruct(_a, _b, _c);
  // Do something with myStruct
}
```

In this example, we have a simple MyStruct data structure with three uint256 fields. The assignValuesToStruct function takes three input parameters _a, _b, and _c, and assigns them to the corresponding fields in a new myStruct variable. This is done using the struct constructor syntax, which creates a new instance of the MyStruct struct with the specified field values.

The following approach can be more efficient than assigning values to the struct fields:

```solidity
function assignValuesToStruct(uint256 _a, uint256 _b, uint256 _c) public {
  MyStruct memory myStruct;
  myStruct.a = _a;
  myStruct.b = _b;
  myStruct.c = _c;
  // Do something with myStruct
}
```

By changing the pattern of assigning value to the structure, gas savings of ~130 per instance are achieved. In addition, this use will provide significant savings in distribution costs.

*There are 1 Instance of this issue* :
```solidity
File: contracts/SemiFungiblePositionManager.sol

379:         s_poolContext[poolId] = PoolAddressAndLock({
                 pool: IUniswapV3Pool(univ3pool),
                 locked: s_poolContext[poolId].locked
             );

```
([379](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L379-L382))
### <a name="GAS-39"></a>[GAS-39] Optimize Storage with Byte Truncation for Time Related State Variables
Storage optimization in Solidity contracts is vital for reducing gas costs, especially when storing time-related state variables. Using `uint32` for storing time values like timestamps is often sufficient, given it can represent dates up to the year 2106. By truncating larger default integer types to `uint32`, you significantly save on storage space and consequently on gas costs for deployment and state modifications. However, ensure that the truncation does not lead to overflow issues and that the variable's size is adequate for the application's expected lifespan and precision requirements. Adopting this optimization practice contributes to more efficient and cost-effective smart contract development.

*There are 7 Instances of this issue* :
```solidity
File: contracts/PanopticPool.sol

136:     uint256 internal constant MEDIAN_PERIOD = 60;

145:     uint256 internal constant FAST_ORACLE_PERIOD = 1;

152:     uint256 internal constant SLOW_ORACLE_PERIOD = 5;

```
([136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L136-L136),[145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L145-L145),[152](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L152-L152))
```solidity
File: contracts/libraries/PanopticMath.sol

130:         uint256 period

171:         uint256 period,

186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

192:                     (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool

```
([130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L130-L130),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L171-L171),[186](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L186-L186),[192](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L192-L192))
### <a name="GAS-40"></a>[GAS-40] Trade-offs Between Modifiers and Internal Functions
In Solidity, both modifiers and internal functions can be used to modularize and reuse code, but they have different trade-offs.

Modifiers are primarily used to augment the behavior of functions, often for checks or validations. They can access parameters of the function they modify and are integrated into the function’s code at compile time. This makes them syntactically cleaner for repetitive precondition checks. However, modifiers can sometimes lead to less readable code, especially when the logic is complex or when multiple modifiers are used on a single function.

Internal functions, on the other hand, offer more flexibility. They can contain complex logic, return values, and be called from other functions. This makes them more suitable for reusable chunks of business logic. Since internal functions are separate entities, they can be more readable and easier to test in isolation compared to modifiers.

Using internal functions can result in slightly more gas consumption, as it involves an internal function call. However, this cost is usually minimal and can be a worthwhile trade-off for increased code clarity and maintainability.

In summary, while modifiers offer a concise way to include checks and simple logic across multiple functions, internal functions provide more flexibility and are better suited for complex and reusable code. The choice between the two should be based on the specific use case, considering factors like code complexity, readability, and gas efficiency.

*There are 152 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

741:     function _poolUtilization() internal view returns (int256 poolUtilization) {

751:     function _sellCollateralRatio(
             int256 utilization
         ) internal view returns (uint256 sellCollateralRatio) {

806:     function _buyCollateralRatio(
             uint256 utilization
         ) internal view returns (uint256 buyCollateralRatio) {

1096:     function _getExchangedAmount(
              int128 longAmount,
              int128 shortAmount,
              int128 swappedAmount
          ) internal view returns (int256 exchangedAmount) {

1159:     function _getAccountMargin(
              address user,
              int24 atTick,
              uint256[2][] memory positionBalanceArray,
              int128 premiumAllPositions
          ) internal view returns (LeftRightUnsigned tokenData) {

1200:     function _getTotalRequiredCollateral(
              int24 atTick,
              uint256[2][] memory positionBalanceArray
          ) internal view returns (uint256 tokenRequired) {

1245:     function _getRequiredCollateralAtTickSinglePosition(
              TokenId tokenId,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 tokenRequired) {

1278:     function _getRequiredCollateralSingleLeg(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 required) {

1311:     function _getRequiredCollateralSingleLegNoPartner(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 required) {

1439:     function _getRequiredCollateralSingleLegPartner(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 required) {

1473:     function _getRequiredCollateralAtUtilization(
              uint128 amount,
              uint256 isLong,
              int256 utilization
          ) internal view returns (uint256 required) {

1510:     function _computeSpread(
              TokenId tokenId,
              uint128 positionSize,
              uint256 index,
              uint256 partnerIndex,
              uint128 poolUtilization
          ) internal view returns (uint256 spreadRequirement) {

1600:     function _computeStrangle(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 strangleRequired) {

```
([741](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L741-L741),[751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L751-L753),[806](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L806-L808),[1096](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1096-L1100),[1159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1159-L1164),[1200](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1200-L1203),[1245](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1245-L1250),[1278](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1278-L1284),[1311](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1311-L1317),[1439](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1439-L1445),[1473](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1473-L1477),[1510](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1510-L1516),[1600](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1600-L1606))
```solidity
File: contracts/PanopticFactory.sol

335:     function _mintFullRange(
             IUniswapV3Pool v3Pool,
             address token0,
             address token1,
             uint24 fee
         ) internal returns (uint256, uint256) {

```
([335](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L335-L340))
```solidity
File: contracts/PanopticPool.sol

429:     function _calculateAccumulatedPremia(
             address user,
             TokenId[] calldata positionIdList,
             bool computeAllPremia,
             bool includePendingPremium,
             int24 atTick
         ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

499:     function _getSlippageLimits(
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal pure returns (int24, int24) {

614:     function _mintOptions(
             TokenId[] calldata positionIdList,
             uint128 positionSize,
             uint64 effectiveLiquidityLimitX32,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal {

677:     function _mintInSFPMAndUpdateCollateral(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal returns (uint128) {

706:     function _payCommissionAndWriteData(
             TokenId tokenId,
             uint128 positionSize,
             LeftRightSigned totalSwapped
         ) internal returns (uint128) {

739:     function _addUserOption(TokenId tokenId, uint64 effectiveLiquidityLimitX32) internal {

794:     function _burnAllOptionsFrom(
             address owner,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool commitLongSettled,
             TokenId[] calldata positionIdList
         ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

826:     function _burnOptions(
             bool commitLongSettled,
             TokenId tokenId,
             address owner,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

887:     function _validateSolvency(
             address user,
             TokenId[] calldata positionIdList,
             uint256 buffer
         ) internal view returns (uint256 medianData) {

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

1339:     function _getSolvencyBalances(
              LeftRightUnsigned tokenData0,
              LeftRightUnsigned tokenData1,
              uint160 sqrtPriceX96
          ) internal pure returns (uint256 balanceCross, uint256 thresholdCross) {

1367:     function _validatePositionList(
              address account,
              TokenId[] calldata positionIdList,
              uint256 offset
          ) internal view {

1405:     function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {

1450:     function getUniV3TWAP() internal view returns (int24 twapTick) {

1465:     function _checkLiquiditySpread(
              TokenId tokenId,
              uint256 leg,
              int24 tickLower,
              int24 tickUpper,
              uint64 effectiveLiquidityLimitX32
          ) internal view {

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

1666:     function _updateSettlementPostMint(
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize
          ) internal {

1757:     function _getAvailablePremium(
              uint256 totalLiquidity,
              LeftRightUnsigned settledTokens,
              LeftRightUnsigned grossPremiumLast,
              LeftRightUnsigned premiumOwed,
              uint256[2] memory premiumAccumulators
          ) internal pure returns (LeftRightUnsigned) {

1802:     function _getTotalLiquidity(
              TokenId tokenId,
              uint256 leg
          ) internal view returns (uint256 totalLiquidity) {

1833:     function _updateSettlementPostBurn(
              address owner,
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize,
              bool commitLongSettled
          ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {

```
([429](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L429-L435),[499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L499-L502),[614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L614-L620),[677](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L677-L682),[706](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L706-L710),[739](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L739-L739),[794](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L794-L800),[826](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L826-L832),[859](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L859-L859),[887](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L887-L891),[955](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L955-L969),[1290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1290-L1296),[1339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1339-L1343),[1367](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1367-L1371),[1405](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1405-L1405),[1450](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1450-L1450),[1465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1465-L1471),[1503](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1503-L1516),[1666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1666-L1670),[1757](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1757-L1763),[1802](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1802-L1805),[1833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1833-L1839))
```solidity
File: contracts/SemiFungiblePositionManager.sol

320:     function beginReentrancyLock(uint64 poolId) internal {

330:     function endReentrancyLock(uint64 poolId) internal {

593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

680:     function _validateAndForwardToAMM(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool isBurn
         ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

756:     function swapInAMM(
             IUniswapV3Pool univ3pool,
             LeftRightSigned itmAmounts
         ) internal returns (LeftRightSigned totalSwapped) {

863:     function _createPositionInAMM(
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
         {

958:     function _createLegInAMM(
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
         {

1185:     function _mintLiquidity(
              LiquidityChunk liquidityChunk,
              IUniswapV3Pool univ3pool
          ) internal returns (LeftRightSigned movedAmounts) {

1224:     function _burnLiquidity(
              LiquidityChunk liquidityChunk,
              IUniswapV3Pool univ3pool
          ) internal returns (LeftRightSigned movedAmounts) {

1255:     function _collectAndWritePositionData(
              LiquidityChunk liquidityChunk,
              IUniswapV3Pool univ3pool,
              LeftRightUnsigned currentLiquidity,
              bytes32 positionKey,
              LeftRightSigned movedInLeg,
              uint256 isLong
          ) internal returns (LeftRightUnsigned collectedChunk) {

```
([320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L320-L320),[330](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L330-L330),[593](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L593-L593),[680](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L680-L686),[756](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L756-L759),[863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L863-L875),[958](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L958-L971),[1185](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1185-L1188),[1224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1224-L1227),[1255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1255-L1262))
```solidity
File: contracts/libraries/CallbackLib.sol

30:     function validateCallback(
            address sender,
            IUniswapV3Factory factory,
            PoolFeatures memory features
        ) internal view {

```
([30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L30-L34))
```solidity
File: contracts/libraries/FeesCalc.sol

130:     function _getAMMSwapFeesPerLiquidityCollected(
             IUniswapV3Pool univ3pool,
             int24 currentTick,
             int24 tickLower,
             int24 tickUpper
         ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {

```
([130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L130-L135))
```solidity
File: contracts/libraries/Math.sol

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
             int24 currentTick,
             LiquidityChunk liquidityChunk
         ) internal pure returns (uint256 amount0, uint256 amount1) {

241:     function getLiquidityForAmount0(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount0
         ) internal pure returns (LiquidityChunk) {

271:     function getLiquidityForAmount1(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount1
         ) internal pure returns (LiquidityChunk) {

296:     function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

340:     function mulDiv(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {

440:     function mulDivRoundingUp(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {

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
([25](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L25-L25),[33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L33-L33),[41](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L41-L41),[49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L49-L49),[57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L57-L57),[65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L65-L65),[73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L73-L73),[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L81-L81),[91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L91-L91),[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L128-L128),[191](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L191-L191),[207](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L207-L207),[221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L221-L224),[241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L241-L245),[271](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L271-L275),[296](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L296-L296),[302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L302-L302),[311](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L311-L311),[318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L318-L318),[325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L325-L325),[340](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L340-L344),[440](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L440-L444),[458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L458-L458),[521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L521-L521),[584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L584-L584),[598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L598-L598),[661](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L661-L661),[675](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L675-L675),[738](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L738-L738),[753](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L753-L753),[776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L776-L776))
```solidity
File: contracts/libraries/PanopticMath.sol

47:     function getPoolId(address univ3pool) internal view returns (uint64) {

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

92:     function updatePositionsHash(
            uint256 existingHash,
            TokenId tokenId,
            bool addFlag
        ) internal pure returns (uint256) {

289:     function getLiquidityChunk(
             TokenId tokenId,
             uint256 legIndex,
             uint128 positionSize
         ) internal pure returns (LiquidityChunk) {

338:     function getTicks(
             int24 strike,
             int24 width,
             int24 tickSpacing
         ) internal pure returns (int24 tickLower, int24 tickUpper) {

371:     function getRangesFromStrike(
             int24 width,
             int24 tickSpacing
         ) internal pure returns (int24, int24) {

390:     function computeExercisedAmounts(
             TokenId tokenId,
             uint128 positionSize
         ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {

419:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             uint160 sqrtPriceX96
         ) internal pure returns (uint256, uint256) {

445:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             int24 tick
         ) internal pure returns (uint256, uint256) {

468:     function convertNotional(
             uint128 contractSize,
             int24 tickLower,
             int24 tickUpper,
             uint256 asset
         ) internal pure returns (uint128) {

490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

574:     function getAmountsMoved(
             TokenId tokenId,
             uint128 positionSize,
             uint256 legIndex
         ) internal pure returns (LeftRightUnsigned) {

607:     function _calculateIOAmounts(
             TokenId tokenId,
             uint128 positionSize,
             uint256 legIndex
         ) internal pure returns (LeftRightSigned longs, LeftRightSigned shorts) {

```
([47](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L47-L47),[59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L59-L59),[92](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L92-L96),[289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L289-L293),[338](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L338-L342),[371](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L371-L374),[390](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L390-L393),[419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L419-L424),[445](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L445-L450),[468](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L468-L473),[490](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L490-L490),[507](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L507-L507),[524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L524-L524),[547](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L547-L547),[574](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L574-L578),[607](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L607-L611))
```solidity
File: contracts/libraries/SafeTransferLib.sol

21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:     function safeTransfer(address token, address to, uint256 amount) internal {

```
([21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L21-L21),[52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L52-L52))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

214:     function _mint(address to, uint256 id, uint256 amount) internal {

236:     function _burn(address from, uint256 id, uint256 amount) internal {

```
([214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L214-L214),[236](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L236-L236))
```solidity
File: contracts/tokens/ERC20Minimal.sol

103:     function _transferFrom(address from, address to, uint256 amount) internal {

122:     function _mint(address to, uint256 amount) internal {

136:     function _burn(address from, uint256 amount) internal {

```
([103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L103-L103),[122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L122-L122),[136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L136-L136))
```solidity
File: contracts/types/LeftRight.sol

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
([39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L39-L39),[46](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L46-L46),[59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L59-L62),[78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L78-L81),[101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L101-L101),[108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L108-L108),[121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L121-L124),[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L134-L134),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L148-L151),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L171-L174),[194](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L194-L194),[214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L214-L214),[232](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L232-L232),[251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L251-L254),[279](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L279-L284))
```solidity
File: contracts/types/LiquidityChunk.sol

70:     function createChunk(
            int24 _tickLower,
            int24 _tickUpper,
            uint128 amount
        ) internal pure returns (LiquidityChunk) {

89:     function addLiquidity(
            LiquidityChunk self,
            uint128 amount
        ) internal pure returns (LiquidityChunk) {

102:     function addTickLower(
             LiquidityChunk self,
             int24 _tickLower
         ) internal pure returns (LiquidityChunk) {

118:     function addTickUpper(
             LiquidityChunk self,
             int24 _tickUpper
         ) internal pure returns (LiquidityChunk) {

135:     function updateTickLower(
             LiquidityChunk self,
             int24 _tickLower
         ) internal pure returns (LiquidityChunk) {

151:     function updateTickUpper(
             LiquidityChunk self,
             int24 _tickUpper
         ) internal pure returns (LiquidityChunk) {

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```
([70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L70-L74),[89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L89-L92),[102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L102-L105),[118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L118-L121),[135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L135-L138),[151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L151-L154),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L171-L171),[180](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L180-L180),[189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L189-L189))
```solidity
File: contracts/types/TokenId.sol

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
([87](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L87-L87),[96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L96-L96),[108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L108-L108),[118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L118-L118),[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L128-L128),[138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L138-L138),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L148-L148),[158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L158-L158),[169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L169-L169),[183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L183-L183),[193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L193-L193),[205](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L205-L209),[221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L221-L225),[240](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L240-L244),[255](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L255-L259),[273](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L273-L277),[291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L291-L295),[310](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L310-L314),[336](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L336-L346),[366](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L366-L366),[404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L404-L404),[416](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L416-L419),[432](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L432-L432),[464](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L464-L464),[500](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L500-L500),[578](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L578-L578))
### <a name="GAS-41"></a>[GAS-41] Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes
Use `uint256(1)` and `uint256(2)` for `true`/`false` to avoid a Gwarmaccess (100 gas), and to avoid Gsset (20000 gas) when changing from `false` to `true`, after having been `true` in the past. Refer to the [source](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/5ae630684a0f57de400ef69499addab4c32ac8fb/contracts/security/ReentrancyGuard.sol#L23-L27).

*There are 13 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

93:     bool internal s_initialized;

102:     bool internal s_underlyingIsToken0;

```
([93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L93-L93),[102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L102-L102))
```solidity
File: contracts/PanopticFactory.sol

99:     bool internal s_initialized;

```
([99](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L99-L99))
```solidity
File: contracts/PanopticPool.sol

109:     bool internal constant COMPUTE_ALL_PREMIA = true;

111:     bool internal constant COMPUTE_LONG_PREMIA = false;

114:     bool internal constant ONLY_AVAILABLE_PREMIUM = false;

119:     bool internal constant COMMIT_LONG_SETTLED = true;

120:     bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

123:     bool internal constant ADD = true;

133:     bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;

```
([109](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L109-L109),[111](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L111-L111),[114](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L114-L114),[119](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L119-L119),[120](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L120-L120),[123](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L123-L123),[133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L133-L133))
```solidity
File: contracts/SemiFungiblePositionManager.sol

125:     bool internal constant MINT = false;

126:     bool internal constant BURN = true;

```
([125](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L125-L125),[126](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L126-L126))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

71:     mapping(address owner => mapping(address operator => bool approvedForAll))
            public isApprovedForAll;

```
([71](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L71-L72))
### <a name="GAS-42"></a>[GAS-42] Divisions can be `unchecked` to save gas
The expression `type(int).min/(-1)` is the only case where division causes an overflow. Therefore, uncheck can be used to [save gas](https://gist.github.com/DadeKuma/3bc597338ae774b8b3bd43280d55271f) in scenarios where it is certain that such an overflow will not occur.

*There are 1 Instance of this issue* :
```solidity
File: contracts/libraries/PanopticMath.sol

376:             (width * tickSpacing) / 2,

```
([376](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L376-L376))
### <a name="GAS-43"></a>[GAS-43] Avoid unnecessary public variables
Public state variables in Solidity automatically generate getter functions, increasing contract size and potentially leading to higher deployment and interaction costs. To optimize gas usage and contract efficiency, minimize the use of public variables unless external access is necessary. Instead, use internal or private visibility combined with explicit getter functions when required. This practice not only reduces contract size but also provides better control over data access and manipulation, enhancing security and readability. Prioritize lean, efficient contracts to ensure cost-effectiveness and better performance on the blockchain.

*There are 5 Instances of this issue* :
```solidity
File: contracts/tokens/ERC1155Minimal.sol

66:     mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;

71:     mapping(address owner => mapping(address operator => bool approvedForAll))
            public isApprovedForAll;

```
([66](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L66-L66),[71](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L71-L72))
```solidity
File: contracts/tokens/ERC20Minimal.sol

32:     uint256 public totalSupply;

35:     mapping(address account => uint256 balance) public balanceOf;

39:     mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;

```
([32](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L32-L32),[35](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L35-L35),[39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L39-L39))

### <a name="GAS-44"></a>[GAS-44] Using assembly to check for `address(0)` can save gas(Not captured by 4nalyzer)
Using assembly to check for `address(0)` can save gas by allowing more direct access to the evm and reducing some of the overhead associated with high-level operations in solidity.

*There are 1 Instance of this issue* :

```solidity
File: contracts/SemiFungiblePositionManager.sol

355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

```
([355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L355-L355))


### <a name="GAS-45"></a>[GAS-45] Use assembly to `emit` events
To efficiently `emit` events, it's possible to utilize assembly by making use of scratch space and the free memory pointer. This approach has the advantage of potentially avoiding the costs associated with memory expansion.
However, it's important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.
A good example of such practice can be seen in [Solady's](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) codebase.

*There are 25 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

439:         emit Deposit(msg.sender, receiver, assets, shares);

499:         emit Deposit(msg.sender, receiver, assets, shares);

563:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

623:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

```
([439](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L439-L439),[499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L499-L499),[563](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L563-L563),[623](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L623-L623))
```solidity
File: contracts/PanopticFactory.sol

154:         emit OwnershipTransferred(currentOwner, newOwner);

268:         emit PoolDeployed(
                 newPoolContract,
                 v3Pool,
                 collateralTracker0,
                 collateralTracker1,
                 amount0,
                 amount1
             );

```
([154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L154-L154),[268](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L268-L275))
```solidity
File: contracts/PanopticPool.sol

666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);

853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

1170:         emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

1277:         emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

1654:             emit PremiumSettled(owner, tokenId, realizedPremia);

```
([666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L666-L666),[853](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L853-L853),[1170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1170-L1170),[1277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1277-L1277),[1654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1654-L1654))
```solidity
File: contracts/SemiFungiblePositionManager.sol

390:         emit PoolInitialized(univ3pool, poolId);

485:         emit TokenizedPositionBurnt(msg.sender, tokenId, positionSize);

517:         emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);

```
([390](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L390-L390),[485](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L485-L485),[517](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L517-L517))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

84:         emit ApprovalForAll(msg.sender, operator, approved);

110:         emit TransferSingle(msg.sender, from, to, id, amount);

161:         emit TransferBatch(msg.sender, from, to, ids, amounts);

220:         emit TransferSingle(msg.sender, address(0), to, id, amount);

239:         emit TransferSingle(msg.sender, from, address(0), id, amount);

```
([84](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L84-L84),[110](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L110-L110),[161](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L161-L161),[220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L220-L220),[239](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L239-L239))
```solidity
File: contracts/tokens/ERC20Minimal.sol

52:         emit Approval(msg.sender, spender, amount);

70:         emit Transfer(msg.sender, to, amount);

94:         emit Transfer(from, to, amount);

112:         emit Transfer(from, to, amount);

130:         emit Transfer(address(0), to, amount);

145:         emit Transfer(from, address(0), amount);

```
([52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L52-L52),[70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L70-L70),[94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L94-L94),[112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L112-L112),[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L130-L130),[145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L145-L145))
### <a name="GAS-46"></a>[GAS-46] Use assembly to validate `msg.sender`
We can use assembly to efficiently validate `msg.sender` with the least amount of opcodes necessary. For more details check the following report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender)

*There are 8 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

170:         if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

541:         if (msg.sender != owner) {

599:         if (msg.sender != owner) {

```
([170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L170-L170),[541](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L541-L541),[599](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L599-L599))
```solidity
File: contracts/PanopticFactory.sol

150:         if (msg.sender != currentOwner) revert Errors.NotOwner();

220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

```
([150](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L150-L150),[220](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L220-L220),[224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L224-L224))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

101:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

```
([101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L101-L101),[137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L137-L137))
### <a name="GAS-47"></a>[GAS-47] Simple checks for zero can be done using assembly to save gas

*There are 137 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

664:                 if (positionId.isLong(leg) == 0) continue;

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

776:         if (utilization < 0) {

976:         if (assets > 0) {

1010:             if (tokenToPay > 0) {

1018:             } else if (tokenToPay < 0) {

1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1067:             if (tokenToPay > 0) {

1075:             } else if (tokenToPay < 0) {

1107:             if (intrinsicValue != 0) {

1168:         if (positionBalanceArray.length > 0) {

1173:             if (premiumAllPositions < 0) {

1182:         if (premiumAllPositions > 0) {

1257:                 if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;

1325:         uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();

1328:         int64 utilization = tokenType == 0

1339:             if (isLong == 0) {

1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1479:         if (isLong == 0) {

1544:                 if (tokenType == 0) {

1582:                 tokenType == 0 ? movedRight : movedLeft,

1584:                 tokenType == 0

1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```
([331](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L331-L331),[350](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L350-L350),[512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L512-L512),[575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L575-L575),[664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L664-L664),[708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L708-L708),[776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L776-L776),[976](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L976-L976),[1010](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1010-L1010),[1018](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1018-L1018),[1060](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1060-L1060),[1067](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1067-L1067),[1075](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1075-L1075),[1107](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1107-L1107),[1168](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1168-L1168),[1173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1173-L1173),[1182](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1182-L1182),[1257](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1257-L1257),[1325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1325-L1325),[1328](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1328-L1328),[1339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1339-L1339),[1347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1347-L1347),[1375](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1375-L1375),[1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1479-L1479),[1544](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1544-L1544),[1582](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1582-L1582),[1584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1584-L1584),[1637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1637-L1637),[1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1638-L1638))
```solidity
File: contracts/PanopticFactory.sol

181:         if (amount0Owed > 0)

188:         if (amount1Owed > 0)

224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

229:         if (address(s_getPanopticPool[v3Pool]) != address(0))

```
([181](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L181-L181),[188](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L188-L188),[224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L224-L224),[227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L227-L227),[229](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L229-L229))
```solidity
File: contracts/PanopticPool.sol

299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

533:         if (medianData != 0) s_miniMedian = medianData;

638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

664:         if (medianData != 0) s_miniMedian = medianData;

865:             if (tokenId.isLong(leg) == 0) {

1274:         if (positionIdListExercisor.length > 0)

1483:         if (netLiquidity == 0) return;

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1679:             if (tokenId.isLong(leg) == 0) {

1780:                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),

1789:                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),

1862:             if (LeftRightSigned.unwrap(legPremia) != 0) {

1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0

```
([299](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L299-L299),[460](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L460-L460),[533](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L533-L533),[638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L638-L638),[664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L664-L664),[865](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L865-L865),[1274](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1274-L1274),[1483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1483-L1483),[1596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1596-L1596),[1679](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1679-L1679),[1780](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1780-L1780),[1789](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1789-L1789),[1862](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1862-L1862),[1928](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1928-L1928))
```solidity
File: contracts/SemiFungiblePositionManager.sol

355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

362:         if (s_AddrToPoolIdData[univ3pool] != 0) return;

372:         while (address(s_poolContext[poolId].pool) != address(0)) {

412:         if (amount0Owed > 0)

419:         if (amount1Owed > 0)

446:         address token = amount0Delta > 0

453:         uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);

632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

702:         if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

787:             if ((itm0 != 0) && (itm1 != 0)) {

819:                 zeroForOne = net0 < 0;

823:             } else if (itm0 != 0) {

824:                 zeroForOne = itm0 < 0;

827:                 zeroForOne = itm1 > 0;

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

999:             if (isLong == 0) {

1066:             moved = isLong == 0

1078:             if (tokenType == 0) {

1085:         if (currentLiquidity.rightSlot() > 0) {

1279:         if (LeftRightSigned.unwrap(amountToCollect) != 0) {

1296:                 collected0 = movedInLeg.rightSlot() < 0

1299:                 collected1 = movedInLeg.leftSlot() < 0

1469:             if (netLiquidity != 0) {

```
([355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L355-L355),[362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L362-L362),[372](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L372-L372),[412](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L412-L412),[419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L419-L419),[446](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L446-L446),[453](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L453-L453),[632](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L632-L632),[633](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L633-L633),[688](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L688-L688),[702](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L702-L702),[717](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L717-L717),[787](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L787-L787),[819](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L819-L819),[823](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L823-L823),[824](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L824-L824),[827](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L827-L827),[833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L833-L833),[999](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L999-L999),[1066](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1066-L1066),[1078](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1078-L1078),[1085](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1085-L1085),[1279](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1279-L1279),[1296](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1296-L1296),[1299](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1299-L1299),[1469](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1469-L1469))
```solidity
File: contracts/libraries/FeesCalc.sol

67:                 if (tokenId.isLong(leg) == 0) {

```
([67](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L67-L67))
```solidity
File: contracts/libraries/Math.sol

74:         return x > 0 ? x : -x;

83:             return x > 0 ? uint256(x) : uint256(-x);

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
([74](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L74-L74),[83](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L83-L83),[130](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L130-L130),[133](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L133-L133),[137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L137-L137),[139](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L139-L139),[141](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L141-L141),[143](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L143-L143),[145](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L145-L145),[147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L147-L147),[149](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L149-L149),[151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L151-L151),[153](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L153-L153),[155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L155-L155),[157](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L157-L157),[159](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L159-L159),[161](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L161-L161),[163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L163-L163),[165](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L165-L165),[167](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L167-L167),[169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L169-L169),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L171-L171),[173](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L173-L173),[176](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L176-L176),[179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L179-L179),[312](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L312-L312),[360](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L360-L360),[361](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L361-L361),[447](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L447-L447),[474](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L474-L474),[537](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L537-L537),[587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L587-L587),[614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L614-L614),[664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L664-L664),[691](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L691-L691))
```solidity
File: contracts/libraries/PanopticMath.sol

77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

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

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

931:             if (balanceShortage > 0) {

949:             if (balanceShortage > 0) {

```
([77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L77-L77),[325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L325-L325),[357](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L357-L357),[358](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L358-L358),[425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L425-L425),[475](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L475-L475),[479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L479-L479),[532](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L532-L532),[537](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L537-L537),[555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L555-L555),[564](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L564-L564),[584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L584-L584),[615](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L615-L615),[618](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L618-L618),[856](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L856-L856),[857](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L857-L857),[931](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L931-L931),[949](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L949-L949))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

112:         if (to.code.length != 0) {

163:         if (to.code.length != 0) {

222:         if (to.code.length != 0) {

224:                 ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
                     ERC1155Holder.onERC1155Received.selector

```
([112](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L112-L112),[163](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L163-L163),[222](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L222-L222),[224](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L224-L225))
```solidity
File: contracts/types/TokenId.sol

465:         if (i == 0)

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

508:                 if (self.optionRatio(i) == 0) {

512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

```
([465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L465-L465),[501](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L501-L501),[508](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L508-L508),[512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L512-L512),[528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L528-L528))
### <a name="GAS-48"></a>[GAS-48] Use assembly in place of `abi.decode` to extract calldata values more efficiently
Using inline assembly to extract calldata values can be more gas-efficient than using `abi.decode` in Solidity. Inline assembly gives more direct access to EVM operations, enabling optimized usage of calldata. However, assembly should be used judiciously as it's more prone to errors. Opt for this approach when performance is critical and the complexity it introduces is manageable

*There are 3 Instances of this issue* :
```solidity
File: contracts/PanopticFactory.sol

177:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

```
([177](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L177-L177))
```solidity
File: contracts/SemiFungiblePositionManager.sol

408:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

441:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

```
([408](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L408-L408),[441](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L441-L441))
### <a name="GAS-49"></a>[GAS-49] Use `byte32` in place of `string`
For strings of 32 char strings and below you can use bytes32 instead as it's more gas efficient

*There are 16 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

70:     string internal constant TICKER_PREFIX = "po";

73:     string internal constant NAME_PREFIX = "POPT-V1";

289:     function name() external view returns (string memory) {

303:     function symbol() external view returns (string memory) {

```
([70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L70-L70),[73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L73-L73),[289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L289-L289),[303](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L303-L303))
```solidity
File: contracts/libraries/InteractionHelper.sol

53:         string memory prefix

54:     ) external view returns (string memory) {

58:         string memory symbol0;

59:         string memory symbol1;

60:         try IERC20Metadata(token0).symbol() returns (string memory _symbol) {

65:         try IERC20Metadata(token1).symbol() returns (string memory _symbol) {

72:                 string.concat(

93:         string memory prefix

94:     ) external view returns (string memory) {

97:         try IERC20Metadata(token).symbol() returns (string memory tokenSymbol) {

98:             return string.concat(prefix, tokenSymbol);

100:             return string.concat(prefix, "???");

```
([53](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L53-L53),[54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L54-L54),[58](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L58-L58),[59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L59-L59),[60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L60-L60),[65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L65-L65),[72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L72-L72),[93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L93-L93),[94](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L94-L94),[97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L97-L97),[98](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L98-L98),[100](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L100-L100))


*There are 82 Instances of this issue* :
```solidity
File: contracts/libraries/CallbackLib.sol

30:     function validateCallback(
            address sender,
            IUniswapV3Factory factory,
            PoolFeatures memory features
        ) internal view {

```
([30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L30-L34))
```solidity
File: contracts/libraries/Math.sol

25:     function min24(int24 a, int24 b) internal pure returns (int24) {

33:     function max24(int24 a, int24 b) internal pure returns (int24) {

41:     function min(uint256 a, uint256 b) internal pure returns (uint256) {

49:     function min(int256 a, int256 b) internal pure returns (int256) {

57:     function max(uint256 a, uint256 b) internal pure returns (uint256) {

65:     function max(int256 a, int256 b) internal pure returns (int256) {

73:     function abs(int256 x) internal pure returns (int256) {

81:     function absUint(int256 x) internal pure returns (uint256) {

91:     function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {

221:     function getAmountsForLiquidity(
             int24 currentTick,
             LiquidityChunk liquidityChunk
         ) internal pure returns (uint256 amount0, uint256 amount1) {

241:     function getLiquidityForAmount0(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount0
         ) internal pure returns (LiquidityChunk) {

271:     function getLiquidityForAmount1(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount1
         ) internal pure returns (LiquidityChunk) {

302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {

318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

440:     function mulDivRoundingUp(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {

458:     function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

584:     function mulDiv96RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

661:     function mulDiv128RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

675:     function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

738:     function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

776:     function sort(int256[] memory data) internal pure returns (int256[] memory) {

```
([25](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L25-L25),[33](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L33-L33),[41](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L41-L41),[49](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L49-L49),[57](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L57-L57),[65](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L65-L65),[73](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L73-L73),[81](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L81-L81),[91](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L91-L91),[221](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L221-L224),[241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L241-L245),[271](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L271-L275),[302](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L302-L302),[311](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L311-L311),[318](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L318-L318),[325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L325-L325),[440](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L440-L444),[458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L458-L458),[584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L584-L584),[661](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L661-L661),[675](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L675-L675),[738](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L738-L738),[776](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L776-L776))
```solidity
File: contracts/libraries/PanopticMath.sol

47:     function getPoolId(address univ3pool) internal view returns (uint64) {

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

92:     function updatePositionsHash(
            uint256 existingHash,
            TokenId tokenId,
            bool addFlag
        ) internal pure returns (uint256) {

289:     function getLiquidityChunk(
             TokenId tokenId,
             uint256 legIndex,
             uint128 positionSize
         ) internal pure returns (LiquidityChunk) {

338:     function getTicks(
             int24 strike,
             int24 width,
             int24 tickSpacing
         ) internal pure returns (int24 tickLower, int24 tickUpper) {

371:     function getRangesFromStrike(
             int24 width,
             int24 tickSpacing
         ) internal pure returns (int24, int24) {

390:     function computeExercisedAmounts(
             TokenId tokenId,
             uint128 positionSize
         ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {

468:     function convertNotional(
             uint128 contractSize,
             int24 tickLower,
             int24 tickUpper,
             uint256 asset
         ) internal pure returns (uint128) {

```
([47](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L47-L47),[59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L59-L59),[92](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L92-L96),[289](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L289-L293),[338](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L338-L342),[371](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L371-L374),[390](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L390-L393),[468](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L468-L473))
```solidity
File: contracts/libraries/SafeTransferLib.sol

21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:     function safeTransfer(address token, address to, uint256 amount) internal {

```
([21](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L21-L21),[52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L52-L52))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

214:     function _mint(address to, uint256 id, uint256 amount) internal {

236:     function _burn(address from, uint256 id, uint256 amount) internal {

```
([214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L214-L214),[236](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L236-L236))
```solidity
File: contracts/tokens/ERC20Minimal.sol

103:     function _transferFrom(address from, address to, uint256 amount) internal {

122:     function _mint(address to, uint256 amount) internal {

136:     function _burn(address from, uint256 amount) internal {

```
([103](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L103-L103),[122](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L122-L122),[136](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L136-L136))
```solidity
File: contracts/types/LeftRight.sol

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
([39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L39-L39),[46](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L46-L46),[59](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L59-L62),[78](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L78-L81),[101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L101-L101),[108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L108-L108),[121](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L121-L124),[134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L134-L134),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L148-L151),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L171-L174),[194](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L194-L194),[214](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L214-L214),[232](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L232-L232),[251](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L251-L254),[279](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L279-L284))
```solidity
File: contracts/types/LiquidityChunk.sol

70:     function createChunk(
            int24 _tickLower,
            int24 _tickUpper,
            uint128 amount
        ) internal pure returns (LiquidityChunk) {

89:     function addLiquidity(
            LiquidityChunk self,
            uint128 amount
        ) internal pure returns (LiquidityChunk) {

102:     function addTickLower(
             LiquidityChunk self,
             int24 _tickLower
         ) internal pure returns (LiquidityChunk) {

118:     function addTickUpper(
             LiquidityChunk self,
             int24 _tickUpper
         ) internal pure returns (LiquidityChunk) {

135:     function updateTickLower(
             LiquidityChunk self,
             int24 _tickLower
         ) internal pure returns (LiquidityChunk) {

151:     function updateTickUpper(
             LiquidityChunk self,
             int24 _tickUpper
         ) internal pure returns (LiquidityChunk) {

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```
([70](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L70-L74),[89](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L89-L92),[102](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L102-L105),[118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L118-L121),[135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L135-L138),[151](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L151-L154),[171](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L171-L171),[180](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L180-L180),[189](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L189-L189))
```solidity
File: contracts/types/TokenId.sol

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
([87](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L87-L87),[96](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L96-L96),[108](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L108-L108),[118](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L118-L118),[128](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L128-L128),[138](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L138-L138),[148](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L148-L148),[158](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L158-L158),[169](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L169-L169),[183](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L183-L183),[193](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L193-L193),[336](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L336-L346),[366](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L366-L366),[404](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L404-L404),[416](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L416-L419),[432](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L432-L432),[464](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L464-L464),[500](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L500-L500),[578](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L578-L578))
### <a name="GAS-50"></a>[GAS-50] Use `x = x + y` instead of `x += y` for state variables(Not captured by 4nalyzer)
Using `x = x + y` instead of `x += y` for simple state variables can save 10 gas. The same applies to `-=` , `*=` , etc.

*There are 3 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol


552:             s_poolAssets -= uint128(assets);

612:             s_poolAssets -= uint128(assets);

```
([552](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L552-L552),[612](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L612-L612))


```solidity
File: contracts/tokens/ERC20Minimal.sol


142:             totalSupply -= amount;

```
([142](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L142-L142))

### <a name="GAS-51"></a>[GAS-51] Use solady library where possible to save gas
The following OpenZeppelin imports have a Solady equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible

*There are 5 Instances of this issue* :
```solidity
File: contracts/PanopticFactory.sol

14: import {Clones} from "@openzeppelin/contracts/proxy/Clones.sol";

```
([14](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L14-L14))
```solidity
File: contracts/PanopticPool.sol

9: import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";

```
([9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L9-L9))
```solidity
File: contracts/libraries/InteractionHelper.sol

6: import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

10: import {Strings} from "@openzeppelin/contracts/utils/Strings.sol";

```
([6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L6-L6),[10](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L10-L10))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

5: import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";

```
([5](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L5-L5))

### <a name="GAS-52"></a>[GAS-52] Variable declared within iteration
Please elaborate and generalise the following with detail and feel free to use your own knowledge and lmit ur words to 100 words please:

*There are 102 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

667:                     int24 range = int24(

681:                 uint256 currentValue0;

682:                 uint256 currentValue1;

683:                 uint256 oracleValue0;

684:                 uint256 oracleValue1;

687:                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

704:                 uint256 tokenType = positionId.tokenType(leg);

1210:             TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);

1213:             uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();

1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

1219:             uint256 _tokenRequired = _getRequiredCollateralAtTickSinglePosition(

```
([667](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L667-L667),[681](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L681-L681),[682](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L682-L682),[683](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L683-L683),[684](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L684-L684),[687](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L687-L687),[704](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L704-L704),[1210](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1210-L1210),[1213](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1213-L1213),[1216](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1216-L1216),[1219](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1219-L1219))

```solidity
File: contracts/PanopticFactory.sol

304:             uint256 rarity = PanopticMath.numberOfLeadingHexZeros(

```
([304](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L304-L304))
```solidity
File: contracts/PanopticPool.sol

442:             TokenId tokenId = positionIdList[k];

448:                 LeftRightSigned[4] memory premiaByLeg,

449:                 uint256[2][4] memory premiumAccumulatorsByLeg

458:             uint256 numLegs = tokenId.countLegs();

459:             for (uint256 leg = 0; leg < numLegs; ) {

461:                     bytes32 chunkKey = keccak256(

461:                     bytes32 chunkKey = keccak256(

469:                     LeftRightUnsigned availablePremium = _getAvailablePremium(

469:                     LeftRightUnsigned availablePremium = _getAvailablePremium(

748:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);

748:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);

749:             uint256 isLong = tokenId.isLong(leg);

751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

803:             LeftRightSigned paidAmounts;

867:                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);

867:                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);

1519:             uint256 isLong = tokenId.isLong(leg);

1521:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

1526:                 uint256 tokenType = tokenId.tokenType(leg);

1540:                     LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];

1673:             bytes32 chunkKey = keccak256(

1680:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

1687:                 uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);

1706:                 uint256[2] memory grossCurrent;

1719:                     LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];

1721:                     uint256 positionLiquidity = liquidityChunk.liquidity();

1723:                     uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;

1853:             LeftRightSigned legPremia = premiaByLeg[leg];

1855:             bytes32 chunkKey = keccak256(

1860:             LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);

1877:                     uint256 positionLiquidity = PanopticMath

1882:                     uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);

1884:                     uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;

1886:                     LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];

1888:                     LeftRightUnsigned availablePremium = _getAvailablePremium(

1923:                         uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;

1924:                         uint256 _leg = leg;

```
([442](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L442-L442),[448](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L448-L448),[449](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L449-L449),[458](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L458-L458),[459](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L459-L459),[461](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L461-L461),[461](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L461-L461),[469](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L469-L469),[469](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L469-L469),[748](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L748-L748),[748](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L748-L748),[749](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L749-L749),[751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L751-L751),[751](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L751-L751),[803](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L803-L803),[867](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L867-L867),[867](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L867-L867),[1519](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1519-L1519),[1521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1521-L1521),[1526](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1526-L1526),[1540](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1540-L1540),[1673](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1673-L1673),[1680](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1680-L1680),[1687](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1687-L1687),[1706](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1706-L1706),[1719](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1719-L1719),[1721](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1721-L1721),[1723](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1723-L1723),[1853](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1853-L1853),[1855](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1855-L1855),[1860](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1860-L1860),[1877](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1877-L1877),[1882](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1882-L1882),[1884](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1884-L1884),[1886](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1886-L1886),[1888](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1888-L1888),[1923](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1923-L1923),[1924](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1924-L1924))

```solidity
File: contracts/SemiFungiblePositionManager.sol

604:             LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

611:             bytes32 positionKey_from = keccak256(

620:             bytes32 positionKey_to = keccak256(

637:             LeftRightUnsigned fromLiq = s_accountLiquidity[positionKey_from];

641:             LeftRightSigned fromBase = s_accountFeesBase[positionKey_from];

883:             LeftRightSigned _moved;

884:             LeftRightSigned _itmAmounts;

885:             LeftRightUnsigned _collectedSingleLeg;

889:                 IUniswapV3Pool _univ3pool = univ3pool;

890:                 TokenId _tokenId = tokenId;

891:                 bool _isBurn = isBurn;

892:                 uint128 _positionSize = positionSize;

893:                 uint256 _leg;

904:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

```
([604](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L604-L604),[611](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L611-L611),[620](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L620-L620),[637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L637-L637),[641](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L641-L641),[883](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L883-L883),[884](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L884-L884),[885](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L885-L885),[889](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L889-L889),[890](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L890-L890),[891](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L891-L891),[892](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L892-L892),[893](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L893-L893),[904](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L904-L904))
```solidity
File: contracts/libraries/FeesCalc.sol

52:             TokenId tokenId = positionIdList[k];

53:             uint128 positionSize = userBalance[tokenId].rightSlot();

54:             uint256 numLegs = tokenId.countLegs();

55:             for (uint256 leg = 0; leg < numLegs; ) {

56:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

56:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(

62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(

62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(

62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(

```
([52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L52-L52),[53](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L53-L53),[54](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L54-L54),[55](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L55-L55),[56](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L56-L56),[56](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L56-L56),[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L62-L62),[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L62-L62),[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L62-L62),[62](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L62-L62))
```solidity
File: contracts/libraries/PanopticMath.sol

397:             (LeftRightSigned longs, LeftRightSigned shorts) = _calculateIOAmounts(

397:             (LeftRightSigned longs, LeftRightSigned shorts) = _calculateIOAmounts(

782:                 TokenId tokenId = positionIdList[i];

783:                 uint256 numLegs = tokenId.countLegs();

784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {

861:                 TokenId tokenId = positionIdList[i];

862:                 LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;

863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

865:                         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
                                 storage _settledTokens = settledTokens;

865:                         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
                                 storage _settledTokens = settledTokens;

869:                         uint256 settled0 = Math.unsafeDivRoundingUp(

869:                         uint256 settled0 = Math.unsafeDivRoundingUp(

873:                         uint256 settled1 = Math.unsafeDivRoundingUp(

873:                         uint256 settled1 = Math.unsafeDivRoundingUp(

878:                         bytes32 chunkKey = keccak256(

878:                         bytes32 chunkKey = keccak256(

```
([397](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L397-L397),[397](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L397-L397),[782](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L782-L782),[783](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L783-L783),[784](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L784-L784),[861](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L861-L861),[862](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L862-L862),[863](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L863-L863),[865](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L865-L866),[865](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L865-L866),[869](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L869-L869),[869](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L869-L869),[873](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L873-L873),[873](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L873-L873),[878](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L878-L878),[878](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L878-L878))
```solidity
File: contracts/multicall/Multicall.sol

15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);

15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);

```
([15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L15-L15),[15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L15-L15))
```solidity
File: contracts/types/TokenId.sol

519:                 uint256 numLegs = self.countLegs();

520:                 for (uint256 j = i + 1; j < numLegs; ++j) {

538:                 uint256 riskPartnerIndex = self.riskPartner(i);

551:                     uint256 _isLong = self.isLong(i);

552:                     uint256 isLongP = self.isLong(riskPartnerIndex);

555:                     uint256 _tokenType = self.tokenType(i);

556:                     uint256 tokenTypeP = self.tokenType(riskPartnerIndex);

582:                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(

582:                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(

587:                 int24 _strike = self.strike(i);

```
([519](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L519-L519),[520](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L520-L520),[538](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L538-L538),[551](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L551-L551),[552](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L552-L552),[555](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L555-L555),[556](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L556-L556),[582](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L582-L582),[582](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L582-L582),[587](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L587-L587))
### <a name="GAS-53"></a>[GAS-53] Enable IR-based code generation
Enabling Intermediate Representation (IR)-based code generation in Solidity, via the --via-ir compiler flag or setting {'viaIR': true} in the configuration, activates an advanced optimization phase. This approach allows the compiler to perform more sophisticated optimizations across multiple functions, potentially leading to significant gas savings. IR-based compilation can optimize contract bytecode more efficiently, making smart contracts cheaper to deploy and execute by reducing the gas required for transactions

*There are 20 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {

```
([36](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36-L36))
```solidity
File: contracts/PanopticFactory.sol

26: contract PanopticFactory is Multicall {

```
([26](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L26-L26))
```solidity
File: contracts/PanopticPool.sol

27: contract PanopticPool is ERC1155Holder, Multicall {

```
([27](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L27-L27))
```solidity
File: contracts/SemiFungiblePositionManager.sol

72: contract SemiFungiblePositionManager is ERC1155, Multicall {

```
([72](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L72-L72))
```solidity
File: contracts/libraries/CallbackLib.sol

12: library CallbackLib {

```
([12](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L12-L12))
```solidity
File: contracts/libraries/Constants.sol

7: library Constants {

```
([7](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L7-L7))
```solidity
File: contracts/libraries/Errors.sol

7: library Errors {

```
([7](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L7-L7))
```solidity
File: contracts/libraries/FeesCalc.sol

39: library FeesCalc {

```
([39](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L39-L39))
```solidity
File: contracts/libraries/InteractionHelper.sol

17: library InteractionHelper {

```
([17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17-L17))
```solidity
File: contracts/libraries/Math.sol

13: library Math {

```
([13](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L13-L13))
```solidity
File: contracts/libraries/PanopticMath.sol

18: library PanopticMath {

```
([18](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18-L18))
```solidity
File: contracts/libraries/SafeTransferLib.sol

11: library SafeTransferLib {

```
([11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L11-L11))
```solidity
File: contracts/multicall/Multicall.sol

8: abstract contract Multicall {

```
([8](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L8-L8))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

11: abstract contract ERC1155 {

```
([11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L11-L11)
)
```solidity
File: contracts/tokens/ERC20Minimal.sol

9: abstract contract ERC20Minimal {

```
([9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L9-L9)
)
```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: interface IDonorNFT {

```
([6](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6-L6)
)
```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

11: interface IERC20Partial {

```
([11](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L11-L11)
)
```solidity
File: contracts/types/LeftRight.sol

17: library LeftRightLibrary {

```
([17](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L17-L17)
)
```solidity
File: contracts/types/LiquidityChunk.sol

52: library LiquidityChunkLibrary {

```
([52](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52-L52))
```solidity
File: contracts/types/TokenId.sol

60: library TokenIdLibrary {

```
([60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L60-L60))

### <a name="GAS-54"></a>[GAS-54] Using XOR (^) and AND (&) bitwise equivalents for gas optimizations
Given 4 variables a, b, c and d represented as such:

```

0 0 0 0 0 1 1 0 <- a
0 1 1 0 0 1 1 0 <- b
0 0 0 0 0 0 0 0 <- c
1 1 1 1 1 1 1 1 <- d

```

To have a == b means that every 0 and 1 match on both variables. Meaning that a XOR (operator ^) would evaluate to 0 ((a ^ b) == 0), as it excludes by definition any equalities.Now, if a != b, this means that there’s at least somewhere a 1 and a 0 not matching between a and b, making (a ^ b) != 0.Both formulas are logically equivalent and using the XOR bitwise operator costs actually the same amount of gas.However, it is much cheaper to use the bitwise OR operator (|) than comparing the truthy or falsy values.These are logically equivalent too, as the OR bitwise operator (|) would result in a 1 somewhere if any value is not 0 between the XOR (^) statements, meaning if any XOR (^) statement verifies that its arguments are different.

*There are 88 Instances of this issue* :
```solidity
File: contracts/CollateralTracker.sol

512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

664:                 if (positionId.isLong(leg) == 0) continue;

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

709:                     (tokenType == 1 && currentValue0 < oracleValue0)

1286:             tokenId.riskPartner(index) == index // does this leg have a risk partner? Affects required collateral

1325:         uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();

1328:         int64 utilization = tokenType == 0

1339:             if (isLong == 0) {

1346:                     ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1

1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1362:                     uint160 ratio = tokenType == 1 // tokenType

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1451:             if (isLong == 1) {

1479:         if (isLong == 0) {

1488:         } else if (isLong == 1) {

1544:                 if (tokenType == 0) {

1559:                 if (tokenType == 1) {

1582:                 tokenType == 0 ? movedRight : movedLeft,

1584:                 tokenType == 0

1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```
([512](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L512-L512),[575](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L575-L575),[664](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L664-L664),[708](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L708-L708),[709](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L709-L709),[1286](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1286-L1286),[1325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1325-L1325),[1328](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1328-L1328),[1339](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1339-L1339),[1346](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1346-L1346),[1347](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1347-L1347),[1362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1362-L1362),[1374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1374-L1374),[1375](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1375-L1375),[1451](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1451-L1451),[1479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1479-L1479),[1488](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1488-L1488),[1544](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1544-L1544),[1559](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1559-L1559),[1582](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1582-L1582),[1584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1584-L1584),[1637](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1637-L1637),[1638](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1638-L1638))
```solidity
File: contracts/PanopticFactory.sol

227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

351:             if (token0 == WETH) {

355:             } else if (token1 == WETH) {

```
([227](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L227-L227),[351](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L351-L351),[355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L355-L355))
```solidity
File: contracts/PanopticPool.sol

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

504:         if (tickLimitLow == tickLimitHigh) {

768:             if (isLong == 1) {

865:             if (tokenId.isLong(leg) == 0) {

1483:         if (netLiquidity == 0) return;

1520:             if ((isLong == 1) || computeAllPremia) {

1566:                     if (isLong == 1) {

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1679:             if (tokenId.isLong(leg) == 0) {

1780:                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),

1789:                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),

1864:                 if (tokenId.isLong(leg) == 1) {

```
([460](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L460-L460),[504](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L504-L504),[768](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L768-L768),[865](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L865-L865),[1483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1483-L1483),[1520](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1520-L1520),[1566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1566-L1566),[1596](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1596-L1596),[1679](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1679-L1679),[1780](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1780-L1780),[1789](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1789-L1789),[1864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1864-L1864))
```solidity
File: contracts/SemiFungiblePositionManager.sol

355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

702:         if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

999:             if (isLong == 0) {

1066:             moved = isLong == 0

1073:             if (tokenType == 1) {

1078:             if (tokenType == 0) {

1275:         if (isLong == 1) {

1514:                 acctPremia = isLong == 1 ? premiumOwed : premiumGross;

1518:             acctPremia = isLong == 1

```
([355](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L355-L355),[688](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L688-L688),[702](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L702-L702),[833](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L833-L833),[999](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L999-L999),[1066](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1066-L1066),[1073](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1073-L1073),[1078](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1078-L1078),[1275](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1275-L1275),[1514](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1514-L1514),[1518](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1518-L1518))
```solidity
File: contracts/libraries/FeesCalc.sol

67:                 if (tokenId.isLong(leg) == 0) {

```
([67](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L67-L67))
```solidity
File: contracts/libraries/Math.sol

179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

360:             if (prod1 == 0) {

474:             if (prod1 == 0) {

537:             if (prod1 == 0) {

614:             if (prod1 == 0) {

691:             if (prod1 == 0) {

757:             if (i == j) return;

```
([179](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L179-L179),[319](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L319-L319),[360](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L360-L360),[474](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L474-L474),[537](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L537-L537),[614](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L614-L614),[691](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L691-L691),[757](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L757-L757))
```solidity
File: contracts/libraries/PanopticMath.sol

77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

211:                     if (rank == 7) {

325:         if (tokenId.asset(legIndex) == 0) {

425:         if (tokenType == 0) {

475:             uint256 notional = asset == 0

479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

584:         if (tokenId.asset(legIndex) == 0) {

615:         bool isShort = tokenId.isLong(legIndex) == 0;

618:         if (tokenId.tokenType(legIndex) == 0) {

785:                     if (tokenId.isLong(leg) == 1) {

864:                     if (tokenId.isLong(leg) == 1) {

```
([77](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L77-L77),[211](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L211-L211),[325](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L325-L325),[425](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L425-L425),[475](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L475-L475),[479](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L479-L479),[584](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L584-L584),[615](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L615-L615),[618](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L618-L618),[785](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L785-L785),[864](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L864-L864))
```solidity
File: contracts/tokens/ERC1155Minimal.sol

101:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

202:             interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

203:             interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

```
([101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L101-L101),[137](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L137-L137),[202](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L202-L202),[203](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L203-L203))
```solidity
File: contracts/types/LeftRight.sol

290:         bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);

291:         bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);

```
([290](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L290-L290),[291](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L291-L291))
```solidity
File: contracts/types/TokenId.sol

465:         if (i == 0)

471:         if (i == 1)

477:         if (i == 2)

483:         if (i == 3)

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

508:                 if (self.optionRatio(i) == 0) {

521:                     if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

531:                     (self.strike(i) == Constants.MIN_V3POOL_TICK) ||

532:                     (self.strike(i) == Constants.MAX_V3POOL_TICK)

560:                     if ((_isLong == isLongP) && (_tokenType == tokenTypeP))

566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

592:                     if (self.isLong(i) == 1) return; // validated

```
([465](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L465-L465),[471](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L471-L471),[477](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L477-L477),[483](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L483-L483),[501](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L501-L501),[508](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L508-L508),[521](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L521-L521),[528](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L528-L528),[531](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L531-L531),[532](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L532-L532),[560](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L560-L560),[566](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L566-L566),[592](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L592-L592))
