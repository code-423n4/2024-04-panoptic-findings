## [L-01] Transfering positions on the SFPM falls into DoS when the position's owner has different positions that have deployed liquidity on the same chunk
Users can't transfer their positions on the SFPM even though they are transfering all the liquidity of the position.

When an account opens opens different positions with options deploying liquidity to the same chunk, the `s_accountLiquidity` will be udpated to reflect all the account's liquidity.

This causes that when the [`SemiFungiblePositionManager.registerTokenTransfer() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593-L653) checks if the liquidity of the position to be transferred matches the `s_accountLiquidity` to not be the same, which will cause the tx to revert, even though the user is attempting to transfer the full liquidity of the position.

The problem is that the `s_accountLiquidity` is updated with all the account's liquidity that has been deployed to the same chunk, not only the liquidity of the position that is beent transferred.

<details>
<summary><b>Expand to see a Coded PoC</b></summary>
<br>

Add the below PoC to the [`SemiFungiblePositionManager.t.sol`](https://github.com/code-423n4/2024-04-panoptic/blob/main/test/foundry/core/SemiFungiblePositionManager.t.sol) test file, and run it with the next command:

> forge test --match-test testStalin_tokenTransfer_PoC -vvvv

```
function testStalin_tokenTransfer_PoC(
    uint256 x,
    uint256 widthSeed,
    int256 strikeSeed,
    uint256 positionSizeSeed
) public {
    _initPool(x);

    (int24 width, int24 strike) = PositionUtils.getOutOfRangeSW(
        widthSeed,
        strikeSeed,
        uint24(tickSpacing),
        currentTick
    );

    populatePositionData(width, strike, positionSizeSeed);

    vm.startPrank(Alice);
    
    //@audit-info => Short Option 1 (Position 1)
    TokenId tokenId1 = TokenId.wrap(0).addPoolId(poolId).addLeg(0, 1, 1, 0, 1, 0, strike, width);

    //@audit-info => mint tokenId1
    sfpm.mintTokenizedPosition(
        tokenId1,
        uint128(positionSize),
        TickMath.MIN_TICK,
        TickMath.MAX_TICK
    );

    //@audit-info => Short Option 2 (Position 2) deploying liquidity on the same chunk as the first position!
    TokenId tokenId2 = TokenId.wrap(0).addPoolId(poolId).addLeg(0, 1, 2, 0, 1, 0, strike, width);

    //@audit-info => mint tokenId2
    sfpm.mintTokenizedPosition(
        tokenId2,
        uint128(positionSize) * 2,
        TickMath.MIN_TICK,
        TickMath.MAX_TICK
    );

    //@audit-info => Alice attempts transfers her tokenId1 to Bob - Will revert even though is transferring all the liquidity of the tokenId1/position1
    sfpm.safeTransferFrom(Alice, Bob, TokenId.unwrap(tokenId1), positionSize, "");
}
```

</details>

**Fix:**
- The potential fix for this finding would require to track the liquidity of each position on the liquidity chunk where it was deployed, instead of only tracking the liquidity of the whole account per liquidity chunk.
- Also,it would be required to compute the exact amount of baseFees that would need to be transferred to match the equivalent amount of liquidity that is been transferred.
- Another option, if this is an expected behavior it would be to simply document this behavior, so that users know in advance what would happen if their accounts contains different positions with liquidity deployed on the same liquidity chunk


## [L-02] Precission loss on the maxMint() causes to compute a lower amount of shares that would be received for the maximum allowed deposit
The [`CollateralTracker.maxMint() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444-L448) has a precision loss that computed incorrectly the amount of shares that would be received for the maximum allowed deposit. 

If the returned value from the `maxMint() function` is compared with the returned value of the [`CollateralTracker.previewDeposit() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L399-L408), the values are not equals.

The discrepancy on these values could cause integration problems with contracts that wanted to deposit the maximum amount, and, validate the received shares for the deposit with the expected output for depositing the maximum allowed deposit.

<details>
<summary><b>Expand to see a Coded PoC</b></summary>
<br>
Add the below PoC to the [`CollateralTracker.t.sol`](https://github.com/code-423n4/2024-04-panoptic/blob/main/test/foundry/core/CollateralTracker.t.sol) test file, and run it with the next command:

> forge test --match-test test_Success_maxMint_PoC -vvvv

```
function test_Success_maxMint_PoC(uint256 x) public {
    _initWorld(x);

    uint256 expectedValue = collateralToken0.previewDeposit(type(uint104).max);

    // real value
    uint256 actualValue = collateralToken0.maxMint(Bob);

    //@audit => Will revert!
    assertEq(expectedValue, actualValue);
}
```

</details>
</br>

**Fix:**
- On the [`CollateralTracker.maxMint() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444-L448), instead of using the current formula, call directly the [`CollateralTracker.previewDeposit() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L399-L408) and pass as a parameter the value of `type(uint104).max`
```
function maxMint(address) external view returns (uint256 maxShares) {
    unchecked {
-         return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
+         return (previewDeposit(type(uint104).max));
    }
}
```

## [L-03] Possible to frontrun the initialization of the PanopticFactory contract
The [`PanopticFactory.initialize() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134-L139) can be frontrun and a malicious user can set an address of his own as the onwer of the PanopticFactory, this would force the protocol to redeploy the PanopticFactory until they can set the owner as an account controlled by them.

```
//@audit-issue => Function can be called by anyone to set the owner of the contract as any address they want
function initialize(address _owner) public {
    if (!s_initialized) {
        s_owner = _owner;
        s_initialized = true;
    }
}
```

**Fix:**
- Since only the `owner` is initialized on the [`PanopticFactory.initialize() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134-L139), better set the owner in the constructor. Since the PanopticFactory is not an upgradeable contract, it is not really necessary to initialize the owner using a separate function outside of the constructor.