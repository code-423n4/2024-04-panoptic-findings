# Remove unnecessary revert statements

Since [initializeAMMPool](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L354C1-L362C56) function has checked whether v3 pool has been initialized and the pool has been initialized in SFPM in SemiFungiblePositionManager.sol contract, there is no requirement of revert check in [deployNewPool](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L227C1-L230C52) function of PanopticFactory starting at line 227. 

[SemiFungiblePositionManager::initializeAMMPool#L354-362](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L354C1-L362C56)

```solidity
        // reverts if the Uni v3 pool has not been initialized
        if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

        // return if the pool has already been initialized in SFPM
        // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting
        // would prevent any PanopticPool from being deployed
        // @dev some pools may not be deployable if the poolId has a collision (since we take only 8 bytes)
        // if poolId == 0, we have a bit on the left set if it was initialized, so this will still return properly
        if (s_AddrToPoolIdData[univ3pool] != 0) return;
```

Remove the below require statement:

[PanopticFactory::deployNewPool#L227-230](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L227C1-L230C52)


```solidity

        if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

        if (address(s_getPanopticPool[v3Pool]) != address(0))
            revert Errors.PoolAlreadyInitialized();

```