## L-01: Unchecked Uniswap V3 pool initialization

## Impact
In the [initializeAMMPool](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350-L391) function, it checks if the pool has already been initialized in SFPM and returns if so. However, it does not revert if the pool is uninitialized in Uniswap V3. This could lead to unexpected behavior if `initializeAMMPool` is called on a V3 pool before it's created.

## Recommendation
Add check

## L-02: Unchecked return value from `SFPM.burnTokenizedPosition`

## Impact
In the [_burnAndHandleExercise](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L955-L1005) function, the return values `LeftRightUnsigned[4]` memory and `LeftRightSigned `from [SFPM.burnTokenizedPosition](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L471-L495) are not checked. If the SFPM function fails, the Panoptic pool may not detect it and continue processing with invalid data.

## Recommendation
Consider adding checks on the return values.

## L-03: Unchecked `positionSize` in `mintOptions`

## Impact
The [mintOptions](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L547-L561) function does not check if `positionSize` is greater than zero. Minting a position with zero size doesn't make sense and wastes gas. 

## Recommendation
Consider adding a requirement that `positionSize > 0`.