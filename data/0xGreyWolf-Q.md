# `PanopticFactory::initialize()` can be front-ran
## Description
The `initialize()` function intializes the `_owner` address. However, this function can be called by anyone. An attacker can initialize and set his / her own address in the contract before the protocol deployer does with the hopes that it will go unnoticed. 

- [`initialize()`](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L132-L139)
    ```solidity
    /// @notice Initialize state.
    /// @param _owner The first owner of `PanopticFactory`

    function initialize(address _owner) public {
        if (!s_initialized) {
            s_owner = _owner;
            s_initialized = true;
        }
    }
    ```
Looking at the code above, calling the function (the 2nd time) does not tell if the contract is initialized or not. It just stays silent. State variable `s_initialized` which supposed to tell whether the contract is initialized or not is `internal`. The only convenient way to check if the ownership is compromised is by calling the function `owner()` and check if the address is the intended `owner`. Still, there is a possibility (although slim) that this attack may get unnoticed. 

```solidity
/// @notice Whether this contract's state has been initialized
bool internal s_initialized;
```

## Impact
If the protocol team notices it, the impact is limited to the cost of gas and time inconvenience.

## Proof of Concept
## Tools Used
Manual Review

## Recommended Mitigation Steps
1. Invoke `initialize()` in the constructor 
2. Or delete the `initialize()` function and just set the `owner` in the constructor