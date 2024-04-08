In `PanopticFactory.sol`, make sure to emit an event when initializing the owner and setting the `s_initialized` bool to true. This creates a transparent and immutable record of the initialization, making it easier to track when and by whom the contract was initialized.

```
function initialize(address _owner) public {
    if (!s_initialized) {
        s_owner = _owner;
        s_initialized = true;
    } /// @audit Make sure to emit an event for initializing
}
```

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134