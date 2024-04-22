# QA Report

## [L-01] `PanopticPool` and `CollateralTracker` underlying implementation can be initialized by anyone

### Bug Description

Both `PanopticPool` and `CollateralTracker` are deployed using the proxy pattern, using the reference to their underlying implementation. However, the underlying implementation can be initialized by anyone with any parameters, and may cause confusion.

### Code Snippet

- https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291
- https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221

### Recommendation

Disable initialization in constructor of these two contracts.

## [L-02] CollateralTracker is not ERC20 compliant

### Bug Description

In CollateralTracker, it is initialized with `totalSupply = 10**6` virtual shares. This is equivalent to minting `10**6` share tokens, which should emit a Transfer event according to EIP20.
```
A token contract which creates new tokens SHOULD trigger a Transfer event with the _from address set to 0x0 when tokens are created.
```

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
>       totalSupply = 10 ** 6;
        ...
    }
```

### Code Snippet

- https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L234

### Recommendation

Emit Transfer event during `startToken`.