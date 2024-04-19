## L-1: Unsafe ERC20 Operations should not be used

ERC20 functions may not behave as expected. For example: return values are not always meaningful. It is recommended to use OpenZeppelin's SafeERC20 library.

- Found in contracts/CollateralTracker.sol [https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L333](contracts/CollateralTracker.sol#L333)

	```solidity
	        return ERC20Minimal.transfer(recipient, amount);
	```

- Found in contracts/CollateralTracker.sol [https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L352](contracts/CollateralTracker.sol#L352)

	```solidity
	        return ERC20Minimal.transferFrom(from, to, amount);
	```

- Found in contracts/libraries/InteractionHelper.sol [Line: 32](contracts/libraries/InteractionHelper.sol#L32)

	```solidity
	        IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
	```

- Found in contracts/libraries/InteractionHelper.sol [Line: 33](contracts/libraries/InteractionHelper.sol#L33)

	```solidity
	        IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
	```

- Found in contracts/libraries/InteractionHelper.sol [Line: 36](contracts/libraries/InteractionHelper.sol#L36)

	```solidity
	        IERC20Partial(token0).approve(address(ct0), type(uint256).max);
	```

- Found in contracts/libraries/InteractionHelper.sol [Line: 37](contracts/libraries/InteractionHelper.sol#L37)

	```solidity
	        IERC20Partial(token1).approve(address(ct1), type(uint256).max);
	```
