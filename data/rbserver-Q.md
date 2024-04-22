## QA REPORT

|      | Issue                                                                                                                  |
| ---- | :--------------------------------------------------------------------------------------------------------------------- |
| [01] | `maxRedeem` FUNCTION ROUNDS DOWN `available`, WHICH IS NOT COMPLIANT TO EIP-4626 STANDARD                              |
| [02] | `name` FUNCTION IS NOT COMPLIANT TO EIP-4626 STANDARD                                                                  |
| [03] | CALLING `Math.getLiquidityForAmount0` AND `Math.getLiquidityForAmount1` FUNCTIONS CAN REVERT WITH `CastingError` ERROR |
| [04] | `SafeTransferLib.safeTransferFrom` FUNCTION DOES NOT CHECK FOR TOKEN'S EXISTENCE                                       |
| [05] | CALLING `deposit` FUNCTION CAN CAUSE USER TO MINT 0 SHARES BUT DEPOSIT SOME ASSETS                                     |
| [06] | MISSING CHECK THAT REQUIRES `_commissionFee` TO BE CAPPED BY A REASONABLE VALUE                                        |
| [07] | MISSING CHECK THAT REQUIRES `_ITMSpreadMultiplier` TO BE AT LEAST A REASONABLE POSITIVE VALUE                          |
| [08] | EVENT EMISSIONS OF `deposit`, `mint`, `withdraw`, AND `redeem` FUNCTIONS CAN BE POISONED                               |

## [01] `maxRedeem` FUNCTION ROUNDS DOWN `available`, WHICH IS NOT COMPLIANT TO EIP-4626 STANDARD
The following `maxRedeem` function executes `uint256 available = convertToShares(s_poolAssets)` to calculate the available number of shares corresponding to `s_poolAssets`. Because the `convertToShares` function below rounds down, such `available` is rounded down. This is different from the `previewWithdraw` function below, which rounds up `shares` when converting `assets` to `shares`. Hence, when `available` is less than `balance` in the `maxRedeem` function, the rounded down `available` is the `maxShares` that the user can at most redeem when calling the `redeem` function below. Since such `maxShares` is rounded down, calling the `redeem` function can only allow the user to at most redeem a number of shares that is less than what she or he would burn through a `withdraw` function call for withdrawing the same `s_poolAssets` amount of assets.

Moreover, https://eips.ethereum.org/EIPS/eip-4626#security-considerations states `EIP-4626 Vault implementers should be aware of the need for specific, opposing rounding directions across the different mutable and view methods, as it is considered most secure to favor the Vault itself during calculations over its users:` `If (1) it’s calculating the amount of shares a user has to supply to receive a given amount of the underlying tokens`. To be compliant to the EIP-4626 standard, shares to be burned should be rounded up for withdrawing a given amount of assets. Allowing the user to call the `redeem` function to at most burn a number of shares that is less than what the `withdraw` function call would burn for withdrawing the same `s_poolAssets` amount of assets makes the `maxRedeem` function not be compliant to the EIP-4626 standard.

As a mitigation, the `maxRedeem` function can be updated to execute `uint256 available = previewWithdraw(s_poolAssets)` instead of `uint256 available = convertToShares(s_poolAssets)`.

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L572-L576
```solidity
    function maxRedeem(address owner) public view returns (uint256 maxShares) {
        uint256 available = convertToShares(s_poolAssets);
        uint256 balance = balanceOf[owner];
        return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L379-L381
```solidity
    function convertToShares(uint256 assets) public view returns (uint256 shares) {
        return Math.mulDiv(assets, totalSupply, totalAssets());
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L518-L522
```solidity
    function previewWithdraw(uint256 assets) public view returns (uint256 shares) {
        uint256 supply = totalSupply; // Saves an extra SLOAD if totalSupply is non-zero.

        return Math.mulDivRoundingUp(assets, supply, totalAssets());
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L591-L626
```solidity
    function redeem(
        uint256 shares,
        address receiver,
        address owner
    ) external returns (uint256 assets) {
        if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();

        ...
    }
```

## [02] `name` FUNCTION IS NOT COMPLIANT TO EIP-4626 STANDARD
The following `name` function calls the `computeName` function below to create the name for a CollateralTracker. Based on https://eips.ethereum.org/EIPS/eip-4626, `All EIP-4626 tokenized Vaults MUST implement EIP-20’s optional metadata extensions. The ``name`` and ``symbol`` functions SHOULD reflect the underlying token’s ``name`` and ``symbol`` in some way.`  Because the `computeName` function only uses the underlying tokens' symbols, the name returned by the `name` function does not include information about the underlying tokens' names. Hence, the `name` function is not compliant to the EIP-4626 standard. To mitigate this, the `computeName` function can be updated to use the underlying tokens' names instead of their symbols.

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L289-L299
```solidity
    function name() external view returns (string memory) {
        // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size
        return
            InteractionHelper.computeName(
                s_univ3token0,
                s_univ3token1,
                s_underlyingIsToken0,
                s_poolFee,
                NAME_PREFIX
            );
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/libraries/InteractionHelper.sol#L48-L85
```solidity
    function computeName(
        address token0,
        address token1,
        bool isToken0,
        uint24 fee,
        string memory prefix
    ) external view returns (string memory) {
        // get the underlying token symbols
        // it's not guaranteed that they support the metadata extension
        // so we need to let them fail and return placeholder if not
        string memory symbol0;
        string memory symbol1;
        try IERC20Metadata(token0).symbol() returns (string memory _symbol) {
            symbol0 = _symbol;
        } catch {
            symbol0 = "???";
        }
        try IERC20Metadata(token1).symbol() returns (string memory _symbol) {
            symbol1 = _symbol;
        } catch {
            symbol1 = "???";
        }
        unchecked {
            return
                string.concat(
                    prefix,
                    " ",
                    isToken0 ? symbol0 : symbol1,
                    " LP on ",
                    symbol0,
                    "/",
                    symbol1,
                    " ",
                    Strings.toString(fee),
                    "bps"
                );
        }
    }
```

## [03] CALLING `Math.getLiquidityForAmount0` AND `Math.getLiquidityForAmount1` FUNCTIONS CAN REVERT WITH `CastingError` ERROR
The following `getLiquidityForAmount0` and `getLiquidityForAmount1` functions call the `toUint128` function below when calculating the respective amount of liquidity. For `amount0` and `amount1` that are less than `type(uint128).max`, calling these `getLiquidityForAmount0` and `getLiquidityForAmount1` functions can unexpectedly revert due to `toUint128`. Because important functions like `PanopticPool.settleLongPremium`, `PanopticPool._updateSettlementPostMint`, and `PanopticPool._updateSettlementPostBurn` eventually call the `getLiquidityForAmount0` and `getLiquidityForAmount1` functions, calling functions like `PanopticPool.burnOptions`, which eventually call these important functions, can revert if `amount0` or `amount1`, which is less than `type(uint128).max`, is high enough to make the `getLiquidityForAmount0` or `getLiquidityForAmount1` function call revert. For example, the user can be unexpectedly DOS'ed when burning options.

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/libraries/Math.sol#L241-L263
```solidity
    function getLiquidityForAmount0(
        int24 tickLower,
        int24 tickUpper,
        uint256 amount0
    ) internal pure returns (LiquidityChunk) {
        uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);
        uint160 highPriceX96 = getSqrtRatioAtTick(tickUpper);

        unchecked {
            return
                LiquidityChunkLibrary.createChunk(
                    tickLower,
                    tickUpper,
                    toUint128(
                        mulDiv(
                            amount0,
                            mulDiv96(highPriceX96, lowPriceX96),
                            highPriceX96 - lowPriceX96
                        )
                    )
                );
        }
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/libraries/Math.sol#L271-L287
```solidity
    function getLiquidityForAmount1(
        int24 tickLower,
        int24 tickUpper,
        uint256 amount1
    ) internal pure returns (LiquidityChunk) {
        uint160 lowPriceX96 = getSqrtRatioAtTick(tickLower);
        uint160 highPriceX96 = getSqrtRatioAtTick(tickUpper);

        unchecked {
            return
                LiquidityChunkLibrary.createChunk(
                    tickLower,
                    tickUpper,
                    toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))
                );
        }
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/libraries/Math.sol#L296-L298
```solidity
    function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {
        if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();
    }
```

The following tests can be added in `test\foundry\libraries\Math.t.sol`, and these tests will pass to demonstrate the described scenarios.

```solidity
    function test_getLiquidityForAmount0RevertsWithCastingError() public {
        // amount0 is smaller than type(uint128).max
        uint128 amount0 = 408359281065716608791339802364529987;
        assertLt(amount0, type(uint128).max);

        // getLiquidityForAmount0 can revert with CastingError
        vm.expectRevert(Errors.CastingError.selector);
        harness.getLiquidityForAmount0(int24(-14), int24(10), amount0);
    }
```

```solidity
    function test_getLiquidityForAmount1RevertsWithCastingError() public {
        // amount1 is smaller than type(uint128).max
        uint128 amount1 = 408277621458648664471958765892009984;
        assertLt(amount1, type(uint128).max);

        // getLiquidityForAmount1 can revert with CastingError
        vm.expectRevert(Errors.CastingError.selector);
        harness.getLiquidityForAmount1(int24(-14), int24(10), amount1);
    }
```

As a mitigation, the `getLiquidityForAmount0` and `getLiquidityForAmount1` functions can be updated to call the `toUint128Capped` function instead of the `toUint128` function.

## [04] `SafeTransferLib.safeTransferFrom` FUNCTION DOES NOT CHECK FOR TOKEN'S EXISTENCE
The following `deposit`, `mint`, `withdraw`, and `redeem` functions use Solmate's `SafeTransferLib.safeTransferFrom` function below to transfer the underlying token between the user and the Panoptic pool. Since such `safeTransferFrom` function does not check whether the token has code or not, if the token's contract is destroyed for some reason or a Uniswap pool, which is linked by the Panoptic pool, is somehow set for a token address that does not have a contract yet, users can unexpectedly mint shares without depositing any assets or burn shares without withdrawing any assets. To mitigate this, OpenZeppelin's `SafeERC20.safeTransferFrom` function that does check for the token's existence can be used instead of Solmate's `SafeTransferLib.safeTransferFrom` function in the `deposit`, `mint`, `withdraw`, and `redeem` functions.

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L417-L440
```solidity
    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
        ...
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        );
        ...
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L477-L500
```solidity
    function mint(uint256 shares, address receiver) external returns (uint256 assets) {
        ...
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        );
        ...
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L531-L566
```solidity
    function withdraw(
        uint256 assets,
        address receiver,
        address owner
    ) external returns (uint256 shares) {
        ...
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        );
        ...
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L591-L626
```solidity
    function redeem(
        uint256 shares,
        address receiver,
        address owner
    ) external returns (uint256 assets) {
        ...
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        );
        ...
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/libraries/SafeTransferLib.sol#L21-L46
```solidity
    function safeTransferFrom(address token, address from, address to, uint256 amount) internal {
        bool success;

        assembly ("memory-safe") {
            // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
            let p := mload(0x40)

            // Write the abi-encoded calldata into memory, beginning with the function selector.
            mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)
            mstore(add(4, p), from) // Append the "from" argument.
            mstore(add(36, p), to) // Append the "to" argument.
            mstore(add(68, p), amount) // Append the "amount" argument.

            success := and(
                // Set success to whether the call reverted, if not we check it either
                // returned exactly 1 (can't just be non-zero data), or had no return data.
                or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
                // We use 100 because that's the total length of our calldata (4 + 32 * 3)
                // Counterintuitively, this call() must be positioned after the or() in the
                // surrounding and() because and() evaluates its arguments from right to left.
                call(gas(), token, 0, p, 100, 0, 32)
            )
        }

        if (!success) revert Errors.TransferFailed();
    }
```

## [05] CALLING `deposit` FUNCTION CAN CAUSE USER TO MINT 0 SHARES BUT DEPOSIT SOME ASSETS
The higher `COMMISSION_FEE` is, the more likely that the following `previewDeposit` function returns 0 `shares` for a positive `assets`. When the `previewDeposit` function returns 0 `shares` for a positive `assets`, calling the `deposit` function below will cause the user to mint 0 shares but deposit some assets. To prevent this situation, a check can be added in the `deposit` function to make it revert if `shares` equals 0 while `assets` is positive.

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L399-L408
```solidity
    function previewDeposit(uint256 assets) public view returns (uint256 shares) {
        // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid
        unchecked {
            shares = Math.mulDiv(
                assets * (DECIMALS - COMMISSION_FEE),
                totalSupply,
                totalAssets() * DECIMALS
            );
        }
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L417-L440
```solidity
    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
        ...
        shares = previewDeposit(assets);
        ...
        // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
        _mint(receiver, shares);
        ...
    }
```

## [06] MISSING CHECK THAT REQUIRES `_commissionFee` TO BE CAPPED BY A REASONABLE VALUE
When setting `COMMISSION_FEE` in the `CollateralTracker` contract's `constructor`, there is no check that requires `_commissionFee` to be capped by a reasonable value. When `COMMISSION_FEE` is set to be higher than `DECIMALS`, the `previewDeposit` and `previewMint` functions below would return unexpected values because the `unchecked` blocks allow `DECIMALS - COMMISSION_FEE` to underflow. As a mitigation, a check can be added in the `constructor` to require `_commissionFee` to be capped by a reasonable value that is less or equal to `DECIMALS`.

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L178-L211
```solidity
    constructor(
        uint256 _commissionFee,
        uint256 _sellerCollateralRatio,
        uint256 _buyerCollateralRatio,
        int256 _forceExerciseCost,
        uint256 _targetPoolUtilization,
        uint256 _saturatedPoolUtilization,
        uint256 _ITMSpreadMultiplier
    ) {
        COMMISSION_FEE = _commissionFee;
        ...
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L399-L408
```solidity
    function previewDeposit(uint256 assets) public view returns (uint256 shares) {
        ...
        unchecked {
            shares = Math.mulDiv(
                assets * (DECIMALS - COMMISSION_FEE),
                totalSupply,
                totalAssets() * DECIMALS
            );
        }
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L453-L468
```solidity
    function previewMint(uint256 shares) public view returns (uint256 assets) {
        ...
        unchecked {
            assets = Math.mulDivRoundingUp(
                shares * DECIMALS,
                totalAssets(),
                totalSupply * (DECIMALS - COMMISSION_FEE)
            );
        }
    }
```

## [07] MISSING CHECK THAT REQUIRES `_ITMSpreadMultiplier` TO BE AT LEAST A REASONABLE POSITIVE VALUE
When calling the `CollateralTracker` contract's `constructor`, `ITM_SPREAD_MULTIPLIER` can be set to as low as 0 since there is no check that requires `_ITMSpreadMultiplier` to be at least a reasonable positive value. Because `_poolFee` can be as low as 5, it is possible that calling the `startToken` function below can set `s_ITMSpreadFee` to 0 when `ITM_SPREAD_MULTIPLIER` is smaller than 2000, which can unexpectedly cause no additional risk premium to be charged on intrinsic value of ITM positions. To avoid unexpected situations like that, a check can be added in the `CollateralTracker` contract's `constructor` to require `_ITMSpreadMultiplier` to be at least a reasonable positive value.

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L178-L211
```solidity
    constructor(
        uint256 _commissionFee,
        uint256 _sellerCollateralRatio,
        uint256 _buyerCollateralRatio,
        int256 _forceExerciseCost,
        uint256 _targetPoolUtilization,
        uint256 _saturatedPoolUtilization,
        uint256 _ITMSpreadMultiplier
    ) {
        ...
        ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;

        ...
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L221-L264
```solidity
    function startToken(
        bool underlyingIsToken0,
        address token0,
        address token1,
        uint24 fee,
        PanopticPool panopticPool
    ) external {
        ...

        // Additional risk premium charged on intrinsic value of ITM positions
        unchecked {
            s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);
        }
    }
```

## [08] EVENT EMISSIONS OF `deposit`, `mint`, `withdraw`, AND `redeem` FUNCTIONS CAN BE POISONED
Calling the following `deposit`, `mint`, `withdraw`, and `redeem` functions respectively with 0 as the corresponding `assets` or `shares` input can emit meaningless `Deposit` or `Withdraw` event. Doing this repeatedly can spam the event logs and poison the monitor system that consumes these events. To mitigate, these functions can be updated to revert when the corresponding `assets` or `shares` input is 0.

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L417-L440
```solidity
    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
        if (assets > type(uint104).max) revert Errors.DepositTooLarge();
        ...
        emit Deposit(msg.sender, receiver, assets, shares);
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L477-L500
```solidity
    function mint(uint256 shares, address receiver) external returns (uint256 assets) {
        ...
        emit Deposit(msg.sender, receiver, assets, shares);
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L531-L566
```solidity
    function withdraw(
        uint256 assets,
        address receiver,
        address owner
    ) external returns (uint256 shares) {
        if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();
        ...
        emit Withdraw(msg.sender, receiver, owner, assets, shares);
        ...
    }
```

https://github.com/code-423n4/2024-04-panoptic/blob/58dda1b3b74e48f4d924731ec5da14096043fde0/contracts/CollateralTracker.sol#L591-L626
```solidity
    function redeem(
        uint256 shares,
        address receiver,
        address owner
    ) external returns (uint256 assets) {
        if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();
        ...
        emit Withdraw(msg.sender, receiver, owner, assets, shares);
        ...
    }
```