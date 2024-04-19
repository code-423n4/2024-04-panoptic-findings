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


## L-2: Solidity pragma should be specific, not wide

Consider using a specific version of Solidity in your contracts instead of a wide version. For example, instead of `pragma solidity ^0.8.0;`, use `pragma solidity 0.8.0;`

- Found in contracts/CollateralTracker.sol [Line: 2](contracts/CollateralTracker.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- Found in contracts/PanopticFactory.sol [Line: 2](contracts/PanopticFactory.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- Found in contracts/PanopticPool.sol [Line: 2](contracts/PanopticPool.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- Found in contracts/SemiFungiblePositionManager.sol [Line: 2](contracts/SemiFungiblePositionManager.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- Found in contracts/libraries/CallbackLib.sol [Line: 2](contracts/libraries/CallbackLib.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/libraries/Constants.sol [Line: 2](contracts/libraries/Constants.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/libraries/Errors.sol [Line: 2](contracts/libraries/Errors.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/libraries/FeesCalc.sol [Line: 2](contracts/libraries/FeesCalc.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/libraries/InteractionHelper.sol [Line: 2](contracts/libraries/InteractionHelper.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/libraries/Math.sol [Line: 2](contracts/libraries/Math.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/libraries/PanopticMath.sol [Line: 2](contracts/libraries/PanopticMath.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/libraries/SafeTransferLib.sol [Line: 2](contracts/libraries/SafeTransferLib.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/multicall/Multicall.sol [Line: 2](contracts/multicall/Multicall.sol#L2)

	```solidity
	pragma solidity ^0.8.18;
	```

- Found in contracts/tokens/ERC1155Minimal.sol [Line: 2](contracts/tokens/ERC1155Minimal.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 2](contracts/tokens/ERC20Minimal.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/tokens/interfaces/IDonorNFT.sol [Line: 2](contracts/tokens/interfaces/IDonorNFT.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in contracts/tokens/interfaces/IERC20Partial.sol [Line: 2](contracts/tokens/interfaces/IERC20Partial.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in lib/forge-std/src/StdMath.sol [Line: 2](lib/forge-std/src/StdMath.sol#L2)

	```solidity
	pragma solidity >=0.6.2 <0.9.0;
	```

- Found in lib/openzeppelin-contracts/contracts/utils/math/Math.sol [Line: 4](lib/openzeppelin-contracts/contracts/utils/math/Math.sol#L4)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolErrors.sol [Line: 2](lib/v3-core/contracts/interfaces/pool/IUniswapV3PoolErrors.sol#L2)

	```solidity
	pragma solidity >=0.5.0;
	```

- Found in lib/v3-core/contracts/libraries/BitMath.sol [Line: 2](lib/v3-core/contracts/libraries/BitMath.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in lib/v3-core/contracts/libraries/FullMath.sol [Line: 2](lib/v3-core/contracts/libraries/FullMath.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in lib/v3-core/contracts/libraries/SqrtPriceMath.sol [Line: 2](lib/v3-core/contracts/libraries/SqrtPriceMath.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in lib/v3-core/contracts/libraries/TickMath.sol [Line: 2](lib/v3-core/contracts/libraries/TickMath.sol#L2)

	```solidity
	pragma solidity ^0.8.0;
	```

- Found in lib/v3-core/contracts/libraries/UnsafeMath.sol [Line: 2](lib/v3-core/contracts/libraries/UnsafeMath.sol#L2)

	```solidity
	pragma solidity >=0.5.0;
	```

## L-3: Missing checks for `address(0)` when assigning values to address state variables

Check for `address(0)` when assigning values to address state variables.

- Found in contracts/CollateralTracker.sol [Line: 241](contracts/CollateralTracker.sol#L241)

	```solidity
	        s_underlyingToken = underlyingIsToken0 ? token0 : token1;
	```

- Found in contracts/CollateralTracker.sol [Line: 244](contracts/CollateralTracker.sol#L244)

	```solidity
	        s_panopticPool = panopticPool;
	```

- Found in contracts/CollateralTracker.sol [Line: 254](contracts/CollateralTracker.sol#L254)

	```solidity
	        s_univ3token0 = token0;
	```

- Found in contracts/CollateralTracker.sol [Line: 255](contracts/CollateralTracker.sol#L255)

	```solidity
	        s_univ3token1 = token1;
	```

- Found in contracts/CollateralTracker.sol [Line: 602](contracts/CollateralTracker.sol#L602)

	```solidity
	            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
	```

- Found in contracts/CollateralTracker.sol [Line: 895](contracts/CollateralTracker.sol#L895)

	```solidity
	        balanceOf[delegatee] += convertToShares(assets);
	```

- Found in contracts/CollateralTracker.sol [Line: 904](contracts/CollateralTracker.sol#L904)

	```solidity
	        balanceOf[delegatee] -= convertToShares(assets);
	```

- Found in contracts/PanopticFactory.sol [Line: 136](contracts/PanopticFactory.sol#L136)

	```solidity
	            s_owner = _owner;
	```

- Found in contracts/PanopticFactory.sol [Line: 152](contracts/PanopticFactory.sol#L152)

	```solidity
	        s_owner = newOwner;
	```

- Found in contracts/PanopticPool.sol [Line: 302](contracts/PanopticPool.sol#L302)

	```solidity
	        s_univ3pool = IUniswapV3Pool(_univ3pool);
	```

- Found in contracts/PanopticPool.sol [Line: 318](contracts/PanopticPool.sol#L318)

	```solidity
	        s_collateralToken0 = collateralTracker0;
	```

- Found in contracts/PanopticPool.sol [Line: 319](contracts/PanopticPool.sol#L319)

	```solidity
	        s_collateralToken1 = collateralTracker1;
	```

- Found in contracts/PanopticPool.sol [Line: 654](contracts/PanopticPool.sol#L654)

	```solidity
	        s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
	```

- Found in contracts/tokens/ERC1155Minimal.sol [Line: 82](contracts/tokens/ERC1155Minimal.sol#L82)

	```solidity
	        isApprovedForAll[msg.sender][operator] = approved;
	```

- Found in contracts/tokens/ERC1155Minimal.sol [Line: 237](contracts/tokens/ERC1155Minimal.sol#L237)

	```solidity
	        balanceOf[from][id] -= amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 50](contracts/tokens/ERC20Minimal.sol#L50)

	```solidity
	        allowance[msg.sender][spender] = amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 62](contracts/tokens/ERC20Minimal.sol#L62)

	```solidity
	        balanceOf[msg.sender] -= amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 67](contracts/tokens/ERC20Minimal.sol#L67)

	```solidity
	            balanceOf[to] += amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 84](contracts/tokens/ERC20Minimal.sol#L84)

	```solidity
	        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 86](contracts/tokens/ERC20Minimal.sol#L86)

	```solidity
	        balanceOf[from] -= amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 91](contracts/tokens/ERC20Minimal.sol#L91)

	```solidity
	            balanceOf[to] += amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 104](contracts/tokens/ERC20Minimal.sol#L104)

	```solidity
	        balanceOf[from] -= amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 109](contracts/tokens/ERC20Minimal.sol#L109)

	```solidity
	            balanceOf[to] += amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 126](contracts/tokens/ERC20Minimal.sol#L126)

	```solidity
	            balanceOf[to] += amount;
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 137](contracts/tokens/ERC20Minimal.sol#L137)

	```solidity
	        balanceOf[from] -= amount;
	```