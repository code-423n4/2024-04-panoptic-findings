# QA Report for Panoptic

## Table of Contents

| Issue ID | Description |
| -------- | ----------- |
| [QA-01](#qa-01-no-check-for-active-sequencer-on-l2s) | No check for active sequencer on L2s |
| [QA-02](#qa-02-a-malicious-user-can-grief-attempts-of-transfers-in-panoptic) | A malicious user can grief attempts of transfers in Panoptic |
| [QA-03](#qa-03-introduce-a-functionality-to-reset-s_accountfeesbase-as-a-user-can-currently-not-receive-sfpm-tokens-when-s_accountfeesbase-!=-0-which-might-not-be-in-their-control) | Introduce a functionality to reset `s_accountFeesBase` as a user can currently not receive `SFPM` tokens when `s_accountFeesBase != 0` which might not be in their control |
| [QA-04](#qa-04-cei-is-not-being-followed-in-minttokenizedposition()-makes-execution-susceptible-to-reentrancy) | CEI is not being followed in `mintTokenizedPosition()`, makes execution susceptible to reentrancy |
| [QA-05](#qa-05-uniswap-oracle-should-not-be-used-as-a-source-of-pricing-on-l2s) | Uniswap oracle should not be used as a source of pricing on L2s |
| [QA-06](#qa-06-fix-documentation-_(multiple-instances)_) | Fix documentation _(multiple instances)_ |
| [QA-07](#qa-07-important-addresses-should-be-changed-in-a-two-step-format) | Important addresses should be changed in a two-step format |
| [QA-08](#qa-08-user-should-not-be-allowed-to-liquidate-themselves) | User should not be allowed to liquidate themselves |
| [QA-09](#qa-09-collateraltracker.sol-is-not-compatible-with-erc-4626) | `Collateraltracker.sol` is not compatible with ERC-4626 |
| [QA-10](#qa-10-_getsolvencybalances()-should-round-up-for-both-balancecross-&-thresholdcross-or-round-down-for-both) | `_getSolvencyBalances()` should round up for both `balanceCross` & `thresholdCross` or round down for both |
| [QA-11](#qa-11-fix-typos-_(multiple-instances)_) | Fix typos _(multiple instances)_ |
| [QA-12](#qa-12-current-pool-id-thats-gotten-is-way-less-unique) | Current Pool id that's gotten is way less unique |
| [QA-13](#qa-13-uniswaps-callback-return-value-should-be-checked) | Uniswap's callback return value should be checked |
| [QA-14](#qa-14-consider-just-calling-the-functions-on-a-low-level-instead-of-not-taking-the-failures-into-account) | Consider just calling the functions on a low level instead of not taking the failures into account |
| [QA-15](#qa-15-consider-introducing-a-functionality-to-update-vegoid) | Consider introducing a functionality to update `VEGOID` |
| [QA-16](#qa-16-erc1155minimal.sol-does-not-comply-with-the-eip-1155-token-standard) | `ERC1155Minimal.sol` does not comply with the EIP-1155 Token standard |
| [QA-17](#qa-17-incorrect-calculations-in-convert0to1()&-convert1to0()) | Incorrect calculations in `convert0to1()`& `convert1to0()` |
| [QA-18](#qa-18-erc1155minimalsafebatchtransferfrom()-should-verify-the-length-of-ids-and-amounts-as-is-done-in-the-eip) | `ERC1155Minimal::safeBatchTransferFrom()` should verify the length of ids and amounts as is done in the EIP |
| [QA-19](#qa-19-erc20.sols-minting-doesnt-follow-cei) | `ERC20.sol`'s minting doesn't follow CEI |
| [QA-20](#qa-20-swapping-attempts-could-end-up-being-partial-due-to-usage-of-sqrtpricex96) | Swapping attempts could end up being partial due to usage of `sqrtPriceX96` |
| [QA-21](#qa-21-eth-could-get-stuck-in-semifungiblepositionmanager-due-to-an-inheritance-overlap) | Eth could get stuck in `SemiFungiblePositionManager` due to an inheritance overlap |
| [QA-22](#qa-22-no-deadline-check-for-uniswap-amm-causes-transactions-to-be-potentially-maliciously-executed) | No deadline check for Uniswap AMM causes transactions to be potentially maliciously executed |
| [QA-23](#qa-23-protocols-collected-and-written-position-data-could-be-flawed) | Protocol's collected and written position data could be flawed |
| [QA-24](#qa-24-closing-a-long-position-in-some-instances-wouldnt-work-due-to-uniswaps-tickspacingtomaxliquiditypertick-limitation) | Closing a long position in some instances wouldn't work due to Uniswap's `tickSpacingToMaxLiquidityPerTick` limitation |
| [QA-25](#qa-25-math.muldiv()-does-not-explicitly-check-that-denominator-!=-0) | `Math.mulDiv()` does not explicitly check that `denominator != 0` |
| [QA-26](#qa-26-consider-depleting-allowances-in-all-instances-of-transfers) | Consider depleting allowances in all instances of transfers |
| [QA-27](#qa-27-math.getamount0forliquidity()-could-cause-a-break-up-in-accounting-data-due-to-precision-loss) | `Math.getAmount0ForLiquidity()` could cause a break up in accounting data due to precision loss |
| [QA-28](#qa-28-excessive-usage-of-floating-pragma-should-be-curbed) | Excessive usage of floating pragma should be curbed |

## QA-01 No check for active sequencer on L2s

The protocol does not check whether the L2 sequencer is active when minting or burning positions. This can result in outdated trades and incorrect premia calculations and exercising options that unexpectedly becomes out of the money

https://github.com/code-423n4/2023-11-panoptic/blob/aa86461c9d6e60ef75ed5a1fe36a748b952c8666/contracts/SemiFungiblePositionManager.sol#L510-L518

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1060-L1067 from `PanopticPool.liquidate()`

```solidity
            (uint256 balanceCross, uint256 thresholdCross) = _getSolvencyBalances(
                tokenData0,
                tokenData1,
                Math.getSqrtRatioAtTick(twapTick)
            );

            if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();
        }

```

This is the check that's been applied to see if a user is liquidatable or not, i.e `tokenData0` & `tokenData1` is goten [from the previous queries to get the account margin details](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1048-L1060) with the price from the collateral trackers for both tokens.

Problem is that protocol have clearly stated that they would deploy to multiple EVM compatible chain from here: https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/README.md#L242

```markdown
| Chains the protocol will be deployed on | Ethereum, Arbitrum, Avax, Base, BSC, Optimism ,Polygon |
```

The above list includes different L2s, that heavily rely on the sequencer, but evidently no sequencer hecks are present in protocol, this leads to a scenario where if the sequencer ever goes down and comes back up users wouldn't have enough time to get their positions back afloat since all price updates would be immediately consumed after the sequencer comes back up (note that while the sequencer is down users can't really deposit in more capital to keep their positions afloat), this now causes their positions to be immediately unfairly liquidatable.

### Impact

> Borderline medium/low

Users could be unfairly liquidated since they do not have enough ample time to return their positions back afloat after the sequencer goes off.

### Recommended Mitigation Steps

Introduce L2 sequencer checks and provide a grace period for users if the sequencer ever goes down to keep their positions afloat.

## QA-02 A malicious user can grief attempts of transfers in Panoptic

### Proof of Concept

Protocol implements a subtle invariant that in order for a user to receive options they must not yet have one.

However this just allows a user with malicious intent to break this logic as they can just front run any transfer of options by transferring an option of their own, now since there is no `minAmount` to buy this means that this attack could actually be done for very minute amount of funds.

### Impact

Borderline low/medium as this can be looked at as `the function of the protocol or its availability could be impacted` which is [`medium` on C4.](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization). Since this means that in this case User B now no longer has access to receive tokens

> Consider upgrading if applicable.

### Recommended Mitigation Steps

Consider having a `minAmount` logic when buying options, that way this attack gets way more expensive.

## QA-03 Introduce a functionality to reset `s_accountFeesBase` as a user can currently not receive `SFPM` tokens when `s_accountFeesBase != 0` which might not be in their control

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L593-L594

```solidity
    function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {
        //(..snip)
                    // Revert if recipient already has that position
            if (
                (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
                (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)
            ) revert Errors.TransferFailed();
        //(..snip)

}

```

Evidently the user cannot receive SFPM tokens when `s_accountFeesBase` is not 0.

Consider this minimalistic POC:

User A transfers `SFPM` tokens to User B. After a while, User B consumes these `SFPM` tokens reducing the liquidity to `0`. Later on User A tries to mint the same SFPM tokens and send them back to User B. However, this action fails because User B's `s_accountFeesBase` is not zero.

### Impact

Borderline low/medium as this can even be looked at as `the function of the protocol or its availability could be impacted` which is [`medium` on C4.](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization). Since this means that in this case User B now no longer has access to receive tokens

### Recommended Mitigation Steps

Introduce an admin backed function to set `s_accountFeesBase` to 0 when there is no liquidity.

## QA-04 CEI is not being followed in `mintTokenizedPosition()`, makes execution susceptible to reentrancy

### Proof of Concept

First take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L215-L231

```solidity
    function _mint(address to, uint256 id, uint256 amount) internal {
        // balance will never overflow
        unchecked {
            balanceOf[to][id] += amount;
        }

        emit TransferSingle(msg.sender, address(0), to, id, amount);

        if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
                ERC1155Holder.onERC1155Received.selector
            ) {
                revert UnsafeRecipient();
            }
        }
    }
```

This is the internal utility to mint tokens to a user's account (could be an EOA/or an SC), evidently in the case where this receiver is a smart contract, there is a check to ensure the contract supports ERC1155, by using the `onERC1155Received()` callback, note that in this instance the execution is already in the control of the account so they can attach any custom logic.

Now see https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L504-L528

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

        emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);

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

This function is used to new positions for the `tokenId`, erroneously it doesn't follow the CEI pattern, it first mints the position and then checks if the execution is valid via `_validateAndForwardToAMM()`.

Now going to the implementation of [SemiFungiblePositionManager.\_validateAndForwardToAMM()](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L680-L730), we can see that multiple checks exist here, including that of [checking that the pool exists](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L698-L703).

The above flow path means that anyone with/without malicious intent can just call `mintTokenizedPosition()` and then using the `onERC1155Received()` callback to reenter the function and execute any custom data they want before the validations take place.

### Impact

The `mintTokenizedPosition()` function is vulnerable to a classic reentrancy as an attacker can reenter it while the position is being minted and execute any custom logic.

### Recommended Mitigation Steps

Consider validating the position before minting it.

## QA-05 Uniswap oracle should not be used as a source of pricing on L2s

### Proof of Concept

Protocol heavily relies on Uniswap V3 oracles as source of pricing data, also protocol have clearly stated that they would deploy to multiple EVM compatible chain from here: https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/README.md#L242

```markdown
| Chains the protocol will be deployed on | Ethereum, Arbitrum, Avax, Base, BSC, Optimism ,Polygon |
```

However this quoted [statement](https://docs.uniswap.org/concepts/protocol/oracle#oracles-integrations-on-layer-2-rollups) made from the Uniswap team is regarding integration on L2 Optimism, where every transaction is a different block, however, it is also valid for Arbitrum, as the average block time on Arbitrum is ~0.25s.

> ### Oracles Integrations on Layer 2 Rollups
>
> Optimism
> On Optimism, every transaction is confirmed as an individual block. The block.timestamp of these blocks, however, reflect the block.timestamp of the last L1 block ingested by the Sequencer. For this reason, Uniswap pools on Optimism are not suitable for providing oracle prices, as this high-latency block.timestamp update process makes the oracle much less costly to manipulate. In the future, it's possible that the Optimism block.timestamp will have much higher granularity (with a small trust assumption in the Sequencer), or that forced inclusion transactions will improve oracle security. For more information on these potential upcoming changes, please see the [Optimistic Specs repo](https://github.com/ethereum-optimism/optimistic-specs/discussions/23). **For the time being, usage of the oracle feature on Optimism should be avoided.**

### Impact

> Borderline medium/low

The above means that easily manipulated oracle prices could be ingested, leading to multiple cases, for e.g liquidations might now no longer go through cause the [MAX_TWAP_DELTA_LIQUIDATION](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L156) check below from attempts at liquidation could now cause often reverts if the price data has been manipulated, i.e https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1034-L1037

```solidity
            // Enforce maximum delta between TWAP and currentTick to prevent extreme price manipulation
            if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)
                revert Errors.StaleTWAP();


```

### Recommendation

Consider not completely relying on Uniswap's oracle on L2s like Optimism/Arbitrum for the time being.

## QA-06 Fix documentation _(multiple instances)_

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L138-L145

```solidity
    // base collateral ratios
    /// @notice Required collateral ratios for buying, represented as percentage * 10_000.
    /// i.e 20% -> 0.2 * 10_000 = 2_000.
    uint256 immutable SELLER_COLLATERAL_RATIO;

    /// @notice Required collateral ratios for selling, represented as percentage * 10_000.
    /// i.e 10% -> 0.1 * 10_000 = 1_000.
    uint256 immutable BUYER_COLLATERAL_RATIO;
```

The comments around both variables should be swapped as the explanation for `SELLER_COLLATERAL_RATIO` is actually for `BUYER_COLLATERAL_RATIO` and vice versa.

- Another instance can be seen here https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L291-L296

```solidity
    /// @dev mapping that stores a LeftRight packing of feesBase of  keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))
    /// @dev Base fees is stored as int128((feeGrowthInside0LastX128 * liquidity) / 2**128), which allows us to store the accumulated fees as int128 instead of uint256
    /// @dev Right slot: int128 token0 base fees, Left slot: int128 token1 base fees.
    /// feesBase represents the baseline fees collected by the position last time it was updated - this is recalculated every time the position is collected from with the new value
    mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;

```

The line `    /// @dev mapping that stores a LeftRight packing of feesBase of  keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))` is misleading, cause navigating to the actual implementation of the data that is being encoded we can see that there are five elements and the `tokenType` is missing.

- Another instance can be seen here https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1464-L1465

```solidity
        // Compute the premium up to the current block (ie. after last touch until now). Do not proceed if atTick == type(int24).max = 8388608
        if (atTick < type(int24).max) {
```

Change the comment to `        // Compute the premium up to the current block (ie. after last touch until now). Do not proceed if atTick >= type(int24).max = 8388608`

- Another instance can be seen here https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L173-L179

```solidity
    /// @dev mapping that stores the liquidity data of keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))
    // liquidityData is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user
    // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller
    // the reason why it is called "removedLiquidity" is because long options are created by removed liquidity -ie. short selling LP positions
    mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
        internal s_accountLiquidity;

```

The line `      /// @dev mapping that stores the liquidity data of keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))` is misleading, cause navigating to the actual implementation of the data that is being encoded we can see that there are five elements and the `tokenType` is missing.

### Recommended Mitigation Steps

Apply these changes to https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L138-L145

```diff
    // base collateral ratios
    /// @notice Required collateral ratios for buying, represented as percentage * 10_000.
    /// i.e 20% -> 0.2 * 10_000 = 2_000.
-    uint256 immutable SELLER_COLLATERAL_RATIO;
+    uint256 immutable BUYER_COLLATERAL_RATIO;

    /// @notice Required collateral ratios for selling, represented as percentage * 10_000.
    /// i.e 10% -> 0.1 * 10_000 = 1_000.
-    uint256 immutable BUYER_COLLATERAL_RATIO;
+    uint256 immutable SELLER_COLLATERAL_RATIO;
```

## QA-07 Important addresses should be changed in a two-step format

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L145-L156

```solidity
    /// @notice Set the owner of the Panoptic Factory.
    /// @param newOwner The new owner of the Panoptic Factory
    function transferOwnership(address newOwner) external {
        address currentOwner = s_owner;

        if (msg.sender != currentOwner) revert Errors.NotOwner();

        s_owner = newOwner;

        emit OwnershipTransferred(currentOwner, newOwner);
    }

```

This function is used to set the owner of the Panoptic Factory however it's being done in one step which could then cause the execution to be irreversible if any errors were to occur.

### Recommended Mitigation Steps

A general rule is to have these attempts done in a two-step format, that way we ensure the attempt at swapping the admins is safe.

## QA-08 User should not be allowed to liquidate themselves

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1019-L1176

```solidity
function liquidate(
    TokenId[] calldata positionIdListLiquidator,
    address liquidatee,
    LeftRightUnsigned delegations,
    TokenId[] calldata positionIdList
) external {
    _validatePositionList(liquidatee, positionIdList, 0);
    //(...snip)

        (uint256 balanceCross, uint256 thresholdCross) = _getSolvencyBalances(
            tokenData0,
            tokenData1,
            Math.getSqrtRatioAtTick(twapTick)
        );

        if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();
    }
    //@audit
    s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());
    s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());

    int256 liquidationBonus0;
    int256 liquidationBonus1;
    int24 finalTick;
    {
        LeftRightSigned netExchanged;
        LeftRightSigned[4][] memory premiasByLeg;

        (netExchanged, premiasByLeg) = _burnAllOptionsFrom(
            liquidatee,
            Constants.MIN_V3POOL_TICK,
            Constants.MAX_V3POOL_TICK,
            DONOT_COMMIT_LONG_SETTLED,
            positionIdList
        );

        (, finalTick, , , , , ) = s_univ3pool.slot0();
    //(...snip)
    emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);
}
```

This function is used to liquidate an account, or better said as liquidating a [distressed account](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L35), it does this by burning all the positions and some other steps like sending the liqudiation bonus, issue is that this function has no check that the `liquidatee != liquidator` and allows a user to liquidate themselves and bypass all protocol's native validations, for example protocol doesn't allow for long premiums to be settled except when liquidating a distressed account, so in this case a user can just liquidate themselves and not settle their long premiums, additionally they could pass on their accounts and have it not being able to pay the liquidation bonus and game the system to mint them tokens for free.

> NB: The above is just a simple case as to how a user could game this integration multiple ideas can stem up from users just being able to liquidate themselves

### Recommended Mitigation Steps

As a somewhat general rule pertaining Defi, users shouldn't be allowed to liquidate themselves, so in our case here recommendation would be to always ensure `liquidator != liquidatee` in `liquidate()`

## QA-09 `Collateraltracker.sol` is not compatible with ERC-4626

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol

we can see that this contract is expected to use the ERC4626 standard allowing the minting and burning of "shares", however the contract doesn't really comply with ERC-4626.

Note that the below has been stated:

> All EIP-4626 tokenized Vaults MUST implement EIP-20 to represent shares.

For the contract to be fully EIP-20 compliant, it should also support ERC20 as per EIP-165, which it currently does not. More information about EIP-165 can be found here:

[EIP-165](https://eips.ethereum.org/EIPS/eip-165)

### Recommended Mitigation Steps

Modify the vault to ensure full EIP-4626 compliance

## QA-10 `_getSolvencyBalances()` should round up for both `balanceCross` & `thresholdCross` or round down for both

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1344-L1361

```solidity
    function _getSolvencyBalances(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint160 sqrtPriceX96
    ) internal pure returns (uint256 balanceCross, uint256 thresholdCross) {
        unchecked {
            // the cross-collateral balance, computed in terms of liquidity X*√P + Y/√P
            // We use mulDiv to compute Y/√P + X*√P while correctly handling overflows, round down
            balanceCross =
                Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +
                Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);
            // the amount of cross-collateral balance needed for the account to be solvent, computed in terms of liquidity
            // overstimate by rounding up
            thresholdCross =
                Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +
                Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);
        }
    }
```

This function is used to get the parameters related to the solvency state of the account associated with the incoming tokenData and is used in multiple instances in scope, from [liquidations](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1061-L1070) to [force exercises](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1324-L1332), but as shown in the function we can see that an over estimation is being done for the `thresholdCross` however not the same is being done for the `balanceCross` which could cause user's to be assumed to be insolvent where as they are solvent, leading to unfair liquidations and what not.

### Recommended Mitigation Steps

Consider either overestimating both or underestimating both, that way it's fair for both parties.

## QA-11 Fix typos _(multiple instances)_

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L245-L250

```solidity

        unchecked {
            // construct the time stots
            for (uint256 i = 0; i < 20; ++i) {
                secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);
            }
```

`            // construct the time stots` should be
`            // construct the time SLOTS`

- Another instance can be seen here https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L260-L263

```solidity
        However, since we require that Eqn 2 holds up-- ie. the gross fees collected should be equal
        to the net fees collected plus the ower fees plus the small spread, the expression for the
        s_accountPremiumGross accumulator has to be given by (you`ll see why in a minute):

```

The line `        to the net fees collected plus the ower fees plus the small spread, the expression for the` should instead be `        to the net fees collected plus the OWNER fees plus the small spread, the expression for the`

### Impact

### Recommended Mitigation Steps

## QA-12 Current Pool id that's gotten is way less unique

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L47-L55

```solidity
    function getPoolId(address univ3pool) internal view returns (uint64) {
        unchecked {
            int24 tickSpacing = IUniswapV3Pool(univ3pool).tickSpacing();
            uint64 poolId = uint64(uint160(univ3pool) >> 112);
            poolId += uint64(uint24(tickSpacing)) << 48;
            return poolId;
        }
    }

```

This function is used to get a 64-bit ID after given an address to a Uniswap v3 pool, and is being used as the `TokenId` for that pool in Panoptic, however compared to the previous implementation, pool ids gotten by this implementation are not as unique

The previous implementation had a bit shifting of 96 bytes, when integrating with the univ3Pool address, i.e `uint64(uint160(univ3pool) >> 96);;` however here we have `uint64 poolId = uint64(uint160(univ3pool) >> 112);` which means that in this case we get to keep in lesser bits for the pool id generation than previously, would be key to note that the "lesser the bits the higher the chances" of clashing as even though in this case we have an integration of the addition of the tickspacing, on uniswap tickspacing are arguably standardized and multiple pools have the same tick spacing

### Impact

The chances of tokenIds clashing is way higher and would disrupt the functionality within the Panoptic protocol compared to the previous implementation

### Recommended Mitigation Steps

Consider reimplementing as was done in the previous codebase.

## QA-13 Uniswap's callback return value should be checked

### Proof of Concept

Protocol integrates with queries to uniswap and it's callbacks but in no instance is the callback's return value being checked.

The above could cause silencing of important mishaps since protocol doesn't work with the data that was returned

### Recommended Mitigation Steps

Consider checking the return value.

## QA-14 Consider just calling the functions on a low level instead of not taking the failures into account

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L11-L29

```solidity
interface IERC20Partial {
    /// @notice Returns the amount of tokens owned by `account`.
    /// @dev This function is unchanged from the EIP
    /// @param account The address to query the balance of
    /// @return The amount of tokens owned by `account`
    function balanceOf(address account) external view returns (uint256);

    /// @notice Sets `amount` as the allowance of `spender` over the caller's tokens.
    /// @dev While this function is specified to return a boolean value in the EIP, this interface does not expect one
    /// @param spender The address which will spend the funds
    /// @param amount The amount of tokens allowed to be spent
    function approve(address spender, uint256 amount) external;

    /// @notice Transfers tokens from the caller to another user.
    /// @param to The user to transfer tokens to
    /// @param amount The amount of tokens to transfer
    function transfer(address to, uint256 amount) external;
}

```

These are partial definition of the ERC20 interface as defined in the EIP, these instances do not include return values as certain tokens such as USDT fail to implement them.

However this just ensures that the transaction doesn't revert, i.e an attempt to approve/transfer, however they could fail and protocol wouldn't know about it since there is no way to check the return value.

### Recommended Mitigation Steps

Consider just using the `safe` prefixed methods of calling these instead, as that is being done via a low-level call and as such protocol would be able to catch any instance of failures

## QA-15 Consider introducing a functionality to update `VEGOID`

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L128-L134

```solidity
    // ν = 1/2**VEGOID = multiplicative factor for long premium (Eqns 1-5)
    // Similar to vega in options because the liquidity utilization is somewhat reflective of the implied volatility (IV),
    // and vegoid modifies the sensitivity of the streamia to changes in that utilization,
    // much like vega measures the sensitivity of traditional option prices to IV.
    // The effect of vegoid on the long premium multiplier can be explored here: https://www.desmos.com/calculator/mdeqob2m04
    uint128 private constant VEGOID = 2;

```

From the description we can see that The `VEGOID` is implemented to measure the sensitivity of an option.

However, from tradFi and even implementations in defi we can confirm that the volatility of an option can change whenever there is a change in price This is also shown in in protocol in `_getpremiumdeltas()` which hints that this value shouldn't be a constant and instead be changeable.

### Recommended Mitigation Steps

Consider having a functionality that can update the `VEGOID` value.

## QA-16 `ERC1155Minimal.sol` does not comply with the EIP-1155 Token standard

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L94-L120

```solidity
    function safeTransferFrom(
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
            }
        }
    }
```

And https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L130-L172

```solidity
    function safeBatchTransferFrom(
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
                //onERC1155BatchReceived could be used to hack protocol no? @audit
                ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
                ERC1155Holder.onERC1155BatchReceived.selector
            ) {
                revert UnsafeRecipient();
            }
        }
    }
```

We can see that both functions as used to transfer a single or multiple tokens via the batch transfers, issue however is that navigating to the specs for EIP-1155 we can see the below stated under the specification https://eips.ethereum.org/EIPS/eip-1155

> MUST revert if \_to is the zero address

However in both instances of the transfers there are no checks that the receiving address is not the zero address.

Essentially meaning that whenever the `safeTransferFrom` or `safeBatchTransferFrom` fare used by the panoptic protocol by passing in the to address as address(0) this could lead to loss of funds to the users of the protocol who are minting or burning option positions.

### Recommended Mitigation Steps

Consider making the implementation of transfers to be more in line with the EIP, i,e add this pseudo fix: `require(to != address(0))`

## QA-17 Incorrect calculations in `convert0to1()`& `convert1to0()`

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L524-L567

```solidity
    function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
        unchecked {
            // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
            // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
            if (sqrtPriceX96 < type(uint128).max) {
                int256 absResult = Math
                    .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }
        }
}

    function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
        unchecked {
            // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
            // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
            if (sqrtPriceX96 < type(uint128).max) {
                int256 absResult = Math
                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv(
                        Math.absUint(amount),
                        2 ** 128,
                        Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
                    )
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }
        }
    }
```

Both functions are used to amounts provided into either of token1/token0 after being given the `sqrtPriceX96` from the uniswap pool.

When we examine those functions closely, we can conclude there are basically the same with Uniswap's getQuoteAtTick(): https://github.com/Uniswap/v3-periphery/blob/main/contracts/libraries/OracleLibrary.sol#L49-L69

```solidity
  if (sqrtRatioX96 <= type(uint128).max) {
            uint256 ratioX192 = uint256(sqrtRatioX96) * sqrtRatioX96;
            quoteAmount = baseToken < quoteToken
                ? FullMath.mulDiv(ratioX192, baseAmount, 1 << 192)
                : FullMath.mulDiv(1 << 192, baseAmount, ratioX192);
        } else {
            uint256 ratioX128 = FullMath.mulDiv(sqrtRatioX96, sqrtRatioX96, 1 << 64);
            quoteAmount = baseToken < quoteToken
                ? FullMath.mulDiv(ratioX128, baseAmount, 1 << 128)
                : FullMath.mulDiv(1 << 128, baseAmount, ratioX128);
        }
```

However protocol's implementation has a strict check instead of `<=` check making it deviate from the native implementation.

Thats to say the Uniswap sets the `sqrtRatioX96` boundary to `sqrtRatioX96 <= type(uint128).max`, while the current implementation to`sqrtRatioX96 < type(uint128).max`.

### Recommended Mitigation Steps

Change `sqrtRatioX96 < type(uint128).max` to `sqrtRatioX96 <= type(uint128).max`

## QA-18 `ERC1155Minimal::safeBatchTransferFrom()` should verify the length of ids and amounts as is done in the EIP

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L130-L172

```solidity
    function safeBatchTransferFrom(
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
                //onERC1155BatchReceived could be used to hack protocol no? @audit
                ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
                ERC1155Holder.onERC1155BatchReceived.selector
            ) {
                revert UnsafeRecipient();
            }
        }
    }
```

From the EIP-1155 we can see the below stated https://eips.ethereum.org/EIPS/eip-1155

> safeBatchTransferFrom rules:
> (...)
> MUST revert if length of \_ids is not the same as length of \_values.

However as shown above this is not being implemented here as the functionality assumes that `ids.length == amounts.length` and automatically starts to iterate from 0 to the `length` of the provided `ids` array.

Now, when `ids.length > amounts.length,` safeBatchTransferFrom() will revert, because it will try to access non-existing index in amounts.

Keep in mind that this contract was stated to have been modified from solmate, and protocol hinted to only remove the metadata functionality as hinted here https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L10

However navigating to the Solmate implementation itself we can see this line `require(ids.length == amounts.length, "LENGTH_MISMATCH");`

> NB: A similar bug case is applicable to the `balanceOfBatch()` function in regards to the `owners` &`ids` array, albeit in this instance no explicit statements has been made in the EIP about this.

### Recommended Mitigation Steps

Consider implementing a similar check as is done in the Solmate library `require(ids.length == amounts.length, "LENGTH_MISMATCH");`.

## QA-19 `ERC20.sol`'s minting doesn't follow CEI

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L122-L131

```solidity
    function _mint(address to, uint256 amount) internal {
        // Cannot overflow because the sum of all user
        // balances can't exceed the max uint256 value.
        unchecked {
            balanceOf[to] += amount;
        }
        totalSupply += amount;

        emit Transfer(address(0), to, amount);
    }


```

This is the internal utility function used to mint tokens to a user's account, however compared to it's inspired implementation here https://github.com/transmissions11/solmate/blob/v7/src/tokens/ERC20.sol#L183

```solidity
function _mint(address to, uint256 amount) internal virtual {
        totalSupply += amount;

        // Cannot overflow because the sum of all user
        // balances can't exceed the max uint256 value.
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(address(0), to, amount);
    }

```

Evidently minting doesn't follow CEI in our case here totalSupply is only added after the balances of the user has been updated.

### Recommended Mitigation Steps

Consider implementing CEI

## QA-20 Swapping attempts could end up being partial due to usage of `sqrtPriceX96`

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L756-L852

```solidity
  function swapInAMM(
        IUniswapV3Pool univ3pool,
        LeftRightSigned itmAmounts
    ) internal returns (LeftRightSigned totalSwapped) {
        // Initialize variables
        bool zeroForOne; // The direction of the swap, true for token0 to token1, false for token1 to token0
        int256 swapAmount; // The amount of token0 or token1 to swap
        bytes memory data;

        IUniswapV3Pool _univ3pool = univ3pool;

        unchecked {
            // unpack the in-the-money amounts
            int128 itm0 = itmAmounts.rightSlot();
            int128 itm1 = itmAmounts.leftSlot();

            // construct the swap callback struct
            data = abi.encode(
                CallbackLib.CallbackData({
                    poolFeatures: CallbackLib.PoolFeatures({
                        token0: _univ3pool.token0(),
                        token1: _univ3pool.token1(),
                        fee: _univ3pool.fee()
                    }),
                    payer: msg.sender
                })
            );

            // note: upstream users of this function such as the Panoptic Pool should ensure users always compensate for the ITM amount delta
            // the netting swap is not perfectly accurate, and it is possible for swaps to run out of liquidity, so we do not want to rely on it
            // this is simply a convenience feature, and should be treated as such
            if ((itm0 != 0) && (itm1 != 0)) {
                //@audit
                (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();
//(...snip)
                int256 net0 = itm0 - PanopticMath.convert1to0(itm1, sqrtPriceX96);
//(...snip)
            // Add amounts swapped to totalSwapped variable
            totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(
                swap1.toInt128()
            );
        }
    }
```

We can see that when swapping, `sqrtPriceX96` is being heavily used, this can be seen from the query to `convert1to0` however integrating `sqrtPriceX96` with AMM swaps in some situations would result in partial swaps and as such should be avoided,

### Recommended Mitigation Steps

Reimplement the logic and drop the usage of `sqrtPriceX96` for the swaps or clearly document this behaviour.

## QA-21 Eth could get stuck in `SemiFungiblePositionManager` due to an inheritance overlap

### Proof of Concept

Going through the `SemiFungiblePositionManager.sol` contract we can see that there is no specification of a `payable` function or even a `receive()` which means that this contract is not supposed to work with ETH.
But take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L72

```solidity
contract SemiFungiblePositionManager is ERC1155, Multicall {

```

We can see that the contract inherits from the `Multicall` and as such has access to the function below, https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L12-L36

```solidity
    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
        results = new bytes[](data.length);
        for (uint256 i = 0; i < data.length; ) {
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

            unchecked {
                ++i;
            }
        }
    }
```

Evidently this means that since there is no method to retrieve tokens from the `SemiFungiblePositionManager` contract, a user querying this function and mistakenly passing in eth would actually lose their tokens since the Ether is going to be stuck in the contract with no options to get it back.

### Recommended Mitigation Steps

Consider adding an option to get ether back

## QA-22 No deadline check for Uniswap AMM causes transactions to be potentially maliciously executed

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L471-L528

```solidity
    function burnTokenizedPosition(
        TokenId tokenId,
        uint128 positionSize,
        int24 slippageTickLimitLow,
        int24 slippageTickLimitHigh
    )
        external
        ReentrancyLock(tokenId.poolId())
        returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
    {
        // burn this ERC1155 token id
        _burn(msg.sender, TokenId.unwrap(tokenId), positionSize);

        // emit event
        emit TokenizedPositionBurnt(msg.sender, tokenId, positionSize);

        // Call a function that contains other functions to mint/burn position, collect amounts, swap if necessary
        (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
            tokenId,
            positionSize,
            slippageTickLimitLow,
            slippageTickLimitHigh,
            BURN
        );
    }


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

        emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);

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

Both functions are used to burn a new position, or create one, they both interact with the uniswap AMM however they lack any deadline/expiration check whatsoever.

Would be key to note that `SemiFungiblePositionManager` is said to be an alt to `NonfungiblePositionManager`, but `NonfungiblePositionManager` provides expiration protection for theirs users... [source](https://github.com/Uniswap/v3-periphery/blob/main/contracts/NonfungiblePositionManager.sol#L132) which means that there is a generic protection not to the use of old tx from mempool and run it against uniswap pool, as prices can be changed already.

Since the `SemiFungiblePositionManager` doesn't have such protections, it can't guarantee same protection as uniswap's NonfungiblePositionManager.

### Recommended Mitigation Steps

Allow users attach their wanted deadlines, this way outdated tx from the mempool can't be executed against uniswap pool with updated prices, so as to cause loss for the tx initiator.

## QA-23 Protocol's collected and written position data could be flawed

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1085-L1095

```solidity
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

```

The snippet above is from SFPM's attempt at creating a leg in AMM, we can see that the `_collectAndWritePositionData()` function only gets called when the `currentLiquidity.rightSlot() > 0` however valid cases are present for this function to also be called when the `currentLiquidity.rightSlot() == 0`, see reasoning below.

Notice the function itself https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1255-L1314

```solidity
    function _collectAndWritePositionData(
        LiquidityChunk liquidityChunk,
        IUniswapV3Pool univ3pool,
        LeftRightUnsigned currentLiquidity,
        bytes32 positionKey,
        LeftRightSigned movedInLeg,
        uint256 isLong
    ) internal returns (LeftRightUnsigned collectedChunk) {
        uint128 startingLiquidity = currentLiquidity.rightSlot();
        // round down current fees base to minimize Δfeesbase
        // If the current feesBase is close or identical to the stored one, the amountToCollect can be negative.
        // This is because the stored feesBase is rounded up, and the current feesBase is rounded down.
        // When this is the case, we want to behave as if there are 0 fees, so we just rectify the values.
        LeftRightSigned amountToCollect = _getFeesBase(
            univ3pool,
            startingLiquidity,
            liquidityChunk,
            false
        ).subRect(s_accountFeesBase[positionKey]);

        if (isLong == 1) {
            amountToCollect = amountToCollect.sub(movedInLeg);
        }

        if (LeftRightSigned.unwrap(amountToCollect) != 0) {
            // first collect amounts from Uniswap corresponding to this position
            // Collect only if there was existing startingLiquidity=liquidities.rightSlot() at that position: collect all fees

            // Collects tokens owed to a liquidity chunk
            (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(
                msg.sender,
                liquidityChunk.tickLower(),
                liquidityChunk.tickUpper(),
                uint128(amountToCollect.rightSlot()),
                uint128(amountToCollect.leftSlot())
            );

            // moved will be negative if the leg was long (funds left the caller, don't count it in collected fees)
            uint128 collected0;
            uint128 collected1;
            unchecked {
                collected0 = movedInLeg.rightSlot() < 0
                    ? receivedAmount0 - uint128(-movedInLeg.rightSlot())
                    : receivedAmount0;
                collected1 = movedInLeg.leftSlot() < 0
                    ? receivedAmount1 - uint128(-movedInLeg.leftSlot())
                    : receivedAmount1;
            }

            // CollectedOut is the amount of fees accumulated+collected (received - burnt)
            // That's because receivedAmount contains the burnt tokens and whatever amount of fees collected
            collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(
                collected1
            );

            // record the collected amounts in the s_accountPremiumOwed and s_accountPremiumGross accumulators
            _updateStoredPremia(positionKey, currentLiquidity, collectedChunk);
        }
    }

```

From both attached snippets, we can see that `liquidity.rightSlot `is the net liquidity, i.e `(totalLiquidity - removedLiquidity)` and It is possible for this value to be `0`, for example when liquidity has been added and 100% of the liquidity has been removed/borrowed. In this case, we have `liquidity.leftSlot() `to be positive, while `liquidity.rightSlot()` would be 0.

Where as it's sensible that no fees are collected via the `collect` call to the Uniswap pool in the case where net liquidity is `0`, Evidently, the `_collectAndWritePositionData()` also contains the `_updatePremiaDelta()` function call and this is not be skipped when there is `non-zero `removedLiquidity in the liquidity chunk, if at all IT IS SKIPPED, then the `premiaOwed` ends up not being tracked for the borrowed liquidity.

### Impact

> Borderline low/medium
> This is cause the accounting for `premia` could be stale, since when there is borrowed liquidity, but zero net liquidity for a `positionKey`, the `premia` for the borrowed position is not updated.

### Recommended Mitigation Steps

The currentLiquidity should be wholly checked to be `> 0` and not just the `rightSlot`, if it `currentLiquidity > 0` then `_collectAndWritePositionData()` should be called, whether the `rightSlot` is `+ve` or `0`.

## QA-24 Closing a long position in some instances wouldn't work due to Uniswap's `tickSpacingToMaxLiquidityPerTick` limitation

### Proof of Concept

When a user opens a long position, the SFPM removes liquidity from Uniswap. To close the position, the user must replenish the same Uniswap position, which requires providing liquidity to the same ticks. However, Uniswap's tickSpacingToMaxLiquidityPerTick limits the amount of liquidity a tick can hold. If adding liquidity exceeds the max liquidity per tick, it's impossible to mint the liquidity in the given range, preventing the long position from being closed.

Consider a DAI-USDC 0.01% pool with concentrated liquidity in few ticks. If Alice opens a long position by removing liquidity from ticks x-y, which are close to the max liquidity per tick, she cannot mint the same liquidity later due to the `tickSpacingToMaxLiquidityPerTick` limitation, il.e if the tick to be added would then make the max range to be passed. This issue can also be exploited by an attacker who tops up liquidity to prevent Alice from closing her long position.

This issue might seem unlikely for volatile pools but can be realistic for stable pools with high liquidity. Since SFPM cannot control Uniswap pools directly, it can only control liquidity provisioning through itself.

### Recommended Mitigation Steps

SFPM should check if opening a short position will exceed the Uniswap tick value and maybe revert if necessary. Additionally, SFPM should ensure that the sum of liquidity borrowed by longers, current liquidity in the tick for all Uniswap liquidity providers, and requested short positions mint liquidity does not exceed the max liquidity per tick.

## QA-25 `Math.mulDiv()` does not explicitly check that `denominator != 0`

### Proof of Concept

Take a look at thr `mulDiv's` implementation here https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L340-L434

We can see that in no instance is there a check that the denominator is not `0`, would be key to note that while the` require(denominator > prod1)` checks indirectly prevents division by zero in most cases, it does not cover the scenario where both `prod1` and `denominator` are `0`. In such a case, the function might exhibit undefined behavior or cause a panic revert since we are attempting to divide by `0`

### Recommended Mitigation Steps

Add an explicit check at the beginning of the function to ensure that the denominator is not zero. This can be done using a require statement

## QA-26 Consider depleting allowances in all instances of transfers

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L81-L98

```solidity
    function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
        uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.

        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;

        balanceOf[from] -= amount;

        // Cannot overflow because the sum of all user
        // balances can't exceed the max uint256 value.
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(from, to, amount);

        return true;
    }

```

This function is used to transfer tokens from one user to another, before the change in balances are applied we can see that there is an allowance check, however the allowance only gets deducted in the case where the current approval set is not ` type(uint256).max)`, issue here is that whereas this could take a very long duration, there is a very slim chance that after a long duration + multiple transactions, the user is to have to depleted their allowance but protocol still assumes they are infinitely allowed.

### Recommended Mitigation Steps

Consider depleting the allowances in all instances of transfers.

## QA-27 `Math.getAmount0ForLiquidity()` could cause a break up in accounting data due to precision loss

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L191-L214

```solidity
    function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
        uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
        uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());
        unchecked {
            return
                mulDiv(
                    uint256(liquidityChunk.liquidity()) << 96,
                    highPriceX96 - lowPriceX96,
                    highPriceX96
                ) / lowPriceX96;
        }
    }

    function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {
        uint160 lowPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickLower());
        uint160 highPriceX96 = getSqrtRatioAtTick(liquidityChunk.tickUpper());

        unchecked {
            return mulDiv96(liquidityChunk.liquidity(), highPriceX96 - lowPriceX96);
        }
    }
```

Both functions are used to calculate the amount of `token0/token1` after being given a liquudity, however unlike `getAmount1ForLiquidity()` the `getAmount0ForLiquidity()` function is susceptible to a precision lossmas double divisions are being made instead of just one.

This could subtly affect protocol's accounting logic as the amounts gotten for the liquidity would now not match it's real value

### Recommended Mitigation Steps

Consider having the division attempt in one step instead

## QA-28 Excessive usage of floating pragma should be curbed

### Proof of Concept

Query this search command: [https://github.com/search?q=repo%3Acode-423n4%2F2024-04-panoptic+%5E0.8+NOT+language%3AJSON+NOT+language%3AMarkdown+NOT+path%3A%2F%5Etest%5C%2Ffoundry%5C%2F%2F&type=code](https://github.com/search?q=repo%3Acode-423n4%2F2024-04-panoptic+%5E0.8+NOT+language%3AJSON+NOT+language%3AMarkdown+NOT+path%3A%2F%5Etest%5C%2Ffoundry%5C%2F%2F&type=code)

We can see that multiple contracts in scope implement the floating pragma which is not advisable for a project, as a fixed compiler is not used.

### Recommended Mitigation Steps

Consider choosing one compiler version and use that as was done in the previous codebase, e.g https://github.com/code-423n4/2023-11-panoptic/blob/main/contracts/multicall/Multicall.sol#L2.
