## L-1: Usage of `delegatecall` in for loop:

When `delegatecall` gets called the same `msg.value` amount will be accredited multiple times.

@> contracts/multicall/Multicall.sol [Line: 15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L15)

	```solidity
	            (bool success, bytes memory result) = address(this).delegatecall(data[i]);
	```
	
	
## L-2: Unprotected initializer

Consider protecting the initializer functions with modifiers.

@> contracts/PanopticFactory.sol [Line: 134](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134)

	```solidity
	    function initialize(address _owner) public {
	```

@> contracts/SemiFungiblePositionManager.sol [Line: 350](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L350)

	```solidity
	    function initializeAMMPool(address token0, address token1, uint24 fee) external {
	```
	
	
## L-3: Large literal values multiples of 10000 can be replaced with scientific notation

Make use of the `e` notation, per example: `1e18`, instead of its full numeric value.


@> contracts/libraries/Constants.sol [Line: 9](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L9)

	```solidity
	    uint256 internal constant FP96 = 0x1000000000000000000000000;
	```

@> contracts/libraries/Math.sol [Line: 93](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L93)

	```solidity
	            if (x >= 0x100000000000000000000000000000000) {
	```

@> contracts/libraries/Math.sol [Line: 97](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L97)

	```solidity
	            if (x >= 0x10000000000000000) {
	```

@> contracts/libraries/Math.sol [Line: 101](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L101)

	```solidity
	            if (x >= 0x100000000) {
	```

@> contracts/libraries/Math.sol [Line: 135](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L135)

	```solidity
	                : 0x100000000000000000000000000000000;
	```


## L-4: Internal functions called only once can be in-lined

Instead of separating the logic into a separate function, consider in-lining the logic into the calling function. This can reduce the number of function calls and improve readability.

@> contracts/SemiFungiblePositionManager.sol [Line: 320](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L320)

	```solidity
	    function beginReentrancyLock(uint64 poolId) internal {
	```

@> contracts/SemiFungiblePositionManager.sol [Line: 330](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L330)

	```solidity
	    function endReentrancyLock(uint64 poolId) internal {
	```

@> contracts/SemiFungiblePositionManager.sol [Line: 756](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L756)

	```solidity
	    function swapInAMM(
	```

@> contracts/libraries/Math.sol [Line: 598](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L598)

	```solidity
	    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {
	```

@> contracts/libraries/PanopticMath.sol [Line: 419](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L419)

	```solidity
	    function convertCollateralData(
	```

@> contracts/libraries/PanopticMath.sol [Line: 574](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L574)

	```solidity
	    function getAmountsMoved(
	```