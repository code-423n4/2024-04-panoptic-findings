## A. Lack of Two-Step Ownership Transfer Mechanism
[PanopticFactory.sol#L147-L155](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L147-L155)
The contract lacks a two-step ownership transfer mechanism. Currently, ownership transfer is performed in a single step through the `transferOwnership` function. This function allows the current owner to transfer ownership directly to a new owner without any intermediary steps.
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
### Impact:
The absence of a two-step ownership transfer mechanism can introduce security risks, especially in scenarios where multiple parties are involved in ownership transitions. Without an intermediary step, there is a lack of validation or verification before the final ownership transfer occurs. This could potentially lead to unauthorized or unintended ownership changes, compromising the integrity and security of the contract.

### Mitigation:
Implement a two-step ownership transfer mechanism to enhance security and mitigate risks associated with direct ownership transfers. 
## B. Risk of Arithmetic Overflow and Underflow in ERC20 Token Contract
[ERC20Minimal.sol#L122-L131](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L122-L131)
[ERC20Minimal.sol#L136-L147](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L136-L147)
The ERC20 token contract provided in the code is susceptible to arithmetic overflow and underflow. Specifically, in functions such as `_mint` and `_burn`, there is a risk of overflow when updating the total supply and individual token balances. For instance, in the `_mint` function, if the total supply or an account's balance reaches the maximum value of `uint256`, adding more tokens could result in an overflow. Similarly, in the `_burn` function, subtracting tokens from an account's balance or decreasing the total supply without proper checks can lead to underflow if the balance is already zero.

```solidity
function _mint(address to, uint256 amount) internal {
    // Potential overflow here if balanceOf[to] or totalSupply is close to uint256 maximum value
    balanceOf[to] += amount;
    totalSupply += amount;
    
    emit Transfer(address(0), to, amount);
}

function _burn(address from, uint256 amount) internal {
    // Potential underflow here if balanceOf[from] is already zero
    balanceOf[from] -= amount;
    totalSupply -= amount;
    
    emit Transfer(from, address(0), amount);
}
```
### Impact:
The impact of an arithmetic overflow or underflow in the ERC20 token contract can lead to unexpected behavior and potential loss of funds. An overflow might result in falsely inflated token balances or total supply, while an underflow could cause balances to wrap around to the maximum value or become negative, leading to incorrect accounting of token ownership.
### Mitigation:
To mitigate the risk of arithmetic overflow and underflow, developers should implement comprehensive checks and safeguards in the token contract. One effective mitigation strategy is to use SafeMath library functions for arithmetic operations. 
```solidity
library SafeMath {
    function add(uint256 a, uint256 b) internal pure returns (uint256) {
        uint256 c = a + b;
        require(c >= a, "SafeMath: addition overflow");
        return c;
    }

    function sub(uint256 a, uint256 b) internal pure returns (uint256) {
        require(b <= a, "SafeMath: subtraction overflow");
        uint256 c = a - b;
        return c;
    }
}

```