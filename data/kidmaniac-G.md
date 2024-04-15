## Booleans are more expensive than uint256


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