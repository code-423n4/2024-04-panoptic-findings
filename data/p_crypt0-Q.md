# [informational / low] EIP-2612 Non-compliance - ERC20Minimal.sol
Unlike ERC115Minimal.sol which stipulates non-compliance in its pre-contract comments, ERC20Minimal does not forewarn users that the contract is non-compliant. However, ERC20Minimal contract does not implement the `permit` function which ensures EIP-2612 compliance.

Users expecting full compliance will likely experience unexpected behaviour.

# [low] Lack of Owner and ID length equivalence check can result in transaction reverting due to `index out of bound` runtime error.

```
/// @notice Query balances for multiple users and tokens at once.
    /// @dev `owners` and `ids` should be of equal length - solmate required them to be?
    /// @param owners The list of users to query balances for
    /// @param ids The list of ERC1155 token ids to query
    /// @return balances The balances for each owner-id pair in the same order as the input arrays
    function balanceOfBatch(
        address[] calldata owners,
        uint256[] calldata ids
    ) public view returns (uint256[] memory balances) {
        balances = new uint256[](owners.length);

        // Unchecked because the only math done is incrementing
        // the array index counter which cannot possibly overflow.
		
		//@audit: if owners.length > ids.length, or vice versa, index out of bounds error will be produced, causing transaction to revert. Error handling would be appropriate.
        unchecked {
            for (uint256 i = 0; i < owners.length; ++i) {
                balances[i] = balanceOf[owners[i]][ids[i]];
            }
        }
    }
```

To avoid this, create a custom error: `error LengthMismatch()` and call it when the lengths are not equal along with the `revert command`

Please see the following:

```
error LengthMismatch();
/// @notice Query balances for multiple users and tokens at once.
    /// @dev `owners` and `ids` should be of equal length - solmate required them to be?
    /// @param owners The list of users to query balances for
    /// @param ids The list of ERC1155 token ids to query
    /// @return balances The balances for each owner-id pair in the same order as the input arrays
    function balanceOfBatch(
        address[] calldata owners,
        uint256[] calldata ids
    ) public view returns (uint256[] memory balances) {
		if (owners.length != ids.length){
			revert LengthMismatch();
		}
        balances = new uint256[](owners.length);

        // Unchecked because the only math done is incrementing
        // the array index counter which cannot possibly overflow.
		
        unchecked {
            for (uint256 i = 0; i < owners.length; ++i) {
                balances[i] = balanceOf[owners[i]][ids[i]];
            }
        }
    }
```