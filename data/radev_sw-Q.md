
1. `constructor`/`initialize` function lacks parameter validation
        
        Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.
        
        ```solidity
        📁 File: contracts/CollateralTracker.sol
        
        /// @audit _commissionFee , _sellerCollateralRatio , _buyerCollateralRatio , _forceExerciseCost , _targetPoolUtilization , _saturatedPoolUtilization , _ITMSpreadMultiplier
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
        
        [178](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L178-L186)
        
        ```solidity
        📁 File: contracts/PanopticFactory.sol
        
        /// @audit _WETH9 , _SFPM , _univ3Factory , _donorNFT , _poolReference , _collateralReference
        115:     constructor(
        116:         address _WETH9,
        117:         SemiFungiblePositionManager _SFPM,
        118:         IUniswapV3Factory _univ3Factory,
        119:         IDonorNFT _donorNFT,
        120:         address _poolReference,
        121:         address _collateralReference
        122:     ) {
        
        /// @audit _owner
        134:     function initialize(address _owner) public {
        
        ```
        
        [115](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L115-L122), [134](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L134)
        
        ```solidity
        📁 File: contracts/PanopticPool.sol
        
        /// @audit _sfpm
        280:     constructor(SemiFungiblePositionManager _sfpm) {
        
        ```
        
        [280](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L280)
        
        ```solidity
        📁 File: contracts/SemiFungiblePositionManager.sol
        
        /// @audit _factory
        341:     constructor(IUniswapV3Factory _factory) {
        
        ```
        
        [341](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L341)
        
    2. Contract contains payable multicall
        
        In the functions bellow loops over all of the execution call data targets and executes them, sending the ethers to the to target address of each request. To avoid a DOS the team have implemented a role restriction of the functions, but duo to the nature of handling control flow through doing .call, an OOG grief is possible.
        
        ```solidity
        📁 File: contracts/multicall/Multicall.sol
        
        14:         for (uint256 i = 0; i < data.length; ) {
        15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);
        16:
        17:             if (!success) {
        18:                 // Bubble up the revert reason
        19:                 // The bytes type is ABI encoded as a length-prefixed byte array
        20:                 // So we simply need to add 32 to the pointer to get the start of the data
        21:                 // And then revert with the size loaded from the first 32 bytes
        22:                 // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
        23:                 // However, we have chosen to simply replicate the the normal behavior of the call
        24:                 // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
        25:                 assembly ("memory-safe") {
        26:                     revert(add(result, 32), mload(result))
        27:                 }
        28:             }
        29:
        30:             results[i] = result;
        31:
        32:             unchecked {
        33:                 ++i;
        34:             }
        35:         }
        
        ```
        
        [14](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L14-L35)
        
    3. Consider bounding input array length
    The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to `require()` that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.
        
        ```solidity
        📁 File: contracts/SemiFungiblePositionManager.sol
        
        575:         for (uint256 i = 0; i < ids.length; ) {
        576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
        577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
        578:             unchecked {
        579:                 ++i;
        580:             }
        581:         }
        
        ```
        
        [575](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L575-L581)
        
        ```solidity
        📁 File: contracts/libraries/FeesCalc.sol
        
        /// @audit positionIdList.length not bounded
        51:         for (uint256 k = 0; k < positionIdList.length; ) {
        52:             TokenId tokenId = positionIdList[k];
        53:             uint128 positionSize = userBalance[tokenId].rightSlot();
        54:             uint256 numLegs = tokenId.countLegs();
        55:             for (uint256 leg = 0; leg < numLegs; ) {
        56:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
        57:                     tokenId,
        58:                     leg,
        59:                     positionSize
        60:                 );
        61:
        62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
        63:                     atTick,
        64:                     liquidityChunk
        65:                 );
        66:
        67:                 if (tokenId.isLong(leg) == 0) {
        68:                     unchecked {
        69:                         value0 += int256(amount0);
        70:                         value1 += int256(amount1);
        71:                     }
        72:                 } else {
        73:                     unchecked {
        74:                         value0 -= int256(amount0);
        75:                         value1 -= int256(amount1);
        76:                     }
        77:                 }
        78:
        79:                 unchecked {
        80:                     ++leg;
        81:                 }
        82:             }
        83:             unchecked {
        84:                 ++k;
        85:             }
        86:         }
        
        ```
        
        [51](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L51-L86)
        
        ```solidity
        📁 File: contracts/libraries/PanopticMath.sol
        
        /// @audit positionIdList.length not bounded
        781:             for (uint256 i = 0; i < positionIdList.length; ++i) {
        782:                 TokenId tokenId = positionIdList[i];
        783:                 uint256 numLegs = tokenId.countLegs();
        784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {
        785:                     if (tokenId.isLong(leg) == 1) {
        786:                         longPremium = longPremium.sub(premiasByLeg[i][leg]);
        787:                     }
        788:                 }
        789:             }
        
        /// @audit positionIdList.length not bounded
        860:             for (uint256 i = 0; i < positionIdList.length; i++) {
        861:                 TokenId tokenId = positionIdList[i];
        862:                 LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
        863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
        864:                     if (tokenId.isLong(leg) == 1) {
        865:                         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
        866:                             storage _settledTokens = settledTokens;
        867:
        868:                         // calculate amounts to revoke from settled and subtract from haircut req
        869:                         uint256 settled0 = Math.unsafeDivRoundingUp(
        870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
        871:                             uint128(longPremium.rightSlot())
        872:                         );
        873:                         uint256 settled1 = Math.unsafeDivRoundingUp(
        874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
        875:                             uint128(longPremium.leftSlot())
        876:                         );
        877:
        878:                         bytes32 chunkKey = keccak256(
        879:                             abi.encodePacked(
        880:                                 tokenId.strike(0),
        881:                                 tokenId.width(0),
        882:                                 tokenId.tokenType(0)
        883:                             )
        884:                         );
        885:
        886:                         // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
        887:                         // for the haircut directly to the accumulator
        888:                         settled0 = Math.max(
        889:                             0,
        890:                             uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
        891:                         );
        892:                         settled1 = Math.max(
        893:                             0,
        894:                             uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
        895:                         );
        896:
        897:                         _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
        898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
        899:                                 uint128(settled1)
        900:                             )
        901:                         );
        902:                     }
        903:                 }
        904:             }
        
        ```
        
        [781](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L781-L789), [860](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L860-L904)
        
        ```solidity
        📁 File: contracts/tokens/ERC1155Minimal.sol
        
        /// @audit ids.length not bounded
        143:         for (uint256 i = 0; i < ids.length; ) {
        144:             id = ids[i];
        145:             amount = amounts[i];
        146:
        147:             balanceOf[from][id] -= amount;
        148:
        149:             // balance will never overflow
        150:             unchecked {
        151:                 balanceOf[to][id] += amount;
        152:             }
        153:
        154:             // An array can't have a total length
        155:             // larger than the max uint256 value.
        156:             unchecked {
        157:                 ++i;
        158:             }
        159:         }
        
        187:             for (uint256 i = 0; i < owners.length; ++i) {
        188:                 balances[i] = balanceOf[owners[i]][ids[i]];
        189:             }
        
        ```
        
        [143](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L143-L159), [187](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L187-L189)
        
    4. Contracts use infinite approvals with no means to revoke
    Infinite approvals on external contracts can be dangerous if the target becomes compromised. See [here](https://revoke.cash/exploits) for a list of approval exploits.  The following contracts are vulnerable to such attacks since they have no functionality to revoke the approval (call `approve` with amount `0`). Consider enabling the contract to revoke approval in emergency situations.
        
        ```solidity
        📁 File: contracts/libraries/InteractionHelper.sol
        
        32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
        33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
        
        36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
        37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
        
        ```
        
        [32](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L32-L33), [36](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L36-L37)
        
    5. `decimals()` is not a part of the ERC-20 standard
    The `decimals()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.
        
        ```solidity
        📁 File: contracts/libraries/InteractionHelper.sol
        
        110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {
        
        ```
        
        [110](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L110)
        
    6. External calls in an un-bounded `for`loop may result in a DOS
        
        Consider limiting the number of iterations in `for`-loops that make external calls
        
        ```solidity
        📁 File: contracts/PanopticPool.sol
        
        /// @audit line 751
        745:         for (uint256 leg = 0; leg < numLegs; ) {
        746:             // Extract base fee (AMM swap/trading fees) for the position and add it to s_options
        747:             // (ie. the (feeGrowth * liquidity) / 2**128 for each token)
        748:             (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
        749:             uint256 isLong = tokenId.isLong(leg);
        750:             {
        751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
        752:                     address(s_univ3pool),
        753:                     address(this),
        754:                     tokenId.tokenType(leg),
        755:                     tickLower,
        756:                     tickUpper,
        757:                     type(int24).max,
        758:                     isLong
        759:                 );
        760:
        761:                 // update the premium accumulators
        762:                 s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
        763:                     .wrap(0)
        764:                     .toRightSlot(premiumAccumulator0)
        765:                     .toLeftSlot(premiumAccumulator1);
        766:             }
        767:             // verify base Liquidity limit only if new position is long
        768:             if (isLong == 1) {
        769:                 // Move this into a new function
        770:                 _checkLiquiditySpread(
        771:                     tokenId,
        772:                     leg,
        773:                     tickLower,
        774:                     tickUpper,
        775:                     uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))
        776:                 );
        777:             }
        778:             unchecked {
        779:                 ++leg;
        780:             }
        781:         }
        
        /// @audit line 1528
        1518:         for (uint256 leg = 0; leg < numLegs; ) {
        1519:             uint256 isLong = tokenId.isLong(leg);
        1520:             if ((isLong == 1) || computeAllPremia) {
        1521:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
        1522:                     tokenId,
        1523:                     leg,
        1524:                     positionSize
        1525:                 );
        1526:                 uint256 tokenType = tokenId.tokenType(leg);
        1527:
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
        1538:
        1539:                 unchecked {
        1540:                     LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];
        1541:
        1542:                     // if the premium accumulatorLast is higher than current, it means the premium accumulator has overflowed and rolled over at least once
        1543:                     // we can account for one rollover by doing (acc_cur + (acc_max - acc_last))
        1544:                     // if there are multiple rollovers or the rollover goes past the last accumulator, rolled over fees will just remain unclaimed
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
        1565:
        1566:                     if (isLong == 1) {
        1567:                         premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);
        1568:                     }
        1569:                 }
        1570:             }
        1571:             unchecked {
        1572:                 ++leg;
        1573:             }
        1574:         }
        
        /// @audit line 1707
        1672:         for (uint256 leg = 0; leg < numLegs; ++leg) {
        1673:             bytes32 chunkKey = keccak256(
        1674:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
        1675:             );
        1676:             // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers
        1677:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
        1678:
        1679:             if (tokenId.isLong(leg) == 0) {
        1680:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
        1681:                     tokenId,
        1682:                     leg,
        1683:                     positionSize
        1684:                 );
        1685:
        1686:                 // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (R + N)
        1687:                 uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
        1688:
        1689:                 // We need to adjust the grossPremiumLast value such that the result of
        1690:                 // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64
        1691:                 // G: total gross premium
        1692:                 // T: totalLiquidityBeforeMint
        1693:                 // R: positionLiquidity
        1694:                 // C: current grossPremium value
        1695:                 // L: current grossPremiumLast value
        1696:                 // Ln: updated grossPremiumLast value
        1697:                 // T * (C - L) = G
        1698:                 // (T + R) * (C - Ln) = G
        1699:                 //
        1700:                 // T * (C - L) = (T + R) * (C - Ln)
        1701:                 // (TC - TL) / (T + R) = C - Ln
        1702:                 // Ln = C - (TC - TL)/(T + R)
        1703:                 // Ln = (CT + CR - TC + TL)/(T+R)
        1704:                 // Ln = (CR + TL)/(T+R)
        1705:
        1706:                 uint256[2] memory grossCurrent;
        1707:                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
        1708:                     address(s_univ3pool),
        1709:                     address(this),
        1710:                     tokenId.tokenType(leg),
        1711:                     liquidityChunk.tickLower(),
        1712:                     liquidityChunk.tickUpper(),
        1713:                     type(int24).max,
        1714:                     0
        1715:                 );
        1716:
        1717:                 unchecked {
        1718:                     // L
        1719:                     LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
        1720:                     // R
        1721:                     uint256 positionLiquidity = liquidityChunk.liquidity();
        1722:                     // T (totalLiquidity is (T + R) after minting)
        1723:                     uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
        1724:
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
        1743:                 }
        1744:             }
        1745:         }
        
        ```
        
        [745](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L745-L781), [1518](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1518-L1574), [1672](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1672-L1745)
        
        ```solidity
        📁 File: contracts/libraries/PanopticMath.sol
        
        /// @audit line 138
        137:             for (uint256 i = 0; i < cardinality + 1; ++i) {
        138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
        139:                     uint256(
        140:                         (int256(observationIndex) - int256(i * period)) +
        141:                             int256(observationCardinality)
        142:                     ) % observationCardinality
        143:                 );
        144:             }
        
        ```
        
        [137](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L137-L144)
        
    7. File allows a version of solidity that is susceptible to `.selector`related optimizer bug
        
        In solidity versions prior to 0.8.21, there is a legacy code generation [bug](https://soliditylang.org/blog/2023/07/19/missing-side-effects-on-selector-access-bug/) where if `foo().selector` is called, `foo()` doesn't actually get evaluated. It is listed as low-severity, because projects usually use the contract name rather than a function call to look up the selector. I've flagged all files using `.selector` where the version is vulnerable.
        
        ```solidity
        📁 File: contracts/tokens/ERC1155Minimal.sol
        
        2: pragma solidity ^0.8.0;
        
        ```
        
        [2](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L2)
        
    8. File allows a version of solidity that is susceptible to an assembly optimizer bug
        
        In solidity versions 0.8.13 and 0.8.14, there is an [optimizer bug](https://github.com/ethereum/solidity-blog/blob/499ab8abc19391be7b7b34f88953a067029a5b45/_posts/2022-06-15-inline-assembly-memory-side-effects-bug.md) where, if the use of a variable is in a separate `assembly` block from the block in which it was stored, the `mstore` operation is optimized out, leading to uninitialized memory. The code currently does not have such a pattern of execution, but it does use `mstore`s in `assembly` blocks, so it is a risk for future changes. The affected solidity versions should be avoided if at all possible.
        
        ```solidity
        📁 File: contracts/libraries/SafeTransferLib.sol
        
        /// @audit mstore on line: 29, 30, 31, 32
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
        
        /// @audit mstore on line: 60, 61, 62
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
        
        [24](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L24-L43), [55](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L55-L73)
        
    9. Input array lengths may differ
    If the caller makes a copy-paste error, the lengths may be mismatched and an operation believed to have been completed may not in fact have been completed (e.g. if the array being iterated over is shorter than the one being indexed into).
        
        ```solidity
        📁 File: contracts/SemiFungiblePositionManager.sol
        
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
        /// @audit amounts's length could be different from ids's length
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
        
        [566](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566-L585)
        
        ```solidity
        📁 File: contracts/libraries/PanopticMath.sol
        
        768:     function haircutPremia(
        769:         address liquidatee,
        770:         TokenId[] memory positionIdList,
        771:         LeftRightSigned[4][] memory premiasByLeg,
        772:         LeftRightSigned collateralRemaining,
        773:         CollateralTracker collateral0,
        774:         CollateralTracker collateral1,
        775:         uint160 sqrtPriceX96Final,
        776:         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
        777:     ) external returns (int256, int256) {
        778:         unchecked {
        779:             // get the amount of premium paid by the liquidatee
        780:             LeftRightSigned longPremium;
        781:             for (uint256 i = 0; i < positionIdList.length; ++i) {
        782:                 TokenId tokenId = positionIdList[i];
        783:                 uint256 numLegs = tokenId.countLegs();
        784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {
        785:                     if (tokenId.isLong(leg) == 1) {
        /// @audit premiasByLeg's length could be different from positionIdList's length
        786:                         longPremium = longPremium.sub(premiasByLeg[i][leg]);
        787:                     }
        788:                 }
        789:             }
        790:             // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token
        791:             int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);
        792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);
        793:             int256 haircut0;
        794:             int256 haircut1;
        795:             // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,
        796:             // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token
        797:             if (
        798:                 longPremium.rightSlot() < collateralDelta0 &&
        799:                 longPremium.leftSlot() > collateralDelta1
        800:             ) {
        801:                 int256 protocolLoss1 = collateralDelta1;
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
        818:
        819:                 haircut0 = longPremium.rightSlot();
        820:                 haircut1 = protocolLoss1 + collateralDelta1;
        821:             } else if (
        822:                 longPremium.leftSlot() < collateralDelta1 &&
        823:                 longPremium.rightSlot() > collateralDelta0
        824:             ) {
        825:                 int256 protocolLoss0 = collateralDelta0;
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
        842:
        843:                 haircut0 = collateralDelta0 + protocolLoss0;
        844:                 haircut1 = longPremium.leftSlot();
        845:             } else {
        846:                 // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
        847:                 haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
        848:                 haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
        849:
        850:                 collateralDelta0 = 0;
        851:                 collateralDelta1 = 0;
        852:             }
        853:
        854:             {
        855:                 address _liquidatee = liquidatee;
        856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
        857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
        858:             }
        859:
        860:             for (uint256 i = 0; i < positionIdList.length; i++) {
        861:                 TokenId tokenId = positionIdList[i];
        862:                 LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
        863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
        864:                     if (tokenId.isLong(leg) == 1) {
        865:                         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
        866:                             storage _settledTokens = settledTokens;
        867:
        868:                         // calculate amounts to revoke from settled and subtract from haircut req
        869:                         uint256 settled0 = Math.unsafeDivRoundingUp(
        870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
        871:                             uint128(longPremium.rightSlot())
        872:                         );
        873:                         uint256 settled1 = Math.unsafeDivRoundingUp(
        874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
        875:                             uint128(longPremium.leftSlot())
        876:                         );
        877:
        878:                         bytes32 chunkKey = keccak256(
        879:                             abi.encodePacked(
        880:                                 tokenId.strike(0),
        881:                                 tokenId.width(0),
        882:                                 tokenId.tokenType(0)
        883:                             )
        884:                         );
        885:
        886:                         // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
        887:                         // for the haircut directly to the accumulator
        888:                         settled0 = Math.max(
        889:                             0,
        890:                             uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
        891:                         );
        892:                         settled1 = Math.max(
        893:                             0,
        894:                             uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
        895:                         );
        896:
        897:                         _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
        898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
        899:                                 uint128(settled1)
        900:                             )
        901:                         );
        902:                     }
        903:                 }
        904:             }
        905:
        906:             return (collateralDelta0, collateralDelta1);
        907:         }
        908:     }
        
        ```
        
        [768](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)
        
        ```solidity
        📁 File: contracts/tokens/ERC1155Minimal.sol
        
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
        140:         uint256 id;
        141:         uint256 amount;
        142:
        143:         for (uint256 i = 0; i < ids.length; ) {
        144:             id = ids[i];
        /// @audit amounts's length could be different from ids's length
        145:             amount = amounts[i];
        146:
        147:             balanceOf[from][id] -= amount;
        148:
        149:             // balance will never overflow
        150:             unchecked {
        151:                 balanceOf[to][id] += amount;
        152:             }
        153:
        154:             // An array can't have a total length
        155:             // larger than the max uint256 value.
        156:             unchecked {
        157:                 ++i;
        158:             }
        159:         }
        160:
        161:         emit TransferBatch(msg.sender, from, to, ids, amounts);
        162:
        163:         if (to.code.length != 0) {
        164:             if (
        165:                 ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
        166:                 ERC1155Holder.onERC1155BatchReceived.selector
        167:             ) {
        168:                 revert UnsafeRecipient();
        169:             }
        170:         }
        171:     }
        
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
        /// @audit ids's length could be different from owners's length
        188:                 balances[i] = balanceOf[owners[i]][ids[i]];
        189:             }
        190:         }
        191:     }
        
        ```
        
        [130](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L130-L171), [178](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L178-L191)
        
    10. Int casting `block.timestamp` can reduce the lifespan of a contract
        
        ```solidity
        📁 File: contracts/PanopticPool.sol
        
        309:                 (uint256(block.timestamp) << 216) +
        
        ```
        
        [309](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L309)
        
    11. Missing contract-existence checks before yul `call()`
    Low-level calls return success if there is no code present at the specified address. In addition to the zero-address checks, add a check to verify that `extcodesize()` is non-zero.
        
        ```solidity
        📁 File: contracts/libraries/SafeTransferLib.sol
        
        /// @audit call() on line 41
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
        
        /// @audit call() on line 71
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
        
        [24](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L24-L43), [55](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L55-L73)
        
    12. Some tokens do not consider `type(uint256).max` as an infinite approval
    Some tokens such as [COMP](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L89-L91) downcast such approvals to uint96 and use that as a raw value rather than interpreting it as an infinite approval. Eventually these approvals will reach zero, at which point the calling contract will no longer function properly.
        
        ```solidity
        📁 File: contracts/libraries/InteractionHelper.sol
        
        32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
        33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
        
        36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
        37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
        
        ```
        
        [32](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L32-L33), [36](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L36-L37)
        
    13. Some tokens may revert when zero value transfers are made
    In spite of the fact that EIP-20 [states](https://github.com/ethereum/EIPs/blob/46b9b698815abbfa628cd1097311deee77dd45c5/EIPS/eip-20.md?plain=1#L116) that zero-valued transfers must be accepted, some tokens, such as `LEND` will revert if this is attempted, which may cause transactions that involve other tokens (such as batch operations) to fully revert. Consider skipping the transfer if the amount is zero, which will also save **gas**.
        
        ```solidity
        📁 File: contracts/CollateralTracker.sol
        
        333:         return ERC20Minimal.transfer(recipient, amount);
        
        352:         return ERC20Minimal.transferFrom(from, to, amount);
        
        616:         SafeTransferLib.safeTransferFrom(
        617:             s_underlyingToken,
        618:             address(s_panopticPool),
        619:             receiver,
        620:             assets
        621:         );
        
        ```
        
        [333](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L333), [352](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L352), [616](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L616-L621)
        
        ```solidity
        📁 File: contracts/SemiFungiblePositionManager.sol
        
        456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);
        
        555:         super.safeTransferFrom(from, to, id, amount, data);
        
        ```
        
        [456](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L456), [555](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L555)
        
    14. Consider adding minimum/maximum value checks to ensure that the state variables below can never be used to excessively harm users, including via griefing
        
        ```solidity
        📁 File: contracts/CollateralTracker.sol
        
        /// @audit s_panopticPool on line 244
        /// @audit s_univ3token0 on line 254
        /// @audit s_univ3token1 on line 255
        221:     function startToken(
        222:         bool underlyingIsToken0,
        223:         address token0,
        224:         address token1,
        225:         uint24 fee,
        226:         PanopticPool panopticPool
        227:     ) external {
        228:         // fails if already initialized
        229:         if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();
        230:         s_initialized = true;
        231:
        232:         // these virtual shares function as a multiplier for the capital requirement to manipulate the pool price
        233:         // e.g if the virtual shares are 10**6, then the capital requirement to manipulate the price to 10**12 is 10**18
        234:         totalSupply = 10 ** 6;
        235:
        236:         // set total assets to 1
        237:         // the initial share price is defined by 1/virtualShares
        238:         s_poolAssets = 1;
        239:
        240:         // store the address of the underlying ERC20 token
        241:         s_underlyingToken = underlyingIsToken0 ? token0 : token1;
        242:
        243:         // store the Panoptic pool for this collateral token
        244:         s_panopticPool = panopticPool;
        245:
        246:         // cache the pool fee in basis points
        247:         uint24 _poolFee;
        248:         unchecked {
        249:             _poolFee = fee / 100;
        250:         }
        251:         s_poolFee = _poolFee;
        252:
        253:         // Stores the addresses of the underlying tracked tokens.
        254:         s_univ3token0 = token0;
        255:         s_univ3token1 = token1;
        256:
        257:         // store whether the current collateral token is token0 (true) or token1 (false; since there's always exactly two tokens it could be)
        258:         s_underlyingIsToken0 = underlyingIsToken0;
        259:
        260:         // Additional risk premium charged on intrinsic value of ITM positions
        261:         unchecked {
        262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);
        263:         }
        264:     }
        
        ```
        
        [221](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L221-L264)
        
        ```solidity
        📁 File: contracts/tokens/ERC20Minimal.sol
        
        /// @audit totalSupply on line 128
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
        
        /// @audit totalSupply on line 142
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
        
        [122](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L122-L131), [136](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L136-L146)
        
    15. `symbol()` is not a part of the ERC-20 standard
        
        The `symbol()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.
        
        ```solidity
        📁 File: contracts/libraries/InteractionHelper.sol
        
        60:         try IERC20Metadata(token0).symbol() returns (string memory _symbol) {
        
        65:         try IERC20Metadata(token1).symbol() returns (string memory _symbol) {
        
        97:         try IERC20Metadata(token).symbol() returns (string memory tokenSymbol) {
        
        ```
        
        [60](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L60), [65](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L65), [97](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L97)