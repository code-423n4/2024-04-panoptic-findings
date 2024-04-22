# QA Report: Panoptic

## L1: Lack of pause functionality for withdraw and deposit

### Impact

The absence of pause functionality means that in the event of a detected vulnerability or bug in the contract, there is no quick way to halt deposits or withdrawals while a fix is implemented. This could lead to exploitation and significant losses before corrective measures can be taken.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L417


```solidity
function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
        if (assets > type(uint104).max) revert Errors.DepositTooLarge();

        shares = previewDeposit(assets);

        // transfer assets (underlying token funds) from the user/the LP to the PanopticPool
        // in return for the shares to be minted
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        );

        // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
        _mint(receiver, shares);

        // update tracked asset balance
        unchecked {
            s_poolAssets += uint128(assets);
        }

        emit Deposit(msg.sender, receiver, assets, shares);
    }

```

### Loc

https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L531

```solidity
function withdraw(
        uint256 assets,
        address receiver,
        address owner
    ) external returns (uint256 shares) {
        if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

        shares = previewWithdraw(assets);

        // check/update allowance for approved withdraw
        if (msg.sender != owner) {
            uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.

            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
        }

        // burn collateral shares of the Panoptic Pool funds (this ERC20 token)
        _burn(owner, shares);

        // update tracked asset balance
        unchecked {
            s_poolAssets -= uint128(assets);
        }

        // transfer assets (underlying token funds) from the PanopticPool to the LP
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        );

        emit Withdraw(msg.sender, receiver, owner, assets, shares);

        return shares;
    }
```

## L2: Performing calculations and updates on positions with zero liquidity is unnecessary and can lead to inconsistencies

### Impact

In the case where startingLiquidity is zero, the lack of a zero check in the _collectAndWritePositionData function can lead to the following impacts:

The function will continue to execute and perform calculations even when there is no existing liquidity at the position. This includes calculating amountToCollect based on the difference between the current fees base and the stored fees base. These computations are unnecessary and wasteful when there is no liquidity to collect from.

If amountToCollect happens to be non-zero despite startingLiquidity being zero, the function will proceed with the collect call to the Uniswap V3 pool. However, since there is no liquidity at the position, this call is unnecessary and will not result in any actual collection of fees.

Performing updates on positions with zero liquidity can also lead to inconsistencies.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1255

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


## L3: Potential cloneDeterministic fails on Unsupported Chains

### Impact
Potential cloneDeterministic fails if EVM bytecode not supported for clones.

> the reason why this is not currently supported is because EIP 1167 is written directly in EVM bytecode, which is quite different from the bytecode that zkEVM operates on.

[source](https://github.com/zkSync-Community-Hub/zksync-developers/discussions/91)

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L237

```solidity
 newPoolContract = PanopticPool(POOL_REFERENCE.cloneDeterministic(salt));
```



## L4: Oracle Manipulation and Price Feeds Vulnerability during Low Liquidity or Orchestrated Trades by Bad Actors

### Impact

The PanopticPool smart contract uses a TWAP (Time-Weighted Average Price) mechanism sourced from Uniswap V3 to provide price feeds for its operations. The contract uses a combination of a "slow" oracle updated less frequently and a "fast" oracle that provides more current data. These feeds influence critical functionalities such as liquidations, minting, and burning of options.

If an actor or colluding group conducts trades specifically around the oracle's sampling times, they might skew the TWAP significantly enough to impact the contract operations, such as triggering inappropriate liquidations or allowing adverse selection against other users.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1450

```solidity
uint32 internal constant TWAP_WINDOW = 600;
```

```solidity
/// @notice Compute the TWAP price from the last 600s = 10mins.
/// @return twapTick The TWAP price in ticks.
function getUniV3TWAP() internal view returns (int24 twapTick) {
    twapTick = PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW);
}

```

## L5: Hardcoded Slippage Limits and Tick Constraints

### Impact

The contract enforces strict limits on tick movements during swaps. In highly volatile markets, these constraints might either prevent necessary adjustments to positions or expose users to slippage that could be otherwise avoided with more dynamic settings.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L103C5-L106C1

```solidity
int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;
    /// @dev has to be one below MAX because of univ3pool.swap's strict "<" check
    int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;

```

## L6: Position Limit Restriction Hinders Protocal Adoption

### Impact

While limiting the maximum number of positions per account can prevent excessive system load and reduce risk, it might also restrict high-volume traders or institutional participants. This could limit the protocol's adoption or utility for larger market players.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L168

```solidity
uint64 internal constant MAX_POSITIONS = 32;
```

## L7: Missing Low Threshold Liquidity Checks

### Impact

CollateralTracker system does not include adequate checks and safeguards for handling scenarios where the liquidity in the associated Uniswap V3 pool falls below critical thresholds. This can lead to potential issues such as increased slippage, price manipulation and failing operations due to insufficient liquidity.

Add checks in deposit, withdraw, mint, and redeem functions to ensure pool liquidity is above a safe minimum threshold before allowing the operation. 

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L417
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L477
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L591

```solidity
function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
        if (assets > type(uint104).max) revert Errors.DepositTooLarge();

        shares = previewDeposit(assets);

        // transfer assets (underlying token funds) from the user/the LP to the PanopticPool
        // in return for the shares to be minted
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        );

        // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
        _mint(receiver, shares);

        // update tracked asset balance
        unchecked {
            s_poolAssets += uint128(assets);
        }

        emit Deposit(msg.sender, receiver, assets, shares);
    }
```

```solidity
function redeem(
        uint256 shares,
        address receiver,
        address owner
    ) external returns (uint256 assets) {
        if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

        // check/update allowance for approved redeem
        if (msg.sender != owner) {
            uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.

            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
        }

        assets = previewRedeem(shares);

        // burn collateral shares of the Panoptic Pool funds (this ERC20 token)
        _burn(owner, shares);

        // update tracked asset balance
        unchecked {
            s_poolAssets -= uint128(assets);
        }

        // transfer assets (underlying token funds) from the PanopticPool to the LP
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        );

        emit Withdraw(msg.sender, receiver, owner, assets, shares);

        return assets;
    }

```


```solidity
function withdraw(
        uint256 assets,
        address receiver,
        address owner
    ) external returns (uint256 shares) {
        if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

        shares = previewWithdraw(assets);

        // check/update allowance for approved withdraw
        if (msg.sender != owner) {
            uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.

            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
        }

        // burn collateral shares of the Panoptic Pool funds (this ERC20 token)
        _burn(owner, shares);

        // update tracked asset balance
        unchecked {
            s_poolAssets -= uint128(assets);
        }

        // transfer assets (underlying token funds) from the PanopticPool to the LP
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        );

        emit Withdraw(msg.sender, receiver, owner, assets, shares);

        return shares;
    }


```

## L8: Introduce Two-Step ownership transfer

### Impact
By introducing a confirmation step, it prevents accidental ownership transfers which could happen due to typos or other errors when specifying the new owner's address.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147

```solidity
function transferOwnership(address newOwner) external {
        address currentOwner = s_owner;

        if (msg.sender != currentOwner) revert Errors.NotOwner();

        s_owner = newOwner;

        emit OwnershipTransferred(currentOwner, newOwner);
    }
```

## L9: Single Point of Failure

### Impact

Relying on a single oracle source, such as the TWAP from Uniswap V3, can be risky if the data source is manipulated.

Use multiple oracle sources to determine the current market price. A composite price can be derived from several trusted sources, such as Chainlink, MakerDAO's Oracle, and Uniswap, to minimize the risk of price manipulation.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1450

```solidity
function getUniV3TWAP() internal view returns (int24 twapTick) {
    twapTick = PanopticMath.twapFilter(s_univ3pool, TWAP_WINDOW);
}
```

## L10: Insufficient validaition in exerciseCost Function

### Impact

The positionBalance parameter represents the balance in account of the position to be exercised and should be checked if greater than zero to avoid calculations on non-existent positions.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L650

```solidity
function exerciseCost(
        int24 currentTick,
        int24 oracleTick,
        TokenId positionId,
        uint128 positionBalance,
        LeftRightSigned longAmounts
    ) external view returns (LeftRightSigned exerciseFees) {
        // find the leg furthest to the strike price 'currentTick'; this will have the lowest exercise cost
        // we don't need the leg information itself, really just "the number of half ranges" from the strike price:
        uint256 maxNumRangesFromStrike = 1; // technically "maxNum(Half)RangesFromStrike" but the name is long

        unchecked {
            for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {
                // short legs are not counted - exercise is intended to be based on long legs
                if (positionId.isLong(leg) == 0) continue;

                {
                    int24 range = int24(
                        int256(
                            Math.unsafeDivRoundingUp(
                                uint24(positionId.width(leg) * positionId.tickSpacing()),
                                2
                            )
                        )
                    );
                    maxNumRangesFromStrike = Math.max(
                        maxNumRangesFromStrike,
                        uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
                    );
                }

                uint256 currentValue0;
                uint256 currentValue1;
                uint256 oracleValue0;
                uint256 oracleValue1;

                {
                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                        positionId,
                        leg,
                        positionBalance
                    );

                    (currentValue0, currentValue1) = Math.getAmountsForLiquidity(
                        currentTick,
                        liquidityChunk
                    );

                    (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(
                        oracleTick,
                        liquidityChunk
                    );
                }

                uint256 tokenType = positionId.tokenType(leg);
                // compensate user for loss in value if chunk has lost money between current and median tick
                // note: the delta for one token will be positive and the other will be negative. This cancels out any moves in their positions
                if (
                    (tokenType == 0 && currentValue1 < oracleValue1) ||
                    (tokenType == 1 && currentValue0 < oracleValue0)
                )
                    exerciseFees = exerciseFees.sub(
                        LeftRightSigned
                            .wrap(0)
                            .toRightSlot(
                                int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
                            )
                            .toLeftSlot(
                                int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
                            )
                    );
            }
```

## L11: Insufficient validaition in startToken Function

### Impact

This should be greater than zero to ensure the Uniswap pool is initialized with a valid fee structure. A zero fee would not make sense and could potentially lead to financial inaccuracies or exploitation.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221

```solidity
 function startToken(
        bool underlyingIsToken0,
        address token0,
        address token1,
        uint24 fee,
        PanopticPool panopticPool
    ) external {
        // fails if already initialized
        if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();
        s_initialized = true;

        // these virtual shares function as a multiplier for the capital requirement to manipulate the pool price
        // e.g if the virtual shares are 10**6, then the capital requirement to manipulate the price to 10**12 is 10**18
        totalSupply = 10 ** 6;

        // set total assets to 1
        // the initial share price is defined by 1/virtualShares
        s_poolAssets = 1;

        // store the address of the underlying ERC20 token
        s_underlyingToken = underlyingIsToken0 ? token0 : token1;

        // store the Panoptic pool for this collateral token
        s_panopticPool = panopticPool;

        // cache the pool fee in basis points
        uint24 _poolFee;
        unchecked {
            _poolFee = fee / 100;
        }
        s_poolFee = _poolFee;

        // Stores the addresses of the underlying tracked tokens.
        s_univ3token0 = token0;
        s_univ3token1 = token1;

        // store whether the current collateral token is token0 (true) or token1 (false; since there's always exactly two tokens it could be)
        s_underlyingIsToken0 = underlyingIsToken0;

        // Additional risk premium charged on intrinsic value of ITM positions
        unchecked {
            s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);
        }
    }
```

## L12: deployNewPool function can be front-run by malicious actors

### Impact

This function is used to deploy new Panoptic Pools. The risk of frontrunning here is significant because of the dependence on specific parameters like token0, token1, fee, and salt. If these parameters are visible in a pending transaction, a frontrunner could deploy a pool using the same parameters but with a different salt that still meets their conditions.

Implement a two-phase commit-reveal process to hide the true intent of a transaction until it's too late to frontrun effectively.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L210

```solidity
 function deployNewPool(
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

        // initialize pool in SFPM if it has not already been initialized
        SFPM.initializeAMMPool(token0, token1, fee);

        // This creates a new Panoptic Pool (proxy to the PanopticPool implementation)
        // Users can specify a salt, the aim is to incentivize the mining of addresses with leading zeros
        newPoolContract = PanopticPool(POOL_REFERENCE.cloneDeterministic(salt));

        // Deploy collateral token proxies
        CollateralTracker collateralTracker0 = CollateralTracker(
            Clones.clone(COLLATERAL_REFERENCE)
        );
        CollateralTracker collateralTracker1 = CollateralTracker(
            Clones.clone(COLLATERAL_REFERENCE)
        );

        // Run state initialization sequence for pool and collateral tokens
        collateralTracker0.startToken(true, token0, token1, fee, newPoolContract);
        collateralTracker1.startToken(false, token0, token1, fee, newPoolContract);

        newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);

        s_getPanopticPool[v3Pool] = newPoolContract;

        // The Panoptic pool won't be safe to use until the observation cardinality is at least CARDINALITY_INCREASE
        // If this is not the case, we increase the next cardinality during deployment so the cardinality can catch up over time
        // When that happens, there will be a period of time where the PanopticPool is deployed, but not (safely) usable
        v3Pool.increaseObservationCardinalityNext(CARDINALITY_INCREASE);

        // Mints the full-range initial deposit
        // which is why the deployer becomes also a "donor" of full-range liquidity
        // The SFPM will `safeTransferFrom` tokens from the donor during the mint callback
        (uint256 amount0, uint256 amount1) = _mintFullRange(v3Pool, token0, token1, fee);

        // Issue reward NFT to donor
        DONOR_NFT.issueNFT(msg.sender, newPoolContract, token0, token1, fee);

        emit PoolDeployed(
            newPoolContract,
            v3Pool,
            collateralTracker0,
            collateralTracker1,
            amount0,
            amount1
        );
    }
```

## L13: maxDeposit should be determined by current pool conditions rather than maximum value of uint104

### Impact

The function does not account for current pool conditions, such as available liquidity, which should ideally dictate the deposit capacity. It simply returns the maximum value of a uint104, which may not realistically reflect the operational or liquidity constraints of the underlying system or market conditions.

### Loc
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L392

```solidity
/// @notice Returns the maximum deposit amount.
/// @return maxAssets The maximum amount of assets that can be deposited.
function maxDeposit(address) external pure returns (uint256 maxAssets) {
    return type(uint104).max;
}

```