# Code and comment mismatch

In CollateralTracker.sol, lines 321 and 338 it says `"the caller must have a balance of at least 'amount'"` and `"the 'from' must have a balance of at least 'amount'"`, but the functions `transfer` and `transferFrom` do not check whether they have enough balance. Consider either removing those comments or putting the code to meet the requirments as shown below:

[CollateralTracker.sol#L321](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L321C1-L321C63)
[CollateralTracker.sol#L338](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L338C1-L338C63)

```solidity

    /// @dev See {IERC20-transfer}.
    /// Requirements:
    /// - the caller must have a balance of at least 'amount'.
    /// - the msg.sender must not have any position on the panoptic pool
    function transfer(
        address recipient,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool) {
        // make sure the caller does not have any open option positions
        // if they do: we don't want them sending panoptic pool shares to others
        // since that's like reducing collateral

+       uint256 balance = balanceOf[msg.sender];
+       require(balance >= amount, "TRANSFER_AMOUNT_EXCEEDS_BALANCE");

        if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

        return ERC20Minimal.transfer(recipient, amount);
    }

    /// @dev See {IERC20-transferFrom}.
    /// Requirements:
    /// - the 'from' must have a balance of at least 'amount'.
    /// - the caller must have allowance for 'from' of at least 'amount' tokens.
    /// - 'from' must not have any open positions on the panoptic pool.
    function transferFrom(
        address from,
        address to,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool) {
        // make sure the caller does not have any open option positions
        // if they do: we don't want them sending panoptic pool shares to others
        // as this would reduce their amount of collateral against the opened positions

+       uint256 allowed = allowance[from][msg.sender];
+       require(allowed >= amount, "TRANSFER_AMOUNT_EXCEEDS_ALLOWANCE");

        if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

        return ERC20Minimal.transferFrom(from, to, amount);
    }
```