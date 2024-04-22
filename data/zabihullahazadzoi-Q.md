# Low risk Issues

#### *Note*: All findings in 4naly3er automated report are excluded.


| |Issue|Instances|
|-|:-|:-:|
| [L-1](#L-1) | Addition/multiplication in `unchecked` block is unsafe | 83 |
| [L-2](#L-2) | Code does not follow the best practice of check-effects-interaction | 30 |
| [L-3](#L-3) | Consider implementing two-step procedure for updating protocol addresses | 2 |
| [L-4](#L-4) | External calls in modifiers should be avoided | 1 |
| [L-5](#L-5) | File allows a version of solidity that is susceptible to .selector-related optimizer bug | 3 |
| [L-6](#L-6) | Function can return unassigned variable | 11 |
| [L-7](#L-7) | Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard | 2 |
| [L-8](#L-8) | Missing checks for `address(0x0)` in the constructor | 1 |
| [L-9](#L-9) | Missing checks for `address(0x0)` in the initializer | 1 |
| [L-10](#L-10) | Missing contract-existence checks before low-level calls | 1 |
| [L-11](#L-11) | Missing contract-existence checks before yul `call()` | 2 |
| [L-12](#L-12) | Revert on transfer to the zero address | 2 |
| [L-13](#L-13) | Some tokens do not consider `type(uint256).max` as an infinite approval | 4 |
| [L-14](#L-14) | Unsafe conversion from unsigned to signed values | 79 |
| [L-15](#L-15) | Use of abi.encodePacked with dynamic types inside keccak256 | 6 |
| [L-16](#L-16) | Using zero as a parameter | 6 |


## [L-1] Addition/multiplication in `unchecked` block is unsafe
The additions/multiplications may silently overflow because they’re in `unchecked` blocks with no preceding value checks, which may lead to unexpected results.

**Total Instances:** 83

```solidity
File: contracts/CollateralTracker.sol

                         (12500 * ratioTick) /

 262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

 372:             return s_poolAssets + s_inAMM;

 403:                 assets * (DECIMALS - COMMISSION_FEE),
                     totalSupply,
                     totalAssets() * DECIMALS

 446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

 463:                 shares * DECIMALS,
                     totalAssets(),
                     totalSupply * (DECIMALS - COMMISSION_FEE)

 732:                 .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));

 743:             return int256((s_inAMM * DECIMALS) / totalAssets());

 796:                 min_sell_ratio +
                     ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /

 849:                 (BUYER_COLLATERAL_RATIO +
                         (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /

 1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

 1084:             s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));

 1110:                     s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),
                          DECIMALS
                      );
      
                      // set the exchanged amount to the sum of the intrinsic value and swapCommission
                      exchangedAmount = intrinsicValue + int256(swapCommission);
                  }
      
                  //compute total commission amount = commission rate + spread fee
                  exchangedAmount += int256(
                      Math.unsafeDivRoundingUp(
                          uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,

 1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)
                              ); // calls -> strike/price
      
                          // compute the collateral requirement depending on whether the position is ITM & out-of-range or ITM and in-range:
      
                          /// ITM and out-of-range
                          if (
                              ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1
                              ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0
                          ) {
                              /**
                                          Short put BPR = 100% - (price/strike) + SCR
      
                                 BUYING
                                 POWER
                                 REQUIREMENT
                               
                                               ^               .         .
                                               |        <- ITM . <-ATM-> . OTM ->
                                 100% + SCR% - |--__           .    .    .
                                        100% - | . .¯¯--__     .    .    .
                                               |    .     ¯¯--__    .    .
                                         SCR - |    .          .¯¯--__________
                                               |    .          .    .    .
                                               +----+----------+----+----+--->   current
                                               0   Liqui-     Pa  strike Pb       price
                                                   dation
                                                   price = SCR*strike                                         
                               */
      
                              uint256 c2 = Constants.FP96 - ratio;
      
                              // compute the tokens required
                              // position is in-the-money, collateral requirement = amountMoved*(1-ratio) + SCR*amountMoved
                              required += Math.mulDiv96RoundingUp(amountMoved, c2);
                          } else {
                              // position is in-range (ie. current tick is between upper+lower tick): we draw a line between the
                              // collateral requirement at the lowerTick and the one at the upperTick. We use that interpolation as
                              // the collateral requirement when in-range, which always over-estimates the amount of token required
                              // Specifically:
                              //  required = amountMoved * (scaleFactor - ratio) / (scaleFactor + 1) + sellCollateralRatio*amountMoved
                              uint160 scaleFactor = Math.getSqrtRatioAtTick(
                                  (tickUpper - strike) + (strike - tickLower)
                              );
                              uint256 c3 = Math.mulDivRoundingUp(
                                  amountMoved,
                                  scaleFactor - ratio,
                                  scaleFactor + Constants.FP96

 1486:                 required = Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS);

 1496:                 required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);

 1572:                     : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

 1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L202

```solidity
File: contracts/PanopticFactory.sol

 300:             maxSalt = uint256(salt) + loops;

 323:                 salt = bytes32(uint256(salt) + 1);

 392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L300

```solidity
File: contracts/PanopticPool.sol

 309:                 (uint256(block.timestamp) << 216) +

 730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

 1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

 1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +
                      Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);
                  // the amount of cross-collateral balance needed for the account to be solvent, computed in terms of liquidity
                  // overstimate by rounding up
                  thresholdCross =
                      Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

 1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

 1559:                                     ((premiumAccumulatorsByLeg[leg][1] -

 1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

 1737:                                 (grossCurrent[1] *

 1768:             uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *
                      totalLiquidity) / 2 ** 64;
                  uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *
                      totalLiquidity) / 2 ** 64;
      
                  return (
                      LeftRightUnsigned
                          .wrap(0)
                          .toRightSlot(
                              uint128(
                                  Math.min(
                                      (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /

 1820:             totalLiquidity = accountLiquidities.rightSlot() + accountLiquidities.leftSlot();

 1952:                                                 (int256(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L309

```solidity
File: contracts/SemiFungiblePositionManager.sol

 388:             s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;

 842:                     ? Constants.MIN_V3POOL_SQRT_RATIO + 1

 1340:             uint256 totalLiquidity = netLiquidity + removedLiquidity;
      
                  uint256 premium0X64_base;
                  uint256 premium1X64_base;
      
                  {
                      uint128 collected0 = collectedAmounts.rightSlot();
                      uint128 collected1 = collectedAmounts.leftSlot();
      
                      // compute the base premium as collected * total / net^2 (from Eqn 3)
                      premium0X64_base = Math.mulDiv(
                          collected0,
                          totalLiquidity * 2 ** 64,
                          netLiquidity ** 2
                      );
                      premium1X64_base = Math.mulDiv(
                          collected1,
                          totalLiquidity * 2 ** 64,
                          netLiquidity ** 2
                      );
                  }
      
                  {
                      uint128 premium0X64_owed;
                      uint128 premium1X64_owed;
                      {
                          // compute the owed premium (from Eqn 3)
                          uint256 numerator = netLiquidity + (removedLiquidity / 2 ** VEGOID);
      
                          premium0X64_owed = Math
                              .mulDiv(premium0X64_base, numerator, totalLiquidity)
                              .toUint128Capped();
                          premium1X64_owed = Math
                              .mulDiv(premium1X64_base, numerator, totalLiquidity)
                              .toUint128Capped();
      
                          deltaPremiumOwed = LeftRightUnsigned
                              .wrap(0)
                              .toRightSlot(premium0X64_owed)
                              .toLeftSlot(premium1X64_owed);
                      }
                  }
      
                  {
                      uint128 premium0X64_gross;
                      uint128 premium1X64_gross;
                      {
                          // compute the gross premium (from Eqn 4)
                          uint256 numerator = totalLiquidity ** 2 -
                              totalLiquidity *

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L388

```solidity
File: contracts/libraries/Math.sol

 179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

 407:             prod0 |= prod1 * twos;
     
                 // Invert denominator mod 2**256
                 // Now that denominator is an odd number, it has an inverse
                 // modulo 2**256 such that denominator * inv = 1 mod 2**256.
                 // Compute the inverse by starting with a seed that is correct
                 // correct for four bits. That is, denominator * inv = 1 mod 2**4
                 uint256 inv = (3 * denominator) ^ 2;
                 // Now use Newton-Raphson iteration to improve the precision.
                 // Thanks to Hensel's lifting lemma, this also works in modular
                 // arithmetic, doubling the correct bits in each step.
                 inv *= 2 - denominator * inv; // inverse mod 2**8
                 inv *= 2 - denominator * inv; // inverse mod 2**16
                 inv *= 2 - denominator * inv; // inverse mod 2**32
                 inv *= 2 - denominator * inv; // inverse mod 2**64
                 inv *= 2 - denominator * inv; // inverse mod 2**128
                 inv *= 2 - denominator * inv; // inverse mod 2**256

 511:             prod0 |= prod1 * 2 ** 192;

 574:             prod0 |= prod1 * 2 ** 160;

 651:             prod0 |= prod1 * 2 ** 128;

 728:             prod0 |= prod1 * 2 ** 64;

 758:             int256 pivot = arr[uint256(left + (right - left) / 2)];

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L179

```solidity
File: contracts/libraries/PanopticMath.sol

 62:             return (poolId & TICKSPACING_MASK) + (uint48(poolId) + 1);

 108:                     : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);

 133:             int256[] memory tickCumulatives = new int256[](cardinality + 1);
     
                 uint256[] memory timestamps = new uint256[](cardinality + 1);
                 // get the last 4 timestamps/tickCumulatives (if observationIndex < cardinality, the index will wrap back from observationCardinality)
                 for (uint256 i = 0; i < cardinality + 1; ++i) {
                     (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
                         uint256(
                             (int256(observationIndex) - int256(i * period)) +

 183:             if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

 249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);
                 }
     
                 // observe the tickCumulative at the 20 pre-defined time slots
                 (int56[] memory tickCumulatives, ) = univ3pool.observe(secondsAgos);
     
                 // compute the average tick per 30s window
                 for (uint256 i = 0; i < 19; ++i) {
                     twapMeasurement[i] = int24(
                         (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

 346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;
                 int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;
     
                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(width, tickSpacing);
     
                 (tickLower, tickUpper) = (strike - rangeDown, strike + rangeUp);

 477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

 698:             int256 paid0 = bonus0 + int256(netExchanged.rightSlot());

 820:                 haircut1 = protocolLoss1 + collateralDelta1;
                 } else if (
                     longPremium.leftSlot() < collateralDelta1 &&
                     longPremium.rightSlot() > collateralDelta0
                 ) {
                     int256 protocolLoss0 = collateralDelta0;
                     (collateralDelta0, collateralDelta1) = (
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
                     );
     
                     haircut0 = collateralDelta0 + protocolLoss0;
                     haircut1 = longPremium.leftSlot();
                 } else {
                     // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
                     haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
                     haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
     
                     collateralDelta0 = 0;
                     collateralDelta1 = 0;
                 }
     
                 {
                     address _liquidatee = liquidatee;
                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
                 }
     
                 for (uint256 i = 0; i < positionIdList.length; i++) {
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

 938:                                 int256(
                                         PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
                                     ) + refundValues.leftSlot()
                                 )
                             );
                 }
     
                 balanceShortage =
                     refundValues.leftSlot() -
                     int256(collateral1.convertToAssets(collateral1.balanceOf(refunder)));
     
                 if (balanceShortage > 0) {
                     return
                         LeftRightSigned
                             .wrap(0)
                             .toLeftSlot(int128(refundValues.leftSlot() - balanceShortage))
                             .toRightSlot(
                                 int128(
                                     int256(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L62

```solidity
File: contracts/types/LeftRight.sol

 68:                     (LeftRightUnsigned.unwrap(self) & LEFT_HALF_BIT_MASK) +
                            uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)

 88:                     (LeftRightSigned.unwrap(self) & LEFT_HALF_BIT_MASK_INT) +
                            (int256(int128(LeftRightSigned.unwrap(self)) + right) & RIGHT_HALF_BIT_MASK)

 126:             return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));

 136:             return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));

 155:             z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));

 196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();
                 int128 left128 = int128(left);
     
                 if (left128 != left) revert Errors.UnderOverFlow();
     
                 int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();

 216:             int256 left256 = int256(x.leftSlot()) + y.leftSlot();
                 int128 left128 = int128(left256);
     
                 int256 right256 = int256(x.rightSlot()) + y.rightSlot();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L68

```solidity
File: contracts/types/LiquidityChunk.sol

 78:                     (uint256(uint24(_tickLower)) << 232) +

 94:             return LiquidityChunk.wrap(LiquidityChunk.unwrap(self) + amount);

 109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

 126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L78

```solidity
File: contracts/types/TokenId.sol

 110:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);

 120:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);

 130:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);

 140:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);

 150:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);

 160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

 171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

 185:             return TokenId.wrap(TokenId.unwrap(self) + _poolId);

 195:             return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

 212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));

 229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))

 246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));

 263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))

 281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))

 299:                     TokenId.unwrap(self) +
                             uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))

 319:                     TokenId.unwrap(self) +
                             (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))

 395:                         ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)

 406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

 520:                 for (uint256 j = i + 1; j < numLegs; ++j) {

 589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L589


## [L-2] Code does not follow the best practice of check-effects-interaction
Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

**Total Instances:** 30

```solidity
File: contracts/CollateralTracker.sol

 /// @audit  CollateralTokenAlreadyInitialized() prior to this assignment
 230:         s_initialized = true;

 /// @audit  CollateralTokenAlreadyInitialized() prior to this assignment
 238:         s_poolAssets = 1;

 /// @audit  CollateralTokenAlreadyInitialized() prior to this assignment
 241:         s_underlyingToken = underlyingIsToken0 ? token0 : token1;

 /// @audit  CollateralTokenAlreadyInitialized() prior to this assignment
 244:         s_panopticPool = panopticPool;

 /// @audit  safeTransferFrom() prior to this assignment
 436:             s_poolAssets += uint128(assets);

 /// @audit  safeTransferFrom() prior to this assignment
 496:             s_poolAssets += uint128(assets);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L230

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  NotOwner() prior to this assignment
 152:         s_owner = newOwner;

 /// @audit  InvalidSalt() prior to this assignment
 253:         s_getPanopticPool[v3Pool] = newPoolContract;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L152

```solidity
File: contracts/PanopticPool.sol

 /// @audit  slot0() prior to this assignment
 308:             s_miniMedian =

 /// @audit  computeInternalMedian() prior to this assignment
 533:         if (medianData != 0) s_miniMedian = medianData;

 /// @audit  InvalidTokenIdParameter() prior to this assignment
 654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned

 /// @audit  InvalidTokenIdParameter() prior to this assignment
 664:         if (medianData != 0) s_miniMedian = medianData;

 /// @audit  updatePositionsHash() prior to this assignment
 1416:         s_positionsHash[account] = newHash;

 /// @audit  liquidity() prior to this assignment
 1650:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(

 /// @audit  getLiquidityChunk() prior to this assignment
 1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned

 /// @audit  getLiquidityChunk() prior to this assignment
 1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned

 /// @audit  getLiquidityChunk() prior to this assignment
 1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned

 /// @audit  unwrap() prior to this assignment
 1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0

 /// @audit  unwrap() prior to this assignment
 1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0

 /// @audit  liquidity() prior to this assignment
 1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0

 /// @audit  liquidity() prior to this assignment
 1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L308

```solidity
File: contracts/SemiFungiblePositionManager.sol

 /// @audit  ReentrantCall() prior to this assignment
 325:         s_poolContext[poolId].locked = true;

 /// @audit  getLiquidityChunk() prior to this assignment
 644:             s_accountLiquidity[positionKey_to] = fromLiq;

 /// @audit  getLiquidityChunk() prior to this assignment
 644:             s_accountLiquidity[positionKey_to] = fromLiq;

 /// @audit  getLiquidityChunk() prior to this assignment
 645:             s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

 /// @audit  getLiquidityChunk() prior to this assignment
 645:             s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

 /// @audit  getLiquidityChunk() prior to this assignment
 647:             s_accountFeesBase[positionKey_to] = fromBase;

 /// @audit  getLiquidityChunk() prior to this assignment
 647:             s_accountFeesBase[positionKey_to] = fromBase;

 /// @audit  getLiquidityChunk() prior to this assignment
 648:             s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

 /// @audit  getLiquidityChunk() prior to this assignment
 648:             s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L648


## [L-3] Consider implementing two-step procedure for updating protocol addresses
A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must "accept" the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement [EIP-165](https://eips.ethereum.org/EIPS/eip-165), and to have the "set" functions ensure that the recipient is of the right interface type.

**Total Instances:** 2

```solidity
File: contracts/PanopticPool.sol

 1587:     function settleLongPremium(
              TokenId[] calldata positionIdList,
              address owner,
              uint256 legIndex
          ) external {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1587

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 81:     function setApprovalForAll(address operator, bool approved) public {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L81


## [L-4] External calls in modifiers should be avoided
External calls within modifiers can introduce unintended reentrancy risks and obscure the flow of a contract's logic. Modifiers are designed to perform checks before executing function logic, and using external calls can make the flow unpredictable due to the potential for state changes or reentrancy by the called contract. Such ambiguity makes code harder to audit and understand. To ensure clarity and security, avoid external calls in modifiers. Instead, place them in the function body, where their execution order and effects are more explicit. This practice enhances contract readability, aids auditors, and minimizes unexpected behaviors.

**Total Instances:** 1

```solidity
File: contracts/CollateralTracker.sol

 169:     modifier onlyPanopticPool() {
             if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L169


## [L-5] File allows a version of solidity that is susceptible to .selector-related optimizer bug
'In solidity versions prior to 0.8.21, there is a legacy code generation [bug](https://soliditylang.org/blog/2023/07/19/missing-side-effects-on-selector-access-bug/) where if `foo().selector` is called, `foo()` doesn't actually get evaluated. It is listed as low-severity, because projects usually use the contract name rather than a function call to look up the selector.'

**Total Instances:** 3

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 115:                 ERC1155Holder.onERC1155Received.selector

 166:                 ERC1155Holder.onERC1155BatchReceived.selector

 225:                 ERC1155Holder.onERC1155Received.selector

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L225


## [L-6] Function can return unassigned variable
Make sure that functions with a return value always return a valid and assigned value. Even if the default value is as expected, it should be assigned with the default value for code clarity and to reduce confusion.

**Total Instances:** 11

```solidity
File: contracts/CollateralTracker.sol

 /// @audit  s_underlyingToken is unassigned!
 362:         return s_underlyingToken;

 /// @audit  DECIMALS is unassigned!
 791:             return DECIMALS;

 /// @audit  BUYER_COLLATERAL_RATIO is unassigned!
 836:             return BUYER_COLLATERAL_RATIO;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L362

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  s_owner is unassigned!
 160:         return s_owner;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L160

```solidity
File: contracts/PanopticPool.sol

 /// @audit  s_univ3pool is unassigned!
 1426:         return s_univ3pool;

 /// @audit  s_collateralToken0 is unassigned!
 1432:         return s_collateralToken0;

 /// @audit  s_collateralToken1 is unassigned!
 1438:         return s_collateralToken1;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1426

```solidity
File: contracts/libraries/InteractionHelper.sol

 /// @audit  _decimals is unassigned!
 111:             return _decimals;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L111

```solidity
File: contracts/libraries/Math.sol

 /// @audit  data is unassigned!
 780:         return data;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L780

```solidity
File: contracts/libraries/PanopticMath.sol

 /// @audit  refundValues is unassigned!
 965:         return refundValues;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L965

```solidity
File: contracts/types/TokenId.sol

 /// @audit  self is unassigned!
 490:         return self;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L490


## [L-7] Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard
Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks opens the users of this protocol up to [read-only reentrancy vulnerability](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect them except by block-listing the entire protocol.

**Total Instances:** 2

```solidity
File: contracts/CollateralTracker.sol

 333:         return ERC20Minimal.transfer(recipient, amount);

 352:         return ERC20Minimal.transferFrom(from, to, amount);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L352


## [L-8] Missing checks for `address(0x0)` in the constructor
'Constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a checking, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could be due to an error or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it will be irretrievable. It's therefore crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.'

**Total Instances:** 1

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  _WETH9, _poolReference, _collateralReference not checked!
 115:     constructor(
             address _WETH9,
             SemiFungiblePositionManager _SFPM,
             IUniswapV3Factory _univ3Factory,
             IDonorNFT _donorNFT,
             address _poolReference,
             address _collateralReference
         ) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L115


## [L-9] Missing checks for `address(0x0)` in the initializer
Consider adding a zero address check for address type variables in the initializer

**Total Instances:** 1

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  _owner not checked!
 134:     function initialize(address _owner) public {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134


## [L-10] Missing contract-existence checks before low-level calls
Low-level calls return success if there is no code present at the specified address. In addition to the zero-address checks, add a check to verify that `<address>.code.length > 0`

**Total Instances:** 1

```solidity
File: contracts/multicall/Multicall.sol

 15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L15


## [L-11] Missing contract-existence checks before yul `call()`
Low-level calls return success if there is no code present at the specified address. In addition to the zero-address checks, add a check to verify that `extcodesize()` is non-zero.

**Total Instances:** 2

```solidity
File: contracts/libraries/SafeTransferLib.sol

 41:                 call(gas(), token, 0, p, 100, 0, 32)

 71:                 call(gas(), token, 0, p, 68, 0, 32)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L71


## [L-12] Revert on transfer to the zero address
It’s good practice to revert a token transfer transaction if the recipient’s address is the zero address. This can prevent unintentional transfers to the zero address due to accidental operations or programming errors. Many token contracts implement such a safeguard, such as `OpenZeppelin - ERC20`, `OpenZeppelin - ERC721`.

**Total Instances:** 2

```solidity
File: contracts/CollateralTracker.sol

 333:         return ERC20Minimal.transfer(recipient, amount);

 352:         return ERC20Minimal.transferFrom(from, to, amount);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L352


## [L-13] Some tokens do not consider `type(uint256).max` as an infinite approval
Some tokens such as [COMP](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L89-L91) downcast such approvals to uint96 and use that as a raw value rather than interpreting it as an infinite approval. Eventually these approvals will reach zero, at which point the calling contract will no longer function properly.

**Total Instances:** 4

```solidity
File: contracts/libraries/InteractionHelper.sol

 32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

 33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

 36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);

 37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L37


## [L-14] Unsafe conversion from unsigned to signed values
Solidity follows [two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) rules for its integers, meaning that the most significant bit for signed integers is used to denote the sign, and converting between the two requires inverting all of the bits and adding one. Because of this, casting an unsigned integer to a signed one may result in a change of the sign and or magnitude of the value. For example, `int8(type(uint8).max)` is not equal to `type(int8).max`, but is equal to `-1`. `type(uint8).max` in binary is `11111111`, which if cast to a signed value, means the first binary `1` indicates a negative value, and the binary `1`s, invert to all zeroes, and when one is added, it becomes one, but negative, and therefore the decimal value of binary `11111111` is `-1`.

**Total Instances:** 79

```solidity
File: contracts/CollateralTracker.sol

 /// @audit  conversion from 'uint256' to 'int256'
 200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

 /// @audit  conversion from 'uint256' to 'int256'
 668:                         int256(

 /// @audit  conversion from 'uint128' to 'int128'
 715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

 /// @audit  conversion from 'uint128' to 'int128'
 715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

 /// @audit  conversion from 'uint128' to 'int128'
 718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

 /// @audit  conversion from 'uint128' to 'int128'
 718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

 /// @audit  conversion from 'uint256' to 'int256'
 743:             return int256((s_inAMM * DECIMALS) / totalAssets());

 /// @audit  conversion from 'uint256' to 'int256'
 959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

 /// @audit  conversion from 'uint256' to 'int256'
 959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

 /// @audit  conversion from 'uint256' to 'int256'
 1003:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

 /// @audit  conversion from 'uint256' to 'int256'
 1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

 /// @audit  conversion from 'uint256' to 'int256'
 1052:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

 /// @audit  conversion from 'uint256' to 'int256'
 1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

 /// @audit  conversion from 'uint256' to 'int256'
 1115:                 exchangedAmount = intrinsicValue + int256(swapCommission);

 /// @audit  conversion from 'uint256' to 'int256'
 1119:             exchangedAmount += int256(

 /// @audit  conversion from 'uint64' to 'int64'
 1329:             ? int64(uint64(poolUtilization))

 /// @audit  conversion from 'uint64' to 'int64'
 1330:             : int64(uint64(poolUtilization >> 64));

 /// @audit  conversion from 'uint64' to 'int64'
 1585:                     ? int64(uint64(poolUtilization))

 /// @audit  conversion from 'uint64' to 'int64'
 1586:                     : int64(uint64(poolUtilization >> 64))

 /// @audit  conversion from 'uint64' to 'int64'
 1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

 /// @audit  conversion from 'uint64' to 'int64'
 1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L200

```solidity
File: contracts/PanopticPool.sol

 /// @audit  conversion from 'uint256' to 'int256'
 477:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

 /// @audit  conversion from 'uint256' to 'int256'
 1144:             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)

 /// @audit  conversion from 'uint256' to 'int256'
 1149:             uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)

 /// @audit  conversion from 'uint256' to 'int256'
 1549:                                 int256(

 /// @audit  conversion from 'uint256' to 'int256'
 1558:                                 int256(

 /// @audit  conversion from 'uint256' to 'int256'
 1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

 /// @audit  conversion from 'uint256' to 'int256'
 1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

 /// @audit  conversion from 'uint256' to 'int256'
 1870:                                         .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))

 /// @audit  conversion from 'uint256' to 'int256'
 1901:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

 /// @audit  conversion from 'uint256' to 'int256'
 1935:                                                 (int256(

 /// @audit  conversion from 'uint256' to 'int256'
 1939:                                                     int256(

 /// @audit  conversion from 'uint256' to 'int256'
 1952:                                                 (int256(

 /// @audit  conversion from 'uint256' to 'int256'
 1956:                                                     int256(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L477

```solidity
File: contracts/SemiFungiblePositionManager.sol

 /// @audit  conversion from 'uint256' to 'int256'
 1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

 /// @audit  conversion from 'uint256' to 'int256'
 1172:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

 /// @audit  conversion from 'uint256' to 'int256'
 1176:                 .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

 /// @audit  conversion from 'uint256' to 'int256'
 1177:                 .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

 /// @audit  conversion from 'uint256' to 'int256'
 1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

 /// @audit  conversion from 'uint256' to 'int256'
 1215:             int128(int256(amount1))

 /// @audit  conversion from 'uint256' to 'int256'
 1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

 /// @audit  conversion from 'uint256' to 'int256'
 1242:                 -int128(int256(amount1))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1169

```solidity
File: contracts/libraries/FeesCalc.sol

 /// @audit  conversion from 'uint256' to 'int256'
 69:                         value0 += int256(amount0);

 /// @audit  conversion from 'uint256' to 'int256'
 70:                         value1 += int256(amount1);

 /// @audit  conversion from 'uint256' to 'int256'
 74:                         value0 -= int256(amount0);

 /// @audit  conversion from 'uint256' to 'int256'
 75:                         value1 -= int256(amount1);

 /// @audit  conversion from 'uint256' to 'int256'
 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

 /// @audit  conversion from 'uint256' to 'int256'
 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L69

```solidity
File: contracts/libraries/Math.sol

 /// @audit  conversion from 'uint128' to 'int128'
 312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

 /// @audit  conversion from 'uint256' to 'int256'
 327:         return int256(toCast);

 /// @audit  conversion from 'uint256' to 'int256'
 778:             quickSort(data, int256(0), int256(data.length - 1));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L312

```solidity
File: contracts/libraries/PanopticMath.sol

 /// @audit  conversion from 'uint256' to 'int256'
 140:                         (int256(observationIndex) - int256(i * period)) +

 /// @audit  conversion from 'uint256' to 'int256'
 140:                         (int256(observationIndex) - int256(i * period)) +

 /// @audit  conversion from 'uint256' to 'int256'
 141:                             int256(observationCardinality)

 /// @audit  conversion from 'uint256' to 'int256'
 151:                     int256(timestamps[i] - timestamps[i + 1]);

 /// @audit  conversion from 'uint24' to 'int24'
 178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

 /// @audit  conversion from 'uint24' to 'int24'
 179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

 /// @audit  conversion from 'uint256' to 'int256'
 188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)

 /// @audit  conversion from 'uint256' to 'int256'
 188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)

 /// @audit  conversion from 'uint256' to 'int256'
 196:                             int256(timestamp_last - timestamp_old)

 /// @audit  conversion from 'uint24' to 'int24'
 217:                     entry = int24(uint24(medianData >> (rank * 24)));

 /// @audit  conversion from 'uint56' to 'int56'
 258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

 /// @audit  conversion from 'uint256' to 'int256'
 377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

 /// @audit  conversion from 'uint256' to 'int256'
 681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));

 /// @audit  conversion from 'uint256' to 'int256'
 683:                 bonus1 = int256(

 /// @audit  conversion from 'uint256' to 'int256'
 693:             int256 balance0 = int256(uint256(tokenData0.rightSlot())) -

 /// @audit  conversion from 'uint256' to 'int256'
 695:             int256 balance1 = int256(uint256(tokenData1.rightSlot())) -

 /// @audit  conversion from 'uint256' to 'int256'
 929:                 int256(collateral0.convertToAssets(collateral0.balanceOf(refunder)));

 /// @audit  conversion from 'uint256' to 'int256'
 938:                                 int256(

 /// @audit  conversion from 'uint256' to 'int256'
 947:                 int256(collateral1.convertToAssets(collateral1.balanceOf(refunder)));

 /// @audit  conversion from 'uint256' to 'int256'
 956:                                 int256(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L140

```solidity
File: contracts/types/LeftRight.sol

 /// @audit  conversion from 'uint256' to 'int256'
 27:         int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

 /// @audit  conversion from 'uint256' to 'int256'
 196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();

 /// @audit  conversion from 'uint256' to 'int256'
 201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L27

```solidity
File: contracts/types/LiquidityChunk.sol

 /// @audit  conversion from 'uint256' to 'int256'
 173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));

 /// @audit  conversion from 'uint256' to 'int256'
 182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L173

```solidity
File: contracts/types/TokenId.sol

 /// @audit  conversion from 'uint24' to 'int24'
 98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

 /// @audit  conversion from 'uint256' to 'int256'
 160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

 /// @audit  conversion from 'uint256' to 'int256'
 171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L171


## [L-15] Use of abi.encodePacked with dynamic types inside keccak256
Using abi.encodePacked with dynamic types for hashing functions like keccak256 can be risky due to the potential for hash collisions. This function concatenates arguments tightly, without padding, which might lead to different inputs producing the same hash. This is especially problematic with dynamic types, where the boundaries between inputs can blur. To mitigate this, use abi.encode instead. abi.encode pads its arguments to 32 bytes, creating clear distinctions between different inputs and significantly reducing the chance of hash collisions. This approach ensures more reliable and collision-resistant hashing, crucial for maintaining data integrity and security in smart contracts.

**Total Instances:** 6

```solidity
File: contracts/SemiFungiblePositionManager.sol

 611:             bytes32 positionKey_from = keccak256(
                     abi.encodePacked(
                         address(univ3pool),
                         from,

 620:             bytes32 positionKey_to = keccak256(
                     abi.encodePacked(
                         address(univ3pool),
                         to,

 974:         bytes32 positionKey = keccak256(
                 abi.encodePacked(
                     address(univ3pool),
                     msg.sender,
                     tokenType,

 1431:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

 1458:         bytes32 positionKey = keccak256(
                  abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)

 1544:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1544


## [L-16] Using zero as a parameter
Taking `0` as a valid argument in Solidity without checks can lead to severe security issues. A historical example is the infamous `0x0` address bug where numerous tokens were lost. This happens because `0` can be interpreted as an uninitialized `address`, leading to transfers to the `0x0` `address`, effectively burning tokens. Moreover, `0` as a denominator in division operations would cause a runtime exception. It’s also often indicative of a logical error in the caller’s code. It’s important to always validate input and handle edge cases like `0` appropriately. Use `require()` statements to enforce conditions and provide clear error messages to facilitate debugging and safer code.

**Total Instances:** 6

```solidity
File: contracts/PanopticPool.sol

 893:         _validatePositionList(user, positionIdList, 0);

 1023:         _validatePositionList(liquidatee, positionIdList, 0);

 1153:         _validatePositionList(msg.sender, positionIdListLiquidator, 0);

 1191:         _validatePositionList(msg.sender, positionIdListExercisor, 0);

 1227:         _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

 1592:         _validatePositionList(owner, positionIdList, 0);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1592



# Non Critical Issues


| |Issue|Instances|
|-|:-|:-:|
| [NC-1](#NC-1) | Large or complicated code bases should implement invariant tests | 1 |
| [NC-2](#NC-2) | UPPER_CASE names should be reserved for `constant`/`immutable` variables | 2 |
| [NC-3](#NC-3) | Add inline comments for unnamed parameters | 2 |
| [NC-4](#NC-4) | Missing checks for `address(0)` when assigning values to address state variables | 4 |
| [NC-5](#NC-5) | address parameters should be sanitized | 33 |
| [NC-6](#NC-6) | Assembly blocks should have extensive comments | 21 |
| [NC-7](#NC-7) | Avoid mutating `function`/`modifier` parameters | 9 |
| [NC-8](#NC-8) | Complex casting | 63 |
| [NC-9](#NC-9) | Consider adding formal verification proofs | 20 |
| [NC-10](#NC-10) | Consider adding validation of user inputs | 46 |
| [NC-11](#NC-11) | Consider bounding input array length | 25 |
| [NC-12](#NC-12) | Consider emitting an event at the end of the constructor | 4 |
| [NC-13](#NC-13) | Consider splitting long calculations | 5 |
| [NC-14](#NC-14) | Consider using delete rather than assigning zero/false to clear values | 1 |
| [NC-15](#NC-15) | Consider using descriptive constants when passing zero as a function argument | 62 |
| [NC-16](#NC-16) | Consider using the `using-for` syntax | 321 |
| [NC-17](#NC-17) | Constants/Immutables redefined elsewhere | 2 |
| [NC-18](#NC-18) | Constants in comparisons should appear on the left side | 132 |
| [NC-19](#NC-19) | constructor should emit an event | 4 |
| [NC-20](#NC-20) | Contract uses both require()/revert() as well as custom errors | 5 |
| [NC-21](#NC-21) | Contracts should expose an interface | 7 |
| [NC-22](#NC-22) | Contract variables should have comments | 1 |
| [NC-23](#NC-23) | Contracts should have full test coverage | 1 |
| [NC-24](#NC-24) | Custom error has no error details | 34 |
| [NC-25](#NC-25) | Default `address(0)` can be returned | 2 |
| [NC-26](#NC-26) | Down casting `uint` or `int` may result in overflow | 25 |
| [NC-27](#NC-27) | else-block not required | 7 |
| [NC-28](#NC-28) | Empty bytes check is missing | 7 |
| [NC-29](#NC-29) | Events are missing sender information | 9 |
| [NC-30](#NC-30) | Events may be emitted out of order due to reentrancy | 3 |
| [NC-31](#NC-31) | Expressions for constant values should use immutable rather than constant | 7 |
| [NC-32](#NC-32) | High cyclomatic complexity | 6 |
| [NC-33](#NC-33) | if-statement can be converted to a ternary | 10 |
| [NC-34](#NC-34) | If statement control structures do not comply with best practices | 71 |
| [NC-35](#NC-35) | Imports could be organized more systematically | 6 |
| [NC-36](#NC-36) | Inconsistent spacing in comments | 5 |
| [NC-37](#NC-37) | Interface files should not use fixed compiler versions | 2 |
| [NC-38](#NC-38) | `internal` functions not called by the contract should be removed | 46 |
| [NC-39](#NC-39) | Invalid NatSpec comment style | 6 |
| [NC-40](#NC-40) | Libraries should be defined in separate files from their usage | 4 |
| [NC-41](#NC-41) | Long functions should be refactored into multiple, smaller, functions | 23 |
| [NC-42](#NC-42) | Missing checks constructor/initializer assignments | 15 |
| [NC-43](#NC-43) | Missing checks for state variable assignments | 11 |
| [NC-44](#NC-44) | Missing event for critical changes | 4 |
| [NC-45](#NC-45) | Modifiers should be named in mixedCase style | 1 |
| [NC-46](#NC-46) | Multiple `address`/`ID` mappings can be combined into a single `mapping` of an `address`/`ID` to a struct, for readability | 7 |
| [NC-47](#NC-47) | NatSpec: Contract declarations should have `@author` tags | 3 |
| [NC-48](#NC-48) | NatSpec: Contract declarations should have descriptions | 3 |
| [NC-49](#NC-49) | NatSpec: Contract declarations should have `@dev` tags | 12 |
| [NC-50](#NC-50) | NatSpec: Contract declarations should have `@notice` tags | 6 |
| [NC-51](#NC-51) | NatSpec: Contract declarations should have `@title` tags | 5 |
| [NC-52](#NC-52) | NatSpec: Error declarations should have `@dev` tag | 33 |
| [NC-53](#NC-53) | NatSpec: Error declarations should have `@param` tag | 34 |
| [NC-54](#NC-54) | NatSpec: Event Declaration should have `@dev` tag | 11 |
| [NC-55](#NC-55) | NatSpec: Function declarations should have` @notice` tags | 6 |
| [NC-56](#NC-56) | NatSpec: Function declarations should have descriptions | 3 |
| [NC-57](#NC-57) | NatSpec: Modifier declarations should have `@dev` tag | 1 |
| [NC-58](#NC-58) | NatSpec: state variable declarations should have descriptions | 11 |
| [NC-59](#NC-59) | No equate comparison checks between to and from address parameters | 9 |
| [NC-60](#NC-60) | Non-library/interface files should use fixed compiler versions, not floating ones | 7 |
| [NC-61](#NC-61) | Not using the named return variables anywhere in the function is confusing | 25 |
| [NC-62](#NC-62) | Overflows in unchecked blocks | 36 |
| [NC-63](#NC-63) | Polymorphic functions make security audits more time-consuming and error-prone | 15 |
| [NC-64](#NC-64) | Functions not used internally could be marked external | 13 |
| [NC-65](#NC-65) | `pure` function accesses storage | 11 |
| [NC-66](#NC-66) | Duplicated require()/revert() checks should be refactored to a modifier or function. | 19 |
| [NC-67](#NC-67) | Return values of `approve()` not checked | 2 |
| [NC-68](#NC-68) | Revert statements within external and public functions can be used to perform DOS attacks | 19 |
| [NC-69](#NC-69) | Style guide: Function names should use lowerCamelCase | 11 |
| [NC-70](#NC-70) | Style guide: State and local variables should be named using lowerCamelCase | 54 |
| [NC-71](#NC-71) | Style guide: Top level pragma declarations should be separated by two blank lines | 20 |
| [NC-72](#NC-72) | Unused function parameter | 12 |
| [NC-73](#NC-73) | Unused import | 1 |
| [NC-74](#NC-74) | Unused structs | 1 |
| [NC-75](#NC-75) | Unusual loop variable | 15 |
| [NC-76](#NC-76) | Use bit shifts in an immutable variable rather than long bit masks of a single bit, for readability | 9 |
| [NC-77](#NC-77) | Use bytes.concat() on bytes instead of abi.encodePacked() for clearer semantic meaning | 12 |
| [NC-78](#NC-78) | Use `@inheritdoc` for overridden functions | 4 |
| [NC-79](#NC-79) | Use the latest solidity (prior to 0.8.20 if on L2s) for deployment. | 20 |
| [NC-80](#NC-80) | Use named function calls | 159 |
| [NC-81](#NC-81) | Use of override is unnecessary. | 4 |
| [NC-82](#NC-82) | Use single file for all system-wide constants | 31 |
| [NC-83](#NC-83) | Use a struct instead of returning multiple values | 7 |
| [NC-84](#NC-84) | Use a struct to encapsulate multiple function parameters | 8 |
| [NC-85](#NC-85) | Use `using` keyword when using specific imports rather than calling the specific import directly | 344 |
| [NC-86](#NC-86) | Utility contracts can be made into libraries | 1 |
| [NC-87](#NC-87) | Visibility should be set explicitly rather than defaulting to internal | 11 |


## [NC-1] Large or complicated code bases should implement invariant tests
Large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts, should implement [invariant fuzzing tests](https://medium.com/coinmonks/smart-contract-fuzzing-d9b88e0b0a05). Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold. Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers, with properly and extensively-written invariants, can close this testing gap significantly.

**Total Instances:** 20

```solidity
File: contracts/CollateralTracker.sol

 36: contract CollateralTracker is ERC20Minimal, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36

```solidity
File: contracts/PanopticFactory.sol

 26: contract PanopticFactory is Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L26

```solidity
File: contracts/PanopticPool.sol

 27: contract PanopticPool is ERC1155Holder, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L27

```solidity
File: contracts/SemiFungiblePositionManager.sol

 72: contract SemiFungiblePositionManager is ERC1155, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L72

```solidity
File: contracts/libraries/CallbackLib.sol

 12: library CallbackLib {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L12

```solidity
File: contracts/libraries/Constants.sol

 7: library Constants {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L7

```solidity
File: contracts/libraries/Errors.sol

 7: library Errors {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L7

```solidity
File: contracts/libraries/FeesCalc.sol

 39: library FeesCalc {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L39

```solidity
File: contracts/libraries/InteractionHelper.sol

 17: library InteractionHelper {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17

```solidity
File: contracts/libraries/Math.sol

 13: library Math {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L13

```solidity
File: contracts/libraries/PanopticMath.sol

 18: library PanopticMath {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18

```solidity
File: contracts/libraries/SafeTransferLib.sol

 11: library SafeTransferLib {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L11

```solidity
File: contracts/multicall/Multicall.sol

 8: abstract contract Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L8

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 11: abstract contract ERC1155 {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L11

```solidity
File: contracts/tokens/ERC20Minimal.sol

 9: abstract contract ERC20Minimal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L9

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 6: interface IDonorNFT {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

 11: interface IERC20Partial {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L11

```solidity
File: contracts/types/LeftRight.sol

 17: library LeftRightLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L17

```solidity
File: contracts/types/LiquidityChunk.sol

 52: library LiquidityChunkLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52

```solidity
File: contracts/types/TokenId.sol

 60: library TokenIdLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L60


## [NC-2] UPPER_CASE names should be reserved for `constant`/`immutable` variables
If the variable needs to be different based on which class it comes from, a `view`/`pure` function should be used instead (e.g. like [this](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59)).

**Total Instances:** 2

```solidity
File: contracts/PanopticFactory.sol

 116:         address _WETH9,

 117:         SemiFungiblePositionManager _SFPM,

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L117


## [NC-3] Add inline comments for unnamed parameters
`function func(address a, address)` `->` `function func(address a, address /* b */)`

**Total Instances:** 2

```solidity
File: contracts/CollateralTracker.sol

 392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

 444:     function maxMint(address) external view returns (uint256 maxShares) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L444


## [NC-4] Missing checks for `address(0)` when assigning values to address state variables

**Total Instances:** 4

```solidity
File: contracts/CollateralTracker.sol

 254:         s_univ3token0 = token0;

 255:         s_univ3token1 = token1;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L254

```solidity
File: contracts/PanopticFactory.sol

 136:             s_owner = _owner;

 152:         s_owner = newOwner;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L152


## [NC-5] address parameters should be sanitized
Implement a zero address check in functions with `address` parameters to prevent unexpected behavior.

**Total Instances:** 33

```solidity
File: contracts/CollateralTracker.sol

 /// @audit  'token0', 'token1' not checked
 221:     function startToken(
             bool underlyingIsToken0,
             address token0,
             address token1,
             uint24 fee,
             PanopticPool panopticPool
         ) external {

 /// @audit  'recipient' not checked
 323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

 /// @audit  'from', 'to' not checked
 341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

 392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

 /// @audit  'receiver' not checked
 417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {

 /// @audit  'receiver' not checked
 477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {

 /// @audit  'receiver', 'owner' not checked
 531:     function withdraw(
             uint256 assets,
             address receiver,
             address owner
         ) external returns (uint256 shares) {

 /// @audit  'receiver', 'owner' not checked
 591:     function redeem(
             uint256 shares,
             address receiver,
             address owner
         ) external returns (uint256 assets) {

 /// @audit  'delegator', 'delegatee' not checked
 864:     function delegate(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {

 /// @audit  'delegatee' not checked
 894:     function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

 /// @audit  'delegatee' not checked
 903:     function refund(address delegatee, uint256 assets) external onlyPanopticPool {

 /// @audit  'delegator', 'delegatee' not checked
 911:     function revoke(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {

 /// @audit  'refunder', 'refundee' not checked
 975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

 /// @audit  'optionOwner' not checked
 995:     function takeCommissionAddData(
             address optionOwner,
             int128 longAmount,
             int128 shortAmount,
             int128 swappedAmount
         ) external onlyPanopticPool returns (int256 utilization) {

 /// @audit  'optionOwner' not checked
 1043:     function exercise(
              address optionOwner,
              int128 longAmount,
              int128 shortAmount,
              int128 swappedAmount,
              int128 realizedPremium
          ) external onlyPanopticPool returns (int128) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L221

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  '_owner' not checked
 134:     function initialize(address _owner) public {

 /// @audit  'newOwner' not checked
 147:     function transferOwnership(address newOwner) external {

 /// @audit  'token1' not checked
 210:     function deployNewPool(
             address token0,
             address token1,
             uint24 fee,
             bytes32 salt
         ) external returns (PanopticPool newPoolContract) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134

```solidity
File: contracts/PanopticPool.sol

 /// @audit  'token0', 'token1' not checked
 291:     function startPool(
             IUniswapV3Pool _univ3pool,
             address token0,
             address token1,
             CollateralTracker collateralTracker0,
             CollateralTracker collateralTracker1
         ) external {

 /// @audit  'liquidatee' not checked
 1017:     function liquidate(
              TokenId[] calldata positionIdListLiquidator,
              address liquidatee,
              LeftRightUnsigned delegations,
              TokenId[] calldata positionIdList
          ) external {

 /// @audit  'account' not checked
 1179:     function forceExercise(
              address account,
              TokenId[] calldata touchedId,
              TokenId[] calldata positionIdListExercisee,
              TokenId[] calldata positionIdListExercisor
          ) external {

 /// @audit  'owner' not checked
 1587:     function settleLongPremium(
              TokenId[] calldata positionIdList,
              address owner,
              uint256 legIndex
          ) external {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L291

```solidity
File: contracts/SemiFungiblePositionManager.sol

 /// @audit  'token0', 'token1' not checked
 350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

 /// @audit  'from', 'to' not checked
 540:     function safeTransferFrom(
             address from,
             address to,
             uint256 id,
             uint256 amount,
             bytes calldata data
         ) public override {

 /// @audit  'from', 'to' not checked
 566:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public override {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350

```solidity
File: contracts/libraries/InteractionHelper.sol

 /// @audit  'token0', 'token1' not checked
 24:     function doApprovals(
            SemiFungiblePositionManager sfpm,
            CollateralTracker ct0,
            CollateralTracker ct1,
            address token0,
            address token1
        ) external {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L24

```solidity
File: contracts/libraries/PanopticMath.sol

 /// @audit  'liquidatee' not checked
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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L768

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 /// @audit  'operator' not checked
 81:     function setApprovalForAll(address operator, bool approved) public {

 /// @audit  'from', 'to' not checked
 94:     function safeTransferFrom(
            address from,
            address to,
            uint256 id,
            uint256 amount,
            bytes calldata data
        ) public virtual {

 /// @audit  'from', 'to' not checked
 130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L81

```solidity
File: contracts/tokens/ERC20Minimal.sol

 /// @audit  'spender' not checked
 49:     function approve(address spender, uint256 amount) public returns (bool) {

 /// @audit  'to' not checked
 61:     function transfer(address to, uint256 amount) public virtual returns (bool) {

 /// @audit  'from', 'to' not checked
 81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L81


## [NC-6] Assembly blocks should have extensive comments
Assembly blocks take a lot more time to audit than normal Solidity code, and often have gotchas and side-effects that the Solidity versions of the same code do not. Consider adding more comments explaining what is being done in every step of the assembly code, and describe why assembly is being used instead of Solidity.

**Total Instances:** 21

```solidity
File: contracts/libraries/Math.sol

 353:             assembly ("memory-safe") {
                     let mm := mulmod(a, b, not(0))
                     prod0 := mul(a, b)
                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))

 362:                 assembly ("memory-safe") {
                         result := div(prod0, denominator)

 379:             assembly ("memory-safe") {
                     remainder := mulmod(a, b, denominator)

 383:             assembly ("memory-safe") {
                     prod1 := sub(prod1, gt(remainder, prod0))
                     prod0 := sub(prod0, remainder)

 393:             assembly ("memory-safe") {
                     denominator := div(denominator, twos)

 398:             assembly ("memory-safe") {
                     prod0 := div(prod0, twos)

 404:             assembly ("memory-safe") {
                     twos := add(div(sub(0, twos), twos), 1)

 467:             assembly ("memory-safe") {
                     let mm := mulmod(a, b, not(0))
                     prod0 := mul(a, b)
                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))

 493:             assembly ("memory-safe") {
                     remainder := mulmod(a, b, 0x10000000000000000)

 497:             assembly ("memory-safe") {
                     prod1 := sub(prod1, gt(remainder, prod0))
                     prod0 := sub(prod0, remainder)

 530:             assembly ("memory-safe") {
                     let mm := mulmod(a, b, not(0))
                     prod0 := mul(a, b)
                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))

 556:             assembly ("memory-safe") {
                     remainder := mulmod(a, b, 0x1000000000000000000000000)

 560:             assembly ("memory-safe") {
                     prod1 := sub(prod1, gt(remainder, prod0))
                     prod0 := sub(prod0, remainder)

 607:             assembly ("memory-safe") {
                     let mm := mulmod(a, b, not(0))
                     prod0 := mul(a, b)
                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))

 633:             assembly ("memory-safe") {
                     remainder := mulmod(a, b, 0x100000000000000000000000000000000)

 637:             assembly ("memory-safe") {
                     prod1 := sub(prod1, gt(remainder, prod0))
                     prod0 := sub(prod0, remainder)

 684:             assembly ("memory-safe") {
                     let mm := mulmod(a, b, not(0))
                     prod0 := mul(a, b)
                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))

 710:             assembly ("memory-safe") {
                     remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)

 714:             assembly ("memory-safe") {
                     prod1 := sub(prod1, gt(remainder, prod0))
                     prod0 := sub(prod0, remainder)

 739:         assembly ("memory-safe") {
                 result := add(div(a, b), gt(mod(a, b), 0))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L353

```solidity
File: contracts/multicall/Multicall.sol

 25:                 assembly ("memory-safe") {
                        revert(add(result, 32), mload(result))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L25


## [NC-7] Avoid mutating `function`/`modifier` parameters
Use a local variable instead.

**Total Instances:** 9

```solidity
File: contracts/CollateralTracker.sol

 /// @audit  utilization
 779:                 utilization = -utilization;

 /// @audit  poolUtilization
 1636:             poolUtilization =

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L779

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  salt
 323:                 salt = bytes32(uint256(salt) + 1);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L323

```solidity
File: contracts/SemiFungiblePositionManager.sol

 /// @audit  tokenId
 692:             tokenId = tokenId.flipToBurnToken();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L692

```solidity
File: contracts/libraries/Math.sol

 /// @audit  x
 94:                 x >>= 128;

 /// @audit  x
 98:                 x >>= 64;

 /// @audit  x
 102:                 x >>= 32;

 /// @audit  x
 106:                 x >>= 16;

 /// @audit  x
 110:                 x >>= 8;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L110


## [NC-8] Complex casting
Consider whether the number of casts is really necessary, or whether using a different type would be more appropriate. Alternatively, add comments to explain in detail why the casts are necessary, and any implicit reasons why the cast does not introduce an overflow.

**Total Instances:** 63

```solidity
File: contracts/CollateralTracker.sol

 667:                     int24 range = int24(

 715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

 718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

 1003:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

 1028:             s_poolAssets = uint128(uint256(updatedAssets));

 1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

 1052:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

 1084:             s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L667

```solidity
File: contracts/PanopticFactory.sol

 220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L220

```solidity
File: contracts/PanopticPool.sol

 313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

 314:                 (uint256(uint24(currentTick))); // add to slot 3

 1144:             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)

 1149:             uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)

 1548:                             int128(

 1557:                             int128(

 1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

 1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L313

```solidity
File: contracts/SemiFungiblePositionManager.sol

 1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

 1172:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

 1176:                 .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

 1177:                 .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

 1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

 1215:             int128(int256(amount1))

 1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

 1242:                 -int128(int256(amount1))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1169

```solidity
File: contracts/libraries/FeesCalc.sol

 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L117

```solidity
File: contracts/libraries/Math.sol

 130:             uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));

 131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L130

```solidity
File: contracts/libraries/PanopticMath.sol

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L51

```solidity
File: contracts/types/LeftRight.sol

 27:         int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

 196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();

 201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L27

```solidity
File: contracts/types/LiquidityChunk.sol

 78:                     (uint256(uint24(_tickLower)) << 232) +

 79:                         (uint256(uint24(_tickUpper)) << 208) +

 109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

 126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

 173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));

 182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L78

```solidity
File: contracts/types/TokenId.sol

 98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

 160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

 171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

 195:             return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L195


## [NC-9] Consider adding formal verification proofs
Consider using formal verification to mathematically prove that your code does what is intended, and does not have any edge cases with unexpected behavior. The solidity compiler itself has this functionality [built in](https://docs.soliditylang.org/en/latest/smtchecker.html#smtchecker-and-formal-verification)

**Total Instances:** 20

```solidity
File: contracts/CollateralTracker.sol

 36: contract CollateralTracker is ERC20Minimal, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36

```solidity
File: contracts/PanopticFactory.sol

 26: contract PanopticFactory is Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L26

```solidity
File: contracts/PanopticPool.sol

 27: contract PanopticPool is ERC1155Holder, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L27

```solidity
File: contracts/SemiFungiblePositionManager.sol

 72: contract SemiFungiblePositionManager is ERC1155, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L72

```solidity
File: contracts/libraries/CallbackLib.sol

 12: library CallbackLib {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L12

```solidity
File: contracts/libraries/Constants.sol

 7: library Constants {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L7

```solidity
File: contracts/libraries/Errors.sol

 7: library Errors {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L7

```solidity
File: contracts/libraries/FeesCalc.sol

 39: library FeesCalc {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L39

```solidity
File: contracts/libraries/InteractionHelper.sol

 17: library InteractionHelper {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17

```solidity
File: contracts/libraries/Math.sol

 13: library Math {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L13

```solidity
File: contracts/libraries/PanopticMath.sol

 18: library PanopticMath {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18

```solidity
File: contracts/libraries/SafeTransferLib.sol

 11: library SafeTransferLib {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L11

```solidity
File: contracts/multicall/Multicall.sol

 8: abstract contract Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L8

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 11: abstract contract ERC1155 {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L11

```solidity
File: contracts/tokens/ERC20Minimal.sol

 9: abstract contract ERC20Minimal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L9

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 6: interface IDonorNFT {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

 11: interface IERC20Partial {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L11

```solidity
File: contracts/types/LeftRight.sol

 17: library LeftRightLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L17

```solidity
File: contracts/types/LiquidityChunk.sol

 52: library LiquidityChunkLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52

```solidity
File: contracts/types/TokenId.sol

 60: library TokenIdLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L60


## [NC-10] Consider adding validation of user inputs
here are no validations done on the arguments below. Consider that the Solidity [documentation](https://docs.soliditylang.org/en/latest/control-structures.html#panic-via-assert-and-error-via-require) states that `Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix`. This means that there should be explicit checks for expected ranges of inputs. Underflows/overflows result in panics should not be used as range checks, and allowing funds to be sent to  `0x0`, which is the default value of address variables and has many gotchas, should be avoided.

**Total Instances:** 46

```solidity
File: contracts/CollateralTracker.sol

 /// @audit  token0, token1
 221:     function startToken(
             bool underlyingIsToken0,
             address token0,
             address token1,
             uint24 fee,
             PanopticPool panopticPool
         ) external {

 /// @audit  recipient
 323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

 /// @audit  from, to
 341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

 /// @audit  receiver
 417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {

 /// @audit  receiver
 477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {

 /// @audit  owner
 507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

 /// @audit  receiver, owner
 531:     function withdraw(
             uint256 assets,
             address receiver,
             address owner
         ) external returns (uint256 shares) {

 /// @audit  owner
 572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {

 /// @audit  receiver, owner
 591:     function redeem(
             uint256 shares,
             address receiver,
             address owner
         ) external returns (uint256 assets) {

 /// @audit  delegator, delegatee
 864:     function delegate(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {

 /// @audit  delegatee
 894:     function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

 /// @audit  delegatee
 903:     function refund(address delegatee, uint256 assets) external onlyPanopticPool {

 /// @audit  delegator, delegatee
 911:     function revoke(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {

 /// @audit  refunder, refundee
 975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

 /// @audit  optionOwner
 995:     function takeCommissionAddData(
             address optionOwner,
             int128 longAmount,
             int128 shortAmount,
             int128 swappedAmount
         ) external onlyPanopticPool returns (int256 utilization) {

 /// @audit  optionOwner
 1043:     function exercise(
              address optionOwner,
              int128 longAmount,
              int128 shortAmount,
              int128 swappedAmount,
              int128 realizedPremium
          ) external onlyPanopticPool returns (int128) {

 /// @audit  user
 1141:     function getAccountMarginDetails(
              address user,
              int24 currentTick,
              uint256[2][] memory positionBalanceArray,
              int128 premiumAllPositions
          ) public view returns (LeftRightUnsigned tokenData) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L221

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  newOwner
 147:     function transferOwnership(address newOwner) external {

 /// @audit  token1
 210:     function deployNewPool(
             address token0,
             address token1,
             uint24 fee,
             bytes32 salt
         ) external returns (PanopticPool newPoolContract) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L147

```solidity
File: contracts/PanopticPool.sol

 /// @audit  token0, token1
 291:     function startPool(
             IUniswapV3Pool _univ3pool,
             address token0,
             address token1,
             CollateralTracker collateralTracker0,
             CollateralTracker collateralTracker1
         ) external {

 /// @audit  user
 352:     function optionPositionBalance(
             address user,
             TokenId tokenId
         ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

 /// @audit  user
 381:     function calculateAccumulatedFeesBatch(
             address user,
             bool includePendingPremium,
             TokenId[] calldata positionIdList
         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

 /// @audit  user
 410:     function calculatePortfolioValue(
             address user,
             int24 atTick,
             TokenId[] calldata positionIdList
         ) external view returns (int256 value0, int256 value1) {

 /// @audit  liquidatee
 1017:     function liquidate(
              TokenId[] calldata positionIdListLiquidator,
              address liquidatee,
              LeftRightUnsigned delegations,
              TokenId[] calldata positionIdList
          ) external {

 /// @audit  account
 1179:     function forceExercise(
              address account,
              TokenId[] calldata touchedId,
              TokenId[] calldata positionIdListExercisee,
              TokenId[] calldata positionIdListExercisor
          ) external {

 /// @audit  user
 1444:     function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

 /// @audit  owner
 1587:     function settleLongPremium(
              TokenId[] calldata positionIdList,
              address owner,
              uint256 legIndex
          ) external {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L291

```solidity
File: contracts/SemiFungiblePositionManager.sol

 /// @audit  token0, token1
 350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

 /// @audit  from, to
 540:     function safeTransferFrom(
             address from,
             address to,
             uint256 id,
             uint256 amount,
             bytes calldata data
         ) public override {

 /// @audit  from, to
 566:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public override {

 /// @audit  univ3pool, owner
 1421:     function getAccountLiquidity(
              address univ3pool,
              address owner,
              uint256 tokenType,
              int24 tickLower,
              int24 tickUpper
          ) external view returns (LeftRightUnsigned accountLiquidities) {

 /// @audit  univ3pool, owner
 1449:     function getAccountPremium(
              address univ3pool,
              address owner,
              uint256 tokenType,
              int24 tickLower,
              int24 tickUpper,
              int24 atTick,
              uint256 isLong
          ) external view returns (uint128, uint128) {

 /// @audit  univ3pool, owner
 1535:     function getAccountFeesBase(
              address univ3pool,
              address owner,
              uint256 tokenType,
              int24 tickLower,
              int24 tickUpper
          ) external view returns (int128 feesBase0, int128 feesBase1) {

 /// @audit  univ3pool
 1566:     function getPoolId(address univ3pool) external view returns (uint64 poolId) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350

```solidity
File: contracts/libraries/InteractionHelper.sol

 /// @audit  token0, token1
 24:     function doApprovals(
            SemiFungiblePositionManager sfpm,
            CollateralTracker ct0,
            CollateralTracker ct1,
            address token0,
            address token1
        ) external {

 /// @audit  token0, token1
 48:     function computeName(
            address token0,
            address token1,
            bool isToken0,
            uint24 fee,
            string memory prefix
        ) external view returns (string memory) {

 /// @audit  token
 91:     function computeSymbol(
            address token,
            string memory prefix
        ) external view returns (string memory) {

 /// @audit  token
 107:     function computeDecimals(address token) external view returns (uint8) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L24

```solidity
File: contracts/libraries/PanopticMath.sol

 /// @audit  liquidatee
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

 /// @audit  refunder
 917:     function getRefundAmounts(
             address refunder,
             LeftRightSigned refundValues,
             int24 atTick,
             CollateralTracker collateral0,
             CollateralTracker collateral1
         ) external view returns (LeftRightSigned) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L768

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 /// @audit  operator
 81:     function setApprovalForAll(address operator, bool approved) public {

 /// @audit  from, to
 94:     function safeTransferFrom(
            address from,
            address to,
            uint256 id,
            uint256 amount,
            bytes calldata data
        ) public virtual {

 /// @audit  from, to
 130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L81

```solidity
File: contracts/tokens/ERC20Minimal.sol

 /// @audit  spender
 49:     function approve(address spender, uint256 amount) public returns (bool) {

 /// @audit  to
 61:     function transfer(address to, uint256 amount) public virtual returns (bool) {

 /// @audit  from, to
 81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L81


## [NC-11] Consider bounding input array length
The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to require() that the length of the array is below some reasonable maximum, so that the user doesn’t have to use up a full transaction’s gas only to see that the transaction reverts.

**Total Instances:** 25

```solidity
File: contracts/CollateralTracker.sol

 1208:         for (uint256 i = 0; i < totalIterations; ) {
                  // read the ith tokenId from the account
                  TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);
      
                  // read the position size and the pool utilization at mint
                  uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();
      
                  // read the pool utilization at mint
                  uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1208

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

 459:             for (uint256 leg = 0; leg < numLegs; ) {
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

 745:         for (uint256 leg = 0; leg < numLegs; ) {
                 // Extract base fee (AMM swap/trading fees) for the position and add it to s_options
                 // (ie. the (feeGrowth * liquidity) / 2**128 for each token)
                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
                 uint256 isLong = tokenId.isLong(leg);
                 {
                     (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
                         address(s_univ3pool),
                         address(this),
                         tokenId.tokenType(leg),
                         tickLower,
                         tickUpper,
                         type(int24).max,
                         isLong
                     );
     
                     // update the premium accumulators
                     s_options[msg.sender][tokenId][leg] = LeftRightUnsigned

 802:         for (uint256 i = 0; i < positionIdList.length; ) {
                 LeftRightSigned paidAmounts;
                 (paidAmounts, premiasByLeg[i]) = _burnOptions(
                     commitLongSettled,
                     positionIdList[i],

 864:         for (uint256 leg = 0; leg < numLegs; ) {
                 if (tokenId.isLong(leg) == 0) {
                     // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
                     (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
                     _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
                 }
                 s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);

 1382:         for (uint256 i = 0; i < pLength; ) {
                  fingerprintIncomingList = PanopticMath.updatePositionsHash(
                      fingerprintIncomingList,
                      positionIdList[i],

 1518:         for (uint256 leg = 0; leg < numLegs; ) {
                  uint256 isLong = tokenId.isLong(leg);
                  if ((isLong == 1) || computeAllPremia) {
                      LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                          tokenId,
                          leg,
                          positionSize
                      );
                      uint256 tokenType = tokenId.tokenType(leg);
      
                      (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM
                          .getAccountPremium(
                              address(s_univ3pool),
                              address(this),
                              tokenType,
                              liquidityChunk.tickLower(),
                              liquidityChunk.tickUpper(),
                              atTick,
                              isLong
                          );
      
                      unchecked {
                          LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];
      
                          // if the premium accumulatorLast is higher than current, it means the premium accumulator has overflowed and rolled over at least once
                          // we can account for one rollover by doing (acc_cur + (acc_max - acc_last))
                          // if there are multiple rollovers or the rollover goes past the last accumulator, rolled over fees will just remain unclaimed
                          premiaByLeg[leg] = LeftRightSigned
                              .wrap(0)
                              .toRightSlot(
                                  int128(
                                      int256(
                                          ((premiumAccumulatorsByLeg[leg][0] -

 1672:         for (uint256 leg = 0; leg < numLegs; ++leg) {
                  bytes32 chunkKey = keccak256(
                      abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
                  );
                  // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers
                  s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
      
                  if (tokenId.isLong(leg) == 0) {
                      LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                          tokenId,
                          leg,
                          positionSize
                      );
      
                      // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (R + N)
                      uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
      
                      // We need to adjust the grossPremiumLast value such that the result of
                      // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64
                      // G: total gross premium
                      // T: totalLiquidityBeforeMint
                      // R: positionLiquidity
                      // C: current grossPremium value
                      // L: current grossPremiumLast value
                      // Ln: updated grossPremiumLast value
                      // T * (C - L) = G
                      // (T + R) * (C - Ln) = G
                      //
                      // T * (C - L) = (T + R) * (C - Ln)
                      // (TC - TL) / (T + R) = C - Ln
                      // Ln = C - (TC - TL)/(T + R)
                      // Ln = (CT + CR - TC + TL)/(T+R)
                      // Ln = (CR + TL)/(T+R)
      
                      uint256[2] memory grossCurrent;
                      (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
                          address(s_univ3pool),
                          address(this),
                          tokenId.tokenType(leg),
                          liquidityChunk.tickLower(),
                          liquidityChunk.tickUpper(),
                          type(int24).max,
                          0
                      );
      
                      unchecked {
                          // L
                          LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
                          // R
                          uint256 positionLiquidity = liquidityChunk.liquidity();
                          // T (totalLiquidity is (T + R) after minting)
                          uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
      
                          s_grossPremiumLast[chunkKey] = LeftRightUnsigned
                              .wrap(0)
                              .toRightSlot(
                                  uint128(
                                      (grossCurrent[0] *

 1852:         for (uint256 leg = 0; leg < numLegs; ) {
                  LeftRightSigned legPremia = premiaByLeg[leg];
      
                  bytes32 chunkKey = keccak256(
                      abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
                  );
      
                  // collected from Uniswap
                  LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
      
                  if (LeftRightSigned.unwrap(legPremia) != 0) {
                      // (will be) paid by long legs
                      if (tokenId.isLong(leg) == 1) {
                          if (commitLongSettled)
                              settledTokens = LeftRightUnsigned.wrap(
                                  uint256(
                                      LeftRightSigned.unwrap(
                                          LeftRightSigned
                                              .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
                                              .sub(legPremia)
                                      )
                                  )
                              );
                          realizedPremia = realizedPremia.add(legPremia);
                      } else {
                          uint256 positionLiquidity = PanopticMath
                              .getLiquidityChunk(tokenId, leg, positionSize)
                              .liquidity();
      
                          // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (T - R)
                          uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
                          // T (totalLiquidity is (T - R) after burning)
                          uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;
      
                          LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
      
                          LeftRightUnsigned availablePremium = _getAvailablePremium(
                              totalLiquidity + positionLiquidity,
                              settledTokens,
                              grossPremiumLast,
                              LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
                              premiumAccumulatorsByLeg[leg]
                          );
      
                          // subtract settled tokens sent to seller
                          settledTokens = settledTokens.sub(availablePremium);
      
                          // add available premium to amount that should be settled
                          realizedPremia = realizedPremia.add(
                              LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
                          );
      
                          // We need to adjust the grossPremiumLast value such that the result of
                          // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostBurn/2**64 is equal to
                          // (grossPremium - grossPremiumLast)*totalLiquidityBeforeBurn/2**64 - premiumOwedToPosition
                          // G: total gross premium (- premiumOwedToPosition)
                          // T: totalLiquidityBeforeMint
                          // R: positionLiquidity
                          // C: current grossPremium value
                          // L: current grossPremiumLast value
                          // Ln: updated grossPremiumLast value
                          // T * (C - L) = G
                          // (T - R) * (C - Ln) = G - P
                          //
                          // T * (C - L) = (T - R) * (C - Ln) + P
                          // (TC - TL - P) / (T - R) = C - Ln
                          // Ln = C - (TC - TL - P) / (T - R)
                          // Ln = (TC - CR - TC + LT + P) / (T-R)
                          // Ln = (LT - CR + P) / (T-R)
      
                          unchecked {
                              uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
                              uint256 _leg = leg;
      
                              // if there's still liquidity, compute the new grossPremiumLast
                              // otherwise, we just reset grossPremiumLast to the current grossPremium
                              s_grossPremiumLast[chunkKey] = totalLiquidity != 0
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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L441

```solidity
File: contracts/SemiFungiblePositionManager.sol

 575:         for (uint256 i = 0; i < ids.length; ) {
                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

 601:         for (uint256 leg = 0; leg < numLegs; ) {
                 // for this leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
                 // @dev see `contracts/types/LiquidityChunk.sol`
                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                     id,
                     leg,
                     uint128(amount)
                 );
     
                 //construct the positionKey for the from and to addresses
                 bytes32 positionKey_from = keccak256(
                     abi.encodePacked(
                         address(univ3pool),
                         from,
                         id.tokenType(leg),
                         liquidityChunk.tickLower(),
                         liquidityChunk.tickUpper()
                     )
                 );
                 bytes32 positionKey_to = keccak256(
                     abi.encodePacked(
                         address(univ3pool),
                         to,
                         id.tokenType(leg),
                         liquidityChunk.tickLower(),
                         liquidityChunk.tickUpper()
                     )
                 );
     
                 // Revert if recipient already has that position
                 if (
                     (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
                     (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

 882:         for (uint256 leg = 0; leg < numLegs; ) {
                 LeftRightSigned _moved;
                 LeftRightSigned _itmAmounts;
                 LeftRightUnsigned _collectedSingleLeg;
     
                 {
                     // cache the univ3pool, tokenId, isBurn, and _positionSize variables to get rid of stack too deep error
                     IUniswapV3Pool _univ3pool = univ3pool;
                     TokenId _tokenId = tokenId;
                     bool _isBurn = isBurn;
                     uint128 _positionSize = positionSize;
                     uint256 _leg;
     
                     unchecked {
                         // Reverse the order of the legs if this call is burning a position (LIFO)
                         // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,
                         // allowing the corresponding short liquidity to be removed
                         _leg = _isBurn ? numLegs - leg - 1 : leg;
                     }
     
                     // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
                     // @dev see `contracts/types/LiquidityChunk.sol`
                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                         _tokenId,
                         _leg,
                         _positionSize
                     );
     
                     (_moved, _itmAmounts, _collectedSingleLeg) = _createLegInAMM(
                         _univ3pool,
                         _tokenId,
                         _leg,
                         liquidityChunk,
                         _isBurn
                     );
     
                     collectedByLeg[_leg] = _collectedSingleLeg;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L575

```solidity
File: contracts/libraries/FeesCalc.sol

 51:         for (uint256 k = 0; k < positionIdList.length; ) {
                TokenId tokenId = positionIdList[k];
                uint128 positionSize = userBalance[tokenId].rightSlot();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L51

```solidity
File: contracts/libraries/PanopticMath.sol

 137:             for (uint256 i = 0; i < cardinality + 1; ++i) {
                     (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(

 148:             for (uint256 i = 0; i < cardinality; ++i) {
                     ticks[i] =
                         (tickCumulatives[i] - tickCumulatives[i + 1]) /
                         int256(timestamps[i] - timestamps[i + 1]);

 248:             for (uint256 i = 0; i < 20; ++i) {
                     secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);

 256:             for (uint256 i = 0; i < 19; ++i) {
                     twapMeasurement[i] = int24(
                         (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

 781:             for (uint256 i = 0; i < positionIdList.length; ++i) {
                     TokenId tokenId = positionIdList[i];
                     uint256 numLegs = tokenId.countLegs();
                     for (uint256 leg = 0; leg < numLegs; ++leg) {
                         if (tokenId.isLong(leg) == 1) {
                             longPremium = longPremium.sub(premiasByLeg[i][leg]);

 784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {
                         if (tokenId.isLong(leg) == 1) {
                             longPremium = longPremium.sub(premiasByLeg[i][leg]);

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

 863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L137

```solidity
File: contracts/multicall/Multicall.sol

 14:         for (uint256 i = 0; i < data.length; ) {
                (bool success, bytes memory result) = address(this).delegatecall(data[i]);
    
                if (!success) {
                    // Bubble up the revert reason
                    // The bytes type is ABI encoded as a length-prefixed byte array
                    // So we simply need to add 32 to the pointer to get the start of the data
                    // And then revert with the size loaded from the first 32 bytes
                    // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
                    // However, we have chosen to simply replicate the the normal behavior of the call
                    // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
                    assembly ("memory-safe") {
                        revert(add(result, 32), mload(result))
                    }
                }
    
                results[i] = result;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L14

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 143:         for (uint256 i = 0; i < ids.length; ) {
                 id = ids[i];
                 amount = amounts[i];
     
                 balanceOf[from][id] -= amount;
     
                 // balance will never overflow
                 unchecked {
                     balanceOf[to][id] += amount;

 187:             for (uint256 i = 0; i < owners.length; ++i) {
                     balances[i] = balanceOf[owners[i]][ids[i]];

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L187


## [NC-12] Consider emitting an event at the end of the constructor
This will allow users to easily exactly pinpoint when and by whom a contract was constructed

**Total Instances:** 4

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
             COMMISSION_FEE = _commissionFee;
             SELLER_COLLATERAL_RATIO = _sellerCollateralRatio;
             BUYER_COLLATERAL_RATIO = _buyerCollateralRatio;
             FORCE_EXERCISE_COST = _forceExerciseCost;
             TARGET_POOL_UTIL = _targetPoolUtilization;
             SATURATED_POOL_UTIL = _saturatedPoolUtilization;
             ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;
     
             // calculate amount of ticks required for upwards and downwards moves, used to check if current and mini-median tick
             // are out of sync (then apply a 100% collateral requirement)
             unchecked {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L178

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
             WETH = _WETH9;
             SFPM = _SFPM;
             DONOR_NFT = _donorNFT;
             // We store the Uniswap Factory contract - later we can use this to verify uniswap pools
             UNIV3_FACTORY = _univ3Factory;
             POOL_REFERENCE = _poolReference;
             COLLATERAL_REFERENCE = _collateralReference;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L115

```solidity
File: contracts/PanopticPool.sol

 280:     constructor(SemiFungiblePositionManager _sfpm) {
             SFPM = _sfpm;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L280

```solidity
File: contracts/SemiFungiblePositionManager.sol

 341:     constructor(IUniswapV3Factory _factory) {
             FACTORY = _factory;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L341


## [NC-13] Consider splitting long calculations
The longer a string of operations is, the harder it is to understand it. Consider splitting the full calculation into more steps, with more descriptive temporary variable names, and add extensive comments.

**Total Instances:** 5

```solidity
File: contracts/CollateralTracker.sol

 202:                 2230 +
                         (12500 * ratioTick) /
                         10_000 +
                         (7812 * ratioTick ** 2) /
                         10_000 ** 2 +
                         (6510 * ratioTick ** 3) /

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L202

```solidity
File: contracts/PanopticPool.sol

 309:                 (uint256(block.timestamp) << 216) +
                     // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
                     // see comment on s_miniMedian initialization for format of this magic number
                     (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
                     (uint256(uint24(currentTick)) << 24) + // add to slot 4
                     (uint256(uint24(currentTick))); // add to slot 3

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L309

```solidity
File: contracts/SemiFungiblePositionManager.sol

 1388:                     uint256 numerator = totalLiquidity ** 2 -
                              totalLiquidity *
                              removedLiquidity +
                              ((removedLiquidity ** 2) / 2 ** (VEGOID));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1388

```solidity
File: contracts/libraries/PanopticMath.sol

 227:                     (block.timestamp << 216) +
                         (uint256(newOrderMap) << 192) +
                         uint256(uint192(medianData << 24)) +
                         uint256(uint24(lastObservedTick));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L227

```solidity
File: contracts/types/TokenId.sol

 406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L406


## [NC-14] Consider using delete rather than assigning zero/false to clear values
The delete keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic

**Total Instances:** 1

```solidity
File: contracts/SemiFungiblePositionManager.sol

 332:         s_poolContext[poolId].locked = false;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L332


## [NC-15] Consider using descriptive constants when passing zero as a function argument
Passing zero as a function argument can sometimes result in a security issue (e.g. passing zero as the slippage parameter). Consider using a constant variable with a descriptive name, so it’s clear that the argument is intentionally being used, and for the right reasons.

**Total Instances:** 62

```solidity
File: contracts/CollateralTracker.sol

 712:                         LeftRightSigned
                                 .wrap(0)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L712

```solidity
File: contracts/PanopticPool.sol

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

 1567:                         premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

 1592:         _validatePositionList(owner, positionIdList, 0);

 1614:             accumulatedPremium = LeftRightUnsigned
                      .wrap(0)

 1633:             LeftRightSigned realizedPremia = LeftRightSigned
                      .wrap(0)

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

 1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned
                              .wrap(0)

 1774:                 LeftRightUnsigned
                          .wrap(0)

 1929:                             ? LeftRightUnsigned
                                      .wrap(0)

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

 1965:                             : LeftRightUnsigned
                                      .wrap(0)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L634

```solidity
File: contracts/SemiFungiblePositionManager.sol

 645:             s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

 648:             s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

 833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

 848:             totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(

 1038:             s_accountLiquidity[positionKey] = LeftRightUnsigned
                      .wrap(0)

 1166:             ? LeftRightSigned
                      .wrap(0)

 1174:             : LeftRightSigned
                      .wrap(0)

 1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

 1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

 1306:             collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(

 1376:                     deltaPremiumOwed = LeftRightUnsigned
                              .wrap(0)

 1400:                     deltaPremiumGross = LeftRightUnsigned
                              .wrap(0)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L645

```solidity
File: contracts/libraries/FeesCalc.sol

 115:             LeftRightSigned
                     .wrap(0)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L115

```solidity
File: contracts/libraries/PanopticMath.sol

 598:         return LeftRightUnsigned.wrap(0).toRightSlot(amount0).toLeftSlot(amount1);

 671:                 (uint256 balanceCross, uint256 thresholdCross) = PanopticMath.convertCollateralData(
                         tokenData0,
                         tokenData1,
                         0,
                         sqrtPriceX96Twap

 694:                 Math.max(premia.rightSlot(), 0);

 696:                 Math.max(premia.leftSlot(), 0);

 749:                 LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(

 791:             int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);

 792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

 856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

 857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

 880:                                 tokenId.strike(0),

 881:                                 tokenId.width(0),

 882:                                 tokenId.tokenType(0)

 888:                         settled0 = Math.max(
                                 0,
                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0

 892:                         settled1 = Math.max(
                                 0,
                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1

 898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(

 933:                     LeftRightSigned
                             .wrap(0)

 951:                     LeftRightSigned
                             .wrap(0)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L598

```solidity
File: contracts/types/LeftRight.sol

 265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

 266:                     int128(Math.max(left128, 0))

 294:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(

 297:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L265

```solidity
File: contracts/types/TokenId.sol

 406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

 501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L501


## [NC-16] Consider using the `using-for` syntax
The `using-for` [syntax](https://docs.soliditylang.org/en/latest/contracts.html#using-for) is the more common way of calling library functions.

**Total Instances:** 321

```solidity
File: contracts/CollateralTracker.sol

 170:         if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

 229:         if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();

 292:             InteractionHelper.computeName(

 305:         return InteractionHelper.computeSymbol(s_underlyingToken, TICKER_PREFIX);

 312:         return InteractionHelper.computeDecimals(s_underlyingToken);

 331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

 350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

 380:         return Math.mulDiv(assets, totalSupply, totalAssets());

 380:         return Math.mulDiv(assets, totalSupply, totalAssets());

 387:         return Math.mulDiv(shares, totalAssets(), totalSupply);

 387:         return Math.mulDiv(shares, totalAssets(), totalSupply);

 402:             shares = Math.mulDiv(

 402:             shares = Math.mulDiv(

 418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 424:         SafeTransferLib.safeTransferFrom(

 462:             assets = Math.mulDivRoundingUp(

 462:             assets = Math.mulDivRoundingUp(

 480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 484:         SafeTransferLib.safeTransferFrom(

 512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

 512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

 521:         return Math.mulDivRoundingUp(assets, supply, totalAssets());

 521:         return Math.mulDivRoundingUp(assets, supply, totalAssets());

 536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

 556:         SafeTransferLib.safeTransferFrom(

 575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

 575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

 596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

 616:         SafeTransferLib.safeTransferFrom(

 669:                             Math.unsafeDivRoundingUp(

 669:                             Math.unsafeDivRoundingUp(

 675:                     maxNumRangesFromStrike = Math.max(

 675:                     maxNumRangesFromStrike = Math.max(

 677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

 677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

 687:                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 693:                     (currentValue0, currentValue1) = Math.getAmountsForLiquidity(

 693:                     (currentValue0, currentValue1) = Math.getAmountsForLiquidity(

 698:                     (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(

 698:                     (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(

 956:                 Math.mulDiv(

 956:                 Math.mulDiv(

 959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

 959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

 1012:                 uint256 sharesToBurn = Math.mulDivRoundingUp(

 1012:                 uint256 sharesToBurn = Math.mulDivRoundingUp(

 1069:                 uint256 sharesToBurn = Math.mulDivRoundingUp(

 1069:                 uint256 sharesToBurn = Math.mulDivRoundingUp(

 1109:                 uint256 swapCommission = Math.unsafeDivRoundingUp(

 1109:                 uint256 swapCommission = Math.unsafeDivRoundingUp(

 1110:                     s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),

 1110:                     s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),

 1120:                 Math.unsafeDivRoundingUp(

 1120:                 Math.unsafeDivRoundingUp(

 1210:             TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);

 1322:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

 1363:                         ? Math.getSqrtRatioAtTick(

 1363:                         ? Math.getSqrtRatioAtTick(

 1364:                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

 1364:                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

 1366:                         : Math.getSqrtRatioAtTick(

 1366:                         : Math.getSqrtRatioAtTick(

 1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

 1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

 1401:                         required += Math.mulDiv96RoundingUp(amountMoved, c2);

 1401:                         required += Math.mulDiv96RoundingUp(amountMoved, c2);

 1408:                         uint160 scaleFactor = Math.getSqrtRatioAtTick(

 1408:                         uint160 scaleFactor = Math.getSqrtRatioAtTick(

 1411:                         uint256 c3 = Math.mulDivRoundingUp(

 1411:                         uint256 c3 = Math.mulDivRoundingUp(

 1486:                 required = Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS);

 1486:                 required = Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS);

 1496:                 required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);

 1496:                 required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);

 1518:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

 1521:         LeftRightUnsigned amountsMovedPartner = PanopticMath.getAmountsMoved(

 1571:                     ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)

 1571:                     ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)

 1572:                     : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

 1572:                     : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

 1579:         spreadRequirement = Math.max(

 1579:         spreadRequirement = Math.max(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L170

```solidity
File: contracts/PanopticFactory.sol

 150:         if (msg.sender != currentOwner) revert Errors.NotOwner();

 179:         CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);

 182:             SafeTransferLib.safeTransferFrom(

 189:             SafeTransferLib.safeTransferFrom(

 220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

 224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

 227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

 230:             revert Errors.PoolAlreadyInitialized();

 241:             Clones.clone(COLLATERAL_REFERENCE)

 244:             Clones.clone(COLLATERAL_REFERENCE)

 304:             uint256 rarity = PanopticMath.numberOfLeadingHexZeros(

 353:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)

 353:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)

 357:                     Math.mulDivRoundingUp(

 357:                     Math.mulDivRoundingUp(

 366:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)

 366:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)

 369:                     Math.mulDivRoundingUp(

 369:                     Math.mulDivRoundingUp(

 397:             CallbackLib.CallbackData({

 398:                 poolFeatures: CallbackLib.PoolFeatures({token0: token0, token1: token1, fee: fee}),

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L150

```solidity
File: contracts/PanopticPool.sol

 299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

 326:         InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);

 342:             revert Errors.PriceBoundFail();

 415:         (value0, value1) = FeesCalc.getPortfolioValue(

 444:             balances[k][0] = TokenId.unwrap(tokenId);

 525:         (, uint256 medianData) = PanopticMath.computeInternalMedian(

 634:             revert Errors.InvalidTokenIdParameter(0);

 639:             revert Errors.PositionAlreadyMinted();

 712:         (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath

 775:                     uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))

 775:                     uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))

 905:         int24 fastOracleTick = PanopticMath.computeMedianObservedPrice(

 915:             slowOracleTick = PanopticMath.computeMedianObservedPrice(

 923:             (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(

 940:         if (!solventAtFast) revert Errors.NotEnoughCollateral();

 943:         if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

 943:         if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

 945:                 revert Errors.NotEnoughCollateral();

 981:         (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath

 1035:             if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

 1035:             if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

 1036:                 revert Errors.StaleTWAP();

 1063:                 Math.getSqrtRatioAtTick(twapTick)

 1063:                 Math.getSqrtRatioAtTick(twapTick)

 1066:             if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();

 1098:             (liquidationBonus0, liquidationBonus1, collateralRemaining) = PanopticMath

 1102:                     Math.getSqrtRatioAtTick(twapTick),

 1102:                     Math.getSqrtRatioAtTick(twapTick),

 1103:                     Math.getSqrtRatioAtTick(finalTick),

 1103:                     Math.getSqrtRatioAtTick(finalTick),

 1122:             (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(

 1129:                 Math.getSqrtRatioAtTick(_finalTick),

 1129:                 Math.getSqrtRatioAtTick(_finalTick),

 1163:         ) revert Errors.NotEnoughCollateral();

 1188:         if (touchedId.length != 1) revert Errors.InputListFail();

 1197:         (LeftRightSigned longAmounts, LeftRightSigned delegatedAmounts) = PanopticMath

 1242:         refundAmounts = PanopticMath.getRefundAmounts(

 1324:             Math.getSqrtRatioAtTick(atTick)

 1324:             Math.getSqrtRatioAtTick(atTick)

 1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

 1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

 1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

 1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

 1349:                 Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);

 1349:                 Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);

 1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

 1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

 1354:                 Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);

 1354:                 Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);

 1383:             fingerprintIncomingList = PanopticMath.updatePositionsHash(

 1394:         if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();

 1410:         uint256 newHash = PanopticMath.updatePositionsHash(

 1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

 1451:         twapTick = PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW);

 1493:             revert Errors.EffectiveLiquidityAboveThreshold();

 1521:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

 1627:         uint256 liquidity = PanopticMath

 1680:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 1778:                             Math.min(

 1778:                             Math.min(

 1787:                             Math.min(

 1787:                             Math.min(

 1877:                     uint256 positionLiquidity = PanopticMath

 1934:                                             Math.max(

 1934:                                             Math.max(

 1951:                                             Math.max(

 1951:                                             Math.max(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L299

```solidity
File: contracts/SemiFungiblePositionManager.sol

 322:         if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();

 355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

 367:         uint64 poolId = PanopticMath.getPoolId(univ3pool);

 373:             poolId = PanopticMath.incrementPoolPattern(poolId);

 410:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

 413:             SafeTransferLib.safeTransferFrom(

 420:             SafeTransferLib.safeTransferFrom(

 443:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

 456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

 482:         _burn(msg.sender, TokenId.unwrap(tokenId), positionSize);

 515:         _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);

 549:         if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

 549:         if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

 552:         registerTokenTransfer(from, to, TokenId.wrap(id), amount);

 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

 577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);

 604:             LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 634:             ) revert Errors.TransferFailed();

 639:                 revert Errors.TransferFailed();

 688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

 702:         if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

 728:             revert Errors.PriceBoundFail();

 774:                 CallbackLib.CallbackData({

 775:                     poolFeatures: CallbackLib.PoolFeatures({

 817:                 int256 net0 = itm0 - PanopticMath.convert1to0(itm1, sqrtPriceX96);

 904:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 922:                     amount0 += Math.getAmount0ForLiquidity(liquidityChunk);

 922:                     amount0 += Math.getAmount0ForLiquidity(liquidityChunk);

 924:                     amount1 += Math.getAmount1ForLiquidity(liquidityChunk);

 924:                     amount1 += Math.getAmount1ForLiquidity(liquidityChunk);

 940:             revert Errors.PositionTooLarge();

 1018:                     revert Errors.NotEnoughLiquidity();

 1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

 1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

 1172:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

 1172:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

 1176:                 .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

 1176:                 .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

 1177:                 .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

 1177:                 .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

 1191:             CallbackLib.CallbackData({ // compute by reading values from univ3pool every time

 1192:                     poolFeatures: CallbackLib.PoolFeatures({

 1350:                 premium0X64_base = Math.mulDiv(

 1350:                 premium0X64_base = Math.mulDiv(

 1355:                 premium1X64_base = Math.mulDiv(

 1355:                 premium1X64_base = Math.mulDiv(

 1369:                     premium0X64_owed = Math

 1369:                     premium0X64_owed = Math

 1372:                     premium1X64_owed = Math

 1372:                     premium1X64_owed = Math

 1393:                     premium0X64_gross = Math

 1393:                     premium0X64_gross = Math

 1396:                     premium1X64_gross = Math

 1396:                     premium1X64_gross = Math

 1480:                     LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L322

```solidity
File: contracts/libraries/CallbackLib.sol

 37:             revert Errors.InvalidUniswapCallback();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L37

```solidity
File: contracts/libraries/FeesCalc.sol

 56:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(

 62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(

 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L56

```solidity
File: contracts/libraries/InteractionHelper.sol

 81:                     Strings.toString(fee),

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L81

```solidity
File: contracts/libraries/Math.sol

 131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

 297:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

 312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

 319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

 326:         if (toCast > uint256(type(int256).max)) revert Errors.CastingError();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L131

```solidity
File: contracts/libraries/PanopticMath.sol

 77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

 155:             return int24(Math.sort(ticks)[cardinality / 2]);

 263:             int256[] memory sortedTicks = Math.sort(twapMeasurement);

 326:             return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);

 328:             return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);

 361:             ) revert Errors.TicksNotInitializable();

 377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

 452:             convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));

 476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

 477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

 479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

 495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);

 497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

 497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

 512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

 514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

 514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

 529:                 int256 absResult = Math

 530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)

 534:                 int256 absResult = Math

 535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

 535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

 552:                 int256 absResult = Math

 553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

 557:                 int256 absResult = Math

 559:                         Math.absUint(amount),

 561:                         Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)

 587:             amount1 = Math

 588:                 .getAmount1ForLiquidity(Math.getLiquidityForAmount0(tickLower, tickUpper, amount0))

 593:             amount0 = Math

 594:                 .getAmount0ForLiquidity(Math.getLiquidityForAmount1(tickLower, tickUpper, amount1))

 621:                 shorts = shorts.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

 624:                 longs = longs.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

 629:                 shorts = shorts.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

 632:                 longs = longs.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

 678:                 uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

 681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));

 685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

 694:                 Math.max(premia.rightSlot(), 0);

 696:                 Math.max(premia.leftSlot(), 0);

 715:                     bonus1 += Math.min(

 719:                     bonus0 -= Math.min(

 733:                     bonus0 += Math.min(

 737:                     bonus1 -= Math.min(

 791:             int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);

 792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

 803:                     -Math.min(

 810:                     Math.min(

 827:                     Math.min(

 834:                     -Math.min(

 847:                 haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());

 848:                 haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());

 869:                         uint256 settled0 = Math.unsafeDivRoundingUp(

 873:                         uint256 settled1 = Math.unsafeDivRoundingUp(

 888:                         settled0 = Math.max(

 892:                         settled1 = Math.max(

 924:         uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L77

```solidity
File: contracts/libraries/SafeTransferLib.sol

 45:         if (!success) revert Errors.TransferFailed();

 75:         if (!success) revert Errors.TransferFailed();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L45

```solidity
File: contracts/types/LeftRight.sol

 163:             ) revert Errors.UnderOverFlow();

 186:             ) revert Errors.UnderOverFlow();

 199:             if (left128 != left) revert Errors.UnderOverFlow();

 204:             if (right128 != right) revert Errors.UnderOverFlow();

 222:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

 240:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

 262:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

 265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

 266:                     int128(Math.max(left128, 0))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L163

```solidity
File: contracts/types/TokenId.sol

 420:         (legLowerTick, legUpperTick) = PanopticMath.getTicks(

 501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

 513:                         revert Errors.InvalidTokenIdParameter(1);

 522:                         revert Errors.InvalidTokenIdParameter(6);

 528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

 533:                 ) revert Errors.InvalidTokenIdParameter(4);

 542:                         revert Errors.InvalidTokenIdParameter(3);

 548:                     ) revert Errors.InvalidTokenIdParameter(3);

 561:                         revert Errors.InvalidTokenIdParameter(4);

 567:                         revert Errors.InvalidTokenIdParameter(5);

 582:                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(

 598:         revert Errors.NoLegsExercisable();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L598


## [NC-17] Constants/Immutables redefined elsewhere
Consider defining in only one contract so that values cannot become out of sync when only one location is updated. A [cheap way](https://medium.com/coinmonks/gas-cost-of-solidity-library-functions-dbe0cedd4678) to store constants in a single location is to create an internal constant in a library. If the variable is a local cache of another contract’s value, consider making the cache variable internal or private, which will require external users to query the contract with the source of truth, so that callers don’t get out of sync.

**Total Instances:** 2

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  also seen in contracts/PanopticPool.sol
 66:     SemiFungiblePositionManager internal immutable SFPM;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L66

```solidity
File: contracts/libraries/Math.sol

 /// @audit  also seen in contracts/libraries/PanopticMath.sol
 15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L15


## [NC-18] Constants in comparisons should appear on the left side
Doing so will prevent [typo bugs](https://www.moserware.com/2008/01/constants-on-left-are-better-but-this.html)

**Total Instances:** 132

```solidity
File: contracts/CollateralTracker.sol

 331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

 350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

 512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

 575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

 664:                 if (positionId.isLong(leg) == 0) continue;

 708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

 709:                     (tokenType == 1 && currentValue0 < oracleValue0)

 1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

 1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

 1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

 1107:             if (intrinsicValue != 0) {

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L331

```solidity
File: contracts/PanopticFactory.sol

 224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

 227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

 229:         if (address(s_getPanopticPool[v3Pool]) != address(0))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L224

```solidity
File: contracts/PanopticPool.sol

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

 1780:                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),

 1789:                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),

 1862:             if (LeftRightSigned.unwrap(legPremia) != 0) {

 1864:                 if (tokenId.isLong(leg) == 1) {

 1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L299

```solidity
File: contracts/SemiFungiblePositionManager.sol

 355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

 362:         if (s_AddrToPoolIdData[univ3pool] != 0) return;

 372:         while (address(s_poolContext[poolId].pool) != address(0)) {

 632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

 633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

 688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

 717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

 787:             if ((itm0 != 0) && (itm1 != 0)) {

 787:             if ((itm0 != 0) && (itm1 != 0)) {

 823:             } else if (itm0 != 0) {

 833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

 999:             if (isLong == 0) {

 1066:             moved = isLong == 0

 1073:             if (tokenType == 1) {

 1078:             if (tokenType == 0) {

 1275:         if (isLong == 1) {

 1279:         if (LeftRightSigned.unwrap(amountToCollect) != 0) {

 1469:             if (netLiquidity != 0) {

 1514:                 acctPremia = isLong == 1 ? premiumOwed : premiumGross;

 1518:             acctPremia = isLong == 1

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L355

```solidity
File: contracts/libraries/FeesCalc.sol

 67:                 if (tokenId.isLong(leg) == 0) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L67

```solidity
File: contracts/libraries/Math.sol

 93:             if (x >= 0x100000000000000000000000000000000) {

 97:             if (x >= 0x10000000000000000) {

 101:             if (x >= 0x100000000) {

 105:             if (x >= 0x10000) {

 109:             if (x >= 0x100) {

 113:             if (x >= 0x10) {

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

 179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

 360:             if (prod1 == 0) {

 474:             if (prod1 == 0) {

 537:             if (prod1 == 0) {

 614:             if (prod1 == 0) {

 691:             if (prod1 == 0) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L93

```solidity
File: contracts/libraries/PanopticMath.sol

 77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

 211:                     if (rank == 7) {

 325:         if (tokenId.asset(legIndex) == 0) {

 357:                 tickLower % tickSpacing != 0 ||

 358:                 tickUpper % tickSpacing != 0 ||

 425:         if (tokenType == 0) {

 475:             uint256 notional = asset == 0

 479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

 584:         if (tokenId.asset(legIndex) == 0) {

 615:         bool isShort = tokenId.isLong(legIndex) == 0;

 618:         if (tokenId.tokenType(legIndex) == 0) {

 785:                     if (tokenId.isLong(leg) == 1) {

 856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

 857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

 864:                     if (tokenId.isLong(leg) == 1) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L77

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 112:         if (to.code.length != 0) {

 163:         if (to.code.length != 0) {

 202:             interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

 203:             interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

 222:         if (to.code.length != 0) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L112

```solidity
File: contracts/types/TokenId.sol

 465:         if (i == 0)

 471:         if (i == 1)

 477:         if (i == 2)

 483:         if (i == 3)

 501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

 508:                 if (self.optionRatio(i) == 0) {

 512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

 528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

 566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

 592:                     if (self.isLong(i) == 1) return; // validated

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L592


## [NC-19] constructor should emit an event
Use events to signal significant changes to off-chain monitoring tools.

**Total Instances:** 4

```solidity
File: contracts/CollateralTracker.sol

 178:     constructor(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L178

```solidity
File: contracts/PanopticFactory.sol

 115:     constructor(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L115

```solidity
File: contracts/PanopticPool.sol

 280:     constructor(SemiFungiblePositionManager _sfpm) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L280

```solidity
File: contracts/SemiFungiblePositionManager.sol

 341:     constructor(IUniswapV3Factory _factory) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L341


## [NC-20] Contract uses both require()/revert() as well as custom errors
Consider using just one method in a single file. The below instances represents the less used technique.

**Total Instances:** 5

```solidity
File: contracts/libraries/Math.sol

 131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

 297:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

 312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

 319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

 326:         if (toCast > uint256(type(int256).max)) revert Errors.CastingError();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L326


## [NC-21] Contracts should expose an interface
`Contracts` that contains `external`/`public` functions should expose an `interface` so that other projects can more easily integrate with it, without having to develop their own non-standard variants.

**Total Instances:** 7

```solidity
File: contracts/CollateralTracker.sol

 36: contract CollateralTracker is ERC20Minimal, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36

```solidity
File: contracts/PanopticFactory.sol

 26: contract PanopticFactory is Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L26

```solidity
File: contracts/PanopticPool.sol

 27: contract PanopticPool is ERC1155Holder, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L27

```solidity
File: contracts/SemiFungiblePositionManager.sol

 72: contract SemiFungiblePositionManager is ERC1155, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L72

```solidity
File: contracts/multicall/Multicall.sol

 8: abstract contract Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L8

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 11: abstract contract ERC1155 {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L11

```solidity
File: contracts/tokens/ERC20Minimal.sol

 9: abstract contract ERC20Minimal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L9


## [NC-22] Contract variables should have comments
Consider adding some comments on non-public contract variables to explain what they are supposed to do. This will help for future code reviews.

**Total Instances:** 1

```solidity
File: contracts/SemiFungiblePositionManager.sol

 289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L289


## [NC-23] Contracts should have full test coverage
While 100% code coverage does not guarantee that there are no bugs, it often will catch easy-to-find bugs, and will ensure that there are fewer regressions when the code invariably has to be modified. Furthermore, in order to get full coverage, code authors will often have to re-organize their code so that it is more modular, so that each component can be tested separately, which reduces interdependencies between modules and layers, and makes for code that is easier to reason about and audit.

**Total Instances:** 20

```solidity
File: contracts/CollateralTracker.sol

 36: contract CollateralTracker is ERC20Minimal, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36

```solidity
File: contracts/PanopticFactory.sol

 26: contract PanopticFactory is Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L26

```solidity
File: contracts/PanopticPool.sol

 27: contract PanopticPool is ERC1155Holder, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L27

```solidity
File: contracts/SemiFungiblePositionManager.sol

 72: contract SemiFungiblePositionManager is ERC1155, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L72

```solidity
File: contracts/libraries/CallbackLib.sol

 12: library CallbackLib {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L12

```solidity
File: contracts/libraries/Constants.sol

 7: library Constants {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L7

```solidity
File: contracts/libraries/Errors.sol

 7: library Errors {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L7

```solidity
File: contracts/libraries/FeesCalc.sol

 39: library FeesCalc {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L39

```solidity
File: contracts/libraries/InteractionHelper.sol

 17: library InteractionHelper {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17

```solidity
File: contracts/libraries/Math.sol

 13: library Math {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L13

```solidity
File: contracts/libraries/PanopticMath.sol

 18: library PanopticMath {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18

```solidity
File: contracts/libraries/SafeTransferLib.sol

 11: library SafeTransferLib {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L11

```solidity
File: contracts/multicall/Multicall.sol

 8: abstract contract Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L8

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 11: abstract contract ERC1155 {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L11

```solidity
File: contracts/tokens/ERC20Minimal.sol

 9: abstract contract ERC20Minimal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L9

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 6: interface IDonorNFT {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

 11: interface IERC20Partial {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L11

```solidity
File: contracts/types/LeftRight.sol

 17: library LeftRightLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L17

```solidity
File: contracts/types/LiquidityChunk.sol

 52: library LiquidityChunkLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52

```solidity
File: contracts/types/TokenId.sol

 60: library TokenIdLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L60


## [NC-24] Custom error has no error details
Consider adding parameters to the error to indicate which user or values caused the failure.

**Total Instances:** 34

```solidity
File: contracts/libraries/Errors.sol

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L10

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 55:     error NotAuthorized();

 58:     error UnsafeRecipient();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L58


## [NC-25] Default `address(0)` can be returned
'Allowing a function in Solidity to return the default address (address(0)) can be problematic as it can represent uninitialized or invalid addresses. If such an address is utilized in transfer operations or other sensitive actions, it could lead to loss of funds or unpredicted behavior. It's prudent to include checks in your functions to prevent the return of the zero address, enhancing contract security.'

**Total Instances:** 2

```solidity
File: contracts/CollateralTracker.sol

 362:         return s_underlyingToken;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L362

```solidity
File: contracts/PanopticFactory.sol

 160:         return s_owner;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L160


## [NC-26] Down casting `uint` or `int` may result in overflow
'Consider using OpenZeppelin's `SafeCast` library to prevent unexpected overflows.'

**Total Instances:** 25

```solidity
File: contracts/CollateralTracker.sol

 667:                     int24 range = int24(

 1028:             s_poolAssets = uint128(uint256(updatedAssets));

 1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

 1084:             s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));

 1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L667

```solidity
File: contracts/PanopticPool.sol

 1548:                             int128(

 1557:                             int128(

 1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))

 1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1548

```solidity
File: contracts/SemiFungiblePositionManager.sol

 1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

 1172:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

 1176:                 .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

 1177:                 .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

 1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

 1215:             int128(int256(amount1))

 1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

 1242:                 -int128(int256(amount1))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1169

```solidity
File: contracts/libraries/FeesCalc.sol

 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L117

```solidity
File: contracts/libraries/PanopticMath.sol

 103:                 (uint248(uint256(keccak256(abi.encode(tokenId)))));

 377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L103

```solidity
File: contracts/types/LiquidityChunk.sol

 173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));

 182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L173

```solidity
File: contracts/types/TokenId.sol

 160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));

 171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L171


## [NC-27] else-block not required
One level of nesting can be removed by not having an else block when the if-block returns, and `if (foo) { return 1; } else { return 2; }` becomes `if (foo) { return 1; } return 2;`. A following `else if` can become `if`

**Total Instances:** 7

```solidity
File: contracts/libraries/PanopticMath.sol

 325:         if (tokenId.asset(legIndex) == 0) {
                 return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
             } else {

 425:         if (tokenType == 0) {
                 return (
                     tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
                     tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
                 );
             } else {

 494:             if (sqrtPriceX96 < type(uint128).max) {
                     return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
                 } else {

 511:             if (sqrtPriceX96 < type(uint128).max) {
                     return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
                 } else {

 528:             if (sqrtPriceX96 < type(uint128).max) {
                     int256 absResult = Math
                         .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
                         .toInt256();
                     return amount < 0 ? -absResult : absResult;
                 } else {

 551:             if (sqrtPriceX96 < type(uint128).max) {
                     int256 absResult = Math
                         .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
                         .toInt256();
                     return amount < 0 ? -absResult : absResult;
                 } else {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L325

```solidity
File: contracts/types/TokenId.sol

 443:         } else if (optionRatios < 2 ** 160) {
                 return 2;
             } else if (optionRatios < 2 ** 208) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L443


## [NC-28] Empty bytes check is missing
'When developing smart contracts in Solidity, it's crucial to validate the inputs of your functions. This includes ensuring that the bytes parameters are not empty, especially when they represent crucial data such as addresses, identifiers, or raw data that the contract needs to process. Missing empty bytes checks can lead to unexpected behaviour in your contract.For instance, certain operations might fail, produce incorrect results, or consume unnecessary gas when performed with empty bytes.Moreover, missing input validation can potentially expose your contract to malicious activity, including exploitation of unhandled edge cases. To mitigate these issues, always validate that bytes parameters are not empty when the logic of your contract requires it.'

**Total Instances:** 7

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  data is not checked
 172:     function uniswapV3MintCallback(
             uint256 amount0Owed,
             uint256 amount1Owed,
             bytes calldata data
         ) external {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L172

```solidity
File: contracts/SemiFungiblePositionManager.sol

 /// @audit  data is not checked
 402:     function uniswapV3MintCallback(
             uint256 amount0Owed,
             uint256 amount1Owed,
             bytes calldata data
         ) external {

 /// @audit  data is not checked
 435:     function uniswapV3SwapCallback(
             int256 amount0Delta,
             int256 amount1Delta,
             bytes calldata data
         ) external {

 /// @audit  data is not checked
 540:     function safeTransferFrom(
             address from,
             address to,
             uint256 id,
             uint256 amount,
             bytes calldata data
         ) public override {

 /// @audit  data is not checked
 566:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public override {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L402

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 /// @audit  data is not checked
 94:     function safeTransferFrom(
            address from,
            address to,
            uint256 id,
            uint256 amount,
            bytes calldata data
        ) public virtual {

 /// @audit  data is not checked
 130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L130


## [NC-29] Events are missing sender information
When an action is triggered based on a user’s action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the `msg.sender` the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

**Total Instances:** 9

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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L154

```solidity
File: contracts/PanopticPool.sol

 853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

 1654:             emit PremiumSettled(owner, tokenId, realizedPremia);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L853

```solidity
File: contracts/SemiFungiblePositionManager.sol

 390:         emit PoolInitialized(univ3pool, poolId);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L390

```solidity
File: contracts/tokens/ERC20Minimal.sol

 94:         emit Transfer(from, to, amount);

 112:         emit Transfer(from, to, amount);

 130:         emit Transfer(address(0), to, amount);

 145:         emit Transfer(from, address(0), amount);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L145


## [NC-30] Events may be emitted out of order due to reentrancy
Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls

**Total Instances:** 3

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  cloneDeterministic() prior to emission
 268:         emit PoolDeployed(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L268

```solidity
File: contracts/PanopticPool.sol

 /// @audit  toLeftSlot() prior to emission
 666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);

 /// @audit  toRightSlot() prior to emission
 1170:         emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1170


## [NC-31] Expressions for constant values should use immutable rather than constant
While it does not save gas for some simple binary expressions because the compiler knows that developers often make this mistake, it’s still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.

**Total Instances:** 7

```solidity
File: contracts/PanopticPool.sol

 103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

 105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

 165:     uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L103

```solidity
File: contracts/libraries/Constants.sol

 12:     int24 internal constant MIN_V3POOL_TICK = -887272;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L12

```solidity
File: contracts/libraries/Math.sol

 15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L15

```solidity
File: contracts/libraries/PanopticMath.sol

 23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L23

```solidity
File: contracts/types/LeftRight.sol

 26:     int256 internal constant LEFT_HALF_BIT_MASK_INT =

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L26


## [NC-32] High cyclomatic complexity
Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

**Total Instances:** 6

```solidity
File: contracts/SemiFungiblePositionManager.sol

 680:     function _validateAndForwardToAMM(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool isBurn
         ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {
             // Reverts if positionSize is 0 and user did not own the position before minting/burning
             if (positionSize == 0) revert Errors.OptionsBalanceZero();
     
             /// @dev the flipToBurnToken() function flips the isLong bits
             if (isBurn) {
                 tokenId = tokenId.flipToBurnToken();
             }
     
             // Validate tokenId
             tokenId.validate();
     
             // Extract univ3pool from the poolId map to Uniswap Pool
             IUniswapV3Pool univ3pool = s_poolContext[tokenId.poolId()].pool;
     
             // Revert if the pool not been previously initialized
             if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();
     
             // initialize some variables returned by the _createPositionInAMM function
             LeftRightSigned itmAmounts;
     
             // calls a function that loops through each leg of tokenId and mints/burns liquidity in Uni v3 pool
             (totalMoved, collectedByLeg, itmAmounts) = _createPositionInAMM(
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
             }
     
             // Get the current tick of the Uniswap pool, check slippage
             (, int24 currentTick, , , , , ) = univ3pool.slot0();
     
             if ((currentTick >= tickLimitHigh) || (currentTick <= tickLimitLow))

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
             uint256 tokenType = tokenId.tokenType(leg);
             // unique key to identify the liquidity chunk in this uniswap pool
             bytes32 positionKey = keccak256(
                 abi.encodePacked(
                     address(univ3pool),
                     msg.sender,
                     tokenType,
                     liquidityChunk.tickLower(),
                     liquidityChunk.tickUpper()
                 )
             );
     
             // update our internal bookkeeping of how much liquidity we have deployed in the AMM
             // for example: if this _leg is short, we add liquidity to the amm, make sure to add that to our tracking
             uint128 updatedLiquidity;
             uint256 isLong = tokenId.isLong(leg);
             LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache
             {
                 // did we have liquidity already deployed in Uniswap for this chunk range from some past mint?
     
                 // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user
                 // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller
                 // the reason why it is called "removedLiquidity" is because long options are created by removing -ie.short selling LP positions
                 uint128 startingLiquidity = currentLiquidity.rightSlot();
                 uint128 removedLiquidity = currentLiquidity.leftSlot();
                 uint128 chunkLiquidity = liquidityChunk.liquidity();
     
                 if (isLong == 0) {
                     // selling/short: so move from msg.sender *to* uniswap
                     // we're minting more liquidity in uniswap: so add the incoming liquidity chunk to the existing liquidity chunk
                     updatedLiquidity = startingLiquidity + chunkLiquidity;
     
                     /// @dev If the isLong flag is 0=short but the position was burnt, then this is closing a long position
                     /// @dev so the amount of removed liquidity should decrease.
                     if (isBurn) {
                         removedLiquidity -= chunkLiquidity;
                     }
                 } else {
                     // the _leg is long (buying: moving *from* uniswap to msg.sender)
                     // so we seek to move the incoming liquidity chunk *out* of uniswap - but was there sufficient liquidity sitting in uniswap
                     // in the first place?
                     if (startingLiquidity < chunkLiquidity) {
                         // the amount we want to move (liquidityChunk.legLiquidity()) out of uniswap is greater than
                         // what the account that owns the liquidity in uniswap has (startingLiquidity)
                         // we must ensure that an account can only move its own liquidity out of uniswap
                         // so we revert in this case
                         revert Errors.NotEnoughLiquidity();
                     } else {
                         // startingLiquidity is >= chunkLiquidity, so no possible underflow
                         unchecked {
                             // we want to move less than what already sits in uniswap, no problem:
                             updatedLiquidity = startingLiquidity - chunkLiquidity;
                         }
                     }
     
                     /// @dev If the isLong flag is 1=long and the position is minted, then this is opening a long position
                     /// @dev so the amount of removed liquidity should increase.
                     if (!isBurn) {
                         // we can't remove more liquidity than we add in the first place, so this can't overflow
                         unchecked {
                             removedLiquidity += chunkLiquidity;
                         }
                     }
                 }
     
                 // update the starting liquidity for this position for next time around
                 s_accountLiquidity[positionKey] = LeftRightUnsigned
                     .wrap(0)
                     .toLeftSlot(removedLiquidity)
                     .toRightSlot(updatedLiquidity);
             }
     
             // track how much liquidity we need to collect from uniswap
             // add the fees that accumulated in uniswap within the liquidityChunk:
             {
                 /** if the position is NOT long (selling a put or a call), then _mintLiquidity to move liquidity
                     from the msg.sender to the uniswap v3 pool:
                     Selling(isLong=0): Mint chunk of liquidity in Uniswap (defined by upper tick, lower tick, and amount)
                            ┌─────────────────────────────────┐
                     ▲     ┌▼┐ liquidityChunk                 │
                     │  ┌──┴─┴──┐                         ┌───┴──┐
                     │  │       │                         │      │
                     └──┴───────┴──►                      └──────┘
                        Uniswap v3                      msg.sender
                 
                  else: the position is long (buying a put or a call), then _burnLiquidity to remove liquidity from univ3
                     Buying(isLong=1): Burn in Uniswap
                            ┌─────────────────┐
                     ▲     ┌┼┐                │
                     │  ┌──┴─┴──┐         ┌───▼──┐
                     │  │       │         │      │
                     └──┴───────┴──►      └──────┘
                         Uniswap v3      msg.sender 
                 */
                 moved = isLong == 0
                     ? _mintLiquidity(liquidityChunk, univ3pool)
                     : _burnLiquidity(liquidityChunk, univ3pool); // from msg.sender to Uniswap
                 // add the moved liquidity chunk to amount we need to collect from uniswap:
     
                 // Is this _leg ITM?
                 // if tokenType is 1, and we transacted some token0: then this leg is ITM!
                 if (tokenType == 1) {
                     // extract amount moved out of UniswapV3 pool
                     itmAmounts = itmAmounts.toRightSlot(moved.rightSlot());
                 }
                 // if tokenType is 0, and we transacted some token1: then this leg is ITM
                 if (tokenType == 0) {
                     // Add this in-the-money amount transacted.
                     itmAmounts = itmAmounts.toLeftSlot(moved.leftSlot());
                 }
             }
     
             // if there was liquidity at that tick before the transaction, collect any accumulated fees
             if (currentLiquidity.rightSlot() > 0) {
                 collectedSingleLeg = _collectAndWritePositionData(
                     liquidityChunk,
                     univ3pool,
                     currentLiquidity,
                     positionKey,
                     moved,
                     isLong
                 );
             }
     
             // position has been touched, update s_accountFeesBase with the latest values from the pool.positions
             // round up the stored feesbase to minimize Δfeesbase when we next calculate it
             s_accountFeesBase[positionKey] = _getFeesBase(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L680

```solidity
File: contracts/libraries/Math.sol

 91:     function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {
            unchecked {

 128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {
             unchecked {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L91

```solidity
File: contracts/libraries/PanopticMath.sol

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
             unchecked {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L768

```solidity
File: contracts/types/TokenId.sol

 500:     function validate(TokenId self) internal pure {
             if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);
     
             // loop through the 4 (possible) legs in the tokenId `self`
             unchecked {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L500


## [NC-33] if-statement can be converted to a ternary
The code can be made more compact while also increasing readability by converting the following if-statements to ternaries (e.g. ``foo += (x > y) ? a : b`)

**Total Instances:** 10

```solidity
File: contracts/CollateralTracker.sol

 976:         if (assets > 0) {
                 _transferFrom(refunder, refundee, convertToShares(uint256(assets)));
             } else {
                 unchecked {

 1450:         if (isLong != tokenId.isLong(partnerIndex)) {
                  if (isLong == 1) {
                      // compute the total amount of funds moved for that position
                      required = _computeSpread(
                          tokenId,
                          positionSize,
                          index,
                          partnerIndex,
                          poolUtilization
                      );
                  }
              } else {
                  required = _computeStrangle(tokenId, index, positionSize, atTick, poolUtilization);

 1541:         if (tokenId.asset(index) != tokenType) {
                  unchecked {
                      // always take the absolute values of the difference of amounts moved
                      if (tokenType == 0) {
                          spreadRequirement = movedRight < movedPartnerRight
                              ? movedPartnerRight - movedRight
                              : movedRight - movedPartnerRight;
                      } else {
                          spreadRequirement = movedLeft < movedPartnerLeft
                              ? movedPartnerLeft - movedLeft
                              : movedLeft - movedPartnerLeft;
                      }
                  }
              } else {
                  unchecked {

 1544:                 if (tokenType == 0) {
                          spreadRequirement = movedRight < movedPartnerRight
                              ? movedPartnerRight - movedRight
                              : movedRight - movedPartnerRight;
                      } else {
                          spreadRequirement = movedLeft < movedPartnerLeft

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L976

```solidity
File: contracts/PanopticPool.sol

 914:         if (SLOW_ORACLE_UNISWAP_MODE) {
                 slowOracleTick = PanopticMath.computeMedianObservedPrice(
                     _univ3pool,
                     observationIndex,
                     observationCardinality,
                     SLOW_ORACLE_CARDINALITY,
                     SLOW_ORACLE_PERIOD
                 );
             } else {
                 (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L914

```solidity
File: contracts/SemiFungiblePositionManager.sol

 1013:                 if (startingLiquidity < chunkLiquidity) {
                          // the amount we want to move (liquidityChunk.legLiquidity()) out of uniswap is greater than
                          // what the account that owns the liquidity in uniswap has (startingLiquidity)
                          // we must ensure that an account can only move its own liquidity out of uniswap
                          // so we revert in this case
                          revert Errors.NotEnoughLiquidity();
                      } else {
                          // startingLiquidity is >= chunkLiquidity, so no possible underflow
                          unchecked {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1013

```solidity
File: contracts/libraries/FeesCalc.sol

 67:                 if (tokenId.isLong(leg) == 0) {
                        unchecked {
                            value0 += int256(amount0);
                            value1 += int256(amount1);
                        }
                    } else {
                        unchecked {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L67

```solidity
File: contracts/libraries/PanopticMath.sol

 618:         if (tokenId.tokenType(legIndex) == 0) {
                 if (isShort) {
                     // if option is short, increment shorts by contracts
                     shorts = shorts.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));
                 } else {
                     // is option is long, increment longs by contracts
                     longs = longs.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));
                 }
             } else {
                 if (isShort) {

 619:             if (isShort) {
                     // if option is short, increment shorts by contracts
                     shorts = shorts.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));
                 } else {
                     // is option is long, increment longs by contracts
                     longs = longs.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

 627:             if (isShort) {
                     // if option is short, increment shorts by notional
                     shorts = shorts.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));
                 } else {
                     // if option is long, increment longs by notional
                     longs = longs.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L627


## [NC-34] If statement control structures do not comply with best practices
If statements which include a single line do not need to have curly brackets, however according to the Solidity style guide the line of code executed upon the if statement condition being met should still be on the next line, not on the same line as the if statement declaration.

**Total Instances:** 71

```solidity
File: contracts/CollateralTracker.sol

 170:         if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

 229:         if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();

 331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

 350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

 418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

 544:             if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

 596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

 602:             if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L170

```solidity
File: contracts/PanopticFactory.sol

 150:         if (msg.sender != currentOwner) revert Errors.NotOwner();

 220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

 224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

 227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L150

```solidity
File: contracts/PanopticPool.sol

 299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

 533:         if (medianData != 0) s_miniMedian = medianData;

 664:         if (medianData != 0) s_miniMedian = medianData;

 940:         if (!solventAtFast) revert Errors.NotEnoughCollateral();

 1066:             if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();

 1188:         if (touchedId.length != 1) revert Errors.InputListFail();

 1394:         if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();

 1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

 1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L299

```solidity
File: contracts/SemiFungiblePositionManager.sol

 322:         if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();

 355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

 549:         if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

 688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

 702:         if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L322

```solidity
File: contracts/libraries/Math.sol

 131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

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

 297:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

 312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

 319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

 326:         if (toCast > uint256(type(int256).max)) revert Errors.CastingError();

 768:             if (left < j) quickSort(arr, left, j);

 769:             if (i < right) quickSort(arr, i, right);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L131

```solidity
File: contracts/libraries/PanopticMath.sol

 479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

 856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

 857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L479

```solidity
File: contracts/libraries/SafeTransferLib.sol

 45:         if (!success) revert Errors.TransferFailed();

 75:         if (!success) revert Errors.TransferFailed();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L45

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 101:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

 137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L101

```solidity
File: contracts/tokens/ERC20Minimal.sol

 84:         if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L84

```solidity
File: contracts/types/LeftRight.sol

 199:             if (left128 != left) revert Errors.UnderOverFlow();

 204:             if (right128 != right) revert Errors.UnderOverFlow();

 222:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

 240:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

 262:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L199

```solidity
File: contracts/types/TokenId.sol

 501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

 528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L528


## [NC-35] Imports could be organized more systematically
The contract’s interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

**Total Instances:** 6

```solidity
File: contracts/CollateralTracker.sol

 /// @audit  Out of order with the previous import
 12: import {InteractionHelper} from "@libraries/InteractionHelper.sol";

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L12

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  Out of order with the previous import
 8: import {IDonorNFT} from "@contracts/tokens/interfaces/IDonorNFT.sol";

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L8

```solidity
File: contracts/PanopticPool.sol

 /// @audit  Out of order with the previous import
 7: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";

 /// @audit  Out of order with the previous import
 15: import {InteractionHelper} from "@libraries/InteractionHelper.sol";

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L7

```solidity
File: contracts/libraries/InteractionHelper.sol

 /// @audit  Out of order with the previous import
 6: import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L6

```solidity
File: contracts/libraries/PanopticMath.sol

 /// @audit  Out of order with the previous import
 6: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L6


## [NC-36] Inconsistent spacing in comments
The comments below are in the `//x` format, which differs from the commonly used idiomatic comment syntax of `//<space>x`. It is recommended to use a consistent comment syntax throughout.

**Total Instances:** 5

```solidity
File: contracts/CollateralTracker.sol

 1118:             //compute total commission amount = commission rate + spread fee

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1118

```solidity
File: contracts/SemiFungiblePositionManager.sol

 610:             //construct the positionKey for the from and to addresses

 643:             //update+store liquidity and fee values between accounts

 821:                 //compute the swap amount, set as positive (exact input)

 988:         LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L988


## [NC-37] Interface files should not use fixed compiler versions
Interfaces should not use fixed compiler versions, since they may be used by projects using a different version.

**Total Instances:** 2

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L2

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L2


## [NC-38] `internal` functions not called by the contract should be removed
If the functions are required by an interface, the contract should inherit from that interface and use the `override` keyword

**Total Instances:** 46

```solidity
File: contracts/libraries/Math.sol

 25:     function min24(int24 a, int24 b) internal pure returns (int24) {

 302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {

 325:     function toInt256(uint256 toCast) internal pure returns (int256) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L25

```solidity
File: contracts/libraries/PanopticMath.sol

 468:     function convertNotional(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L468

```solidity
File: contracts/libraries/SafeTransferLib.sol

 52:     function safeTransfer(address token, address to, uint256 amount) internal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L52

```solidity
File: contracts/types/LeftRight.sol

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L39

```solidity
File: contracts/types/LiquidityChunk.sol

 89:     function addLiquidity(

 102:     function addTickLower(

 118:     function addTickUpper(

 135:     function updateTickLower(

 151:     function updateTickUpper(

 171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

 180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

 189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L89

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

 366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

 404:     function countLongs(TokenId self) internal pure returns (uint256) {

 416:     function asTicks(

 432:     function countLegs(TokenId self) internal pure returns (uint256) {

 464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

 500:     function validate(TokenId self) internal pure {

 578:     function validateIsExercisable(TokenId self, int24 currentTick) internal pure {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L578


## [NC-39] Invalid NatSpec comment style
NatSpec comment in solidity should use `///` or `/* ... */` syntax.

**Total Instances:** 6

```solidity
File: contracts/SemiFungiblePositionManager.sol

 358:         // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting

 360:         // @dev some pools may not be deployable if the poolId has a collision (since we take only 8 bytes)

 603:             // @dev see `contracts/types/LiquidityChunk.sol`

 836:             // @dev note this triggers our swap callback function

 903:                 // @dev see `contracts/types/LiquidityChunk.sol`

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L358

```solidity
File: contracts/libraries/PanopticMath.sol

 98:         // @dev 0 ^ x = x

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L98


## [NC-40] Libraries should be defined in separate files from their usage
The libraries below should be defined in separate files, so that it’s easier for future projects to import them, and to avoid duplication later on if they need to be used elsewhere in the project.

**Total Instances:** 4

```solidity
File: contracts/libraries/PanopticMath.sol

 18: library PanopticMath {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18

```solidity
File: contracts/types/LeftRight.sol

 17: library LeftRightLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L17

```solidity
File: contracts/types/LiquidityChunk.sol

 52: library LiquidityChunkLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52

```solidity
File: contracts/types/TokenId.sol

 60: library TokenIdLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L60


## [NC-41] Long functions should be refactored into multiple, smaller, functions
Refactor long functions into smaller, more modular ones for improved code readability and maintainability.

**Total Instances:** 23

```solidity
File: contracts/CollateralTracker.sol

 /// @audit  40+ lines
 221:     function startToken(
             bool underlyingIsToken0,
             address token0,
             address token1,
             uint24 fee,
             PanopticPool panopticPool
         ) external {

 /// @audit  40+ lines
 751:     function _sellCollateralRatio(
             int256 utilization
         ) internal view returns (uint256 sellCollateralRatio) {

 /// @audit  40+ lines
 806:     function _buyCollateralRatio(
             uint256 utilization
         ) internal view returns (uint256 buyCollateralRatio) {

 /// @audit  30+ lines
 1200:     function _getTotalRequiredCollateral(
              int24 atTick,
              uint256[2][] memory positionBalanceArray
          ) internal view returns (uint256 tokenRequired) {

 /// @audit  60+ lines
 1510:     function _computeSpread(
              TokenId tokenId,
              uint128 positionSize,
              uint256 index,
              uint256 partnerIndex,
              uint128 poolUtilization
          ) internal view returns (uint256 spreadRequirement) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L221

```solidity
File: contracts/PanopticFactory.sol

 /// @audit  50+ lines
 210:     function deployNewPool(
             address token0,
             address token1,
             uint24 fee,
             bytes32 salt
         ) external returns (PanopticPool newPoolContract) {

 /// @audit  60+ lines
 335:     function _mintFullRange(
             IUniswapV3Pool v3Pool,
             address token0,
             address token1,
             uint24 fee
         ) internal returns (uint256, uint256) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L210

```solidity
File: contracts/PanopticPool.sol

 /// @audit  30+ lines
 291:     function startPool(
             IUniswapV3Pool _univ3pool,
             address token0,
             address token1,
             CollateralTracker collateralTracker0,
             CollateralTracker collateralTracker1
         ) external {

 /// @audit  60+ lines
 429:     function _calculateAccumulatedPremia(
             address user,
             TokenId[] calldata positionIdList,
             bool computeAllPremia,
             bool includePendingPremium,
             int24 atTick
         ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

 /// @audit  50+ lines
 614:     function _mintOptions(
             TokenId[] calldata positionIdList,
             uint128 positionSize,
             uint64 effectiveLiquidityLimitX32,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal {

 /// @audit  50+ lines
 887:     function _validateSolvency(
             address user,
             TokenId[] calldata positionIdList,
             uint256 buffer
         ) internal view returns (uint256 medianData) {

 /// @audit  40+ lines
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

 /// @audit  150+ lines
 1017:     function liquidate(
              TokenId[] calldata positionIdListLiquidator,
              address liquidatee,
              LeftRightUnsigned delegations,
              TokenId[] calldata positionIdList
          ) external {

 /// @audit  90+ lines
 1179:     function forceExercise(
              address account,
              TokenId[] calldata touchedId,
              TokenId[] calldata positionIdListExercisee,
              TokenId[] calldata positionIdListExercisor
          ) external {

 /// @audit  30+ lines
 1290:     function _checkSolvencyAtTick(
              address account,
              TokenId[] calldata positionIdList,
              int24 currentTick,
              int24 atTick,
              uint256 buffer
          ) internal view returns (bool) {

 /// @audit  70+ lines
 1587:     function settleLongPremium(
              TokenId[] calldata positionIdList,
              address owner,
              uint256 legIndex
          ) external {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L291

```solidity
File: contracts/SemiFungiblePositionManager.sol

 /// @audit  40+ lines
 350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

 /// @audit  40+ lines
 680:     function _validateAndForwardToAMM(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool isBurn
         ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

 /// @audit  70+ lines
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

 /// @audit  140+ lines
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

 /// @audit  70+ lines
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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350

```solidity
File: contracts/libraries/PanopticMath.sol

 /// @audit  30+ lines
 289:     function getLiquidityChunk(
             TokenId tokenId,
             uint256 legIndex,
             uint128 positionSize
         ) internal pure returns (LiquidityChunk) {

 /// @audit  40+ lines
 917:     function getRefundAmounts(
             address refunder,
             LeftRightSigned refundValues,
             int24 atTick,
             CollateralTracker collateral0,
             CollateralTracker collateral1
         ) external view returns (LeftRightSigned) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L917


## [NC-42] Missing checks constructor/initializer assignments
Consider whether reasonable bounds checks for variables would be useful.

**Total Instances:** 15

```solidity
File: contracts/CollateralTracker.sol

 187:         COMMISSION_FEE = _commissionFee;

 188:         SELLER_COLLATERAL_RATIO = _sellerCollateralRatio;

 189:         BUYER_COLLATERAL_RATIO = _buyerCollateralRatio;

 190:         FORCE_EXERCISE_COST = _forceExerciseCost;

 191:         TARGET_POOL_UTIL = _targetPoolUtilization;

 192:         SATURATED_POOL_UTIL = _saturatedPoolUtilization;

 193:         ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L187

```solidity
File: contracts/PanopticFactory.sol

 123:         WETH = _WETH9;

 124:         SFPM = _SFPM;

 125:         DONOR_NFT = _donorNFT;

 127:         UNIV3_FACTORY = _univ3Factory;

 128:         POOL_REFERENCE = _poolReference;

 129:         COLLATERAL_REFERENCE = _collateralReference;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L123

```solidity
File: contracts/PanopticPool.sol

 281:         SFPM = _sfpm;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L281

```solidity
File: contracts/SemiFungiblePositionManager.sol

 342:         FACTORY = _factory;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L342


## [NC-43] Missing checks for state variable assignments
Consider whether reasonable bounds checks for variables would be useful.

**Total Instances:** 11

```solidity
File: contracts/CollateralTracker.sol

 244:         s_panopticPool = panopticPool;

 251:         s_poolFee = _poolFee;

 254:         s_univ3token0 = token0;

 255:         s_univ3token1 = token1;

 258:         s_underlyingIsToken0 = underlyingIsToken0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L244

```solidity
File: contracts/PanopticFactory.sol

 136:             s_owner = _owner;

 152:         s_owner = newOwner;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L136

```solidity
File: contracts/PanopticPool.sol

 318:         s_collateralToken0 = collateralTracker0;

 319:         s_collateralToken1 = collateralTracker1;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L318

```solidity
File: contracts/tokens/ERC20Minimal.sol

 128:         totalSupply += amount;

 142:             totalSupply -= amount;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L142


## [NC-44] Missing event for critical changes
Events should be emitted when critical changes are made to the contracts.

**Total Instances:** 4

```solidity
File: contracts/PanopticPool.sol

 859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {

 1405:     function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {

 1666:     function _updateSettlementPostMint(
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize
          ) internal {

 1833:     function _updateSettlementPostBurn(
              address owner,
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize,
              bool commitLongSettled
          ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1833


## [NC-45] Modifiers should be named in mixedCase style
As the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#modifier-names) suggests: modifiers should be named in mixedCase style. Use mixedCase. Examples: `onlyBy`, `onlyAfter`, `onlyDuringThePreSale`.

**Total Instances:** 1

```solidity
File: contracts/SemiFungiblePositionManager.sol

 305:     modifier ReentrancyLock(uint64 poolId) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L305


## [NC-46] Multiple `address`/`ID` mappings can be combined into a single `mapping` of an `address`/`ID` to a struct, for readability
Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it’s clear what data is related.

**Total Instances:** 7

```solidity
File: contracts/PanopticPool.sol

 238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

 258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))

 272:     mapping(address account => uint256 positionsHash) internal s_positionsHash;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L238

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 66:     mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;

 71:     mapping(address owner => mapping(address operator => bool approvedForAll))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L66

```solidity
File: contracts/tokens/ERC20Minimal.sol

 35:     mapping(address account => uint256 balance) public balanceOf;

 39:     mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L39


## [NC-47] NatSpec: Contract declarations should have `@author` tags
Contract declarations should have `@author` tags

**Total Instances:** 3

```solidity
File: contracts/CollateralTracker.sol

 36: contract CollateralTracker is ERC20Minimal, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 6: interface IDonorNFT {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6

```solidity
File: contracts/types/LiquidityChunk.sol

 52: library LiquidityChunkLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52


## [NC-48] NatSpec: Contract declarations should have descriptions
e.g. `@dev` or `@notice`, and it must appear above the contract definition braces in order to be identified by the compiler as NatSpec

**Total Instances:** 3

```solidity
File: contracts/libraries/InteractionHelper.sol

 17: library InteractionHelper {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17

```solidity
File: contracts/libraries/PanopticMath.sol

 18: library PanopticMath {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 6: interface IDonorNFT {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6


## [NC-49] NatSpec: Contract declarations should have `@dev` tags
`@dev` is used to explain extra details to developers

**Total Instances:** 12

```solidity
File: contracts/CollateralTracker.sol

 36: contract CollateralTracker is ERC20Minimal, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36

```solidity
File: contracts/PanopticFactory.sol

 26: contract PanopticFactory is Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L26

```solidity
File: contracts/libraries/CallbackLib.sol

 12: library CallbackLib {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L12

```solidity
File: contracts/libraries/Constants.sol

 7: library Constants {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L7

```solidity
File: contracts/libraries/Errors.sol

 7: library Errors {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L7

```solidity
File: contracts/libraries/InteractionHelper.sol

 17: library InteractionHelper {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17

```solidity
File: contracts/libraries/Math.sol

 13: library Math {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L13

```solidity
File: contracts/libraries/PanopticMath.sol

 18: library PanopticMath {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 6: interface IDonorNFT {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6

```solidity
File: contracts/types/LeftRight.sol

 17: library LeftRightLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L17

```solidity
File: contracts/types/LiquidityChunk.sol

 52: library LiquidityChunkLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52

```solidity
File: contracts/types/TokenId.sol

 60: library TokenIdLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L60


## [NC-50] NatSpec: Contract declarations should have `@notice` tags
`@notice` is used to explain to end users what the contract does, and the compiler interprets `///` or `/**` comments as this tag if one wasn’t explicitly provided

**Total Instances:** 6

```solidity
File: contracts/libraries/InteractionHelper.sol

 17: library InteractionHelper {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17

```solidity
File: contracts/libraries/PanopticMath.sol

 18: library PanopticMath {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L18

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 11: abstract contract ERC1155 {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L11

```solidity
File: contracts/tokens/ERC20Minimal.sol

 9: abstract contract ERC20Minimal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L9

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 6: interface IDonorNFT {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

 11: interface IERC20Partial {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L11


## [NC-51] NatSpec: Contract declarations should have `@title` tags
Contract declarations should have `@title` tags

**Total Instances:** 5

```solidity
File: contracts/CollateralTracker.sol

 36: contract CollateralTracker is ERC20Minimal, Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L36

```solidity
File: contracts/libraries/InteractionHelper.sol

 17: library InteractionHelper {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L17

```solidity
File: contracts/libraries/SafeTransferLib.sol

 11: library SafeTransferLib {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L11

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 6: interface IDonorNFT {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L6

```solidity
File: contracts/types/LiquidityChunk.sol

 52: library LiquidityChunkLibrary {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L52


## [NC-52] NatSpec: Error declarations should have `@dev` tag
Error declarations should have `@dev` tag

**Total Instances:** 33

```solidity
File: contracts/libraries/Errors.sol

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L13

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 55:     error NotAuthorized();

 58:     error UnsafeRecipient();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L58


## [NC-53] NatSpec: Error declarations should have `@param` tag
Error declarations should have `@param` tag

**Total Instances:** 34

```solidity
File: contracts/libraries/Errors.sol

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L10

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 55:     error NotAuthorized();

 58:     error UnsafeRecipient();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L58


## [NC-54] NatSpec: Event Declaration should have `@dev` tag
NatSpec: Event Declaration should have `@dev` tag.

**Total Instances:** 11

```solidity
File: contracts/CollateralTracker.sol

 49:     event Deposit(address indexed sender, address indexed owner, uint256 assets, uint256 shares);

 57:     event Withdraw(
            address indexed sender,
            address indexed receiver,
            address indexed owner,
            uint256 assets,
            uint256 shares

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L49

```solidity
File: contracts/PanopticFactory.sol

 34:     event OwnershipTransferred(address indexed oldOwner, address indexed newOwner);

 43:     event PoolDeployed(
            PanopticPool indexed poolAddress,
            IUniswapV3Pool indexed uniswapPool,
            CollateralTracker collateralTracker0,
            CollateralTracker collateralTracker1,
            uint256 amount0,
            uint256 amount1

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L34

```solidity
File: contracts/PanopticPool.sol

 62:     event PremiumSettled(
            address indexed user,
            TokenId indexed tokenId,
            LeftRightSigned settledAmounts

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L62

```solidity
File: contracts/SemiFungiblePositionManager.sol

 80:     event PoolInitialized(address indexed uniswapPool, uint64 poolId);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L80

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 22:     event TransferSingle(
            address indexed operator,
            address indexed from,
            address indexed to,
            uint256 id,
            uint256 amount

 36:     event TransferBatch(
            address indexed operator,
            address indexed from,
            address indexed to,
            uint256[] ids,
            uint256[] amounts

 48:     event ApprovalForAll(address indexed owner, address indexed operator, bool approved);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L22

```solidity
File: contracts/tokens/ERC20Minimal.sol

 18:     event Transfer(address indexed from, address indexed to, uint256 amount);

 24:     event Approval(address indexed owner, address indexed spender, uint256 amount);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L24


## [NC-55] NatSpec: Function declarations should have` @notice` tags
`@notice` is used to explain to end users what the function does, and the compiler interprets `///` or `/**` comments as this tag if one wasn’t explicitly provided

**Total Instances:** 6

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

 323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

 341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

 741:     function _poolUtilization() internal view returns (int256 poolUtilization) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L178

```solidity
File: contracts/SemiFungiblePositionManager.sol

 680:     function _validateAndForwardToAMM(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool isBurn
         ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L680

```solidity
File: contracts/types/TokenId.sol

 464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L464


## [NC-56] NatSpec: Function declarations should have descriptions
Function declarations should have descriptions.

**Total Instances:** 3

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L178

```solidity
File: contracts/SemiFungiblePositionManager.sol

 680:     function _validateAndForwardToAMM(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool isBurn
         ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L680

```solidity
File: contracts/types/TokenId.sol

 464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L464


## [NC-57] NatSpec: Modifier declarations should have `@dev` tag
Modifier declarations should have `@dev` tag.

**Total Instances:** 1

```solidity
File: contracts/CollateralTracker.sol

 169:     modifier onlyPanopticPool() {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L169


## [NC-58] NatSpec: state variable declarations should have descriptions
e.g. `@notice` for public state variables, and `@dev` for [non-public](https://docs.soliditylang.org/en/latest/natspec-format.html#tags) ones

**Total Instances:** 11

```solidity
File: contracts/PanopticPool.sol

 120:     bool internal constant DONOT_COMMIT_LONG_SETTLED = false;

 133:     bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;

 136:     uint256 internal constant MEDIAN_PERIOD = 60;

 156:     int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;

 160:     int256 internal constant MAX_SLOW_FAST_DELTA = 1800;

 171:     uint256 internal constant BP_DECREASE_BUFFER = 13_333;

 174:     uint256 internal constant NO_BUFFER = 10_000;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L120

```solidity
File: contracts/SemiFungiblePositionManager.sol

 126:     bool internal constant BURN = true;

 133:     uint128 private constant VEGOID = 2;

 287:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

 289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L289


## [NC-59] No equate comparison checks between to and from address parameters
'The function lacks a standard check: it does not validate if the `to` and `from` addresses are identical. This omission can lead to unintended outcomes if the same address is used in both parameters. To rectify this, we recommend implementing a comparison check at the beginning of the function. In the context of Solidity, the command `require(to != from, 'To and From addresses can't be the same')`; could be utilized. This addition will generate an error if the `to` and `from` addresses are the same, thereby fortifying the function's robustness and security.'

**Total Instances:** 9

```solidity
File: contracts/CollateralTracker.sol

 341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L341

```solidity
File: contracts/SemiFungiblePositionManager.sol

 540:     function safeTransferFrom(
             address from,
             address to,
             uint256 id,
             uint256 amount,
             bytes calldata data
         ) public override {

 566:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public override {

 593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L540

```solidity
File: contracts/libraries/SafeTransferLib.sol

 21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L21

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 94:     function safeTransferFrom(
            address from,
            address to,
            uint256 id,
            uint256 amount,
            bytes calldata data
        ) public virtual {

 130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L94

```solidity
File: contracts/tokens/ERC20Minimal.sol

 81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

 103:     function _transferFrom(address from, address to, uint256 amount) internal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L103


## [NC-60] Non-library/interface files should use fixed compiler versions, not floating ones
Note that some file names may indicate an interface, but actually contain abstract contracts

**Total Instances:** 7

```solidity
File: contracts/CollateralTracker.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L2

```solidity
File: contracts/PanopticFactory.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L2

```solidity
File: contracts/PanopticPool.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L2

```solidity
File: contracts/SemiFungiblePositionManager.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L2

```solidity
File: contracts/multicall/Multicall.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L2

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L2

```solidity
File: contracts/tokens/ERC20Minimal.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L2


## [NC-61] Not using the named return variables anywhere in the function is confusing
Consider changing the variable to be an unnamed one, since the variable is never assigned, nor is it returned by name. If the optimizer is not turned on, leaving the code as it is will also waste gas for the stack variable.

**Total Instances:** 25

```solidity
File: contracts/CollateralTracker.sol

 361:     function asset() external view returns (address assetTokenAddress) {

 370:     function totalAssets() public view returns (uint256 totalManagedAssets) {

 379:     function convertToShares(uint256 assets) public view returns (uint256 shares) {

 386:     function convertToAssets(uint256 shares) public view returns (uint256 assets) {

 392:     function maxDeposit(address) external pure returns (uint256 maxAssets) {

 444:     function maxMint(address) external view returns (uint256 maxShares) {

 507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {

 518:     function previewWithdraw(uint256 assets) public view returns (uint256 shares) {

 572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {

 581:     function previewRedeem(uint256 shares) public view returns (uint256 assets) {

 741:     function _poolUtilization() internal view returns (int256 poolUtilization) {

 751:     function _sellCollateralRatio(
             int256 utilization
         ) internal view returns (uint256 sellCollateralRatio) {

 806:     function _buyCollateralRatio(
             uint256 utilization
         ) internal view returns (uint256 buyCollateralRatio) {

 1278:     function _getRequiredCollateralSingleLeg(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 required) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L361

```solidity
File: contracts/PanopticPool.sol

 381:     function calculateAccumulatedFeesBatch(
             address user,
             bool includePendingPremium,
             TokenId[] calldata positionIdList
         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

 410:     function calculatePortfolioValue(
             address user,
             int24 atTick,
             TokenId[] calldata positionIdList
         ) external view returns (int256 value0, int256 value1) {

 826:     function _burnOptions(
             bool commitLongSettled,
             TokenId tokenId,
             address owner,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

 887:     function _validateSolvency(
             address user,
             TokenId[] calldata positionIdList,
             uint256 buffer
         ) internal view returns (uint256 medianData) {

 1431:     function collateralToken0() external view returns (CollateralTracker collateralToken) {

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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L381

```solidity
File: contracts/SemiFungiblePositionManager.sol

 471:     function burnTokenizedPosition(
             TokenId tokenId,
             uint128 positionSize,
             int24 slippageTickLimitLow,
             int24 slippageTickLimitHigh
         )
             external
             ReentrancyLock(tokenId.poolId())
             returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)

 504:     function mintTokenizedPosition(
             TokenId tokenId,
             uint128 positionSize,
             int24 slippageTickLimitLow,
             int24 slippageTickLimitHigh
         )
             external
             ReentrancyLock(tokenId.poolId())
             returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)

 1555:     function getUniswapV3PoolFromId(
              uint64 poolId
          ) external view returns (IUniswapV3Pool UniswapV3Pool) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L471

```solidity
File: contracts/libraries/Math.sol

 738:     function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L738

```solidity
File: contracts/types/TokenId.sol

 416:     function asTicks(
             TokenId self,
             uint256 legIndex
         ) internal pure returns (int24 legLowerTick, int24 legUpperTick) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L416


## [NC-62] Overflows in unchecked blocks
While integers with a large number of bits are unlikely to overflow on human time scales, it is not strictly correct to use an `unchecked` block around them, because eventually they will overflow, and `unchecked` blocks are meant for cases where it’s mathematically impossible for an operation to trigger an overflow (e.g. a prior `require()` statement prevents the overflow case)

**Total Instances:** 36

```solidity
File: contracts/CollateralTracker.sol

 661:         unchecked {
                 for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

 1230:             unchecked {
                      ++i;

 1254:         unchecked {
                  for (uint256 index = 0; index < numLegs; ++index) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L661

```solidity
File: contracts/PanopticPool.sol

 482:                 unchecked {
                         ++leg;

 487:             unchecked {
                     ++k;

 778:             unchecked {
                     ++leg;

 812:             unchecked {
                     ++i;

 871:             unchecked {
                     ++leg;

 1388:             unchecked {
                      ++i;

 1571:             unchecked {
                      ++leg;

 1976:             unchecked {
                      ++leg;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L482

```solidity
File: contracts/SemiFungiblePositionManager.sol

 578:             unchecked {
                     ++i;

 649:             unchecked {
                     ++leg;

 931:             unchecked {
                     ++leg;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L578

```solidity
File: contracts/libraries/FeesCalc.sol

 79:                 unchecked {
                        ++leg;

 83:             unchecked {
                    ++k;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L79

```solidity
File: contracts/libraries/Math.sol

 754:         unchecked {
                 int256 i = left;
                 int256 j = right;
                 if (i == j) return;
                 int256 pivot = arr[uint256(left + (right - left) / 2)];
                 while (i < j) {
                     while (arr[uint256(i)] < pivot) i++;

 754:         unchecked {
                 int256 i = left;
                 int256 j = right;
                 if (i == j) return;
                 int256 pivot = arr[uint256(left + (right - left) / 2)];
                 while (i < j) {
                     while (arr[uint256(i)] < pivot) i++;
                     while (pivot < arr[uint256(j)]) j--;

 754:         unchecked {
                 int256 i = left;
                 int256 j = right;
                 if (i == j) return;
                 int256 pivot = arr[uint256(left + (right - left) / 2)];
                 while (i < j) {
                     while (arr[uint256(i)] < pivot) i++;
                     while (pivot < arr[uint256(j)]) j--;
                     if (i <= j) {
                         (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);
                         i++;

 754:         unchecked {
                 int256 i = left;
                 int256 j = right;
                 if (i == j) return;
                 int256 pivot = arr[uint256(left + (right - left) / 2)];
                 while (i < j) {
                     while (arr[uint256(i)] < pivot) i++;
                     while (pivot < arr[uint256(j)]) j--;
                     if (i <= j) {
                         (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);
                         i++;
                         j--;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L754

```solidity
File: contracts/libraries/PanopticMath.sol

 132:         unchecked {
                 int256[] memory tickCumulatives = new int256[](cardinality + 1);
     
                 uint256[] memory timestamps = new uint256[](cardinality + 1);
                 // get the last 4 timestamps/tickCumulatives (if observationIndex < cardinality, the index will wrap back from observationCardinality)
                 for (uint256 i = 0; i < cardinality + 1; ++i) {

 132:         unchecked {
                 int256[] memory tickCumulatives = new int256[](cardinality + 1);
     
                 uint256[] memory timestamps = new uint256[](cardinality + 1);
                 // get the last 4 timestamps/tickCumulatives (if observationIndex < cardinality, the index will wrap back from observationCardinality)
                 for (uint256 i = 0; i < cardinality + 1; ++i) {
                     (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
                         uint256(
                             (int256(observationIndex) - int256(i * period)) +
                                 int256(observationCardinality)
                         ) % observationCardinality
                     );
                 }
     
                 int256[] memory ticks = new int256[](cardinality);
                 // use cardinality periods given by cardinality + 1 accumulator observations to compute the last cardinality observed ticks spaced by period
                 for (uint256 i = 0; i < cardinality; ++i) {

 175:         unchecked {
                 // return the average of the rank 3 and 4 values
                 medianTick =
                     (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
                         int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
                     2;
     
                 // only proceed if last entry is at least MEDIAN_PERIOD seconds old
                 if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {
                     int24 lastObservedTick;
                     {
                         (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(
                             uint256(
                                 int256(observationIndex) - int256(1) + int256(observationCardinality)
                             ) % observationCardinality
                         );
     
                         (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool
                             .observations(observationIndex);
                         lastObservedTick = int24(
                             (tickCumulative_last - tickCumulative_old) /
                                 int256(timestamp_last - timestamp_old)
                         );
                     }
     
                     uint24 orderMap = uint24(medianData >> 192);
     
                     uint24 newOrderMap;
                     uint24 shift = 1;
                     bool below = true;
                     uint24 rank;
                     int24 entry;
                     for (uint8 i; i < 8; ++i) {

 246:         unchecked {
                 // construct the time stots
                 for (uint256 i = 0; i < 20; ++i) {

 246:         unchecked {
                 // construct the time stots
                 for (uint256 i = 0; i < 20; ++i) {
                     secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);
                 }
     
                 // observe the tickCumulative at the 20 pre-defined time slots
                 (int56[] memory tickCumulatives, ) = univ3pool.observe(secondsAgos);
     
                 // compute the average tick per 30s window
                 for (uint256 i = 0; i < 19; ++i) {

 406:             unchecked {
                     ++leg;

 778:         unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;
                 for (uint256 i = 0; i < positionIdList.length; ++i) {

 778:         unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;
                 for (uint256 i = 0; i < positionIdList.length; ++i) {
                     TokenId tokenId = positionIdList[i];
                     uint256 numLegs = tokenId.countLegs();
                     for (uint256 leg = 0; leg < numLegs; ++leg) {
                         if (tokenId.isLong(leg) == 1) {
                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
                         }
                     }
                 }
                 // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token
                 int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);
                 int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);
                 int256 haircut0;
                 int256 haircut1;
                 // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,
                 // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token
                 if (
                     longPremium.rightSlot() < collateralDelta0 &&
                     longPremium.leftSlot() > collateralDelta1
                 ) {
                     int256 protocolLoss1 = collateralDelta1;
                     (collateralDelta0, collateralDelta1) = (
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
                     );
     
                     haircut0 = longPremium.rightSlot();
                     haircut1 = protocolLoss1 + collateralDelta1;
                 } else if (
                     longPremium.leftSlot() < collateralDelta1 &&
                     longPremium.rightSlot() > collateralDelta0
                 ) {
                     int256 protocolLoss0 = collateralDelta0;
                     (collateralDelta0, collateralDelta1) = (
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
                     );
     
                     haircut0 = collateralDelta0 + protocolLoss0;
                     haircut1 = longPremium.leftSlot();
                 } else {
                     // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
                     haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
                     haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
     
                     collateralDelta0 = 0;
                     collateralDelta1 = 0;
                 }
     
                 {
                     address _liquidatee = liquidatee;
                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
                 }
     
                 for (uint256 i = 0; i < positionIdList.length; i++) {

 778:         unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;
                 for (uint256 i = 0; i < positionIdList.length; ++i) {
                     TokenId tokenId = positionIdList[i];
                     uint256 numLegs = tokenId.countLegs();
                     for (uint256 leg = 0; leg < numLegs; ++leg) {

 778:         unchecked {
                 // get the amount of premium paid by the liquidatee
                 LeftRightSigned longPremium;
                 for (uint256 i = 0; i < positionIdList.length; ++i) {
                     TokenId tokenId = positionIdList[i];
                     uint256 numLegs = tokenId.countLegs();
                     for (uint256 leg = 0; leg < numLegs; ++leg) {
                         if (tokenId.isLong(leg) == 1) {
                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
                         }
                     }
                 }
                 // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token
                 int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);
                 int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);
                 int256 haircut0;
                 int256 haircut1;
                 // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,
                 // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token
                 if (
                     longPremium.rightSlot() < collateralDelta0 &&
                     longPremium.leftSlot() > collateralDelta1
                 ) {
                     int256 protocolLoss1 = collateralDelta1;
                     (collateralDelta0, collateralDelta1) = (
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
                     );
     
                     haircut0 = longPremium.rightSlot();
                     haircut1 = protocolLoss1 + collateralDelta1;
                 } else if (
                     longPremium.leftSlot() < collateralDelta1 &&
                     longPremium.rightSlot() > collateralDelta0
                 ) {
                     int256 protocolLoss0 = collateralDelta0;
                     (collateralDelta0, collateralDelta1) = (
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
                     );
     
                     haircut0 = collateralDelta0 + protocolLoss0;
                     haircut1 = longPremium.leftSlot();
                 } else {
                     // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
                     haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
                     haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
     
                     collateralDelta0 = 0;
                     collateralDelta1 = 0;
                 }
     
                 {
                     address _liquidatee = liquidatee;
                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
                 }
     
                 for (uint256 i = 0; i < positionIdList.length; i++) {
                     TokenId tokenId = positionIdList[i];
                     LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L132

```solidity
File: contracts/multicall/Multicall.sol

 32:             unchecked {
                    ++i;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L32

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 156:             unchecked {
                     ++i;

 186:         unchecked {
                 for (uint256 i = 0; i < owners.length; ++i) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L156

```solidity
File: contracts/types/TokenId.sol

 504:         unchecked {
                 // extract strike, width, and tokenType
                 uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;
                 for (uint256 i = 0; i < 4; ++i) {

 504:         unchecked {
                 // extract strike, width, and tokenType
                 uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;
                 for (uint256 i = 0; i < 4; ++i) {
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

 579:         unchecked {
                 uint256 numLegs = self.countLegs();
                 for (uint256 i = 0; i < numLegs; ++i) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L579


## [NC-63] Polymorphic functions make security audits more time-consuming and error-prone
The instances below point to one of two functions with the same name. Consider naming each function differently, in order to make code navigation and analysis easier.

**Total Instances:** 15

```solidity
File: contracts/CollateralTracker.sol

 894:     function delegate(address delegatee, uint256 assets) external onlyPanopticPool {

 975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L894

```solidity
File: contracts/PanopticPool.sol

 586:     function burnOptions(
             TokenId[] calldata positionIdList,
             TokenId[] calldata newPositionIdList,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) external {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L586

```solidity
File: contracts/libraries/Math.sol

 49:     function min(int256 a, int256 b) internal pure returns (int256) {

 65:     function max(int256 a, int256 b) internal pure returns (int256) {

 318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L49

```solidity
File: contracts/libraries/PanopticMath.sol

 445:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             int24 tick
         ) internal pure returns (uint256, uint256) {

 524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

 547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L445

```solidity
File: contracts/types/LeftRight.sol

 46:     function rightSlot(LeftRightSigned self) internal pure returns (int128) {

 78:     function toRightSlot(
            LeftRightSigned self,
            int128 right
        ) internal pure returns (LeftRightSigned) {

 108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

 134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

 194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

 232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L232


## [NC-64] Functions not used internally could be marked external
When the function is not used internally marking function as 'external' designates it for external access, enhancing clarity and security for interactions with other contracts and external accounts.

**Total Instances:** 13

```solidity
File: contracts/CollateralTracker.sol

 323:     function transfer(

 341:     function transferFrom(

 1141:     function getAccountMarginDetails(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L323

```solidity
File: contracts/PanopticFactory.sol

 134:     function initialize(address _owner) public {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134

```solidity
File: contracts/PanopticPool.sol

 1444:     function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1444

```solidity
File: contracts/SemiFungiblePositionManager.sol

 540:     function safeTransferFrom(

 566:     function safeBatchTransferFrom(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L540

```solidity
File: contracts/libraries/FeesCalc.sol

 97:     function calculateAMMSwapFees(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L97

```solidity
File: contracts/multicall/Multicall.sol

 12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L12

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 81:     function setApprovalForAll(address operator, bool approved) public {

 178:     function balanceOfBatch(

 200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L81

```solidity
File: contracts/tokens/ERC20Minimal.sol

 49:     function approve(address spender, uint256 amount) public returns (bool) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L49


## [NC-65] `pure` function accesses storage
While the compiler currently flags functions like these as being pure, this is a [bug](https://github.com/ethereum/solidity/issues/11573) which will be fixed in a future version, so it’s best to not use pure visibility, in order to not break when this bug is fixed.

**Total Instances:** 11

```solidity
File: contracts/PanopticPool.sol

 499:     function _getSlippageLimits(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L499

```solidity
File: contracts/SemiFungiblePositionManager.sol

 1321:     function _getPremiaDeltas(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1321

```solidity
File: contracts/libraries/PanopticMath.sol

 59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L59

```solidity
File: contracts/types/LeftRight.sol

 59:     function toRightSlot(

 78:     function toRightSlot(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L59

```solidity
File: contracts/types/LiquidityChunk.sol

 135:     function updateTickLower(

 151:     function updateTickUpper(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L135

```solidity
File: contracts/types/TokenId.sol

 291:     function addStrike(

 366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

 432:     function countLegs(TokenId self) internal pure returns (uint256) {

 500:     function validate(TokenId self) internal pure {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L500


## [NC-66] Duplicated require()/revert() checks should be refactored to a modifier or function.
In Solidity, duplicated require() or revert() checks should be consolidated into modifiers or separate functions to enhance code clarity, reduce redundancy, and simplify maintenance.

**Total Instances:** 19

```solidity
File: contracts/CollateralTracker.sol

 350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

 480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L350

```solidity
File: contracts/PanopticFactory.sol

 224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L224

```solidity
File: contracts/PanopticPool.sol

 1163:         ) revert Errors.NotEnoughCollateral();

 1394:         if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1163

```solidity
File: contracts/SemiFungiblePositionManager.sol

 549:         if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

 639:                 revert Errors.TransferFailed();

 702:         if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L549

```solidity
File: contracts/libraries/Math.sol

 312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

 588:                 require(result < type(uint256).max);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L312

```solidity
File: contracts/libraries/SafeTransferLib.sol

 75:         if (!success) revert Errors.TransferFailed();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L75

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

 168:                 revert UnsafeRecipient();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L137

```solidity
File: contracts/types/LeftRight.sol

 186:             ) revert Errors.UnderOverFlow();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L186

```solidity
File: contracts/types/TokenId.sol

 513:                         revert Errors.InvalidTokenIdParameter(1);

 548:                     ) revert Errors.InvalidTokenIdParameter(3);

 561:                         revert Errors.InvalidTokenIdParameter(4);

 567:                         revert Errors.InvalidTokenIdParameter(5);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L567


## [NC-67] Return values of `approve()` not checked
Not all IERC20 implementations `revert()` when there's a failure in `approve()`. The function signature has a boolean return value and they indicate errors that way instead. By not checking the return value, operations that should have marked as failed, may potentially go through without actually approving anything

**Total Instances:** 2

```solidity
File: contracts/libraries/InteractionHelper.sol

 33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

 37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L37


## [NC-68] Revert statements within external and public functions can be used to perform DOS attacks
'In Solidity, 'revert' statements are used to undo changes and throw an exception when certain conditions are not met. However, in public and external functions, improper use of revert can be exploited for Denial of Service (DoS) attacks. An attacker can intentionally trigger these `revert` conditions, causing legitimate transactions to consistently fail. For example, if a function relies on specific conditions from user input or contract state, an attacker could manipulate these to continually force reverts, blocking the function's execution. Therefore, it's crucial to design contract logic to handle exceptions properly and avoid scenarios where `revert` can be predictably triggered by malicious actors. This includes careful input validation and considering alternative design patterns that are less susceptible to such abuses.'

**Total Instances:** 19

```solidity
File: contracts/CollateralTracker.sol

 221:     function startToken(
             bool underlyingIsToken0,
             address token0,
             address token1,
             uint24 fee,
             PanopticPool panopticPool
         ) external {
             // fails if already initialized
             if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();

 323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions
             // if they do: we don't want them sending panoptic pool shares to others
             // since that's like reducing collateral
     
             if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

 341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {
             // make sure the caller does not have any open option positions
             // if they do: we don't want them sending panoptic pool shares to others
             // as this would reduce their amount of collateral against the opened positions
     
             if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

 417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
             if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {
             assets = previewMint(shares);
     
             if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 531:     function withdraw(
             uint256 assets,
             address receiver,
             address owner
         ) external returns (uint256 shares) {
             if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

 591:     function redeem(
             uint256 shares,
             address receiver,
             address owner
         ) external returns (uint256 assets) {
             if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L221

```solidity
File: contracts/PanopticFactory.sol

 147:     function transferOwnership(address newOwner) external {
             address currentOwner = s_owner;
     
             if (msg.sender != currentOwner) revert Errors.NotOwner();

 210:     function deployNewPool(
             address token0,
             address token1,
             uint24 fee,
             bytes32 salt
         ) external returns (PanopticPool newPoolContract) {
             // sort the tokens, if necessary:
             (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);
     
             // frontrunning protection for mined pool addresses
             if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();
     
             // restrict pool deployment to owner if contract has not been made permissionless
             address _owner = s_owner;
             if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();
     
             IUniswapV3Pool v3Pool = IUniswapV3Pool(UNIV3_FACTORY.getPool(token0, token1, fee));
             if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();
     
             if (address(s_getPanopticPool[v3Pool]) != address(0))
                 revert Errors.PoolAlreadyInitialized();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L147

```solidity
File: contracts/PanopticPool.sol

 291:     function startPool(
             IUniswapV3Pool _univ3pool,
             address token0,
             address token1,
             CollateralTracker collateralTracker0,
             CollateralTracker collateralTracker1
         ) external {
             // reverts if the Uniswap pool has already been initialized
             if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

 338:     function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {
             (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();
     
             if (currentSqrtPriceX96 <= sqrtLowerBound || currentSqrtPriceX96 >= sqrtUpperBound) {
                 revert Errors.PriceBoundFail();

 1017:     function liquidate(
              TokenId[] calldata positionIdListLiquidator,
              address liquidatee,
              LeftRightUnsigned delegations,
              TokenId[] calldata positionIdList
          ) external {
              _validatePositionList(liquidatee, positionIdList, 0);
      
              // Assert the account we are liquidating is actually insolvent
              int24 twapTick = getUniV3TWAP();
      
              LeftRightUnsigned tokenData0;
              LeftRightUnsigned tokenData1;
              LeftRightSigned premia;
              {
                  (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
      
                  // Enforce maximum delta between TWAP and currentTick to prevent extreme price manipulation
                  if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)
                      revert Errors.StaleTWAP();
      
                  uint256[2][] memory positionBalanceArray = new uint256[2][](positionIdList.length);
                  (premia, positionBalanceArray) = _calculateAccumulatedPremia(
                      liquidatee,
                      positionIdList,
                      COMPUTE_ALL_PREMIA,
                      ONLY_AVAILABLE_PREMIUM,
                      currentTick
                  );
                  tokenData0 = s_collateralToken0.getAccountMarginDetails(
                      liquidatee,
                      twapTick,
                      positionBalanceArray,
                      premia.rightSlot()
                  );
      
                  tokenData1 = s_collateralToken1.getAccountMarginDetails(
                      liquidatee,
                      twapTick,
                      positionBalanceArray,
                      premia.leftSlot()
                  );
      
                  (uint256 balanceCross, uint256 thresholdCross) = _getSolvencyBalances(
                      tokenData0,
                      tokenData1,
                      Math.getSqrtRatioAtTick(twapTick)
                  );
      
                  if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();

 1179:     function forceExercise(
              address account,
              TokenId[] calldata touchedId,
              TokenId[] calldata positionIdListExercisee,
              TokenId[] calldata positionIdListExercisor
          ) external {
              // revert if multiple positions are specified
              // the reason why the singular touchedId is an array is so it composes well with the rest of the system
              // '_calculateAccumulatedPremia' expects a list of positions to be touched, and this is the only way to pass a single position
              if (touchedId.length != 1) revert Errors.InputListFail();

 1587:     function settleLongPremium(
              TokenId[] calldata positionIdList,
              address owner,
              uint256 legIndex
          ) external {
              _validatePositionList(owner, positionIdList, 0);
      
              TokenId tokenId = positionIdList[positionIdList.length - 1];
      
              if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L291

```solidity
File: contracts/SemiFungiblePositionManager.sol

 350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {
             // compute the address of the Uniswap v3 pool for the given token0, token1, and fee tier
             address univ3pool = FACTORY.getPool(token0, token1, fee);
     
             // reverts if the Uni v3 pool has not been initialized
             if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

 540:     function safeTransferFrom(
             address from,
             address to,
             uint256 id,
             uint256 amount,
             bytes calldata data
         ) public override {
             // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
             // so just check if there is an active reentrancy lock for the relevant pool on the token we're transferring
             if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

 566:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public override {
             // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
             // so just check if there is an active reentrancy lock for the relevant pool on each token
             for (uint256 i = 0; i < ids.length; ) {
                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350

```solidity
File: contracts/tokens/ERC1155Minimal.sol

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
    
            if (to.code.length != 0) {
                if (
                    ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=
                    ERC1155Holder.onERC1155Received.selector
                ) {
                    revert UnsafeRecipient();

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
     
             if (to.code.length != 0) {
                 if (
                     ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
                     ERC1155Holder.onERC1155BatchReceived.selector
                 ) {
                     revert UnsafeRecipient();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L130


## [NC-69] Style guide: Function names should use lowerCamelCase
According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#function-names) function names should be in `mixedCase` (lowerCamelCase)

**Total Instances:** 11

```solidity
File: contracts/PanopticPool.sol

 677:     function _mintInSFPMAndUpdateCollateral(

 1450:     function getUniV3TWAP() internal view returns (int24 twapTick) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L677

```solidity
File: contracts/SemiFungiblePositionManager.sol

 350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

 680:     function _validateAndForwardToAMM(

 756:     function swapInAMM(

 863:     function _createPositionInAMM(

 958:     function _createLegInAMM(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350

```solidity
File: contracts/libraries/FeesCalc.sol

 97:     function calculateAMMSwapFees(

 130:     function _getAMMSwapFeesPerLiquidityCollected(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L97

```solidity
File: contracts/libraries/PanopticMath.sol

 607:     function _calculateIOAmounts(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L607

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 13:     function issueNFT(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L13


## [NC-70] Style guide: State and local variables should be named using lowerCamelCase
The Solidity style guide [says](https://docs.soliditylang.org/en/latest/style-guide.html#local-and-state-variable-names) to use mixedCase for local and state variable names. Note that while OpenZeppelin may not follow this advice, it still is the recommended way of naming variables.

**Total Instances:** 54

```solidity
File: contracts/CollateralTracker.sol

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

 185:         uint256 _ITMSpreadMultiplier

 280:         returns (uint256 poolAssets, uint256 insideAMM, int256 currentPoolUtilization)

 773:         uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L89

```solidity
File: contracts/PanopticFactory.sol

 96:     address internal s_owner;

 99:     bool internal s_initialized;

 102:     mapping(IUniswapV3Pool univ3pool => PanopticPool panopticPool) internal s_getPanopticPool;

 116:         address _WETH9,

 117:         SemiFungiblePositionManager _SFPM,

 119:         IDonorNFT _donorNFT,

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L96

```solidity
File: contracts/PanopticPool.sol

 186:     IUniswapV3Pool internal s_univ3pool;

 225:     uint256 internal s_miniMedian;

 231:     CollateralTracker internal s_collateralToken0;

 233:     CollateralTracker internal s_collateralToken1;

 238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

 245:     mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

 251:     mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;

 258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))

 272:     mapping(address account => uint256 positionsHash) internal s_positionsHash;

 439:         address c_user = user;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L186

```solidity
File: contracts/SemiFungiblePositionManager.sol

 145:     mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;

 150:     mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;

 177:     mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)

 287:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;

 289:     mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;

 295:     mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;

 611:             bytes32 positionKey_from = keccak256(

 620:             bytes32 positionKey_to = keccak256(

 1342:             uint256 premium0X64_base;

 1343:             uint256 premium1X64_base;

 1363:                 uint128 premium0X64_owed;

 1364:                 uint128 premium1X64_owed;

 1384:                 uint128 premium0X64_gross;

 1385:                 uint128 premium1X64_gross;

 1557:     ) external view returns (IUniswapV3Pool UniswapV3Pool) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L145

```solidity
File: contracts/libraries/PanopticMath.sol

 186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

 186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(

 192:                     (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool

 192:                     (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L186

```solidity
File: contracts/types/LeftRight.sol

 285:         uint128 z_xR = (uint256(x.rightSlot()) + dx.rightSlot()).toUint128Capped();

 286:         uint128 z_xL = (uint256(x.leftSlot()) + dx.leftSlot()).toUint128Capped();

 287:         uint128 z_yR = (uint256(y.rightSlot()) + dy.rightSlot()).toUint128Capped();

 288:         uint128 z_yL = (uint256(y.leftSlot()) + dy.leftSlot()).toUint128Capped();

 290:         bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);

 291:         bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L291


## [NC-71] Style guide: Top level pragma declarations should be separated by two blank lines
Top level pragma declarations should be separated by two blank lines.

**Total Instances:** 20

```solidity
File: contracts/CollateralTracker.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L2

```solidity
File: contracts/PanopticFactory.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L2

```solidity
File: contracts/PanopticPool.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L2

```solidity
File: contracts/SemiFungiblePositionManager.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L2

```solidity
File: contracts/libraries/CallbackLib.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L2

```solidity
File: contracts/libraries/Constants.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L2

```solidity
File: contracts/libraries/Errors.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L2

```solidity
File: contracts/libraries/FeesCalc.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L2

```solidity
File: contracts/libraries/InteractionHelper.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L2

```solidity
File: contracts/libraries/Math.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L2

```solidity
File: contracts/libraries/PanopticMath.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L2

```solidity
File: contracts/libraries/SafeTransferLib.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L2

```solidity
File: contracts/multicall/Multicall.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L2

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L2

```solidity
File: contracts/tokens/ERC20Minimal.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L2

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L2

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L2

```solidity
File: contracts/types/LeftRight.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L2

```solidity
File: contracts/types/LiquidityChunk.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L2

```solidity
File: contracts/types/TokenId.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L2


## [NC-72] Unused function parameter
Comment out the variable name to suppress compiler warnings.

**Total Instances:** 12

```solidity
File: contracts/libraries/Math.sol

 /// @audit  a, b
 340:     function mulDiv(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {

 /// @audit  a, b
 458:     function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

 /// @audit  a, b
 521:     function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

 /// @audit  a, b
 598:     function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

 /// @audit  a, b
 675:     function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

 /// @audit  a, b
 738:     function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L340

```solidity
File: contracts/libraries/SafeTransferLib.sol

 /// @audit  token, from, to, amount
 21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

 /// @audit  token, to, amount
 52:     function safeTransfer(address token, address to, uint256 amount) internal {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L21

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 /// @audit  deployer, newPoolContract, token0, token1, fee
 13:     function issueNFT(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L13

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

 /// @audit  account
 16:     function balanceOf(address account) external view returns (uint256);

 /// @audit  spender, amount
 22:     function approve(address spender, uint256 amount) external;

 /// @audit  to, amount
 27:     function transfer(address to, uint256 amount) external;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L27


## [NC-73] Unused import
The identifier is imported but never used within the file.

**Total Instances:** 1

```solidity
File: contracts/types/LiquidityChunk.sol

 /// @audit  TokenId
 5: import {TokenId} from "@types/TokenId.sol";

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L5


## [NC-74] Unused structs
Note that there may be cases where a struct superficially appears to be used, but this is only because there are multiple definitions of the struct in different files. In such cases, the struct definition should be moved into a separate file. The instances below are the unused definitions.

**Total Instances:** 1

```solidity
File: contracts/libraries/CallbackLib.sol

 21:     struct CallbackData {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L21


## [NC-75] Unusual loop variable
The normal name for loop variables is `i`, and when there is a nested loop, to use `j`. Not following this convention may lead to some reviewer confusion.

**Total Instances:** 15

```solidity
File: contracts/CollateralTracker.sol

 662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L662

```solidity
File: contracts/PanopticPool.sol

 441:         for (uint256 k = 0; k < pLength; ) {

 459:             for (uint256 leg = 0; leg < numLegs; ) {

 745:         for (uint256 leg = 0; leg < numLegs; ) {

 864:         for (uint256 leg = 0; leg < numLegs; ) {

 1518:         for (uint256 leg = 0; leg < numLegs; ) {

 1672:         for (uint256 leg = 0; leg < numLegs; ++leg) {

 1852:         for (uint256 leg = 0; leg < numLegs; ) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L441

```solidity
File: contracts/SemiFungiblePositionManager.sol

 601:         for (uint256 leg = 0; leg < numLegs; ) {

 882:         for (uint256 leg = 0; leg < numLegs; ) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L601

```solidity
File: contracts/libraries/FeesCalc.sol

 51:         for (uint256 k = 0; k < positionIdList.length; ) {

 55:             for (uint256 leg = 0; leg < numLegs; ) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L51

```solidity
File: contracts/libraries/PanopticMath.sol

 395:         for (uint256 leg = 0; leg < numLegs; ) {

 784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {

 863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L863


## [NC-76] Use bit shifts in an immutable variable rather than long bit masks of a single bit, for readability
Enhance readability by employing bit shifts in immutable variables instead of long bit masks of a single bit.

**Total Instances:** 9

```solidity
File: contracts/PanopticPool.sol

 312:                 (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L312

```solidity
File: contracts/libraries/Constants.sol

 9:     uint256 internal constant FP96 = 0x1000000000000000000000000;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L9

```solidity
File: contracts/libraries/Math.sol

 93:             if (x >= 0x100000000000000000000000000000000) {

 97:             if (x >= 0x10000000000000000) {

 101:             if (x >= 0x100000000) {

 135:                 : 0x100000000000000000000000000000000;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L93

```solidity
File: contracts/libraries/PanopticMath.sol

 26:     uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L26

```solidity
File: contracts/types/LeftRight.sol

 23:         0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000;

 27:         int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L27


## [NC-77] Use bytes.concat() on bytes instead of abi.encodePacked() for clearer semantic meaning
Starting with version 0.8.4, Solidity has the `bytes.concat()` function, which allows one to concatenate a list of bytes/strings, without extra padding. Using this function rather than `abi.encodePacked()` makes the intended operation more clear, leading to less reviewer confusion.

**Total Instances:** 12

```solidity
File: contracts/PanopticPool.sol

 462:                         abi.encodePacked(

 1643:                 abi.encodePacked(

 1674:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

 1856:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L462

```solidity
File: contracts/SemiFungiblePositionManager.sol

 612:                 abi.encodePacked(

 621:                 abi.encodePacked(

 975:             abi.encodePacked(

 1151:                     abi.encodePacked(

 1431:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

 1459:             abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)

 1544:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L612

```solidity
File: contracts/libraries/PanopticMath.sol

 879:                             abi.encodePacked(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L879


## [NC-78] Use `@inheritdoc` for overridden functions
It is recommended to use `@inheritdoc` for overridden functions.

**Total Instances:** 4

```solidity
File: contracts/CollateralTracker.sol

 323:     function transfer(

 341:     function transferFrom(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L323

```solidity
File: contracts/SemiFungiblePositionManager.sol

 540:     function safeTransferFrom(

 566:     function safeBatchTransferFrom(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L566


## [NC-79] Use the latest solidity (prior to 0.8.20 if on L2s) for deployment.
When deploying contracts, you should use the latest released version of Solidity. Apart from exceptional cases, only the latest version receives security fixes. Since deployed contracts should not use floating pragmas, I’ve flagged all instances where a version prior to 0.8.19 is allowed by the version pragma.

**Total Instances:** 20

```solidity
File: contracts/CollateralTracker.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L2

```solidity
File: contracts/PanopticFactory.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L2

```solidity
File: contracts/PanopticPool.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L2

```solidity
File: contracts/SemiFungiblePositionManager.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L2

```solidity
File: contracts/libraries/CallbackLib.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L2

```solidity
File: contracts/libraries/Constants.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L2

```solidity
File: contracts/libraries/Errors.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L2

```solidity
File: contracts/libraries/FeesCalc.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L2

```solidity
File: contracts/libraries/InteractionHelper.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L2

```solidity
File: contracts/libraries/Math.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L2

```solidity
File: contracts/libraries/PanopticMath.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L2

```solidity
File: contracts/libraries/SafeTransferLib.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L2

```solidity
File: contracts/multicall/Multicall.sol

 2: pragma solidity ^0.8.18;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L2

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L2

```solidity
File: contracts/tokens/ERC20Minimal.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L2

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L2

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L2

```solidity
File: contracts/types/LeftRight.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L2

```solidity
File: contracts/types/LiquidityChunk.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L2

```solidity
File: contracts/types/TokenId.sol

 2: pragma solidity ^0.8.0;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L2


## [NC-80] Use named function calls
When calling a function, use named parameters to improve readability and reduce the chance of making mistakes. For example: `_mint({account: msg.sender, amount: _amount})`

**Total Instances:** 159

```solidity
File: contracts/CollateralTracker.sol

 420:         shares = previewDeposit(assets);

 432:         _mint(receiver, shares);

 446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);

 478:         assets = previewMint(shares);

 492:         _mint(receiver, shares);

 511:         uint256 balance = convertToAssets(balanceOf[owner]);

 536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

 538:         shares = previewWithdraw(assets);

 548:         _burn(owner, shares);

 573:         uint256 available = convertToShares(s_poolAssets);

 582:         return convertToAssets(shares);

 596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

 605:         assets = previewRedeem(shares);

 608:         _burn(owner, shares);

 883:         uint256 shares = convertToShares(assets);

 886:         _transferFrom(delegator, delegatee, shares);

 895:         balanceOf[delegatee] += convertToShares(assets);

 904:         balanceOf[delegatee] -= convertToShares(assets);

 930:         uint256 shares = convertToShares(assets);

 939:             _transferFrom(delegatee, delegator, delegateeBalance);

 954:             _mint(
                     delegator,
                     Math.mulDiv(

 965:             _transferFrom(delegatee, delegator, shares);

 977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

 977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));

 980:                 _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));

 980:                 _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));

 1006:             int256 tokenToPay = _getExchangedAmount(longAmount, shortAmount, swappedAmount);

 1017:                 _burn(optionOwner, sharesToBurn);

 1020:                 uint256 sharesToMint = convertToShares(uint256(-tokenToPay));

 1021:                 _mint(optionOwner, sharesToMint);

 1074:                 _burn(optionOwner, sharesToBurn);

 1077:                 uint256 sharesToMint = convertToShares(uint256(-tokenToPay));

 1078:                 _mint(optionOwner, sharesToMint);

 1147:         tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);

 1170:             tokenRequired = _getTotalRequiredCollateral(atTick, positionBalanceArray);

 1181:         uint256 netBalance = convertToAssets(balanceOf[user]);

 1219:             uint256 _tokenRequired = _getRequiredCollateralAtTickSinglePosition(
                      tokenId,
                      positionSize,
                      atTick,
                      poolUtilization

 1259:                 tokenRequired += _getRequiredCollateralSingleLeg(
                          tokenId,
                          index,
                          positionSize,
                          atTick,
                          poolUtilization

 1287:                 ? _getRequiredCollateralSingleLegNoPartner(
                          tokenId,
                          index,
                          positionSize,
                          atTick,
                          poolUtilization

 1294:                 : _getRequiredCollateralSingleLegPartner(
                          tokenId,
                          index,
                          positionSize,
                          atTick,
                          poolUtilization

 1335:         required = _getRequiredCollateralAtUtilization(amountMoved, isLong, utilization);

 1453:                 required = _computeSpread(
                          tokenId,
                          positionSize,
                          index,
                          partnerIndex,
                          poolUtilization

 1462:             required = _computeStrangle(tokenId, index, positionSize, atTick, poolUtilization);

 1481:             uint256 sellCollateral = _sellCollateralRatio(utilization);

 1491:             uint256 buyCollateral = _buyCollateralRatio(uint256(utilization));

 1581:             _getRequiredCollateralAtUtilization(
                      tokenType == 0 ? movedRight : movedLeft,
                      1,
                      tokenType == 0

 1641:                 strangleRequired = _getRequiredCollateralSingleLegNoPartner(
                          tokenId,
                          index,
                          positionSize,
                          atTick,
                          poolUtilization

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L420

```solidity
File: contracts/PanopticFactory.sol

 263:         (uint256 amount0, uint256 amount1) = _mintFullRange(v3Pool, token0, token1, fee);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L263

```solidity
File: contracts/PanopticPool.sol

 390:         (LeftRightSigned premia, uint256[2][] memory balances) = _calculateAccumulatedPremia(
                 user,
                 positionIdList,
                 COMPUTE_ALL_PREMIA,
                 includePendingPremium,
                 currentTick

 450:             ) = _getPremia(
                         tokenId,
                         LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
                         c_user,
                         computeAllPremia,
                         atTick

 469:                     LeftRightUnsigned availablePremium = _getAvailablePremium(
                             _getTotalLiquidity(tokenId, leg),
                             s_settledTokens[chunkKey],
                             s_grossPremiumLast[chunkKey],
                             LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
                             premiumAccumulatorsByLeg[leg]

 470:                         _getTotalLiquidity(tokenId, leg),

 554:         _mintOptions(
                 positionIdList,
                 positionSize,
                 effectiveLiquidityLimitX32,
                 tickLimitLow,
                 tickLimitHigh

 575:         _burnOptions(COMMIT_LONG_SETTLED, tokenId, msg.sender, tickLimitLow, tickLimitHigh);

 577:         _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);

 592:         _burnAllOptionsFrom(
                 msg.sender,
                 tickLimitLow,
                 tickLimitHigh,
                 COMMIT_LONG_SETTLED,
                 positionIdList

 600:         _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);

 628:         _validatePositionList(msg.sender, positionIdList, 1);

 630:         (tickLimitLow, tickLimitHigh) = _getSlippageLimits(tickLimitLow, tickLimitHigh);

 642:         uint128 poolUtilizations = _mintInSFPMAndUpdateCollateral(
                 tokenId,
                 positionSize,
                 tickLimitLow,
                 tickLimitHigh

 650:         _addUserOption(tokenId, effectiveLiquidityLimitX32);

 661:         uint256 medianData = _validateSolvency(msg.sender, positionIdList, BP_DECREASE_BUFFER);

 689:         _updateSettlementPostMint(tokenId, collectedByLeg, positionSize);

 693:         uint128 poolUtilizations = _payCommissionAndWriteData(tokenId, positionSize, totalSwapped);

 741:         _updatePositionsHash(msg.sender, tokenId, ADD);

 770:                 _checkLiquiditySpread(
                         tokenId,
                         leg,
                         tickLower,
                         tickUpper,
                         uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))

 804:             (paidAmounts, premiasByLeg[i]) = _burnOptions(
                     commitLongSettled,
                     positionIdList[i],
                     owner,
                     tickLimitLow,
                     tickLimitHigh

 834:         (tickLimitLow, tickLimitHigh) = _getSlippageLimits(tickLimitLow, tickLimitHigh);

 840:         (premiaOwed, premiaByLeg, paidAmounts) = _burnAndHandleExercise(
                 commitLongSettled,
                 tickLimitLow,
                 tickLimitHigh,
                 tokenId,
                 positionSize,
                 owner

 850:         _updatePositionDataBurn(owner, tokenId);

 868:                 _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);

 877:         _updatePositionsHash(owner, tokenId, !ADD);

 893:         _validatePositionList(user, positionIdList, 0);

 933:         bool solventAtFast = _checkSolvencyAtTick(
                 user,
                 positionIdList,
                 currentTick,
                 fastOracleTick,
                 buffer

 944:             if (!_checkSolvencyAtTick(user, positionIdList, currentTick, slowOracleTick, buffer))

 973:         (realizedPremia, premiaByLeg) = _updateSettlementPostBurn(
                 owner,
                 tokenId,
                 collectedByLeg,
                 positionSize,
                 commitLongSettled

 1023:         _validatePositionList(liquidatee, positionIdList, 0);

 1039:             (premia, positionBalanceArray) = _calculateAccumulatedPremia(
                      liquidatee,
                      positionIdList,
                      COMPUTE_ALL_PREMIA,
                      ONLY_AVAILABLE_PREMIUM,
                      currentTick

 1060:             (uint256 balanceCross, uint256 thresholdCross) = _getSolvencyBalances(
                      tokenData0,
                      tokenData1,
                      Math.getSqrtRatioAtTick(twapTick)

 1086:             (netExchanged, premiasByLeg) = _burnAllOptionsFrom(
                      liquidatee,
                      Constants.MIN_V3POOL_TICK,
                      Constants.MAX_V3POOL_TICK,
                      DONOT_COMMIT_LONG_SETTLED,
                      positionIdList

 1153:         _validatePositionList(msg.sender, positionIdListLiquidator, 0);

 1156:             !_checkSolvencyAtTick(
                      msg.sender,
                      positionIdListLiquidator,
                      finalTick,
                      finalTick,
                      BP_DECREASE_BUFFER

 1191:         _validatePositionList(msg.sender, positionIdListExercisor, 0);

 1206:             (LeftRightSigned positionPremia, ) = _calculateAccumulatedPremia(
                      account,
                      touchedId,
                      COMPUTE_LONG_PREMIA,
                      ONLY_AVAILABLE_PREMIUM,
                      currentTick

 1227:         _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

 1268:         _validateSolvency(account, positionIdListExercisee, NO_BUFFER);

 1275:             _validateSolvency(msg.sender, positionIdListExercisor, BP_DECREASE_BUFFER);

 1300:         ) = _calculateAccumulatedPremia(
                      account,
                      positionIdList,
                      COMPUTE_ALL_PREMIA,
                      ONLY_AVAILABLE_PREMIUM,
                      currentTick

 1321:         (uint256 balanceCross, uint256 thresholdCross) = _getSolvencyBalances(
                  tokenData0,
                  tokenData1,
                  Math.getSqrtRatioAtTick(atTick)

 1592:         _validatePositionList(owner, positionIdList, 0);

 1658:         _validateSolvency(owner, positionIdList, NO_BUFFER);

 1687:                 uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);

 1844:         (premiaByLeg, premiumAccumulatorsByLeg) = _getPremia(
                  tokenId,
                  positionSize,
                  owner,
                  COMPUTE_ALL_PREMIA,
                  type(int24).max

 1882:                     uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);

 1888:                     LeftRightUnsigned availablePremium = _getAvailablePremium(
                              totalLiquidity + positionLiquidity,
                              settledTokens,
                              grossPremiumLast,
                              LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
                              premiumAccumulatorsByLeg[leg]

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L390

```solidity
File: contracts/SemiFungiblePositionManager.sol

 308:         beginReentrancyLock(poolId);

 314:         endReentrancyLock(poolId);

 482:         _burn(msg.sender, TokenId.unwrap(tokenId), positionSize);

 488:         (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
                 tokenId,
                 positionSize,
                 slippageTickLimitLow,
                 slippageTickLimitHigh,
                 BURN

 515:         _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);

 520:         (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
                 tokenId,
                 positionSize,
                 slippageTickLimitLow,
                 slippageTickLimitHigh,
                 MINT

 552:         registerTokenTransfer(from, to, TokenId.wrap(id), amount);

 577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);

 708:         (totalMoved, collectedByLeg, itmAmounts) = _createPositionInAMM(
                 univ3pool,
                 tokenId,
                 positionSize,
                 isBurn

 718:                 totalMoved = swapInAMM(univ3pool, itmAmounts).add(totalMoved);

 910:                 (_moved, _itmAmounts, _collectedSingleLeg) = _createLegInAMM(
                         _univ3pool,
                         _tokenId,
                         _leg,
                         liquidityChunk,
                         _isBurn

 1067:                 ? _mintLiquidity(liquidityChunk, univ3pool)

 1068:                 : _burnLiquidity(liquidityChunk, univ3pool); // from msg.sender to Uniswap

 1086:             collectedSingleLeg = _collectAndWritePositionData(
                      liquidityChunk,
                      univ3pool,
                      currentLiquidity,
                      positionKey,
                      moved,
                      isLong

 1098:         s_accountFeesBase[positionKey] = _getFeesBase(
                  univ3pool,
                  updatedLiquidity,
                  liquidityChunk,
                  true

 1118:         ) = _getPremiaDeltas(currentLiquidity, collectedAmounts);

 1268:         LeftRightSigned amountToCollect = _getFeesBase(
                  univ3pool,
                  startingLiquidity,
                  liquidityChunk,
                  false

 1311:             _updateStoredPremia(positionKey, currentLiquidity, collectedChunk);

 1499:                 (LeftRightUnsigned premiumOwed, LeftRightUnsigned premiumGross) = _getPremiaDeltas(
                          accountLiquidities,
                          amountToCollect

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L308

```solidity
File: contracts/libraries/FeesCalc.sol

 109:         ) = _getAMMSwapFeesPerLiquidityCollected(univ3pool, currentTick, tickLower, tickUpper);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L109

```solidity
File: contracts/libraries/Math.sol

 192:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());

 193:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());

 196:                 mulDiv(
                         uint256(liquidityChunk.liquidity()) << 96,
                         highPriceX96 - lowPriceX96,
                         highPriceX96

 208:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());

 209:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());

 212:             return mulDiv96(liquidityChunk.liquidity(), highPriceX96 - lowPriceX96);

 226:             amount0 = getAmount0ForLiquidity(liquidityChunk);

 228:             amount1 = getAmount1ForLiquidity(liquidityChunk);

 230:             amount0 = getAmount0ForLiquidity(liquidityChunk.updateTickLower(currentTick));

 231:             amount1 = getAmount1ForLiquidity(liquidityChunk.updateTickUpper(currentTick));

 246:         uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);

 247:         uint160 highPriceX96 = getSqrtRatioAtTick(tickUpper);

 254:                     toUint128(
                             mulDiv(

 255:                         mulDiv(
                                 amount0,
                                 mulDiv96(highPriceX96, lowPriceX96),
                                 highPriceX96 - lowPriceX96

 257:                             mulDiv96(highPriceX96, lowPriceX96),

 276:         uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);

 277:         uint160 highPriceX96 = getSqrtRatioAtTick(tickUpper);

 284:                     toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))

 284:                     toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))

 446:             result = mulDiv(a, b, denominator);

 447:             if (mulmod(a, b, denominator) > 0) {

 586:             result = mulDiv96(a, b);

 587:             if (mulmod(a, b, 2 ** 96) > 0) {

 663:             result = mulDiv128(a, b);

 664:             if (mulmod(a, b, 2 ** 128) > 0) {

 768:             if (left < j) quickSort(arr, left, j);

 769:             if (i < right) quickSort(arr, i, right);

 778:             quickSort(data, int256(0), int256(data.length - 1));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L192

```solidity
File: contracts/libraries/PanopticMath.sol

 397:             (LeftRightSigned longs, LeftRightSigned shorts) = _calculateIOAmounts(
                     tokenId,
                     positionSize,
                     leg

 427:                 tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),

 428:                 tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)

 432:                 tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),

 433:                 tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)

 452:             convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));

 476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

 477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

 613:         LeftRightUnsigned amountsMoved = getAmountsMoved(tokenId, positionSize, legIndex);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L397

```solidity
File: contracts/types/TokenId.sol

 347:         tokenId = addOptionRatio(self, _optionRatio, legIndex);

 348:         tokenId = addAsset(tokenId, _asset, legIndex);

 349:         tokenId = addIsLong(tokenId, _isLong, legIndex);

 350:         tokenId = addTokenType(tokenId, _tokenType, legIndex);

 351:         tokenId = addRiskPartner(tokenId, _riskPartner, legIndex);

 352:         tokenId = addStrike(tokenId, _strike, legIndex);

 353:         tokenId = addWidth(tokenId, _width, legIndex);

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L353


## [NC-81] Use of override is unnecessary.
Starting with Solidity version [0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), using the `override` keyword when the function solely overrides an interface function, and the function doesn’t exist in multiple base contracts, is unnecessary.

**Total Instances:** 4

```solidity
File: contracts/CollateralTracker.sol

 323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

 341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L323

```solidity
File: contracts/SemiFungiblePositionManager.sol

 540:     function safeTransferFrom(
             address from,
             address to,
             uint256 id,
             uint256 amount,
             bytes calldata data
         ) public override {

 566:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public override {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L566


## [NC-82] Use single file for all system-wide constants
Use single file for all system-wide constants.

**Total Instances:** 31

```solidity
File: contracts/CollateralTracker.sol

 70:     string internal constant TICKER_PREFIX = "po";

 73:     string internal constant NAME_PREFIX = "POPT-V1";

 77:     uint256 internal constant DECIMALS = 10_000;

 81:     int128 internal constant DECIMALS_128 = 10_000;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L70

```solidity
File: contracts/PanopticFactory.sol

 82:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;

 86:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

 89:     uint16 internal constant CARDINALITY_INCREASE = 100;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L82

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L103

```solidity
File: contracts/SemiFungiblePositionManager.sol

 125:     bool internal constant MINT = false;

 126:     bool internal constant BURN = true;

 133:     uint128 private constant VEGOID = 2;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L133


## [NC-83] Use a struct instead of returning multiple values
Functions that return many variables can become difficult to read and maintain. Using a struct to encapsulate these return values can improve code readability, increase reusability, and reduce the likelihood of errors. Consider refactoring functions that return more than three variables to use a struct instead.

**Total Instances:** 7

```solidity
File: contracts/CollateralTracker.sol

 277:     function getPoolData()
             external
             view
             returns (uint256 poolAssets, uint256 insideAMM, int256 currentPoolUtilization)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L277

```solidity
File: contracts/PanopticPool.sol

 352:     function optionPositionBalance(
             address user,
             TokenId tokenId
         ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

 381:     function calculateAccumulatedFeesBatch(
             address user,
             bool includePendingPremium,
             TokenId[] calldata positionIdList
         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L352

```solidity
File: contracts/SemiFungiblePositionManager.sol

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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L863

```solidity
File: contracts/libraries/PanopticMath.sol

 651:     function getLiquidationBonus(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint160 sqrtPriceX96Twap,
             uint160 sqrtPriceX96Final,
             LeftRightSigned netExchanged,
             LeftRightSigned premia
         ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L651


## [NC-84] Use a struct to encapsulate multiple function parameters
If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

**Total Instances:** 8

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L178

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L115

```solidity
File: contracts/PanopticPool.sol

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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L955

```solidity
File: contracts/SemiFungiblePositionManager.sol

 1255:     function _collectAndWritePositionData(
              LiquidityChunk liquidityChunk,
              IUniswapV3Pool univ3pool,
              LeftRightUnsigned currentLiquidity,
              bytes32 positionKey,
              LeftRightSigned movedInLeg,
              uint256 isLong
          ) internal returns (LeftRightUnsigned collectedChunk) {

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1255

```solidity
File: contracts/libraries/PanopticMath.sol

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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L651

```solidity
File: contracts/types/TokenId.sol

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L336


## [NC-85] Use `using` keyword when using specific imports rather than calling the specific import directly
In Solidity, the `using` keyword can streamline the use of library functions for specific types. Instead of calling library functions directly with their full import paths, you can declare a library once with `using` for a specific type. This approach makes your code more readable and concise. For example, instead of `LibraryName.functionName(variable)`, you would first declare `using LibraryName for TypeName`; at the contract level. After this, you can call library functions directly on variables of TypeName like `variable.functionName()`. This method not only enhances code clarity but also promotes cleaner and more organized code, especially when multiple functions from the same library are used frequently.

**Total Instances:** 344

```solidity
File: contracts/CollateralTracker.sol

 170:         if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();

 229:         if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();

 292:             InteractionHelper.computeName(

 305:         return InteractionHelper.computeSymbol(s_underlyingToken, TICKER_PREFIX);

 312:         return InteractionHelper.computeDecimals(s_underlyingToken);

 331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

 333:         return ERC20Minimal.transfer(recipient, amount);

 350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

 352:         return ERC20Minimal.transferFrom(from, to, amount);

 380:         return Math.mulDiv(assets, totalSupply, totalAssets());

 387:         return Math.mulDiv(shares, totalAssets(), totalSupply);

 402:             shares = Math.mulDiv(

 418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 424:         SafeTransferLib.safeTransferFrom(

 462:             assets = Math.mulDivRoundingUp(

 480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

 484:         SafeTransferLib.safeTransferFrom(

 512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

 521:         return Math.mulDivRoundingUp(assets, supply, totalAssets());

 536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

 556:         SafeTransferLib.safeTransferFrom(

 575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

 596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

 616:         SafeTransferLib.safeTransferFrom(

 669:                             Math.unsafeDivRoundingUp(

 675:                     maxNumRangesFromStrike = Math.max(

 677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)

 687:                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 693:                     (currentValue0, currentValue1) = Math.getAmountsForLiquidity(

 698:                     (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(

 712:                         LeftRightSigned

 956:                 Math.mulDiv(

 959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

 1012:                 uint256 sharesToBurn = Math.mulDivRoundingUp(

 1069:                 uint256 sharesToBurn = Math.mulDivRoundingUp(

 1109:                 uint256 swapCommission = Math.unsafeDivRoundingUp(

 1110:                     s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),

 1120:                 Math.unsafeDivRoundingUp(

 1210:             TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);

 1213:             uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();

 1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

 1322:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

 1363:                         ? Math.getSqrtRatioAtTick(

 1364:                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

 1364:                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)

 1366:                         : Math.getSqrtRatioAtTick(

 1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

 1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)

 1397:                         uint256 c2 = Constants.FP96 - ratio;

 1401:                         required += Math.mulDiv96RoundingUp(amountMoved, c2);

 1408:                         uint160 scaleFactor = Math.getSqrtRatioAtTick(

 1411:                         uint256 c3 = Math.mulDivRoundingUp(

 1414:                             scaleFactor + Constants.FP96

 1486:                 required = Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS);

 1496:                 required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);

 1518:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

 1521:         LeftRightUnsigned amountsMovedPartner = PanopticMath.getAmountsMoved(

 1571:                     ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)

 1572:                     : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);

 1579:         spreadRequirement = Math.max(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L170

```solidity
File: contracts/PanopticFactory.sol

 150:         if (msg.sender != currentOwner) revert Errors.NotOwner();

 177:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

 179:         CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);

 182:             SafeTransferLib.safeTransferFrom(

 189:             SafeTransferLib.safeTransferFrom(

 220:         if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

 224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

 227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

 230:             revert Errors.PoolAlreadyInitialized();

 241:             Clones.clone(COLLATERAL_REFERENCE)

 244:             Clones.clone(COLLATERAL_REFERENCE)

 304:             uint256 rarity = PanopticMath.numberOfLeadingHexZeros(

 353:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)

 357:                     Math.mulDivRoundingUp(

 359:                         Constants.FP96,

 366:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)

 369:                     Math.mulDivRoundingUp(

 371:                         Constants.FP96,

 392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

 397:             CallbackLib.CallbackData({

 398:                 poolFeatures: CallbackLib.PoolFeatures({token0: token0, token1: token1, fee: fee}),

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L150

```solidity
File: contracts/PanopticPool.sol

 103:     int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;

 105:     int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

 299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

 326:         InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);

 342:             revert Errors.PriceBoundFail();

 415:         (value0, value1) = FeesCalc.getPortfolioValue(

 444:             balances[k][0] = TokenId.unwrap(tokenId);

 445:             balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);

 452:                     LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),

 473:                         LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),

 473:                         LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),

 477:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

 477:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

 525:         (, uint256 medianData) = PanopticMath.computeInternalMedian(

 634:             revert Errors.InvalidTokenIdParameter(0);

 638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

 639:             revert Errors.PositionAlreadyMinted();

 654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned

 712:         (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath

 762:                 s_options[msg.sender][tokenId][leg] = LeftRightUnsigned

 775:                     uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))

 861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

 870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);

 905:         int24 fastOracleTick = PanopticMath.computeMedianObservedPrice(

 915:             slowOracleTick = PanopticMath.computeMedianObservedPrice(

 923:             (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(

 940:         if (!solventAtFast) revert Errors.NotEnoughCollateral();

 943:         if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)

 945:                 revert Errors.NotEnoughCollateral();

 981:         (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) = PanopticMath

 1035:             if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)

 1036:                 revert Errors.StaleTWAP();

 1063:                 Math.getSqrtRatioAtTick(twapTick)

 1066:             if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();

 1088:                 Constants.MIN_V3POOL_TICK,

 1089:                 Constants.MAX_V3POOL_TICK,

 1098:             (liquidationBonus0, liquidationBonus1, collateralRemaining) = PanopticMath

 1102:                     Math.getSqrtRatioAtTick(twapTick),

 1103:                     Math.getSqrtRatioAtTick(finalTick),

 1122:             (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(

 1129:                 Math.getSqrtRatioAtTick(_finalTick),

 1163:         ) revert Errors.NotEnoughCollateral();

 1165:         LeftRightSigned bonusAmounts = LeftRightSigned

 1188:         if (touchedId.length != 1) revert Errors.InputListFail();

 1197:         (LeftRightSigned longAmounts, LeftRightSigned delegatedAmounts) = PanopticMath

 1242:         refundAmounts = PanopticMath.getRefundAmounts(

 1324:             Math.getSqrtRatioAtTick(atTick)

 1329:             return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);

 1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +

 1349:                 Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);

 1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +

 1354:                 Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);

 1383:             fingerprintIncomingList = PanopticMath.updatePositionsHash(

 1394:         if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();

 1410:         uint256 newHash = PanopticMath.updatePositionsHash(

 1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

 1451:         twapTick = PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW);

 1493:             revert Errors.EffectiveLiquidityAboveThreshold();

 1521:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 1545:                     premiaByLeg[leg] = LeftRightSigned

 1567:                         premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

 1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

 1614:             accumulatedPremium = LeftRightUnsigned

 1627:         uint256 liquidity = PanopticMath

 1633:             LeftRightSigned realizedPremia = LeftRightSigned

 1651:                 LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))

 1651:                 LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))

 1680:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned

 1774:                 LeftRightUnsigned

 1778:                             Math.min(

 1787:                             Math.min(

 1862:             if (LeftRightSigned.unwrap(legPremia) != 0) {

 1866:                         settledTokens = LeftRightUnsigned.wrap(

 1868:                                 LeftRightSigned.unwrap(

 1869:                                     LeftRightSigned

 1870:                                         .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))

 1877:                     uint256 positionLiquidity = PanopticMath

 1892:                         LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),

 1892:                         LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),

 1901:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

 1901:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))

 1929:                             ? LeftRightUnsigned

 1934:                                             Math.max(

 1951:                                             Math.max(

 1965:                             : LeftRightUnsigned

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L103

```solidity
File: contracts/SemiFungiblePositionManager.sol

 322:         if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();

 355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

 367:         uint64 poolId = PanopticMath.getPoolId(univ3pool);

 373:             poolId = PanopticMath.incrementPoolPattern(poolId);

 408:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

 410:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

 413:             SafeTransferLib.safeTransferFrom(

 420:             SafeTransferLib.safeTransferFrom(

 441:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

 443:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

 456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

 482:         _burn(msg.sender, TokenId.unwrap(tokenId), positionSize);

 515:         _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);

 549:         if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

 549:         if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

 552:         registerTokenTransfer(from, to, TokenId.wrap(id), amount);

 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

 577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);

 604:             LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

 633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

 634:             ) revert Errors.TransferFailed();

 638:             if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity())

 639:                 revert Errors.TransferFailed();

 645:             s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

 648:             s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

 688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

 702:         if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

 717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

 728:             revert Errors.PriceBoundFail();

 774:                 CallbackLib.CallbackData({

 775:                     poolFeatures: CallbackLib.PoolFeatures({

 817:                 int256 net0 = itm0 - PanopticMath.convert1to0(itm1, sqrtPriceX96);

 833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

 842:                     ? Constants.MIN_V3POOL_SQRT_RATIO + 1

 843:                     : Constants.MAX_V3POOL_SQRT_RATIO - 1,

 848:             totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(

 904:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 922:                     amount0 += Math.getAmount0ForLiquidity(liquidityChunk);

 924:                     amount1 += Math.getAmount1ForLiquidity(liquidityChunk);

 940:             revert Errors.PositionTooLarge();

 1018:                     revert Errors.NotEnoughLiquidity();

 1038:             s_accountLiquidity[positionKey] = LeftRightUnsigned

 1123:         (s_accountPremiumOwed[positionKey], s_accountPremiumGross[positionKey]) = LeftRightLibrary

 1166:             ? LeftRightSigned

 1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

 1172:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

 1174:             : LeftRightSigned

 1176:                 .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

 1177:                 .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

 1191:             CallbackLib.CallbackData({ // compute by reading values from univ3pool every time

 1192:                     poolFeatures: CallbackLib.PoolFeatures({

 1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

 1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

 1279:         if (LeftRightSigned.unwrap(amountToCollect) != 0) {

 1306:             collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(

 1350:                 premium0X64_base = Math.mulDiv(

 1355:                 premium1X64_base = Math.mulDiv(

 1369:                     premium0X64_owed = Math

 1372:                     premium1X64_owed = Math

 1376:                     deltaPremiumOwed = LeftRightUnsigned

 1393:                     premium0X64_gross = Math

 1396:                     premium1X64_gross = Math

 1400:                     deltaPremiumGross = LeftRightUnsigned

 1480:                     LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(

 1492:                     amountToCollect = LeftRightUnsigned.wrap(

 1494:                             LeftRightSigned.unwrap(feesBase.subRect(s_accountFeesBase[positionKey]))

 1507:                 (premiumOwed, premiumGross) = LeftRightLibrary.addCapped(

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L322

```solidity
File: contracts/libraries/CallbackLib.sol

 37:             revert Errors.InvalidUniswapCallback();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L37

```solidity
File: contracts/libraries/FeesCalc.sol

 56:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(

 62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(

 115:             LeftRightSigned

 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L56

```solidity
File: contracts/libraries/InteractionHelper.sol

 81:                     Strings.toString(fee),

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L81

```solidity
File: contracts/libraries/Math.sol

 131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

 131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

 251:                 LiquidityChunkLibrary.createChunk(

 281:                 LiquidityChunkLibrary.createChunk(

 284:                     toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))

 297:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();

 312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

 319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();

 326:         if (toCast > uint256(type(int256).max)) revert Errors.CastingError();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L131

```solidity
File: contracts/libraries/PanopticMath.sol

 77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

 155:             return int24(Math.sort(ticks)[cardinality / 2]);

 263:             int256[] memory sortedTicks = Math.sort(twapMeasurement);

 326:             return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);

 328:             return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);

 346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

 347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

 361:             ) revert Errors.TicksNotInitializable();

 377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))

 452:             convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));

 476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))

 477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));

 479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

 495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);

 497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

 497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

 512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

 514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

 514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

 529:                 int256 absResult = Math

 530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)

 534:                 int256 absResult = Math

 535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

 535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))

 552:                 int256 absResult = Math

 553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)

 557:                 int256 absResult = Math

 559:                         Math.absUint(amount),

 561:                         Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)

 587:             amount1 = Math

 588:                 .getAmount1ForLiquidity(Math.getLiquidityForAmount0(tickLower, tickUpper, amount0))

 593:             amount0 = Math

 594:                 .getAmount0ForLiquidity(Math.getLiquidityForAmount1(tickLower, tickUpper, amount1))

 598:         return LeftRightUnsigned.wrap(0).toRightSlot(amount0).toLeftSlot(amount1);

 621:                 shorts = shorts.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

 624:                 longs = longs.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));

 629:                 shorts = shorts.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

 632:                 longs = longs.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));

 678:                 uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

 681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));

 685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),

 694:                 Math.max(premia.rightSlot(), 0);

 696:                 Math.max(premia.leftSlot(), 0);

 715:                     bonus1 += Math.min(

 719:                     bonus0 -= Math.min(

 733:                     bonus0 += Math.min(

 737:                     bonus1 -= Math.min(

 749:                 LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(

 791:             int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);

 792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

 803:                     -Math.min(

 810:                     Math.min(

 827:                     Math.min(

 834:                     -Math.min(

 847:                 haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());

 848:                 haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());

 869:                         uint256 settled0 = Math.unsafeDivRoundingUp(

 873:                         uint256 settled1 = Math.unsafeDivRoundingUp(

 888:                         settled0 = Math.max(

 892:                         settled1 = Math.max(

 898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(

 924:         uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);

 933:                     LeftRightSigned

 951:                     LeftRightSigned

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L77

```solidity
File: contracts/libraries/SafeTransferLib.sol

 45:         if (!success) revert Errors.TransferFailed();

 75:         if (!success) revert Errors.TransferFailed();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L45

```solidity
File: contracts/tokens/ERC1155Minimal.sol

 115:                 ERC1155Holder.onERC1155Received.selector

 166:                 ERC1155Holder.onERC1155BatchReceived.selector

 225:                 ERC1155Holder.onERC1155Received.selector

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L115

```solidity
File: contracts/types/LeftRight.sol

 163:             ) revert Errors.UnderOverFlow();

 186:             ) revert Errors.UnderOverFlow();

 199:             if (left128 != left) revert Errors.UnderOverFlow();

 204:             if (right128 != right) revert Errors.UnderOverFlow();

 222:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

 240:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

 262:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

 265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

 266:                     int128(Math.max(left128, 0))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L163

```solidity
File: contracts/types/TokenId.sol

 420:         (legLowerTick, legUpperTick) = PanopticMath.getTicks(

 501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

 513:                         revert Errors.InvalidTokenIdParameter(1);

 522:                         revert Errors.InvalidTokenIdParameter(6);

 528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

 531:                     (self.strike(i) == Constants.MIN_V3POOL_TICK) ||

 532:                     (self.strike(i) == Constants.MAX_V3POOL_TICK)

 533:                 ) revert Errors.InvalidTokenIdParameter(4);

 542:                         revert Errors.InvalidTokenIdParameter(3);

 548:                     ) revert Errors.InvalidTokenIdParameter(3);

 561:                         revert Errors.InvalidTokenIdParameter(4);

 567:                         revert Errors.InvalidTokenIdParameter(5);

 582:                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(

 598:         revert Errors.NoLegsExercisable();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L598


## [NC-86] Utility contracts can be made into libraries
Transform utility contracts into libraries for improved code organization and reusability.

**Total Instances:** 1

```solidity
File: contracts/multicall/Multicall.sol

 8: abstract contract Multicall {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L8


## [NC-87] Visibility should be set explicitly rather than defaulting to internal
Explicitly set visibility in Solidity contracts instead of relying on the default internal visibility for improved clarity and maintainability.

**Total Instances:** 11

```solidity
File: contracts/CollateralTracker.sol

 131:     uint256 immutable TICK_DEVIATION;

 136:     uint256 immutable COMMISSION_FEE;

 141:     uint256 immutable SELLER_COLLATERAL_RATIO;

 145:     uint256 immutable BUYER_COLLATERAL_RATIO;

 149:     int256 immutable FORCE_EXERCISE_COST;

 154:     uint256 immutable TARGET_POOL_UTIL;

 158:     uint256 immutable SATURATED_POOL_UTIL;

 162:     uint256 immutable ITM_SPREAD_MULTIPLIER;

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L131

```solidity
File: contracts/PanopticPool.sol

 238:     mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))

 258:     mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L238

```solidity
File: contracts/SemiFungiblePositionManager.sol

 177:     mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L177
