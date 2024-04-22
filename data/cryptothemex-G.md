## Summary

| |Issue|Instances| Gas Savings
|-|:-|:-:|:-:|
| [[G-01](#g-01)] | Multiple accesses of a mapping/array should use a local variable cache | 33| 0|
| [[G-02](#g-02)] | Constructors can be marked `payable` | 4| 84|
| [[G-03](#g-03)] | Division which can not overflow | 20| 1700|
| [[G-04](#g-04)] | Use assembly to emit events | 25| 950|
| [[G-05](#g-05)] | Emit event in setter function only if the state variable was changed | 2| 0|
| [[G-06](#g-06)] | Use nested if to save gas | 10| 0|
| [[G-07](#g-07)] | Internal or Private Function can be Inlined to Save Gas | 5| 100|
| [[G-08](#g-08)] | Modulus operations that could be unchecked | 18| 540|
| [[G-09](#g-09)] | Functions guaranteed to revert when called by normal users can be marked `payable` | 10| 0|
| [[G-10](#g-10)] | if variable is casted more than once, consider caching the result to save gas | 21| 0|
| [[G-11](#g-11)] | Inefficient Parameter Storage | 117| 5850|
| [[G-12](#g-12)] | Consider Merge Sequential Loops | 1| 0|
| [[G-13](#g-13)] | Avoid updating storage when the value hasn't changed | 1| 800|
| [[G-14](#g-14)] | smaller uint/int types cause gas overhead | 50| 300|
| [[G-15](#g-15)] | Use Bytes32 for small data storage | 1| 0|
| [[G-16](#g-16)] | Solidity versions 0.8.19 and above are more gas efficient | 20| 0|
| [[G-17](#g-17)] | Optimal State Variable Order | 2| 10000|
| [[G-18](#g-18)] | Use assembly to write address storage values | 4| 308|
| [[G-19](#g-19)] | State variable read in a loop | 4| 0|
| [[G-20](#g-20)] | Unnecessary casting as variable is already of the same type | 3| 0|
| [[G-21](#g-21)] | Shorten the array rather than copying to a new one | 2| 0|
| [[G-22](#g-22)] | checks for zero uint should be done using assembly to save gas | 47| 1410|
| [[G-23](#g-23)] | Use Assembly for Hash Calculation | 10| 800|
| [[G-24](#g-24)] | `>=` costs less gas than `>` | 150| 450|
| [[G-25](#g-25)] | Counting down in for statements is more gas efficient | 16| 480|
| [[G-26](#g-26)] | Avoid transferring amounts of zero in order to save gas | 12| 1200|

### Gas Risk Issues

### [G-01]<a name="g-01"></a> Multiple accesses of a mapping/array should use a local variable cache

The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the key's keccak256 hash (`Gkeccak256` - **30 gas**) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

*There are 33 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278) should cache `touchedId[0]` :-
	- positionBalance = s_positionBalance[account][touchedId[0]].rightSlot() (contracts/PanopticPool.sol#1193)
	- (longAmounts,delegatedAmounts) = PanopticMath.computeExercisedAmounts(touchedId[0],positionBalance) (contracts/PanopticPool.sol#1197-1198)
	- touchedId[0].validateIsExercisable(twapTick) (contracts/PanopticPool.sol#1219)
	- exerciseFees = s_collateralToken0.exerciseCost(currentTick,twapTick,touchedId[0],positionBalance,longAmounts) (contracts/PanopticPool.sol#1231-1237)

/// @audit ************** Possible Issue Line(s) **************
	L#1193,  L#1197-1198,  L#1219,  L#1231-1237,  

/// @audit ****************** Affected Code *******************
1193:         uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();
1197:         (LeftRightSigned longAmounts, LeftRightSigned delegatedAmounts) = PanopticMath
1198:             .computeExercisedAmounts(touchedId[0], positionBalance);
1219:         touchedId[0].validateIsExercisable(twapTick);
1231:         LeftRightSigned exerciseFees = s_collateralToken0.exerciseCost(
1232:             currentTick,
1233:             twapTick,
1234:             touchedId[0],
1235:             positionBalance,
1236:             longAmounts
1237:         );

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._calculateAccumulatedPremia(address,TokenId[],bool,bool,int24) (contracts/PanopticPool.sol#429-492) should cache `balances[k]` :-
	- balances[k][0] = TokenId.unwrap(tokenId) (contracts/PanopticPool.sol#444)
	- balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]) (contracts/PanopticPool.sol#445)
	- (premiaByLeg,premiumAccumulatorsByLeg) = _getPremia(tokenId,LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),c_user,computeAllPremia,atTick) (contracts/PanopticPool.sol#447-456)

/// @audit ************** Possible Issue Line(s) **************
	L#444,  L#445,  L#447-456,  

/// @audit ****************** Affected Code *******************
 444:             balances[k][0] = TokenId.unwrap(tokenId);
 445:             balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);
 447:             (
 448:                 LeftRightSigned[4] memory premiaByLeg,
 449:                 uint256[2][4] memory premiumAccumulatorsByLeg
 450:             ) = _getPremia(
 451:                     tokenId,
 452:                     LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
 453:                     c_user,
 454:                     computeAllPremia,
 455:                     atTick
 456:                 );

```

*GitHub* : [429-492](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L429-L492)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getPremia(TokenId,uint128,address,bool,int24) (contracts/PanopticPool.sol#1503-1575) should cache `premiaByLeg[leg]` :-
	- premiaByLeg[leg] = LeftRightSigned.wrap(0).toRightSlot(int128(int256(((premiumAccumulatorsByLeg[leg][0] - premiumAccumulatorLast.rightSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))).toLeftSlot(int128(int256(((premiumAccumulatorsByLeg[leg][1] - premiumAccumulatorLast.leftSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))) (contracts/PanopticPool.sol#1545-1564)
	- premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]) (contracts/PanopticPool.sol#1567)
	- premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]) (contracts/PanopticPool.sol#1567)

/// @audit ************** Possible Issue Line(s) **************
	L#1545-1564,  L#1567,  

/// @audit ****************** Affected Code *******************
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
1567:                         premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

```

*GitHub* : [1503-1575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1503-L1575)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256) (contracts/SemiFungiblePositionManager.sol#593-653) should cache `s_accountLiquidity[positionKey_to]` :-
	- (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) || (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0) (contracts/SemiFungiblePositionManager.sol#632-633)
	- s_accountLiquidity[positionKey_to] = fromLiq (contracts/SemiFungiblePositionManager.sol#644)

/// @audit ************** Possible Issue Line(s) **************
	L#632-633,  L#644,  

/// @audit ****************** Affected Code *******************
 632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
 633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)
 644:             s_accountLiquidity[positionKey_to] = fromLiq;

```

*GitHub* : [593-653](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593-L653)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) should cache `_premiasByLeg[i_scope_0]` :-
	- settled0 = Math.unsafeDivRoundingUp(uint128(- _premiasByLeg[i_scope_0][leg_scope_2].rightSlot()) * uint256(haircut0),uint128(longPremium.rightSlot())) (contracts/libraries/PanopticMath.sol#869-872)
	- settled1 = Math.unsafeDivRoundingUp(uint128(- _premiasByLeg[i_scope_0][leg_scope_2].leftSlot()) * uint256(haircut1),uint128(longPremium.leftSlot())) (contracts/libraries/PanopticMath.sol#873-876)
	- settled0 = Math.max(0,uint128(- _premiasByLeg[i_scope_0][leg_scope_2].rightSlot()) - settled0) (contracts/libraries/PanopticMath.sol#888-891)
	- settled1 = Math.max(0,uint128(- _premiasByLeg[i_scope_0][leg_scope_2].leftSlot()) - settled1) (contracts/libraries/PanopticMath.sol#892-895)

/// @audit ************** Possible Issue Line(s) **************
	L#869-872,  L#873-876,  L#888-891,  L#892-895,  

/// @audit ****************** Affected Code *******************
 869:                         uint256 settled0 = Math.unsafeDivRoundingUp(
 870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
 871:                             uint128(longPremium.rightSlot())
 872:                         );
 873:                         uint256 settled1 = Math.unsafeDivRoundingUp(
 874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
 875:                             uint128(longPremium.leftSlot())
 876:                         );
 888:                         settled0 = Math.max(
 889:                             0,
 890:                             uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
 891:                         );
 892:                         settled1 = Math.max(
 893:                             0,
 894:                             uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
 895:                         );

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128) (contracts/PanopticPool.sol#1666-1746) should cache `s_grossPremiumLast[chunkKey]` :-
	- grossPremiumLast = s_grossPremiumLast[chunkKey] (contracts/PanopticPool.sol#1719)
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128((grossCurrent[0] * positionLiquidity + grossPremiumLast.rightSlot() * totalLiquidityBefore) / (totalLiquidity))).toLeftSlot(uint128((grossCurrent[1] * positionLiquidity + grossPremiumLast.leftSlot() * totalLiquidityBefore) / (totalLiquidity))) (contracts/PanopticPool.sol#1725-1742)

/// @audit ************** Possible Issue Line(s) **************
	L#1719,  L#1725-1742,  

/// @audit ****************** Affected Code *******************
1719:                     LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
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

```

*GitHub* : [1666-1746](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1666-L1746)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._updateStoredPremia(bytes32,LeftRightUnsigned,LeftRightUnsigned) (contracts/SemiFungiblePositionManager.sol#1110-1130) should cache `s_accountPremiumOwed[positionKey]` :-
	- (s_accountPremiumOwed[positionKey],s_accountPremiumGross[positionKey]) = LeftRightLibrary.addCapped(s_accountPremiumOwed[positionKey],deltaPremiumOwed,s_accountPremiumGross[positionKey],deltaPremiumGross) (contracts/SemiFungiblePositionManager.sol#1123-1129)

/// @audit ************** Possible Issue Line(s) **************
	L#1123-1129,  

/// @audit ****************** Affected Code *******************
1110:     function _updateStoredPremia(
1111:         bytes32 positionKey,
1112:         LeftRightUnsigned currentLiquidity,
1113:         LeftRightUnsigned collectedAmounts
1114:     ) private {
1115:         (
1116:             LeftRightUnsigned deltaPremiumOwed,
1117:             LeftRightUnsigned deltaPremiumGross
1118:         ) = _getPremiaDeltas(currentLiquidity, collectedAmounts);
1119: 
1120:         // add deltas to accumulators and freeze both accumulators (for a token) if one of them overflows
1121:         // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)
1122:         // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing
1123:         (s_accountPremiumOwed[positionKey], s_accountPremiumGross[positionKey]) = LeftRightLibrary
1124:             .addCapped(
1125:                 s_accountPremiumOwed[positionKey],
1126:                 deltaPremiumOwed,
1127:                 s_accountPremiumGross[positionKey],
1128:                 deltaPremiumGross
1129:             );
1130:     }

```

*GitHub* : [1110-1130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1110-L1130)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) should cache `_premiumAccumulatorsByLeg[_leg]` :-
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(uint256(Math.max((int256(grossPremiumLast.rightSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][0] * positionLiquidity)) + int256(legPremia.rightSlot() * 2 ** 64),0)) / totalLiquidity)).toLeftSlot(uint128(uint256(Math.max((int256(grossPremiumLast.leftSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][1] * positionLiquidity)) + int256(legPremia.leftSlot()) * 2 ** 64,0)) / totalLiquidity)) (contracts/PanopticPool.sol#1928-1968)
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(uint256(Math.max((int256(grossPremiumLast.rightSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][0] * positionLiquidity)) + int256(legPremia.rightSlot() * 2 ** 64),0)) / totalLiquidity)).toLeftSlot(uint128(uint256(Math.max((int256(grossPremiumLast.leftSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][1] * positionLiquidity)) + int256(legPremia.leftSlot()) * 2 ** 64,0)) / totalLiquidity)) (contracts/PanopticPool.sol#1928-1968)

/// @audit ************** Possible Issue Line(s) **************
	L#1928-1968,  

/// @audit ****************** Affected Code *******************
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

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.redeem(uint256,address,address) (contracts/CollateralTracker.sol#591-626) should cache `allowance[owner]` :-
	- allowed = allowance[owner][msg.sender] (contracts/CollateralTracker.sol#600)
	- allowance[owner][msg.sender] = allowed - shares (contracts/CollateralTracker.sol#602)

/// @audit ************** Possible Issue Line(s) **************
	L#600,  L#602,  

/// @audit ****************** Affected Code *******************
 600:             uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.
 602:             if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

```

*GitHub* : [591-626](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L591-L626)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256) (contracts/SemiFungiblePositionManager.sol#593-653) should cache `s_accountFeesBase[positionKey_to]` :-
	- (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) || (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0) (contracts/SemiFungiblePositionManager.sol#632-633)
	- s_accountFeesBase[positionKey_to] = fromBase (contracts/SemiFungiblePositionManager.sol#647)

/// @audit ************** Possible Issue Line(s) **************
	L#632-633,  L#647,  

/// @audit ****************** Affected Code *******************
 632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
 633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)
 647:             s_accountFeesBase[positionKey_to] = fromBase;

```

*GitHub* : [593-653](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593-L653)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256) (contracts/SemiFungiblePositionManager.sol#1449-1523) should cache `s_accountPremiumGross[positionKey]` :-
	- (premiumOwed,premiumGross) = LeftRightLibrary.addCapped(s_accountPremiumOwed[positionKey],premiumOwed,s_accountPremiumGross[positionKey],premiumGross) (contracts/SemiFungiblePositionManager.sol#1507-1512)
	- acctPremia = s_accountPremiumGross[positionKey] (contracts/SemiFungiblePositionManager.sol#1518-1520)

/// @audit ************** Possible Issue Line(s) **************
	L#1507-1512,  L#1518-1520,  

/// @audit ****************** Affected Code *******************
1507:                 (premiumOwed, premiumGross) = LeftRightLibrary.addCapped(
1508:                     s_accountPremiumOwed[positionKey],
1509:                     premiumOwed,
1510:                     s_accountPremiumGross[positionKey],
1511:                     premiumGross
1512:                 );
1518:             acctPremia = isLong == 1
1519:                 ? s_accountPremiumOwed[positionKey]
1520:                 : s_accountPremiumGross[positionKey];

```

*GitHub* : [1449-1523](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1449-L1523)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) should cache `s_settledTokens[chunkKey]` :-
	- s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))) (contracts/PanopticPool.sol#1650-1652)
	- s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))) (contracts/PanopticPool.sol#1650-1652)

/// @audit ************** Possible Issue Line(s) **************
	L#1650-1652,  

/// @audit ****************** Affected Code *******************
1650:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(
1651:                 LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))
1652:             );

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#958-1104) should cache `s_accountLiquidity[positionKey]` :-
	- currentLiquidity = s_accountLiquidity[positionKey] (contracts/SemiFungiblePositionManager.sol#988)
	- s_accountLiquidity[positionKey] = LeftRightUnsigned.wrap(0).toLeftSlot(removedLiquidity).toRightSlot(updatedLiquidity) (contracts/SemiFungiblePositionManager.sol#1038-1041)

/// @audit ************** Possible Issue Line(s) **************
	L#988,  L#1038-1041,  

/// @audit ****************** Affected Code *******************
 988:         LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache
1038:             s_accountLiquidity[positionKey] = LeftRightUnsigned
1039:                 .wrap(0)
1040:                 .toLeftSlot(removedLiquidity)
1041:                 .toRightSlot(updatedLiquidity);

```

*GitHub* : [958-1104](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L958-L1104)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128) (contracts/PanopticPool.sol#1666-1746) should cache `grossCurrent[1]` :-
	- (grossCurrent[0],grossCurrent[1]) = SFPM.getAccountPremium(address(s_univ3pool),address(this),tokenId.tokenType(leg),liquidityChunk.tickLower(),liquidityChunk.tickUpper(),type()(int24).max,0) (contracts/PanopticPool.sol#1707-1715)
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128((grossCurrent[0] * positionLiquidity + grossPremiumLast.rightSlot() * totalLiquidityBefore) / (totalLiquidity))).toLeftSlot(uint128((grossCurrent[1] * positionLiquidity + grossPremiumLast.leftSlot() * totalLiquidityBefore) / (totalLiquidity))) (contracts/PanopticPool.sol#1725-1742)

/// @audit ************** Possible Issue Line(s) **************
	L#1707-1715,  L#1725-1742,  

/// @audit ****************** Affected Code *******************
1707:                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1708:                     address(s_univ3pool),
1709:                     address(this),
1710:                     tokenId.tokenType(leg),
1711:                     liquidityChunk.tickLower(),
1712:                     liquidityChunk.tickUpper(),
1713:                     type(int24).max,
1714:                     0
1715:                 );
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

```

*GitHub* : [1666-1746](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1666-L1746)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256) (contracts/SemiFungiblePositionManager.sol#593-653) should cache `s_accountFeesBase[positionKey_from]` :-
	- fromBase = s_accountFeesBase[positionKey_from] (contracts/SemiFungiblePositionManager.sol#641)
	- s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0) (contracts/SemiFungiblePositionManager.sol#648)

/// @audit ************** Possible Issue Line(s) **************
	L#641,  L#648,  

/// @audit ****************** Affected Code *******************
 641:             LeftRightSigned fromBase = s_accountFeesBase[positionKey_from];
 648:             s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

```

*GitHub* : [593-653](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593-L653)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getPremia(TokenId,uint128,address,bool,int24) (contracts/PanopticPool.sol#1503-1575) should cache `premiumAccumulatorsByLeg[leg]` :-
	- (premiumAccumulatorsByLeg[leg][0],premiumAccumulatorsByLeg[leg][1]) = SFPM.getAccountPremium(address(s_univ3pool),address(this),tokenType,liquidityChunk.tickLower(),liquidityChunk.tickUpper(),atTick,isLong) (contracts/PanopticPool.sol#1528-1537)
	- (premiumAccumulatorsByLeg[leg][0],premiumAccumulatorsByLeg[leg][1]) = SFPM.getAccountPremium(address(s_univ3pool),address(this),tokenType,liquidityChunk.tickLower(),liquidityChunk.tickUpper(),atTick,isLong) (contracts/PanopticPool.sol#1528-1537)
	- premiaByLeg[leg] = LeftRightSigned.wrap(0).toRightSlot(int128(int256(((premiumAccumulatorsByLeg[leg][0] - premiumAccumulatorLast.rightSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))).toLeftSlot(int128(int256(((premiumAccumulatorsByLeg[leg][1] - premiumAccumulatorLast.leftSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))) (contracts/PanopticPool.sol#1545-1564)
	- premiaByLeg[leg] = LeftRightSigned.wrap(0).toRightSlot(int128(int256(((premiumAccumulatorsByLeg[leg][0] - premiumAccumulatorLast.rightSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))).toLeftSlot(int128(int256(((premiumAccumulatorsByLeg[leg][1] - premiumAccumulatorLast.leftSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))) (contracts/PanopticPool.sol#1545-1564)

/// @audit ************** Possible Issue Line(s) **************
	L#1528-1537,  L#1545-1564,  

/// @audit ****************** Affected Code *******************
1528:                 (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM
1529:                     .getAccountPremium(
1530:                         address(s_univ3pool),
1531:                         address(this),
1532:                         tokenType,
1533:                         liquidityChunk.tickLower(),
1534:                         liquidityChunk.tickUpper(),
1535:                         atTick,
1536:                         isLong
1537:                     );
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

```

*GitHub* : [1503-1575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1503-L1575)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) should cache `s_settledTokens[chunkKey]` :-
	- settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]) (contracts/PanopticPool.sol#1860)
	- s_settledTokens[chunkKey] = settledTokens (contracts/PanopticPool.sol#1974)

/// @audit ************** Possible Issue Line(s) **************
	L#1860,  L#1974,  

/// @audit ****************** Affected Code *******************
1860:             LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1974:             s_settledTokens[chunkKey] = settledTokens;

```

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.deployNewPool(address,address,uint24,bytes32) (contracts/PanopticFactory.sol#210-276) should cache `s_getPanopticPool[v3Pool]` :-
	- address(s_getPanopticPool[v3Pool]) != address(0) (contracts/PanopticFactory.sol#229)
	- s_getPanopticPool[v3Pool] = newPoolContract (contracts/PanopticFactory.sol#253)

/// @audit ************** Possible Issue Line(s) **************
	L#229,  L#253,  

/// @audit ****************** Affected Code *******************
 229:         if (address(s_getPanopticPool[v3Pool]) != address(0))
 253:         s_getPanopticPool[v3Pool] = newPoolContract;

```

*GitHub* : [210-276](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210-L276)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/SemiFungiblePositionManager.sol#566-585) should cache `ids[i]` :-
	- s_poolContext[TokenId.wrap(ids[i]).poolId()].locked (contracts/SemiFungiblePositionManager.sol#576)
	- registerTokenTransfer(from,to,TokenId.wrap(ids[i]),amounts[i]) (contracts/SemiFungiblePositionManager.sol#577)

/// @audit ************** Possible Issue Line(s) **************
	L#576,  L#577,  

/// @audit ****************** Affected Code *******************
 566:     function safeBatchTransferFrom(
 567:         address from,
 568:         address to,
 569:         uint256[] calldata ids,
 570:         uint256[] calldata amounts,
 571:         bytes calldata data
 572:     ) public override {
 573:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
 574:         // so just check if there is an active reentrancy lock for the relevant pool on each token
 575:         for (uint256 i = 0; i < ids.length; ) {
 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
 577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
 578:             unchecked {
 579:                 ++i;
 580:             }
 581:         }
 582: 
 583:         // transfer the token (note that all state updates are completed before reentrancy is possible)
 584:         super.safeBatchTransferFrom(from, to, ids, amounts, data);
 585:     }

```

*GitHub* : [566-585](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566-L585)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.withdraw(uint256,address,address) (contracts/CollateralTracker.sol#531-566) should cache `allowance[owner]` :-
	- allowed = allowance[owner][msg.sender] (contracts/CollateralTracker.sol#542)
	- allowance[owner][msg.sender] = allowed - shares (contracts/CollateralTracker.sol#544)

/// @audit ************** Possible Issue Line(s) **************
	L#542,  L#544,  

/// @audit ****************** Affected Code *******************
 542:             uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.
 544:             if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

```

*GitHub* : [531-566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L531-L566)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24) (contracts/PanopticPool.sol#614-667) should cache `s_positionBalance[msg.sender]` :-
	- LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0 (contracts/PanopticPool.sol#638)
	- s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned.wrap(0).toLeftSlot(poolUtilizations).toRightSlot(positionSize) (contracts/PanopticPool.sol#654-657)

/// @audit ************** Possible Issue Line(s) **************
	L#638,  L#654-657,  

/// @audit ****************** Affected Code *******************
 638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)
 654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
 655:             .wrap(0)
 656:             .toLeftSlot(poolUtilizations)
 657:             .toRightSlot(positionSize);

```

*GitHub* : [614-667](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L614-L667)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.beginReentrancyLock(uint64) (contracts/SemiFungiblePositionManager.sol#320-326) should cache `s_poolContext[poolId]` :-
	- s_poolContext[poolId].locked (contracts/SemiFungiblePositionManager.sol#322)

/// @audit ************** Possible Issue Line(s) **************
	L#322,  

/// @audit ****************** Affected Code *******************
 320:     function beginReentrancyLock(uint64 poolId) internal {
 321:         // check if the pool is already locked, if so, revert
 322:         if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();
 323: 
 324:         // activate lock
 325:         s_poolContext[poolId].locked = true;
 326:     }

```

*GitHub* : [320-326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L320-L326)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal.transferFrom(address,address,uint256) (contracts/tokens/ERC20Minimal.sol#81-97) should cache `allowance[from]` :-
	- allowed = allowance[from][msg.sender] (contracts/tokens/ERC20Minimal.sol#82)
	- allowance[from][msg.sender] = allowed - amount (contracts/tokens/ERC20Minimal.sol#84)

/// @audit ************** Possible Issue Line(s) **************
	L#82,  L#84,  

/// @audit ****************** Affected Code *******************
  81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
  82:         uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.
  83: 
  84:         if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
  85: 
  86:         balanceOf[from] -= amount;
  87: 
  88:         // Cannot overflow because the sum of all user
  89:         // balances can't exceed the max uint256 value.
  90:         unchecked {
  91:             balanceOf[to] += amount;
  92:         }
  93: 
  94:         emit Transfer(from, to, amount);
  95: 
  96:         return true;
  97:     }

```

*GitHub* : [81-97](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L81-L97)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getTotalRequiredCollateral(int24,uint256[2][]) (contracts/CollateralTracker.sol#1200-1236) should cache `positionBalanceArray[i]` :-
	- tokenId = TokenId.wrap(positionBalanceArray[i][0]) (contracts/CollateralTracker.sol#1210)
	- positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot() (contracts/CollateralTracker.sol#1213)
	- poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot() (contracts/CollateralTracker.sol#1216)

/// @audit ************** Possible Issue Line(s) **************
	L#1210,  L#1213,  L#1216,  

/// @audit ****************** Affected Code *******************
1210:             TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);
1213:             uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();
1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

```

*GitHub* : [1200-1236](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1200-L1236)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) should cache `_settledTokens[chunkKey]` :-
	- _settledTokens[chunkKey] = _settledTokens[chunkKey].add(LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(uint128(settled1))) (contracts/libraries/PanopticMath.sol#897-901)
	- _settledTokens[chunkKey] = _settledTokens[chunkKey].add(LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(uint128(settled1))) (contracts/libraries/PanopticMath.sol#897-901)

/// @audit ************** Possible Issue Line(s) **************
	L#897-901,  

/// @audit ****************** Affected Code *******************
 897:                         _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
 898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
 899:                                 uint128(settled1)
 900:                             )
 901:                         );

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) should cache `s_grossPremiumLast[chunkKey]` :-
	- grossPremiumLast = s_grossPremiumLast[chunkKey] (contracts/PanopticPool.sol#1886)
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(uint256(Math.max((int256(grossPremiumLast.rightSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][0] * positionLiquidity)) + int256(legPremia.rightSlot() * 2 ** 64),0)) / totalLiquidity)).toLeftSlot(uint128(uint256(Math.max((int256(grossPremiumLast.leftSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][1] * positionLiquidity)) + int256(legPremia.leftSlot()) * 2 ** 64,0)) / totalLiquidity)) (contracts/PanopticPool.sol#1928-1968)
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0])).toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1])) (contracts/PanopticPool.sol#1928-1968)

/// @audit ************** Possible Issue Line(s) **************
	L#1886,  L#1928-1968,  

/// @audit ****************** Affected Code *******************
1886:                     LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
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

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256) (contracts/SemiFungiblePositionManager.sol#593-653) should cache `s_accountLiquidity[positionKey_from]` :-
	- fromLiq = s_accountLiquidity[positionKey_from] (contracts/SemiFungiblePositionManager.sol#637)
	- s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0) (contracts/SemiFungiblePositionManager.sol#645)

/// @audit ************** Possible Issue Line(s) **************
	L#637,  L#645,  

/// @audit ****************** Affected Code *******************
 637:             LeftRightUnsigned fromLiq = s_accountLiquidity[positionKey_from];
 645:             s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

```

*GitHub* : [593-653](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593-L653)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) should cache `s_options[owner]` :-
	- premiumAccumulatorsLast = s_options[owner][tokenId][legIndex] (contracts/PanopticPool.sol#1621)
	- s_options[owner][tokenId][legIndex] = accumulatedPremium (contracts/PanopticPool.sol#1622)

/// @audit ************** Possible Issue Line(s) **************
	L#1621,  L#1622,  

/// @audit ****************** Affected Code *******************
1621:             LeftRightUnsigned premiumAccumulatorsLast = s_options[owner][tokenId][legIndex];
1622:             s_options[owner][tokenId][legIndex] = accumulatedPremium;

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.initializeAMMPool(address,address,uint24) (contracts/SemiFungiblePositionManager.sol#350-391) should cache `s_AddrToPoolIdData[univ3pool]` :-
	- s_AddrToPoolIdData[univ3pool] != 0 (contracts/SemiFungiblePositionManager.sol#362)
	- s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255 (contracts/SemiFungiblePositionManager.sol#388)

/// @audit ************** Possible Issue Line(s) **************
	L#362,  L#388,  

/// @audit ****************** Affected Code *******************
 362:         if (s_AddrToPoolIdData[univ3pool] != 0) return;
 388:             s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;

```

*GitHub* : [350-391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350-L391)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._calculateAccumulatedPremia(address,TokenId[],bool,bool,int24) (contracts/PanopticPool.sol#429-492) should cache `premiaByLeg[leg]` :-
	- availablePremium = _getAvailablePremium(_getTotalLiquidity(tokenId,leg),s_settledTokens[chunkKey],s_grossPremiumLast[chunkKey],LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),premiumAccumulatorsByLeg[leg]) (contracts/PanopticPool.sol#469-475)
	- portfolioPremium = portfolioPremium.add(premiaByLeg[leg]) (contracts/PanopticPool.sol#480)

/// @audit ************** Possible Issue Line(s) **************
	L#469-475,  L#480,  

/// @audit ****************** Affected Code *******************
 469:                     LeftRightUnsigned availablePremium = _getAvailablePremium(
 470:                         _getTotalLiquidity(tokenId, leg),
 471:                         s_settledTokens[chunkKey],
 472:                         s_grossPremiumLast[chunkKey],
 473:                         LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
 474:                         premiumAccumulatorsByLeg[leg]
 475:                     );
 480:                     portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);

```

*GitHub* : [429-492](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L429-L492)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updatePositionsHash(address,TokenId,bool) (contracts/PanopticPool.sol#1405-1417) should cache `s_positionsHash[account]` :-
	- newHash = PanopticMath.updatePositionsHash(s_positionsHash[account],tokenId,addFlag) (contracts/PanopticPool.sol#1410-1414)

/// @audit ************** Possible Issue Line(s) **************
	L#1410-1414,  

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [1405-1417](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1405-L1417)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128) (contracts/PanopticPool.sol#1666-1746) should cache `s_settledTokens[chunkKey]` :-
	- s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]) (contracts/PanopticPool.sol#1677)
	- s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]) (contracts/PanopticPool.sol#1677)

/// @audit ************** Possible Issue Line(s) **************
	L#1677,  

/// @audit ****************** Affected Code *******************
1677:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);

```

*GitHub* : [1666-1746](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1666-L1746)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.initializeAMMPool(address,address,uint24) (contracts/SemiFungiblePositionManager.sol#350-391) should cache `s_poolContext[poolId]` :-
	- address(s_poolContext[poolId].pool) != address(0) (contracts/SemiFungiblePositionManager.sol#372)
	- s_poolContext[poolId] = PoolAddressAndLock({pool:IUniswapV3Pool(univ3pool),locked:s_poolContext[poolId].locked}) (contracts/SemiFungiblePositionManager.sol#379-382)
	- s_poolContext[poolId] = PoolAddressAndLock({pool:IUniswapV3Pool(univ3pool),locked:s_poolContext[poolId].locked}) (contracts/SemiFungiblePositionManager.sol#379-382)

/// @audit ************** Possible Issue Line(s) **************
	L#372,  L#379-382,  

/// @audit ****************** Affected Code *******************
 372:         while (address(s_poolContext[poolId].pool) != address(0)) {
 379:         s_poolContext[poolId] = PoolAddressAndLock({
 380:             pool: IUniswapV3Pool(univ3pool),
 381:             locked: s_poolContext[poolId].locked
 382:         });

```

*GitHub* : [350-391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350-L391)

### [G-02]<a name="g-02"></a> Constructors can be marked `payable`

Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.constructor(IUniswapV3Factory) (contracts/SemiFungiblePositionManager.sol#341-343) can be payable.

/// @audit ****************** Affected Code *******************
 341:     constructor(IUniswapV3Factory _factory) {
 342:         FACTORY = _factory;
 343:     }

```

*GitHub* : [341-343](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L341-L343)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address) (contracts/PanopticFactory.sol#115-130) can be payable.

/// @audit ****************** Affected Code *******************
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

*GitHub* : [115-130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L115-L130)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.constructor(SemiFungiblePositionManager) (contracts/PanopticPool.sol#280-282) can be payable.

/// @audit ****************** Affected Code *******************
 280:     constructor(SemiFungiblePositionManager _sfpm) {
 281:         SFPM = _sfpm;
 282:     }

```

*GitHub* : [280-282](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L280-L282)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.constructor(uint256,uint256,uint256,int256,uint256,uint256,uint256) (contracts/CollateralTracker.sol#178-211) can be payable.

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [178-211](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L178-L211)

### [G-03]<a name="g-03"></a> Division which can not overflow

Division operations on unsigned integers should be `unchecked` to save gas since they cannot overflow or underflow. Because unsigned integers cannot have negative values, execution of division operations outside `unchecked` blocks adds nothing but overhead. Saves about 85 gas.

*There are 20 instance(s) of this issue:*

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned) (contracts/SemiFungiblePositionManager.sol#1321-1407) perform division which can not overflow (can use unchecked) :-
	- numerator = netLiquidity + (removedLiquidity / 2 ** VEGOID) (contracts/SemiFungiblePositionManager.sol#1367)
	- numerator_scope_0 = totalLiquidity ** 2 - totalLiquidity * removedLiquidity + ((removedLiquidity ** 2) / 2 ** (VEGOID)) (contracts/SemiFungiblePositionManager.sol#1388-1391)

/// @audit ************** Possible Issue Line(s) **************
	L#1367,  L#1388-1391,  

/// @audit ****************** Affected Code *******************
1367:                     uint256 numerator = netLiquidity + (removedLiquidity / 2 ** VEGOID);
1388:                     uint256 numerator = totalLiquidity ** 2 -
1389:                         totalLiquidity *
1390:                         removedLiquidity +
1391:                         ((removedLiquidity ** 2) / 2 ** (VEGOID));

```

*GitHub* : [1321-1407](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1321-L1407)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getPremia(TokenId,uint128,address,bool,int24) (contracts/PanopticPool.sol#1503-1575) perform division which can not overflow (can use unchecked) :-
	- premiaByLeg[leg] = LeftRightSigned.wrap(0).toRightSlot(int128(int256(((premiumAccumulatorsByLeg[leg][0] - premiumAccumulatorLast.rightSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))).toLeftSlot(int128(int256(((premiumAccumulatorsByLeg[leg][1] - premiumAccumulatorLast.leftSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))) (contracts/PanopticPool.sol#1545-1564)

/// @audit ************** Possible Issue Line(s) **************
	L#1545-1564,  

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [1503-1575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1503-L1575)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._sellCollateralRatio(int256) (contracts/CollateralTracker.sol#751-800) perform division which can not overflow (can use unchecked) :-
	- min_sell_ratio /= 2 (contracts/CollateralTracker.sol#778)
	- min_sell_ratio + ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) / (SATURATED_POOL_UTIL - TARGET_POOL_UTIL) (contracts/CollateralTracker.sol#795-798)

/// @audit ************** Possible Issue Line(s) **************
	L#778,  L#795-798,  

/// @audit ****************** Affected Code *******************
 778:                 min_sell_ratio /= 2;
 795:             return
 796:                 min_sell_ratio +
 797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
 798:                 (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);

```

*GitHub* : [751-800](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L751-L800)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128) (contracts/PanopticPool.sol#1666-1746) perform division which can not overflow (can use unchecked) :-
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128((grossCurrent[0] * positionLiquidity + grossPremiumLast.rightSlot() * totalLiquidityBefore) / (totalLiquidity))).toLeftSlot(uint128((grossCurrent[1] * positionLiquidity + grossPremiumLast.leftSlot() * totalLiquidityBefore) / (totalLiquidity))) (contracts/PanopticPool.sol#1725-1742)

/// @audit ************** Possible Issue Line(s) **************
	L#1725-1742,  

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [1666-1746](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1666-L1746)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.constructor(uint256,uint256,uint256,int256,uint256,uint256,uint256) (contracts/CollateralTracker.sol#178-211) perform division which can not overflow (can use unchecked) :-
	- TICK_DEVIATION = uint256(2230 + (12500 * ratioTick) / 10_000 + (7812 * ratioTick ** 2) / 10_000 ** 2 + (6510 * ratioTick ** 3) / 10_000 ** 3) (contracts/CollateralTracker.sol#201-209)

/// @audit ************** Possible Issue Line(s) **************
	L#201-209,  

/// @audit ****************** Affected Code *******************
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

*GitHub* : [178-211](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L178-L211)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) perform division which can not overflow (can use unchecked) :-
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#176,  

/// @audit ****************** Affected Code *******************
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) perform division which can not overflow (can use unchecked) :-
	- realizedPremia = LeftRightSigned.wrap(0).toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64))).toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64))) (contracts/PanopticPool.sol#1633-1636)

/// @audit ************** Possible Issue Line(s) **************
	L#1633-1636,  

/// @audit ****************** Affected Code *******************
1633:             LeftRightSigned realizedPremia = LeftRightSigned
1634:                 .wrap(0)
1635:                 .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))
1636:                 .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.unsafeDivRoundingUp(uint256,uint256) (contracts/libraries/Math.sol#738-742) perform division which can not overflow (can use unchecked) :-
	- result = a / b + a % b > 0 (contracts/libraries/Math.sol#740)

/// @audit ************** Possible Issue Line(s) **************
	L#740,  

/// @audit ****************** Affected Code *******************
 738:     function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
 739:         assembly ("memory-safe") {
 740:             result := add(div(a, b), gt(mod(a, b), 0))
 741:         }
 742:     }

```

*GitHub* : [738-742](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L738-L742)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getAmount0ForLiquidity(LiquidityChunk) (contracts/libraries/Math.sol#191-202) perform division which can not overflow (can use unchecked) :-
	- mulDiv(uint256(liquidityChunk.liquidity()) << 96,highPriceX96 - lowPriceX96,highPriceX96) / lowPriceX96 (contracts/libraries/Math.sol#195-200)

/// @audit ************** Possible Issue Line(s) **************
	L#195-200,  

/// @audit ****************** Affected Code *******************
 191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
 192:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
 193:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());
 194:         unchecked {
 195:             return
 196:                 mulDiv(
 197:                     uint256(liquidityChunk.liquidity()) << 96,
 198:                     highPriceX96 - lowPriceX96,
 199:                     highPriceX96
 200:                 ) / lowPriceX96;
 201:         }
 202:     }

```

*GitHub* : [191-202](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L191-L202)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) perform division which can not overflow (can use unchecked) :-
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(uint256(Math.max((int256(grossPremiumLast.rightSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][0] * positionLiquidity)) + int256(legPremia.rightSlot() * 2 ** 64),0)) / totalLiquidity)).toLeftSlot(uint128(uint256(Math.max((int256(grossPremiumLast.leftSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][1] * positionLiquidity)) + int256(legPremia.leftSlot()) * 2 ** 64,0)) / totalLiquidity)) (contracts/PanopticPool.sol#1928-1968)

/// @audit ************** Possible Issue Line(s) **************
	L#1928-1968,  

/// @audit ****************** Affected Code *******************
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

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) perform division which can not overflow (can use unchecked) :-
	- result = prod0 / denominator (contracts/libraries/Math.sol#363)
	- denominator = denominator / twos (contracts/libraries/Math.sol#394)
	- prod0 = prod0 / twos (contracts/libraries/Math.sol#399)
	- twos = 0 - twos / twos + 1 (contracts/libraries/Math.sol#405)

/// @audit ************** Possible Issue Line(s) **************
	L#363,  L#394,  L#399,  L#405,  

/// @audit ****************** Affected Code *******************
 363:                     result := div(prod0, denominator)
 394:                 denominator := div(denominator, twos)
 399:                 prod0 := div(prod0, twos)
 405:                 twos := add(div(sub(0, twos), twos), 1)

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.twapFilter(IUniswapV3Pool,uint32) (contracts/libraries/PanopticMath.sol#241-268) perform division which can not overflow (can use unchecked) :-
	- secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20) (contracts/libraries/PanopticMath.sol#249)
	- twapMeasurement[i_scope_0] = int24((tickCumulatives[i_scope_0] - tickCumulatives[i_scope_0 + 1]) / int56(uint56(twapWindow / 20))) (contracts/libraries/PanopticMath.sol#257-259)

/// @audit ************** Possible Issue Line(s) **************
	L#249,  L#257-259,  

/// @audit ****************** Affected Code *******************
 249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);
 257:                 twapMeasurement[i] = int24(
 258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
 259:                 );

```

*GitHub* : [241-268](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L241-L268)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._buyCollateralRatio(uint256) (contracts/CollateralTracker.sol#806-853) perform division which can not overflow (can use unchecked) :-
	- BUYER_COLLATERAL_RATIO / 2 (contracts/CollateralTracker.sol#843)
	- (BUYER_COLLATERAL_RATIO + (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) / (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2 (contracts/CollateralTracker.sol#848-851)

/// @audit ************** Possible Issue Line(s) **************
	L#843,  L#848-851,  

/// @audit ****************** Affected Code *******************
 843:                 return BUYER_COLLATERAL_RATIO / 2;
 848:             return
 849:                 (BUYER_COLLATERAL_RATIO +
 850:                     (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
 851:                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2

```

*GitHub* : [806-853](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L806-L853)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned) (contracts/libraries/PanopticMath.sol#651-754) perform division which can not overflow (can use unchecked) :-
	- requiredRatioX128 = (required0 << 128) / (required0 + required1) (contracts/libraries/PanopticMath.sol#669)
	- bonusCross = Math.min(balanceCross / 2,thresholdCross - balanceCross) (contracts/libraries/PanopticMath.sol#678)

/// @audit ************** Possible Issue Line(s) **************
	L#669,  L#678,  

/// @audit ****************** Affected Code *******************
 669:                 uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);
 678:                 uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);

```

*GitHub* : [651-754](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L651-L754)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.maxMint(address) (contracts/CollateralTracker.sol#444-448) perform division which can not overflow (can use unchecked) :-
	- (convertToShares(type()(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE) (contracts/CollateralTracker.sol#446)

/// @audit ************** Possible Issue Line(s) **************
	L#446,  

/// @audit ****************** Affected Code *******************
 444:     function maxMint(address) external view returns (uint256 maxShares) {
 445:         unchecked {
 446:             return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
 447:         }
 448:     }

```

*GitHub* : [444-448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444-L448)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._poolUtilization() (contracts/CollateralTracker.sol#741-745) perform division which can not overflow (can use unchecked) :-
	- int256((s_inAMM * DECIMALS) / totalAssets()) (contracts/CollateralTracker.sol#743)

/// @audit ************** Possible Issue Line(s) **************
	L#743,  

/// @audit ****************** Affected Code *******************
 741:     function _poolUtilization() internal view returns (int256 poolUtilization) {
 742:         unchecked {
 743:             return int256((s_inAMM * DECIMALS) / totalAssets());
 744:         }
 745:     }

```

*GitHub* : [741-745](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L741-L745)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]) (contracts/PanopticPool.sol#1757-1796) perform division which can not overflow (can use unchecked) :-
	- accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) * totalLiquidity) / 2 ** 64 (contracts/PanopticPool.sol#1768-1769)
	- accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) * totalLiquidity) / 2 ** 64 (contracts/PanopticPool.sol#1770-1771)
	- (LeftRightUnsigned.wrap(0).toRightSlot(uint128(Math.min((uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) / type()(uint256).max,premiumOwed.rightSlot()))).toLeftSlot(uint128(Math.min((uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) / type()(uint256).max,premiumOwed.leftSlot())))) (contracts/PanopticPool.sol#1773-1794)
	- (LeftRightUnsigned.wrap(0).toRightSlot(uint128(Math.min((uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) / type()(uint256).max,premiumOwed.rightSlot()))).toLeftSlot(uint128(Math.min((uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) / accumulated1,premiumOwed.leftSlot())))) (contracts/PanopticPool.sol#1773-1794)
	- (LeftRightUnsigned.wrap(0).toRightSlot(uint128(Math.min((uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) / accumulated0,premiumOwed.rightSlot()))).toLeftSlot(uint128(Math.min((uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) / type()(uint256).max,premiumOwed.leftSlot())))) (contracts/PanopticPool.sol#1773-1794)
	- (LeftRightUnsigned.wrap(0).toRightSlot(uint128(Math.min((uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) / accumulated0,premiumOwed.rightSlot()))).toLeftSlot(uint128(Math.min((uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) / accumulated1,premiumOwed.leftSlot())))) (contracts/PanopticPool.sol#1773-1794)

/// @audit ************** Possible Issue Line(s) **************
	L#1768-1769,  L#1770-1771,  L#1773-1794,  

/// @audit ****************** Affected Code *******************
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

*GitHub* : [1757-1796](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1757-L1796)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) perform division which can not overflow (can use unchecked) :-
	- int24(Math.sort(ticks)[cardinality / 2]) (contracts/libraries/PanopticMath.sol#155)

/// @audit ************** Possible Issue Line(s) **************
	L#155,  

/// @audit ****************** Affected Code *******************
 155:             return int24(Math.sort(ticks)[cardinality / 2]);

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._checkLiquiditySpread(TokenId,uint256,int24,int24,uint64) (contracts/PanopticPool.sol#1465-1494) perform division which can not overflow (can use unchecked) :-
	- effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity (contracts/PanopticPool.sol#1487)

/// @audit ************** Possible Issue Line(s) **************
	L#1487,  

/// @audit ****************** Affected Code *******************
1487:             effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;

```

*GitHub* : [1465-1494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1465-L1494)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.startToken(bool,address,address,uint24,PanopticPool) (contracts/CollateralTracker.sol#221-264) perform division which can not overflow (can use unchecked) :-
	- _poolFee = fee / 100 (contracts/CollateralTracker.sol#249)
	- s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS) (contracts/CollateralTracker.sol#262)

/// @audit ************** Possible Issue Line(s) **************
	L#249,  L#262,  

/// @audit ****************** Affected Code *******************
 249:             _poolFee = fee / 100;
 262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

```

*GitHub* : [221-264](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221-L264)

### [G-04]<a name="g-04"></a> Use assembly to emit events

With the use of inline assembly in Solidity, we can take advantage of low-level features like scratch space and the free memory pointer, offering more gas-efficient ways of emitting events. The scratch space is a certain area of memory where we can temporarily store data, and the free memory pointer indicates the next available memory slot. Using these, we can efficiently assemble event data without incurring additional memory expansion costs. However, safety is paramount: to avoid overwriting or leakage, we must cache the free memory pointer before use and restore it afterward, ensuring that it points to the correct memory location post-operation.

*There are 25 instance(s) of this issue:*

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.deployNewPool(address,address,uint24,bytes32) (contracts/PanopticFactory.sol#210-276) should emit event(s) using assembly :-
	- PoolDeployed(newPoolContract,v3Pool,collateralTracker0,collateralTracker1,amount0,amount1) (contracts/PanopticFactory.sol#268-275)

/// @audit ************** Possible Issue Line(s) **************
	L#268-275,  

/// @audit ****************** Affected Code *******************
 268:         emit PoolDeployed(
 269:             newPoolContract,
 270:             v3Pool,
 271:             collateralTracker0,
 272:             collateralTracker1,
 273:             amount0,
 274:             amount1
 275:         );

```

*GitHub* : [210-276](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210-L276)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.setApprovalForAll(address,bool) (contracts/tokens/ERC1155Minimal.sol#81-85) should emit event(s) using assembly :-
	- ApprovalForAll(msg.sender,operator,approved) (contracts/tokens/ERC1155Minimal.sol#84)

/// @audit ************** Possible Issue Line(s) **************
	L#84,  

/// @audit ****************** Affected Code *******************
  81:     function setApprovalForAll(address operator, bool approved) public {
  82:         isApprovedForAll[msg.sender][operator] = approved;
  83: 
  84:         emit ApprovalForAll(msg.sender, operator, approved);
  85:     }

```

*GitHub* : [81-85](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L81-L85)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal._transferFrom(address,address,uint256) (contracts/tokens/ERC20Minimal.sol#103-113) should emit event(s) using assembly :-
	- Transfer(from,to,amount) (contracts/tokens/ERC20Minimal.sol#112)

/// @audit ************** Possible Issue Line(s) **************
	L#112,  

/// @audit ****************** Affected Code *******************
 103:     function _transferFrom(address from, address to, uint256 amount) internal {
 104:         balanceOf[from] -= amount;
 105: 
 106:         // Cannot overflow because the sum of all user
 107:         // balances can't exceed the max uint256 value.
 108:         unchecked {
 109:             balanceOf[to] += amount;
 110:         }
 111: 
 112:         emit Transfer(from, to, amount);
 113:     }

```

*GitHub* : [103-113](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L103-L113)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._burnOptions(bool,TokenId,address,int24,int24) (contracts/PanopticPool.sol#826-854) should emit event(s) using assembly :-
	- OptionBurnt(owner,positionSize,tokenId,premiaOwed) (contracts/PanopticPool.sol#853)

/// @audit ************** Possible Issue Line(s) **************
	L#853,  

/// @audit ****************** Affected Code *******************
 853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

```

*GitHub* : [826-854](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L826-L854)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.withdraw(uint256,address,address) (contracts/CollateralTracker.sol#531-566) should emit event(s) using assembly :-
	- Withdraw(msg.sender,receiver,owner,assets,shares) (contracts/CollateralTracker.sol#563)

/// @audit ************** Possible Issue Line(s) **************
	L#563,  

/// @audit ****************** Affected Code *******************
 563:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

```

*GitHub* : [531-566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L531-L566)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal.transfer(address,uint256) (contracts/tokens/ERC20Minimal.sol#61-73) should emit event(s) using assembly :-
	- Transfer(msg.sender,to,amount) (contracts/tokens/ERC20Minimal.sol#70)

/// @audit ************** Possible Issue Line(s) **************
	L#70,  

/// @audit ****************** Affected Code *******************
  61:     function transfer(address to, uint256 amount) public virtual returns (bool) {
  62:         balanceOf[msg.sender] -= amount;
  63: 
  64:         // Cannot overflow because the sum of all user
  65:         // balances can't exceed the max uint256 value.
  66:         unchecked {
  67:             balanceOf[to] += amount;
  68:         }
  69: 
  70:         emit Transfer(msg.sender, to, amount);
  71: 
  72:         return true;
  73:     }

```

*GitHub* : [61-73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L61-L73)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.transferOwnership(address) (contracts/PanopticFactory.sol#147-155) should emit event(s) using assembly :-
	- OwnershipTransferred(currentOwner,newOwner) (contracts/PanopticFactory.sol#154)

/// @audit ************** Possible Issue Line(s) **************
	L#154,  

/// @audit ****************** Affected Code *******************
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

*GitHub* : [147-155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147-L155)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal.transferFrom(address,address,uint256) (contracts/tokens/ERC20Minimal.sol#81-97) should emit event(s) using assembly :-
	- Transfer(from,to,amount) (contracts/tokens/ERC20Minimal.sol#94)

/// @audit ************** Possible Issue Line(s) **************
	L#94,  

/// @audit ****************** Affected Code *******************
  81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
  82:         uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.
  83: 
  84:         if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
  85: 
  86:         balanceOf[from] -= amount;
  87: 
  88:         // Cannot overflow because the sum of all user
  89:         // balances can't exceed the max uint256 value.
  90:         unchecked {
  91:             balanceOf[to] += amount;
  92:         }
  93: 
  94:         emit Transfer(from, to, amount);
  95: 
  96:         return true;
  97:     }

```

*GitHub* : [81-97](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L81-L97)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.redeem(uint256,address,address) (contracts/CollateralTracker.sol#591-626) should emit event(s) using assembly :-
	- Withdraw(msg.sender,receiver,owner,assets,shares) (contracts/CollateralTracker.sol#623)

/// @audit ************** Possible Issue Line(s) **************
	L#623,  

/// @audit ****************** Affected Code *******************
 623:         emit Withdraw(msg.sender, receiver, owner, assets, shares);

```

*GitHub* : [591-626](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L591-L626)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.deposit(uint256,address) (contracts/CollateralTracker.sol#417-440) should emit event(s) using assembly :-
	- Deposit(msg.sender,receiver,assets,shares) (contracts/CollateralTracker.sol#439)

/// @audit ************** Possible Issue Line(s) **************
	L#439,  

/// @audit ****************** Affected Code *******************
 417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
 418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();
 419: 
 420:         shares = previewDeposit(assets);
 421: 
 422:         // transfer assets (underlying token funds) from the user/the LP to the PanopticPool
 423:         // in return for the shares to be minted
 424:         SafeTransferLib.safeTransferFrom(
 425:             s_underlyingToken,
 426:             msg.sender,
 427:             address(s_panopticPool),
 428:             assets
 429:         );
 430: 
 431:         // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
 432:         _mint(receiver, shares);
 433: 
 434:         // update tracked asset balance
 435:         unchecked {
 436:             s_poolAssets += uint128(assets);
 437:         }
 438: 
 439:         emit Deposit(msg.sender, receiver, assets, shares);
 440:     }

```

*GitHub* : [417-440](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L417-L440)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal._burn(address,uint256) (contracts/tokens/ERC20Minimal.sol#136-146) should emit event(s) using assembly :-
	- Transfer(from,address(0),amount) (contracts/tokens/ERC20Minimal.sol#145)

/// @audit ************** Possible Issue Line(s) **************
	L#145,  

/// @audit ****************** Affected Code *******************
 136:     function _burn(address from, uint256 amount) internal {
 137:         balanceOf[from] -= amount;
 138: 
 139:         // Cannot underflow because a user's balance
 140:         // will never be larger than the total supply.
 141:         unchecked {
 142:             totalSupply -= amount;
 143:         }
 144: 
 145:         emit Transfer(from, address(0), amount);
 146:     }

```

*GitHub* : [136-146](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L136-L146)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155._mint(address,uint256,uint256) (contracts/tokens/ERC1155Minimal.sol#214-230) should emit event(s) using assembly :-
	- TransferSingle(msg.sender,address(0),to,id,amount) (contracts/tokens/ERC1155Minimal.sol#220)

/// @audit ************** Possible Issue Line(s) **************
	L#220,  

/// @audit ****************** Affected Code *******************
 214:     function _mint(address to, uint256 id, uint256 amount) internal {
 215:         // balance will never overflow
 216:         unchecked {
 217:             balanceOf[to][id] += amount;
 218:         }
 219: 
 220:         emit TransferSingle(msg.sender, address(0), to, id, amount);
 221: 
 222:         if (to.code.length != 0) {
 223:             if (
 224:                 ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
 225:                 ERC1155Holder.onERC1155Received.selector
 226:             ) {
 227:                 revert UnsafeRecipient();
 228:             }
 229:         }
 230:     }

```

*GitHub* : [214-230](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L214-L230)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) should emit event(s) using assembly :-
	- PremiumSettled(owner,tokenId,realizedPremia) (contracts/PanopticPool.sol#1654)

/// @audit ************** Possible Issue Line(s) **************
	L#1654,  

/// @audit ****************** Affected Code *******************
1654:             emit PremiumSettled(owner, tokenId, realizedPremia);

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155._burn(address,uint256,uint256) (contracts/tokens/ERC1155Minimal.sol#236-240) should emit event(s) using assembly :-
	- TransferSingle(msg.sender,from,address(0),id,amount) (contracts/tokens/ERC1155Minimal.sol#239)

/// @audit ************** Possible Issue Line(s) **************
	L#239,  

/// @audit ****************** Affected Code *******************
 236:     function _burn(address from, uint256 id, uint256 amount) internal {
 237:         balanceOf[from][id] -= amount;
 238: 
 239:         emit TransferSingle(msg.sender, from, address(0), id, amount);
 240:     }

```

*GitHub* : [236-240](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L236-L240)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278) should emit event(s) using assembly :-
	- ForcedExercised(msg.sender,account,touchedId[0],exerciseFees) (contracts/PanopticPool.sol#1277)

/// @audit ************** Possible Issue Line(s) **************
	L#1277,  

/// @audit ****************** Affected Code *******************
1277:         emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) should emit event(s) using assembly :-
	- AccountLiquidated(msg.sender,liquidatee,bonusAmounts) (contracts/PanopticPool.sol#1170)

/// @audit ************** Possible Issue Line(s) **************
	L#1170,  

/// @audit ****************** Affected Code *******************
1170:         emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.mintTokenizedPosition(TokenId,uint128,int24,int24) (contracts/SemiFungiblePositionManager.sol#504-527) should emit event(s) using assembly :-
	- TokenizedPositionMinted(msg.sender,tokenId,positionSize) (contracts/SemiFungiblePositionManager.sol#517)

/// @audit ************** Possible Issue Line(s) **************
	L#517,  

/// @audit ****************** Affected Code *******************
 504:     function mintTokenizedPosition(
 505:         TokenId tokenId,
 506:         uint128 positionSize,
 507:         int24 slippageTickLimitLow,
 508:         int24 slippageTickLimitHigh
 509:     )
 510:         external
 511:         ReentrancyLock(tokenId.poolId())
 512:         returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
 513:     {
 514:         // create the option position via its ID in this erc1155
 515:         _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);
 516: 
 517:         emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);
 518: 
 519:         // validate the incoming option position, then forward to the AMM for minting/burning required liquidity chunks
 520:         (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
 521:             tokenId,
 522:             positionSize,
 523:             slippageTickLimitLow,
 524:             slippageTickLimitHigh,
 525:             MINT
 526:         );
 527:     }

```

*GitHub* : [504-527](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L504-L527)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24) (contracts/PanopticPool.sol#614-667) should emit event(s) using assembly :-
	- OptionMinted(msg.sender,positionSize,tokenId,poolUtilizations) (contracts/PanopticPool.sol#666)

/// @audit ************** Possible Issue Line(s) **************
	L#666,  

/// @audit ****************** Affected Code *******************
 666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);

```

*GitHub* : [614-667](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L614-L667)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.mint(uint256,address) (contracts/CollateralTracker.sol#477-500) should emit event(s) using assembly :-
	- Deposit(msg.sender,receiver,assets,shares) (contracts/CollateralTracker.sol#499)

/// @audit ************** Possible Issue Line(s) **************
	L#499,  

/// @audit ****************** Affected Code *******************
 477:     function mint(uint256 shares, address receiver) external returns (uint256 assets) {
 478:         assets = previewMint(shares);
 479: 
 480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();
 481: 
 482:         // transfer assets (underlying token funds) from the user/the LP to the PanopticPool
 483:         // in return for the shares to be minted
 484:         SafeTransferLib.safeTransferFrom(
 485:             s_underlyingToken,
 486:             msg.sender,
 487:             address(s_panopticPool),
 488:             assets
 489:         );
 490: 
 491:         // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
 492:         _mint(receiver, shares);
 493: 
 494:         // update tracked asset balance
 495:         unchecked {
 496:             s_poolAssets += uint128(assets);
 497:         }
 498: 
 499:         emit Deposit(msg.sender, receiver, assets, shares);
 500:     }

```

*GitHub* : [477-500](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L477-L500)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes) (contracts/tokens/ERC1155Minimal.sol#94-120) should emit event(s) using assembly :-
	- TransferSingle(msg.sender,from,to,id,amount) (contracts/tokens/ERC1155Minimal.sol#110)

/// @audit ************** Possible Issue Line(s) **************
	L#110,  

/// @audit ****************** Affected Code *******************
 110:         emit TransferSingle(msg.sender, from, to, id, amount);

```

*GitHub* : [94-120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L94-L120)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.burnTokenizedPosition(TokenId,uint128,int24,int24) (contracts/SemiFungiblePositionManager.sol#471-495) should emit event(s) using assembly :-
	- TokenizedPositionBurnt(msg.sender,tokenId,positionSize) (contracts/SemiFungiblePositionManager.sol#485)

/// @audit ************** Possible Issue Line(s) **************
	L#485,  

/// @audit ****************** Affected Code *******************
 471:     function burnTokenizedPosition(
 472:         TokenId tokenId,
 473:         uint128 positionSize,
 474:         int24 slippageTickLimitLow,
 475:         int24 slippageTickLimitHigh
 476:     )
 477:         external
 478:         ReentrancyLock(tokenId.poolId())
 479:         returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
 480:     {
 481:         // burn this ERC1155 token id
 482:         _burn(msg.sender, TokenId.unwrap(tokenId), positionSize);
 483: 
 484:         // emit event
 485:         emit TokenizedPositionBurnt(msg.sender, tokenId, positionSize);
 486: 
 487:         // Call a function that contains other functions to mint/burn position, collect amounts, swap if necessary
 488:         (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
 489:             tokenId,
 490:             positionSize,
 491:             slippageTickLimitLow,
 492:             slippageTickLimitHigh,
 493:             BURN
 494:         );
 495:     }

```

*GitHub* : [471-495](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L471-L495)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/tokens/ERC1155Minimal.sol#130-171) should emit event(s) using assembly :-
	- TransferBatch(msg.sender,from,to,ids,amounts) (contracts/tokens/ERC1155Minimal.sol#161)

/// @audit ************** Possible Issue Line(s) **************
	L#161,  

/// @audit ****************** Affected Code *******************
 161:         emit TransferBatch(msg.sender, from, to, ids, amounts);

```

*GitHub* : [130-171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L130-L171)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal.approve(address,uint256) (contracts/tokens/ERC20Minimal.sol#49-55) should emit event(s) using assembly :-
	- Approval(msg.sender,spender,amount) (contracts/tokens/ERC20Minimal.sol#52)

/// @audit ************** Possible Issue Line(s) **************
	L#52,  

/// @audit ****************** Affected Code *******************
  49:     function approve(address spender, uint256 amount) public returns (bool) {
  50:         allowance[msg.sender][spender] = amount;
  51: 
  52:         emit Approval(msg.sender, spender, amount);
  53: 
  54:         return true;
  55:     }

```

*GitHub* : [49-55](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L49-L55)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.initializeAMMPool(address,address,uint24) (contracts/SemiFungiblePositionManager.sol#350-391) should emit event(s) using assembly :-
	- PoolInitialized(univ3pool,poolId) (contracts/SemiFungiblePositionManager.sol#390)

/// @audit ************** Possible Issue Line(s) **************
	L#390,  

/// @audit ****************** Affected Code *******************
 390:         emit PoolInitialized(univ3pool, poolId);

```

*GitHub* : [350-391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350-L391)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal._mint(address,uint256) (contracts/tokens/ERC20Minimal.sol#122-131) should emit event(s) using assembly :-
	- Transfer(address(0),to,amount) (contracts/tokens/ERC20Minimal.sol#130)

/// @audit ************** Possible Issue Line(s) **************
	L#130,  

/// @audit ****************** Affected Code *******************
 122:     function _mint(address to, uint256 amount) internal {
 123:         // Cannot overflow because the sum of all user
 124:         // balances can't exceed the max uint256 value.
 125:         unchecked {
 126:             balanceOf[to] += amount;
 127:         }
 128:         totalSupply += amount;
 129: 
 130:         emit Transfer(address(0), to, amount);
 131:     }

```

*GitHub* : [122-131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L122-L131)

### [G-05]<a name="g-05"></a> Emit event in setter function only if the state variable was changed

Emitting events in setter functions of smart contracts only when state variables change saves gas. This is because emitting events consumes gas, and unnecessary events, where no actual state change occurs, lead to wasteful consumption.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.setApprovalForAll(address,bool) (contracts/tokens/ERC1155Minimal.sol#81-85) should emit event only if state variable(s) changed :-
	- ApprovalForAll(msg.sender,operator,approved) (contracts/tokens/ERC1155Minimal.sol#84)

/// @audit ************** Possible Issue Line(s) **************
	L#84,  

/// @audit ****************** Affected Code *******************
  81:     function setApprovalForAll(address operator, bool approved) public {
  82:         isApprovedForAll[msg.sender][operator] = approved;
  83: 
  84:         emit ApprovalForAll(msg.sender, operator, approved);
  85:     }

```

*GitHub* : [81-85](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L81-L85)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) should emit event only if state variable(s) changed :-
	- PremiumSettled(owner,tokenId,realizedPremia) (contracts/PanopticPool.sol#1654)

/// @audit ************** Possible Issue Line(s) **************
	L#1654,  

/// @audit ****************** Affected Code *******************
1654:             emit PremiumSettled(owner, tokenId, realizedPremia);

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587-L1659)

### [G-06]<a name="g-06"></a> Use nested if to save gas

Using nested `if` statements instead of logical AND (`&&`) operators can potentially save gas in Solidity contracts. When a series of conditions are connected with `&&`, all conditions must be evaluated even if the first one fails. In contrast, nested `if` statements allow for short-circuiting; if the first condition fails, the rest are skipped, saving gas. This approach is more gas-efficient, especially when dealing with complex or gas-intensive conditions. However, it's crucial to balance gas savings with code readability and maintainability, ensuring that the code remains clear and easy to understand.

*There are 10 instance(s) of this issue:*

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned) (contracts/SemiFungiblePositionManager.sol#756-852) has IF statement with && (logical AND):-
	- (itm0 != 0) && (itm1 != 0) (contracts/SemiFungiblePositionManager.sol#787)

/// @audit ************** Possible Issue Line(s) **************
	L#787,  

/// @audit ****************** Affected Code *******************
 787:             if ((itm0 != 0) && (itm1 != 0)) {

```

*GitHub* : [756-852](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L756-L852)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.deployNewPool(address,address,uint24,bytes32) (contracts/PanopticFactory.sol#210-276) has IF statement with && (logical AND):-
	- _owner != address(0) && _owner != msg.sender (contracts/PanopticFactory.sol#224)

/// @audit ************** Possible Issue Line(s) **************
	L#224,  

/// @audit ****************** Affected Code *******************
 224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

```

*GitHub* : [210-276](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210-L276)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned) (contracts/libraries/PanopticMath.sol#651-754) has IF statement with && (logical AND):-
	- ! (paid0 > balance0 && paid1 > balance1) (contracts/libraries/PanopticMath.sol#704)

/// @audit ************** Possible Issue Line(s) **************
	L#704,  

/// @audit ****************** Affected Code *******************
 704:             if (!(paid0 > balance0 && paid1 > balance1)) {

```

*GitHub* : [651-754](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L651-L754)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) has IF statement with && (logical AND):-
	- longPremium.rightSlot() < collateralDelta0 && longPremium.leftSlot() > collateralDelta1 (contracts/libraries/PanopticMath.sol#798-799)
	- longPremium.leftSlot() < collateralDelta1 && longPremium.rightSlot() > collateralDelta0 (contracts/libraries/PanopticMath.sol#822-823)

/// @audit ************** Possible Issue Line(s) **************
	L#798-799,  L#822-823,  

/// @audit ****************** Affected Code *******************
 798:                 longPremium.rightSlot() < collateralDelta0 &&
 799:                 longPremium.leftSlot() > collateralDelta1
 822:                 longPremium.leftSlot() < collateralDelta1 &&
 823:                 longPremium.rightSlot() > collateralDelta0

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exercise(address,int128,int128,int128,int128) (contracts/CollateralTracker.sol#1043-1089) has IF statement with && (logical AND):-
	- (intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0)) (contracts/CollateralTracker.sol#1060)

/// @audit ************** Possible Issue Line(s) **************
	L#1060,  

/// @audit ****************** Affected Code *******************
1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

```

*GitHub* : [1043-1089](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043-L1089)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) has IF statement with && (logical AND):-
	- (below) && (lastObservedTick > entry) (contracts/libraries/PanopticMath.sol#218)

/// @audit ************** Possible Issue Line(s) **************
	L#218,  

/// @audit ****************** Affected Code *******************
 218:                     if ((below) && (lastObservedTick > entry)) {

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._calculateAccumulatedPremia(address,TokenId[],bool,bool,int24) (contracts/PanopticPool.sol#429-492) has IF statement with && (logical AND):-
	- tokenId.isLong(leg) == 0 && ! includePendingPremium (contracts/PanopticPool.sol#460)

/// @audit ************** Possible Issue Line(s) **************
	L#460,  

/// @audit ****************** Affected Code *******************
 460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

```

*GitHub* : [429-492](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L429-L492)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.validate(TokenId) (contracts/types/TokenId.sol#500-571) has IF statement with && (logical AND):-
	- (_isLong == isLongP) && (_tokenType == tokenTypeP) (contracts/types/TokenId.sol#560)
	- ((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP) (contracts/types/TokenId.sol#566)

/// @audit ************** Possible Issue Line(s) **************
	L#560,  L#566,  

/// @audit ****************** Affected Code *******************
 560:                     if ((_isLong == isLongP) && (_tokenType == tokenTypeP))
 566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

```

*GitHub* : [500-571](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L500-L571)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1311-1422) has IF statement with && (logical AND):-
	- ((atTick >= tickUpper) && (tokenType == 1)) || ((atTick < tickLower) && (tokenType == 0)) (contracts/CollateralTracker.sol#1346-1347)
	- ((atTick < tickLower) && (tokenType == 1)) || ((atTick >= tickUpper) && (tokenType == 0)) (contracts/CollateralTracker.sol#1374-1375)

/// @audit ************** Possible Issue Line(s) **************
	L#1346-1347,  L#1374-1375,  

/// @audit ****************** Affected Code *******************
1346:                     ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1
1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0
1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1
1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

```

*GitHub* : [1311-1422](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1311-L1422)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned) (contracts/CollateralTracker.sol#650-734) has IF statement with && (logical AND):-
	- (tokenType == 0 && currentValue1 < oracleValue1) || (tokenType == 1 && currentValue0 < oracleValue0) (contracts/CollateralTracker.sol#708-709)

/// @audit ************** Possible Issue Line(s) **************
	L#708-709,  

/// @audit ****************** Affected Code *******************
 708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||
 709:                     (tokenType == 1 && currentValue0 < oracleValue0)

```

*GitHub* : [650-734](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L650-L734)

### [G-07]<a name="g-07"></a> Internal or Private Function can be Inlined to Save Gas

Setting the internal/private function that called once to inline would save gas.

*There are 5 instance(s) of this issue:*

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math (contracts/libraries/Math.sol#13-782) may make following functions inline :- 
	- Math.getAmount0ForLiquidity(LiquidityChunk) (contracts/libraries/Math.sol#191-202)
	- Math.getAmount1ForLiquidity(LiquidityChunk) (contracts/libraries/Math.sol#207-214)
	- Math.mulDiv128(uint256,uint256) (contracts/libraries/Math.sol#598-655)

/// @audit ************** Possible Issue Line(s) **************
	L#191-202,  L#207-214,  L#598-655,  

/// @audit ****************** Affected Code *******************
 191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
 192:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
 193:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());
 194:         unchecked {
 195:             return
 196:                 mulDiv(
 197:                     uint256(liquidityChunk.liquidity()) << 96,
 198:                     highPriceX96 - lowPriceX96,
 199:                     highPriceX96
 200:                 ) / lowPriceX96;
 201:         }
 202:     }
 207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
 208:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
 209:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());
 210: 
 211:         unchecked {
 212:             return mulDiv96(liquidityChunk.liquidity(), highPriceX96 - lowPriceX96);
 213:         }
 214:     }
 598:     function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {
 599:         unchecked {
 600:             // 512-bit multiply [prod1 prod0] = a * b
 601:             // Compute the product mod 2**256 and mod 2**256 - 1
 602:             // then use the Chinese Remainder Theorem to reconstruct
 603:             // the 512 bit result. The result is stored in two 256
 604:             // variables such that product = prod1 * 2**256 + prod0
 605:             uint256 prod0; // Least significant 256 bits of the product
 606:             uint256 prod1; // Most significant 256 bits of the product
 607:             assembly ("memory-safe") {
 608:                 let mm := mulmod(a, b, not(0))
 609:                 prod0 := mul(a, b)
 610:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
 611:             }
 612: 
 613:             // Handle non-overflow cases, 256 by 256 division
 614:             if (prod1 == 0) {
 615:                 uint256 res;
 616:                 assembly ("memory-safe") {
 617:                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 618:                     res := shr(128, prod0)
 619:                 }
 620:                 return res;
 621:             }
 622: 
 623:             // Make sure the result is less than 2**256.
 624:             require(2 ** 128 > prod1);
 625: 
 626:             ///////////////////////////////////////////////
 627:             // 512 by 256 division.
 628:             ///////////////////////////////////////////////
 629: 
 630:             // Make division exact by subtracting the remainder from [prod1 prod0]
 631:             // Compute remainder using mulmod
 632:             uint256 remainder;
 633:             assembly ("memory-safe") {
 634:                 remainder := mulmod(a, b, 0x100000000000000000000000000000000)
 635:             }
 636:             // Subtract 256 bit number from 512 bit number
 637:             assembly ("memory-safe") {
 638:                 prod1 := sub(prod1, gt(remainder, prod0))
 639:                 prod0 := sub(prod0, remainder)
 640:             }
 641: 
 642:             // Divide [prod1 prod0] by the factors of two (note that this is just 2**128 since the denominator is a power of 2 itself)
 643:             assembly ("memory-safe") {
 644:                 // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 645:                 prod0 := shr(128, prod0)
 646:             }
 647:             // Shift in bits from prod1 into prod0. For this we need
 648:             // to flip `twos` such that it is 2**256 / twos.
 649:             // If twos is zero, then it becomes one
 650:             // Note that this is just 2**160 since 2**256 over the fixed denominator (2**128) equals 2**128
 651:             prod0 |= prod1 * 2 ** 128;
 652: 
 653:             return prod0;
 654:         }
 655:     }

```

*GitHub* : [13-782](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L13-L782)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc (contracts/libraries/FeesCalc.sol#39-209) may make following functions inline :- 
	- FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24) (contracts/libraries/FeesCalc.sol#130-208)

/// @audit ************** Possible Issue Line(s) **************
	L#130-208,  

/// @audit ****************** Affected Code *******************
 130:     function _getAMMSwapFeesPerLiquidityCollected(
 131:         IUniswapV3Pool univ3pool,
 132:         int24 currentTick,
 133:         int24 tickLower,
 134:         int24 tickUpper
 135:     ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
 136:         // Get feesGrowths from the option position's lower+upper ticks
 137:         // lowerOut0: For token0: fee growth per unit of liquidity on the _other_ side of tickLower (relative to currentTick)
 138:         // only has relative meaning, not absolute — the value depends on when the tick is initialized
 139:         // (...)
 140:         // upperOut1: For token1: fee growth on the _other_ side of tickUpper (again: relative to currentTick)
 141:         // the point is: the range covered by lowerOut0 changes depending on where currentTick is.
 142:         (, , uint256 lowerOut0, uint256 lowerOut1, , , , ) = univ3pool.ticks(tickLower);
 143:         (, , uint256 upperOut0, uint256 upperOut1, , , , ) = univ3pool.ticks(tickUpper);
 144: 
 145:         // compute the effective feeGrowth, depending on whether price is above/below/within range
 146:         unchecked {
 147:             if (currentTick < tickLower) {
 148:                 /**
 149:                   Diagrams shown for token0, and applies for token1 the same
 150:                   L = lowerTick, U = upperTick
 151: 
 152:                     liquidity         lowerOut0 (all fees collected in this price tick range for token0)
 153:                         ▲            ◄──────────────^v───► (to MAX_TICK)
 154:                         │
 155:                         │                      upperOut0
 156:                         │                     ◄─────^v───►
 157:                         │           ┌────────┐
 158:                         │           │ chunk  │
 159:                         │           │        │
 160:                         └─────▲─────┴────────┴────────► price tick
 161:                               │     L        U
 162:                               │
 163:                            current
 164:                             tick
 165:                 */
 166:                 feeGrowthInside0X128 = lowerOut0 - upperOut0; // fee growth inside the chunk
 167:                 feeGrowthInside1X128 = lowerOut1 - upperOut1;
 168:             } else if (currentTick >= tickUpper) {
 169:                 /**
 170:                     liquidity
 171:                         ▲           upperOut0
 172:                         │◄─^v─────────────────────►
 173:                         │     
 174:                         │     lowerOut0  ┌────────┐
 175:                         │◄─^v───────────►│ chunk  │
 176:                         │                │        │
 177:                         └────────────────┴────────┴─▲─────► price tick
 178:                                          L        U │
 179:                                                     │
 180:                                                  current
 181:                                                   tick
 182:                  */
 183:                 feeGrowthInside0X128 = upperOut0 - lowerOut0;
 184:                 feeGrowthInside1X128 = upperOut1 - lowerOut1;
 185:             } else {
 186:                 /**
 187:                   current AMM tick is within the option position range (within the chunk)
 188: 
 189:                      liquidity
 190:                         ▲        feeGrowthGlobal0X128 = global fee growth
 191:                         │                             = (all fees collected for the entire price range for token 0)
 192:                         │
 193:                         │                        
 194:                         │     lowerOut0  ┌──────────────┐ upperOut0
 195:                         │◄─^v───────────►│              │◄─────^v───►
 196:                         │                │     chunk    │
 197:                         │                │              │
 198:                         └────────────────┴───────▲──────┴─────► price tick
 199:                                          L       │      U
 200:                                                  │
 201:                                               current
 202:                                                tick
 203:                 */
 204:                 feeGrowthInside0X128 = univ3pool.feeGrowthGlobal0X128() - lowerOut0 - upperOut0;
 205:                 feeGrowthInside1X128 = univ3pool.feeGrowthGlobal1X128() - lowerOut1 - upperOut1;
 206:             }
 207:         }
 208:     }

```

*GitHub* : [39-209](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L39-L209)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath (contracts/libraries/PanopticMath.sol#18-967) may make following functions inline :- 
	- PanopticMath.getRangesFromStrike(int24,int24) (contracts/libraries/PanopticMath.sol#371-379)
	- PanopticMath._calculateIOAmounts(TokenId,uint128,uint256) (contracts/libraries/PanopticMath.sol#607-635)
	- PanopticMath.getAmountsMoved(TokenId,uint128,uint256) (contracts/libraries/PanopticMath.sol#574-599)

/// @audit ************** Possible Issue Line(s) **************
	L#371-379,  L#607-635,  L#574-599,  

/// @audit ****************** Affected Code *******************
 371:     function getRangesFromStrike(
 372:         int24 width,
 373:         int24 tickSpacing
 374:     ) internal pure returns (int24, int24) {
 375:         return (
 376:             (width * tickSpacing) / 2,
 377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))
 378:         );
 379:     }
 574:     function getAmountsMoved(
 575:         TokenId tokenId,
 576:         uint128 positionSize,
 577:         uint256 legIndex
 578:     ) internal pure returns (LeftRightUnsigned) {
 579:         // get the tick range for this leg in order to get the strike price (the underlying price)
 580:         (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);
 581: 
 582:         uint128 amount0;
 583:         uint128 amount1;
 584:         if (tokenId.asset(legIndex) == 0) {
 585:             amount0 = positionSize * uint128(tokenId.optionRatio(legIndex));
 586: 
 587:             amount1 = Math
 588:                 .getAmount1ForLiquidity(Math.getLiquidityForAmount0(tickLower, tickUpper, amount0))
 589:                 .toUint128();
 590:         } else {
 591:             amount1 = positionSize * uint128(tokenId.optionRatio(legIndex));
 592: 
 593:             amount0 = Math
 594:                 .getAmount0ForLiquidity(Math.getLiquidityForAmount1(tickLower, tickUpper, amount1))
 595:                 .toUint128();
 596:         }
 597: 
 598:         return LeftRightUnsigned.wrap(0).toRightSlot(amount0).toLeftSlot(amount1);
 599:     }
 607:     function _calculateIOAmounts(
 608:         TokenId tokenId,
 609:         uint128 positionSize,
 610:         uint256 legIndex
 611:     ) internal pure returns (LeftRightSigned longs, LeftRightSigned shorts) {
 612:         // compute amounts moved
 613:         LeftRightUnsigned amountsMoved = getAmountsMoved(tokenId, positionSize, legIndex);
 614: 
 615:         bool isShort = tokenId.isLong(legIndex) == 0;
 616: 
 617:         // if token0
 618:         if (tokenId.tokenType(legIndex) == 0) {
 619:             if (isShort) {
 620:                 // if option is short, increment shorts by contracts
 621:                 shorts = shorts.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));
 622:             } else {
 623:                 // is option is long, increment longs by contracts
 624:                 longs = longs.toRightSlot(Math.toInt128(amountsMoved.rightSlot()));
 625:             }
 626:         } else {
 627:             if (isShort) {
 628:                 // if option is short, increment shorts by notional
 629:                 shorts = shorts.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));
 630:             } else {
 631:                 // if option is long, increment longs by notional
 632:                 longs = longs.toLeftSlot(Math.toInt128(amountsMoved.leftSlot()));
 633:             }
 634:         }
 635:     }

```

*GitHub* : [18-967](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L18-L967)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary (contracts/types/TokenId.sol#60-600) may make following functions inline :- 
	- TokenIdLibrary.addStrike(TokenId,int24,uint256) (contracts/types/TokenId.sol#291-303)
	- TokenIdLibrary.addIsLong(TokenId,uint256,uint256) (contracts/types/TokenId.sol#240-248)
	- TokenIdLibrary.addWidth(TokenId,int24,uint256) (contracts/types/TokenId.sol#310-323)
	- TokenIdLibrary.addTokenType(TokenId,uint256,uint256) (contracts/types/TokenId.sol#255-266)
	- TokenIdLibrary.addAsset(TokenId,uint256,uint256) (contracts/types/TokenId.sol#205-214)
	- TokenIdLibrary.addRiskPartner(TokenId,uint256,uint256) (contracts/types/TokenId.sol#273-284)
	- TokenIdLibrary.addOptionRatio(TokenId,uint256,uint256) (contracts/types/TokenId.sol#221-232)

/// @audit ************** Possible Issue Line(s) **************
	L#291-303,  L#240-248,  L#310-323,  L#255-266,  L#205-214,  L#273-284,  L#221-232,  

/// @audit ****************** Affected Code *******************
 205:     function addAsset(
 206:         TokenId self,
 207:         uint256 _asset,
 208:         uint256 legIndex
 209:     ) internal pure returns (TokenId) {
 210:         unchecked {
 211:             return
 212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));
 213:         }
 214:     }
 221:     function addOptionRatio(
 222:         TokenId self,
 223:         uint256 _optionRatio,
 224:         uint256 legIndex
 225:     ) internal pure returns (TokenId) {
 226:         unchecked {
 227:             return
 228:                 TokenId.wrap(
 229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))
 230:                 );
 231:         }
 232:     }
 240:     function addIsLong(
 241:         TokenId self,
 242:         uint256 _isLong,
 243:         uint256 legIndex
 244:     ) internal pure returns (TokenId) {
 245:         unchecked {
 246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));
 247:         }
 248:     }
 255:     function addTokenType(
 256:         TokenId self,
 257:         uint256 _tokenType,
 258:         uint256 legIndex
 259:     ) internal pure returns (TokenId) {
 260:         unchecked {
 261:             return
 262:                 TokenId.wrap(
 263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))
 264:                 );
 265:         }
 266:     }
 273:     function addRiskPartner(
 274:         TokenId self,
 275:         uint256 _riskPartner,
 276:         uint256 legIndex
 277:     ) internal pure returns (TokenId) {
 278:         unchecked {
 279:             return
 280:                 TokenId.wrap(
 281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))
 282:                 );
 283:         }
 284:     }
 291:     function addStrike(
 292:         TokenId self,
 293:         int24 _strike,
 294:         uint256 legIndex
 295:     ) internal pure returns (TokenId) {
 296:         unchecked {
 297:             return
 298:                 TokenId.wrap(
 299:                     TokenId.unwrap(self) +
 300:                         uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))
 301:                 );
 302:         }
 303:     }
 310:     function addWidth(
 311:         TokenId self,
 312:         int24 _width,
 313:         uint256 legIndex
 314:     ) internal pure returns (TokenId) {
 315:         // % 4096 -> take 12 bits from the incoming 24 bits (there's no uint12)
 316:         unchecked {
 317:             return
 318:                 TokenId.wrap(
 319:                     TokenId.unwrap(self) +
 320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))
 321:                 );
 322:         }
 323:     }

```

*GitHub* : [60-600](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L60-L600)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker (contracts/CollateralTracker.sol#36-1650) may make following functions inline :- 
	- CollateralTracker._getExchangedAmount(int128,int128,int128) (contracts/CollateralTracker.sol#1096-1126)
	- CollateralTracker._getAccountMargin(address,int24,uint256[2][],int128) (contracts/CollateralTracker.sol#1159-1193)
	- CollateralTracker._getTotalRequiredCollateral(int24,uint256[2][]) (contracts/CollateralTracker.sol#1200-1236)
	- CollateralTracker._getRequiredCollateralAtTickSinglePosition(TokenId,uint128,int24,uint128) (contracts/CollateralTracker.sol#1245-1268)
	- CollateralTracker._getRequiredCollateralSingleLeg(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1278-1301)
	- CollateralTracker._getRequiredCollateralSingleLegPartner(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1439-1464)
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128) (contracts/CollateralTracker.sol#1510-1589)
	- CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1600-1649)
	- CollateralTracker._sellCollateralRatio(int256) (contracts/CollateralTracker.sol#751-800)
	- CollateralTracker._buyCollateralRatio(uint256) (contracts/CollateralTracker.sol#806-853)

/// @audit ************** Possible Issue Line(s) **************
	L#1096-1126,  L#1159-1193,  L#1200-1236,  L#1245-1268,  L#1278-1301,  L#1439-1464,  L#1510-1589,  L#1600-1649,  L#751-800,  L#806-853,  

/// @audit ****************** Affected Code *******************
 751:     function _sellCollateralRatio(
 752:         int256 utilization
 753:     ) internal view returns (uint256 sellCollateralRatio) {
 754:         // the sell ratio is on a straight line defined between two points (x0,y0) and (x1,y1):
 755:         //   (x0,y0) = (targetPoolUtilization,min_sell_ratio) and
 756:         //   (x1,y1) = (saturatedPoolUtilization,max_sell_ratio)
 757:         // the line's formula: y = a * (x - x0) + y0, where a = (y1 - y0) / (x1 - x0)
 758:         /**
 759:             SELL
 760:             COLLATERAL
 761:             RATIO
 762:                           ^
 763:                           |                  max ratio = 100%
 764:                    100% - |                _------
 765:                           |             _-¯
 766:                           |          _-¯
 767:                     20% - |---------¯
 768:                           |         .       . .
 769:                           +---------+-------+-+--->   POOL_
 770:                                    50%    90% 100%     UTILIZATION
 771:         */
 772: 
 773:         uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;
 774:         /// if utilization is less than zero, this is the calculation for a strangle, which gets 2x the capital efficiency at low pool utilization
 775:         /// at 0% utilization, strangle legs do not compound efficiency
 776:         if (utilization < 0) {
 777:             unchecked {
 778:                 min_sell_ratio /= 2;
 779:                 utilization = -utilization;
 780:             }
 781:         }
 782: 
 783:         // return the basal sell ratio if pool utilization is lower than target
 784:         if (uint256(utilization) < TARGET_POOL_UTIL) {
 785:             return min_sell_ratio;
 786:         }
 787: 
 788:         // return 100% collateral ratio if utilization is above saturated pool utilization
 789:         // this means all new positions are fully collateralized, which reduces risks of insolvency at high pool utilization
 790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {
 791:             return DECIMALS;
 792:         }
 793: 
 794:         unchecked {
 795:             return
 796:                 min_sell_ratio +
 797:                 ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
 798:                 (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);
 799:         }
 800:     }
 806:     function _buyCollateralRatio(
 807:         uint256 utilization
 808:     ) internal view returns (uint256 buyCollateralRatio) {
 809:         // linear from BUY to BUY/2 between 50% and 90%
 810:         // the buy ratio is on a straight line defined between two points (x0,y0) and (x1,y1):
 811:         //   (x0,y0) = (targetPoolUtilization,buyCollateralRatio) and
 812:         //   (x1,y1) = (saturatedPoolUtilization,buyCollateralRatio / 2)
 813:         // note that y1<y0 so the slope is negative:
 814:         // aka the buy ratio starts high and drops to a lower value with increased utilization; the sell ratio does the opposite (slope is positive)
 815:         // the line's formula: y = a * (x - x0) + y0, where a = (y1 - y0) / (x1 - x0)
 816:         // but since a<0, we rewrite as:
 817:         // y = a' * (x0 - x) + y0, where a' = (y0 - y1) / (x1 - x0)
 818: 
 819:         // HOWEVER, if the utilization is larger than 10_000, then default to 100% buying power requirement.
 820:         // this denotes a situation where the median is too far away from the current price, so we need to require fully collateralized positions for safety
 821:         /**
 822:           BUY
 823:           COLLATERAL
 824:           RATIO
 825:                  ^
 826:                  |   buy_ratio = 10%
 827:            10% - |----------__       min_ratio = 5%
 828:            5%  - | . . . . .  ¯¯¯--______
 829:                  |         .       . .
 830:                  +---------+-------+-+--->   POOL_
 831:                           50%    90% 100%      UTILIZATION
 832:          */
 833: 
 834:         // return the basal buy ratio if pool utilization is lower than target
 835:         if (utilization < TARGET_POOL_UTIL) {
 836:             return BUYER_COLLATERAL_RATIO;
 837:         }
 838: 
 839:         // return the basal ratio divided by 2 if pool utilization is above saturated pool utilization
 840:         /// this is incentivized buying, which returns funds to the panoptic pool
 841:         if (utilization > SATURATED_POOL_UTIL) {
 842:             unchecked {
 843:                 return BUYER_COLLATERAL_RATIO / 2;
 844:             }
 845:         }
 846: 
 847:         unchecked {
 848:             return
 849:                 (BUYER_COLLATERAL_RATIO +
 850:                     (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
 851:                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2
 852:         }
 853:     }
1096:     function _getExchangedAmount(
1097:         int128 longAmount,
1098:         int128 shortAmount,
1099:         int128 swappedAmount
1100:     ) internal view returns (int256 exchangedAmount) {
1101:         // If amount swapped is positive, the amount of tokens to pay is the ITM amount
1102: 
1103:         unchecked {
1104:             // intrinsic value is the amount that need to be exchanged due to minting in-the-money
1105:             int256 intrinsicValue = swappedAmount - (shortAmount - longAmount);
1106: 
1107:             if (intrinsicValue != 0) {
1108:                 // the swap commission is paid on the intrinsic value, and it is always positive
1109:                 uint256 swapCommission = Math.unsafeDivRoundingUp(
1110:                     s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),
1111:                     DECIMALS
1112:                 );
1113: 
1114:                 // set the exchanged amount to the sum of the intrinsic value and swapCommission
1115:                 exchangedAmount = intrinsicValue + int256(swapCommission);
1116:             }
1117: 
1118:             //compute total commission amount = commission rate + spread fee
1119:             exchangedAmount += int256(
1120:                 Math.unsafeDivRoundingUp(
1121:                     uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
1122:                     DECIMALS
1123:                 )
1124:             );
1125:         }
1126:     }
1159:     function _getAccountMargin(
1160:         address user,
1161:         int24 atTick,
1162:         uint256[2][] memory positionBalanceArray,
1163:         int128 premiumAllPositions
1164:     ) internal view returns (LeftRightUnsigned tokenData) {
1165:         uint256 tokenRequired;
1166: 
1167:         // if the account has active options, compute the required collateral to keep account in good health
1168:         if (positionBalanceArray.length > 0) {
1169:             // get all collateral required for the incoming list of positions
1170:             tokenRequired = _getTotalRequiredCollateral(atTick, positionBalanceArray);
1171: 
1172:             // If premium is negative (ie. user has to pay for their purchased options), add this long premium to the token requirement
1173:             if (premiumAllPositions < 0) {
1174:                 unchecked {
1175:                     tokenRequired += uint128(-premiumAllPositions);
1176:                 }
1177:             }
1178:         }
1179: 
1180:         // if premium is positive (ie. user will receive funds due to selling options), add this premum to the user's balance
1181:         uint256 netBalance = convertToAssets(balanceOf[user]);
1182:         if (premiumAllPositions > 0) {
1183:             unchecked {
1184:                 netBalance += uint256(uint128(premiumAllPositions));
1185:             }
1186:         }
1187: 
1188:         // store assetBalance and tokens required in tokenData variable
1189:         tokenData = tokenData.toRightSlot(netBalance.toUint128()).toLeftSlot(
1190:             tokenRequired.toUint128()
1191:         );
1192:         return tokenData;
1193:     }
1200:     function _getTotalRequiredCollateral(
1201:         int24 atTick,
1202:         uint256[2][] memory positionBalanceArray
1203:     ) internal view returns (uint256 tokenRequired) {
1204:         // loop through each active position.
1205:         // Offset determined whether to consider the last tokenId from the list
1206:         // (a potentially newly minted position)
1207:         uint256 totalIterations = positionBalanceArray.length;
1208:         for (uint256 i = 0; i < totalIterations; ) {
1209:             // read the ith tokenId from the account
1210:             TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);
1211: 
1212:             // read the position size and the pool utilization at mint
1213:             uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();
1214: 
1215:             // read the pool utilization at mint
1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();
1217: 
1218:             // Get tokens required for the current tokenId (a single active position)
1219:             uint256 _tokenRequired = _getRequiredCollateralAtTickSinglePosition(
1220:                 tokenId,
1221:                 positionSize,
1222:                 atTick,
1223:                 poolUtilization
1224:             );
1225: 
1226:             // add to the tokenRequired accumulator
1227:             unchecked {
1228:                 tokenRequired += _tokenRequired;
1229:             }
1230:             unchecked {
1231:                 ++i;
1232:             }
1233:         }
1234: 
1235:         return tokenRequired;
1236:     }
1245:     function _getRequiredCollateralAtTickSinglePosition(
1246:         TokenId tokenId,
1247:         uint128 positionSize,
1248:         int24 atTick,
1249:         uint128 poolUtilization
1250:     ) internal view returns (uint256 tokenRequired) {
1251:         bool underlyingIsToken0 = s_underlyingIsToken0;
1252:         uint256 numLegs = tokenId.countLegs();
1253: 
1254:         unchecked {
1255:             for (uint256 index = 0; index < numLegs; ++index) {
1256:                 // revert if the tokenType does not match the current collateral token
1257:                 if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;
1258:                 // Increment the tokenRequired accumulator
1259:                 tokenRequired += _getRequiredCollateralSingleLeg(
1260:                     tokenId,
1261:                     index,
1262:                     positionSize,
1263:                     atTick,
1264:                     poolUtilization
1265:                 );
1266:             }
1267:         }
1268:     }
1278:     function _getRequiredCollateralSingleLeg(
1279:         TokenId tokenId,
1280:         uint256 index,
1281:         uint128 positionSize,
1282:         int24 atTick,
1283:         uint128 poolUtilization
1284:     ) internal view returns (uint256 required) {
1285:         return
1286:             tokenId.riskPartner(index) == index // does this leg have a risk partner? Affects required collateral
1287:                 ? _getRequiredCollateralSingleLegNoPartner(
1288:                     tokenId,
1289:                     index,
1290:                     positionSize,
1291:                     atTick,
1292:                     poolUtilization
1293:                 )
1294:                 : _getRequiredCollateralSingleLegPartner(
1295:                     tokenId,
1296:                     index,
1297:                     positionSize,
1298:                     atTick,
1299:                     poolUtilization
1300:                 );
1301:     }
1439:     function _getRequiredCollateralSingleLegPartner(
1440:         TokenId tokenId,
1441:         uint256 index,
1442:         uint128 positionSize,
1443:         int24 atTick,
1444:         uint128 poolUtilization
1445:     ) internal view returns (uint256 required) {
1446:         // extract partner index (associated with another liquidity chunk)
1447:         uint256 partnerIndex = tokenId.riskPartner(index);
1448: 
1449:         uint256 isLong = tokenId.isLong(index);
1450:         if (isLong != tokenId.isLong(partnerIndex)) {
1451:             if (isLong == 1) {
1452:                 // compute the total amount of funds moved for that position
1453:                 required = _computeSpread(
1454:                     tokenId,
1455:                     positionSize,
1456:                     index,
1457:                     partnerIndex,
1458:                     poolUtilization
1459:                 );
1460:             }
1461:         } else {
1462:             required = _computeStrangle(tokenId, index, positionSize, atTick, poolUtilization);
1463:         }
1464:     }
1510:     function _computeSpread(
1511:         TokenId tokenId,
1512:         uint128 positionSize,
1513:         uint256 index,
1514:         uint256 partnerIndex,
1515:         uint128 poolUtilization
1516:     ) internal view returns (uint256 spreadRequirement) {
1517:         // compute the total amount of funds moved for the position's current leg
1518:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);
1519: 
1520:         // compute the total amount of funds moved for the position's partner leg
1521:         LeftRightUnsigned amountsMovedPartner = PanopticMath.getAmountsMoved(
1522:             tokenId,
1523:             positionSize,
1524:             partnerIndex
1525:         );
1526: 
1527:         // amount moved is right slot if tokenType=0, left slot otherwise
1528:         uint128 movedRight = amountsMoved.rightSlot();
1529:         uint128 movedLeft = amountsMoved.leftSlot();
1530: 
1531:         // amounts moved for partner
1532:         uint128 movedPartnerRight = amountsMovedPartner.rightSlot();
1533:         uint128 movedPartnerLeft = amountsMovedPartner.leftSlot();
1534: 
1535:         uint256 tokenType = tokenId.tokenType(index);
1536: 
1537:         // compute the max loss of the spread
1538: 
1539:         // if asset is NOT the same as the tokenType, the required amount is simply the difference in notional values
1540:         // ie. asset = 1, tokenType = 0:
1541:         if (tokenId.asset(index) != tokenType) {
1542:             unchecked {
1543:                 // always take the absolute values of the difference of amounts moved
1544:                 if (tokenType == 0) {
1545:                     spreadRequirement = movedRight < movedPartnerRight
1546:                         ? movedPartnerRight - movedRight
1547:                         : movedRight - movedPartnerRight;
1548:                 } else {
1549:                     spreadRequirement = movedLeft < movedPartnerLeft
1550:                         ? movedPartnerLeft - movedLeft
1551:                         : movedLeft - movedPartnerLeft;
1552:                 }
1553:             }
1554:         } else {
1555:             unchecked {
1556:                 uint256 notional;
1557:                 uint256 notionalP;
1558:                 uint128 contracts;
1559:                 if (tokenType == 1) {
1560:                     notional = movedRight;
1561:                     notionalP = movedPartnerRight;
1562:                     contracts = movedLeft;
1563:                 } else {
1564:                     notional = movedLeft;
1565:                     notionalP = movedPartnerLeft;
1566:                     contracts = movedRight;
1567:                 }
1568:                 // the required amount is the amount of contracts multiplied by (notional1 - notional2)/min(notional1, notional2)
1569:                 // can use unsafe because denominator is always nonzero
1570:                 spreadRequirement = (notional < notionalP)
1571:                     ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)
1572:                     : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);
1573:             }
1574:         }
1575: 
1576:         // calculate the spread requirement as max(max_loss, long_leg_col_req)
1577:         // narrower spreads will be very capital efficient (1/3 of non-partnered CR!), but
1578:         // wider spreads (an uncommon position w/ high max loss) may not benefit from risk partnering
1579:         spreadRequirement = Math.max(
1580:             spreadRequirement,
1581:             _getRequiredCollateralAtUtilization(
1582:                 tokenType == 0 ? movedRight : movedLeft,
1583:                 1,
1584:                 tokenType == 0
1585:                     ? int64(uint64(poolUtilization))
1586:                     : int64(uint64(poolUtilization >> 64))
1587:             )
1588:         );
1589:     }
1600:     function _computeStrangle(
1601:         TokenId tokenId,
1602:         uint256 index,
1603:         uint128 positionSize,
1604:         int24 atTick,
1605:         uint128 poolUtilization
1606:     ) internal view returns (uint256 strangleRequired) {
1607:         // If both tokenTypes are the same, then this is a long or short strangle.
1608:         // A strangle is an options strategy in which the investor holds a position
1609:         // in both a call and a put option with different strike prices,
1610:         // but with the same expiration date and underlying asset.
1611: 
1612:         /// collateral requirement is for short strangles depicted:
1613:         /**
1614:                     Put side of a short strangle, BPR = 100% - (100% - SCR/2)*(price/strike)
1615:            BUYING
1616:            POWER
1617:            REQUIREMENT
1618:                          ^                    .
1619:                          |           <- ITM   .  OTM ->
1620:                   100% - |--__                .
1621:                          |    ¯¯--__          .
1622:                          |          ¯¯--__    .
1623:                  SCR/2 - |                ¯¯--______ <------ base collateral is half that of a single-leg
1624:                          +--------------------+--->   current
1625:                          0                  strike     price
1626:          */
1627:         unchecked {
1628:             // A negative pool utilization is used to denote a position which is a strangle
1629:             // at low pool utilization's strangle legs are evaluated at 2x capital efficiency
1630: 
1631:             uint64 poolUtilization0 = uint64(poolUtilization);
1632:             uint64 poolUtilization1 = uint64(poolUtilization >> 64);
1633: 
1634:             // add 1 to handle poolUtilization = 0
1635: 
1636:             poolUtilization =
1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +
1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
1639: 
1640:             return
1641:                 strangleRequired = _getRequiredCollateralSingleLegNoPartner(
1642:                     tokenId,
1643:                     index,
1644:                     positionSize,
1645:                     atTick,
1646:                     poolUtilization
1647:                 );
1648:         }
1649:     }

```

*GitHub* : [36-1650](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L36-L1650)

### [G-08]<a name="g-08"></a> Modulus operations that could be unchecked

Modulus operations should be unchecked to save gas since they cannot overflow or underflow. Execution of modulus operations outside unchecked blocks adds nothing but overhead. Saves about 30 gas.

*There are 18 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) perform modulus which can not overflow (can use unchecked) :-
	- (timestamps[i],tickCumulatives[i],None,None) = univ3pool.observations(uint256((int256(observationIndex) - int256(i * period)) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#138-143)

/// @audit ************** Possible Issue Line(s) **************
	L#138-143,  

/// @audit ****************** Affected Code *******************
 138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
 139:                     uint256(
 140:                         (int256(observationIndex) - int256(i * period)) +
 141:                             int256(observationCardinality)
 142:                     ) % observationCardinality
 143:                 );

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.isLong(TokenId,uint256) (contracts/types/TokenId.sol#128-132) perform modulus which can not overflow (can use unchecked) :-
	- uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2) (contracts/types/TokenId.sol#130)

/// @audit ************** Possible Issue Line(s) **************
	L#130,  

/// @audit ****************** Affected Code *******************
 128:     function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 129:         unchecked {
 130:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);
 131:         }
 132:     }

```

*GitHub* : [128-132](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L128-L132)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addOptionRatio(TokenId,uint256,uint256) (contracts/types/TokenId.sol#221-232) perform modulus which can not overflow (can use unchecked) :-
	- TokenId.wrap(TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))) (contracts/types/TokenId.sol#227-230)

/// @audit ************** Possible Issue Line(s) **************
	L#227-230,  

/// @audit ****************** Affected Code *******************
 221:     function addOptionRatio(
 222:         TokenId self,
 223:         uint256 _optionRatio,
 224:         uint256 legIndex
 225:     ) internal pure returns (TokenId) {
 226:         unchecked {
 227:             return
 228:                 TokenId.wrap(
 229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))
 230:                 );
 231:         }
 232:     }

```

*GitHub* : [221-232](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L221-L232)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getTicks(int24,int24,int24) (contracts/libraries/PanopticMath.sol#338-363) perform modulus which can not overflow (can use unchecked) :-
	- tickLower % tickSpacing != 0 || tickUpper % tickSpacing != 0 || tickLower < minTick || tickUpper > maxTick (contracts/libraries/PanopticMath.sol#357-360)

/// @audit ************** Possible Issue Line(s) **************
	L#357-360,  

/// @audit ****************** Affected Code *******************
 357:                 tickLower % tickSpacing != 0 ||
 358:                 tickUpper % tickSpacing != 0 ||
 359:                 tickLower < minTick ||
 360:                 tickUpper > maxTick

```

*GitHub* : [338-363](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L338-L363)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addTokenType(TokenId,uint256,uint256) (contracts/types/TokenId.sol#255-266) perform modulus which can not overflow (can use unchecked) :-
	- TokenId.wrap(TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))) (contracts/types/TokenId.sol#261-264)

/// @audit ************** Possible Issue Line(s) **************
	L#261-264,  

/// @audit ****************** Affected Code *******************
 255:     function addTokenType(
 256:         TokenId self,
 257:         uint256 _tokenType,
 258:         uint256 legIndex
 259:     ) internal pure returns (TokenId) {
 260:         unchecked {
 261:             return
 262:                 TokenId.wrap(
 263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))
 264:                 );
 265:         }
 266:     }

```

*GitHub* : [255-266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L255-L266)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) perform modulus which can not overflow (can use unchecked) :-
	- sqrtR % (1 << 32) == 0 (contracts/libraries/Math.sol#179)

/// @audit ************** Possible Issue Line(s) **************
	L#179,  

/// @audit ****************** Affected Code *******************
 179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addAsset(TokenId,uint256,uint256) (contracts/types/TokenId.sol#205-214) perform modulus which can not overflow (can use unchecked) :-
	- TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48))) (contracts/types/TokenId.sol#211-212)

/// @audit ************** Possible Issue Line(s) **************
	L#211-212,  

/// @audit ****************** Affected Code *******************
 205:     function addAsset(
 206:         TokenId self,
 207:         uint256 _asset,
 208:         uint256 legIndex
 209:     ) internal pure returns (TokenId) {
 210:         unchecked {
 211:             return
 212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));
 213:         }
 214:     }

```

*GitHub* : [205-214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L205-L214)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addRiskPartner(TokenId,uint256,uint256) (contracts/types/TokenId.sol#273-284) perform modulus which can not overflow (can use unchecked) :-
	- TokenId.wrap(TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))) (contracts/types/TokenId.sol#279-282)

/// @audit ************** Possible Issue Line(s) **************
	L#279-282,  

/// @audit ****************** Affected Code *******************
 273:     function addRiskPartner(
 274:         TokenId self,
 275:         uint256 _riskPartner,
 276:         uint256 legIndex
 277:     ) internal pure returns (TokenId) {
 278:         unchecked {
 279:             return
 280:                 TokenId.wrap(
 281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))
 282:                 );
 283:         }
 284:     }

```

*GitHub* : [273-284](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L273-L284)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.riskPartner(TokenId,uint256) (contracts/types/TokenId.sol#148-152) perform modulus which can not overflow (can use unchecked) :-
	- uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4) (contracts/types/TokenId.sol#150)

/// @audit ************** Possible Issue Line(s) **************
	L#150,  

/// @audit ****************** Affected Code *******************
 148:     function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 149:         unchecked {
 150:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);
 151:         }
 152:     }

```

*GitHub* : [148-152](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L148-L152)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.unsafeDivRoundingUp(uint256,uint256) (contracts/libraries/Math.sol#738-742) perform modulus which can not overflow (can use unchecked) :-
	- result = a / b + a % b > 0 (contracts/libraries/Math.sol#740)

/// @audit ************** Possible Issue Line(s) **************
	L#740,  

/// @audit ****************** Affected Code *******************
 738:     function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
 739:         assembly ("memory-safe") {
 740:             result := add(div(a, b), gt(mod(a, b), 0))
 741:         }
 742:     }

```

*GitHub* : [738-742](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L738-L742)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.optionRatio(TokenId,uint256) (contracts/types/TokenId.sol#118-122) perform modulus which can not overflow (can use unchecked) :-
	- uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128) (contracts/types/TokenId.sol#120)

/// @audit ************** Possible Issue Line(s) **************
	L#120,  

/// @audit ****************** Affected Code *******************
 118:     function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 119:         unchecked {
 120:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);
 121:         }
 122:     }

```

*GitHub* : [118-122](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L118-L122)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.tickSpacing(TokenId) (contracts/types/TokenId.sol#96-100) perform modulus which can not overflow (can use unchecked) :-
	- int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16)) (contracts/types/TokenId.sol#98)

/// @audit ************** Possible Issue Line(s) **************
	L#98,  

/// @audit ****************** Affected Code *******************
  96:     function tickSpacing(TokenId self) internal pure returns (int24) {
  97:         unchecked {
  98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));
  99:         }
 100:     }

```

*GitHub* : [96-100](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L96-L100)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.tokenType(TokenId,uint256) (contracts/types/TokenId.sol#138-142) perform modulus which can not overflow (can use unchecked) :-
	- uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2) (contracts/types/TokenId.sol#140)

/// @audit ************** Possible Issue Line(s) **************
	L#140,  

/// @audit ****************** Affected Code *******************
 138:     function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 139:         unchecked {
 140:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);
 141:         }
 142:     }

```

*GitHub* : [138-142](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L138-L142)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) perform modulus which can not overflow (can use unchecked) :-
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180)
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190)
	- rank = (orderMap >> (3 * i)) % 8 (contracts/libraries/PanopticMath.sol#209)

/// @audit ************** Possible Issue Line(s) **************
	L#177-180,  L#186-190,  L#209,  

/// @audit ****************** Affected Code *******************
 177:             medianTick =
 178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
 179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
 180:                 2;
 186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(
 187:                         uint256(
 188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)
 189:                         ) % observationCardinality
 190:                     );
 209:                     rank = (orderMap >> (3 * i)) % 8;

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.width(TokenId,uint256) (contracts/types/TokenId.sol#169-173) perform modulus which can not overflow (can use unchecked) :-
	- int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096)) (contracts/types/TokenId.sol#171)

/// @audit ************** Possible Issue Line(s) **************
	L#171,  

/// @audit ****************** Affected Code *******************
 169:     function width(TokenId self, uint256 legIndex) internal pure returns (int24) {
 170:         unchecked {
 171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));
 172:         } // "% 4096" = take last (2 ** 12 = 4096) 12 bits
 173:     }

```

*GitHub* : [169-173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L169-L173)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addWidth(TokenId,int24,uint256) (contracts/types/TokenId.sol#310-323) perform modulus which can not overflow (can use unchecked) :-
	- TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))) (contracts/types/TokenId.sol#317-321)

/// @audit ************** Possible Issue Line(s) **************
	L#317-321,  

/// @audit ****************** Affected Code *******************
 310:     function addWidth(
 311:         TokenId self,
 312:         int24 _width,
 313:         uint256 legIndex
 314:     ) internal pure returns (TokenId) {
 315:         // % 4096 -> take 12 bits from the incoming 24 bits (there's no uint12)
 316:         unchecked {
 317:             return
 318:                 TokenId.wrap(
 319:                     TokenId.unwrap(self) +
 320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))
 321:                 );
 322:         }
 323:     }

```

*GitHub* : [310-323](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L310-L323)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.asset(TokenId,uint256) (contracts/types/TokenId.sol#108-112) perform modulus which can not overflow (can use unchecked) :-
	- uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2) (contracts/types/TokenId.sol#110)

/// @audit ************** Possible Issue Line(s) **************
	L#110,  

/// @audit ****************** Affected Code *******************
 108:     function asset(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 109:         unchecked {
 110:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);
 111:         }
 112:     }

```

*GitHub* : [108-112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L108-L112)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addIsLong(TokenId,uint256,uint256) (contracts/types/TokenId.sol#240-248) perform modulus which can not overflow (can use unchecked) :-
	- TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8))) (contracts/types/TokenId.sol#246)

/// @audit ************** Possible Issue Line(s) **************
	L#246,  

/// @audit ****************** Affected Code *******************
 240:     function addIsLong(
 241:         TokenId self,
 242:         uint256 _isLong,
 243:         uint256 legIndex
 244:     ) internal pure returns (TokenId) {
 245:         unchecked {
 246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));
 247:         }
 248:     }

```

*GitHub* : [240-248](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L240-L248)

### [G-09]<a name="g-09"></a> Functions guaranteed to revert when called by normal users can be marked `payable`

If a function modifier such as `onlyOwner` is used, or a function checks `msg.sender` some other way, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. The extra opcodes avoided are `CALLVALUE`(2),`DUP1`(3),`ISZERO`(3),`PUSH2`(3),`JUMPI`(10),`PUSH1`(3),`DUP1`(3),`REVERT`(0),`JUMPDEST`(1),`POP`(2), which costs an average of about **21 gas per call** to the function, in addition to the extra deployment cost

*There are 10 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24) (contracts/PanopticPool.sol#614-667) can be marked `payable`.

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [614-667](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L614-L667)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.withdraw(uint256,address,address) (contracts/CollateralTracker.sol#531-566) can be marked `payable`.

/// @audit ****************** Affected Code *******************
 531:     function withdraw(
 532:         uint256 assets,
 533:         address receiver,
 534:         address owner
 535:     ) external returns (uint256 shares) {
 536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();
 537: 
 538:         shares = previewWithdraw(assets);
 539: 
 540:         // check/update allowance for approved withdraw

```

*GitHub* : [531-566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L531-L566)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.transfer(address,uint256) (contracts/CollateralTracker.sol#323-334) can be marked `payable`.

/// @audit ****************** Affected Code *******************
 323:     function transfer(
 324:         address recipient,
 325:         uint256 amount
 326:     ) public override(ERC20Minimal) returns (bool) {
 327:         // make sure the caller does not have any open option positions
 328:         // if they do: we don't want them sending panoptic pool shares to others
 329:         // since that's like reducing collateral
 330: 
 331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();
 332: 
 333:         return ERC20Minimal.transfer(recipient, amount);
 334:     }

```

*GitHub* : [323-334](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L323-L334)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/tokens/ERC1155Minimal.sol#130-171) can be marked `payable`.

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [130-171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L130-L171)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) can be marked `payable`.

/// @audit ****************** Affected Code *******************
1017:     function liquidate(
1018:         TokenId[] calldata positionIdListLiquidator,
1019:         address liquidatee,
1020:         LeftRightUnsigned delegations,
1021:         TokenId[] calldata positionIdList
1022:     ) external {
1023:         _validatePositionList(liquidatee, positionIdList, 0);
1024: 
1025:         // Assert the account we are liquidating is actually insolvent
1026:         int24 twapTick = getUniV3TWAP();

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.transferOwnership(address) (contracts/PanopticFactory.sol#147-155) can be marked `payable`.

/// @audit ****************** Affected Code *******************
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

*GitHub* : [147-155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147-L155)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155._mint(address,uint256,uint256) (contracts/tokens/ERC1155Minimal.sol#214-230) can be marked `payable`.

/// @audit ****************** Affected Code *******************
 214:     function _mint(address to, uint256 id, uint256 amount) internal {
 215:         // balance will never overflow
 216:         unchecked {
 217:             balanceOf[to][id] += amount;
 218:         }
 219: 
 220:         emit TransferSingle(msg.sender, address(0), to, id, amount);
 221: 
 222:         if (to.code.length != 0) {
 223:             if (
 224:                 ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
 225:                 ERC1155Holder.onERC1155Received.selector
 226:             ) {
 227:                 revert UnsafeRecipient();
 228:             }
 229:         }
 230:     }

```

*GitHub* : [214-230](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L214-L230)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.redeem(uint256,address,address) (contracts/CollateralTracker.sol#591-626) can be marked `payable`.

/// @audit ****************** Affected Code *******************
 591:     function redeem(
 592:         uint256 shares,
 593:         address receiver,
 594:         address owner
 595:     ) external returns (uint256 assets) {
 596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();
 597: 
 598:         // check/update allowance for approved redeem
 599:         if (msg.sender != owner) {
 600:             uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.

```

*GitHub* : [591-626](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L591-L626)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes) (contracts/tokens/ERC1155Minimal.sol#94-120) can be marked `payable`.

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [94-120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L94-L120)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.deployNewPool(address,address,uint24,bytes32) (contracts/PanopticFactory.sol#210-276) can be marked `payable`.

/// @audit ****************** Affected Code *******************
 210:     function deployNewPool(
 211:         address token0,
 212:         address token1,
 213:         uint24 fee,
 214:         bytes32 salt
 215:     ) external returns (PanopticPool newPoolContract) {
 216:         // sort the tokens, if necessary:
 217:         (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);
 218: 
 219:         // frontrunning protection for mined pool addresses

```

*GitHub* : [210-276](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210-L276)

### [G-10]<a name="g-10"></a> if variable is casted more than once, consider caching the result to save gas

Casting values multiple times in Solidity can be gas-inefficient. When a value undergoes repeated type conversions, the EVM must execute additional operations for each cast, consuming more gas than necessary. To optimize for gas efficiency, cache the result of the initial cast in a local variable and reuse it, rather than performing multiple casts. This not only conserves gas but also enhances code readability, reducing potential error points. For example, instead of repeatedly casting an `address` to `uint256`, cast once, store the result in a local variable, and reference that variable in subsequent operations.

*There are 21 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getPoolId(address) (contracts/libraries/PanopticMath.sol#47-54) casts (address univ3pool) multiple time(s) :-
	- tickSpacing = IUniswapV3Pool(univ3pool).tickSpacing() (contracts/libraries/PanopticMath.sol#49)
	- poolId = uint64(uint160(univ3pool) >> 112) (contracts/libraries/PanopticMath.sol#50)

/// @audit ************** Possible Issue Line(s) **************
	L#49,  L#50,  

/// @audit ****************** Affected Code *******************
  47:     function getPoolId(address univ3pool) internal view returns (uint64) {
  48:         unchecked {
  49:             int24 tickSpacing = IUniswapV3Pool(univ3pool).tickSpacing();
  50:             uint64 poolId = uint64(uint160(univ3pool) >> 112);
  51:             poolId += uint64(uint24(tickSpacing)) << 48;
  52:             return poolId;
  53:         }
  54:     }

```

*GitHub* : [47-54](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L47-L54)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) casts (LeftRightSigned legPremia) multiple time(s) :-
	- LeftRightSigned.unwrap(legPremia) != 0 (contracts/PanopticPool.sol#1862)
	- availablePremium = _getAvailablePremium(totalLiquidity + positionLiquidity,settledTokens,grossPremiumLast,LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),premiumAccumulatorsByLeg[leg]) (contracts/PanopticPool.sol#1888-1894)

/// @audit ************** Possible Issue Line(s) **************
	L#1862,  L#1888-1894,  

/// @audit ****************** Affected Code *******************
1862:             if (LeftRightSigned.unwrap(legPremia) != 0) {
1888:                     LeftRightUnsigned availablePremium = _getAvailablePremium(
1889:                         totalLiquidity + positionLiquidity,
1890:                         settledTokens,
1891:                         grossPremiumLast,
1892:                         LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
1893:                         premiumAccumulatorsByLeg[leg]
1894:                     );

```

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) casts (int256 haircut1) multiple time(s) :-
	- collateral1.exercise(_liquidatee,0,0,0,int128(haircut1)) (contracts/libraries/PanopticMath.sol#857)
	- settled1 = Math.unsafeDivRoundingUp(uint128(- _premiasByLeg[i_scope_0][leg_scope_2].leftSlot()) * uint256(haircut1),uint128(longPremium.leftSlot())) (contracts/libraries/PanopticMath.sol#873-876)

/// @audit ************** Possible Issue Line(s) **************
	L#857,  L#873-876,  

/// @audit ****************** Affected Code *******************
 857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
 873:                         uint256 settled1 = Math.unsafeDivRoundingUp(
 874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
 875:                             uint128(longPremium.leftSlot())
 876:                         );

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.validate(TokenId) (contracts/types/TokenId.sol#500-571) casts (TokenId self) multiple time(s) :-
	- chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64 (contracts/types/TokenId.sol#506)
	- (TokenId.unwrap(self) >> (64 + 48 * i)) != 0 (contracts/types/TokenId.sol#512)

/// @audit ************** Possible Issue Line(s) **************
	L#506,  L#512,  

/// @audit ****************** Affected Code *******************
 506:             uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;
 512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

```

*GitHub* : [500-571](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L500-L571)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) casts (int256 haircut0) multiple time(s) :-
	- collateral0.exercise(_liquidatee,0,0,0,int128(haircut0)) (contracts/libraries/PanopticMath.sol#856)
	- settled0 = Math.unsafeDivRoundingUp(uint128(- _premiasByLeg[i_scope_0][leg_scope_2].rightSlot()) * uint256(haircut0),uint128(longPremium.rightSlot())) (contracts/libraries/PanopticMath.sol#869-872)

/// @audit ************** Possible Issue Line(s) **************
	L#856,  L#869-872,  

/// @audit ****************** Affected Code *******************
 856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
 869:                         uint256 settled0 = Math.unsafeDivRoundingUp(
 870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
 871:                             uint128(longPremium.rightSlot())
 872:                         );

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256) (contracts/SemiFungiblePositionManager.sol#593-653) casts (IUniswapV3Pool univ3pool) multiple time(s) :-
	- positionKey_from = keccak256(bytes)(abi.encodePacked(address(univ3pool),from,id.tokenType(leg),liquidityChunk.tickLower(),liquidityChunk.tickUpper())) (contracts/SemiFungiblePositionManager.sol#611-619)
	- positionKey_to = keccak256(bytes)(abi.encodePacked(address(univ3pool),to,id.tokenType(leg),liquidityChunk.tickLower(),liquidityChunk.tickUpper())) (contracts/SemiFungiblePositionManager.sol#620-628)

/// @audit ************** Possible Issue Line(s) **************
	L#611-619,  L#620-628,  

/// @audit ****************** Affected Code *******************
 611:             bytes32 positionKey_from = keccak256(
 612:                 abi.encodePacked(
 613:                     address(univ3pool),
 614:                     from,
 615:                     id.tokenType(leg),
 616:                     liquidityChunk.tickLower(),
 617:                     liquidityChunk.tickUpper()
 618:                 )
 619:             );
 620:             bytes32 positionKey_to = keccak256(
 621:                 abi.encodePacked(
 622:                     address(univ3pool),
 623:                     to,
 624:                     id.tokenType(leg),
 625:                     liquidityChunk.tickLower(),
 626:                     liquidityChunk.tickUpper()
 627:                 )
 628:             );

```

*GitHub* : [593-653](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593-L653)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.minePoolAddress(bytes32,uint256,uint256) (contracts/PanopticFactory.sol#290-326) casts (bytes32 salt) multiple time(s) :-
	- maxSalt = uint256(salt) + loops (contracts/PanopticFactory.sol#300)
	- uint256(salt) < maxSalt (contracts/PanopticFactory.sol#303)
	- salt = bytes32(uint256(salt) + 1) (contracts/PanopticFactory.sol#323)

/// @audit ************** Possible Issue Line(s) **************
	L#300,  L#303,  L#323,  

/// @audit ****************** Affected Code *******************
 300:             maxSalt = uint256(salt) + loops;
 303:         for (; uint256(salt) < maxSalt; ) {
 323:                 salt = bytes32(uint256(salt) + 1);

```

*GitHub* : [290-326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L290-L326)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) casts (SemiFungiblePositionManager sfpm) multiple time(s) :-
	- IERC20Partial(token0).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#32)
	- IERC20Partial(token1).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#33)

/// @audit ************** Possible Issue Line(s) **************
	L#32,  L#33,  

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L24-L38)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) casts (uint256 amount1) multiple time(s) :-
	- value1 += int256(amount1) (contracts/libraries/FeesCalc.sol#70)
	- value1 -= int256(amount1) (contracts/libraries/FeesCalc.sol#75)

/// @audit ************** Possible Issue Line(s) **************
	L#70,  L#75,  

/// @audit ****************** Affected Code *******************
  70:                         value1 += int256(amount1);
  75:                         value1 -= int256(amount1);

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1600-1649) casts (uint64 poolUtilization0) multiple time(s) :-
	- poolUtilization = uint128(uint64(- int64(poolUtilization0))) + (uint128(uint64(- int64(1))) << 64) (contracts/CollateralTracker.sol#1636-1638)
	- poolUtilization = uint128(uint64(- int64(poolUtilization0))) + (uint128(uint64(- int64(poolUtilization1))) << 64) (contracts/CollateralTracker.sol#1636-1638)

/// @audit ************** Possible Issue Line(s) **************
	L#1636-1638,  

/// @audit ****************** Affected Code *******************
1636:             poolUtilization =
1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +
1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```

*GitHub* : [1600-1649](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1600-L1649)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightUnsigned,LeftRightUnsigned) (contracts/types/LeftRight.sol#148-165) casts (LeftRightUnsigned x) multiple time(s) :-
	- z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y)) (contracts/types/LeftRight.sol#155)
	- LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) || (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x))) (contracts/types/LeftRight.sol#161-162)

/// @audit ************** Possible Issue Line(s) **************
	L#155,  L#161-162,  

/// @audit ****************** Affected Code *******************
 148:     function add(
 149:         LeftRightUnsigned x,
 150:         LeftRightUnsigned y
 151:     ) internal pure returns (LeftRightUnsigned z) {
 152:         unchecked {
 153:             // adding leftRight packed uint128's is same as just adding the values explictily
 154:             // given that we check for overflows of the left and right values
 155:             z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));
 156: 
 157:             // on overflow z will be less than either x or y
 158:             // type cast z to uint128 to isolate the right slot and if it's lower than a value it's comprised of (x)
 159:             // then an overflow has occured
 160:             if (
 161:                 LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||
 162:                 (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))
 163:             ) revert Errors.UnderOverFlow();
 164:         }
 165:     }

```

*GitHub* : [148-165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L148-L165)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.sub(LeftRightUnsigned,LeftRightUnsigned) (contracts/types/LeftRight.sol#171-188) casts (LeftRightUnsigned x) multiple time(s) :-
	- z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y)) (contracts/types/LeftRight.sol#178)
	- LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) || (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x))) (contracts/types/LeftRight.sol#184-185)

/// @audit ************** Possible Issue Line(s) **************
	L#178,  L#184-185,  

/// @audit ****************** Affected Code *******************
 171:     function sub(
 172:         LeftRightUnsigned x,
 173:         LeftRightUnsigned y
 174:     ) internal pure returns (LeftRightUnsigned z) {
 175:         unchecked {
 176:             // subtracting leftRight packed uint128's is same as just subtracting the values explictily
 177:             // given that we check for underflows of the left and right values
 178:             z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));
 179: 
 180:             // on underflow z will be greater than either x or y
 181:             // type cast z to uint128 to isolate the right slot and if it's higher than a value that was subtracted from (x)
 182:             // then an underflow has occured
 183:             if (
 184:                 LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||
 185:                 (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))
 186:             ) revert Errors.UnderOverFlow();
 187:         }
 188:     }

```

*GitHub* : [171-188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L171-L188)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) casts (uint256 amount0) multiple time(s) :-
	- value0 += int256(amount0) (contracts/libraries/FeesCalc.sol#69)
	- value0 -= int256(amount0) (contracts/libraries/FeesCalc.sol#74)

/// @audit ************** Possible Issue Line(s) **************
	L#69,  L#74,  

/// @audit ****************** Affected Code *******************
  69:                         value0 += int256(amount0);
  74:                         value0 -= int256(amount0);

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.safeTransferFrom(address,address,uint256,uint256,bytes) (contracts/SemiFungiblePositionManager.sol#540-556) casts (uint256 id) multiple time(s) :-
	- s_poolContext[TokenId.wrap(id).poolId()].locked (contracts/SemiFungiblePositionManager.sol#549)
	- registerTokenTransfer(from,to,TokenId.wrap(id),amount) (contracts/SemiFungiblePositionManager.sol#552)

/// @audit ************** Possible Issue Line(s) **************
	L#549,  L#552,  

/// @audit ****************** Affected Code *******************
 540:     function safeTransferFrom(
 541:         address from,
 542:         address to,
 543:         uint256 id,
 544:         uint256 amount,
 545:         bytes calldata data
 546:     ) public override {
 547:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
 548:         // so just check if there is an active reentrancy lock for the relevant pool on the token we're transferring
 549:         if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();
 550: 
 551:         // update the position data
 552:         registerTokenTransfer(from, to, TokenId.wrap(id), amount);
 553: 
 554:         // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)
 555:         super.safeTransferFrom(from, to, id, amount, data);
 556:     }

```

*GitHub* : [540-556](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L540-L556)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.quickSort(int256[],int256,int256) (contracts/libraries/Math.sol#753-771) casts (int256 j) multiple time(s) :-
	- pivot < arr[uint256(j)] (contracts/libraries/Math.sol#761)
	- (arr[uint256(i)],arr[uint256(j)]) = (arr[uint256(j)],arr[uint256(i)]) (contracts/libraries/Math.sol#763)

/// @audit ************** Possible Issue Line(s) **************
	L#761,  L#763,  

/// @audit ****************** Affected Code *******************
 753:     function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {
 754:         unchecked {
 755:             int256 i = left;
 756:             int256 j = right;
 757:             if (i == j) return;
 758:             int256 pivot = arr[uint256(left + (right - left) / 2)];
 759:             while (i < j) {
 760:                 while (arr[uint256(i)] < pivot) i++;
 761:                 while (pivot < arr[uint256(j)]) j--;
 762:                 if (i <= j) {
 763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);
 764:                     i++;
 765:                     j--;
 766:                 }
 767:             }
 768:             if (left < j) quickSort(arr, left, j);
 769:             if (i < right) quickSort(arr, i, right);
 770:         }
 771:     }

```

*GitHub* : [753-771](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L753-L771)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._sellCollateralRatio(int256) (contracts/CollateralTracker.sol#751-800) casts (int256 utilization) multiple time(s) :-
	- uint256(utilization) < TARGET_POOL_UTIL (contracts/CollateralTracker.sol#784)
	- uint256(utilization) > SATURATED_POOL_UTIL (contracts/CollateralTracker.sol#790)

/// @audit ************** Possible Issue Line(s) **************
	L#784,  L#790,  

/// @audit ****************** Affected Code *******************
 784:         if (uint256(utilization) < TARGET_POOL_UTIL) {
 790:         if (uint256(utilization) > SATURATED_POOL_UTIL) {

```

*GitHub* : [751-800](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L751-L800)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) casts (int24 tick) multiple time(s) :-
	- absTick = uint256(- int256(tick)) (contracts/libraries/Math.sol#130)
	- absTick = uint256(int256(tick)) (contracts/libraries/Math.sol#130)

/// @audit ************** Possible Issue Line(s) **************
	L#130,  

/// @audit ****************** Affected Code *******************
 130:             uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) casts (address token0) multiple time(s) :-
	- IERC20Partial(token0).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#32)
	- IERC20Partial(token0).approve(address(ct0),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#36)

/// @audit ************** Possible Issue Line(s) **************
	L#32,  L#36,  

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L24-L38)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) casts (address token1) multiple time(s) :-
	- IERC20Partial(token1).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#33)
	- IERC20Partial(token1).approve(address(ct1),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#37)

/// @audit ************** Possible Issue Line(s) **************
	L#33,  L#37,  

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L24-L38)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.quickSort(int256[],int256,int256) (contracts/libraries/Math.sol#753-771) casts (int256 i) multiple time(s) :-
	- arr[uint256(i)] < pivot (contracts/libraries/Math.sol#760)
	- (arr[uint256(i)],arr[uint256(j)]) = (arr[uint256(j)],arr[uint256(i)]) (contracts/libraries/Math.sol#763)

/// @audit ************** Possible Issue Line(s) **************
	L#760,  L#763,  

/// @audit ****************** Affected Code *******************
 753:     function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {
 754:         unchecked {
 755:             int256 i = left;
 756:             int256 j = right;
 757:             if (i == j) return;
 758:             int256 pivot = arr[uint256(left + (right - left) / 2)];
 759:             while (i < j) {
 760:                 while (arr[uint256(i)] < pivot) i++;
 761:                 while (pivot < arr[uint256(j)]) j--;
 762:                 if (i <= j) {
 763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);
 764:                     i++;
 765:                     j--;
 766:                 }
 767:             }
 768:             if (left < j) quickSort(arr, left, j);
 769:             if (i < right) quickSort(arr, i, right);
 770:         }
 771:     }

```

*GitHub* : [753-771](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L753-L771)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker) (contracts/PanopticPool.sol#291-327) casts (IUniswapV3Pool _univ3pool) multiple time(s) :-
	- s_univ3pool = IUniswapV3Pool(_univ3pool) (contracts/PanopticPool.sol#302)
	- (currentTick) = IUniswapV3Pool(_univ3pool).slot0() (contracts/PanopticPool.sol#304)

/// @audit ************** Possible Issue Line(s) **************
	L#302,  L#304,  

/// @audit ****************** Affected Code *******************
 302:         s_univ3pool = IUniswapV3Pool(_univ3pool);
 304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

```

*GitHub* : [291-327](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L327)

### [G-11]<a name="g-11"></a> Inefficient Parameter Storage

When passing function parameters, using the `calldata` area instead of `memory` can improve gas efficiency. `Calldata` is a read-only area where function arguments and external function calls' parameters are stored.

By using `calldata` for function parameters, you avoid unnecessary gas costs associated with copying data from calldata to `memory`. This is particularly beneficial when the parameter is read-only and is not modified during the function call.

*There are 117 instance(s) of this issue:*

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.subRect(LeftRightSigned,LeftRightSigned) (contracts/types/LeftRight.sol#251-269) should use calldata instead of memory for :- 
	- LeftRightLibrary.subRect(LeftRightSigned,LeftRightSigned).x (contracts/types/LeftRight.sol#252)
	- LeftRightLibrary.subRect(LeftRightSigned,LeftRightSigned).y (contracts/types/LeftRight.sol#253)

/// @audit ************** Possible Issue Line(s) **************
	L#252,  L#253,  

/// @audit ****************** Affected Code *******************
 251:     function subRect(
 252:         LeftRightSigned x,
 253:         LeftRightSigned y
 254:     ) internal pure returns (LeftRightSigned z) {
 255:         unchecked {
 256:             int256 left256 = int256(x.leftSlot()) - y.leftSlot();
 257:             int128 left128 = int128(left256);
 258: 
 259:             int256 right256 = int256(x.rightSlot()) - y.rightSlot();
 260:             int128 right128 = int128(right256);
 261: 
 262:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
 263: 
 264:             return
 265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(
 266:                     int128(Math.max(left128, 0))
 267:                 );
 268:         }
 269:     }

```

*GitHub* : [251-269](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L251-L269)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.sub(LeftRightSigned,LeftRightSigned) (contracts/types/LeftRight.sol#232-244) should use calldata instead of memory for :- 
	- LeftRightLibrary.sub(LeftRightSigned,LeftRightSigned).x (contracts/types/LeftRight.sol#232)
	- LeftRightLibrary.sub(LeftRightSigned,LeftRightSigned).y (contracts/types/LeftRight.sol#232)

/// @audit ************** Possible Issue Line(s) **************
	L#232,  

/// @audit ****************** Affected Code *******************
 232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 233:         unchecked {
 234:             int256 left256 = int256(x.leftSlot()) - y.leftSlot();
 235:             int128 left128 = int128(left256);
 236: 
 237:             int256 right256 = int256(x.rightSlot()) - y.rightSlot();
 238:             int128 right128 = int128(right256);
 239: 
 240:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
 241: 
 242:             return z.toRightSlot(right128).toLeftSlot(left128);
 243:         }
 244:     }

```

*GitHub* : [232-244](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L232-L244)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getAmountsMoved(TokenId,uint128,uint256) (contracts/libraries/PanopticMath.sol#574-599) should use calldata instead of memory for :- 
	- PanopticMath.getAmountsMoved(TokenId,uint128,uint256).tokenId (contracts/libraries/PanopticMath.sol#575)

/// @audit ************** Possible Issue Line(s) **************
	L#575,  

/// @audit ****************** Affected Code *******************
 575:         TokenId tokenId,

```

*GitHub* : [574-599](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L574-L599)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLegPartner(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1439-1464) should use calldata instead of memory for :- 
	- CollateralTracker._getRequiredCollateralSingleLegPartner(TokenId,uint256,uint128,int24,uint128).tokenId (contracts/CollateralTracker.sol#1440)

/// @audit ************** Possible Issue Line(s) **************
	L#1440,  

/// @audit ****************** Affected Code *******************
1440:         TokenId tokenId,

```

*GitHub* : [1439-1464](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1439-L1464)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.addTickUpper(LiquidityChunk,int24) (contracts/types/LiquidityChunk.sol#118-129) should use calldata instead of memory for :- 
	- LiquidityChunkLibrary.addTickUpper(LiquidityChunk,int24).self (contracts/types/LiquidityChunk.sol#119)

/// @audit ************** Possible Issue Line(s) **************
	L#119,  

/// @audit ****************** Affected Code *******************
 118:     function addTickUpper(
 119:         LiquidityChunk self,
 120:         int24 _tickUpper
 121:     ) internal pure returns (LiquidityChunk) {
 122:         unchecked {
 123:             // convert tick upper to uint24 as explicit conversion from int24 to uint256 is not allowed
 124:             return
 125:                 LiquidityChunk.wrap(
 126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)
 127:                 );
 128:         }
 129:     }

```

*GitHub* : [118-129](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L118-L129)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.addTickLower(LiquidityChunk,int24) (contracts/types/LiquidityChunk.sol#102-112) should use calldata instead of memory for :- 
	- LiquidityChunkLibrary.addTickLower(LiquidityChunk,int24).self (contracts/types/LiquidityChunk.sol#103)

/// @audit ************** Possible Issue Line(s) **************
	L#103,  

/// @audit ****************** Affected Code *******************
 102:     function addTickLower(
 103:         LiquidityChunk self,
 104:         int24 _tickLower
 105:     ) internal pure returns (LiquidityChunk) {
 106:         unchecked {
 107:             return
 108:                 LiquidityChunk.wrap(
 109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)
 110:                 );
 111:         }
 112:     }

```

*GitHub* : [102-112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L102-L112)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getAccountMargin(address,int24,uint256[2][],int128) (contracts/CollateralTracker.sol#1159-1193) should use calldata instead of memory for :- 
	- CollateralTracker._getAccountMargin(address,int24,uint256[2][],int128).positionBalanceArray (contracts/CollateralTracker.sol#1162)

/// @audit ************** Possible Issue Line(s) **************
	L#1162,  

/// @audit ****************** Affected Code *******************
1162:         uint256[2][] memory positionBalanceArray,

```

*GitHub* : [1159-1193](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1159-L1193)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.burnTokenizedPosition(TokenId,uint128,int24,int24) (contracts/SemiFungiblePositionManager.sol#471-495) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager.burnTokenizedPosition(TokenId,uint128,int24,int24).tokenId (contracts/SemiFungiblePositionManager.sol#472)

/// @audit ************** Possible Issue Line(s) **************
	L#472,  

/// @audit ****************** Affected Code *******************
 471:     function burnTokenizedPosition(
 472:         TokenId tokenId,
 473:         uint128 positionSize,
 474:         int24 slippageTickLimitLow,
 475:         int24 slippageTickLimitHigh
 476:     )
 477:         external
 478:         ReentrancyLock(tokenId.poolId())
 479:         returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
 480:     {
 481:         // burn this ERC1155 token id
 482:         _burn(msg.sender, TokenId.unwrap(tokenId), positionSize);
 483: 
 484:         // emit event
 485:         emit TokenizedPositionBurnt(msg.sender, tokenId, positionSize);
 486: 
 487:         // Call a function that contains other functions to mint/burn position, collect amounts, swap if necessary
 488:         (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
 489:             tokenId,
 490:             positionSize,
 491:             slippageTickLimitLow,
 492:             slippageTickLimitHigh,
 493:             BURN
 494:         );
 495:     }

```

*GitHub* : [471-495](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L471-L495)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath._calculateIOAmounts(TokenId,uint128,uint256) (contracts/libraries/PanopticMath.sol#607-635) should use calldata instead of memory for :- 
	- PanopticMath._calculateIOAmounts(TokenId,uint128,uint256).tokenId (contracts/libraries/PanopticMath.sol#608)

/// @audit ************** Possible Issue Line(s) **************
	L#608,  

/// @audit ****************** Affected Code *******************
 608:         TokenId tokenId,

```

*GitHub* : [607-635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L607-L635)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.poolId(TokenId) (contracts/types/TokenId.sol#87-91) should use calldata instead of memory for :- 
	- TokenIdLibrary.poolId(TokenId).self (contracts/types/TokenId.sol#87)

/// @audit ************** Possible Issue Line(s) **************
	L#87,  

/// @audit ****************** Affected Code *******************
  87:     function poolId(TokenId self) internal pure returns (uint64) {
  88:         unchecked {
  89:             return uint64(TokenId.unwrap(self));
  90:         }
  91:     }

```

*GitHub* : [87-91](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L87-L91)

```solidity
File: contracts/libraries/CallbackLib.sol

/// @audit ******************* Issue Detail *******************
CallbackLib.validateCallback(address,IUniswapV3Factory,CallbackLib.PoolFeatures) (contracts/libraries/CallbackLib.sol#30-38) should use calldata instead of memory for :- 
	- CallbackLib.validateCallback(address,IUniswapV3Factory,CallbackLib.PoolFeatures).factory (contracts/libraries/CallbackLib.sol#32)
	- CallbackLib.validateCallback(address,IUniswapV3Factory,CallbackLib.PoolFeatures).features (contracts/libraries/CallbackLib.sol#33)

/// @audit ************** Possible Issue Line(s) **************
	L#32,  L#33,  

/// @audit ****************** Affected Code *******************
  30:     function validateCallback(
  31:         address sender,
  32:         IUniswapV3Factory factory,
  33:         PoolFeatures memory features
  34:     ) internal view {
  35:         // Call getPool on the factory to verify that the sender corresponds to the canonical pool with the claimed features
  36:         if (factory.getPool(features.token0, features.token1, features.fee) != sender)
  37:             revert Errors.InvalidUniswapCallback();
  38:     }

```

*GitHub* : [30-38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L30-L38)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.tickUpper(LiquidityChunk) (contracts/types/LiquidityChunk.sol#180-184) should use calldata instead of memory for :- 
	- LiquidityChunkLibrary.tickUpper(LiquidityChunk).self (contracts/types/LiquidityChunk.sol#180)

/// @audit ************** Possible Issue Line(s) **************
	L#180,  

/// @audit ****************** Affected Code *******************
 180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {
 181:         unchecked {
 182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));
 183:         }
 184:     }

```

*GitHub* : [180-184](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L180-L184)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.constructor(IUniswapV3Factory) (contracts/SemiFungiblePositionManager.sol#341-343) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager.constructor(IUniswapV3Factory)._factory (contracts/SemiFungiblePositionManager.sol#341)

/// @audit ************** Possible Issue Line(s) **************
	L#341,  

/// @audit ****************** Affected Code *******************
 341:     constructor(IUniswapV3Factory _factory) {
 342:         FACTORY = _factory;
 343:     }

```

*GitHub* : [341-343](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L341-L343)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) should use calldata instead of memory for :- 
	- InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address).sfpm (contracts/libraries/InteractionHelper.sol#25)
	- InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address).ct0 (contracts/libraries/InteractionHelper.sol#26)
	- InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address).ct1 (contracts/libraries/InteractionHelper.sol#27)

/// @audit ************** Possible Issue Line(s) **************
	L#25,  L#26,  L#27,  

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L24-L38)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker) (contracts/libraries/PanopticMath.sol#917-966) should use calldata instead of memory for :- 
	- PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker).refundValues (contracts/libraries/PanopticMath.sol#919)
	- PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker).collateral0 (contracts/libraries/PanopticMath.sol#921)
	- PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker).collateral1 (contracts/libraries/PanopticMath.sol#922)

/// @audit ************** Possible Issue Line(s) **************
	L#919,  L#921,  L#922,  

/// @audit ****************** Affected Code *******************
 919:         LeftRightSigned refundValues,
 921:         CollateralTracker collateral0,
 922:         CollateralTracker collateral1

```

*GitHub* : [917-966](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L917-L966)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.getAccountMarginDetails(address,int24,uint256[2][],int128) (contracts/CollateralTracker.sol#1141-1148) should use calldata instead of memory for :- 
	- CollateralTracker.getAccountMarginDetails(address,int24,uint256[2][],int128).positionBalanceArray (contracts/CollateralTracker.sol#1144)

/// @audit ************** Possible Issue Line(s) **************
	L#1144,  

/// @audit ****************** Affected Code *******************
1141:     function getAccountMarginDetails(
1142:         address user,
1143:         int24 currentTick,
1144:         uint256[2][] memory positionBalanceArray,
1145:         int128 premiumAllPositions
1146:     ) public view returns (LeftRightUnsigned tokenData) {
1147:         tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);
1148:     }

```

*GitHub* : [1141-1148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1141-L1148)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.width(TokenId,uint256) (contracts/types/TokenId.sol#169-173) should use calldata instead of memory for :- 
	- TokenIdLibrary.width(TokenId,uint256).self (contracts/types/TokenId.sol#169)

/// @audit ************** Possible Issue Line(s) **************
	L#169,  

/// @audit ****************** Affected Code *******************
 169:     function width(TokenId self, uint256 legIndex) internal pure returns (int24) {
 170:         unchecked {
 171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));
 172:         } // "% 4096" = take last (2 ** 12 = 4096) 12 bits
 173:     }

```

*GitHub* : [169-173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L169-L173)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.rightSlot(LeftRightUnsigned) (contracts/types/LeftRight.sol#39-41) should use calldata instead of memory for :- 
	- LeftRightLibrary.rightSlot(LeftRightUnsigned).self (contracts/types/LeftRight.sol#39)

/// @audit ************** Possible Issue Line(s) **************
	L#39,  

/// @audit ****************** Affected Code *******************
  39:     function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {
  40:         return uint128(LeftRightUnsigned.unwrap(self));
  41:     }

```

*GitHub* : [39-41](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L39-L41)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.twapFilter(IUniswapV3Pool,uint32) (contracts/libraries/PanopticMath.sol#241-268) should use calldata instead of memory for :- 
	- PanopticMath.twapFilter(IUniswapV3Pool,uint32).univ3pool (contracts/libraries/PanopticMath.sol#241)

/// @audit ************** Possible Issue Line(s) **************
	L#241,  

/// @audit ****************** Affected Code *******************
 241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

```

*GitHub* : [241-268](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L241-L268)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.countLongs(TokenId) (contracts/types/TokenId.sol#404-408) should use calldata instead of memory for :- 
	- TokenIdLibrary.countLongs(TokenId).self (contracts/types/TokenId.sol#404)

/// @audit ************** Possible Issue Line(s) **************
	L#404,  

/// @audit ****************** Affected Code *******************
 404:     function countLongs(TokenId self) internal pure returns (uint256) {
 405:         unchecked {
 406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);
 407:         }
 408:     }

```

*GitHub* : [404-408](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L404-L408)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._burnLiquidity(LiquidityChunk,IUniswapV3Pool) (contracts/SemiFungiblePositionManager.sol#1224-1245) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager._burnLiquidity(LiquidityChunk,IUniswapV3Pool).liquidityChunk (contracts/SemiFungiblePositionManager.sol#1225)
	- SemiFungiblePositionManager._burnLiquidity(LiquidityChunk,IUniswapV3Pool).univ3pool (contracts/SemiFungiblePositionManager.sol#1226)

/// @audit ************** Possible Issue Line(s) **************
	L#1225,  L#1226,  

/// @audit ****************** Affected Code *******************
1224:     function _burnLiquidity(
1225:         LiquidityChunk liquidityChunk,
1226:         IUniswapV3Pool univ3pool
1227:     ) internal returns (LeftRightSigned movedAmounts) {
1228:         // burn that option's liquidity in the Uniswap Pool.
1229:         // This will send the underlying tokens back to the Panoptic Pool (msg.sender)
1230:         (uint256 amount0, uint256 amount1) = univ3pool.burn(
1231:             liquidityChunk.tickLower(),
1232:             liquidityChunk.tickUpper(),
1233:             liquidityChunk.liquidity()
1234:         );
1235: 
1236:         // amount0 The amount of token0 that was sent back to the Panoptic Pool
1237:         // amount1 The amount of token1 that was sent back to the Panoptic Pool
1238:         // no need to safecast to int from uint here as the max position size is int128
1239:         // decrement the amountsOut with burnt amounts. amountsOut = notional value of tokens moved
1240:         unchecked {
1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(
1242:                 -int128(int256(amount1))
1243:             );
1244:         }
1245:     }

```

*GitHub* : [1224-1245](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1224-L1245)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.leftSlot(LeftRightSigned) (contracts/types/LeftRight.sol#108-110) should use calldata instead of memory for :- 
	- LeftRightLibrary.leftSlot(LeftRightSigned).self (contracts/types/LeftRight.sol#108)

/// @audit ************** Possible Issue Line(s) **************
	L#108,  

/// @audit ****************** Affected Code *******************
 108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {
 109:         return int128(LeftRightSigned.unwrap(self) >> 128);
 110:     }

```

*GitHub* : [108-110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L108-L110)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.getPanopticPool(IUniswapV3Pool) (contracts/PanopticFactory.sol#420-422) should use calldata instead of memory for :- 
	- PanopticFactory.getPanopticPool(IUniswapV3Pool).univ3pool (contracts/PanopticFactory.sol#420)

/// @audit ************** Possible Issue Line(s) **************
	L#420,  

/// @audit ****************** Affected Code *******************
 420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {
 421:         return s_getPanopticPool[univ3pool];
 422:     }

```

*GitHub* : [420-422](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L420-L422)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addOptionRatio(TokenId,uint256,uint256) (contracts/types/TokenId.sol#221-232) should use calldata instead of memory for :- 
	- TokenIdLibrary.addOptionRatio(TokenId,uint256,uint256).self (contracts/types/TokenId.sol#222)

/// @audit ************** Possible Issue Line(s) **************
	L#222,  

/// @audit ****************** Affected Code *******************
 221:     function addOptionRatio(
 222:         TokenId self,
 223:         uint256 _optionRatio,
 224:         uint256 legIndex
 225:     ) internal pure returns (TokenId) {
 226:         unchecked {
 227:             return
 228:                 TokenId.wrap(
 229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))
 230:                 );
 231:         }
 232:     }

```

*GitHub* : [221-232](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L221-L232)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.sub(LeftRightUnsigned,LeftRightUnsigned) (contracts/types/LeftRight.sol#171-188) should use calldata instead of memory for :- 
	- LeftRightLibrary.sub(LeftRightUnsigned,LeftRightUnsigned).x (contracts/types/LeftRight.sol#172)
	- LeftRightLibrary.sub(LeftRightUnsigned,LeftRightUnsigned).y (contracts/types/LeftRight.sol#173)

/// @audit ************** Possible Issue Line(s) **************
	L#172,  L#173,  

/// @audit ****************** Affected Code *******************
 171:     function sub(
 172:         LeftRightUnsigned x,
 173:         LeftRightUnsigned y
 174:     ) internal pure returns (LeftRightUnsigned z) {
 175:         unchecked {
 176:             // subtracting leftRight packed uint128's is same as just subtracting the values explictily
 177:             // given that we check for underflows of the left and right values
 178:             z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));
 179: 
 180:             // on underflow z will be greater than either x or y
 181:             // type cast z to uint128 to isolate the right slot and if it's higher than a value that was subtracted from (x)
 182:             // then an underflow has occured
 183:             if (
 184:                 LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||
 185:                 (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))
 186:             ) revert Errors.UnderOverFlow();
 187:         }
 188:     }

```

*GitHub* : [171-188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L171-L188)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128) (contracts/CollateralTracker.sol#1510-1589) should use calldata instead of memory for :- 
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128).tokenId (contracts/CollateralTracker.sol#1511)

/// @audit ************** Possible Issue Line(s) **************
	L#1511,  

/// @audit ****************** Affected Code *******************
1511:         TokenId tokenId,

```

*GitHub* : [1510-1589](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1510-L1589)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getPremia(TokenId,uint128,address,bool,int24) (contracts/PanopticPool.sol#1503-1575) should use calldata instead of memory for :- 
	- PanopticPool._getPremia(TokenId,uint128,address,bool,int24).tokenId (contracts/PanopticPool.sol#1504)

/// @audit ************** Possible Issue Line(s) **************
	L#1504,  

/// @audit ****************** Affected Code *******************
1504:         TokenId tokenId,

```

*GitHub* : [1503-1575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1503-L1575)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightUnsigned,LeftRightUnsigned) (contracts/types/LeftRight.sol#148-165) should use calldata instead of memory for :- 
	- LeftRightLibrary.add(LeftRightUnsigned,LeftRightUnsigned).x (contracts/types/LeftRight.sol#149)
	- LeftRightLibrary.add(LeftRightUnsigned,LeftRightUnsigned).y (contracts/types/LeftRight.sol#150)

/// @audit ************** Possible Issue Line(s) **************
	L#149,  L#150,  

/// @audit ****************** Affected Code *******************
 148:     function add(
 149:         LeftRightUnsigned x,
 150:         LeftRightUnsigned y
 151:     ) internal pure returns (LeftRightUnsigned z) {
 152:         unchecked {
 153:             // adding leftRight packed uint128's is same as just adding the values explictily
 154:             // given that we check for overflows of the left and right values
 155:             z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));
 156: 
 157:             // on overflow z will be less than either x or y
 158:             // type cast z to uint128 to isolate the right slot and if it's lower than a value it's comprised of (x)
 159:             // then an overflow has occured
 160:             if (
 161:                 LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||
 162:                 (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))
 163:             ) revert Errors.UnderOverFlow();
 164:         }
 165:     }

```

*GitHub* : [148-165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L148-L165)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.strike(TokenId,uint256) (contracts/types/TokenId.sol#158-162) should use calldata instead of memory for :- 
	- TokenIdLibrary.strike(TokenId,uint256).self (contracts/types/TokenId.sol#158)

/// @audit ************** Possible Issue Line(s) **************
	L#158,  

/// @audit ****************** Affected Code *******************
 158:     function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {
 159:         unchecked {
 160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));
 161:         }
 162:     }

```

*GitHub* : [158-162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L158-L162)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.toLeftSlot(LeftRightSigned,int128) (contracts/types/LeftRight.sol#134-138) should use calldata instead of memory for :- 
	- LeftRightLibrary.toLeftSlot(LeftRightSigned,int128).self (contracts/types/LeftRight.sol#134)

/// @audit ************** Possible Issue Line(s) **************
	L#134,  

/// @audit ****************** Affected Code *******************
 134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {
 135:         unchecked {
 136:             return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));
 137:         }
 138:     }

```

*GitHub* : [134-138](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L134-L138)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getAmountsForLiquidity(int24,LiquidityChunk) (contracts/libraries/Math.sol#221-233) should use calldata instead of memory for :- 
	- Math.getAmountsForLiquidity(int24,LiquidityChunk).liquidityChunk (contracts/libraries/Math.sol#223)

/// @audit ************** Possible Issue Line(s) **************
	L#223,  

/// @audit ****************** Affected Code *******************
 221:     function getAmountsForLiquidity(
 222:         int24 currentTick,
 223:         LiquidityChunk liquidityChunk
 224:     ) internal pure returns (uint256 amount0, uint256 amount1) {
 225:         if (currentTick <= liquidityChunk.tickLower()) {
 226:             amount0 = getAmount0ForLiquidity(liquidityChunk);
 227:         } else if (currentTick >= liquidityChunk.tickUpper()) {
 228:             amount1 = getAmount1ForLiquidity(liquidityChunk);
 229:         } else {
 230:             amount0 = getAmount0ForLiquidity(liquidityChunk.updateTickLower(currentTick));
 231:             amount1 = getAmount1ForLiquidity(liquidityChunk.updateTickUpper(currentTick));
 232:         }
 233:     }

```

*GitHub* : [221-233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L221-L233)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.startToken(bool,address,address,uint24,PanopticPool) (contracts/CollateralTracker.sol#221-264) should use calldata instead of memory for :- 
	- CollateralTracker.startToken(bool,address,address,uint24,PanopticPool).panopticPool (contracts/CollateralTracker.sol#226)

/// @audit ************** Possible Issue Line(s) **************
	L#226,  

/// @audit ****************** Affected Code *******************
 226:         PanopticPool panopticPool

```

*GitHub* : [221-264](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221-L264)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updatePositionDataBurn(address,TokenId) (contracts/PanopticPool.sol#859-878) should use calldata instead of memory for :- 
	- PanopticPool._updatePositionDataBurn(address,TokenId).tokenId (contracts/PanopticPool.sol#859)

/// @audit ************** Possible Issue Line(s) **************
	L#859,  

/// @audit ****************** Affected Code *******************
 859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {
 860:         // reset balances and delete stored option data
 861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
 862: 
 863:         uint256 numLegs = tokenId.countLegs();
 864:         for (uint256 leg = 0; leg < numLegs; ) {
 865:             if (tokenId.isLong(leg) == 0) {
 866:                 // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
 867:                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
 868:                 _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
 869:             }
 870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
 871:             unchecked {
 872:                 ++leg;
 873:             }
 874:         }
 875: 
 876:         // Update the position list hash (hash = XOR of all keccak256(tokenId)). Remove hash by XOR'ing again
 877:         _updatePositionsHash(owner, tokenId, !ADD);
 878:     }

```

*GitHub* : [859-878](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L859-L878)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getTotalLiquidity(TokenId,uint256) (contracts/PanopticPool.sol#1802-1822) should use calldata instead of memory for :- 
	- PanopticPool._getTotalLiquidity(TokenId,uint256).tokenId (contracts/PanopticPool.sol#1803)

/// @audit ************** Possible Issue Line(s) **************
	L#1803,  

/// @audit ****************** Affected Code *******************
1802:     function _getTotalLiquidity(
1803:         TokenId tokenId,
1804:         uint256 leg
1805:     ) internal view returns (uint256 totalLiquidity) {
1806:         unchecked {
1807:             // totalLiquidity (total sold) = removedLiquidity + netLiquidity
1808: 
1809:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
1810:             uint256 tokenType = tokenId.tokenType(leg);
1811:             LeftRightUnsigned accountLiquidities = SFPM.getAccountLiquidity(
1812:                 address(s_univ3pool),
1813:                 address(this),
1814:                 tokenType,
1815:                 tickLower,
1816:                 tickUpper
1817:             );
1818: 
1819:             // removed + net
1820:             totalLiquidity = accountLiquidities.rightSlot() + accountLiquidities.leftSlot();
1821:         }
1822:     }

```

*GitHub* : [1802-1822](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1802-L1822)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned) (contracts/types/LeftRight.sol#194-208) should use calldata instead of memory for :- 
	- LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned).x (contracts/types/LeftRight.sol#194)
	- LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned).y (contracts/types/LeftRight.sol#194)

/// @audit ************** Possible Issue Line(s) **************
	L#194,  

/// @audit ****************** Affected Code *******************
 194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 195:         unchecked {
 196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();
 197:             int128 left128 = int128(left);
 198: 
 199:             if (left128 != left) revert Errors.UnderOverFlow();
 200: 
 201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();
 202:             int128 right128 = int128(right);
 203: 
 204:             if (right128 != right) revert Errors.UnderOverFlow();
 205: 
 206:             return z.toRightSlot(right128).toLeftSlot(left128);
 207:         }
 208:     }

```

*GitHub* : [194-208](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L194-L208)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.countLegs(TokenId) (contracts/types/TokenId.sol#432-449) should use calldata instead of memory for :- 
	- TokenIdLibrary.countLegs(TokenId).self (contracts/types/TokenId.sol#432)

/// @audit ************** Possible Issue Line(s) **************
	L#432,  

/// @audit ****************** Affected Code *******************
 432:     function countLegs(TokenId self) internal pure returns (uint256) {
 433:         // Strip all bits except for the option ratios
 434:         uint256 optionRatios = TokenId.unwrap(self) & OPTION_RATIO_MASK;
 435: 
 436:         // The legs are filled in from least to most significant
 437:         // Each comparison here is to the start of the next leg's option ratio section
 438:         // Since only the option ratios remain, we can be sure that no bits above the start of the inactive legs will be 1
 439:         if (optionRatios < 2 ** 64) {
 440:             return 0;
 441:         } else if (optionRatios < 2 ** 112) {
 442:             return 1;
 443:         } else if (optionRatios < 2 ** 160) {
 444:             return 2;
 445:         } else if (optionRatios < 2 ** 208) {
 446:             return 3;
 447:         }
 448:         return 4;
 449:     }

```

*GitHub* : [432-449](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L432-L449)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) should use calldata instead of memory for :- 
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).univ3pool (contracts/libraries/PanopticMath.sol#173)

/// @audit ************** Possible Issue Line(s) **************
	L#173,  

/// @audit ****************** Affected Code *******************
 173:         IUniswapV3Pool univ3pool

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.burnOptions(TokenId,TokenId[],int24,int24) (contracts/PanopticPool.sol#569-578) should use calldata instead of memory for :- 
	- PanopticPool.burnOptions(TokenId,TokenId[],int24,int24).tokenId (contracts/PanopticPool.sol#570)

/// @audit ************** Possible Issue Line(s) **************
	L#570,  

/// @audit ****************** Affected Code *******************
 569:     function burnOptions(
 570:         TokenId tokenId,
 571:         TokenId[] calldata newPositionIdList,
 572:         int24 tickLimitLow,
 573:         int24 tickLimitHigh
 574:     ) external {
 575:         _burnOptions(COMMIT_LONG_SETTLED, tokenId, msg.sender, tickLimitLow, tickLimitHigh);
 576: 
 577:         _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);
 578:     }

```

*GitHub* : [569-578](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L569-L578)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.liquidity(LiquidityChunk) (contracts/types/LiquidityChunk.sol#189-193) should use calldata instead of memory for :- 
	- LiquidityChunkLibrary.liquidity(LiquidityChunk).self (contracts/types/LiquidityChunk.sol#189)

/// @audit ************** Possible Issue Line(s) **************
	L#189,  

/// @audit ****************** Affected Code *******************
 189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {
 190:         unchecked {
 191:             return uint128(LiquidityChunk.unwrap(self));
 192:         }
 193:     }

```

*GitHub* : [189-193](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L189-L193)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightSigned,LeftRightSigned) (contracts/types/LeftRight.sol#214-226) should use calldata instead of memory for :- 
	- LeftRightLibrary.add(LeftRightSigned,LeftRightSigned).x (contracts/types/LeftRight.sol#214)
	- LeftRightLibrary.add(LeftRightSigned,LeftRightSigned).y (contracts/types/LeftRight.sol#214)

/// @audit ************** Possible Issue Line(s) **************
	L#214,  

/// @audit ****************** Affected Code *******************
 214:     function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 215:         unchecked {
 216:             int256 left256 = int256(x.leftSlot()) + y.leftSlot();
 217:             int128 left128 = int128(left256);
 218: 
 219:             int256 right256 = int256(x.rightSlot()) + y.rightSlot();
 220:             int128 right128 = int128(right256);
 221: 
 222:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
 223: 
 224:             return z.toRightSlot(right128).toLeftSlot(left128);
 225:         }
 226:     }

```

*GitHub* : [214-226](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L214-L226)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addAsset(TokenId,uint256,uint256) (contracts/types/TokenId.sol#205-214) should use calldata instead of memory for :- 
	- TokenIdLibrary.addAsset(TokenId,uint256,uint256).self (contracts/types/TokenId.sol#206)

/// @audit ************** Possible Issue Line(s) **************
	L#206,  

/// @audit ****************** Affected Code *******************
 205:     function addAsset(
 206:         TokenId self,
 207:         uint256 _asset,
 208:         uint256 legIndex
 209:     ) internal pure returns (TokenId) {
 210:         unchecked {
 211:             return
 212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));
 213:         }
 214:     }

```

*GitHub* : [205-214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L205-L214)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128) (contracts/PanopticPool.sol#1666-1746) should use calldata instead of memory for :- 
	- PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128).tokenId (contracts/PanopticPool.sol#1667)
	- PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128).collectedByLeg (contracts/PanopticPool.sol#1668)

/// @audit ************** Possible Issue Line(s) **************
	L#1667,  L#1668,  

/// @audit ****************** Affected Code *******************
1667:         TokenId tokenId,
1668:         LeftRightUnsigned[4] memory collectedByLeg,

```

*GitHub* : [1666-1746](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1666-L1746)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._mintLiquidity(LiquidityChunk,IUniswapV3Pool) (contracts/SemiFungiblePositionManager.sol#1185-1217) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager._mintLiquidity(LiquidityChunk,IUniswapV3Pool).liquidityChunk (contracts/SemiFungiblePositionManager.sol#1186)
	- SemiFungiblePositionManager._mintLiquidity(LiquidityChunk,IUniswapV3Pool).univ3pool (contracts/SemiFungiblePositionManager.sol#1187)

/// @audit ************** Possible Issue Line(s) **************
	L#1186,  L#1187,  

/// @audit ****************** Affected Code *******************
1186:         LiquidityChunk liquidityChunk,
1187:         IUniswapV3Pool univ3pool

```

*GitHub* : [1185-1217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1185-L1217)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralAtTickSinglePosition(TokenId,uint128,int24,uint128) (contracts/CollateralTracker.sol#1245-1268) should use calldata instead of memory for :- 
	- CollateralTracker._getRequiredCollateralAtTickSinglePosition(TokenId,uint128,int24,uint128).tokenId (contracts/CollateralTracker.sol#1246)

/// @audit ************** Possible Issue Line(s) **************
	L#1246,  

/// @audit ****************** Affected Code *******************
1245:     function _getRequiredCollateralAtTickSinglePosition(
1246:         TokenId tokenId,
1247:         uint128 positionSize,
1248:         int24 atTick,
1249:         uint128 poolUtilization
1250:     ) internal view returns (uint256 tokenRequired) {
1251:         bool underlyingIsToken0 = s_underlyingIsToken0;
1252:         uint256 numLegs = tokenId.countLegs();
1253: 
1254:         unchecked {
1255:             for (uint256 index = 0; index < numLegs; ++index) {
1256:                 // revert if the tokenType does not match the current collateral token
1257:                 if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;
1258:                 // Increment the tokenRequired accumulator
1259:                 tokenRequired += _getRequiredCollateralSingleLeg(
1260:                     tokenId,
1261:                     index,
1262:                     positionSize,
1263:                     atTick,
1264:                     poolUtilization
1265:                 );
1266:             }
1267:         }
1268:     }

```

*GitHub* : [1245-1268](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1245-L1268)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]) (contracts/PanopticPool.sol#1757-1796) should use calldata instead of memory for :- 
	- PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]).settledTokens (contracts/PanopticPool.sol#1759)
	- PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]).grossPremiumLast (contracts/PanopticPool.sol#1760)
	- PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]).premiumOwed (contracts/PanopticPool.sol#1761)
	- PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]).premiumAccumulators (contracts/PanopticPool.sol#1762)

/// @audit ************** Possible Issue Line(s) **************
	L#1759,  L#1760,  L#1761,  L#1762,  

/// @audit ****************** Affected Code *******************
1759:         LeftRightUnsigned settledTokens,
1760:         LeftRightUnsigned grossPremiumLast,
1761:         LeftRightUnsigned premiumOwed,
1762:         uint256[2] memory premiumAccumulators

```

*GitHub* : [1757-1796](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1757-L1796)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getAmount1ForLiquidity(LiquidityChunk) (contracts/libraries/Math.sol#207-214) should use calldata instead of memory for :- 
	- Math.getAmount1ForLiquidity(LiquidityChunk).liquidityChunk (contracts/libraries/Math.sol#207)

/// @audit ************** Possible Issue Line(s) **************
	L#207,  

/// @audit ****************** Affected Code *******************
 207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
 208:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
 209:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());
 210: 
 211:         unchecked {
 212:             return mulDiv96(liquidityChunk.liquidity(), highPriceX96 - lowPriceX96);
 213:         }
 214:     }

```

*GitHub* : [207-214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L207-L214)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.updateTickLower(LiquidityChunk,int24) (contracts/types/LiquidityChunk.sol#135-145) should use calldata instead of memory for :- 
	- LiquidityChunkLibrary.updateTickLower(LiquidityChunk,int24).self (contracts/types/LiquidityChunk.sol#136)

/// @audit ************** Possible Issue Line(s) **************
	L#136,  

/// @audit ****************** Affected Code *******************
 135:     function updateTickLower(
 136:         LiquidityChunk self,
 137:         int24 _tickLower
 138:     ) internal pure returns (LiquidityChunk) {
 139:         unchecked {
 140:             return
 141:                 LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TL_MASK).addTickLower(
 142:                     _tickLower
 143:                 );
 144:         }
 145:     }

```

*GitHub* : [135-145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L135-L145)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address) (contracts/PanopticFactory.sol#115-130) should use calldata instead of memory for :- 
	- PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._SFPM (contracts/PanopticFactory.sol#117)
	- PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._univ3Factory (contracts/PanopticFactory.sol#118)
	- PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._donorNFT (contracts/PanopticFactory.sol#119)

/// @audit ************** Possible Issue Line(s) **************
	L#117,  L#118,  L#119,  

/// @audit ****************** Affected Code *******************
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

*GitHub* : [115-130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L115-L130)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) should use calldata instead of memory for :- 
	- PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).positionIdList (contracts/libraries/PanopticMath.sol#770)
	- PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).premiasByLeg (contracts/libraries/PanopticMath.sol#771)
	- PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateralRemaining (contracts/libraries/PanopticMath.sol#772)
	- PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateral0 (contracts/libraries/PanopticMath.sol#773)
	- PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateral1 (contracts/libraries/PanopticMath.sol#774)

/// @audit ************** Possible Issue Line(s) **************
	L#770,  L#771,  L#772,  L#773,  L#774,  

/// @audit ****************** Affected Code *******************
 770:         TokenId[] memory positionIdList,
 771:         LeftRightSigned[4][] memory premiasByLeg,
 772:         LeftRightSigned collateralRemaining,
 773:         CollateralTracker collateral0,
 774:         CollateralTracker collateral1,

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._createPositionInAMM(IUniswapV3Pool,TokenId,uint128,bool) (contracts/SemiFungiblePositionManager.sol#863-941) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager._createPositionInAMM(IUniswapV3Pool,TokenId,uint128,bool).univ3pool (contracts/SemiFungiblePositionManager.sol#864)
	- SemiFungiblePositionManager._createPositionInAMM(IUniswapV3Pool,TokenId,uint128,bool).tokenId (contracts/SemiFungiblePositionManager.sol#865)

/// @audit ************** Possible Issue Line(s) **************
	L#864,  L#865,  

/// @audit ****************** Affected Code *******************
 864:         IUniswapV3Pool univ3pool,
 865:         TokenId tokenId,

```

*GitHub* : [863-941](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L863-L941)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addTokenType(TokenId,uint256,uint256) (contracts/types/TokenId.sol#255-266) should use calldata instead of memory for :- 
	- TokenIdLibrary.addTokenType(TokenId,uint256,uint256).self (contracts/types/TokenId.sol#256)

/// @audit ************** Possible Issue Line(s) **************
	L#256,  

/// @audit ****************** Affected Code *******************
 255:     function addTokenType(
 256:         TokenId self,
 257:         uint256 _tokenType,
 258:         uint256 legIndex
 259:     ) internal pure returns (TokenId) {
 260:         unchecked {
 261:             return
 262:                 TokenId.wrap(
 263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))
 264:                 );
 265:         }
 266:     }

```

*GitHub* : [255-266](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L255-L266)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.rightSlot(LeftRightSigned) (contracts/types/LeftRight.sol#46-48) should use calldata instead of memory for :- 
	- LeftRightLibrary.rightSlot(LeftRightSigned).self (contracts/types/LeftRight.sol#46)

/// @audit ************** Possible Issue Line(s) **************
	L#46,  

/// @audit ****************** Affected Code *******************
  46:     function rightSlot(LeftRightSigned self) internal pure returns (int128) {
  47:         return int128(LeftRightSigned.unwrap(self));
  48:     }

```

*GitHub* : [46-48](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L46-L48)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.asset(TokenId,uint256) (contracts/types/TokenId.sol#108-112) should use calldata instead of memory for :- 
	- TokenIdLibrary.asset(TokenId,uint256).self (contracts/types/TokenId.sol#108)

/// @audit ************** Possible Issue Line(s) **************
	L#108,  

/// @audit ****************** Affected Code *******************
 108:     function asset(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 109:         unchecked {
 110:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);
 111:         }
 112:     }

```

*GitHub* : [108-112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L108-L112)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._burnOptions(bool,TokenId,address,int24,int24) (contracts/PanopticPool.sol#826-854) should use calldata instead of memory for :- 
	- PanopticPool._burnOptions(bool,TokenId,address,int24,int24).tokenId (contracts/PanopticPool.sol#828)

/// @audit ************** Possible Issue Line(s) **************
	L#828,  

/// @audit ****************** Affected Code *******************
 828:         TokenId tokenId,

```

*GitHub* : [826-854](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L826-L854)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.updatePositionsHash(uint256,TokenId,bool) (contracts/libraries/PanopticMath.sol#92-110) should use calldata instead of memory for :- 
	- PanopticMath.updatePositionsHash(uint256,TokenId,bool).tokenId (contracts/libraries/PanopticMath.sol#94)

/// @audit ************** Possible Issue Line(s) **************
	L#94,  

/// @audit ****************** Affected Code *******************
  92:     function updatePositionsHash(
  93:         uint256 existingHash,
  94:         TokenId tokenId,
  95:         bool addFlag
  96:     ) internal pure returns (uint256) {
  97:         // add the XOR`ed hash of the single option position `tokenId` to the `existingHash`
  98:         // @dev 0 ^ x = x
  99: 
 100:         unchecked {
 101:             // update hash by taking the XOR of the new tokenId
 102:             uint248 updatedHash = uint248(existingHash) ^
 103:                 (uint248(uint256(keccak256(abi.encode(tokenId)))));
 104:             // increment the top 8 bit if addflag=true, decrement otherwise
 105:             return
 106:                 addFlag
 107:                     ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)
 108:                     : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);
 109:         }
 110:     }

```

*GitHub* : [92-110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L92-L110)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24) (contracts/PanopticFactory.sol#335-411) should use calldata instead of memory for :- 
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).v3Pool (contracts/PanopticFactory.sol#336)

/// @audit ************** Possible Issue Line(s) **************
	L#336,  

/// @audit ****************** Affected Code *******************
 336:         IUniswapV3Pool v3Pool,

```

*GitHub* : [335-411](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L335-L411)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._updateStoredPremia(bytes32,LeftRightUnsigned,LeftRightUnsigned) (contracts/SemiFungiblePositionManager.sol#1110-1130) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager._updateStoredPremia(bytes32,LeftRightUnsigned,LeftRightUnsigned).currentLiquidity (contracts/SemiFungiblePositionManager.sol#1112)
	- SemiFungiblePositionManager._updateStoredPremia(bytes32,LeftRightUnsigned,LeftRightUnsigned).collectedAmounts (contracts/SemiFungiblePositionManager.sol#1113)

/// @audit ************** Possible Issue Line(s) **************
	L#1112,  L#1113,  

/// @audit ****************** Affected Code *******************
1110:     function _updateStoredPremia(
1111:         bytes32 positionKey,
1112:         LeftRightUnsigned currentLiquidity,
1113:         LeftRightUnsigned collectedAmounts
1114:     ) private {
1115:         (
1116:             LeftRightUnsigned deltaPremiumOwed,
1117:             LeftRightUnsigned deltaPremiumGross
1118:         ) = _getPremiaDeltas(currentLiquidity, collectedAmounts);
1119: 
1120:         // add deltas to accumulators and freeze both accumulators (for a token) if one of them overflows
1121:         // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)
1122:         // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing
1123:         (s_accountPremiumOwed[positionKey], s_accountPremiumGross[positionKey]) = LeftRightLibrary
1124:             .addCapped(
1125:                 s_accountPremiumOwed[positionKey],
1126:                 deltaPremiumOwed,
1127:                 s_accountPremiumGross[positionKey],
1128:                 deltaPremiumGross
1129:             );
1130:     }

```

*GitHub* : [1110-1130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1110-L1130)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.toLeftSlot(LeftRightUnsigned,uint128) (contracts/types/LeftRight.sol#121-128) should use calldata instead of memory for :- 
	- LeftRightLibrary.toLeftSlot(LeftRightUnsigned,uint128).self (contracts/types/LeftRight.sol#122)

/// @audit ************** Possible Issue Line(s) **************
	L#122,  

/// @audit ****************** Affected Code *******************
 121:     function toLeftSlot(
 122:         LeftRightUnsigned self,
 123:         uint128 left
 124:     ) internal pure returns (LeftRightUnsigned) {
 125:         unchecked {
 126:             return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));
 127:         }
 128:     }

```

*GitHub* : [121-128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L121-L128)

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

/// @audit ******************* Issue Detail *******************
IDonorNFT.issueNFT(address,PanopticPool,address,address,uint24) (contracts/tokens/interfaces/IDonorNFT.sol#13-19) should use calldata instead of memory for :- 
	- IDonorNFT.issueNFT(address,PanopticPool,address,address,uint24).newPoolContract (contracts/tokens/interfaces/IDonorNFT.sol#15)

/// @audit ************** Possible Issue Line(s) **************
	L#15,  

/// @audit ****************** Affected Code *******************
  13:     function issueNFT(
  14:         address deployer,
  15:         PanopticPool newPoolContract,
  16:         address token0,
  17:         address token1,
  18:         uint24 fee
  19:     ) external;

```

*GitHub* : [13-19](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IDonorNFT.sol#L13-L19)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.clearLeg(TokenId,uint256) (contracts/types/TokenId.sol#464-491) should use calldata instead of memory for :- 
	- TokenIdLibrary.clearLeg(TokenId,uint256).self (contracts/types/TokenId.sol#464)

/// @audit ************** Possible Issue Line(s) **************
	L#464,  

/// @audit ****************** Affected Code *******************
 464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```

*GitHub* : [464-491](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L464-L491)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getAmount0ForLiquidity(LiquidityChunk) (contracts/libraries/Math.sol#191-202) should use calldata instead of memory for :- 
	- Math.getAmount0ForLiquidity(LiquidityChunk).liquidityChunk (contracts/libraries/Math.sol#191)

/// @audit ************** Possible Issue Line(s) **************
	L#191,  

/// @audit ****************** Affected Code *******************
 191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
 192:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
 193:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());
 194:         unchecked {
 195:             return
 196:                 mulDiv(
 197:                     uint256(liquidityChunk.liquidity()) << 96,
 198:                     highPriceX96 - lowPriceX96,
 199:                     highPriceX96
 200:                 ) / lowPriceX96;
 201:         }
 202:     }

```

*GitHub* : [191-202](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L191-L202)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addRiskPartner(TokenId,uint256,uint256) (contracts/types/TokenId.sol#273-284) should use calldata instead of memory for :- 
	- TokenIdLibrary.addRiskPartner(TokenId,uint256,uint256).self (contracts/types/TokenId.sol#274)

/// @audit ************** Possible Issue Line(s) **************
	L#274,  

/// @audit ****************** Affected Code *******************
 273:     function addRiskPartner(
 274:         TokenId self,
 275:         uint256 _riskPartner,
 276:         uint256 legIndex
 277:     ) internal pure returns (TokenId) {
 278:         unchecked {
 279:             return
 280:                 TokenId.wrap(
 281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))
 282:                 );
 283:         }
 284:     }

```

*GitHub* : [273-284](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L273-L284)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.validate(TokenId) (contracts/types/TokenId.sol#500-571) should use calldata instead of memory for :- 
	- TokenIdLibrary.validate(TokenId).self (contracts/types/TokenId.sol#500)

/// @audit ************** Possible Issue Line(s) **************
	L#500,  

/// @audit ****************** Affected Code *******************
 500:     function validate(TokenId self) internal pure {

```

*GitHub* : [500-571](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L500-L571)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker) (contracts/PanopticPool.sol#291-327) should use calldata instead of memory for :- 
	- PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker)._univ3pool (contracts/PanopticPool.sol#292)
	- PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker).collateralTracker0 (contracts/PanopticPool.sol#295)
	- PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker).collateralTracker1 (contracts/PanopticPool.sol#296)

/// @audit ************** Possible Issue Line(s) **************
	L#292,  L#295,  L#296,  

/// @audit ****************** Affected Code *******************
 292:         IUniswapV3Pool _univ3pool,
 295:         CollateralTracker collateralTracker0,
 296:         CollateralTracker collateralTracker1

```

*GitHub* : [291-327](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L327)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,int24) (contracts/libraries/PanopticMath.sol#445-453) should use calldata instead of memory for :- 
	- PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,int24).tokenData0 (contracts/libraries/PanopticMath.sol#446)
	- PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,int24).tokenData1 (contracts/libraries/PanopticMath.sol#447)

/// @audit ************** Possible Issue Line(s) **************
	L#446,  L#447,  

/// @audit ****************** Affected Code *******************
 445:     function convertCollateralData(
 446:         LeftRightUnsigned tokenData0,
 447:         LeftRightUnsigned tokenData1,
 448:         uint256 tokenType,
 449:         int24 tick
 450:     ) internal pure returns (uint256, uint256) {
 451:         return
 452:             convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));
 453:     }

```

*GitHub* : [445-453](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L445-L453)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._addUserOption(TokenId,uint64) (contracts/PanopticPool.sol#739-782) should use calldata instead of memory for :- 
	- PanopticPool._addUserOption(TokenId,uint64).tokenId (contracts/PanopticPool.sol#739)

/// @audit ************** Possible Issue Line(s) **************
	L#739,  

/// @audit ****************** Affected Code *******************
 739:     function _addUserOption(TokenId tokenId, uint64 effectiveLiquidityLimitX32) internal {

```

*GitHub* : [739-782](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L739-L782)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.validateIsExercisable(TokenId,int24) (contracts/types/TokenId.sol#578-599) should use calldata instead of memory for :- 
	- TokenIdLibrary.validateIsExercisable(TokenId,int24).self (contracts/types/TokenId.sol#578)

/// @audit ************** Possible Issue Line(s) **************
	L#578,  

/// @audit ****************** Affected Code *******************
 578:     function validateIsExercisable(TokenId self, int24 currentTick) internal pure {
 579:         unchecked {
 580:             uint256 numLegs = self.countLegs();
 581:             for (uint256 i = 0; i < numLegs; ++i) {
 582:                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(
 583:                     self.width(i),
 584:                     self.tickSpacing()
 585:                 );
 586: 
 587:                 int24 _strike = self.strike(i);
 588:                 // check if the price is outside this chunk
 589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {
 590:                     // if this leg is long and the price beyond the leg's range:
 591:                     // this exercised ID, `self`, appears valid
 592:                     if (self.isLong(i) == 1) return; // validated
 593:                 }
 594:             }
 595:         }
 596: 
 597:         // Fail if position has no legs that is far-out-of-the-money
 598:         revert Errors.NoLegsExercisable();
 599:     }

```

*GitHub* : [578-599](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L578-L599)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1600-1649) should use calldata instead of memory for :- 
	- CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128).tokenId (contracts/CollateralTracker.sol#1601)

/// @audit ************** Possible Issue Line(s) **************
	L#1601,  

/// @audit ****************** Affected Code *******************
1601:         TokenId tokenId,

```

*GitHub* : [1600-1649](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1600-L1649)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.calculateAMMSwapFees(IUniswapV3Pool,int24,int24,int24,uint128) (contracts/libraries/FeesCalc.sol#97-119) should use calldata instead of memory for :- 
	- FeesCalc.calculateAMMSwapFees(IUniswapV3Pool,int24,int24,int24,uint128).univ3pool (contracts/libraries/FeesCalc.sol#98)

/// @audit ************** Possible Issue Line(s) **************
	L#98,  

/// @audit ****************** Affected Code *******************
  97:     function calculateAMMSwapFees(
  98:         IUniswapV3Pool univ3pool,
  99:         int24 currentTick,
 100:         int24 tickLower,
 101:         int24 tickUpper,
 102:         uint128 liquidity
 103:     ) public view returns (LeftRightSigned) {
 104:         // extract the amount of AMM fees collected within the liquidity chunk`
 105:         // note: the fee variables are *per unit of liquidity*; so more "rate" variables
 106:         (
 107:             uint256 ammFeesPerLiqToken0X128,
 108:             uint256 ammFeesPerLiqToken1X128
 109:         ) = _getAMMSwapFeesPerLiquidityCollected(univ3pool, currentTick, tickLower, tickUpper);
 110: 
 111:         // Use the fee growth (rate) variable to compute the absolute fees accumulated within the chunk:
 112:         //   ammFeesToken0X128 * liquidity / (2**128)
 113:         // to store the (absolute) fees as int128:
 114:         return
 115:             LeftRightSigned
 116:                 .wrap(0)
 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))
 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));
 119:     }

```

*GitHub* : [97-119](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L97-L119)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.constructor(SemiFungiblePositionManager) (contracts/PanopticPool.sol#280-282) should use calldata instead of memory for :- 
	- PanopticPool.constructor(SemiFungiblePositionManager)._sfpm (contracts/PanopticPool.sol#280)

/// @audit ************** Possible Issue Line(s) **************
	L#280,  

/// @audit ****************** Affected Code *******************
 280:     constructor(SemiFungiblePositionManager _sfpm) {
 281:         SFPM = _sfpm;
 282:     }

```

*GitHub* : [280-282](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L280-L282)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) should use calldata instead of memory for :- 
	- PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool).tokenId (contracts/PanopticPool.sol#1835)
	- PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool).collectedByLeg (contracts/PanopticPool.sol#1836)

/// @audit ************** Possible Issue Line(s) **************
	L#1835,  L#1836,  

/// @audit ****************** Affected Code *******************
1835:         TokenId tokenId,
1836:         LeftRightUnsigned[4] memory collectedByLeg,

```

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.tokenType(TokenId,uint256) (contracts/types/TokenId.sol#138-142) should use calldata instead of memory for :- 
	- TokenIdLibrary.tokenType(TokenId,uint256).self (contracts/types/TokenId.sol#138)

/// @audit ************** Possible Issue Line(s) **************
	L#138,  

/// @audit ****************** Affected Code *******************
 138:     function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 139:         unchecked {
 140:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);
 141:         }
 142:     }

```

*GitHub* : [138-142](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L138-L142)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.optionPositionBalance(address,TokenId) (contracts/PanopticPool.sol#352-371) should use calldata instead of memory for :- 
	- PanopticPool.optionPositionBalance(address,TokenId).tokenId (contracts/PanopticPool.sol#354)

/// @audit ************** Possible Issue Line(s) **************
	L#354,  

/// @audit ****************** Affected Code *******************
 352:     function optionPositionBalance(
 353:         address user,
 354:         TokenId tokenId
 355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {
 356:         // Extract the data stored in s_positionBalance for the provided user + tokenId
 357:         LeftRightUnsigned balanceData = s_positionBalance[user][tokenId];
 358: 
 359:         // Return the unpacked data: balanceOf(user, tokenId) and packed pool utilizations at the time of minting
 360:         balance = balanceData.rightSlot();
 361: 
 362:         // pool utilizations are packed into a single uint128
 363: 
 364:         // the 64 least significant bits are the utilization of token0, so we can simply cast to uint64 to extract it
 365:         // (cutting off the 64 most significant bits)
 366:         poolUtilization0 = uint64(balanceData.leftSlot());
 367: 
 368:         // the 64 most significant bits are the utilization of token1, so we can shift the number to the right by 64 to extract it
 369:         // (shifting away the 64 least significant bits)
 370:         poolUtilization1 = uint64(balanceData.leftSlot() >> 64);
 371:     }

```

*GitHub* : [352-371](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L352-L371)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) should use calldata instead of memory for :- 
	- PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).delegations (contracts/PanopticPool.sol#1020)

/// @audit ************** Possible Issue Line(s) **************
	L#1020,  

/// @audit ****************** Affected Code *******************
1020:         LeftRightUnsigned delegations,

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.addLiquidity(LiquidityChunk,uint128) (contracts/types/LiquidityChunk.sol#89-96) should use calldata instead of memory for :- 
	- LiquidityChunkLibrary.addLiquidity(LiquidityChunk,uint128).self (contracts/types/LiquidityChunk.sol#90)

/// @audit ************** Possible Issue Line(s) **************
	L#90,  

/// @audit ****************** Affected Code *******************
  89:     function addLiquidity(
  90:         LiquidityChunk self,
  91:         uint128 amount
  92:     ) internal pure returns (LiquidityChunk) {
  93:         unchecked {
  94:             return LiquidityChunk.wrap(LiquidityChunk.unwrap(self) + amount);
  95:         }
  96:     }

```

*GitHub* : [89-96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L89-L96)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#958-1104) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).univ3pool (contracts/SemiFungiblePositionManager.sol#959)
	- SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).tokenId (contracts/SemiFungiblePositionManager.sol#960)
	- SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).liquidityChunk (contracts/SemiFungiblePositionManager.sol#962)

/// @audit ************** Possible Issue Line(s) **************
	L#959,  L#960,  L#962,  

/// @audit ****************** Affected Code *******************
 959:         IUniswapV3Pool univ3pool,
 960:         TokenId tokenId,
 962:         LiquidityChunk liquidityChunk,

```

*GitHub* : [958-1104](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L958-L1104)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.riskPartner(TokenId,uint256) (contracts/types/TokenId.sol#148-152) should use calldata instead of memory for :- 
	- TokenIdLibrary.riskPartner(TokenId,uint256).self (contracts/types/TokenId.sol#148)

/// @audit ************** Possible Issue Line(s) **************
	L#148,  

/// @audit ****************** Affected Code *******************
 148:     function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 149:         unchecked {
 150:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);
 151:         }
 152:     }

```

*GitHub* : [148-152](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L148-L152)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getSolvencyBalances(LeftRightUnsigned,LeftRightUnsigned,uint160) (contracts/PanopticPool.sol#1339-1356) should use calldata instead of memory for :- 
	- PanopticPool._getSolvencyBalances(LeftRightUnsigned,LeftRightUnsigned,uint160).tokenData0 (contracts/PanopticPool.sol#1340)
	- PanopticPool._getSolvencyBalances(LeftRightUnsigned,LeftRightUnsigned,uint160).tokenData1 (contracts/PanopticPool.sol#1341)

/// @audit ************** Possible Issue Line(s) **************
	L#1340,  L#1341,  

/// @audit ****************** Affected Code *******************
1339:     function _getSolvencyBalances(
1340:         LeftRightUnsigned tokenData0,
1341:         LeftRightUnsigned tokenData1,
1342:         uint160 sqrtPriceX96
1343:     ) internal pure returns (uint256 balanceCross, uint256 thresholdCross) {
1344:         unchecked {
1345:             // the cross-collateral balance, computed in terms of liquidity X*√P + Y/√P
1346:             // We use mulDiv to compute Y/√P + X*√P while correctly handling overflows, round down
1347:             balanceCross =
1348:                 Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +
1349:                 Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);
1350:             // the amount of cross-collateral balance needed for the account to be solvent, computed in terms of liquidity
1351:             // overstimate by rounding up
1352:             thresholdCross =
1353:                 Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +
1354:                 Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);
1355:         }
1356:     }

```

*GitHub* : [1339-1356](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1339-L1356)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned) (contracts/types/LeftRight.sol#279-301) should use calldata instead of memory for :- 
	- LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned).x (contracts/types/LeftRight.sol#280)
	- LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned).dx (contracts/types/LeftRight.sol#281)
	- LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned).y (contracts/types/LeftRight.sol#282)
	- LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned).dy (contracts/types/LeftRight.sol#283)

/// @audit ************** Possible Issue Line(s) **************
	L#280,  L#281,  L#282,  L#283,  

/// @audit ****************** Affected Code *******************
 279:     function addCapped(
 280:         LeftRightUnsigned x,
 281:         LeftRightUnsigned dx,
 282:         LeftRightUnsigned y,
 283:         LeftRightUnsigned dy
 284:     ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {
 285:         uint128 z_xR = (uint256(x.rightSlot()) + dx.rightSlot()).toUint128Capped();
 286:         uint128 z_xL = (uint256(x.leftSlot()) + dx.leftSlot()).toUint128Capped();
 287:         uint128 z_yR = (uint256(y.rightSlot()) + dy.rightSlot()).toUint128Capped();
 288:         uint128 z_yL = (uint256(y.leftSlot()) + dy.leftSlot()).toUint128Capped();
 289: 
 290:         bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);
 291:         bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);
 292: 
 293:         return (
 294:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(
 295:                 l_Enabled ? z_xL : x.leftSlot()
 296:             ),
 297:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(
 298:                 l_Enabled ? z_yL : y.leftSlot()
 299:             )
 300:         );
 301:     }

```

*GitHub* : [279-301](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L279-L301)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._mintInSFPMAndUpdateCollateral(TokenId,uint128,int24,int24) (contracts/PanopticPool.sol#677-696) should use calldata instead of memory for :- 
	- PanopticPool._mintInSFPMAndUpdateCollateral(TokenId,uint128,int24,int24).tokenId (contracts/PanopticPool.sol#678)

/// @audit ************** Possible Issue Line(s) **************
	L#678,  

/// @audit ****************** Affected Code *******************
 677:     function _mintInSFPMAndUpdateCollateral(
 678:         TokenId tokenId,
 679:         uint128 positionSize,
 680:         int24 tickLimitLow,
 681:         int24 tickLimitHigh
 682:     ) internal returns (uint128) {
 683:         // Mint position by using the SFPM. totalSwapped will reflect tokens swapped because of minting ITM.
 684:         // Switch order of tickLimits to create "swapAtMint" flag
 685:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 686:             .mintTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 687: 
 688:         // update premium settlement info
 689:         _updateSettlementPostMint(tokenId, collectedByLeg, positionSize);
 690: 
 691:         // pay commission based on total moved amount (long + short)
 692:         // write data about inAMM in collateralBase
 693:         uint128 poolUtilizations = _payCommissionAndWriteData(tokenId, positionSize, totalSwapped);
 694: 
 695:         return poolUtilizations;
 696:     }

```

*GitHub* : [677-696](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L677-L696)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addWidth(TokenId,int24,uint256) (contracts/types/TokenId.sol#310-323) should use calldata instead of memory for :- 
	- TokenIdLibrary.addWidth(TokenId,int24,uint256).self (contracts/types/TokenId.sol#311)

/// @audit ************** Possible Issue Line(s) **************
	L#311,  

/// @audit ****************** Affected Code *******************
 310:     function addWidth(
 311:         TokenId self,
 312:         int24 _width,
 313:         uint256 legIndex
 314:     ) internal pure returns (TokenId) {
 315:         // % 4096 -> take 12 bits from the incoming 24 bits (there's no uint12)
 316:         unchecked {
 317:             return
 318:                 TokenId.wrap(
 319:                     TokenId.unwrap(self) +
 320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))
 321:                 );
 322:         }
 323:     }

```

*GitHub* : [310-323](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L310-L323)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._burnAndHandleExercise(bool,int24,int24,TokenId,uint128,address) (contracts/PanopticPool.sol#955-1005) should use calldata instead of memory for :- 
	- PanopticPool._burnAndHandleExercise(bool,int24,int24,TokenId,uint128,address).tokenId (contracts/PanopticPool.sol#959)

/// @audit ************** Possible Issue Line(s) **************
	L#959,  

/// @audit ****************** Affected Code *******************
 959:         TokenId tokenId,

```

*GitHub* : [955-1005](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L955-L1005)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.sort(int256[]) (contracts/libraries/Math.sol#776-781) should use calldata instead of memory for :- 
	- Math.sort(int256[]).data (contracts/libraries/Math.sol#776)

/// @audit ************** Possible Issue Line(s) **************
	L#776,  

/// @audit ****************** Affected Code *******************
 776:     function sort(int256[] memory data) internal pure returns (int256[] memory) {
 777:         unchecked {
 778:             quickSort(data, int256(0), int256(data.length - 1));
 779:         }
 780:         return data;
 781:     }

```

*GitHub* : [776-781](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L776-L781)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1311-1422) should use calldata instead of memory for :- 
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).tokenId (contracts/CollateralTracker.sol#1312)

/// @audit ************** Possible Issue Line(s) **************
	L#1312,  

/// @audit ****************** Affected Code *******************
1312:         TokenId tokenId,

```

*GitHub* : [1311-1422](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1311-L1422)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned) (contracts/libraries/PanopticMath.sol#651-754) should use calldata instead of memory for :- 
	- PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned).tokenData0 (contracts/libraries/PanopticMath.sol#652)
	- PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned).tokenData1 (contracts/libraries/PanopticMath.sol#653)
	- PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned).netExchanged (contracts/libraries/PanopticMath.sol#656)
	- PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned).premia (contracts/libraries/PanopticMath.sol#657)

/// @audit ************** Possible Issue Line(s) **************
	L#652,  L#653,  L#656,  L#657,  

/// @audit ****************** Affected Code *******************
 652:         LeftRightUnsigned tokenData0,
 653:         LeftRightUnsigned tokenData1,
 656:         LeftRightSigned netExchanged,
 657:         LeftRightSigned premia

```

*GitHub* : [651-754](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L651-L754)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLeg(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1278-1301) should use calldata instead of memory for :- 
	- CollateralTracker._getRequiredCollateralSingleLeg(TokenId,uint256,uint128,int24,uint128).tokenId (contracts/CollateralTracker.sol#1279)

/// @audit ************** Possible Issue Line(s) **************
	L#1279,  

/// @audit ****************** Affected Code *******************
1278:     function _getRequiredCollateralSingleLeg(
1279:         TokenId tokenId,
1280:         uint256 index,
1281:         uint128 positionSize,
1282:         int24 atTick,
1283:         uint128 poolUtilization
1284:     ) internal view returns (uint256 required) {
1285:         return
1286:             tokenId.riskPartner(index) == index // does this leg have a risk partner? Affects required collateral
1287:                 ? _getRequiredCollateralSingleLegNoPartner(
1288:                     tokenId,
1289:                     index,
1290:                     positionSize,
1291:                     atTick,
1292:                     poolUtilization
1293:                 )
1294:                 : _getRequiredCollateralSingleLegPartner(
1295:                     tokenId,
1296:                     index,
1297:                     positionSize,
1298:                     atTick,
1299:                     poolUtilization
1300:                 );
1301:     }

```

*GitHub* : [1278-1301](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1278-L1301)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned) (contracts/SemiFungiblePositionManager.sol#756-852) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned).univ3pool (contracts/SemiFungiblePositionManager.sol#757)
	- SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned).itmAmounts (contracts/SemiFungiblePositionManager.sol#758)

/// @audit ************** Possible Issue Line(s) **************
	L#757,  L#758,  

/// @audit ****************** Affected Code *******************
 757:         IUniswapV3Pool univ3pool,
 758:         LeftRightSigned itmAmounts

```

*GitHub* : [756-852](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L756-L852)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.toRightSlot(LeftRightSigned,int128) (contracts/types/LeftRight.sol#78-92) should use calldata instead of memory for :- 
	- LeftRightLibrary.toRightSlot(LeftRightSigned,int128).self (contracts/types/LeftRight.sol#79)

/// @audit ************** Possible Issue Line(s) **************
	L#79,  

/// @audit ****************** Affected Code *******************
  78:     function toRightSlot(
  79:         LeftRightSigned self,
  80:         int128 right
  81:     ) internal pure returns (LeftRightSigned) {
  82:         // bit mask needed in case rightHalfBitPattern < 0 due to 2's complement
  83:         unchecked {
  84:             // prevent the right slot from leaking into the left one in the case of a positive sign change
  85:             // ff + 1 = (1)00, but we want just ff + 1 = 00
  86:             return
  87:                 LeftRightSigned.wrap(
  88:                     (LeftRightSigned.unwrap(self) & LEFT_HALF_BIT_MASK_INT) +
  89:                         (int256(int128(LeftRightSigned.unwrap(self)) + right) & RIGHT_HALF_BIT_MASK)
  90:                 );
  91:         }
  92:     }

```

*GitHub* : [78-92](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L78-L92)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256) (contracts/SemiFungiblePositionManager.sol#593-653) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256).id (contracts/SemiFungiblePositionManager.sol#593)

/// @audit ************** Possible Issue Line(s) **************
	L#593,  

/// @audit ****************** Affected Code *******************
 593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

```

*GitHub* : [593-653](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593-L653)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._payCommissionAndWriteData(TokenId,uint128,LeftRightSigned) (contracts/PanopticPool.sol#706-732) should use calldata instead of memory for :- 
	- PanopticPool._payCommissionAndWriteData(TokenId,uint128,LeftRightSigned).tokenId (contracts/PanopticPool.sol#707)
	- PanopticPool._payCommissionAndWriteData(TokenId,uint128,LeftRightSigned).totalSwapped (contracts/PanopticPool.sol#709)

/// @audit ************** Possible Issue Line(s) **************
	L#707,  L#709,  

/// @audit ****************** Affected Code *******************
 707:         TokenId tokenId,
 709:         LeftRightSigned totalSwapped

```

*GitHub* : [706-732](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L706-L732)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.asTicks(TokenId,uint256) (contracts/types/TokenId.sol#416-425) should use calldata instead of memory for :- 
	- TokenIdLibrary.asTicks(TokenId,uint256).self (contracts/types/TokenId.sol#417)

/// @audit ************** Possible Issue Line(s) **************
	L#417,  

/// @audit ****************** Affected Code *******************
 416:     function asTicks(
 417:         TokenId self,
 418:         uint256 legIndex
 419:     ) internal pure returns (int24 legLowerTick, int24 legUpperTick) {
 420:         (legLowerTick, legUpperTick) = PanopticMath.getTicks(
 421:             self.strike(legIndex),
 422:             self.width(legIndex),
 423:             self.tickSpacing()
 424:         );
 425:     }

```

*GitHub* : [416-425](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L416-L425)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24) (contracts/libraries/FeesCalc.sol#130-208) should use calldata instead of memory for :- 
	- FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24).univ3pool (contracts/libraries/FeesCalc.sol#131)

/// @audit ************** Possible Issue Line(s) **************
	L#131,  

/// @audit ****************** Affected Code *******************
 131:         IUniswapV3Pool univ3pool,

```

*GitHub* : [130-208](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L130-L208)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updatePositionsHash(address,TokenId,bool) (contracts/PanopticPool.sol#1405-1417) should use calldata instead of memory for :- 
	- PanopticPool._updatePositionsHash(address,TokenId,bool).tokenId (contracts/PanopticPool.sol#1405)

/// @audit ************** Possible Issue Line(s) **************
	L#1405,  

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [1405-1417](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1405-L1417)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) should use calldata instead of memory for :- 
	- PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256).univ3pool (contracts/libraries/PanopticMath.sol#126)

/// @audit ************** Possible Issue Line(s) **************
	L#126,  

/// @audit ****************** Affected Code *******************
 126:         IUniswapV3Pool univ3pool,

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned) (contracts/SemiFungiblePositionManager.sol#1321-1407) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).currentLiquidity (contracts/SemiFungiblePositionManager.sol#1322)
	- SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).collectedAmounts (contracts/SemiFungiblePositionManager.sol#1323)

/// @audit ************** Possible Issue Line(s) **************
	L#1322,  L#1323,  

/// @audit ****************** Affected Code *******************
1322:         LeftRightUnsigned currentLiquidity,
1323:         LeftRightUnsigned collectedAmounts

```

*GitHub* : [1321-1407](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1321-L1407)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.updateTickUpper(LiquidityChunk,int24) (contracts/types/LiquidityChunk.sol#151-162) should use calldata instead of memory for :- 
	- LiquidityChunkLibrary.updateTickUpper(LiquidityChunk,int24).self (contracts/types/LiquidityChunk.sol#152)

/// @audit ************** Possible Issue Line(s) **************
	L#152,  

/// @audit ****************** Affected Code *******************
 151:     function updateTickUpper(
 152:         LiquidityChunk self,
 153:         int24 _tickUpper
 154:     ) internal pure returns (LiquidityChunk) {
 155:         unchecked {
 156:             // convert tick upper to uint24 as explicit conversion from int24 to uint256 is not allowed
 157:             return
 158:                 LiquidityChunk.wrap(LiquidityChunk.unwrap(self) & CLEAR_TU_MASK).addTickUpper(
 159:                     _tickUpper
 160:                 );
 161:         }
 162:     }

```

*GitHub* : [151-162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L151-L162)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.leftSlot(LeftRightUnsigned) (contracts/types/LeftRight.sol#101-103) should use calldata instead of memory for :- 
	- LeftRightLibrary.leftSlot(LeftRightUnsigned).self (contracts/types/LeftRight.sol#101)

/// @audit ************** Possible Issue Line(s) **************
	L#101,  

/// @audit ****************** Affected Code *******************
 101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {
 102:         return uint128(LeftRightUnsigned.unwrap(self) >> 128);
 103:     }

```

*GitHub* : [101-103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L101-L103)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.toRightSlot(LeftRightUnsigned,uint128) (contracts/types/LeftRight.sol#59-72) should use calldata instead of memory for :- 
	- LeftRightLibrary.toRightSlot(LeftRightUnsigned,uint128).self (contracts/types/LeftRight.sol#60)

/// @audit ************** Possible Issue Line(s) **************
	L#60,  

/// @audit ****************** Affected Code *******************
  59:     function toRightSlot(
  60:         LeftRightUnsigned self,
  61:         uint128 right
  62:     ) internal pure returns (LeftRightUnsigned) {
  63:         unchecked {
  64:             // prevent the right slot from leaking into the left one in the case of an overflow
  65:             // ff + 1 = (1)00, but we want just ff + 1 = 00
  66:             return
  67:                 LeftRightUnsigned.wrap(
  68:                     (LeftRightUnsigned.unwrap(self) & LEFT_HALF_BIT_MASK) +
  69:                         uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)
  70:                 );
  71:         }
  72:     }

```

*GitHub* : [59-72](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L59-L72)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.isLong(TokenId,uint256) (contracts/types/TokenId.sol#128-132) should use calldata instead of memory for :- 
	- TokenIdLibrary.isLong(TokenId,uint256).self (contracts/types/TokenId.sol#128)

/// @audit ************** Possible Issue Line(s) **************
	L#128,  

/// @audit ****************** Affected Code *******************
 128:     function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 129:         unchecked {
 130:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);
 131:         }
 132:     }

```

*GitHub* : [128-132](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L128-L132)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,uint160) (contracts/libraries/PanopticMath.sol#419-436) should use calldata instead of memory for :- 
	- PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,uint160).tokenData0 (contracts/libraries/PanopticMath.sol#420)
	- PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,uint160).tokenData1 (contracts/libraries/PanopticMath.sol#421)

/// @audit ************** Possible Issue Line(s) **************
	L#420,  L#421,  

/// @audit ****************** Affected Code *******************
 419:     function convertCollateralData(
 420:         LeftRightUnsigned tokenData0,
 421:         LeftRightUnsigned tokenData1,
 422:         uint256 tokenType,
 423:         uint160 sqrtPriceX96
 424:     ) internal pure returns (uint256, uint256) {
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
 436:     }

```

*GitHub* : [419-436](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L419-L436)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#1138-1178) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool).univ3pool (contracts/SemiFungiblePositionManager.sol#1139)
	- SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool).liquidityChunk (contracts/SemiFungiblePositionManager.sol#1141)

/// @audit ************** Possible Issue Line(s) **************
	L#1139,  L#1141,  

/// @audit ****************** Affected Code *******************
1139:         IUniswapV3Pool univ3pool,
1141:         LiquidityChunk liquidityChunk,

```

*GitHub* : [1138-1178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1138-L1178)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24) (contracts/types/TokenId.sol#336-354) should use calldata instead of memory for :- 
	- TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24).self (contracts/types/TokenId.sol#337)

/// @audit ************** Possible Issue Line(s) **************
	L#337,  

/// @audit ****************** Affected Code *******************
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
 347:         tokenId = addOptionRatio(self, _optionRatio, legIndex);
 348:         tokenId = addAsset(tokenId, _asset, legIndex);
 349:         tokenId = addIsLong(tokenId, _isLong, legIndex);
 350:         tokenId = addTokenType(tokenId, _tokenType, legIndex);
 351:         tokenId = addRiskPartner(tokenId, _riskPartner, legIndex);
 352:         tokenId = addStrike(tokenId, _strike, legIndex);
 353:         tokenId = addWidth(tokenId, _width, legIndex);
 354:     }

```

*GitHub* : [336-354](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L336-L354)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.flipToBurnToken(TokenId) (contracts/types/TokenId.sol#366-398) should use calldata instead of memory for :- 
	- TokenIdLibrary.flipToBurnToken(TokenId).self (contracts/types/TokenId.sol#366)

/// @audit ************** Possible Issue Line(s) **************
	L#366,  

/// @audit ****************** Affected Code *******************
 366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

```

*GitHub* : [366-398](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L366-L398)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addPoolId(TokenId,uint64) (contracts/types/TokenId.sol#183-187) should use calldata instead of memory for :- 
	- TokenIdLibrary.addPoolId(TokenId,uint64).self (contracts/types/TokenId.sol#183)

/// @audit ************** Possible Issue Line(s) **************
	L#183,  

/// @audit ****************** Affected Code *******************
 183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {
 184:         unchecked {
 185:             return TokenId.wrap(TokenId.unwrap(self) + _poolId);
 186:         }
 187:     }

```

*GitHub* : [183-187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L183-L187)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256) (contracts/SemiFungiblePositionManager.sol#1255-1313) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).liquidityChunk (contracts/SemiFungiblePositionManager.sol#1256)
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).univ3pool (contracts/SemiFungiblePositionManager.sol#1257)
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).currentLiquidity (contracts/SemiFungiblePositionManager.sol#1258)
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).movedInLeg (contracts/SemiFungiblePositionManager.sol#1260)

/// @audit ************** Possible Issue Line(s) **************
	L#1256,  L#1257,  L#1258,  L#1260,  

/// @audit ****************** Affected Code *******************
1256:         LiquidityChunk liquidityChunk,
1257:         IUniswapV3Pool univ3pool,
1258:         LeftRightUnsigned currentLiquidity,
1260:         LeftRightSigned movedInLeg,

```

*GitHub* : [1255-1313](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255-L1313)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.mintTokenizedPosition(TokenId,uint128,int24,int24) (contracts/SemiFungiblePositionManager.sol#504-527) should use calldata instead of memory for :- 
	- SemiFungiblePositionManager.mintTokenizedPosition(TokenId,uint128,int24,int24).tokenId (contracts/SemiFungiblePositionManager.sol#505)

/// @audit ************** Possible Issue Line(s) **************
	L#505,  

/// @audit ****************** Affected Code *******************
 504:     function mintTokenizedPosition(
 505:         TokenId tokenId,
 506:         uint128 positionSize,
 507:         int24 slippageTickLimitLow,
 508:         int24 slippageTickLimitHigh
 509:     )
 510:         external
 511:         ReentrancyLock(tokenId.poolId())
 512:         returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
 513:     {
 514:         // create the option position via its ID in this erc1155
 515:         _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);
 516: 
 517:         emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);
 518: 
 519:         // validate the incoming option position, then forward to the AMM for minting/burning required liquidity chunks
 520:         (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
 521:             tokenId,
 522:             positionSize,
 523:             slippageTickLimitLow,
 524:             slippageTickLimitHigh,
 525:             MINT
 526:         );
 527:     }

```

*GitHub* : [504-527](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L504-L527)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.tickSpacing(TokenId) (contracts/types/TokenId.sol#96-100) should use calldata instead of memory for :- 
	- TokenIdLibrary.tickSpacing(TokenId).self (contracts/types/TokenId.sol#96)

/// @audit ************** Possible Issue Line(s) **************
	L#96,  

/// @audit ****************** Affected Code *******************
  96:     function tickSpacing(TokenId self) internal pure returns (int24) {
  97:         unchecked {
  98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));
  99:         }
 100:     }

```

*GitHub* : [96-100](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L96-L100)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidityChunk(TokenId,uint256,uint128) (contracts/libraries/PanopticMath.sol#289-330) should use calldata instead of memory for :- 
	- PanopticMath.getLiquidityChunk(TokenId,uint256,uint128).tokenId (contracts/libraries/PanopticMath.sol#290)

/// @audit ************** Possible Issue Line(s) **************
	L#290,  

/// @audit ****************** Affected Code *******************
 290:         TokenId tokenId,

```

*GitHub* : [289-330](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L289-L330)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeExercisedAmounts(TokenId,uint128) (contracts/libraries/PanopticMath.sol#390-410) should use calldata instead of memory for :- 
	- PanopticMath.computeExercisedAmounts(TokenId,uint128).tokenId (contracts/libraries/PanopticMath.sol#391)

/// @audit ************** Possible Issue Line(s) **************
	L#391,  

/// @audit ****************** Affected Code *******************
 390:     function computeExercisedAmounts(
 391:         TokenId tokenId,
 392:         uint128 positionSize
 393:     ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {
 394:         uint256 numLegs = tokenId.countLegs();
 395:         for (uint256 leg = 0; leg < numLegs; ) {
 396:             // Compute the amount of funds that have been removed from the Panoptic Pool
 397:             (LeftRightSigned longs, LeftRightSigned shorts) = _calculateIOAmounts(
 398:                 tokenId,
 399:                 positionSize,
 400:                 leg
 401:             );
 402: 
 403:             longAmounts = longAmounts.add(longs);
 404:             shortAmounts = shortAmounts.add(shorts);
 405: 
 406:             unchecked {
 407:                 ++leg;
 408:             }
 409:         }
 410:     }

```

*GitHub* : [390-410](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L390-L410)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addIsLong(TokenId,uint256,uint256) (contracts/types/TokenId.sol#240-248) should use calldata instead of memory for :- 
	- TokenIdLibrary.addIsLong(TokenId,uint256,uint256).self (contracts/types/TokenId.sol#241)

/// @audit ************** Possible Issue Line(s) **************
	L#241,  

/// @audit ****************** Affected Code *******************
 240:     function addIsLong(
 241:         TokenId self,
 242:         uint256 _isLong,
 243:         uint256 legIndex
 244:     ) internal pure returns (TokenId) {
 245:         unchecked {
 246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));
 247:         }
 248:     }

```

*GitHub* : [240-248](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L240-L248)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.optionRatio(TokenId,uint256) (contracts/types/TokenId.sol#118-122) should use calldata instead of memory for :- 
	- TokenIdLibrary.optionRatio(TokenId,uint256).self (contracts/types/TokenId.sol#118)

/// @audit ************** Possible Issue Line(s) **************
	L#118,  

/// @audit ****************** Affected Code *******************
 118:     function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {
 119:         unchecked {
 120:             return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);
 121:         }
 122:     }

```

*GitHub* : [118-122](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L118-L122)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned) (contracts/CollateralTracker.sol#650-734) should use calldata instead of memory for :- 
	- CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned).positionId (contracts/CollateralTracker.sol#653)
	- CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned).longAmounts (contracts/CollateralTracker.sol#655)

/// @audit ************** Possible Issue Line(s) **************
	L#653,  L#655,  

/// @audit ****************** Affected Code *******************
 653:         TokenId positionId,
 655:         LeftRightSigned longAmounts

```

*GitHub* : [650-734](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L650-L734)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addStrike(TokenId,int24,uint256) (contracts/types/TokenId.sol#291-303) should use calldata instead of memory for :- 
	- TokenIdLibrary.addStrike(TokenId,int24,uint256).self (contracts/types/TokenId.sol#292)

/// @audit ************** Possible Issue Line(s) **************
	L#292,  

/// @audit ****************** Affected Code *******************
 291:     function addStrike(
 292:         TokenId self,
 293:         int24 _strike,
 294:         uint256 legIndex
 295:     ) internal pure returns (TokenId) {
 296:         unchecked {
 297:             return
 298:                 TokenId.wrap(
 299:                     TokenId.unwrap(self) +
 300:                         uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))
 301:                 );
 302:         }
 303:     }

```

*GitHub* : [291-303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L291-L303)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._checkLiquiditySpread(TokenId,uint256,int24,int24,uint64) (contracts/PanopticPool.sol#1465-1494) should use calldata instead of memory for :- 
	- PanopticPool._checkLiquiditySpread(TokenId,uint256,int24,int24,uint64).tokenId (contracts/PanopticPool.sol#1466)

/// @audit ************** Possible Issue Line(s) **************
	L#1466,  

/// @audit ****************** Affected Code *******************
1466:         TokenId tokenId,

```

*GitHub* : [1465-1494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1465-L1494)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getTotalRequiredCollateral(int24,uint256[2][]) (contracts/CollateralTracker.sol#1200-1236) should use calldata instead of memory for :- 
	- CollateralTracker._getTotalRequiredCollateral(int24,uint256[2][]).positionBalanceArray (contracts/CollateralTracker.sol#1202)

/// @audit ************** Possible Issue Line(s) **************
	L#1202,  

/// @audit ****************** Affected Code *******************
1202:         uint256[2][] memory positionBalanceArray

```

*GitHub* : [1200-1236](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1200-L1236)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.tickLower(LiquidityChunk) (contracts/types/LiquidityChunk.sol#171-175) should use calldata instead of memory for :- 
	- LiquidityChunkLibrary.tickLower(LiquidityChunk).self (contracts/types/LiquidityChunk.sol#171)

/// @audit ************** Possible Issue Line(s) **************
	L#171,  

/// @audit ****************** Affected Code *******************
 171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {
 172:         unchecked {
 173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));
 174:         }
 175:     }

```

*GitHub* : [171-175](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L171-L175)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addTickSpacing(TokenId,int24) (contracts/types/TokenId.sol#193-197) should use calldata instead of memory for :- 
	- TokenIdLibrary.addTickSpacing(TokenId,int24).self (contracts/types/TokenId.sol#193)

/// @audit ************** Possible Issue Line(s) **************
	L#193,  

/// @audit ****************** Affected Code *******************
 193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {
 194:         unchecked {
 195:             return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));
 196:         }
 197:     }

```

*GitHub* : [193-197](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L193-L197)

### [G-12]<a name="g-12"></a> Consider Merge Sequential Loops

Multiple loops appear sequentially in the same function. This may indicate an opportunity for loop fusion, a code optimization technique that merges multiple loops into a single one to save gas.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) may merge sequential loop(s) :- 
	- i < positionIdList.length (contracts/libraries/PanopticMath.sol#781)
	- i_scope_0 < positionIdList.length (contracts/libraries/PanopticMath.sol#860)

/// @audit ************** Possible Issue Line(s) **************
	L#781,  L#860,  

/// @audit ****************** Affected Code *******************
 781:             for (uint256 i = 0; i < positionIdList.length; ++i) {
 860:             for (uint256 i = 0; i < positionIdList.length; i++) {

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768-L908)

### [G-13]<a name="g-13"></a> Avoid updating storage when the value hasn't changed

If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (**2900 gas**), potentially at the expense of a Gcoldsload (**2100 gas**) or a Gwarmaccess (**100 gas**)

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) should only update if value changes.

/// @audit ****************** Affected Code *******************
1587:     function settleLongPremium(
1588:         TokenId[] calldata positionIdList,
1589:         address owner,
1590:         uint256 legIndex
1591:     ) external {
1592:         _validatePositionList(owner, positionIdList, 0);
1593: 
1594:         TokenId tokenId = positionIdList[positionIdList.length - 1];
1595: 
1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587-L1659)

### [G-14]<a name="g-14"></a> smaller uint/int types cause gas overhead

When using a smaller int/uint type it first needs to be converted to it's 258 bit counterpart to be operated, this increases the gass cost and thus should be avoided. However it does make sense to use smaller int/uint values within structs provided you pack the struct properly.

*There are 50 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278) has uint/ int smaller than 256-bit:
	- PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]).currentTick (contracts/PanopticPool.sol#1202)
	- PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]).positionBalance (contracts/PanopticPool.sol#1193)
	- PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]).twapTick (contracts/PanopticPool.sol#1200)

/// @audit ************** Possible Issue Line(s) **************
	L#1202,  L#1193,  L#1200,  

/// @audit ****************** Affected Code *******************
1193:         uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();
1200:         int24 twapTick = getUniV3TWAP();
1202:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24) (contracts/PanopticFactory.sol#335-411) has uint/ int smaller than 256-bit:
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).tickSpacing (contracts/PanopticFactory.sol#391)
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).currentSqrtPriceX96 (contracts/PanopticFactory.sol#341)
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).liquidity1 (contracts/PanopticFactory.sol#368-374)
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).liquidity0 (contracts/PanopticFactory.sol#365-367)
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).fullRangeLiquidity (contracts/PanopticFactory.sol#348)
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).tickLower (contracts/PanopticFactory.sol#388)
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).tickUpper (contracts/PanopticFactory.sol#389)

/// @audit ************** Possible Issue Line(s) **************
	L#391,  L#341,  L#368-374,  L#365-367,  L#348,  L#388,  L#389,  

/// @audit ****************** Affected Code *******************
 341:         (uint160 currentSqrtPriceX96, , , , , , ) = v3Pool.slot0();
 348:         uint128 fullRangeLiquidity;
 365:                 uint128 liquidity0 = uint128(
 366:                     Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)
 367:                 );
 368:                 uint128 liquidity1 = uint128(
 369:                     Math.mulDivRoundingUp(
 370:                         FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,
 371:                         Constants.FP96,
 372:                         currentSqrtPriceX96
 373:                     )
 374:                 );
 388:         int24 tickLower;
 389:         int24 tickUpper;
 391:             int24 tickSpacing = v3Pool.tickSpacing();

```

*GitHub* : [335-411](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L335-L411)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getAmount1ForLiquidity(LiquidityChunk) (contracts/libraries/Math.sol#207-214) has uint/ int smaller than 256-bit:
	- Math.getAmount1ForLiquidity(LiquidityChunk).highPriceX96 (contracts/libraries/Math.sol#209)
	- Math.getAmount1ForLiquidity(LiquidityChunk).lowPriceX96 (contracts/libraries/Math.sol#208)

/// @audit ************** Possible Issue Line(s) **************
	L#209,  L#208,  

/// @audit ****************** Affected Code *******************
 207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
 208:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
 209:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());
 210: 
 211:         unchecked {
 212:             return mulDiv96(liquidityChunk.liquidity(), highPriceX96 - lowPriceX96);
 213:         }
 214:     }

```

*GitHub* : [207-214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L207-L214)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.updatePositionsHash(uint256,TokenId,bool) (contracts/libraries/PanopticMath.sol#92-110) has uint/ int smaller than 256-bit:
	- PanopticMath.updatePositionsHash(uint256,TokenId,bool).updatedHash (contracts/libraries/PanopticMath.sol#102-103)

/// @audit ************** Possible Issue Line(s) **************
	L#102-103,  

/// @audit ****************** Affected Code *******************
  92:     function updatePositionsHash(
  93:         uint256 existingHash,
  94:         TokenId tokenId,
  95:         bool addFlag
  96:     ) internal pure returns (uint256) {
  97:         // add the XOR`ed hash of the single option position `tokenId` to the `existingHash`
  98:         // @dev 0 ^ x = x
  99: 
 100:         unchecked {
 101:             // update hash by taking the XOR of the new tokenId
 102:             uint248 updatedHash = uint248(existingHash) ^
 103:                 (uint248(uint256(keccak256(abi.encode(tokenId)))));
 104:             // increment the top 8 bit if addflag=true, decrement otherwise
 105:             return
 106:                 addFlag
 107:                     ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)
 108:                     : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);
 109:         }
 110:     }

```

*GitHub* : [92-110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L92-L110)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) has uint/ int smaller than 256-bit:
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).newOrderMap (contracts/libraries/PanopticMath.sol#202)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).entry (contracts/libraries/PanopticMath.sol#206)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).tickCumulative_last (contracts/libraries/PanopticMath.sol#192)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).shift (contracts/libraries/PanopticMath.sol#203)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).tickCumulative_old (contracts/libraries/PanopticMath.sol#186)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).i (contracts/libraries/PanopticMath.sol#207)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).orderMap (contracts/libraries/PanopticMath.sol#200)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).rank (contracts/libraries/PanopticMath.sol#205)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).lastObservedTick (contracts/libraries/PanopticMath.sol#184)

/// @audit ************** Possible Issue Line(s) **************
	L#202,  L#206,  L#192,  L#203,  L#186,  L#207,  L#200,  L#205,  L#184,  

/// @audit ****************** Affected Code *******************
 184:                 int24 lastObservedTick;
 186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(
 192:                     (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool
 200:                 uint24 orderMap = uint24(medianData >> 192);
 202:                 uint24 newOrderMap;
 203:                 uint24 shift = 1;
 205:                 uint24 rank;
 206:                 int24 entry;
 207:                 for (uint8 i; i < 8; ++i) {

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getTotalLiquidity(TokenId,uint256) (contracts/PanopticPool.sol#1802-1822) has uint/ int smaller than 256-bit:
	- PanopticPool._getTotalLiquidity(TokenId,uint256).tickLower (contracts/PanopticPool.sol#1809)
	- PanopticPool._getTotalLiquidity(TokenId,uint256).tickUpper (contracts/PanopticPool.sol#1809)

/// @audit ************** Possible Issue Line(s) **************
	L#1809,  

/// @audit ****************** Affected Code *******************
1802:     function _getTotalLiquidity(
1803:         TokenId tokenId,
1804:         uint256 leg
1805:     ) internal view returns (uint256 totalLiquidity) {
1806:         unchecked {
1807:             // totalLiquidity (total sold) = removedLiquidity + netLiquidity
1808: 
1809:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
1810:             uint256 tokenType = tokenId.tokenType(leg);
1811:             LeftRightUnsigned accountLiquidities = SFPM.getAccountLiquidity(
1812:                 address(s_univ3pool),
1813:                 address(this),
1814:                 tokenType,
1815:                 tickLower,
1816:                 tickUpper
1817:             );
1818: 
1819:             // removed + net
1820:             totalLiquidity = accountLiquidities.rightSlot() + accountLiquidities.leftSlot();
1821:         }
1822:     }

```

*GitHub* : [1802-1822](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1802-L1822)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.assertPriceWithinBounds(uint160,uint160) (contracts/PanopticPool.sol#338-344) has uint/ int smaller than 256-bit:
	- PanopticPool.assertPriceWithinBounds(uint160,uint160).currentSqrtPriceX96 (contracts/PanopticPool.sol#339)

/// @audit ************** Possible Issue Line(s) **************
	L#339,  

/// @audit ****************** Affected Code *******************
 338:     function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {
 339:         (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();
 340: 
 341:         if (currentSqrtPriceX96 <= sqrtLowerBound || currentSqrtPriceX96 >= sqrtUpperBound) {
 342:             revert Errors.PriceBoundFail();
 343:         }
 344:     }

```

*GitHub* : [338-344](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L338-L344)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned) (contracts/SemiFungiblePositionManager.sol#1321-1407) has uint/ int smaller than 256-bit:
	- SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium0X64_gross (contracts/SemiFungiblePositionManager.sol#1384)
	- SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium1X64_gross (contracts/SemiFungiblePositionManager.sol#1385)
	- SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium0X64_owed (contracts/SemiFungiblePositionManager.sol#1363)
	- SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium1X64_owed (contracts/SemiFungiblePositionManager.sol#1364)
	- SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).collected0 (contracts/SemiFungiblePositionManager.sol#1346)
	- SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).collected1 (contracts/SemiFungiblePositionManager.sol#1347)

/// @audit ************** Possible Issue Line(s) **************
	L#1384,  L#1385,  L#1363,  L#1364,  L#1346,  L#1347,  

/// @audit ****************** Affected Code *******************
1346:                 uint128 collected0 = collectedAmounts.rightSlot();
1347:                 uint128 collected1 = collectedAmounts.leftSlot();
1363:                 uint128 premium0X64_owed;
1364:                 uint128 premium1X64_owed;
1384:                 uint128 premium0X64_gross;
1385:                 uint128 premium1X64_gross;

```

*GitHub* : [1321-1407](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1321-L1407)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24) (contracts/PanopticPool.sol#614-667) has uint/ int smaller than 256-bit:
	- PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24).poolUtilizations (contracts/PanopticPool.sol#642-647)

/// @audit ************** Possible Issue Line(s) **************
	L#642-647,  

/// @audit ****************** Affected Code *******************
 642:         uint128 poolUtilizations = _mintInSFPMAndUpdateCollateral(
 643:             tokenId,
 644:             positionSize,
 645:             tickLimitLow,
 646:             tickLimitHigh
 647:         );

```

*GitHub* : [614-667](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L614-L667)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightSigned,LeftRightSigned) (contracts/types/LeftRight.sol#214-226) has uint/ int smaller than 256-bit:
	- LeftRightLibrary.add(LeftRightSigned,LeftRightSigned).left128 (contracts/types/LeftRight.sol#217)
	- LeftRightLibrary.add(LeftRightSigned,LeftRightSigned).right128 (contracts/types/LeftRight.sol#220)

/// @audit ************** Possible Issue Line(s) **************
	L#217,  L#220,  

/// @audit ****************** Affected Code *******************
 214:     function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 215:         unchecked {
 216:             int256 left256 = int256(x.leftSlot()) + y.leftSlot();
 217:             int128 left128 = int128(left256);
 218: 
 219:             int256 right256 = int256(x.rightSlot()) + y.rightSlot();
 220:             int128 right128 = int128(right256);
 221: 
 222:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
 223: 
 224:             return z.toRightSlot(right128).toLeftSlot(left128);
 225:         }
 226:     }

```

*GitHub* : [214-226](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L214-L226)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned) (contracts/CollateralTracker.sol#650-734) has uint/ int smaller than 256-bit:
	- CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned).range (contracts/CollateralTracker.sol#667-674)

/// @audit ************** Possible Issue Line(s) **************
	L#667-674,  

/// @audit ****************** Affected Code *******************
 667:                     int24 range = int24(
 668:                         int256(
 669:                             Math.unsafeDivRoundingUp(
 670:                                 uint24(positionId.width(leg) * positionId.tickSpacing()),
 671:                                 2
 672:                             )
 673:                         )
 674:                     );

```

*GitHub* : [650-734](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L650-L734)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker) (contracts/libraries/PanopticMath.sol#917-966) has uint/ int smaller than 256-bit:
	- PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker).sqrtPriceX96 (contracts/libraries/PanopticMath.sol#924)

/// @audit ************** Possible Issue Line(s) **************
	L#924,  

/// @audit ****************** Affected Code *******************
 924:         uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);

```

*GitHub* : [917-966](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L917-L966)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._mintInSFPMAndUpdateCollateral(TokenId,uint128,int24,int24) (contracts/PanopticPool.sol#677-696) has uint/ int smaller than 256-bit:
	- PanopticPool._mintInSFPMAndUpdateCollateral(TokenId,uint128,int24,int24).poolUtilizations (contracts/PanopticPool.sol#693)

/// @audit ************** Possible Issue Line(s) **************
	L#693,  

/// @audit ****************** Affected Code *******************
 677:     function _mintInSFPMAndUpdateCollateral(
 678:         TokenId tokenId,
 679:         uint128 positionSize,
 680:         int24 tickLimitLow,
 681:         int24 tickLimitHigh
 682:     ) internal returns (uint128) {
 683:         // Mint position by using the SFPM. totalSwapped will reflect tokens swapped because of minting ITM.
 684:         // Switch order of tickLimits to create "swapAtMint" flag
 685:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 686:             .mintTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 687: 
 688:         // update premium settlement info
 689:         _updateSettlementPostMint(tokenId, collectedByLeg, positionSize);
 690: 
 691:         // pay commission based on total moved amount (long + short)
 692:         // write data about inAMM in collateralBase
 693:         uint128 poolUtilizations = _payCommissionAndWriteData(tokenId, positionSize, totalSwapped);
 694: 
 695:         return poolUtilizations;
 696:     }

```

*GitHub* : [677-696](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L677-L696)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidityChunk(TokenId,uint256,uint128) (contracts/libraries/PanopticMath.sol#289-330) has uint/ int smaller than 256-bit:
	- PanopticMath.getLiquidityChunk(TokenId,uint256,uint128).tickUpper (contracts/libraries/PanopticMath.sol#295)
	- PanopticMath.getLiquidityChunk(TokenId,uint256,uint128).tickLower (contracts/libraries/PanopticMath.sol#295)

/// @audit ************** Possible Issue Line(s) **************
	L#295,  

/// @audit ****************** Affected Code *******************
 295:         (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);

```

*GitHub* : [289-330](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L289-L330)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._validateAndForwardToAMM(TokenId,uint128,int24,int24,bool) (contracts/SemiFungiblePositionManager.sol#680-729) has uint/ int smaller than 256-bit:
	- SemiFungiblePositionManager._validateAndForwardToAMM(TokenId,uint128,int24,int24,bool).currentTick (contracts/SemiFungiblePositionManager.sol#725)

/// @audit ************** Possible Issue Line(s) **************
	L#725,  

/// @audit ****************** Affected Code *******************
 725:         (, int24 currentTick, , , , , ) = univ3pool.slot0();

```

*GitHub* : [680-729](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L680-L729)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._burnOptions(bool,TokenId,address,int24,int24) (contracts/PanopticPool.sol#826-854) has uint/ int smaller than 256-bit:
	- PanopticPool._burnOptions(bool,TokenId,address,int24,int24).positionSize (contracts/PanopticPool.sol#836)

/// @audit ************** Possible Issue Line(s) **************
	L#836,  

/// @audit ****************** Affected Code *******************
 836:         uint128 positionSize = s_positionBalance[owner][tokenId].rightSlot();

```

*GitHub* : [826-854](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L826-L854)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._burnAndHandleExercise(bool,int24,int24,TokenId,uint128,address) (contracts/PanopticPool.sol#955-1005) has uint/ int smaller than 256-bit:
	- PanopticPool._burnAndHandleExercise(bool,int24,int24,TokenId,uint128,address).paid1 (contracts/PanopticPool.sol#996-1002)
	- PanopticPool._burnAndHandleExercise(bool,int24,int24,TokenId,uint128,address).paid0 (contracts/PanopticPool.sol#985-991)

/// @audit ************** Possible Issue Line(s) **************
	L#996-1002,  L#985-991,  

/// @audit ****************** Affected Code *******************
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );

```

*GitHub* : [955-1005](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L955-L1005)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128) (contracts/CollateralTracker.sol#1510-1589) has uint/ int smaller than 256-bit:
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128).movedRight (contracts/CollateralTracker.sol#1528)
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128).movedPartnerRight (contracts/CollateralTracker.sol#1532)
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128).movedPartnerLeft (contracts/CollateralTracker.sol#1533)
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128).contracts (contracts/CollateralTracker.sol#1558)
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128).movedLeft (contracts/CollateralTracker.sol#1529)

/// @audit ************** Possible Issue Line(s) **************
	L#1528,  L#1532,  L#1533,  L#1558,  L#1529,  

/// @audit ****************** Affected Code *******************
1528:         uint128 movedRight = amountsMoved.rightSlot();
1529:         uint128 movedLeft = amountsMoved.leftSlot();
1532:         uint128 movedPartnerRight = amountsMovedPartner.rightSlot();
1533:         uint128 movedPartnerLeft = amountsMovedPartner.leftSlot();
1558:                 uint128 contracts;

```

*GitHub* : [1510-1589](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1510-L1589)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.pokeMedian() (contracts/PanopticPool.sol#522-534) has uint/ int smaller than 256-bit:
	- PanopticPool.pokeMedian().observationCardinality (contracts/PanopticPool.sol#523)
	- PanopticPool.pokeMedian().observationIndex (contracts/PanopticPool.sol#523)

/// @audit ************** Possible Issue Line(s) **************
	L#523,  

/// @audit ****************** Affected Code *******************
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

```

*GitHub* : [522-534](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L522-L534)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#958-1104) has uint/ int smaller than 256-bit:
	- SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).updatedLiquidity (contracts/SemiFungiblePositionManager.sol#986)
	- SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).startingLiquidity (contracts/SemiFungiblePositionManager.sol#995)
	- SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).removedLiquidity (contracts/SemiFungiblePositionManager.sol#996)
	- SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).chunkLiquidity (contracts/SemiFungiblePositionManager.sol#997)

/// @audit ************** Possible Issue Line(s) **************
	L#986,  L#995,  L#996,  L#997,  

/// @audit ****************** Affected Code *******************
 986:         uint128 updatedLiquidity;
 995:             uint128 startingLiquidity = currentLiquidity.rightSlot();
 996:             uint128 removedLiquidity = currentLiquidity.leftSlot();
 997:             uint128 chunkLiquidity = liquidityChunk.liquidity();

```

*GitHub* : [958-1104](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L958-L1104)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1311-1422) has uint/ int smaller than 256-bit:
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).amountMoved (contracts/CollateralTracker.sol#1325)
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).utilization (contracts/CollateralTracker.sol#1328-1330)
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).tickUpper (contracts/CollateralTracker.sol#1342)
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).tickLower (contracts/CollateralTracker.sol#1342)
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).scaleFactor (contracts/CollateralTracker.sol#1408-1410)
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).ratio (contracts/CollateralTracker.sol#1362-1368)
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).strike (contracts/CollateralTracker.sol#1352)

/// @audit ************** Possible Issue Line(s) **************
	L#1325,  L#1328-1330,  L#1342,  L#1408-1410,  L#1362-1368,  L#1352,  

/// @audit ****************** Affected Code *******************
1325:         uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();
1328:         int64 utilization = tokenType == 0
1329:             ? int64(uint64(poolUtilization))
1330:             : int64(uint64(poolUtilization >> 64));
1342:                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(index);
1352:                     int24 strike = tokenId.strike(index);
1362:                     uint160 ratio = tokenType == 1 // tokenType
1363:                         ? Math.getSqrtRatioAtTick(
1364:                             Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)
1365:                         ) // puts ->  price/strike
1366:                         : Math.getSqrtRatioAtTick(
1367:                             Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)
1368:                         ); // calls -> strike/price
1408:                         uint160 scaleFactor = Math.getSqrtRatioAtTick(
1409:                             (tickUpper - strike) + (strike - tickLower)
1410:                         );

```

*GitHub* : [1311-1422](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1311-L1422)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1600-1649) has uint/ int smaller than 256-bit:
	- CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128).poolUtilization1 (contracts/CollateralTracker.sol#1632)
	- CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128).poolUtilization0 (contracts/CollateralTracker.sol#1631)

/// @audit ************** Possible Issue Line(s) **************
	L#1632,  L#1631,  

/// @audit ****************** Affected Code *******************
1631:             uint64 poolUtilization0 = uint64(poolUtilization);
1632:             uint64 poolUtilization1 = uint64(poolUtilization >> 64);

```

*GitHub* : [1600-1649](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1600-L1649)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) has uint/ int smaller than 256-bit:
	- FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]).positionSize (contracts/libraries/FeesCalc.sol#53)

/// @audit ************** Possible Issue Line(s) **************
	L#53,  

/// @audit ****************** Affected Code *******************
  53:             uint128 positionSize = userBalance[tokenId].rightSlot();

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned) (contracts/SemiFungiblePositionManager.sol#756-852) has uint/ int smaller than 256-bit:
	- SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned).itm0 (contracts/SemiFungiblePositionManager.sol#769)
	- SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned).itm1 (contracts/SemiFungiblePositionManager.sol#770)
	- SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned).sqrtPriceX96 (contracts/SemiFungiblePositionManager.sol#788)

/// @audit ************** Possible Issue Line(s) **************
	L#769,  L#770,  L#788,  

/// @audit ****************** Affected Code *******************
 769:             int128 itm0 = itmAmounts.rightSlot();
 770:             int128 itm1 = itmAmounts.leftSlot();
 788:                 (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

```

*GitHub* : [756-852](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L756-L852)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getTotalRequiredCollateral(int24,uint256[2][]) (contracts/CollateralTracker.sol#1200-1236) has uint/ int smaller than 256-bit:
	- CollateralTracker._getTotalRequiredCollateral(int24,uint256[2][]).positionSize (contracts/CollateralTracker.sol#1213)
	- CollateralTracker._getTotalRequiredCollateral(int24,uint256[2][]).poolUtilization (contracts/CollateralTracker.sol#1216)

/// @audit ************** Possible Issue Line(s) **************
	L#1213,  L#1216,  

/// @audit ****************** Affected Code *******************
1213:             uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();
1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

```

*GitHub* : [1200-1236](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1200-L1236)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned) (contracts/types/LeftRight.sol#279-301) has uint/ int smaller than 256-bit:
	- LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned).z_xL (contracts/types/LeftRight.sol#286)
	- LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned).z_xR (contracts/types/LeftRight.sol#285)
	- LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned).z_yR (contracts/types/LeftRight.sol#287)
	- LeftRightLibrary.addCapped(LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned).z_yL (contracts/types/LeftRight.sol#288)

/// @audit ************** Possible Issue Line(s) **************
	L#286,  L#285,  L#287,  L#288,  

/// @audit ****************** Affected Code *******************
 279:     function addCapped(
 280:         LeftRightUnsigned x,
 281:         LeftRightUnsigned dx,
 282:         LeftRightUnsigned y,
 283:         LeftRightUnsigned dy
 284:     ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {
 285:         uint128 z_xR = (uint256(x.rightSlot()) + dx.rightSlot()).toUint128Capped();
 286:         uint128 z_xL = (uint256(x.leftSlot()) + dx.leftSlot()).toUint128Capped();
 287:         uint128 z_yR = (uint256(y.rightSlot()) + dy.rightSlot()).toUint128Capped();
 288:         uint128 z_yL = (uint256(y.leftSlot()) + dy.leftSlot()).toUint128Capped();
 289: 
 290:         bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);
 291:         bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);
 292: 
 293:         return (
 294:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(
 295:                 l_Enabled ? z_xL : x.leftSlot()
 296:             ),
 297:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(
 298:                 l_Enabled ? z_yL : y.leftSlot()
 299:             )
 300:         );
 301:     }

```

*GitHub* : [279-301](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L279-L301)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._addUserOption(TokenId,uint64) (contracts/PanopticPool.sol#739-782) has uint/ int smaller than 256-bit:
	- PanopticPool._addUserOption(TokenId,uint64).premiumAccumulator0 (contracts/PanopticPool.sol#751)
	- PanopticPool._addUserOption(TokenId,uint64).tickUpper (contracts/PanopticPool.sol#748)
	- PanopticPool._addUserOption(TokenId,uint64).tickLower (contracts/PanopticPool.sol#748)
	- PanopticPool._addUserOption(TokenId,uint64).premiumAccumulator1 (contracts/PanopticPool.sol#751)

/// @audit ************** Possible Issue Line(s) **************
	L#751,  L#748,  

/// @audit ****************** Affected Code *******************
 748:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
 751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

```

*GitHub* : [739-782](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L739-L782)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.subRect(LeftRightSigned,LeftRightSigned) (contracts/types/LeftRight.sol#251-269) has uint/ int smaller than 256-bit:
	- LeftRightLibrary.subRect(LeftRightSigned,LeftRightSigned).left128 (contracts/types/LeftRight.sol#257)
	- LeftRightLibrary.subRect(LeftRightSigned,LeftRightSigned).right128 (contracts/types/LeftRight.sol#260)

/// @audit ************** Possible Issue Line(s) **************
	L#257,  L#260,  

/// @audit ****************** Affected Code *******************
 251:     function subRect(
 252:         LeftRightSigned x,
 253:         LeftRightSigned y
 254:     ) internal pure returns (LeftRightSigned z) {
 255:         unchecked {
 256:             int256 left256 = int256(x.leftSlot()) - y.leftSlot();
 257:             int128 left128 = int128(left256);
 258: 
 259:             int256 right256 = int256(x.rightSlot()) - y.rightSlot();
 260:             int128 right128 = int128(right256);
 261: 
 262:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
 263: 
 264:             return
 265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(
 266:                     int128(Math.max(left128, 0))
 267:                 );
 268:         }
 269:     }

```

*GitHub* : [251-269](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L251-L269)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._checkLiquiditySpread(TokenId,uint256,int24,int24,uint64) (contracts/PanopticPool.sol#1465-1494) has uint/ int smaller than 256-bit:
	- PanopticPool._checkLiquiditySpread(TokenId,uint256,int24,int24,uint64).netLiquidity (contracts/PanopticPool.sol#1480)
	- PanopticPool._checkLiquiditySpread(TokenId,uint256,int24,int24,uint64).totalLiquidity (contracts/PanopticPool.sol#1481)

/// @audit ************** Possible Issue Line(s) **************
	L#1480,  L#1481,  

/// @audit ****************** Affected Code *******************
1480:         uint128 netLiquidity = accountLiquidities.rightSlot();
1481:         uint128 totalLiquidity = accountLiquidities.leftSlot();

```

*GitHub* : [1465-1494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1465-L1494)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256) (contracts/SemiFungiblePositionManager.sol#1449-1523) has uint/ int smaller than 256-bit:
	- SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256)._tickLower (contracts/SemiFungiblePositionManager.sol#1473)
	- SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256)._tickUpper (contracts/SemiFungiblePositionManager.sol#1474)
	- SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256).netLiquidity (contracts/SemiFungiblePositionManager.sol#1468)

/// @audit ************** Possible Issue Line(s) **************
	L#1473,  L#1474,  L#1468,  

/// @audit ****************** Affected Code *******************
1468:             uint128 netLiquidity = accountLiquidities.rightSlot();
1473:                     int24 _tickLower = tickLower;
1474:                     int24 _tickUpper = tickUpper;

```

*GitHub* : [1449-1523](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1449-L1523)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getLiquidityForAmount0(int24,int24,uint256) (contracts/libraries/Math.sol#241-263) has uint/ int smaller than 256-bit:
	- Math.getLiquidityForAmount0(int24,int24,uint256).highPriceX96 (contracts/libraries/Math.sol#247)
	- Math.getLiquidityForAmount0(int24,int24,uint256).lowPriceX96 (contracts/libraries/Math.sol#246)

/// @audit ************** Possible Issue Line(s) **************
	L#247,  L#246,  

/// @audit ****************** Affected Code *******************
 241:     function getLiquidityForAmount0(
 242:         int24 tickLower,
 243:         int24 tickUpper,
 244:         uint256 amount0
 245:     ) internal pure returns (LiquidityChunk) {
 246:         uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);
 247:         uint160 highPriceX96 = getSqrtRatioAtTick(tickUpper);
 248: 
 249:         unchecked {
 250:             return
 251:                 LiquidityChunkLibrary.createChunk(
 252:                     tickLower,
 253:                     tickUpper,
 254:                     toUint128(
 255:                         mulDiv(
 256:                             amount0,
 257:                             mulDiv96(highPriceX96, lowPriceX96),
 258:                             highPriceX96 - lowPriceX96
 259:                         )
 260:                     )
 261:                 );
 262:         }
 263:     }

```

*GitHub* : [241-263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L241-L263)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker) (contracts/PanopticPool.sol#291-327) has uint/ int smaller than 256-bit:
	- PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker).currentTick (contracts/PanopticPool.sol#304)

/// @audit ************** Possible Issue Line(s) **************
	L#304,  

/// @audit ****************** Affected Code *******************
 304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

```

*GitHub* : [291-327](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L327)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getAmountsMoved(TokenId,uint128,uint256) (contracts/libraries/PanopticMath.sol#574-599) has uint/ int smaller than 256-bit:
	- PanopticMath.getAmountsMoved(TokenId,uint128,uint256).tickLower (contracts/libraries/PanopticMath.sol#580)
	- PanopticMath.getAmountsMoved(TokenId,uint128,uint256).amount0 (contracts/libraries/PanopticMath.sol#582)
	- PanopticMath.getAmountsMoved(TokenId,uint128,uint256).amount1 (contracts/libraries/PanopticMath.sol#583)
	- PanopticMath.getAmountsMoved(TokenId,uint128,uint256).tickUpper (contracts/libraries/PanopticMath.sol#580)

/// @audit ************** Possible Issue Line(s) **************
	L#580,  L#582,  L#583,  

/// @audit ****************** Affected Code *******************
 580:         (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);
 582:         uint128 amount0;
 583:         uint128 amount1;

```

*GitHub* : [574-599](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L574-L599)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned) (contracts/types/LeftRight.sol#194-208) has uint/ int smaller than 256-bit:
	- LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned).right128 (contracts/types/LeftRight.sol#202)
	- LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned).left128 (contracts/types/LeftRight.sol#197)

/// @audit ************** Possible Issue Line(s) **************
	L#202,  L#197,  

/// @audit ****************** Affected Code *******************
 194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 195:         unchecked {
 196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();
 197:             int128 left128 = int128(left);
 198: 
 199:             if (left128 != left) revert Errors.UnderOverFlow();
 200: 
 201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();
 202:             int128 right128 = int128(right);
 203: 
 204:             if (right128 != right) revert Errors.UnderOverFlow();
 205: 
 206:             return z.toRightSlot(right128).toLeftSlot(left128);
 207:         }
 208:     }

```

*GitHub* : [194-208](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L194-L208)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.validateIsExercisable(TokenId,int24) (contracts/types/TokenId.sol#578-599) has uint/ int smaller than 256-bit:
	- TokenIdLibrary.validateIsExercisable(TokenId,int24)._strike (contracts/types/TokenId.sol#587)
	- TokenIdLibrary.validateIsExercisable(TokenId,int24).rangeUp (contracts/types/TokenId.sol#582)
	- TokenIdLibrary.validateIsExercisable(TokenId,int24).rangeDown (contracts/types/TokenId.sol#582)

/// @audit ************** Possible Issue Line(s) **************
	L#587,  L#582,  

/// @audit ****************** Affected Code *******************
 578:     function validateIsExercisable(TokenId self, int24 currentTick) internal pure {
 579:         unchecked {
 580:             uint256 numLegs = self.countLegs();
 581:             for (uint256 i = 0; i < numLegs; ++i) {
 582:                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(
 583:                     self.width(i),
 584:                     self.tickSpacing()
 585:                 );
 586: 
 587:                 int24 _strike = self.strike(i);
 588:                 // check if the price is outside this chunk
 589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {
 590:                     // if this leg is long and the price beyond the leg's range:
 591:                     // this exercised ID, `self`, appears valid
 592:                     if (self.isLong(i) == 1) return; // validated
 593:                 }
 594:             }
 595:         }
 596: 
 597:         // Fail if position has no legs that is far-out-of-the-money
 598:         revert Errors.NoLegsExercisable();
 599:     }

```

*GitHub* : [578-599](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L578-L599)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.sub(LeftRightSigned,LeftRightSigned) (contracts/types/LeftRight.sol#232-244) has uint/ int smaller than 256-bit:
	- LeftRightLibrary.sub(LeftRightSigned,LeftRightSigned).left128 (contracts/types/LeftRight.sol#235)
	- LeftRightLibrary.sub(LeftRightSigned,LeftRightSigned).right128 (contracts/types/LeftRight.sol#238)

/// @audit ************** Possible Issue Line(s) **************
	L#235,  L#238,  

/// @audit ****************** Affected Code *******************
 232:     function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 233:         unchecked {
 234:             int256 left256 = int256(x.leftSlot()) - y.leftSlot();
 235:             int128 left128 = int128(left256);
 236: 
 237:             int256 right256 = int256(x.rightSlot()) - y.rightSlot();
 238:             int128 right128 = int128(right256);
 239: 
 240:             if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();
 241: 
 242:             return z.toRightSlot(right128).toLeftSlot(left128);
 243:         }
 244:     }

```

*GitHub* : [232-244](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L232-L244)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._createPositionInAMM(IUniswapV3Pool,TokenId,uint128,bool) (contracts/SemiFungiblePositionManager.sol#863-941) has uint/ int smaller than 256-bit:
	- SemiFungiblePositionManager._createPositionInAMM(IUniswapV3Pool,TokenId,uint128,bool)._positionSize (contracts/SemiFungiblePositionManager.sol#892)

/// @audit ************** Possible Issue Line(s) **************
	L#892,  

/// @audit ****************** Affected Code *******************
 892:                 uint128 _positionSize = positionSize;

```

*GitHub* : [863-941](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L863-L941)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.calculateAccumulatedFeesBatch(address,bool,TokenId[]) (contracts/PanopticPool.sol#381-400) has uint/ int smaller than 256-bit:
	- PanopticPool.calculateAccumulatedFeesBatch(address,bool,TokenId[]).currentTick (contracts/PanopticPool.sol#387)

/// @audit ************** Possible Issue Line(s) **************
	L#387,  

/// @audit ****************** Affected Code *******************
 381:     function calculateAccumulatedFeesBatch(
 382:         address user,
 383:         bool includePendingPremium,
 384:         TokenId[] calldata positionIdList
 385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {
 386:         // Get the current tick of the Uniswap pool
 387:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
 388: 
 389:         // Compute the accumulated premia for all tokenId in positionIdList (includes short+long premium)
 390:         (LeftRightSigned premia, uint256[2][] memory balances) = _calculateAccumulatedPremia(
 391:             user,
 392:             positionIdList,
 393:             COMPUTE_ALL_PREMIA,
 394:             includePendingPremium,
 395:             currentTick
 396:         );
 397: 
 398:         // Return the premia as (token0, token1)
 399:         return (premia.rightSlot(), premia.leftSlot(), balances);
 400:     }

```

*GitHub* : [381-400](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L381-L400)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updatePositionDataBurn(address,TokenId) (contracts/PanopticPool.sol#859-878) has uint/ int smaller than 256-bit:
	- PanopticPool._updatePositionDataBurn(address,TokenId).tickLower (contracts/PanopticPool.sol#867)
	- PanopticPool._updatePositionDataBurn(address,TokenId).tickUpper (contracts/PanopticPool.sol#867)

/// @audit ************** Possible Issue Line(s) **************
	L#867,  

/// @audit ****************** Affected Code *******************
 859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {
 860:         // reset balances and delete stored option data
 861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
 862: 
 863:         uint256 numLegs = tokenId.countLegs();
 864:         for (uint256 leg = 0; leg < numLegs; ) {
 865:             if (tokenId.isLong(leg) == 0) {
 866:                 // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
 867:                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
 868:                 _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
 869:             }
 870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
 871:             unchecked {
 872:                 ++leg;
 873:             }
 874:         }
 875: 
 876:         // Update the position list hash (hash = XOR of all keccak256(tokenId)). Remove hash by XOR'ing again
 877:         _updatePositionsHash(owner, tokenId, !ADD);
 878:     }

```

*GitHub* : [859-878](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L859-L878)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) has uint/ int smaller than 256-bit:
	- PanopticPool.settleLongPremium(TokenId[],address,uint256).tickLower (contracts/PanopticPool.sol#1602)
	- PanopticPool.settleLongPremium(TokenId[],address,uint256).premiumAccumulator0 (contracts/PanopticPool.sol#1605)
	- PanopticPool.settleLongPremium(TokenId[],address,uint256).tickUpper (contracts/PanopticPool.sol#1602)
	- PanopticPool.settleLongPremium(TokenId[],address,uint256).currentTick (contracts/PanopticPool.sol#1598)
	- PanopticPool.settleLongPremium(TokenId[],address,uint256).premiumAccumulator1 (contracts/PanopticPool.sol#1605)

/// @audit ************** Possible Issue Line(s) **************
	L#1602,  L#1605,  L#1598,  

/// @audit ****************** Affected Code *******************
1598:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
1602:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);
1605:             (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.initializeAMMPool(address,address,uint24) (contracts/SemiFungiblePositionManager.sol#350-391) has uint/ int smaller than 256-bit:
	- SemiFungiblePositionManager.initializeAMMPool(address,address,uint24).poolId (contracts/SemiFungiblePositionManager.sol#367)

/// @audit ************** Possible Issue Line(s) **************
	L#367,  

/// @audit ****************** Affected Code *******************
 367:         uint64 poolId = PanopticMath.getPoolId(univ3pool);

```

*GitHub* : [350-391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350-L391)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.startToken(bool,address,address,uint24,PanopticPool) (contracts/CollateralTracker.sol#221-264) has uint/ int smaller than 256-bit:
	- CollateralTracker.startToken(bool,address,address,uint24,PanopticPool)._poolFee (contracts/CollateralTracker.sol#247)

/// @audit ************** Possible Issue Line(s) **************
	L#247,  

/// @audit ****************** Affected Code *******************
 247:         uint24 _poolFee;

```

*GitHub* : [221-264](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221-L264)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeDecimals(address) (contracts/libraries/InteractionHelper.sol#107-115) has uint/ int smaller than 256-bit:
	- InteractionHelper.computeDecimals(address)._decimals (contracts/libraries/InteractionHelper.sol#110)

/// @audit ************** Possible Issue Line(s) **************
	L#110,  

/// @audit ****************** Affected Code *******************
 107:     function computeDecimals(address token) external view returns (uint8) {
 108:         // not guaranteed that token supports metadada extension
 109:         // so we need to let call fail and return placeholder if not
 110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {
 111:             return _decimals;
 112:         } catch {
 113:             return 0;
 114:         }
 115:     }

```

*GitHub* : [107-115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L107-L115)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getAmount0ForLiquidity(LiquidityChunk) (contracts/libraries/Math.sol#191-202) has uint/ int smaller than 256-bit:
	- Math.getAmount0ForLiquidity(LiquidityChunk).lowPriceX96 (contracts/libraries/Math.sol#192)
	- Math.getAmount0ForLiquidity(LiquidityChunk).highPriceX96 (contracts/libraries/Math.sol#193)

/// @audit ************** Possible Issue Line(s) **************
	L#192,  L#193,  

/// @audit ****************** Affected Code *******************
 191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
 192:         uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
 193:         uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());
 194:         unchecked {
 195:             return
 196:                 mulDiv(
 197:                     uint256(liquidityChunk.liquidity()) << 96,
 198:                     highPriceX96 - lowPriceX96,
 199:                     highPriceX96
 200:                 ) / lowPriceX96;
 201:         }
 202:     }

```

*GitHub* : [191-202](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L191-L202)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) has uint/ int smaller than 256-bit:
	- PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).currentTick (contracts/PanopticPool.sol#1032)
	- PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[])._finalTick (contracts/PanopticPool.sol#1119)
	- PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).twapTick (contracts/PanopticPool.sol#1026)
	- PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).finalTick (contracts/PanopticPool.sol#1077)

/// @audit ************** Possible Issue Line(s) **************
	L#1032,  L#1119,  L#1026,  L#1077,  

/// @audit ****************** Affected Code *******************
1026:         int24 twapTick = getUniV3TWAP();
1032:             (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
1077:         int24 finalTick;
1119:             int24 _finalTick = finalTick;

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getPoolId(address) (contracts/libraries/PanopticMath.sol#47-54) has uint/ int smaller than 256-bit:
	- PanopticMath.getPoolId(address).tickSpacing (contracts/libraries/PanopticMath.sol#49)
	- PanopticMath.getPoolId(address).poolId (contracts/libraries/PanopticMath.sol#50)

/// @audit ************** Possible Issue Line(s) **************
	L#49,  L#50,  

/// @audit ****************** Affected Code *******************
  47:     function getPoolId(address univ3pool) internal view returns (uint64) {
  48:         unchecked {
  49:             int24 tickSpacing = IUniswapV3Pool(univ3pool).tickSpacing();
  50:             uint64 poolId = uint64(uint160(univ3pool) >> 112);
  51:             poolId += uint64(uint24(tickSpacing)) << 48;
  52:             return poolId;
  53:         }
  54:     }

```

*GitHub* : [47-54](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L47-L54)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256) (contracts/SemiFungiblePositionManager.sol#1255-1313) has uint/ int smaller than 256-bit:
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).receivedAmount0 (contracts/SemiFungiblePositionManager.sol#1284)
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).startingLiquidity (contracts/SemiFungiblePositionManager.sol#1263)
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).collected0 (contracts/SemiFungiblePositionManager.sol#1293)
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).collected1 (contracts/SemiFungiblePositionManager.sol#1294)
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).receivedAmount1 (contracts/SemiFungiblePositionManager.sol#1284)

/// @audit ************** Possible Issue Line(s) **************
	L#1284,  L#1263,  L#1293,  L#1294,  

/// @audit ****************** Affected Code *******************
1263:         uint128 startingLiquidity = currentLiquidity.rightSlot();
1284:             (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(
1293:             uint128 collected0;
1294:             uint128 collected1;

```

*GitHub* : [1255-1313](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255-L1313)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getTicks(int24,int24,int24) (contracts/libraries/PanopticMath.sol#338-363) has uint/ int smaller than 256-bit:
	- PanopticMath.getTicks(int24,int24,int24).minTick (contracts/libraries/PanopticMath.sol#346)
	- PanopticMath.getTicks(int24,int24,int24).maxTick (contracts/libraries/PanopticMath.sol#347)
	- PanopticMath.getTicks(int24,int24,int24).rangeUp (contracts/libraries/PanopticMath.sol#349)
	- PanopticMath.getTicks(int24,int24,int24).rangeDown (contracts/libraries/PanopticMath.sol#349)

/// @audit ************** Possible Issue Line(s) **************
	L#346,  L#347,  L#349,  

/// @audit ****************** Affected Code *******************
 346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;
 347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;
 349:             (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(width, tickSpacing);

```

*GitHub* : [338-363](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L338-L363)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getLiquidityForAmount1(int24,int24,uint256) (contracts/libraries/Math.sol#271-287) has uint/ int smaller than 256-bit:
	- Math.getLiquidityForAmount1(int24,int24,uint256).lowPriceX96 (contracts/libraries/Math.sol#276)
	- Math.getLiquidityForAmount1(int24,int24,uint256).highPriceX96 (contracts/libraries/Math.sol#277)

/// @audit ************** Possible Issue Line(s) **************
	L#276,  L#277,  

/// @audit ****************** Affected Code *******************
 271:     function getLiquidityForAmount1(
 272:         int24 tickLower,
 273:         int24 tickUpper,
 274:         uint256 amount1
 275:     ) internal pure returns (LiquidityChunk) {
 276:         uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);
 277:         uint160 highPriceX96 = getSqrtRatioAtTick(tickUpper);
 278: 
 279:         unchecked {
 280:             return
 281:                 LiquidityChunkLibrary.createChunk(
 282:                     tickLower,
 283:                     tickUpper,
 284:                     toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))
 285:                 );
 286:         }
 287:     }

```

*GitHub* : [271-287](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L271-L287)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._validateSolvency(address,TokenId[],uint256) (contracts/PanopticPool.sol#887-946) has uint/ int smaller than 256-bit:
	- PanopticPool._validateSolvency(address,TokenId[],uint256).fastOracleTick (contracts/PanopticPool.sol#905-911)
	- PanopticPool._validateSolvency(address,TokenId[],uint256).slowOracleTick (contracts/PanopticPool.sol#913)
	- PanopticPool._validateSolvency(address,TokenId[],uint256).observationIndex (contracts/PanopticPool.sol#899)
	- PanopticPool._validateSolvency(address,TokenId[],uint256).currentTick (contracts/PanopticPool.sol#898)
	- PanopticPool._validateSolvency(address,TokenId[],uint256).observationCardinality (contracts/PanopticPool.sol#900)

/// @audit ************** Possible Issue Line(s) **************
	L#905-911,  L#913,  L#899,  L#898,  L#900,  

/// @audit ****************** Affected Code *******************
 898:             int24 currentTick,
 899:             uint16 observationIndex,
 900:             uint16 observationCardinality,
 905:         int24 fastOracleTick = PanopticMath.computeMedianObservedPrice(
 906:             _univ3pool,
 907:             observationIndex,
 908:             observationCardinality,
 909:             FAST_ORACLE_CARDINALITY,
 910:             FAST_ORACLE_PERIOD
 911:         );
 913:         int24 slowOracleTick;

```

*GitHub* : [887-946](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L887-L946)

### [G-15]<a name="g-15"></a> Use Bytes32 for small data storage

Using bytes32 is cheaper in Solidity when the data can fit into 32 bytes.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker (contracts/CollateralTracker.sol#36-1650) should use bytes32 for following string constant(s) :-
	- CollateralTracker.TICKER_PREFIX (contracts/CollateralTracker.sol#70)
	- CollateralTracker.NAME_PREFIX (contracts/CollateralTracker.sol#73)

/// @audit ************** Possible Issue Line(s) **************
	L#70,  L#73,  

/// @audit ****************** Affected Code *******************
  70:     string internal constant TICKER_PREFIX = "po";
  73:     string internal constant NAME_PREFIX = "POPT-V1";

```

*GitHub* : [36-1650](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L36-L1650)

### [G-16]<a name="g-16"></a> Solidity versions 0.8.19 and above are more gas efficient

Solidity version 0.8.19 introduced a array of gas optimizations which make contracts which use it more efficient. Provided compatability it may be beneficial to upgrade to this version

*There are 20 instance(s) of this issue:*

```solidity
File: contracts/libraries/SafeTransferLib.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/libraries/SafeTransferLib.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L2-L2)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
^0.8.18 (contracts/SemiFungiblePositionManager.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.18;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L2-L2)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/libraries/InteractionHelper.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L2-L2)

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/tokens/interfaces/IDonorNFT.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IDonorNFT.sol#L2-L2)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
^0.8.18 (contracts/CollateralTracker.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.18;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L2-L2)

```solidity
File: contracts/libraries/Errors.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/libraries/Errors.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L2-L2)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
^0.8.18 (contracts/PanopticPool.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.18;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L2-L2)

```solidity
File: contracts/libraries/CallbackLib.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/libraries/CallbackLib.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L2-L2)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/libraries/Math.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L2-L2)

```solidity
File: contracts/libraries/Constants.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/libraries/Constants.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L2-L2)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/types/TokenId.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L2-L2)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/types/LeftRight.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L2-L2)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
^0.8.18 (contracts/PanopticFactory.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.18;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L2-L2)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/types/LiquidityChunk.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L2-L2)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/tokens/ERC1155Minimal.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2-L2)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/libraries/FeesCalc.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L2-L2)

```solidity
File: contracts/multicall/Multicall.sol

/// @audit ******************* Issue Detail *******************
^0.8.18 (contracts/multicall/Multicall.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.18;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L2-L2)

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/tokens/interfaces/IERC20Partial.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IERC20Partial.sol#L2-L2)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/tokens/ERC20Minimal.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L2-L2)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
^0.8.0 (contracts/libraries/PanopticMath.sol#2) version lesser than 0.8.19:

/// @audit ************** Possible Issue Line(s) **************
	L#2,  

/// @audit ****************** Affected Code *******************
   2: pragma solidity ^0.8.0;

```

*GitHub* : [2-2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L2-L2)

### [G-17]<a name="g-17"></a> Optimal State Variable Order

Detects optimal variable order in contract storage layouts to decrease the number of storage slots used. Each storage slot used can cost at least 5,000 gas for each write operation, and potentially up to 20,000 gas if you're turning a zero value into a non-zero value. Hence, optimizing storage usage can result in significant gas savings. The real-world savings could vary depending on your contract's specific logic and the state of the Ethereum network.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool (contracts/PanopticPool.sol#27-1981) should reorder state variables as following :- 
```solidity

Orignal variable order (count: 21 slots)
Slot 1: ['int24 MIN_SWAP_TICK (3B)', 'int24 MAX_SWAP_TICK (3B)', 'bool COMPUTE_ALL_PREMIA (1B)', 'bool COMPUTE_LONG_PREMIA (1B)', 'bool ONLY_AVAILABLE_PREMIUM (1B)', 'bool COMMIT_LONG_SETTLED (1B)', 'bool DONOT_COMMIT_LONG_SETTLED (1B)', 'bool ADD (1B)', 'uint32 TWAP_WINDOW (4B)', 'bool SLOW_ORACLE_UNISWAP_MODE (1B)'] 
Slot 2: ['uint256 MEDIAN_PERIOD (32B)'] 
Slot 3: ['uint256 FAST_ORACLE_CARDINALITY (32B)'] 
Slot 4: ['uint256 FAST_ORACLE_PERIOD (32B)'] 
Slot 5: ['uint256 SLOW_ORACLE_CARDINALITY (32B)'] 
Slot 6: ['uint256 SLOW_ORACLE_PERIOD (32B)'] 
Slot 7: ['int256 MAX_TWAP_DELTA_LIQUIDATION (32B)'] 
Slot 8: ['int256 MAX_SLOW_FAST_DELTA (32B)'] 
Slot 9: ['uint64 MAX_SPREAD (8B)', 'uint64 MAX_POSITIONS (8B)'] 
Slot 10: ['uint256 BP_DECREASE_BUFFER (32B)'] 
Slot 11: ['uint256 NO_BUFFER (32B)'] 
Slot 12: ['SemiFungiblePositionManager SFPM (20B)'] 
Slot 13: ['IUniswapV3Pool s_univ3pool (20B)'] 
Slot 14: ['uint256 s_miniMedian (32B)'] 
Slot 15: ['CollateralTracker s_collateralToken0 (20B)'] 
Slot 16: ['CollateralTracker s_collateralToken1 (20B)'] 
Slot 17: ['mapping(address => mapping(TokenId => mapping(uint256 => LeftRightUnsigned))) s_options (32B)'] 
Slot 18: ['mapping(bytes32 => LeftRightUnsigned) s_grossPremiumLast (32B)'] 
Slot 19: ['mapping(bytes32 => LeftRightUnsigned) s_settledTokens (32B)'] 
Slot 20: ['mapping(address => mapping(TokenId => LeftRightUnsigned)) s_positionBalance (32B)'] 
Slot 21: ['mapping(address => uint256) s_positionsHash (32B)'] 

Optimized variable order (count: 19 slots)
Slot 1: ['uint256 MEDIAN_PERIOD (32B)'] 
Slot 2: ['uint256 FAST_ORACLE_CARDINALITY (32B)'] 
Slot 3: ['uint256 FAST_ORACLE_PERIOD (32B)'] 
Slot 4: ['uint256 SLOW_ORACLE_CARDINALITY (32B)'] 
Slot 5: ['uint256 SLOW_ORACLE_PERIOD (32B)'] 
Slot 6: ['int256 MAX_TWAP_DELTA_LIQUIDATION (32B)'] 
Slot 7: ['int256 MAX_SLOW_FAST_DELTA (32B)'] 
Slot 8: ['uint256 BP_DECREASE_BUFFER (32B)'] 
Slot 9: ['uint256 NO_BUFFER (32B)'] 
Slot 10: ['uint256 s_miniMedian (32B)'] 
Slot 11: ['mapping(address => mapping(TokenId => mapping(uint256 => LeftRightUnsigned))) s_options (32B)'] 
Slot 12: ['mapping(bytes32 => LeftRightUnsigned) s_grossPremiumLast (32B)'] 
Slot 13: ['mapping(bytes32 => LeftRightUnsigned) s_settledTokens (32B)'] 
Slot 14: ['mapping(address => mapping(TokenId => LeftRightUnsigned)) s_positionBalance (32B)'] 
Slot 15: ['mapping(address => uint256) s_positionsHash (32B)'] 
Slot 16: ['SemiFungiblePositionManager SFPM (20B)', 'uint64 MAX_SPREAD (8B)', 'uint32 TWAP_WINDOW (4B)'] 
Slot 17: ['IUniswapV3Pool s_univ3pool (20B)', 'uint64 MAX_POSITIONS (8B)', 'int24 MIN_SWAP_TICK (3B)', 'bool COMPUTE_ALL_PREMIA (1B)'] 
Slot 18: ['CollateralTracker s_collateralToken0 (20B)', 'int24 MAX_SWAP_TICK (3B)', 'bool COMPUTE_LONG_PREMIA (1B)', 'bool ONLY_AVAILABLE_PREMIUM (1B)', 'bool COMMIT_LONG_SETTLED (1B)', 'bool DONOT_COMMIT_LONG_SETTLED (1B)', 'bool ADD (1B)', 'bool SLOW_ORACLE_UNISWAP_MODE (1B)'] 
Slot 19: ['CollateralTracker s_collateralToken1 (20B)'] 
```

/// @audit ****************** Affected Code *******************
  27: contract PanopticPool is ERC1155Holder, Multicall {
  28:     /*//////////////////////////////////////////////////////////////
  29:                                 EVENTS
  30:     //////////////////////////////////////////////////////////////*/
  31: 
  32:     /// @notice Emitted when an account is liquidated.
  33:     /// @dev Need to unpack bonusAmounts to get raw numbers, which are always positive.
  34:     /// @param liquidator Address of the caller whom is liquidating the distressed account.
  35:     /// @param liquidatee Address of the distressed/liquidatable account.
  36:     /// @param bonusAmounts LeftRight encoding for the the bonus paid for token 0 (right slot) and 1 (left slot) from the Panoptic Pool to the liquidator.

```

*GitHub* : [27-1981](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L27-L1981)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker (contracts/CollateralTracker.sol#36-1650) should reorder state variables as following :- 
```solidity

Orignal variable order (count: 18 slots)
Slot 1: ['string TICKER_PREFIX (32B)'] 
Slot 2: ['string NAME_PREFIX (32B)'] 
Slot 3: ['uint256 DECIMALS (32B)'] 
Slot 4: ['int128 DECIMALS_128 (16B)'] 
Slot 5: ['address s_underlyingToken (20B)', 'bool s_initialized (1B)'] 
Slot 6: ['address s_univ3token0 (20B)'] 
Slot 7: ['address s_univ3token1 (20B)', 'bool s_underlyingIsToken0 (1B)'] 
Slot 8: ['PanopticPool s_panopticPool (20B)'] 
Slot 9: ['uint128 s_poolAssets (16B)', 'uint128 s_inAMM (16B)'] 
Slot 10: ['uint128 s_ITMSpreadFee (16B)', 'uint24 s_poolFee (3B)'] 
Slot 11: ['uint256 TICK_DEVIATION (32B)'] 
Slot 12: ['uint256 COMMISSION_FEE (32B)'] 
Slot 13: ['uint256 SELLER_COLLATERAL_RATIO (32B)'] 
Slot 14: ['uint256 BUYER_COLLATERAL_RATIO (32B)'] 
Slot 15: ['int256 FORCE_EXERCISE_COST (32B)'] 
Slot 16: ['uint256 TARGET_POOL_UTIL (32B)'] 
Slot 17: ['uint256 SATURATED_POOL_UTIL (32B)'] 
Slot 18: ['uint256 ITM_SPREAD_MULTIPLIER (32B)'] 

Optimized variable order (count: 17 slots)
Slot 1: ['string TICKER_PREFIX (32B)'] 
Slot 2: ['string NAME_PREFIX (32B)'] 
Slot 3: ['uint256 DECIMALS (32B)'] 
Slot 4: ['uint256 TICK_DEVIATION (32B)'] 
Slot 5: ['uint256 COMMISSION_FEE (32B)'] 
Slot 6: ['uint256 SELLER_COLLATERAL_RATIO (32B)'] 
Slot 7: ['uint256 BUYER_COLLATERAL_RATIO (32B)'] 
Slot 8: ['int256 FORCE_EXERCISE_COST (32B)'] 
Slot 9: ['uint256 TARGET_POOL_UTIL (32B)'] 
Slot 10: ['uint256 SATURATED_POOL_UTIL (32B)'] 
Slot 11: ['uint256 ITM_SPREAD_MULTIPLIER (32B)'] 
Slot 12: ['address s_underlyingToken (20B)', 'uint24 s_poolFee (3B)', 'bool s_initialized (1B)', 'bool s_underlyingIsToken0 (1B)'] 
Slot 13: ['address s_univ3token0 (20B)'] 
Slot 14: ['address s_univ3token1 (20B)'] 
Slot 15: ['PanopticPool s_panopticPool (20B)'] 
Slot 16: ['int128 DECIMALS_128 (16B)', 'uint128 s_poolAssets (16B)'] 
Slot 17: ['uint128 s_inAMM (16B)', 'uint128 s_ITMSpreadFee (16B)'] 
```

/// @audit ****************** Affected Code *******************
  36: contract CollateralTracker is ERC20Minimal, Multicall {
  37:     // Used for safecasting
  38:     using Math for uint256;
  39: 
  40:     /*//////////////////////////////////////////////////////////////
  41:                                 EVENTS
  42:     //////////////////////////////////////////////////////////////*/
  43: 
  44:     /// @notice Emitted when assets are deposited into the Collateral Tracker.
  45:     /// @param sender The address of the caller (and depositor)

```

*GitHub* : [36-1650](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L36-L1650)

### [G-18]<a name="g-18"></a> Use assembly to write address storage values

Using assembly to write address storage values can potentially save gas costs. This detector flags instances where address storage values are written without using assembly.

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.transferOwnership(address) (contracts/PanopticFactory.sol#147-155) writes address state variable :- 
	- s_owner = newOwner (contracts/PanopticFactory.sol#152)

/// @audit ************** Possible Issue Line(s) **************
	L#152,  

/// @audit ****************** Affected Code *******************
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

*GitHub* : [147-155](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147-L155)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.startToken(bool,address,address,uint24,PanopticPool) (contracts/CollateralTracker.sol#221-264) writes address state variable :- 
	- s_univ3token0 = token0 (contracts/CollateralTracker.sol#254)
	- s_univ3token1 = token1 (contracts/CollateralTracker.sol#255)
	- s_underlyingToken = token0 (contracts/CollateralTracker.sol#241)
	- s_underlyingToken = token1 (contracts/CollateralTracker.sol#241)

/// @audit ************** Possible Issue Line(s) **************
	L#254,  L#255,  L#241,  

/// @audit ****************** Affected Code *******************
 241:         s_underlyingToken = underlyingIsToken0 ? token0 : token1;
 254:         s_univ3token0 = token0;
 255:         s_univ3token1 = token1;

```

*GitHub* : [221-264](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221-L264)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address) (contracts/PanopticFactory.sol#115-130) writes address state variable :- 
	- WETH = _WETH9 (contracts/PanopticFactory.sol#123)
	- POOL_REFERENCE = _poolReference (contracts/PanopticFactory.sol#128)
	- COLLATERAL_REFERENCE = _collateralReference (contracts/PanopticFactory.sol#129)

/// @audit ************** Possible Issue Line(s) **************
	L#123,  L#128,  L#129,  

/// @audit ****************** Affected Code *******************
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

*GitHub* : [115-130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L115-L130)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.initialize(address) (contracts/PanopticFactory.sol#134-139) writes address state variable :- 
	- s_owner = _owner (contracts/PanopticFactory.sol#136)

/// @audit ************** Possible Issue Line(s) **************
	L#136,  

/// @audit ****************** Affected Code *******************
 134:     function initialize(address _owner) public {
 135:         if (!s_initialized) {
 136:             s_owner = _owner;
 137:             s_initialized = true;
 138:         }
 139:     }

```

*GitHub* : [134-139](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134-L139)

### [G-19]<a name="g-19"></a> State variable read in a loop

Reading a state variable inside a loop can unnecessarily increase gas consumption, as each read operation from the blockchain state is costly. This inefficiency becomes pronounced in loops with many iterations. To optimize gas usage, it's advisable to read the state variable once before the loop starts, store its value in a local (memory) variable, and then use this local variable within the loop. This approach minimizes the number of state read operations, thereby reducing the gas cost associated with executing the contract function, making the smart contract more efficient and cost-effective to run.

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.minePoolAddress(bytes32,uint256,uint256) (contracts/PanopticFactory.sol#290-326) reads state variables in loop: 
	- rarity = PanopticMath.numberOfLeadingHexZeros(POOL_REFERENCE.predictDeterministicAddress(salt)) (contracts/PanopticFactory.sol#304-306)

/// @audit ************** Possible Issue Line(s) **************
	L#304-306,  

/// @audit ****************** Affected Code *******************
 304:             uint256 rarity = PanopticMath.numberOfLeadingHexZeros(
 305:                 POOL_REFERENCE.predictDeterministicAddress(salt)
 306:             );

```

*GitHub* : [290-326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L290-L326)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.balanceOfBatch(address[],uint256[]) (contracts/tokens/ERC1155Minimal.sol#178-191) reads state variables in loop: 
	- balances[i] = balanceOf[owners[i]][ids[i]] (contracts/tokens/ERC1155Minimal.sol#188)

/// @audit ************** Possible Issue Line(s) **************
	L#188,  

/// @audit ****************** Affected Code *******************
 178:     function balanceOfBatch(
 179:         address[] calldata owners,
 180:         uint256[] calldata ids
 181:     ) public view returns (uint256[] memory balances) {
 182:         balances = new uint256[](owners.length);
 183: 
 184:         // Unchecked because the only math done is incrementing
 185:         // the array index counter which cannot possibly overflow.
 186:         unchecked {
 187:             for (uint256 i = 0; i < owners.length; ++i) {
 188:                 balances[i] = balanceOf[owners[i]][ids[i]];
 189:             }
 190:         }
 191:     }

```

*GitHub* : [178-191](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L178-L191)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.initializeAMMPool(address,address,uint24) (contracts/SemiFungiblePositionManager.sol#350-391) reads state variables in loop: 
	- address(s_poolContext[poolId].pool) != address(0) (contracts/SemiFungiblePositionManager.sol#372)

/// @audit ************** Possible Issue Line(s) **************
	L#372,  

/// @audit ****************** Affected Code *******************
 372:         while (address(s_poolContext[poolId].pool) != address(0)) {

```

*GitHub* : [350-391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350-L391)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/SemiFungiblePositionManager.sol#566-585) reads state variables in loop: 
	- s_poolContext[TokenId.wrap(ids[i]).poolId()].locked (contracts/SemiFungiblePositionManager.sol#576)

/// @audit ************** Possible Issue Line(s) **************
	L#576,  

/// @audit ****************** Affected Code *******************
 566:     function safeBatchTransferFrom(
 567:         address from,
 568:         address to,
 569:         uint256[] calldata ids,
 570:         uint256[] calldata amounts,
 571:         bytes calldata data
 572:     ) public override {
 573:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
 574:         // so just check if there is an active reentrancy lock for the relevant pool on each token
 575:         for (uint256 i = 0; i < ids.length; ) {
 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
 577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
 578:             unchecked {
 579:                 ++i;
 580:             }
 581:         }
 582: 
 583:         // transfer the token (note that all state updates are completed before reentrancy is possible)
 584:         super.safeBatchTransferFrom(from, to, ids, amounts, data);
 585:     }

```

*GitHub* : [566-585](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566-L585)

### [G-20]<a name="g-20"></a> Unnecessary casting as variable is already of the same type

Unnecessary casting of a variable to the same type is redundant and can contribute to gas inefficiency and code clutter. This situation commonly arises when developers, perhaps due to oversight or misunderstanding, explicitly cast a variable to its existing type. For example, casting a `uint256` variable to `uint256` again does not change its type or value but adds unnecessary operations and gas.

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker) (contracts/PanopticPool.sol#291-327) performs same type cast
	- s_univ3pool = IUniswapV3Pool(_univ3pool) (contracts/PanopticPool.sol#302) casts (IUniswapV3Pool) to (IUniswapV3Pool).
	- (currentTick) = IUniswapV3Pool(_univ3pool).slot0() (contracts/PanopticPool.sol#304) casts (IUniswapV3Pool) to (IUniswapV3Pool).

/// @audit ************** Possible Issue Line(s) **************
	L#302,  L#304,  

/// @audit ****************** Affected Code *******************
 302:         s_univ3pool = IUniswapV3Pool(_univ3pool);
 304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

```

*GitHub* : [291-327](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L327)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker) (contracts/PanopticPool.sol#291-327) performs same type cast
	- s_univ3pool = IUniswapV3Pool(_univ3pool) (contracts/PanopticPool.sol#302) casts (IUniswapV3Pool) to (IUniswapV3Pool).

/// @audit ************** Possible Issue Line(s) **************
	L#302,  

/// @audit ****************** Affected Code *******************
 302:         s_univ3pool = IUniswapV3Pool(_univ3pool);

```

*GitHub* : [291-327](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L327)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24) (contracts/PanopticFactory.sol#335-411) performs same type cast
	- IUniswapV3Pool(v3Pool).mint(address(this),tickLower,tickUpper,fullRangeLiquidity,mintCallback) (contracts/PanopticFactory.sol#403-410) casts (IUniswapV3Pool) to (IUniswapV3Pool).

/// @audit ************** Possible Issue Line(s) **************
	L#403-410,  

/// @audit ****************** Affected Code *******************
 403:         return
 404:             IUniswapV3Pool(v3Pool).mint(
 405:                 address(this),
 406:                 tickLower,
 407:                 tickUpper,
 408:                 fullRangeLiquidity,
 409:                 mintCallback
 410:             );

```

*GitHub* : [335-411](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L335-L411)

### [G-21]<a name="g-21"></a> Shorten the array rather than copying to a new one

Leveraging inline assembly in Solidity provides the ability to directly manipulate the length slot of an array, thereby altering its length without the need to copy the elements to a new array of the desired size. This technique is more gas-efficient as it avoids the computational expense associated with array duplication. However, this method circumvents the type-checking and safety mechanisms of high-level Solidity and should be used judiciously. Always ensure that the array doesn't contain vital data beyond the revised length, as this data will become unreachable yet still consume storage space.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/multicall/Multicall.sol

13:         results = new bytes[](data.length);

```



*GitHub* : [13](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L13-L13)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

182:         balances = new uint256[](owners.length);

```


*GitHub* : [182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L182-L182)

### [G-22]<a name="g-22"></a> checks for zero uint should be done using assembly to save gas

Using assembly for simple zero checks on unsigned integers can save gas due to lower-level, optimized operations.

*There are 47 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

664:                 if (positionId.isLong(leg) == 0) continue;

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

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



*GitHub* : [512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L512-L512), [575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L575-L575), [664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L664-L664), [708](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L708-L708), [1325](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1325-L1325), [1328](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1328-L1328), [1339](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1339-L1339), [1347](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1347-L1347), [1375](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1375-L1375), [1479](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1479-L1479), [1544](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1544-L1544), [1582](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1582-L1582), [1584](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1584-L1584), [1637](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1637-L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1638-L1638)

```solidity
File: contracts/PanopticPool.sol

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

865:             if (tokenId.isLong(leg) == 0) {

1483:         if (netLiquidity == 0) return;

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1679:             if (tokenId.isLong(leg) == 0) {

1780:                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),

1789:                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),

```



*GitHub* : [460](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L460-L460), [865](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L865-L865), [1483](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1483-L1483), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1596-L1596), [1679](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1679-L1679), [1780](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1780-L1780), [1789](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1789-L1789)

```solidity
File: contracts/SemiFungiblePositionManager.sol

688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

999:             if (isLong == 0) {

1066:             moved = isLong == 0

1078:             if (tokenType == 0) {

```



*GitHub* : [688](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L688-L688), [833](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L833-L833), [999](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L999-L999), [1066](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1066-L1066), [1078](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1078-L1078)

```solidity
File: contracts/libraries/FeesCalc.sol

67:                 if (tokenId.isLong(leg) == 0) {

```



*GitHub* : [67](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L67-L67)

```solidity
File: contracts/libraries/Math.sol

179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

360:             if (prod1 == 0) {

474:             if (prod1 == 0) {

537:             if (prod1 == 0) {

614:             if (prod1 == 0) {

691:             if (prod1 == 0) {

```



*GitHub* : [179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L179-L179), [360](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L360-L360), [474](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L474-L474), [537](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L537-L537), [614](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L614-L614), [691](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L691-L691)

```solidity
File: contracts/libraries/PanopticMath.sol

325:         if (tokenId.asset(legIndex) == 0) {

425:         if (tokenType == 0) {

475:             uint256 notional = asset == 0

479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

584:         if (tokenId.asset(legIndex) == 0) {

615:         bool isShort = tokenId.isLong(legIndex) == 0;

618:         if (tokenId.tokenType(legIndex) == 0) {

```



*GitHub* : [325](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L325-L325), [425](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L425-L425), [475](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L475-L475), [479](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L479-L479), [584](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L584-L584), [615](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L615-L615), [618](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L618-L618)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

202:             interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

203:             interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

```



*GitHub* : [202](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L202-L202), [203](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L203-L203)

```solidity
File: contracts/types/TokenId.sol

465:         if (i == 0)

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

508:                 if (self.optionRatio(i) == 0) {

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

```


*GitHub* : [465](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L465-L465), [501](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L501-L501), [508](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L508-L508), [528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L528-L528)

### [G-23]<a name="g-23"></a> Use Assembly for Hash Calculation

Assembly version of the `keccak256` hashing function is more efficient than the high-level Solidity version as Solidity has additional overhead when handling function calls and memory management, which can increase the gas cost.

*There are 10 instance(s) of this issue:*

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



*GitHub* : [461](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L461-L467), [1642](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1642-L1648), [1673](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1673-L1675), [1855](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1855-L1857)

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

1150:                 keccak256(
                          abi.encodePacked(
                              address(this),
                              liquidityChunk.tickLower(),
                              liquidityChunk.tickUpper()
                          )
                      )
                  );

```



*GitHub* : [611](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L611-L619), [620](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L620-L628), [974](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L974-L982), [1150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1150-L1157)

```solidity
File: contracts/libraries/PanopticMath.sol

103:                 (uint248(uint256(keccak256(abi.encode(tokenId)))));

878:                         bytes32 chunkKey = keccak256(
                                 abi.encodePacked(
                                     tokenId.strike(0),
                                     tokenId.width(0),
                                     tokenId.tokenType(0)
                                 )
                             );

```


*GitHub* : [103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L103-L103), [878](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L878-L884)

### [G-24]<a name="g-24"></a> `>=` costs less gas than `>`

The compiler uses opcodes `GT` and `ISZERO` for solidity code that uses `>`, but only requires `LT` for `>=`, [which saves **3 gas**](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde). If `<` is being used, the condition can be inverted. In cases where a for-loop is being used, one can count down rather than up, in order to use the optimal operator

*There are 150 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

480:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();

536:         if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

596:         if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

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



*GitHub* : [418](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L418-L418), [480](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L480-L480), [536](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L536-L536), [596](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L596-L596), [662](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L662-L662), [708](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L708-L708), [709](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L709-L709), [776](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L776-L776), [784](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L784-L784), [790](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L790-L790), [835](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L835-L835), [841](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L841-L841), [937](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L937-L937), [976](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L976-L976), [1010](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1010-L1010), [1018](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1018-L1018), [1067](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1067-L1067), [1075](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1075-L1075), [1168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1168-L1168), [1173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1173-L1173), [1182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1182-L1182), [1208](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1208-L1208), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1255-L1255), [1347](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1347-L1347), [1374](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1374-L1374), [1545](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1545-L1545), [1549](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1549-L1549), [1570](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1570-L1570)

```solidity
File: contracts/PanopticFactory.sol

181:         if (amount0Owed > 0)

188:         if (amount1Owed > 0)

217:         (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);

303:         for (; uint256(salt) < maxSalt; ) {

308:             if (rarity > highestRarity) {

378:                 fullRangeLiquidity = liquidity0 > liquidity1 ? liquidity0 : liquidity1;

```



*GitHub* : [181](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L181-L181), [188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L188-L188), [217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L217-L217), [303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L303-L303), [308](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L308-L308), [378](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L378-L378)

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



*GitHub* : [441](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L441-L441), [459](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L459-L459), [510](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L510-L510), [745](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L745-L745), [802](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L802-L802), [864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L864-L864), [943](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L943-L943), [1035](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1035-L1035), [1274](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1274-L1274), [1382](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1382-L1382), [1415](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1415-L1415), [1492](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1492-L1492), [1518](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1518-L1518), [1596](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1596-L1596), [1672](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1672-L1672), [1852](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1852-L1852)

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

1013:                 if (startingLiquidity < chunkLiquidity) {

1085:         if (currentLiquidity.rightSlot() > 0) {

1296:                 collected0 = movedInLeg.rightSlot() < 0

1299:                 collected1 = movedInLeg.leftSlot() < 0

1465:         if (atTick < type(int24).max) {

```



*GitHub* : [412](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L412-L412), [419](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L419-L419), [446](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L446-L446), [453](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L453-L453), [575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L575-L575), [601](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L601-L601), [715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L715-L715), [819](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L819-L819), [824](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L824-L824), [827](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L827-L827), [882](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L882-L882), [939](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L939-L939), [1013](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1013-L1013), [1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1085-L1085), [1296](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1296-L1296), [1299](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1299-L1299), [1465](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1465-L1465)

```solidity
File: contracts/libraries/FeesCalc.sol

51:         for (uint256 k = 0; k < positionIdList.length; ) {

55:             for (uint256 leg = 0; leg < numLegs; ) {

147:             if (currentTick < tickLower) {

```



*GitHub* : [51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L51-L51), [55](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L55-L55), [147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L147-L147)

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



*GitHub* : [26](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L26-L26), [34](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L34-L34), [42](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L42-L42), [50](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L50-L50), [58](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L58-L58), [66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L66-L66), [74](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L74-L74), [83](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L83-L83), [130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L130-L130), [131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L131-L131), [176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L176-L176), [312](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L312-L312), [326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L326-L326), [361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L361-L361), [370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L370-L370), [447](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L447-L447), [448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448-L448), [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L484-L484), [547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L547-L547), [587](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L587-L587), [588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588-L588), [624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L624-L624), [664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L664-L664), [665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665-L665), [701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L701-L701), [759](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L759-L759), [760](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L760-L760), [761](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L761-L761), [768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L768-L768), [769](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L769-L769)

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



*GitHub* : [137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L137-L137), [148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L148-L148), [207](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L207-L207), [218](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L218-L218), [248](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L248-L248), [256](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L256-L256), [359](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L359-L359), [360](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L360-L360), [395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L395-L395), [479](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L479-L479), [494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L494-L494), [511](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L511-L511), [528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L528-L528), [532](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L532-L532), [537](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L537-L537), [551](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L551-L551), [555](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L555-L555), [564](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L564-L564), [704](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L704-L704), [706](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L706-L706), [724](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L724-L724), [781](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L781-L781), [784](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L784-L784), [798](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L798-L798), [799](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L799-L799), [822](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L822-L822), [823](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L823-L823), [860](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L860-L860), [863](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L863-L863), [931](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L931-L931), [949](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L949-L949)

```solidity
File: contracts/multicall/Multicall.sol

14:         for (uint256 i = 0; i < data.length; ) {

```



*GitHub* : [14](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L14-L14)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

143:         for (uint256 i = 0; i < ids.length; ) {

187:             for (uint256 i = 0; i < owners.length; ++i) {

```



*GitHub* : [143](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L143-L143), [187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L187-L187)

```solidity
File: contracts/types/LeftRight.sol

161:                 LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||

162:                 (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))

184:                 LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||

185:                 (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))

```



*GitHub* : [161](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L161-L161), [162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L162-L162), [184](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L184-L184), [185](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L185-L185)

```solidity
File: contracts/types/TokenId.sol

376:             if (optionRatios < 2 ** 64) {

378:             } else if (optionRatios < 2 ** 112) {

380:             } else if (optionRatios < 2 ** 160) {

382:             } else if (optionRatios < 2 ** 208) {

439:         if (optionRatios < 2 ** 64) {

441:         } else if (optionRatios < 2 ** 112) {

443:         } else if (optionRatios < 2 ** 160) {

445:         } else if (optionRatios < 2 ** 208) {

507:             for (uint256 i = 0; i < 4; ++i) {

520:                 for (uint256 j = i + 1; j < numLegs; ++j) {

581:             for (uint256 i = 0; i < numLegs; ++i) {

589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {

```


*GitHub* : [376](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L376-L376), [378](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L378-L378), [380](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L380-L380), [382](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L382-L382), [439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L439-L439), [441](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L441-L441), [443](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L443-L443), [445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L445-L445), [507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L507-L507), [520](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L520-L520), [581](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L581-L581), [589](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L589-L589)

### [G-25]<a name="g-25"></a> Counting down in for statements is more gas efficient

Looping downwards in Solidity is more gas efficient due to how the EVM compares variables. In a 'for' loop that counts down, the end condition is usually to compare with zero, which is cheaper than comparing with another number. As such, restructure your loops to count downwards where possible.

*There are 16 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

1255:             for (uint256 index = 0; index < numLegs; ++index) {

```



*GitHub* : [662](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L662-L662), [1255](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1255-L1255)

```solidity
File: contracts/PanopticPool.sol

1672:         for (uint256 leg = 0; leg < numLegs; ++leg) {

```



*GitHub* : [1672](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1672-L1672)

```solidity
File: contracts/libraries/PanopticMath.sol

137:             for (uint256 i = 0; i < cardinality + 1; ++i) {

148:             for (uint256 i = 0; i < cardinality; ++i) {

207:                 for (uint8 i; i < 8; ++i) {

248:             for (uint256 i = 0; i < 20; ++i) {

256:             for (uint256 i = 0; i < 19; ++i) {

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

```



*GitHub* : [137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L137-L137), [148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L148-L148), [207](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L207-L207), [248](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L248-L248), [256](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L256-L256), [781](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L781-L781), [784](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L784-L784), [860](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L860-L860), [863](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L863-L863)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

187:             for (uint256 i = 0; i < owners.length; ++i) {

```



*GitHub* : [187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L187-L187)

```solidity
File: contracts/types/TokenId.sol

507:             for (uint256 i = 0; i < 4; ++i) {

520:                 for (uint256 j = i + 1; j < numLegs; ++j) {

581:             for (uint256 i = 0; i < numLegs; ++i) {

```


*GitHub* : [507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L507-L507), [520](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L520-L520), [581](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L581-L581)

### [G-26]<a name="g-26"></a> Avoid transferring amounts of zero in order to save gas

Skipping the external call when nothing will be transferred, will save at least **100 gas**

*There are 12 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

333:         return ERC20Minimal.transfer(recipient, amount);

352:         return ERC20Minimal.transferFrom(from, to, amount);

424:         SafeTransferLib.safeTransferFrom(

484:         SafeTransferLib.safeTransferFrom(

556:         SafeTransferLib.safeTransferFrom(

616:         SafeTransferLib.safeTransferFrom(

```



*GitHub* : [333](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L333-L333), [352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L352-L352), [424](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L424-L424), [484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L484-L484), [556](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L556-L556), [616](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L616-L616)

```solidity
File: contracts/PanopticFactory.sol

182:             SafeTransferLib.safeTransferFrom(

189:             SafeTransferLib.safeTransferFrom(

```



*GitHub* : [182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L182-L182), [189](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L189-L189)

```solidity
File: contracts/SemiFungiblePositionManager.sol

413:             SafeTransferLib.safeTransferFrom(

420:             SafeTransferLib.safeTransferFrom(

456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

555:         super.safeTransferFrom(from, to, id, amount, data);

```


*GitHub* : [413](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L413-L413), [420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L420-L420), [456](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L456-L456), [555](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L555-L555)


