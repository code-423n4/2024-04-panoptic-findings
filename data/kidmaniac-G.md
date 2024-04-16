## [G-01] Booleans are more expensive than uint256


Using bools is costlier than using uint256 or other types that occupy a full word in storage. Using `bool` data type for storage in Solidity can incur unnecessary gas costs, especially when changing states from `false` to `true` after having been true in the past.

To mitigate these gas costs, you can utilize `uint256` values `uint256(1)` and `uint256(2)` to represent `true` and `false` respectively.

Consider rewriting as following to save gas:

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L115C4-L118C6>
```solidity
File: ./contracts/SemiFungiblePositionManager.sol
115:   struct PoolAddressAndLock {
116:      IUniswapV3Pool pool;
- 117:      bool locked;
+ 117:      uint256 locked;
118:   }
```

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L320-L326>
```solidity
File: ./contracts/SemiFungiblePositionManager.sol
320:    function beginReentrancyLock(uint64 poolId) internal {
321:          // check if the pool is already locked, if so, revert
- 322:        if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();
+ 322:        if (s_poolContext[poolId].locked == 1) revert Errors.ReentrantCall();
323:
324:          // activate lock
- 325:        s_poolContext[poolId].locked = true;
+ 325:        s_poolContext[poolId].locked = 1;
326    }
```

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L330-L333>
```solidity
File: ./contracts/SemiFungiblePositionManager.sol
330:    function endReentrancyLock(uint64 poolId) internal {
331:        // gas refund is triggered here by returning the slot to its original value
- 332:        s_poolContext[poolId].locked = false;
+ 332:        s_poolContext[poolId].locked = 2;
333:    }
```

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L549>
```solidity
File: ./contracts/SemiFungiblePositionManager.sol
- 549:        if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();
+ 549:        if (s_poolContext[TokenId.wrap(id).poolId()].locked == 1) revert Errors.ReentrantCall();

```

<https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L576>
```solidity
- 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
+ 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked == 1) revert Errors.ReentrantCall();
```

## Tools used
Manual audit

## [G-02] Use `assembly` for efficient event emission

We can use assembly to emit events efficiently by utilizing `scratch space` and the `free memory pointer`. This will allow us to potentially avoid memory expansion costs.

**Note: In order to do this optimization safely, we will need to cache and restore the free memory pointer.**

You can find excellent examples of these practices within [Solady's](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) finely optimized codebase.

14 issues instances in 4 main files:

```solidity
 File: ./contracts/CollateralTracker.sol
 439: emit Deposit(msg.sender, receiver, assets, shares);
 499: emit Deposit(msg.sender, receiver, assets, shares);
 563: emit Withdraw(msg.sender, receiver, owner, assets, shares);
 623: emit Withdraw(msg.sender, receiver, owner, assets, shares);
```
[439](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L439) | [499](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L499) | [563](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L563) | [623](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L623)

```solidity
 File: ./contracts/PanopticFactory.sol
 154: emit OwnershipTransferred(currentOwner, newOwner);
 268: emit PoolDeployed(
            newPoolContract,
            v3Pool,
            collateralTracker0,
            collateralTracker1,
            amount0,
            amount1
        );
```

[154](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L154) | [268](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L268)

```solidity
 File: ./contracts/PanopticPool.sol
 666:  emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);
 853:  emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);
 1170: emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);
 1277: emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);
 1654: emit PremiumSettled(owner, tokenId, realizedPremia);
```

[666](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L666) | [853](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L853) | [1170](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1170) | [1277](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1277) | [1654](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1654)

```solidity
 File: ./contracts/SemiFungiblePositionManager.sol
 390: emit PoolInitialized(univ3pool, poolId);
 485: emit TokenizedPositionBurnt(msg.sender, tokenId, positionSize);
 517: emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);
```

[390](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L390) | [485](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L485) | [517](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L517)

## Tools used
Manual audit

