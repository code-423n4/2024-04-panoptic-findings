## QA Report

##

## [L-1] Risks of Unchecked Fee Division for Small Values 

When a fee value is less than 100 results in ``_poolFee`` becoming 0 due to integer division in Solidity, it can pose several risks to the protocol, particularly in financial or transactional systems where fees are crucial for operational integrity.

If ``_poolFee`` becomes zero due to low fee values, the protocol might not collect any fees on certain transactions. This loss of revenue could be significant if a large volume of transactions involves small amounts, potentially impacting the economic model of the protocol.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

 // cache the pool fee in basis points
        uint24 _poolFee;
        unchecked {
            _poolFee = fee / 100;
        }

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L246-L250

##

## [L-2] Lack of Input Validation in ``startToken()`` function

The function doesn't explicitly validate its inputs.It doesn't check if ``fee`` or the addresses of ``token0``, ``token1``, and ``panopticPool`` are valid values. This could lead to unexpected behavior or errors if invalid data is passed.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

 function startToken(
        bool underlyingIsToken0,
        address token0,
        address token1,
        uint24 fee,
        PanopticPool panopticPool
    ) external {

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L221-L227

##

## [L-3] Missing MEV Tax Implementation 

The comments mention an MEV tax levied before adding funds to the pool. However, the actual code doesn't implement this functionality.

The missing MEV tax implementation leads to a discrepancy between the documented behavior and the actual execution.  The pool doesn't collect the intended MEV tax from users depositing assets.

```solidity
File: 2024-04-panoptic/contracts/CollateralTracker.sol

 /// @notice Deposit underlying tokens (assets) to the Panoptic pool from the LP and mint corresponding amount of shares.
    /// There is a maximum asset deposit limit of (2 ** 104) - 1.
    /// An MEV tax is levied, which is equal to a single payment of the commissionRate BEFORE adding the funds.
    /// @dev Shares are minted and sent to the LP ('receiver').
    /// @param assets Amount of assets deposited.
    /// @param receiver User to receive the shares.
    /// @return shares The amount of Panoptic pool shares that were minted to the recipient.
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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L410-L440

##

## [L-4] Potential Limited Precision 

 In the deposit function, the maximum deposit amount is capped by the limit type(uint104).max. This means the largest value a deposit can be is the maximum value a uint104 data type can hold.

If a user tries to deposit an amount exceeding type(uint104).max, the transaction will revert with an error message like "Deposit amount exceeds the maximum limit." This can be frustrating for users with large deposits and hinder their ability to participate in the pool.

The limited deposit amount restricts the pool's ability to handle large asset inflows. This can affect the pool's overall liquidity and potentially reduce its attractiveness to users with substantial assets.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

418: if (assets > type(uint104).max) revert Errors.DepositTooLarge();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L418

##

## [L-5] Potential Data Loss Due to Mismatched Types in deposit

The deposit function has a discrepancy between the data type of its input parameter assets and the logic used for validation.

### Impact 

This mismatch can lead to unexpected behavior. Users might provide valid uint256 values within the intended range, but the function will revert with an "Errors.DepositTooLarge" error because the value exceeds the uint104 limit used for validation.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

418: if (assets > type(uint104).max) revert Errors.DepositTooLarge();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L418

##

## [L-6] Lack of CEI pattern in ``deposit()`` function

Code should follow the best-practice of check-effects-interaction, where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

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
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L417-L440

##

## [L-7] Unsafe unchecked block for user inputs 

The key part here is the unchecked keyword. This tells Solidity to proceed with the calculations even if they might encounter overflow or underflow.

### Overflow Scenario

- Imagine shares is the maximum representable value of uint256 (which is a very large number) and DECIMALS is 10000.
- The product shares * DECIMALS might exceed the maximum value a uint256 can hold, causing an overflow.
In unchecked arithmetic, this would simply wrap around to 0, leading to an incorrect calculation for assets.

The entire Math.mulDivRoundingUp function could potentially overflow if the combined effect of the previous multiplications results in a value exceeding the maximum representable value of uint256.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

461: unchecked {
            assets = Math.mulDivRoundingUp(
                shares * DECIMALS,
                totalAssets(),
                totalSupply * (DECIMALS - COMMISSION_FEE)
            );
        }

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L461-L466

##

## [L-8] Unclear MEV Tax Calculation Comments in ``previewMint`` Function

The comments in the previewMint function regarding the MEV tax calculation might not be clear enough. This poses a risk because:

- The comments don't explicitly explain the steps involved in calculating the final assets value after the MEV tax deduction.
- The current comment ("finalAssets - convertedAssets = commissionRate * finalAssets") focuses on the relationship between final assets and converted assets, which requires additional context for clarity.

Add comments explaining each step involved in calculating the final assets value after the MEV tax deduction. 

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

  // round up depositing assets to avoid protocol loss
        // This prevents minting of shares where the assets provided is rounded down to zero
        // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid
        // finalAssets - convertedAssets = commissionRate * finalAssets
        // finalAssets - commissionRate * finalAssets = convertedAssets
        // finalAssets * (1 - commissionRate) = convertedAssets
        // finalAssets = convertedAssets / (1 - commissionRate)

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L454-L461

##

## [L-9] Restricted Withdrawals Might Impact Panoptic Pool Users

The maxWithdraw function currently returns 0 for any user with open positions (s_panopticPool.numberOfPositions(owner) > 0). This effectively restricts withdrawals to users who don't have any active positions in the Panoptic Pool.

The current implementation doesn't allow for any partial withdrawals for users with open positions. This might be inflexible for future scenarios where users might want to:

- Withdraw a portion of their assets while maintaining their open positions.
- Close a portion of their position and withdraw the corresponding assets.

Risk Scenario:

Imagine a user has deposited 100 units of asset A into the Panoptic Pool and opened a leveraged long position on asset B. Currently, the user cannot withdraw any assets because they have an open position.


```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

function maxWithdraw(address owner) public view returns (uint256 maxAssets) {
        // We can only use the standard 4626 withdraw function if the user has no open positions
        // For the sake of simplicity assets can only be withdrawn through the redeem function
        uint256 available = s_poolAssets;
        uint256 balance = convertToAssets(balanceOf[owner]);
        return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;
    }


```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L507-L513

##

## [L-10] Potential for Manipulation - Long Amounts as Input

The exerciseCost function calculates the cost of exercising an option position. It relies on the longAmounts parameter as input to determine the exercise cost specifically for the long legs of the position. This creates a potential vulnerability for manipulation because the function assumes the validity of the provided longAmounts value.

### Impact

Reduce Exercise Cost for OTM Options: If the option is Out-of-the-Money (OTM), meaning the current price is unfavorable for exercising, the attacker can decrease the longAmounts value. This would proportionally reduce the calculated exercise cost for the long legs. As a result, exercising the option becomes cheaper for the attacker even though it's OTM.

Increase Exercise Cost for ITM Options: Conversely, for In-the-Money (ITM) options (favorable for exercising), the attacker could increase the longAmounts value. This would inflate the exercise cost, potentially discouraging the legitimate owner from exercising and allowing the attacker's position to benefit from further price movements.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

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

            // note: we HAVE to start with a negative number as the base exercise cost because when shifting a negative number right by n bits,
            // the result is rounded DOWN and NOT toward zero
            // this divergence is observed when n (the number of half ranges) is > 10 (ensuring the floor is not zero, but -1 = 1bps at that point)
            // subtract 1 from max half ranges from strike so fee starts at FORCE_EXERCISE_COST when moving OTM
            int256 fee = (FORCE_EXERCISE_COST >> (maxNumRangesFromStrike - 1)); // exponential decay of fee based on number of half ranges away from the price

            // store the exercise fees in the exerciseFees variable
            exerciseFees = exerciseFees
                .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))
                .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));
        }
    }

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L650-L745

##

## [L-11] Risk of Unfair Exercise Costs Due to Stale Price Information of ``currentTick `` and ``oracleTick``

The function relies on currentTick and oracleTick as inputs, which are presumably retrieved from an oracle service. If this data is inconsistent (e.g., significant difference between the two ticks) or outdated, it could lead to inaccurate exercise cost calculations.

The function doesn't explicitly check for data validity or freshness.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

function exerciseCost(
        int24 currentTick,
        int24 oracleTick,
        TokenId positionId,
        uint128 positionBalance,
        LeftRightSigned longAmounts
    ) external view returns (LeftRightSigned exerciseFees) {

``` 
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L650-L656

##

## [L-12] Inaccurate Handling of Edge Cases in ``maxNumRangesFromStrike``

The concern here is that the logic for calculating maxNumRangesFromStrike might not accurately handle situations where the position's strike price is very close to either the current price (currentTick) or the oracle price (oracleTick). This could lead to inaccurate calculations of the exercise cost, especially for positions near their strike price (At-the-Money or ATM options).

The logic for calculating maxNumRangesFromStrike might simply not be designed to handle positions extremely close to the current or oracle tick. This could lead to unexpected behavior or inaccurate calculations for ATM options.

Possible Scenarios:
Scenario 1: Imagine a position with a strike price that is just one tick above the current price. Due to rounding during calculations, maxNumRangesFromStrike might be set to 0 (indicating the position is In-the-Money) when it should be 1 (slightly OTM). This would result in a lower exercise cost than intended.

Scenario 2:  Consider a position with a strike price very close to, but slightly below, the oracle price. Integer limitations might lead to maxNumRangesFromStrike being set to a higher value than intended, making the exercise cost appear more expensive than it should be for a nearly ATM option.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

659: uint256 maxNumRangesFromStrike = 1; // technically "maxNum(Half)RangesFromStrike" but the name is long

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L659

##

## [L-13] Missing Validation for ``salt``

The function relies on a user-defined salt for creating the Panoptic pool address using CREATE2. However, there's no explicit validation for the salt value. A malicious user could potentially provide an invalid salt that disrupts the expected address generation process.

```solidity
FILE: 2024-04-panoptic/contracts/PanopticFactory.sol

220: if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L220

##

## [L-14] Crafted salt value by an attacker could lead to a collision with another pool's address in the deployNewPool function

An attacker aiming for a collision would need to find a specific salt value that, when combined with the existing creation code and their own deployer address, results in the same address as a legitimate Panoptic pool deployed earlier. 

```solidity
FILE: 2024-04-panoptic/contracts/PanopticFactory.sol

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

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L210-L220

##

## [L-15] Denial-of-Service Risk Due to Excessive Looping in ``minePoolAddress()`` function

The minePoolAddress function relies on a loop that iterates for a specified number of times (loops) or until a certain target rarity (minTargetRarity) is achieved.

- The function calculates the rarity (leading zeros) of a potential pool address using another function (PanopticMath.numberOfLeadingHexZeros). This calculation itself might have some gas cost.
- It then compares the calculated rarity with the current highest rarity found so far.
- If a new highest rarity is discovered, the function updates the relevant variables.
- The loop increments a counter (often represented by a salt value) to generate a new potential pool address for the next iteration.

minePoolAddress function consumes more gas than the set limit during its execution (due to a high number of loop iterations), it will result in an out-of-gas error. The transaction will fail, and the user will only pay for the gas used up to the limit.

Practical Scenario:

Imagine a user sets loops to a very high value (e.g., 1000) and minTargetRarity to a challenging number (e.g., 5 leading zeros). In this case, the loop might need to iterate hundreds or even thousands of times before finding an address with the desired rarity. Each iteration consumes gas, and if the total gas cost exceeds the gas limit set by the user, the transaction will fail with an out-of-gas error.

```solidity
FILE: 2024-04-panoptic/contracts/PanopticFactory.sol

 for (; uint256(salt) < maxSalt; ) {
            uint256 rarity = PanopticMath.numberOfLeadingHexZeros(
                POOL_REFERENCE.predictDeterministicAddress(salt)
            );

            if (rarity > highestRarity) {
                // found a more rare address at this nonce
                highestRarity = rarity;
                bestSalt = salt;
            }

            if (rarity >= minTargetRarity) {
                // desired target met
                highestRarity = rarity;
                bestSalt = salt;
                break;
            }

            unchecked {
                // increment the nonce of `currentSalt` (lower 96 bits)
                salt = bytes32(uint256(salt) + 1);
            }
        }

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L303-L324

##

## [L-16] Malleability of "Rarity" Metric in ``minePoolAddress`` Function Weakens Security

The function assumes that a pool address with a higher number of leading zeros (calculated as "rarity") is more secure. This security assumption relies on the difficulty of brute-forcing an address with a desired number of leading zeros.

- While brute-forcing all possible addresses is computationally expensive, it's not entirely infeasible, especially for attackers with significant resources.

- An attacker with advanced knowledge of cryptography might be able to exploit weaknesses in the collision resistance properties of the hashing function used for address generation (e.g., keccak256). This could allow them to find collisions or alternative methods to generate addresses with a high number of leading zeros, bypassing the mining process entirely.

The function uses CREATE2 for deterministic address generation. While CREATE2 offers some security benefits, it doesn't guarantee complete protection against address prediction, especially for attackers with advanced knowledge of the creation bytecode and deployment logic.

```solidity
FILE: 2024-04-panoptic/contracts/PanopticFactory.sol

function minePoolAddress(
        bytes32 salt,
        uint256 loops,
        uint256 minTargetRarity
    ) external view returns (bytes32 bestSalt, uint256 highestRarity) {
        // Start at the given 'salt' value (a checkpoint used to continue mining across multiple calls)

        // Runs until 'bestSalt' reaches 'minTargetRarity' or for 'loops', whichever comes first
        uint256 maxSalt;
        unchecked {
            maxSalt = uint256(salt) + loops;
        }

        for (; uint256(salt) < maxSalt; ) {
            uint256 rarity = PanopticMath.numberOfLeadingHexZeros(
                POOL_REFERENCE.predictDeterministicAddress(salt)
            );

            if (rarity > highestRarity) {
                // found a more rare address at this nonce
                highestRarity = rarity;
                bestSalt = salt;
            }

            if (rarity >= minTargetRarity) {
                // desired target met
                highestRarity = rarity;
                bestSalt = salt;
                break;
            }

            unchecked {
                // increment the nonce of `currentSalt` (lower 96 bits)
                salt = bytes32(uint256(salt) + 1);
            }
        }
    }

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L290-L326

##

## [L-17] Fixed Liquidity Calculation in ``_mintFullRange`` Can Lead to Inefficiencies

The function injects a fixed amount of liquidity (FULL_RANGE_LIQUIDITY_AMOUNT_WETH or FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN) based on a pre-determined price range.
If the actual price range of the pool deviates from this assumption, the provided liquidity might not be sufficient to cover the entire range effectively.

Potential Consequences:

- Impermanent Loss (IL): Liquidity providers in Uniswap V3 pools are susceptible to impermanent loss if the price of the underlying tokens diverges significantly from the price at which they provided liquidity.
With an underestimation of the full-range liquidity, the provided liquidity might get concentrated in a smaller price range than intended. This can exacerbate impermanent loss if the price moves outside the covered range.
- Inefficient Capital Allocation:
If the fixed amount overestimates the actual liquidity needed, it leads to unnecessary capital being locked up in the pool. This reduces the potential returns for the liquidity provider.

Example Scenario:

Imagine the function uses a fixed amount of liquidity based on the assumption that the price of token0 will range between $10 and $100. However, in reality, the price range might be wider, say $5 and $150.

In this case, the provided liquidity won't cover the entire price range effectively. Liquidity providers might suffer from impermanent loss if the price moves outside the assumed range (e.g., below $5 or above $100).
Additionally, if the actual price range is much tighter (e.g., $10 and $20), the fixed amount might be an overkill, locking up more capital than necessary for that specific price range.

```solidity
FILE: 2024-04-panoptic/contracts/PanopticFactory.sol

unchecked {
            // Since we know one of the tokens is WETH, we simply add 0.1 ETH + worth in tokens
            if (token0 == WETH) {
                fullRangeLiquidity = uint128(
                    Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)
                );
            } else if (token1 == WETH) {
                fullRangeLiquidity = uint128(
                    Math.mulDivRoundingUp(
                        FULL_RANGE_LIQUIDITY_AMOUNT_WETH,
                        Constants.FP96,
                        currentSqrtPriceX96
                    )
                );
            } else {
                // Find the resulting liquidity for providing 1e6 of both tokens
                uint128 liquidity0 = uint128(
                    Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)
                );
                uint128 liquidity1 = uint128(
                    Math.mulDivRoundingUp(
                        FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,
                        Constants.FP96,
                        currentSqrtPriceX96
                    )
                );

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L348-L380

##

## [L-18] Unnecessary cache of ``_poolFee``

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

 // cache the pool fee in basis points
        uint24 _poolFee;
        unchecked {
            _poolFee = fee / 100;
        }

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L246-L250

##

## [L-19] Incorrect Comment for Burning Long Position

The comment /// @dev If the isLong flag is 1=long and the position is minted, then this is opening a long position describes the case where isLong is 1 and the position is burned. This seems like a contradiction. It should likely be corrected to /// @dev If the isLong flag is 1=long and the position is **not** burned, then this is opening a long position.

##

## [L-20] Risk of Missing Fee Collection in ``_createLegInAMM``

The function relies on the currentLiquidity.rightSlot() check to determine if fees need to be collected. This value represents the existing liquidity provided by the user at that specific price range (defined by the tick bounds). However, fees accrue continuously in Uniswap V3 pools based on trading activity.

If a user hasn't interacted with the pool at a specific price range for some time (e.g., hasn't minted or burned liquidity at that tick), currentLiquidity.rightSlot() might be zero. This would trigger the function to skip fee collection, even though fees might have accumulated since the last interaction.

Impact:

Users might miss out on collecting fees that have accrued on their existing liquidity positions.
This can lead to a discrepancy between the actual fees earned and the recorded fees within the Panoptic protocol.

```solidity
FILE: 2024-04-panoptic/contracts/SemiFungiblePositionManager.sol

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
            univ3pool,
            updatedLiquidity,
            liquidityChunk,
            true
        );
    }

    /// @notice caches/stores the accumulated premia values for the specified postion.
    /// @param positionKey the hashed data which re


```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L958-L1104