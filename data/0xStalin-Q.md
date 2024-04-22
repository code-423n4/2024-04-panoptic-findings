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


## [L-04] Not checking the returned value when approving the SFPM & CollateralTrackers to spend tokens could leave unnusable a UniV3Pool if the approval process returns false instead of reverting
When a new PanopticPool is deployed, the PanopticFactory calls the [`PanopticPool.startPool() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L327) to initialize some core variables, as well as to grant approvals to the SFPM and the CollateralTrackers associated with the PanopticPool.

To grant allowance, the [`InteractionHelper.doApprovals() function`](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L24-L38) is called, which then proceeds to call the underlyingToken.approve() function to grant infinite allowance to the SFPM and the two CollateralTrackers. The current interface doesn't check for the returned value from the underlyingToken.approve(), if the call fails and returns false instead of reverting, either the SFPM or one of the two CollateralTrackers won't have allowance to spend the underlyingToken from the PanopticPool.
- The problem is that if the SFPM, or one of the two CollateralTrackers are not granted the allowance, first of all, the newly deployed PanopticPool will be unnusable, since core functions won't be able to move the token across the contracts, and also, the underlying UniV3Pool associated with the newly deployed PanopticPool will become unnusable, it won't be possible to deploy a new PanopticPool and associate the same UniV3Pool with a new PP.

```
--- PanopticFactory.sol ---

function deployNewPool(
    address token0,
    address token1,
    uint24 fee,
    bytes32 salt
) external returns (PanopticPool newPoolContract) {
    ...

    //@audit-info => One UniV3 Pool can have assigned only 1 PanopticPool!
    if (address(s_getPanopticPool[v3Pool]) != address(0))
        revert Errors.PoolAlreadyInitialized();

    ...

    //@audit-ok => Initializes the PanopticPool when is deployed from the PanopticFactory
    newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);

    //@audit-info => Links the newly deployed PanopticPool to its assigned UniV3 Pool
    //@audit-info => One UniV3 Pool can have assigned only 1 PanopticPool!
    s_getPanopticPool[v3Pool] = newPoolContract;

    ...
}

--- PanopticPool.sol ---

function startPool(
    ...
) external {
    ...

    //@audit-info => Approves SFPM, and the two CollateralTrackers
    InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);
}

--- InteractionHelper.sol ---

function doApprovals(
    ...
) external {
    //@audit-issue => If the approve fails and returns false instead of reverting, it is not possible to catch the problem and revert the tx
        //@audit-issue => Not reverting the tx would allow the deployment of the new PP to finalize.
        //@audit => This means, the associated UniV3Pool to this PP won't be able to be assigned to a different PP.
        //@audit => If this PP becomes unnusable because the allowance failure, the underlying UniV3Pool won't be able to be used on any other PP.
    // Approve transfers of Panoptic Pool funds by SFPM
    IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
    IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

    // Approve transfers of Panoptic Pool funds by Collateral token
    IERC20Partial(token0).approve(address(ct0), type(uint256).max);
    IERC20Partial(token1).approve(address(ct1), type(uint256).max);
}

```


**Fix:**
The best way to mitigate this potential thread it is by using the [`forceApprove()` of the `SafeErc20.sol` contract from OZ.](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/utils/SafeERC20.sol#L76-L83)
- This approach allows to revert the tx in case the approval process fails and returns false.


## [L-05] Malicious Option Sellers can deploy liquidity on a range far out of the current price to get stuck the liquidity on the UniV3Pool to halt the trading on the PanopticPool because a lack of liquidity
An Option Seller could deploy all the liquidity (if enough collateral) sitting on a PanopticPool onto a range far away from the current price, with the objective to open an unreasonable short position that any OptionSeller would take because of the cost-opportunity to pay premia for an option with a target price very unreasonable that it most likely never hit.

The OptionSeller would need to only pay the COMISSION_FEE to open the short in exchange for deploying liquidity on a range where it won't generate any fees nor OptionBuyers would open long positions for that range.

Even though the OptionSeller will also have its collateral locked during the time the short option remains open, the impact on the PLPs is bigger because of the leverage that OptionSellers have when opening shorts.
- For example, the OptionSeller could have locked 100k USDC of his collateral in exchange for deploying 500k+ to a range where no activity will happen. The fees and commissions those 500k would have generated if that liquidity had been available for other traders who wanted to really trade options would be lost.

Since positions with only shorts can't be force exercised, this short option would remain open for as long as the OptionSeller wants.

**Fix:**
I'd suggest allowing OptionSellers to open shorts without extra commission within a reasonable range from the current price. But if the target range exceeds a defined threshold, charge an extra commission, in this way, this would disincentivize this type of situation because the fees & commissions to pay would be higher.
- For example, if the currentPrice is 1.5k USDC per ETH, allow to open shorts without extra commission within a price range of 700USDC - 3k USDC, smth like this. But, if the target price exceeds the defined threshold, charge an extra fee to disincentivize malicious OptionSellers from deploying liquidity to unreasonable ranges.