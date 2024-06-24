---
sponsor: "Panoptic"
slug: "2024-04-panoptic"
date: "2024-06-24"
title: "Panoptic"
findings: "https://github.com/code-423n4/2024-04-panoptic-findings/issues"
contest: 354
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the Panoptic smart contract system written in Solidity. The audit took place between April 1—April 22 2024.

## Wardens

60 Wardens contributed reports to Panoptic:

  1. [0xLogos](https://code4rena.com/@0xLogos)
  2. [bin2chen](https://code4rena.com/@bin2chen)
  3. [KupiaSec](https://code4rena.com/@KupiaSec)
  4. [rbserver](https://code4rena.com/@rbserver)
  5. [Kalogerone](https://code4rena.com/@Kalogerone)
  6. [0xdice91](https://code4rena.com/@0xdice91)
  7. [pkqs90](https://code4rena.com/@pkqs90)
  8. [petro\_1912](https://code4rena.com/@petro_1912)
  9. [Aymen0909](https://code4rena.com/@Aymen0909)
  10. [0xStalin](https://code4rena.com/@0xStalin)
  11. [DanielArmstrong](https://code4rena.com/@DanielArmstrong)
  12. [Joshuajee](https://code4rena.com/@Joshuajee)
  13. [JecikPo](https://code4rena.com/@JecikPo)
  14. [Udsen](https://code4rena.com/@Udsen)
  15. [FastChecker](https://code4rena.com/@FastChecker)
  16. [DadeKuma](https://code4rena.com/@DadeKuma)
  17. [Dup1337](https://code4rena.com/@Dup1337) ([ChaseTheLight](https://code4rena.com/@ChaseTheLight), [sorrynotsorry](https://code4rena.com/@sorrynotsorry), and [deliriusz](https://code4rena.com/@deliriusz))
  18. [Bauchibred](https://code4rena.com/@Bauchibred)
  19. [sammy](https://code4rena.com/@sammy)
  20. [jesjupyter](https://code4rena.com/@jesjupyter)
  21. [99Crits](https://code4rena.com/@99Crits)
  22. [favelanky](https://code4rena.com/@favelanky)
  23. [cheatc0d3](https://code4rena.com/@cheatc0d3)
  24. [slvDev](https://code4rena.com/@slvDev)
  25. [bareli](https://code4rena.com/@bareli)
  26. [Rolezn](https://code4rena.com/@Rolezn)
  27. [hihen](https://code4rena.com/@hihen)
  28. [ZanyBonzy](https://code4rena.com/@ZanyBonzy)
  29. [albahaca](https://code4rena.com/@albahaca)
  30. [radin100](https://code4rena.com/@radin100)
  31. [Naresh](https://code4rena.com/@Naresh)
  32. [Vancelot](https://code4rena.com/@Vancelot)
  33. [grearlake](https://code4rena.com/@grearlake)
  34. [d3e4](https://code4rena.com/@d3e4)
  35. [zabihullahazadzoi](https://code4rena.com/@zabihullahazadzoi)
  36. [John\_Femi](https://code4rena.com/@John_Femi)
  37. [lanrebayode77](https://code4rena.com/@lanrebayode77)
  38. [jasonxiale](https://code4rena.com/@jasonxiale)
  39. [satoshispeedrunner](https://code4rena.com/@satoshispeedrunner)
  40. [CodeWasp](https://code4rena.com/@CodeWasp) ([slylandro\_star](https://code4rena.com/@slylandro_star), [kuprum](https://code4rena.com/@kuprum), [audithare](https://code4rena.com/@audithare), and [spaghetticode\_sentinel](https://code4rena.com/@spaghetticode_sentinel))
  41. [pfapostol](https://code4rena.com/@pfapostol)
  42. [Rhaydden](https://code4rena.com/@Rhaydden)
  43. [blockchainbuttonmasher](https://code4rena.com/@blockchainbuttonmasher)
  44. [mining\_mario](https://code4rena.com/@mining_mario)
  45. [twcctop](https://code4rena.com/@twcctop)
  46. [0xhacksmithh](https://code4rena.com/@0xhacksmithh)
  47. [K42](https://code4rena.com/@K42)
  48. [Topmark](https://code4rena.com/@Topmark)
  49. [lsaudit](https://code4rena.com/@lsaudit)
  50. [lirezArAzAvi](https://code4rena.com/@lirezArAzAvi)
  51. [crc32](https://code4rena.com/@crc32)
  52. [codeslide](https://code4rena.com/@codeslide)
  53. [oualidpro](https://code4rena.com/@oualidpro)
  54. [Sathish9098](https://code4rena.com/@Sathish9098)
  55. [IllIllI](https://code4rena.com/@IllIllI)

This audit was judged by [Picodes](https://twitter.com/judge).

Final report assembled by [liveactionllama](https://code4rena.com/@Picodes).

# Summary

The C4 analysis yielded an aggregated total of 11 unique vulnerabilities. Of these vulnerabilities, 2 received a risk rating in the category of HIGH severity and 9 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 43 reports detailing issues with a risk rating of LOW severity or non-critical.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 Panoptic repository](https://github.com/code-423n4/2024-04-panoptic), and is composed of 2 interfaces and 18 smart contracts written in the Solidity programming language and includes 4,921 lines of Solidity code.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (2)
## [[H-01] `SettleLongPremium` is incorrectly implemented: premium should be deducted instead of added](https://github.com/code-423n4/2024-04-panoptic-findings/issues/497)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-panoptic-findings/issues/497), also found by [bin2chen](https://github.com/code-423n4/2024-04-panoptic-findings/issues/461), [Aymen0909](https://github.com/code-423n4/2024-04-panoptic-findings/issues/376), [0xStalin](https://github.com/code-423n4/2024-04-panoptic-findings/issues/340), [JecikPo](https://github.com/code-423n4/2024-04-panoptic-findings/issues/335), and [DanielArmstrong](https://github.com/code-423n4/2024-04-panoptic-findings/issues/98)*

<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1621-L1640><br>
<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043-L1089>

`SettleLongPremium` is the function intended to settle premiums for long option holders. When called, it should deduct the premium from the option owner's account, but the current implementation adds the premium instead.

### Bug Description

Let's see the code for premium calculation. We can see that `accumulatedPremium` and `s_options[owner][tokenId][legIndex]` are premium accumulators for calculating the owed amount of premium, and that `accumulatedPremium` is a LeftRightUnsigned type, which means it must be positive.

The `realizedPremia` is also positive, because it is calculated by `accumulatedPremium * liquidity`.

The issue occurs when calling `s_collateralToken.exercise()`. The `realizedPremia` that is passed inside should be negative instead of positive, because negative means user pays premia, and positive means user receives premia. The current implementation is incorrect.

PanopticPool.sol

```solidity
            accumulatedPremium = LeftRightUnsigned
                .wrap(0)
                .toRightSlot(premiumAccumulator0)
                .toLeftSlot(premiumAccumulator1);

            // update the premium accumulator for the long position to the latest value
            // (the entire premia delta will be settled)
            LeftRightUnsigned premiumAccumulatorsLast = s_options[owner][tokenId][legIndex];
            s_options[owner][tokenId][legIndex] = accumulatedPremium;

>           accumulatedPremium = accumulatedPremium.sub(premiumAccumulatorsLast);
        }

        uint256 liquidity = PanopticMath
            .getLiquidityChunk(tokenId, legIndex, s_positionBalance[owner][tokenId].rightSlot())
            .liquidity();

        unchecked {
            // update the realized premia
>           LeftRightSigned realizedPremia = LeftRightSigned
>               .wrap(0)
>               .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))
>               .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));

            // deduct the paid premium tokens from the owner's balance and add them to the cumulative settled token delta
            s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());
            s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());
```

CollateralTracker.sol

```solidity
   function exercise(
        address optionOwner,
        int128 longAmount,
        int128 shortAmount,
        int128 swappedAmount,
        int128 realizedPremium
    ) external onlyPanopticPool returns (int128) {
        unchecked {
            // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
            int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

            // add premium to be paid/collected on position close
>           int256 tokenToPay = -realizedPremium;

            // if burning ITM and swap occurred, compute tokens to be paid through exercise and add swap fees
            int256 intrinsicValue = swappedAmount - (longAmount - shortAmount);

            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {
                // intrinsic value is the amount that need to be exchanged due to burning in-the-money

                // add the intrinsic value to the tokenToPay
                tokenToPay += intrinsicValue;
            }

>           if (tokenToPay > 0) {
                // if user must pay tokens, burn them from user balance (revert if balance too small)
                uint256 sharesToBurn = Math.mulDivRoundingUp(
                    uint256(tokenToPay),
                    totalSupply,
                    totalAssets()
                );
                _burn(optionOwner, sharesToBurn);
>           } else if (tokenToPay < 0) {
                // if user must receive tokens, mint them
                uint256 sharesToMint = convertToShares(uint256(-tokenToPay));
                _mint(optionOwner, sharesToMint);
            }
```

### Proof of Concept

We can also see from unit test `test_success_settleLongPremium`: The tests checks that after calling `settleLongPremium`, the assets of `Buyer[0]` actually increases instead of decreases, which is obviously incorrect.

```solidity
        assetsBefore0 = ct0.convertToAssets(ct0.balanceOf(Buyers[0]));
        assetsBefore1 = ct1.convertToAssets(ct1.balanceOf(Buyers[0]));

        // collect buyer 1's three relevant chunks
        for (uint256 i = 0; i < 3; ++i) {
            pp.settleLongPremium(collateralIdLists[i], Buyers[0], 0);
        }

        assertEq(
            ct0.convertToAssets(ct0.balanceOf(Buyers[0])) - assetsBefore0,
            33_342,
            "Incorrect Buyer 1 1st Collect 0"
        );
```

### Recommended Mitigation Steps

Take the negative of `realizedPremia` before calling `s_collateralToken.exercise()`.

**[dyedm1 (Panoptic) confirmed via duplicate issue \#376](https://github.com/code-423n4/2024-04-panoptic-findings/issues/376#event-12628843435)**

**[Picodes (judge) commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/497#issuecomment-2096436946):**
 > Keeping High severity as funds are at stake.



***

## [[H-02] Overflow in `CollateralTracker` allows minting shares for free](https://github.com/code-423n4/2024-04-panoptic-findings/issues/438)
*Submitted by [0xLogos](https://github.com/code-423n4/2024-04-panoptic-findings/issues/438)*

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L478>

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L461-L467>

### Impact

Malicious actors can mint huge amounts of shares for free and then withdraw all collateral.

### Proof of Concept

In the `mint` function user-controlled `shares` parameter goes right away to the `previewMint` function which then calculates required assets in unchecked block. If the `shares` value is high enough, overflow in `shares * DECIMALS` will occur, and `assets` will be very low.

    function previewMint(uint shares) public view returns (uint assets) {
     unchecked {
     assets = Math.mulDivRoundingUp(
     shares * DECIMALS, totalAssets(), totalSupply * (DECIMALS - COMMISSION_FEE)
     );
     }
    }

    function mint(uint shares, address receiver) external returns (uint assets) {
     assets = previewMint(shares);
     if (assets > type(uint104).max) revert Errors.DepositTooLarge();
     ...
    }

Insert the following snippet to ColalteralTracker.t.sol for coded PoC:

    function test_poc1(uint256 x) public {
     _initWorld(x);
     _grantTokens(Bob);

     vm.startPrank(Bob);

     uint shares = type(uint).max / 10000 + 1;
     IERC20Partial(token0).approve(address(collateralToken0), type(uint256).max);
     uint256 returnedAssets0 = collateralToken0.mint(shares, Bob);

     assertEq(shares, collateralToken0.balanceOf(Bob));
     assertEq(returnedAssets0, 1);
    }

### Recommended Mitigation Steps

Remove unchecked block.

    function maxMint(address) external view returns (uint maxShares) {
     return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
    }

### Assessed type

Under/Overflow

**[dyedm1 (Panoptic) confirmed](https://github.com/code-423n4/2024-04-panoptic-findings/issues/438#event-12628628301)**



***

 
# Medium Risk Findings (9)
## [[M-01] `PanopticFactory` uses spot price when deploying new pools, resulting in liquidity manipulation when minting](https://github.com/code-423n4/2024-04-panoptic-findings/issues/537)
*Submitted by [DadeKuma](https://github.com/code-423n4/2024-04-panoptic-findings/issues/537), also found by [sammy](https://github.com/code-423n4/2024-04-panoptic-findings/issues/547), [Dup1337](https://github.com/code-423n4/2024-04-panoptic-findings/issues/486), [Bauchibred](https://github.com/code-423n4/2024-04-panoptic-findings/issues/351), [jesjupyter](https://github.com/code-423n4/2024-04-panoptic-findings/issues/204), and [Vancelot](https://github.com/code-423n4/2024-04-panoptic-findings/issues/30)*

When `deployNewPool` is called it uses the spot price of the pool, which can be manipulated through a flashloan and thus could return a highly inaccurate result.

The price is used when deciding how much liquidity should be minted for each token, so this can result in an unbalanced pool.

In other parts of the code, this is not an issue as there are oracles that prevent price manipulations, but in case there aren't any checks to avoid so.

### Proof of Concept

The spot price is used to calculate the range liquidity for each token:

```solidity
@>	(uint160 currentSqrtPriceX96, , , , , , ) = v3Pool.slot0();

	// For full range: L = Δx * sqrt(P) = Δy / sqrt(P)
	// We start with fixed token amounts and apply this equation to calculate the liquidity
	// Note that for pools with a tickSpacing that is not a power of 2 or greater than 8 (887272 % ts != 0),
	// a position at the maximum and minimum allowable ticks will be wide, but not necessarily full-range.
	// In this case, the `fullRangeLiquidity` will always be an underestimate in respect to the token amounts required to mint.
	uint128 fullRangeLiquidity;
	unchecked {
	    // Since we know one of the tokens is WETH, we simply add 0.1 ETH + worth in tokens
	    if (token0 == WETH) {
	        fullRangeLiquidity = uint128(
@>	            Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)
	        );
	    } else if (token1 == WETH) {
	        fullRangeLiquidity = uint128(
	            Math.mulDivRoundingUp(
	                FULL_RANGE_LIQUIDITY_AMOUNT_WETH,
	                Constants.FP96,
@>	                currentSqrtPriceX96
	            )
	        );
	    } else {
	        // Find the resulting liquidity for providing 1e6 of both tokens
	        uint128 liquidity0 = uint128(
@>	            Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)
	        );
	        uint128 liquidity1 = uint128(
	            Math.mulDivRoundingUp(
	                FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,
	                Constants.FP96,
@>	                currentSqrtPriceX96
	            )
	        );

	        // Pick the greater of the liquidities - i.e the more "expensive" option
	        // This ensures that the liquidity added is sufficiently large
	        fullRangeLiquidity = liquidity0 > liquidity1 ? liquidity0 : liquidity1;
	    }
	}
```

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L341-L374>

But unlike other parts of the code, the `PanopticFactory` doesn't have any checks against the price (it doesn't use any oracles nor the TWAP), so each token liquidity is manipulable through flash loans.

### Recommended Mitigation Steps

Consider using the TWAP price instead of the spot price.

### Assessed type

Uniswap

**[dyedm1 (Panoptic) disputed and commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/537#issuecomment-2080029411):**
 > True, but I don't see negative consequences for this? This function is just a way to add *some* full-range liquidity to the pool so the entire range can be swapped across, and depending on the tokens we can add very small/large amounts of liquidity anyway (mentioned in the readme: Depending on the token, the amount of funds required for the initial factory deployment may be high or unrealistic)

**[Picodes (judge) commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/537#issuecomment-2088281565):**
 > @dyedm1 - assuming the deployer has infinite approvals, can't we imagine a scenario where, by manipulating the spot pool price, it ends up depositing way too many token1 and getting sandwiched leading to a significant loss? 
> 
> Said differently, the risk is that currently the deployer has no control over the amount of token1 he will donate and this amount can be manipulated by an attacker.

**[Picodes (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/537#issuecomment-2088282706):**
 > This is at most Medium to me considering pool deployers are advanced users and you need to deploy a pool where the manipulation cost is low which should remain exceptional.

**[dyedm1 (Panoptic) commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/537#issuecomment-2096799229):**
 > Yeah I agree this might be less than ideal if you have infinite approvals. Our UI doesn't do infinite approvals to the factory, but some wallets allow users to edit the approval amount before signing the transaction, so it might be prudent to add slippage checks here (to make the process idiot-proof).



***

## [[M-02] `_validatePositionList()` does not check for duplicate tokenIds, allowing attackers to bypass solvency checks](https://github.com/code-423n4/2024-04-panoptic-findings/issues/498)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-panoptic-findings/issues/498), also found by [Udsen](https://github.com/code-423n4/2024-04-panoptic-findings/issues/496), [0xLogos](https://github.com/code-423n4/2024-04-panoptic-findings/issues/465), and [bin2chen](https://github.com/code-423n4/2024-04-panoptic-findings/issues/463)*

<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1367-L1391>

<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L887-L893>

### Impact

The underlying issue is that `_validatePositionList()` does not check for duplicate tokenIds. Attackers can use this issue to bypass solvency checks, which leads to several impacts:

1.  Users can mint/burn/liquidate/forceExercise when they are insolvent.
2.  Users can settleLongPremium/forceExercise another user when the other user is insolvent.

This also conflicts a main invariant stated in audit readme: `Users should not be allowed to mint/burn options or pay premium if their end state is insolvent`.

### Bug Description

First, let's see why `_validatePositionList` does not check for duplicate tokenIds. For a user position hash, the first 8 bits is the length of tokenIds which overflows, last 248 bits is the xor hash. However, we can easily add 256 tokenIds of the same kind to create a duplicate positionHash.

For example: `Hash(key0, key1, key2) == Hash(key0, key1, key2, key0, key0, ..., 256 more key0)`. This way, we can add any tokenId we want while still arriving the same position hash.

PanopticPool.sol

```solidity
    function _validatePositionList(
        address account,
        TokenId[] calldata positionIdList,
        uint256 offset
    ) internal view {
        uint256 pLength;
        uint256 currentHash = s_positionsHash[account];

        unchecked {
            pLength = positionIdList.length - offset;
        }
        // note that if pLength == 0 even if a user has existing position(s) the below will fail b/c the fingerprints will mismatch
        // Check that position hash (the fingerprint of option positions) matches the one stored for the '_account'
        uint256 fingerprintIncomingList;

        for (uint256 i = 0; i < pLength; ) {
>           fingerprintIncomingList = PanopticMath.updatePositionsHash(
                fingerprintIncomingList,
                positionIdList[i],
                ADD
            );
            unchecked {
                ++i;
            }
        }

        // revert if fingerprint for provided '_positionIdList' does not match the one stored for the '_account'
        if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();
    }
```

PanopticMath.sol

```solidity
    function updatePositionsHash(
        uint256 existingHash,
        TokenId tokenId,
        bool addFlag
    ) internal pure returns (uint256) {
        // add the XOR`ed hash of the single option position `tokenId` to the `existingHash`
        // @dev 0 ^ x = x

        unchecked {
            // update hash by taking the XOR of the new tokenId
            uint248 updatedHash = uint248(existingHash) ^
                (uint248(uint256(keccak256(abi.encode(tokenId)))));
            // increment the top 8 bit if addflag=true, decrement otherwise
            return
                addFlag
                    ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)
                    : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);
        }
    }
```

Then, let's see how duplicate ids can bypass solvency check. The solvency check is in `_validateSolvency()`, which is called by all the user interaction functions, such as mint/burn/liquidate/forceExercise/settleLongPremium. This function first checks for a user passed in `positionIdList` (which we already proved can include duplicates), then calls `_checkSolvencyAtTick()` to calculate the `balanceCross` (collateral balance) and `thresholdCross` (required collateral) for all tokens.

The key is the collateral balance includes the premium that is collected for each of the positions. For most of the positions, the collected premium should be less than required collateral to keep this position open. However, if a position has been open for a long enough time, the fees it accumulated may be larger than required collateral.

For this kind of position, we can duplicate it 256 times (or multiple of 256 times, as long as gas fee is enough), and make our collateral balance grow faster than required collateral. This can make a insolvent account "solvent", by duplicating the key tokenId multiple times.

```solidity
    function _validateSolvency(
        address user,
        TokenId[] calldata positionIdList,
        uint256 buffer
    ) internal view returns (uint256 medianData) {
        // check that the provided positionIdList matches the positions in memory
>       _validatePositionList(user, positionIdList, 0);
        ...
        // Check the user's solvency at the fast tick; revert if not solvent
        bool solventAtFast = _checkSolvencyAtTick(
            user,
            positionIdList,
            currentTick,
            fastOracleTick,
            buffer
        );
        if (!solventAtFast) revert Errors.NotEnoughCollateral();

        // If one of the ticks is too stale, we fall back to the more conservative tick, i.e, the user must be solvent at both the fast and slow oracle ticks.
        if (Math.abs(int256(fastOracleTick) - slowOracleTick) > MAX_SLOW_FAST_DELTA)
            if (!_checkSolvencyAtTick(user, positionIdList, currentTick, slowOracleTick, buffer))
                revert Errors.NotEnoughCollateral();
    }

    function _checkSolvencyAtTick(
        address account,
        TokenId[] calldata positionIdList,
        int24 currentTick,
        int24 atTick,
        uint256 buffer
    ) internal view returns (bool) {
        (
            LeftRightSigned portfolioPremium,
            uint256[2][] memory positionBalanceArray
        ) = _calculateAccumulatedPremia(
                account,
                positionIdList,
                COMPUTE_ALL_PREMIA,
                ONLY_AVAILABLE_PREMIUM,
                currentTick
            );

        LeftRightUnsigned tokenData0 = s_collateralToken0.getAccountMarginDetails(
            account,
            atTick,
            positionBalanceArray,
            portfolioPremium.rightSlot()
        );
        LeftRightUnsigned tokenData1 = s_collateralToken1.getAccountMarginDetails(
            account,
            atTick,
            positionBalanceArray,
            portfolioPremium.leftSlot()
        );

        (uint256 balanceCross, uint256 thresholdCross) = _getSolvencyBalances(
            tokenData0,
            tokenData1,
            Math.getSqrtRatioAtTick(atTick)
        );

        // compare balance and required tokens, can use unsafe div because denominator is always nonzero
        unchecked {
            return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);
        }
    }
```

CollateralTracker.sol

```solidity
    function getAccountMarginDetails(
        address user,
        int24 currentTick,
        uint256[2][] memory positionBalanceArray,
        int128 premiumAllPositions
    ) public view returns (LeftRightUnsigned tokenData) {
        tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);
    }

    function _getAccountMargin(
        address user,
        int24 atTick,
        uint256[2][] memory positionBalanceArray,
        int128 premiumAllPositions
    ) internal view returns (LeftRightUnsigned tokenData) {
        uint256 tokenRequired;

        // if the account has active options, compute the required collateral to keep account in good health
        if (positionBalanceArray.length > 0) {
            // get all collateral required for the incoming list of positions
            tokenRequired = _getTotalRequiredCollateral(atTick, positionBalanceArray);

            // If premium is negative (ie. user has to pay for their purchased options), add this long premium to the token requirement
            if (premiumAllPositions < 0) {
                unchecked {
                    tokenRequired += uint128(-premiumAllPositions);
                }
            }
        }

        // if premium is positive (ie. user will receive funds due to selling options), add this premum to the user's balance
        uint256 netBalance = convertToAssets(balanceOf[user]);
        if (premiumAllPositions > 0) {
            unchecked {
                netBalance += uint256(uint128(premiumAllPositions));
            }
        }

        // store assetBalance and tokens required in tokenData variable
        tokenData = tokenData.toRightSlot(netBalance.toUint128()).toLeftSlot(
            tokenRequired.toUint128()
        );
        return tokenData;
    }
```

Now we have shown how to bypass the `_validateSolvency()`, we can bypass all related checks. Listing them here:

1.  Burn options [#1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L577), [#2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L600)
2.  Mint options [#1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L661)
3.  Force exercise [#1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L661), [#2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1275)
4.  SettleLongPremium [#1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1658)

### Proof of Concept

In this report, we will only prove the core issue: duplicate tokenIds are allowed, and won't craft complicated scenarios for relevant impacts.

Add the following test code in `PanopticPool.t.sol`, we can see that passing 257 of the same token ids can still work for `mintOptions()`.

```solidity
    function test_duplicatePositionHash(
        uint256 x,
        uint256[2] memory widthSeeds,
        int256[2] memory strikeSeeds,
        uint256[2] memory positionSizeSeeds,
        uint256 swapSizeSeed
    ) public {
        _initPool(x);

        (int24 width, int24 strike) = PositionUtils.getOTMSW(
            widthSeeds[0],
            strikeSeeds[0],
            uint24(tickSpacing),
            currentTick,
            0
        );

        (int24 width2, int24 strike2) = PositionUtils.getOTMSW(
            widthSeeds[1],
            strikeSeeds[1],
            uint24(tickSpacing),
            currentTick,
            0
        );
        vm.assume(width2 != width || strike2 != strike);

        populatePositionData([width, width2], [strike, strike2], positionSizeSeeds);

        // leg 1
        TokenId tokenId = TokenId.wrap(0).addPoolId(poolId).addLeg(
            0, 1, isWETH, 0, 0, 0, strike, width
        );

        TokenId[] memory posIdList = new TokenId[](257);
        for (uint i = 0; i < 257; ++i) {
            posIdList[i] = tokenId;
        }
        pp.mintOptions(posIdList, positionSizes[0], 0, 0, 0);
    }
```

### Recommended Mitigation Steps

Add a check in `_validatePositionList` that the length is shorter than `MAX_POSITIONS` (32).

### Assessed type

Invalid Validation

**[dyedm1 (Panoptic) confirmed](https://github.com/code-423n4/2024-04-panoptic-findings/issues/498#event-12628202755)**

**[Picodes (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/498#issuecomment-2103284028):**
 > I don't think here "liquidation bots not liquidating the insolvent position during a period of time" is an external requirement considering how critical liquidations are to Panoptic.  My reasoning is that even if the loss of funds is not "direct", being able to properly control when positions can be opened is a key feature, and the fact that you can "increase your leverage" while being insolvent prevents proper risk control.
> 
> However, it's true that this is not strictly speaking a scenario where "assets can be stolen/lost/compromised directly" so I'll downgrade to Med.

*Note: for full discussion, please see the [original submission](https://github.com/code-423n4/2024-04-panoptic-findings/issues/498).*



***

## [[M-03] `CREATE2` address collision during pool deployment allows for complete draining of the pool](https://github.com/code-423n4/2024-04-panoptic-findings/issues/482)
*Submitted by [Kalogerone](https://github.com/code-423n4/2024-04-panoptic-findings/issues/482)*

<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L237>

<https://github.com/OpenZeppelin/openzeppelin-contracts/blob/0a25c1940ca220686588c4af3ec526f725fe2582/contracts/proxy/Clones.sol#L53>

*(NOTE: This report is very highly inspired from [this past valid report.](https://github.com/sherlock-audit/2023-12-arcadia-judging/issues/59) Necessary changes have been made to suit the Panoptic Protocol.)*

The attack consists of two parts: Finding a collision, and actually draining the lending pool. We describe both here:

### Proof of Concept: Finding a collision

Note that in `PanopticFactory::deployNewPool`, `CREATE2` salt is user-supplied which is then passed to `Clones::cloneDeterministic`:

```javascript
    function deployNewPool(address token0, address token1, uint24 fee, bytes32 salt)
        external
        returns (PanopticPool newPoolContract)
    {
        // sort the tokens, if necessary:
        (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);

        .
        .
        .

        // This creates a new Panoptic Pool (proxy to the PanopticPool implementation)
        // Users can specify a salt, the aim is to incentivize the mining of addresses with leading zeros
@>      newPoolContract = PanopticPool(POOL_REFERENCE.cloneDeterministic(salt));

        .
        .
        .
    }
```

```javascript
    function cloneDeterministic(address implementation, bytes32 salt) internal returns (address instance) {
        /// @solidity memory-safe-assembly
        assembly {
            // Cleans the upper 96 bits of the `implementation` word, then packs the first 3 bytes
            // of the `implementation` address with the bytecode before the address.
            mstore(0x00, or(shr(0xe8, shl(0x60, implementation)), 0x3d602d80600a3d3981f3363d3d373d3d3d363d73000000))
            // Packs the remaining 17 bytes of `implementation` with the bytecode after the address.
            mstore(0x20, or(shl(0x78, implementation), 0x5af43d82803e903d91602b57fd5bf3))
@>          instance := create2(0, 0x09, 0x37, salt)
        }
        require(instance != address(0), "ERC1167: create2 failed");
    }
```

The address collision an attacker will need to find are:

*   One undeployed Panoptic Pool address (1).
*   Arbitrary attacker-controlled wallet contract (2).

Both sets of addresses can be brute-force searched because:

*   As shown above, `salt` is a user-supplied parameter. By brute-forcing many `salt` values, we have obtained many different (undeployed) wallet accounts for (1). The user can know the address of the Panoptic Pool before deploying it, since as shown in the above code snippet, the result is deterministic.
*   (2) can be searched the same way. The contract just has to be deployed using `CREATE2`, and the `salt` is in the attacker's control by definition.

An attacker can find any single address collision between (1) and (2) with high probability of success using the following meet-in-the-middle technique, a classic brute-force-based attack in cryptography:

*   Brute-force a sufficient number of values of salt (`2^80`), pre-compute the resulting account addresses, and efficiently store them e.g. in a Bloom filter data structure.
*   Brute-force contract pre-computation to find a collision with any address within the stored set in step 1.

The feasibility, as well as detailed technique and hardware requirements of finding a collision, are sufficiently described in multiple references:

*   [1: A past issue on Sherlock describing this attack.](https://github.com/sherlock-audit/2023-07-kyber-swap-judging/issues/90)
*   [2: EIP-3607, which rationale is this exact attack. The EIP is in final state.](https://eips.ethereum.org/EIPS/eip-3607)
*   [3: A blog post discussing the cost (money and time) of this exact attack.](https://mystenlabs.com/blog/ambush-attacks-on-160bit-objectids-addresses)

The [hashrate of the BTC network](https://www.blockchain.com/explorer/charts/hash-rate) has reached `6.5 x 10^20` hashes per second as of time of writing, taking only just 31 minutes to achieve `2^80` hashes. A fraction of this computing power will still easily find a collision in a reasonably short timeline.

### Proof of Concept: Draining the lending pool

Even given EIP-3607 which disables an EOA if a contract is already deployed on top, we show that it's still possible to drain the Panoptic Pool entirely given a contract collision.

Assuming the attacker has already found an address collision against an undeployed Panoptic Pool, let's say `0xCOLLIDED`. The steps for complete draining of the Panoptic Pool are as follow:

First tx:

*   Deploy the attack contract onto address `0xCOLLIDED`.
*   Set infinite allowance for {`0xCOLLIDED` \-\-\-> attacker wallet} for any token they want.
*   Destroy the contract using `selfdestruct`.

Post Dencun hardfork, [`selfdestruct` is still possible if the contract was created in the same transaction.](https://eips.ethereum.org/EIPS/eip-6780) The only catch is that all 3 of these steps must be done in one tx.

The attacker now has complete control of any funds sent to `0xCOLLIDED`.

Second tx:

*   Deploy the Panoptic Pool to `0xCOLLIDED`.
*   Wait until the Panoptic Pool will hold as many tokens as you want and drain it.

The attacker has stolen all funds from the Panoptic Pool.

### Impact

Address collision can cause all tokens of a Panoptic Pool to be drain.

### Proof of Concept

While we cannot provide an actual hash collision due to infrastructural constraints, we are able to provide a coded PoC to prove the following two properties of the EVM that would enable this attack:

*   A contract can be deployed on top of an address that already had a contract before.
*   By deploying a contract and self-destruct in the same tx, we are able to set allowance for an address that has no bytecode.

Here is the PoC, as well as detailed steps to recreate it:

*   Paste the following file onto Remix (or a developing environment of choice): [POC](https://gist.github.com/midori-fuse/087aa3248da114a0712757348fcce814)
*   Deploy the contract `Test`.
*   Run the function `Test.test()` with a salt of your choice, and record the returned address. The result will be:
    *   `Test.getAllowance()` for that address will return exactly APPROVE_AMOUNT.
    *   `Test.getCodeSize()` for that address will return exactly zero.
    *   This proves the second property.
*   Using the same salt in step 3, run Test.test() again. The tx will go through, and the result will be:
    *   `Test.test()` returns the same address as with the first run.
    *   `Test.getAllowance()` for that address will return twice of APPROVE_AMOUNT.
    *   `Test.getCodeSize()` for that address will still return zero.
    *   This proves the first property.

The provided PoC has been tested on Remix IDE, on the Remix VM - Mainnet fork environment, as well as testing locally on the Holesky testnet fork, which as of time of writing, has been upgraded with the Dencun hardfork.

### Tools Used

Remix IDE

### Recommended Mitigation Steps

*   Don't allow the user to control the `salt` used.
*   Consider also adding and encoding `block.timestamp` and `block.number` combined with the user's `salt`. Then the attacker, after they successfully found a hash collision, already has to execute the attack at a fixed block and probably conspire with the sequencer to ensure that also the time is fixed.

**[dyedm1 (Panoptic) acknowledged and commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/482#issuecomment-2080091343):**
 > Technically true, but the cost to do this is enormous (with a likely minimal return, given that deposits would first have to be solicited into that pool), and we can add safeguards on the frontend to prevent this kind of attack.

**[Picodes (judge) commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/482#issuecomment-2096043469):**
 > This report is worth Medium severity to me, considering:
>  - that the attacker could target any pool playing on the salt
>  - that the attacker can wait for enough deposits before draining the pool
> 
> So it fulfills "hypothetical attack path with stated assumptions, but external requirements".



***

## [[M-04] Incorrect validation during checking liquidity spread](https://github.com/code-423n4/2024-04-panoptic-findings/issues/479)
*Submitted by [KupiaSec](https://github.com/code-423n4/2024-04-panoptic-findings/issues/479)*

### Impact

Because of incorrect validation, it allows option buyers not to pay premium.

### Proof of Concept

When long leg is minted or short leg is burnt, the protocol checks liquidity spread by calculating `TotalLiquidity / NetLiquidity` and allows it not exceed `9`.<br>
However in the check function, the validation is ignored when `NetLiquidity` is zero.

This means when a user mints long leg that buys whole selling amount, the liquidity spread is not checked.<br>
This issue allows the option buyer not to pay premium, and here is why:

1.  When options are minted, last accumulated premium is stored to `s_grossPremiumLast`. Refer to `_updateSettlementPostMint` function of `PanopticPool` contract.
2.  When options are burned, new accumulated premium is fetched and calculates the premium by multiplying liquidity with difference in accumulated premium. Refer to `_updateSettlementPostBurn` function of `PanopticPool` contract.
3.  However, when a long leg of T(total liquidity) amount is minted, N becomes zero.
4.  Later, when the minted long leg is burnt, premium values are not updated in SFPM, because N is zero. Refer to [SFPM:L1085](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1085-L1094).

Since there is no difference in owed premium value, the option buyer will not pay the premium when burning the option.

### Recommended Mitigation Steps

When checking liquidity spread, it should revert when N is zero and T is positive:

```solidity
+   if(netLiquidity == 0 && totalLiquidity > 0) revert;
    if(netLiquidity == 0) return;
```

### Assessed type

Context

**[dyedm1 (Panoptic) confirmed](https://github.com/code-423n4/2024-04-panoptic-findings/issues/479#event-12628350143)**



***

## [[M-05] Panoptic pool can be non-profitable by specific Uniswap governance](https://github.com/code-423n4/2024-04-panoptic-findings/issues/469)
*Submitted by [petro\_1912](https://github.com/code-423n4/2024-04-panoptic-findings/issues/469), also found by [Joshuajee](https://github.com/code-423n4/2024-04-panoptic-findings/issues/266)*

<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L247-L251>

<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L261-L263>

Swap commission is paid on the intrinsic value based on `s_ITMSpreadFee` in `CollateralTracker` contract.<br>
If `s_ITMSpreadFee` is zero, then swap commission can not be paid.

### Proof of Concept

```solidity
    function startToken(
        bool underlyingIsToken0,
        address token0,
        address token1,
        uint24 fee,
        PanopticPool panopticPool
    ) external {
        
        __SNIP__
        // cache the pool fee in basis points
        uint24 _poolFee;
        unchecked {
            _poolFee = fee / 100; // @audit below fee 0.01%, then _poolFee = 0  
        }
        s_poolFee = _poolFee;

        ...

        __SNIP__        
        // Additional risk premium charged on intrinsic value of ITM positions
        unchecked {
            s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);
        }
    }
```

As you can see above code snippet, if fee(Uniswap fee) is below 100, then \_poolFee and s_ITMSpreadFee can be zero.<br>
Currently, there are no such pools that have below 0.01% fee on the UniswapV3.<br>
But Uniswap fee level can be adjusted by the governance proposal like November 2021.<br>
Here is the mention about it in Uniswap Protocol:

> Uniswap v3 introduces multiple pools for each token pair, each with a different swapping fee. Liquidity providers may initially create pools at three fee levels: 0.05%, 0.30%, and 1%. More fee levels may be added by UNI governance, e.g. the 0.01\% fee level added by this governance proposal in November 2021, as executed here.

<https://dune.com/jcarnes/The-StableSwap-Wars>

Competitions between Protocols like Uniswap and Carbon, more fee levels can be added in the future.

Indeed, there are several discussions on the less fee levels in stable coins pair.<br>
<https://gov.bancor.network/t/custom-taker-fee-on-stable-to-stable-trades/4370>

*   Carbon has a protocol wide fee of 20 BP (basis points).
*   This fee, while appropriate for volatile pairs - is not in line with the market when it comes to stable to stable trades.
*   For reference, Uniswap added a 1 BP fee option (0.01\%) - in November 2021 (link)
*   This proposal seeks to take this one step further and introduce a fee of 0.001\% on stable to stable trades. This is 1/10th of a single basis point.

If protocol fee is less than 100 (i.e fee < 0.01 \%), then PanopticPool's swap commission can not be taken.

### Recommended Mitigation Steps

Use Uniswap's DECIMALS (1e6) instead 10\_000 and update all code related to DECIMALS.

### Assessed type

Uniswap

**[dyedm1 (Panoptic) confirmed](https://github.com/code-423n4/2024-04-panoptic-findings/issues/469#event-12628451367)**

**[Picodes (judge) commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/469#issuecomment-2083735676):**
 > This report shows how the current version of the protocol may not support all Uniswap V3 pools whereas the sponsor's label suggests it was their intention, so Medium severity seems appropriate under "broken functionality".



***

## [[M-06] `_updateSettlementPostBurn()` may not correctly reduce `s_grossPremiumLast[chunkKey]`](https://github.com/code-423n4/2024-04-panoptic-findings/issues/462)
*Submitted by [bin2chen](https://github.com/code-423n4/2024-04-panoptic-findings/issues/462)*

`s_grossPremiumLast[]` definitions are as follows:

> /// @dev Per-chunk `last` value that gives the aggregate amount of premium owed to all sellers when multiplied by the total amount of liquidity `totalLiquidity`<br>
> /// totalGrossPremium = totalLiquidity &ast; (grossPremium(perLiquidityX64) - lastGrossPremium(perLiquidityX64)) / 2&ast;&ast;64<br>
> /// Used to compute the denominator for the fraction of premium available to sellers to collect<br>
> /// LeftRight - right slot is token0, left slot is token1<br>
> mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;

A critical rule: if there is a change in `totalLiquidity`, we must recalculate this value.

When `Pool.mintOptions()`, `s_grossPremiumLast[chunkKey]` will increase.

Step: `mintOptions()`->`_mintInSFPMAndUpdateCollateral()`->`_updateSettlementPostMint()`

```solidity
    function _updateSettlementPostMint(
        TokenId tokenId,
        LeftRightUnsigned[4] memory collectedByLeg,
        uint128 positionSize
    ) internal {
...
            if (tokenId.isLong(leg) == 0) { 
                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                    tokenId,
                    leg,
                    positionSize
                );
...
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

@>                  s_grossPremiumLast[chunkKey] = LeftRightUnsigned
                        .wrap(0)
                        .toRightSlot(
                            uint128(
                                (grossCurrent[0] *
                                    positionLiquidity +
                                    grossPremiumLast.rightSlot() *
                                    totalLiquidityBefore) / (totalLiquidity)
                            )
                        )
                        .toLeftSlot(
                            uint128(
                                (grossCurrent[1] *
                                    positionLiquidity +
                                    grossPremiumLast.leftSlot() *
                                    totalLiquidityBefore) / (totalLiquidity)
                            )
                        );
                }
            }
        }
    }
```

When `Pool.burnOptions()`，`s_grossPremiumLast[chunkKey]` will decrease

`burnOptions()`->`_burnAndHandleExercise()`->`_updateSettlementPostBurn()`

```solidity
    function _updateSettlementPostBurn(
        address owner,
        TokenId tokenId,
        LeftRightUnsigned[4] memory collectedByLeg,
        uint128 positionSize,
        bool commitLongSettled
    ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
...
        uint256 numLegs = tokenId.countLegs();
        uint256[2][4] memory premiumAccumulatorsByLeg;

        // compute accumulated fees
        (premiaByLeg, premiumAccumulatorsByLeg) = _getPremia(
            tokenId,
            positionSize,
            owner,
            COMPUTE_ALL_PREMIA,
            type(int24).max
        );

        for (uint256 leg = 0; leg < numLegs; ) {
            LeftRightSigned legPremia = premiaByLeg[leg];

            bytes32 chunkKey = keccak256(
                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
            );

            // collected from Uniswap
            LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);

@>          if (LeftRightSigned.unwrap(legPremia) != 0) {
                // (will be) paid by long legs
                if (tokenId.isLong(leg) == 1) {
...
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

...

                    unchecked {
                        uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
                        uint256 _leg = leg;

                        // if there's still liquidity, compute the new grossPremiumLast
                        // otherwise, we just reset grossPremiumLast to the current grossPremium
@>                      s_grossPremiumLast[chunkKey] = totalLiquidity != 0
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
                                                            positionLiquidity
                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
                                                0
                                            )
                                        ) / totalLiquidity
                                    )
                                )
                                .toLeftSlot(
                                    uint128(
                                        uint256(
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
                                    )
                                )
                            : LeftRightUnsigned
                                .wrap(0)
                                .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
                                .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
                    }
                }
            }

            // update settled tokens in storage with all local deltas
            s_settledTokens[chunkKey] = settledTokens;

            unchecked {
                ++leg;
            }
```

The issue lies within `_updateSettlementPostBurn()`, where it adds a condition that `if (LeftRightSigned.unwrap(legPremia) != 0)` must be met for `s_grossPremiumLast[chunkKey]` to decrease.

This results in not recalculating `s_grossPremiumLast[chunkKey]` even when `totalLiquidity` changes.

For example, in the same block, if a user executes `mintOptions()`, `s_grossPremiumLast[chunkKey]` increases by 50. Immediately after, executing `burnOptions()` doesn't decrease `s_grossPremiumLast[chunkKey]` by 50 because `legPremia == 0`.

### Proof of Concept

The following code demonstrates this scenario, where `s_grossPremiumLast[chunkKey]` keeps increasing, so `last gross accumulated` keeps decreasing.

1.  Add to `Misc.t.sol`

```solidity
    function test_burn_not_reduce_last() public {
        swapperc = new SwapperC();
        vm.startPrank(Swapper);
        token0.mint(Swapper, type(uint128).max);
        token1.mint(Swapper, type(uint128).max);
        token0.approve(address(swapperc), type(uint128).max);
        token1.approve(address(swapperc), type(uint128).max);

        // mint OTM position
        $posIdList.push(
            TokenId.wrap(0).addPoolId(PanopticMath.getPoolId(address(uniPool))).addLeg(
                0,
                1,
                1,
                0,
                0,
                0,
                15,
                1
            )
        );
        //@info Bob same gross
        vm.startPrank(Bob);
        pp.mintOptions($posIdList, 1_000_000, 0, 0, 0);
        vm.startPrank(Swapper);
        swapperc.swapTo(uniPool, Math.getSqrtRatioAtTick(10) + 1);
        // 1998600539
        accruePoolFeesInRange(address(uniPool), (uniPool.liquidity() * 2) / 3, 1, 1);
        swapperc.swapTo(uniPool, 2 ** 96); 
        //@info end of Bob same gross

        //@info start alice , it should without change gross
        console.log("*****start alice mint/burn should not reduce last accumulated");
        for(uint256 i=0;i<10;i++){
            vm.startPrank(Alice);
            pp.mintOptions($posIdList, 250_000, type(uint64).max, 0, 0);

            vm.startPrank(Alice);
            pp.burnOptions($posIdList[0], new TokenId[](0), 0, 0);
        } 
    }    
```

2.  Add to `PanopticPool.sol`

```diff
    function _updateSettlementPostMint(
        TokenId tokenId,
        LeftRightUnsigned[4] memory collectedByLeg,
        uint128 positionSize
    ) internal {
...
               unchecked {
                    // L
                    LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
                    // R
                    uint256 positionLiquidity = liquidityChunk.liquidity();
                    // T (totalLiquidity is (T + R) after minting)
                    uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
                    //console.log("s_grossPremiumLast[chunkKey].rightSlot() from:",s_grossPremiumLast[chunkKey].rightSlot());
                    s_grossPremiumLast[chunkKey] = LeftRightUnsigned
                        .wrap(0)
                        .toRightSlot(
                            uint128(
                                (grossCurrent[0] *
                                    positionLiquidity +
                                    grossPremiumLast.rightSlot() *
                                    totalLiquidityBefore) / (totalLiquidity)
                            )
                        )
                        .toLeftSlot(
                            uint128(
                                (grossCurrent[1] *
                                    positionLiquidity +
                                    grossPremiumLast.leftSlot() *
                                    totalLiquidityBefore) / (totalLiquidity)
                            )
                        );
+                       console.log("last accumulated : ",(grossCurrent[0] - s_grossPremiumLast[chunkKey].rightSlot()) * totalLiquidity);
                }
            }
        }
    }
```

```console
$ forge test -vvv --match-test test_burn_not_reduce_last

[PASS] test_burn_not_reduce_last() (gas: 5276055)
Logs:
  last accumulated :  0
  *****start alice mint/burn should not reduce last accumulated
  last accumulated :  36893488148466911062
  last accumulated :  29514790528266881407
  last accumulated :  23611832432106857683
  last accumulated :  18889465953679888300
  last accumulated :  15111572767940411986
  last accumulated :  12089258220348131204
  last accumulated :  9671406580275706040
  last accumulated :  7737125266718815505
  last accumulated :  6189700215873303077
  last accumulated :  4951760174697243000
```

### Impact

Due to the incorrect accounting of `s_grossPremiumLast[chunkKey]`, the calculation in `_getAvailablePremium()` is also incorrect. This results in inaccuracies in the amount of premium received by the seller when closing their position.

### Recommended Mitigation

Regardless of the value of `legPremia`, it should recalculate `s_grossPremiumLast[chunkKey]` when `long == 0`.

<details>

```diff
    function _updateSettlementPostBurn(
        address owner,
        TokenId tokenId,
        LeftRightUnsigned[4] memory collectedByLeg,
        uint128 positionSize,
        bool commitLongSettled
    ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
...
        for (uint256 leg = 0; leg < numLegs; ) {
            LeftRightSigned legPremia = premiaByLeg[leg];

            bytes32 chunkKey = keccak256(
                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
            );

            // collected from Uniswap
            LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);

            if (LeftRightSigned.unwrap(legPremia) != 0) {
                // (will be) paid by long legs
                if (tokenId.isLong(leg) == 1) {
...
                } else {
....

                    // subtract settled tokens sent to seller
                    settledTokens = settledTokens.sub(availablePremium);

                    // add available premium to amount that should be settled
                    realizedPremia = realizedPremia.add(
                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
                    );


-                   unchecked {
-                       uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;-
-                        uint256 _leg = leg;
-
-                        // if there's still liquidity, compute the new grossPremiumLast
-                        // otherwise, we just reset grossPremiumLast to the current grossPremium
-                        s_grossPremiumLast[chunkKey] = totalLiquidity != 0
-                            ? LeftRightUnsigned
-                                .wrap(0)
-                                .toRightSlot(
-                                    uint128(
-                                        uint256(
-                                            Math.max(
-                                                (int256(
-                                                    grossPremiumLast.rightSlot() *
-                                                        totalLiquidityBefore
-                                                ) -
-                                                    int256(
-                                                        _premiumAccumulatorsByLeg[_leg][0] *
-                                                            positionLiquidity
-                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
-                                                0
-                                            )
-                                        ) / totalLiquidity
-                                    )
-                                )
-                                .toLeftSlot(
-                                    uint128(
-                                        uint256(
-                                            Math.max(
-                                                (int256(
-                                                    grossPremiumLast.leftSlot() *
-                                                        totalLiquidityBefore
-                                                ) -
-                                                    int256(
-                                                        _premiumAccumulatorsByLeg[_leg][1] *
-                                                            positionLiquidity
-                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
-                                                0
-                                            )
-                                        ) / totalLiquidity
-                                    )
-                                )
-                            : LeftRightUnsigned
-                                .wrap(0)
-                                .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
-                                .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
-                       }
                   }
               }

+             if (tokenId.isLong(leg) == 0){
+                   uint256 positionLiquidity = PanopticMath
+                   .getLiquidityChunk(tokenId, leg, positionSize)
+                    .liquidity();
+
+                    // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (T - R)
+                    uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
+                    // T (totalLiquidity is (T - R) after burning)
+                   uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;
+
+                    LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];                
+                    unchecked {
+                        uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
+                        uint256 _leg = leg;
+
+                        // if there's still liquidity, compute the new grossPremiumLast
+                        // otherwise, we just reset grossPremiumLast to the current grossPremium                        
+                        s_grossPremiumLast[chunkKey] = totalLiquidity != 0
+                            ? LeftRightUnsigned
+                                .wrap(0)
+                                .toRightSlot(
+                                    uint128(
+                                        uint256(
+                                            Math.max(
+                                                (int256(
+                                                    grossPremiumLast.rightSlot() *
+                                                        totalLiquidityBefore
+                                                ) -
+                                                    int256(
+                                                        _premiumAccumulatorsByLeg[_leg][0] *
+                                                            positionLiquidity
+                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
+                                                0
+                                            )
+                                        ) / totalLiquidity
+                                    )
+                                )
+                                .toLeftSlot(
+                                    uint128(
+                                       uint256(
+                                            Math.max(
+                                                (int256(
+                                                    grossPremiumLast.leftSlot() *
+                                                        totalLiquidityBefore
+                                                ) -
+                                                    int256(
+                                                        _premiumAccumulatorsByLeg[_leg][1] *
+                                                            positionLiquidity
+                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
+                                                0
+                                            )
+                                        ) / totalLiquidity
+                                    )
+                                )
+                            : LeftRightUnsigned
+                                .wrap(0)
+                                .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
+                                .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));                             
+                    }
+                }

            }

            // update settled tokens in storage with all local deltas
            s_settledTokens[chunkKey] = settledTokens;

            unchecked {
                ++leg;
            }
        }
    }
}
```

</details>

### Assessed type

Context

**[dyedm1 (Panoptic) confirmed](https://github.com/code-423n4/2024-04-panoptic-findings/issues/462#event-12628510967)**



***

## [[M-07] When Burning a Tokenized Position `validate` should be done before flipping the `isLong` bits in `_validateAndForwardToAMM()`](https://github.com/code-423n4/2024-04-panoptic-findings/issues/459)
*Submitted by [0xdice91](https://github.com/code-423n4/2024-04-panoptic-findings/issues/459)*

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L535-L571>

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L673-L702>

Each leg in a `tokenid` has a risk partner which is usually its own index but in some cases, it could be another leg (Partner in defined risk position).

In the function `validate()` if the risk partner of a specific leg is `not` its own index then some additional checks are done to ensure that they are compatible like:

*   Ensuring that risk partners are mutual
*   Ensures that risk partners have the same asset.
*   Ensures that risk partners have the same ratio.
*   Plus other checks that depend on the legs `isLong` value compared to that of its risk partner.

```solidity
    function validate(TokenId self) internal pure {
        if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

// More Code...
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
        }
    }
```

In `burnTokenizedPosition()` the internal function `_validateAndForwardToAMM()` is called, this function calls [Tokenid.flipToBurnToken()](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L366-L398) which simply `flips` the isLong bits of all active legs of the tokenid. Then `validate()` is called which validates a position tokenId and its legs.

```solidity
    /// @param tokenId the option position
    /// @param positionSize the size of the position to create
    /// @param tickLimitLow lower limits on potential slippage
    /// @param tickLimitHigh upper limits on potential slippage
    /// @param isBurn is equal to false for mints and true for burns
    /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg
    /// @return totalMoved the total amount of funds swapped in Uniswap as part of building potential ITM positions
    function _validateAndForwardToAMM(
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
// More Code...
}
```

The issue here is that if a leg in the tokenid has its `risk partner` as another leg (that is, it is not its own risk partner), then flipping the `isLong` bits may cause one of the checks
in `validate()` to fail and revert as the `isLong` bits of its risk partner are `not` changed as well.

Remember that flipping changes the value of the bit from what it was to an opposite value (from 0 to 1 or from 1 to 0).

For example;
Let's say a leg with a different risk partner has  `isLong()` values that are the same but their `tokenType()` is different, this would easily pass these checks below from `validate()`
but after a flip is done to its `isLong` bits using [flipToBurnToken()](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L366-L398) it will fail and revert in the second check below.

```solidity
                   // if the position is the same i.e both long calls, short put's etc.
                   // then this is a regular position, not a defined risk position
                   if ((_isLong == isLongP) && (_tokenType == tokenTypeP))
                       revert Errors.InvalidTokenIdParameter(4);


                   // if the two token long-types and the tokenTypes are both different (one is a short call, the other a long put, e.g.), this is a synthetic position
                   // A synthetic long or short is more capital efficient than each leg separated because the long+short premia accumulate proportionally
                   // unlike short stranlges, long strangles also cannot be partnered, because there is no reduction in risk (both legs can earn premia simultaneously)
                   if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))
                       revert Errors.InvalidTokenIdParameter(5);
```

### Impact

This will result in a continuous revert of the function leading to an inability to Burn a Tokenized Position.

### Recommended Mitigation Steps

This whole issue results from the simple fact the risk partners, if different, are not flipped as well. I recommend validating the `tokenid` before flipping the `isLong` bits, to ensure any changes caused by flipping will not affect the execution of the function.

```solidity
    /// @param tokenId the option position
    /// @param positionSize the size of the position to create
    /// @param tickLimitLow lower limits on potential slippage
    /// @param tickLimitHigh upper limits on potential slippage
    /// @param isBurn is equal to false for mints and true for burns
    /// @return collectedByLeg An array of LeftRight encoded words containing the amount of token0 and token1 collected as fees for each leg
    /// @return totalMoved the total amount of funds swapped in Uniswap as part of building potential ITM positions
    function _validateAndForwardToAMM(
        TokenId tokenId,
        uint128 positionSize,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        bool isBurn
    ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {
        // Reverts if positionSize is 0 and user did not own the position before minting/burning
        if (positionSize == 0) revert Errors.OptionsBalanceZero();

    ++  // Validate tokenId
    ++  tokenId.validate();


        /// @dev the flipToBurnToken() function flips the isLong bits
        if (isBurn) {
            tokenId = tokenId.flipToBurnToken();
        }


        // Extract univ3pool from the poolId map to Uniswap Pool
        IUniswapV3Pool univ3pool = s_poolContext[tokenId.poolId()].pool;


        // Revert if the pool not been previously initialized
        if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();
// More Code...
}
```

**[dyedm1 (Panoptic) confirmed](https://github.com/code-423n4/2024-04-panoptic-findings/issues/459#event-12628512484)**

**[Picodes (judge) commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/459#issuecomment-2096323198):**
 > Keeping Medium severity under "functionality is broken".



***

## [[M-08] Wrong leg `chunkKey` calculation in `haircutPremia` function](https://github.com/code-423n4/2024-04-panoptic-findings/issues/374)
*Submitted by [Aymen0909](https://github.com/code-423n4/2024-04-panoptic-findings/issues/374), also found by [FastChecker](https://github.com/code-423n4/2024-04-panoptic-findings/issues/444), [0xStalin](https://github.com/code-423n4/2024-04-panoptic-findings/issues/343), and [DanielArmstrong](https://github.com/code-423n4/2024-04-panoptic-findings/issues/140)*

<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L878-L884>

<https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1122-L1131>

When the user positions are getting liquidated, the `PanopticPool::liquidate` function will invoke under the hood the `PanopticMath::haircutPremia` function which will use the user's long premium to cover the protocol losses.

The `PanopticMath::haircutPremia` function will also update the storage mapping `settledTokens` which represent the per-chunk accumulator for tokens owed to options sellers.

The issue that it's present in the `PanopticMath::haircutPremia` function is when it runs the for-loop to update `settledTokens` for each position leg chunk, inside the loop the function uses always the index `0` when calculating the leg `chunkKey` instead of using the actual leg index `leg` (which can be 0,1,2,3), this shown in the code snippet below:

```solidity
function haircutPremia(
    address liquidatee,
    TokenId[] memory positionIdList,
    LeftRightSigned[4][] memory premiasByLeg,
    LeftRightSigned collateralRemaining,
    CollateralTracker collateral0,
    CollateralTracker collateral1,
    uint160 sqrtPriceX96Final,
    mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
) external returns (int256, int256) {
    ...

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
                    uint128(longPremium.leftSlot())
                );

                //@audit always calculating the chunkKey of leg 0  
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

    return (collateralDelta0, collateralDelta1);
}
```

This issue means that the `settledTokens` accumulator will be updated incorrectly and will not include all the legs premium, as for each position only the first leg (index=0) is considered, this will result in funds losses for the options sellers and for the protocol.

### Impact

Wrong leg `chunkKey` calculation in `haircutPremia` will cause incorrect update of `settledTokens` accumulator and will result in funds losses for the options sellers and for the protocol.

### Tools Used

VS Code

### Recommended Mitigation

Use the correct leg index when calculating the leg `chunkKey` in `haircutPremia` function, the correct code should be:

```diff
function haircutPremia(
    address liquidatee,
    TokenId[] memory positionIdList,
    LeftRightSigned[4][] memory premiasByLeg,
    LeftRightSigned collateralRemaining,
    CollateralTracker collateral0,
    CollateralTracker collateral1,
    uint160 sqrtPriceX96Final,
    mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
) external returns (int256, int256) {
    ...

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
                    uint128(longPremium.leftSlot())
                );

                bytes32 chunkKey = keccak256(
                    abi.encodePacked(
--                      tokenId.strike(0),
--                      tokenId.width(0),
--                      tokenId.tokenType(0)
++                      tokenId.strike(leg),
++                      tokenId.width(leg),
++                      tokenId.tokenType(leg)
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

    return (collateralDelta0, collateralDelta1);
}
```

### Assessed type

Context

**[dyedm1 (Panoptic) confirmed and commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/374#issuecomment-2080183728):**
 > I will confirm this because we are fixing it, but I don't think high severity is justified here. The only impact is that *during liquidations*, premium paid by the liquidatee for legs other than 0 is effectively haircut/refunded to the liquidatee, which could result in an uneven distribution of the haircut and some premium that could have been safely paid being refunded to the liquidatee. Besides resulting in unfair distribution at liquidation time for sellers in the 2-3-4 chunks, no actor in the protocol actually loses funds (yield for sellers is not realized until it is settled anyway, so if they closed before the liquidation occurred they would get the exact same payment).

**[Picodes (judge) decreased severity to Medium and commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/374#issuecomment-2096327030):**
 > Giving Medium severity as this only concerns unrealized yield and happens during liquidations only.



***

## [[M-09] Removed liquidity can overflow when calling `SemiFungiblePositionManager.mintTokenizedPosition` function](https://github.com/code-423n4/2024-04-panoptic-findings/issues/363)
*Submitted by [rbserver](https://github.com/code-423n4/2024-04-panoptic-findings/issues/363)*

The following `mintTokenizedPosition` function eventually calls the `_createLegInAMM` function below.

<https://github.com/code-423n4/2024-04-panoptic/blob/855f58414589e93fa62e34890118164e8ac7822f/contracts/SemiFungiblePositionManager.sol#L504-L527>

```solidity
    function mintTokenizedPosition(
        TokenId tokenId,
        uint128 positionSize,
        int24 slippageTickLimitLow,
        int24 slippageTickLimitHigh
    )
        external
        ReentrancyLock(tokenId.poolId())
        returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
    {
        // create the option position via its ID in this erc1155
        _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);
        ...
        // validate the incoming option position, then forward to the AMM for minting/burning required liquidity chunks
        (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
            tokenId,
            positionSize,
            slippageTickLimitLow,
            slippageTickLimitHigh,
            MINT
        );
    }
```

The `_createLegInAMM` function increases the removed liquidity when minting a long position by executing `unchecked { removedLiquidity += chunkLiquidity }` in which the related code comment states that `we can't remove more liquidity than we add in the first place, so this can't overflow`. However, minting contracts of the short and long positions repeatedly can actually increase the removed liquidity to overflow `uint128`, which means that the `unchecked` block is unsafe. When such overflow occurs, the accounting for the removed liquidity and liquidity becomes incorrect; in this case, the overflowed removed liquidity becomes less than it should be, and burning such overflowed removed liquidity would increase the liquidity by an amount that is less than it should be.

<https://github.com/code-423n4/2024-04-panoptic/blob/855f58414589e93fa62e34890118164e8ac7822f/contracts/SemiFungiblePositionManager.sol#L958-L1104>

```solidity
    function _createLegInAMM(
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
        ...
        uint128 updatedLiquidity;
        uint256 isLong = tokenId.isLong(leg);
        LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache
        {
            ...
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

        ...
    }
```

### Proof of Concept

Please add the following test in `test\foundry\core\SemiFungiblePositionManager.t.sol`. This test will pass to demonstrate the described scenario.

```solidity
    function test_removedLiquidityOverflow() public {
        _initPool(0);

        _cacheWorldState(USDC_WETH_30);

        sfpm.initializeAMMPool(token0, token1, fee);

        int24 width = 4090;
        int24 strike = 0;

        populatePositionData(width, strike, 0, 0);

        uint128 psnSize = type(uint128).max / 70;

        TokenId shortTokenId = TokenId.wrap(0).addPoolId(poolId).addLeg(
            0,
            1,
            isWETH,
            0,
            0,
            0,
            strike,
            width
        );

        TokenId longTokenId = TokenId.wrap(0).addPoolId(poolId).addLeg(
            0,
            1,
            isWETH,
            1,
            0,
            0,
            strike,
            width
        );

        // repeatedly mint contracts of the short and long positions
        for (uint256 i = 0; i < 32311; i++) {
            sfpm.mintTokenizedPosition(
                shortTokenId,
                psnSize,
                TickMath.MIN_TICK,
                TickMath.MAX_TICK
            );

            sfpm.mintTokenizedPosition(
                longTokenId,
                psnSize,
                TickMath.MIN_TICK,
                TickMath.MAX_TICK
            );
        }

        accountLiquidities = sfpm.getAccountLiquidity(
            address(USDC_WETH_30),
            Alice,
            0,
            tickLower,
            tickUpper
        );

        // at this moment, the removed liquidity does not overflow uint128 yet
        uint128 accountLiquidities_leftSlot_before_overflow = accountLiquidities.leftSlot();
        assertLt(accountLiquidities_leftSlot_before_overflow, type(uint128).max);

        // mint contracts of the short and long positions for one more time
        sfpm.mintTokenizedPosition(
            shortTokenId,
            psnSize,
            TickMath.MIN_TICK,
            TickMath.MAX_TICK
        );

        sfpm.mintTokenizedPosition(
            longTokenId,
            psnSize,
            TickMath.MIN_TICK,
            TickMath.MAX_TICK
        );

        accountLiquidities = sfpm.getAccountLiquidity(
            address(USDC_WETH_30),
            Alice,
            0,
            tickLower,
            tickUpper
        );

        // the removed liquidity has overflowed uint128 since it is now less than its previous value
        assertLt(accountLiquidities.leftSlot(), accountLiquidities_leftSlot_before_overflow);
    }
```

### Recommended Mitigation Steps

[SemiFungiblePositionManager.sol#L1029-L1034](https://github.com/code-423n4/2024-04-panoptic/blob/855f58414589e93fa62e34890118164e8ac7822f/contracts/SemiFungiblePositionManager.sol#L1029-L1034) can be updated to the following code:

```solidity
                if (!isBurn) {
                    removedLiquidity += chunkLiquidity;
                }
```

### Assessed type

Under/Overflow

**[dyedm1 (Panoptic) confirmed](https://github.com/code-423n4/2024-04-panoptic-findings/issues/363#event-12629012028)**



***

# Low Risk and Non-Critical Issues

For this audit, 43 reports were submitted by wardens detailing low risk and non-critical issues. The [report highlighted below](https://github.com/code-423n4/2024-04-panoptic-findings/issues/568) by **DadeKuma** received the top score from the judge.

*The following wardens also submitted reports: [99Crits](https://github.com/code-423n4/2024-04-panoptic-findings/issues/573), [favelanky](https://github.com/code-423n4/2024-04-panoptic-findings/issues/560), [cheatc0d3](https://github.com/code-423n4/2024-04-panoptic-findings/issues/542), [slvDev](https://github.com/code-423n4/2024-04-panoptic-findings/issues/446), [bareli](https://github.com/code-423n4/2024-04-panoptic-findings/issues/421), [Rolezn](https://github.com/code-423n4/2024-04-panoptic-findings/issues/414), [hihen](https://github.com/code-423n4/2024-04-panoptic-findings/issues/395), [Dup1337](https://github.com/code-423n4/2024-04-panoptic-findings/issues/371), [Bauchibred](https://github.com/code-423n4/2024-04-panoptic-findings/issues/355), [0xStalin](https://github.com/code-423n4/2024-04-panoptic-findings/issues/346), [ZanyBonzy](https://github.com/code-423n4/2024-04-panoptic-findings/issues/273), [albahaca](https://github.com/code-423n4/2024-04-panoptic-findings/issues/210), [radin100](https://github.com/code-423n4/2024-04-panoptic-findings/issues/186), [Naresh](https://github.com/code-423n4/2024-04-panoptic-findings/issues/159), [grearlake](https://github.com/code-423n4/2024-04-panoptic-findings/issues/581), [rbserver](https://github.com/code-423n4/2024-04-panoptic-findings/issues/563), [d3e4](https://github.com/code-423n4/2024-04-panoptic-findings/issues/553), [zabihullahazadzoi](https://github.com/code-423n4/2024-04-panoptic-findings/issues/548), [Aymen0909](https://github.com/code-423n4/2024-04-panoptic-findings/issues/534), [John\_Femi](https://github.com/code-423n4/2024-04-panoptic-findings/issues/513), [lanrebayode77](https://github.com/code-423n4/2024-04-panoptic-findings/issues/490), [KupiaSec](https://github.com/code-423n4/2024-04-panoptic-findings/issues/473), [jasonxiale](https://github.com/code-423n4/2024-04-panoptic-findings/issues/439), [satoshispeedrunner](https://github.com/code-423n4/2024-04-panoptic-findings/issues/430), [CodeWasp](https://github.com/code-423n4/2024-04-panoptic-findings/issues/424), [sammy](https://github.com/code-423n4/2024-04-panoptic-findings/issues/370), [pfapostol](https://github.com/code-423n4/2024-04-panoptic-findings/issues/347), [Rhaydden](https://github.com/code-423n4/2024-04-panoptic-findings/issues/345), [blockchainbuttonmasher](https://github.com/code-423n4/2024-04-panoptic-findings/issues/325), [jesjupyter](https://github.com/code-423n4/2024-04-panoptic-findings/issues/322), [mining\_mario](https://github.com/code-423n4/2024-04-panoptic-findings/issues/320), [twcctop](https://github.com/code-423n4/2024-04-panoptic-findings/issues/300), [0xhacksmithh](https://github.com/code-423n4/2024-04-panoptic-findings/issues/295), [K42](https://github.com/code-423n4/2024-04-panoptic-findings/issues/285), [Topmark](https://github.com/code-423n4/2024-04-panoptic-findings/issues/284), [lsaudit](https://github.com/code-423n4/2024-04-panoptic-findings/issues/231), [lirezArAzAvi](https://github.com/code-423n4/2024-04-panoptic-findings/issues/163), [crc32](https://github.com/code-423n4/2024-04-panoptic-findings/issues/162), [codeslide](https://github.com/code-423n4/2024-04-panoptic-findings/issues/158), [oualidpro](https://github.com/code-423n4/2024-04-panoptic-findings/issues/135), [Sathish9098](https://github.com/code-423n4/2024-04-panoptic-findings/issues/71), and [IllIllI](https://github.com/code-423n4/2024-04-panoptic-findings/issues/14).*

## [L-01] Wrong median calculation

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

## [L-02] Some tokens do not consider `type(uint256).max` as an infinite approval

Some tokens such as [COMP](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L89-L91) downcast such approvals to uint96 and use that as a raw value rather than interpreting it as an infinite approval. Eventually these approvals will reach zero, at which point the calling contract will no longer function properly.

*There are 4 instances of this issue. (For in-depth details on this and all further low and non-critical items with multiple instances, see the warden's [full report](https://github.com/code-423n4/2024-04-panoptic-findings/issues/568).)*

---

## [L-03] Contracts use infinite approvals with no means to revoke

Infinite approvals on external contracts can be dangerous if the target becomes compromised. See [here](https://revoke.cash/exploits) for a list of approval exploits.  The following contracts are vulnerable to such attacks since they have no functionality to revoke the approval (call `approve` with amount `0`). Consider enabling the contract to revoke approval in emergency situations.

*There are 4 instances of this issue.*

---

## [L-04] File allows a version of solidity that is susceptible to `.selector`-related optimizer bug

In solidity versions prior to 0.8.21, there is a legacy code generation [bug](https://soliditylang.org/blog/2023/07/19/missing-side-effects-on-selector-access-bug/) where if `foo().selector` is called, `foo()` doesn't actually get evaluated. It is listed as low-severity, because projects usually use the contract name rather than a function call to look up the selector.

*There are 3 instances of this issue.*

---

## [L-05] Low level calls with Solidity before `0.8.14` result in an optimiser bug

The project contracts in scope are using low level calls with solidity version before 0.8.14 which can result in an [optimizer bug](https://medium.com/certora/overly-optimistic-optimizer-certora-bug-disclosure-2101e3f7994d).

> This bug causes the optimizer to consider some memory operations in inline assembly as being 'dead' and remove them.

> Later operations that would read the values written by these improperly removed memory operations will instead observe the old version of memory.

*There are 30 instances of this issue.*

---

## [L-06] Vulnerability to storage write removal

This bug was introduced in Solidity version 0.8.13, and it was fixed in version 0.8.17. This bug is significantly easier to trigger with optimized via-IR code generation, but can theoretically also occur in optimized legacy code generation. More info can be read in this [post](https://blog.soliditylang.org/2022/09/08/storage-write-removal-before-conditional-termination/).

*There are 30 instances of this issue.*

---

## [L-07] Functions calling contracts with transfer hooks are missing reentrancy guards

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks will open the users of this protocol up to read-only reentrancies with no way to protect against it, except by block-listing the whole protocol.

*There are 2 instances of this issue.*

---

## [L-08] Large approvals may not work with some `ERC20` tokens

Not all `IERC20` implementations are totally compliant, and some (e.g `UNI`, `COMP`) may fail if the valued passed to `approve` is larger than `uint96`. If the approval amount is `type(uint256).max`, which may cause issues with systems that expect the value passed to approve to be reflected in the allowances mapping.

*There are 4 instances of this issue.*

---

## [L-09] Initializers could be front-run

Initializers could be front-run, allowing an attacker to either set their own values, take ownership of the contract, and in the best case forcing a re-deployment.

*There are 2 instances of this issue.*

---

## [L-10] Array lengths not checked

If the length of the arrays are not required to be of the same length, user operations may not be fully executed.

*There are 4 instances of this issue.*

---

## [L-11] Possible division by 0 is not prevented

These functions can be called with 0 value in the input and this value is not checked for being bigger than 0, that means in some scenarios this can potentially trigger a division by zero.

*There are 2 instances of this issue.*

---

## [L-12] External calls in an unbounded loop can result in a DoS

Consider limiting the number of iterations in loops that make external calls, as just a single one of them failing will result in a revert.

*There are 22 instances of this issue.*

---

## [L-13] Solidity version `0.8.20` may not work on other chains due to `PUSH0`

In Solidity `0.8.20`'s compiler, the default target EVM version has been changed to Shanghai. This version introduces a new op code called `PUSH0`.

However, not all Layer 2 solutions have implemented this op code yet, leading to deployment failures on these chains. To overcome this problem, it is recommended to utilize an earlier EVM version.

*There are 20 instances of this issue.*

---

## [L-14] Use of `abi.encodePacked` with dynamic types inside `keccak256`

`abi.encodePacked` should not be used with dynamic types when passing the result to a hash function such as `keccak256`. Use `abi.encode` instead, which will pad items to 32 bytes, to [prevent any hash collisions](https://docs.soliditylang.org/en/latest/abi-spec.html#non-standard-packed-mode).

*There are 9 instances of this issue.*

---

## [L-15] Use `increaseAllowance/decreaseAllowance` instead of `approve/safeApprove`

Changing an allowance with `approve` brings the risk that someone may use both the old and the new allowance by unfortunate transaction ordering. Refer to [ERC20 API: An Attack Vector on the Approve/TransferFrom Methods](https://docs.google.com/document/d/1YLPtQxZu1UAvO9cZ1O2RPXBbT0mooh4DYKjA_jp-RLM/edit).

It is recommended to use the `increaseAllowance/decreaseAllowance` to avoid ths problem.

*There are 4 instances of this issue.*

---

## [N-01] Custom `error` should be used rather than `require`/`assert`

Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in try-catch blocks, and are easier to re-use and maintain.

*There are 9 instances of this issue.*

---

## [N-02] Use of `transfer` instead of `safeTransfer` is not recommended

It is good to add a `require` statement that checks the return value of token transfers, or to use something like OpenZeppelin's `safeTransfer`/`safeTransferFrom`, even if one is sure that the given token reverts in case of a failure.

This reduces the risk to zero even if these contracts are upgreadable, and it also helps with security reviews, as the auditor will not have to check this specific edge case.

*There are 2 instances of this issue.*

---

## [N-03] High cyclomatic complexity

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

*There are 33 instances of this issue.*

---

## [N-04] Missing events in sensitive functions

Events should be emitted when sensitive changes are made to the contracts, but some functions lack them.

*There are 8 instances of this issue.*

---

## [N-05] Missing events in initializers

As a best practice, consider emitting an event when the contract is initialized. In this way, it's easy for the user to track the exact point in time when the contract was initialized, by filtering the emitted events.

*There is 1 instance of this issue.*

```solidity
File: contracts/PanopticFactory.sol

135: 		    function initialize(address _owner) public {
```
[[135](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticFactory.sol#L135)]

---

## [N-06] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

*There are 4 instances of this issue.*

---

## [N-07] Setters should prevent re-setting the same value

Not only is wasteful in terms of gas, but this is especially problematic when an event is emitted and the old and new values set are the same, as listeners might not expect this kind of scenario.

*There are 6 instances of this issue.*

---

## [N-08] Using zero as a parameter

Taking zero as a valid argument without checks can lead to severe security issues in some cases.

If using a zero argument is mandatory, consider using descriptive constants or an enum instead of passing zero directly on function calls, as that might be error-prone, to fully describe the caller's intention.

*There are 63 instances of this issue.*

---

## [N-09] Unused named `return`

Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment.

This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

*There are 20 instances of this issue.*

---

## [N-10] Unused `error` definition

The following errors are never used, consider to remove them.

*There are 2 instances of this issue.*

---

## [N-11] Unused arguments should be removed or implemented

Some arguments are never used: if this is intentional, consider removing these arguments from the function. Otherwise, implement the missing logic accordingly.

*There are 8 instances of this issue.*

---

## [N-12] Unused state variables

Consider removing any unusued state variable to improve the readability of the codebase.

*There are 2 instances of this issue.*

---

## [N-13] OpenZeppelin libraries should be upgraded to a newer version

These contracts import some OpenZeppelin libraries, but they are using an old version.

*There are 5 instances of this issue.*

---

## [N-14] Same `constant` is redefined elsewhere

Keeping the same constants in different files may cause some problems, as the values could become out of sync when only one location is updated; reading constants from a single file is preferable. This should also be preferred for gas optimizations.

*There are 4 instances of this issue.*

---

## [N-15] Enum values should be used in place of constant array indexes

Consider using an enum instead of hardcoding an index access to make the code easier to understand.

*There are 26 instances of this issue.*

---

## [N-16] Variable initialization with zero value

It's not necessary to initialize a variable with a zero value, as it's the default behaviour, and it's actually worse in gas terms as it adds an overhead.

*There are 31 instances of this issue.*

---

## [N-17] Duplicated `require/if` statements should be refactored

These statements should be refactored to a separate function, as there are multiple parts of the codebase that use the same logic, to improve the code readability and reduce code duplication.

*There are 5 instances of this issue.*

---

## [N-18] Inconsistent usage of `require`/`error`

Some parts of the codebase use `require` statements, while others use custom `error`s. Consider refactoring the code to use the same approach: the following findings represent the minority of `require` vs `error`, and they show the first occurance in each file, for brevity.

*There is 1 instance of this issue.*

```solidity
File: contracts/libraries/Math.sol

361: 		                require(denominator > 0);
```
[[361](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Math.sol#L361)]

---

## [N-19] Some functions contain the same exact logic

These functions might be a problem if the logic changes before the contract is deployed, as the developer must remember to syncronize the logic between all the function instances.

Consider using a single function instead of duplicating the code, for example by using a `library`, or through inheritance.

*There are 2 instances of this issue.*

---

## [N-20] Unbounded loop may run out of gas

Consider limiting the number of iterations in loops with an explicit revert reason to avoid iterating an array that is too large.

The function would eventually revert if out of gas anyway, but by limiting it the user avoids wasting too much gas, as the loop doesn't execute if an excessive value is provided.

*There are 34 instances of this issue.*

---

## [N-21] Public functions not called internally

Those functions should be declared as `external` instead of `public`, as they are never called internally by the contract.

Contracts are allowed to override their parents' functions and change the visibility from external to public.

*There are 13 instances of this issue.*

---

## [N-22] Large multiples of ten should use scientific notation

Use a scientific notation rather than decimal literals (e.g. `1e6` instead of `1000000`), for better code readability.

*There are 7 instances of this issue.*

---

## [N-23] Use of exponentiation instead of scientific notation

Use a scientific notation rather than exponentiation (e.g. `1e18` instead of `10**18`): although the compiler is capable of optimizing it, it is considered good coding practice to utilize idioms that don't rely on compiler optimization, whenever possible.

*There is 1 instance of this issue.*

```solidity
File: contracts/CollateralTracker.sol

234: 		        totalSupply = 10 ** 6;
```
[[234](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L234)]

---

## [N-24] Missing/malformed underscores for large numeric literals

Large hardcoded numbers in code can be difficult to read. Consider using underscores for number literals to improve readability (e.g `1234567` -> `1_234_567`). Consider using an underscore for every third digit from the right.

*There are 5 instances of this issue.*

---

## [N-25] Avoid complex casting

Consider refactoring the following code, as double casting is confusing, and, in some scenarios, it may introduce unexpected truncations or rounding issues.

Furthermore, double type casting can make the code less readable and harder to maintain, increasing the likelihood of errors and misunderstandings during development and debugging.

*There are 67 instances of this issue.*

---

## [N-26] Consider using the `using-for` syntax

The `using-for` [syntax](https://docs.soliditylang.org/en/latest/contracts.html#using-for) is the more common way of calling library functions.

*There are 460 instances of this issue.*

---

## [N-27] Consider making contracts `Upgradeable`

This allows for bugs to be fixed in production, at the expense of **significantly** increasing centralization.

*There are 20 instances of this issue.*

---

## [N-28] Dependence on external protocols

External protocols should be monitored as such dependencies may introduce vulnerabilities if a vulnerability is found in the external protocol.

*There are 19 instances of this issue.*

---

## [N-29] Debug imports in production code

Remove debug imports, as they increase the contract size, and they are useful only for local tests.

*There is 1 instance of this issue.*

```solidity
File: contracts/PanopticPool.sol

22: 		import "forge-std/console.sol";
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L22)]

---

## [N-30] `2**<n> - 1` should be re-written as `type(uint<n>).max`

Earlier versions of solidity can use `uint<n>(-1)` instead. Expressions not including the `- 1` can often be re-written to accomodate the change (e.g. by using a `>` rather than a `>=`, which will also save some gas).

*There are 44 instances of this issue.*

---

## [N-31] Use of non-named numeric constants

Constants should be defined instead of using magic numbers.

*There are 285 instances of this issue.*

---

## [N-32] Consider splitting complex checks into multiple steps

Assign the expression's parts to intermediate local variables, and check against those instead.

*There are 23 instances of this issue.*

---

## [N-33] Complex math should be split into multiple steps

Consider splitting long arithmetic calculations into multiple steps to improve the code readability.

*There are 53 instances of this issue.*

---

## [N-34] Time related variables should use time units instead of numbers

There are [units](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#time-units) for seconds, minutes, hours, days, and weeks, and since they're defined, they should be used

*There are 3 instances of this issue.*

---

## [N-35] Control structures do not comply with best practices

This is a [best practice](https://docs.soliditylang.org/en/latest/style-guide.html#control-structures) that should be followed. 

*There are 120 instances of this issue.*

---

## [N-36] Use a single file for system wide constants

Consider grouping all the system constants under a single file. This finding shows only the first constant for each file, for brevity.

*There are 10 instances of this issue.*

---

## [N-37] Old Solidity version

Use a more recent version of Solidity: it's safer to use at least the version 0.8.19 to get the latest bugfixes and features when deploying on L2.

*There are 20 instances of this issue.*

---

## [N-38] Use of floating pragma

Locking the pragma helps avoid accidental deploys with an outdated compiler version that may introduce bugs and unexpected vulnerabilities.

Floating pragma is meant to be used for libraries and contracts that have external users and need backward compatibility.

*There are 9 instances of this issue.*

---

## [N-39] No checks for empty bytes

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

## [N-40] Use of `abi.encodePacked` instead of `bytes.concat`

Starting from version `0.8.4`, the recommended approach for appending bytes is to use `bytes.concat` instead of `abi.encodePacked`.

*There are 5 instances of this issue.*

---

## [N-41] Contract functions should use an `interface`

All `external`/`public` functions should override an `interface`. This is useful to make sure that the whole API is extracted.

*There are 85 instances of this issue.*

---

## [N-42] `require`/`revert` without any message

If a transaction reverts, it can be confusing to debug if there aren't any messages. Add a descriptive message to all `require`/`revert` statements.

*There are 9 instances of this issue.*

---

## [N-43] `else` block is not required

Consider moving the logic outside the `else` block, and then removing it (it's not required, as the function is returning a value). There will be one less level of nesting, which will improve the quality of the codebase.

*There are 5 instances of this issue.*

---

## [N-44] Multiple `address`/ID mappings can be combined into a single mapping of an `address`/ID to a `struct`, for readability

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related.

*There are 4 instances of this issue.*

---

## [N-45] Lack of specific `import` identifier

It is better to use `import {<identifier>} from "<file.sol>"` instead of `import "<file.sol>"` to improve readability and speed up the compilation time.

*There is 1 instance of this issue.*


```solidity
File: contracts/PanopticPool.sol

22: 		import "forge-std/console.sol";
```
[[22](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/PanopticPool.sol#L22)]


---

## [N-46] Imports should be organized more systematically

The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

*There are 4 instances of this issue.*

---

## [N-47] Long bitmasks are hard to read

Consider using bitshifts instead of a bitmap if the value is a power of 2 and the variable is constant, to improve the code readability.

*There is 1 instance of this issue.*


```solidity
File: contracts/libraries/Constants.sol

10: 		    uint256 internal constant FP96 = 0x1000000000000000000000000;
```
[[10](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/libraries/Constants.sol#L10)]


---

## [N-48] Use a struct to encapsulate multiple function parameters

If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

*There are 42 instances of this issue.*

---

## [N-49] Event is missing `msg.sender` parameter

The following functions are missing some parameters when emitting an event: when dealing with a source address which uses the value of `msg.sender`, the `msg.sender` value should be specified in every event.

Otherwise, a contract or web page listening to events cannot react to connected users: basically, those events cannot be used properly.

*There are 9 instances of this issue.*

---

## [N-50] Events should emit both new and old values

Events are generally emitted when sensitive changes are made to the contracts.

However, some are missing important parameters, as they should include both the new value and old value where possible.

*There are 2 instances of this issue.*

---

## [N-51] Events may be emitted out of order due to reentrancy

If a reentrancy occurs, some events may be emitted in an unexpected order, and this may be a problem if a third party expects a specific order for these events. Ensure that events follow the best practice of CEI.

*There are 8 instances of this issue.*

---

## [N-52] Use of polymorphism is discouraged for security audits

A duplicated function name in the same contract might have problems with automated auditing tools, so it should be avoided. Consider always using a different name for functions to improve the readability of the code.

*There are 15 instances of this issue.*

---

## [N-53] Avoid external calls in modifiers

It is unusual to have external calls in modifiers, and doing so will make reviewers more likely to miss important external interactions. Consider moving the external call to an internal function, and calling that function from the modifier.

*There is 1 instance of this issue.*


```solidity
File: contracts/CollateralTracker.sol

170: 		        if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();
```
[[170](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L170)]


---

## [N-54] Custom `error` without details

Consider adding some parameters to the error to indicate which user or values caused the failure.

*There are 34 instances of this issue.*

---

## [N-55] Don't use uppercase for non `constant`/`immutable` variables

Variables which are not constants or immutable should **not** be declared in all uppercase.

*There are 2 instances of this issue.*

---

## [N-56] Constants in comparisons should appear on the left side

This is useful to avoid doing some [typo bugs](https://www.moserware.com/2008/01/constants-on-left-are-better-but-this.html).

*There are 119 instances of this issue.*

---

## [N-57] Consider using `delete` instead of assigning zero/false to clear values

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

*There are 5 instances of this issue.*

---

## [N-58] Consider disallowing transfers to `address(this)`

Consider preventing a contract's tokens from being transferred to the contract itself.

*There are 3 instances of this issue.*

---

## [N-59] Use a ternary statement instead of `if`/`else` when appropriate

The `if`/`else` statement can be written in a shorthand way using the ternary operator, as it increases readability and reduces the number of lines of code.

*There are 3 instances of this issue.*

---

## [N-60] Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is ideal for named returns.

*There are 103 instances of this issue.*

---

## [N-61] Layout order does not comply with best practices

This is a [best practice](https://docs.soliditylang.org/en/latest/style-guide.html#order-of-layout) that should be followed.

Inside each contract, library or interface, use the following order:

1. Type declarations
2. State variables
3. Events
4. Errors
5. Modifiers
6. Functions

*There are 6 instances of this issue.*

---

## [N-62] Function visibility order does not comply with best practices

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

---

## [N-63] Long functions should be refactored into multiple functions

Consider splitting long functions into multiple, smaller functions to improve the code readability.

*There are 33 instances of this issue.*

---

## [N-64] Consider moving duplicated strings to constants

This will decrease the probability of making typos, and the code will be more readable

*There are 5 instances of this issue.*

---

## [N-65] Lines are too long

Maximum suggested line length is 120 characters according to the [documentation](https://docs.soliditylang.org/en/latest/style-guide.html#maximum-line-length).

*There are 346 instances of this issue.*

---

## [N-66] Some variables have a implicit default visibility

Consider always adding an explicit visibility modifier for variables, as the default is `internal`.

*There are 8 instances of this issue.*

---

## [N-67] Consider adding a block/deny-list

This can help to prevent hackers from using stolen tokens, but as a side effect it will increase the project centralization.

*There are 3 instances of this issue.*

---

## [N-68] Use of `override` is unnecessary

Starting with Solidity version [0.8.8](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding), using the override keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.

*There are 4 instances of this issue.*

---

## [N-69] Missing variable names

Consider adding a comment with the variable name even if it's not used, to improve the code readability.

*There are 2 instances of this issue.*

---

## [N-70] Typos in comments

Avoid typos, and proper nouns should be capitalized.

*There are 86 instances of this issue.*

---

## [N-71] Contracts should have full test coverage

A 100% test coverage is not foolproof, but it helps immensely in reducing the amount of bugs that may occur.

---

## [N-72] Large or complicated code bases should implement invariant tests

This includes: large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts.

Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold.

Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers may help significantly.

---

## [N-73] Codebase should implement formal verification testing

Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).

---

## [N-74] Inconsistent spacing in comments

Some lines use `// x` and some use `//x`. The instances below point out the usages that don't follow the majority, within each file.

*There are 105 instances of this issue.*

---

## [N-75] State variables should include comments

Consider adding some comments on critical state variables to explain what they are supposed to do: this will help for future code reviews.

*There are 3 instances of this issue.*

---

## [N-76] Complex functions should have explicit comments

Large and/or complex functions should have more comments to better explain the purpose of each logic step.

*There are 24 instances of this issue.*

---

## [N-77] Assembly code should have explicit comments

Low-level languages like assembly should require extensive documentation and comments to clarify the purpose of each instruction.

*There are 3 instances of this issue.*

---

## [N-78] Use `@inheritdoc` for overridden functions

`@inheritdoc` Copies all missing tags from the base function. [Documentation](https://docs.soliditylang.org/en/latest/natspec-format.html#tags)

*There are 4 instances of this issue.*

---

## [N-79] Modifier names don't follow the Solidity naming convention

Use mixedCase. Examples: `onlyBy, onlyAfter, onlyDuringThePreSale`. [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#modifier-names)

*There is 1 instance of this issue.*


```solidity
File: contracts/SemiFungiblePositionManager.sol

305: 		    modifier ReentrancyLock(uint64 poolId) {
```
[[305](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/SemiFungiblePositionManager.sol#L305)]


---

## [N-80] Variable names don't follow the Solidity naming convention

Use `mixedCase` for local and state variables that are not constants, and add a trailing underscore for non-external variables. [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#local-and-state-variable-names)

*There are 52 instances of this issue.*

---

## [N-81] Missing underscore prefix for non-external functions

This convention is suggested for non-external functions (private or internal). [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

*There are 104 instances of this issue.*

---

## [N-82] Missing underscore prefix for non-external variables

This convention is suggested for non-external state variables (private or internal). [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables)

*There are 36 instances of this issue.*

---

## [N-83] Invalid NatSpec comment style

NatSpec [must](https://docs.soliditylang.org/en/latest/natspec-format.html#documentation-example) begin with `///`, or use the `/* ... */` syntax.

*There are 3 instances of this issue.*

---

## [N-84] Missing NatSpec from contract declarations

Some contracts miss a `@dev/@notice` NatSpec, which should be a [best practice](https://docs.soliditylang.org/en/latest/natspec-format.html) to add as a documentation.

*There is 1 instance of this issue.*


```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: 		interface IDonorNFT {
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6)]


---

## [N-85] Missing NatSpec `@author` from contract declaration

Some contract definitions have an incomplete NatSpec: add a `@author` notation to improve the code documentation.

*There is 1 instance of this issue.*


```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

6: 		interface IDonorNFT {
```
[[6](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/tokens/interfaces/IDonorNFT.sol#L6)]


---

## [N-86] Missing NatSpec `@dev` from contract declaration

Some contract definitions have an incomplete NatSpec: add a `@dev` notation to describe the contract to improve the code documentation.

*There are 11 instances of this issue.*

---

## [N-87] Missing NatSpec `@notice` from contract declaration

Some contract definitions have an incomplete NatSpec: add a `@notice` notation to describe the contract to improve the code documentation.

*There are 5 instances of this issue.*

---

## [N-88] Missing NatSpec `@title` from contract declaration

Some contract definitions have an incomplete NatSpec: add a `@title` notation to describe the contract to improve the code documentation.

*There are 2 instances of this issue.*

---

## [N-89] Missing NatSpec `@dev` from error declaration

Some errors have an incomplete NatSpec: add a `@dev` notation to describe the error to improve the code documentation.

*There are 33 instances of this issue.*

---

## [N-90] Missing NatSpec `@param` from error declaration

Some errors have an incomplete NatSpec: add a `@param` notation to describe the error parameters to improve the code documentation.

*There are 34 instances of this issue.*

---

## [N-91] Missing NatSpec `@dev` from event declaration

Some events have an incomplete NatSpec: add a `@dev` notation to describe the event to improve the code documentation.

*There are 11 instances of this issue.*

---

## [N-92] Missing NatSpec `@dev` from modifier declaration

Some modifiers have an incomplete NatSpec: add a `@dev` notation to describe the modifier to improve the code documentation.

*There is 1 instance of this issue.*


```solidity
File: contracts/CollateralTracker.sol

169: 		    modifier onlyPanopticPool() {
```
[[169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L169)]


---

## [N-93] Missing NatSpec `@param` from modifier declaration

Some modifiers have an incomplete NatSpec: add a `@param` notation to describe the modifier parameters to improve the code documentation.

*There is 1 instance of this issue.*


```solidity
File: contracts/CollateralTracker.sol

169: 		    modifier onlyPanopticPool() {
```
[[169](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/CollateralTracker.sol#L169)]


---

## [N-94] Missing NatSpec `@dev` from function declaration

Some functions have an incomplete NatSpec: add a `@dev` notation to describe the function to improve the code documentation.

*There are 142 instances of this issue.*

---

## [N-95] Missing NatSpec `@notice` from function declaration

Some functions have an incomplete NatSpec: add a `@notice` notation to describe the function to improve the code documentation.

*There are 3 instances of this issue.*

---

## [N-96] Missing NatSpec `@param` from function declaration

Some functions have an incomplete NatSpec: add a `@param` notation to describe the function parameters to improve the code documentation.

*There are 19 instances of this issue.*

---

## [N-97] Incomplete NatSpec `@return` from function declaration

Some functions have an incomplete NatSpec: add a `@return` notation to describe the function return value to improve the code documentation.

*There are 8 instances of this issue.*

---

## [N-98] Some parts of the codebase contain unreachable code

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

## [N-99] Lack of deadline when swapping

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

## [N-100] `approve` will always revert as the `IERC20` interface mismatch

Some tokens, such as [USDT](https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7#code#L199), have a different implementation for the approve function: when the address is cast to a compliant `IERC20` interface and the approve function is used, it will always revert due to the interface mismatch.

*There are 4 instances of this issue.*

---

## [N-101] Return values of `approve` not checked

Not all `IERC20` implementations (e.g. USDT, KNC) `revert` when there's a failure in `approve`. The function signature has a boolean return value and they indicate errors that way instead.

By not checking the return value, operations that should have marked as failed, may potentially go through without actually approving anything.

*There are 4 instances of this issue.*

---

## [N-102] Using `delegatecall` inside a loop may cause issues with `payable` functions

If one of the `delegatecall` consumes part of the `msg.value`, other calls might fail, if they expect the full `msg.value`. Consider using a different design, or fully document this decision to avoid potential issues.

*There is 1 instance of this issue.*

```solidity
File: contracts/multicall/Multicall.sol

15: 		            (bool success, bytes memory result) = address(this).delegatecall(data[i]);
```
[[15](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L15)]

---

## [N-103] Missing checks in constructor/initialize

There are some missing checks in these functions, and this could lead to unexpected scenarios. Consider always adding a sanity check for state variables.

*There are 2 instances of this issue.*

---

## [N-104] Missing checks for state variable assignments

There are some missing checks in these functions, and this could lead to unexpected scenarios. Consider always adding a sanity check for state variables.

*There are 23 instances of this issue.*

---

## [N-105] `payable` function does not transfer ETH

The following functions can be called by any user, who may also send some funds by mistake. In that case, those funds will be lost (this also applies to delegatecalls, in case they don't use the transferred ETH).

*There is 1 instance of this issue.*

```solidity
File: contracts/multicall/Multicall.sol

12: 		    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
[[12](https://github.com/code-423n4/2024-04-panoptic/blob/6908144756ef0cce2ede6d3b2013291f0ddd74ec/contracts/multicall/Multicall.sol#L12)]

---

## [N-106] Missing limits when setting min/max amounts

There are some missing limits in these functions, and this could lead to unexpected scenarios. Consider adding a min/max limit for the following values, when appropriate.

*There are 2 instances of this issue.*

---

## [N-107] Loss of precision on division

Solidity doesn't support fractions, so divisions by large numbers could result in the quotient being zero.

To avoid this, it's recommended to require a minimum numerator amount to ensure that it is always greater than the denominator.

*There are 35 instances of this issue.*

---

## [N-108] Using a vulnerable dependency from some libraries

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

---

## [N-109] Missing checks for `address(0)` in constructor/initializers

Check for zero-address to avoid the risk of setting `address(0)` for state variables when deploying.

*There are 9 instances of this issue.*

---

## [N-110] Missing checks for `address(0)` when updating state variables

Check for zero-address to avoid the risk of setting `address(0)` for state variables after an update.

*There are 20 instances of this issue.*

---

**[Picodes (judge) commented](https://github.com/code-423n4/2024-04-panoptic-findings/issues/568#issuecomment-2096433011):**
 > Flagging as best as this is the best mix of custom issues and automated findings I've seen so to me it brings the most value.
> 
> The following issues from this warden have also been considered in scoring and should be considered valid Low findings:
> - [Median is not updated when burning a position, which can result in an inaccurate solvency check](https://github.com/code-423n4/2024-04-panoptic-findings/issues/540)
> - [`PanopticFactory` can be bricked and become unusable](https://github.com/code-423n4/2024-04-panoptic-findings/issues/523)



***

# Disclosures

C4 is an open organization governed by participants in the community.

C4 audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
