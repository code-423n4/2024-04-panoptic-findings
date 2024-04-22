## [L-1] Missed check user can send 0 amount

there is no check when user try to send 0 amount.

```solidity
function transfer(address to, uint256 amount) public virtual returns (bool) {
        balanceOf[msg.sender] -= amount;

        // Cannot overflow because the sum of all user
        // balances can't exceed the max uint256 value.
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(msg.sender, to, amount);

        return true;
    }
```
## [L-2] Missed check user can send to zero address 

should include a check to prevent sending tokens to the zero address in the transfer function.
```solidity
function transfer(address to, uint256 amount) public virtual returns (bool) {
        balanceOf[msg.sender] -= amount;

        // Cannot overflow because the sum of all user
        // balances can't exceed the max uint256 value.
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(msg.sender, to, amount);

        return true;
    }
```

## [L-3] `setApprovalForAll` must revert when approving self

You should add a check to ensure that the user cannot approve themselves in the setApprovalForAll function.
```solidity
function setApprovalForAll(address operator, bool approved) public {
        isApprovedForAll[msg.sender][operator] = approved;

        emit ApprovalForAll(msg.sender, operator, approved);
    }
```

## [L-4] User can send to zero address .

Both `safeTransferFrom` and `safeBatchTransferFrom` functions should revert if the destination address `to` is the zero address.

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
                ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
                ERC1155Holder.onERC1155BatchReceived.selector
            ) {
                revert UnsafeRecipient();
            }
        }
    }
```

## [L-5] user setting approval status for self

The `setApprovalForAll` function should not allow users to set approval status for themselves.

```solidity
    function setApprovalForAll(address operator, bool approved) public {
        isApprovedForAll[msg.sender][operator] = approved;

        emit ApprovalForAll(msg.sender, operator, approved);
    }
```

## [L-6] Missed check it the operator is zero address

You should add a check to ensure that the operator address is not the zero address in the `setApprovalForAll` function.

```solidity
    function setApprovalForAll(address operator, bool approved) public {
        isApprovedForAll[msg.sender][operator] = approved;

        emit ApprovalForAll(msg.sender, operator, approved);
    }
```

## [L-7] Array length mismatch 

There's a potential issue with array length mismatch in the `safeBatchTransferFrom` function. You should ensure that the `ids` and `amounts` arrays have the same length.

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
                ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
                ERC1155Holder.onERC1155BatchReceived.selector
            ) {
                revert UnsafeRecipient();
            }
        }
    }
```

```solidity
function balanceOfBatch(
        address[] calldata owners,
        uint256[] calldata ids
    ) public view returns (uint256[] memory balances) {
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

## [L-8] `ERC1155Minimal.sol`  doesn't respect EIP1155

The `ERC1155Minimal.sol` file is missing the `isApprovedForAll` function, which is necessary for respecting EIP1155.

## [L-9] Can mint to zero address

In the `_mint` function, you should add a check to prevent minting tokens to the zero address.

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

## [L-10] Solmate's ERC20 does not check for token contract's existence

since the contract uses Solmate's SafeTransferLib

> /// @dev Note that none of the functions in this library check that a token has code at all! That responsibility is delegated to the caller.

Therefore if the token address is empty, the transfer will succeed silently, but not crediting the contract with any tokens.

## [L-11] Return values of approve not checked 

Not all IERC20 implementations (e.g. USDT, KNC) revert when there's a failure in approve. The function signature has a boolean return value and they indicate errors that way instead.By not checking the return value, operations that should have marked as failed, may potentially go through without actually approving anything.

```solidity
34:        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

35:        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

38:        IERC20Partial(token0).approve(address(ct0), type(uint256).max);

39:        IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```

*GitHub* : [InteractionHelper.sol#L34](https://github.com/code-423n4/2024-03-coinbase/tree/main/./contracts/libraries/InteractionHelper.sol#L34),[InteractionHelper.sol#L35](https://github.com/code-423n4/2024-03-coinbase/tree/main/./contracts/libraries/InteractionHelper.sol#L35),[InteractionHelper.sol#L38](https://github.com/code-423n4/2024-03-coinbase/tree/main/./contracts/libraries/InteractionHelper.sol#L38),[InteractionHelper.sol#L39](https://github.com/code-423n4/2024-03-coinbase/tree/main/./contracts/libraries/InteractionHelper.sol#L39)

## [L-12] Some tokens do not consider `type(uint256).max` as an infinite approval

Some tokens such as [COMP](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L89-L91) downcast such approvals to uint96 and use that as a raw value rather than interpreting it as an infinite approval. Eventually these approvals will reach zero, at which point the calling contract will no longer function properly.

```solidity
34:        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

35:        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

38:        IERC20Partial(token0).approve(address(ct0), type(uint256).max);

39:        IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```

*GitHub* : [InteractionHelper.sol#L34](https://github.com/code-423n4/2024-03-coinbase/tree/main/./contracts/libraries/InteractionHelper.sol#L34),[InteractionHelper.sol#L35](https://github.com/code-423n4/2024-03-coinbase/tree/main/./contracts/libraries/InteractionHelper.sol#L35),[InteractionHelper.sol#L38](https://github.com/code-423n4/2024-03-coinbase/tree/main/./contracts/libraries/InteractionHelper.sol#L38),[InteractionHelper.sol#L39](https://github.com/code-423n4/2024-03-coinbase/tree/main/./contracts/libraries/InteractionHelper.sol#L39)