# [G-01]Remove unnecessary revert statements

Since [initializeAMMPool](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L354C1-L362C56) function has checked whether v3 pool has been initialized and the pool has been initialized in SFPM in SemiFungiblePositionManager.sol contract, there is no requirement of revert check in [deployNewPool](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L227C1-L230C52) function of PanopticFactory contract starting at line 227. 

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

Consider removing the check:

[PanopticFactory::deployNewPool#L227-230](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L227C1-L230C52)


```solidity

-       if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

-       if (address(s_getPanopticPool[v3Pool]) != address(0))
            revert Errors.PoolAlreadyInitialized();


```

# [G-02] Cache `numLegs` storage in memory outside of nested for loops

By caching the `numLegs` outside of loops, this could be handled in the same way with all other `countLegs()` in those contracts of our Panoptic projects.

[TokenId.sol::validate#L507-524](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L507C1-L524C18)

```solidity

            for (uint256 i = 0; i < 4; ++i) {
                if (self.optionRatio(i) == 0) {                   
                    if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)
                        revert Errors.InvalidTokenIdParameter(1);
                    break; 
                }

                //@audit cache `numLegs` outside from nested for loops
                uint256 numLegs = self.countLegs();
                for (uint256 j = i + 1; j < numLegs; ++j) {
                    if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {
                        revert Errors.InvalidTokenIdParameter(6);
                    }
                }
```
Recommended Mitigation Steps

```solidity

+           uint256 numLegs = self.countLegs();
            for (uint256 i = 0; i < 4; ++i) {
                if (self.optionRatio(i) == 0) {                   
                    if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)
                        revert Errors.InvalidTokenIdParameter(1);
                    break; 
                }

- 519:           uint256 numLegs = self.countLegs();
                for (uint256 j = i + 1; j < numLegs; ++j) {
                    if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {
                        revert Errors.InvalidTokenIdParameter(6);
                    }
                }
```

Additionally, `countLegs()` in the `exerciseCost` function of the `CollateralTracker.sol` contract could be handled in the same way too.

[CollateralTracker.sol::exerciseCost#L662](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L662C1-L662C73)

```solidity
- 662:       for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {
+            uint256 numLegs = positionId.countLegs();
+            for (uint256 leg = 0; leg < numLegs; ++leg) {
```