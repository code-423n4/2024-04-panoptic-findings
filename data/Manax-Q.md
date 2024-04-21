## L-1: Missing checks for `address(0)` when assigning values to address state variables

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


## L-2: `public` functions not used internally could be marked `external`

Instead of marking a function as `public`, consider marking it as `external` if it is not used internally.

- Found in contracts/CollateralTracker.sol [Line: 323](contracts/CollateralTracker.sol#L323)

	```solidity
	    function transfer(
	```

- Found in contracts/CollateralTracker.sol [Line: 341](contracts/CollateralTracker.sol#L341)

	```solidity
	    function transferFrom(
	```

- Found in contracts/CollateralTracker.sol [Line: 1141](contracts/CollateralTracker.sol#L1141)

	```solidity
	    function getAccountMarginDetails(
	```

- Found in contracts/PanopticFactory.sol [Line: 134](contracts/PanopticFactory.sol#L134)

	```solidity
	    function initialize(address _owner) public {
	```

- Found in contracts/PanopticPool.sol [Line: 1444](contracts/PanopticPool.sol#L1444)

	```solidity
	    function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {
	```

- Found in contracts/SemiFungiblePositionManager.sol [Line: 540](contracts/SemiFungiblePositionManager.sol#L540)

	```solidity
	    function safeTransferFrom(
	```

- Found in contracts/SemiFungiblePositionManager.sol [Line: 566](contracts/SemiFungiblePositionManager.sol#L566)

	```solidity
	    function safeBatchTransferFrom(
	```

- Found in contracts/libraries/FeesCalc.sol [Line: 97](contracts/libraries/FeesCalc.sol#L97)

	```solidity
	    function calculateAMMSwapFees(
	```

- Found in contracts/multicall/Multicall.sol [Line: 12](contracts/multicall/Multicall.sol#L12)

	```solidity
	    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
	```

- Found in contracts/tokens/ERC1155Minimal.sol [Line: 81](contracts/tokens/ERC1155Minimal.sol#L81)

	```solidity
	    function setApprovalForAll(address operator, bool approved) public {
	```

- Found in contracts/tokens/ERC1155Minimal.sol [Line: 94](contracts/tokens/ERC1155Minimal.sol#L94)

	```solidity
	    function safeTransferFrom(
	```

- Found in contracts/tokens/ERC1155Minimal.sol [Line: 130](contracts/tokens/ERC1155Minimal.sol#L130)

	```solidity
	    function safeBatchTransferFrom(
	```

- Found in contracts/tokens/ERC1155Minimal.sol [Line: 178](contracts/tokens/ERC1155Minimal.sol#L178)

	```solidity
	    function balanceOfBatch(
	```

- Found in contracts/tokens/ERC1155Minimal.sol [Line: 200](contracts/tokens/ERC1155Minimal.sol#L200)

	```solidity
	    function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 49](contracts/tokens/ERC20Minimal.sol#L49)

	```solidity
	    function approve(address spender, uint256 amount) public returns (bool) {
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 61](contracts/tokens/ERC20Minimal.sol#L61)

	```solidity
	    function transfer(address to, uint256 amount) public virtual returns (bool) {
	```

- Found in contracts/tokens/ERC20Minimal.sol [Line: 81](contracts/tokens/ERC20Minimal.sol#L81)

	```solidity
	    function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
	```



# L-3: Unsafe ERC20 Operations should not be used

ERC20 functions may not behave as expected. For example: return values are not always meaningful. It is recommended to use OpenZeppelin's SafeERC20 library.

- Found in contracts/CollateralTracker.sol [Line: 333](contracts/CollateralTracker.sol#L333)

	```solidity
	        return ERC20Minimal.transfer(recipient, amount);
	```

- Found in contracts/CollateralTracker.sol [Line: 352](contracts/CollateralTracker.sol#L352)

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

## L-4: Empty `require()` / `revert()` statements

Use descriptive reason strings or custom errors for revert paths, to be more informative what type of error happen during a revert. And It would also be way more cool if you used custome errors instead of strings because there gas efficient and putting the name of the contract it emerged from and double underscore will make debugging amazing

- Found in contracts/libraries/Math.sol [Line: 361](contracts/libraries/Math.sol#L361)

	```solidity
	                require(denominator > 0);
	```

- Found in contracts/libraries/Math.sol [Line: 370](contracts/libraries/Math.sol#L370)

	```solidity
	            require(denominator > prod1);
	```

- Found in contracts/libraries/Math.sol [Line: 448](contracts/libraries/Math.sol#L448)

	```solidity
	                require(result < type(uint256).max);
	```

- Found in contracts/libraries/Math.sol [Line: 484](contracts/libraries/Math.sol#L484)

	```solidity
	            require(2 ** 64 > prod1);
	```

- Found in contracts/libraries/Math.sol [Line: 547](contracts/libraries/Math.sol#L547)

	```solidity
	            require(2 ** 96 > prod1);
	```

- Found in contracts/libraries/Math.sol [Line: 588](contracts/libraries/Math.sol#L588)

	```solidity
	                require(result < type(uint256).max);
	```

- Found in contracts/libraries/Math.sol [Line: 624](contracts/libraries/Math.sol#L624)

	```solidity
	            require(2 ** 128 > prod1);
	```

- Found in contracts/libraries/Math.sol [Line: 665](contracts/libraries/Math.sol#L665)

	```solidity
	                require(result < type(uint256).max);
	```

- Found in contracts/libraries/Math.sol [Line: 701](contracts/libraries/Math.sol#L701)

	```solidity
	            require(2 ** 192 > prod1);
	```

- Found in lib/openzeppelin-contracts/contracts/utils/math/Math.sol [Line: 78](lib/openzeppelin-contracts/contracts/utils/math/Math.sol#L78)

	```solidity
	            require(denominator > prod1);
	```

- Found in lib/v3-core/contracts/libraries/BitMath.sol [Line: 14](lib/v3-core/contracts/libraries/BitMath.sol#L14)

	```solidity
	        require(x > 0);
	```

- Found in lib/v3-core/contracts/libraries/BitMath.sol [Line: 56](lib/v3-core/contracts/libraries/BitMath.sol#L56)

	```solidity
	        require(x > 0);
	```

- Found in lib/v3-core/contracts/libraries/FullMath.sol [Line: 35](lib/v3-core/contracts/libraries/FullMath.sol#L35)

	```solidity
	                require(denominator > 0);
	```

- Found in lib/v3-core/contracts/libraries/FullMath.sol [Line: 44](lib/v3-core/contracts/libraries/FullMath.sol#L44)

	```solidity
	            require(denominator > prod1);
	```

- Found in lib/v3-core/contracts/libraries/FullMath.sol [Line: 123](lib/v3-core/contracts/libraries/FullMath.sol#L123)

	```solidity
	                require(result < type(uint256).max);
	```

- Found in lib/v3-core/contracts/libraries/SqrtPriceMath.sol [Line: 53](lib/v3-core/contracts/libraries/SqrtPriceMath.sol#L53)

	```solidity
	                require((product = amount * sqrtPX96) / amount == sqrtPX96 && numerator1 > product);
	```

- Found in lib/v3-core/contracts/libraries/SqrtPriceMath.sol [Line: 93](lib/v3-core/contracts/libraries/SqrtPriceMath.sol#L93)

	```solidity
	            require(sqrtPX96 > quotient);
	```

- Found in lib/v3-core/contracts/libraries/SqrtPriceMath.sol [Line: 114](lib/v3-core/contracts/libraries/SqrtPriceMath.sol#L114)

	```solidity
	        require(sqrtPX96 > 0);
	```

- Found in lib/v3-core/contracts/libraries/SqrtPriceMath.sol [Line: 115](lib/v3-core/contracts/libraries/SqrtPriceMath.sol#L115)

	```solidity
	        require(liquidity > 0);
	```

- Found in lib/v3-core/contracts/libraries/SqrtPriceMath.sol [Line: 137](lib/v3-core/contracts/libraries/SqrtPriceMath.sol#L137)

	```solidity
	        require(sqrtPX96 > 0);
	```

- Found in lib/v3-core/contracts/libraries/SqrtPriceMath.sol [Line: 138](lib/v3-core/contracts/libraries/SqrtPriceMath.sol#L138)

	```solidity
	        require(liquidity > 0);
	```

- Found in lib/v3-core/contracts/libraries/SqrtPriceMath.sol [Line: 167](lib/v3-core/contracts/libraries/SqrtPriceMath.sol#L167)

	```solidity
	            require(sqrtRatioAX96 > 0);
	```


## L-5: Solidity pragma should be specific, not wide

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

## L-6: PUSH0 is not supported by all chains

Solc compiler version 0.8.20 switches the default target EVM version to Shanghai, which means that the generated bytecode will include PUSH0 opcodes. Be sure to select the appropriate EVM version in case you intend to deploy on a chain other than mainnet like L2 chains that may not support PUSH0, otherwise deployment of your contracts will fail.

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


## L-7: Define and use `constant` variables instead of using `MAGIC` Numbers

If the same constant literal value is used multiple times, create a constant state variable and reference it throughout the contract.This makes the contract much easier to understantd

- Found in contracts/CollateralTracker.sol [Line: 204](contracts/CollateralTracker.sol#L204)

	```solidity
	                    10_000 +
	```

- Found in contracts/CollateralTracker.sol [Line: 206](contracts/CollateralTracker.sol#L206)

	```solidity
	                    10_000 ** 2 +
	```

- Found in contracts/CollateralTracker.sol [Line: 207](contracts/CollateralTracker.sol#L207)

	```solidity
	                    (6510 * ratioTick ** 3) /
	```

- Found in contracts/CollateralTracker.sol [Line: 208](contracts/CollateralTracker.sol#L208)

	```solidity
	                    10_000 ** 3
	```

- Found in contracts/CollateralTracker.sol [Line: 1330](contracts/CollateralTracker.sol#L1330)

	```solidity
	            : int64(uint64(poolUtilization >> 64));
	```

- Found in contracts/CollateralTracker.sol [Line: 1586](contracts/CollateralTracker.sol#L1586)

	```solidity
	                    : int64(uint64(poolUtilization >> 64))
	```

- Found in contracts/CollateralTracker.sol [Line: 1632](contracts/CollateralTracker.sol#L1632)

	```solidity
	            uint64 poolUtilization1 = uint64(poolUtilization >> 64);
	```

- Found in contracts/CollateralTracker.sol [Line: 1638](contracts/CollateralTracker.sol#L1638)

	```solidity
	                (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);
	```

- Found in contracts/PanopticPool.sol [Line: 370](contracts/PanopticPool.sol#L370)

	```solidity
	        poolUtilization1 = uint64(balanceData.leftSlot() >> 64);
	```

- Found in contracts/PanopticPool.sol [Line: 730](contracts/PanopticPool.sol#L730)

	```solidity
	            return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));
	```


- Found in contracts/PanopticPool.sol [Line: 1348](contracts/PanopticPool.sol#L1348)

	```solidity
	                Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +
	```

- Found in contracts/PanopticPool.sol [Line: 1353](contracts/PanopticPool.sol#L1353)

	```solidity
	                Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +
	```

- Found in contracts/PanopticPool.sol [Line: 1415](contracts/PanopticPool.sol#L1415)

	```solidity
	        if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();
	```

- Found in contracts/PanopticPool.sol [Line: 1445](contracts/PanopticPool.sol#L1445)

	```solidity
	        _numberOfPositions = (s_positionsHash[user] >> 248);
	```

- Found in contracts/PanopticPool.sol [Line: 1552](contracts/PanopticPool.sol#L1552)

	```solidity
	                                        (liquidityChunk.liquidity())) / 2 ** 64
	```

- Found in contracts/PanopticPool.sol [Line: 1561](contracts/PanopticPool.sol#L1561)

	```solidity
	                                        (liquidityChunk.liquidity())) / 2 ** 64
	```

- Found in contracts/PanopticPool.sol [Line: 1635](contracts/PanopticPool.sol#L1635)

	```solidity
	                .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))
	```

- Found in contracts/PanopticPool.sol [Line: 1636](contracts/PanopticPool.sol#L1636)

	```solidity
	                .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));
	```

- Found in contracts/PanopticPool.sol [Line: 1769](contracts/PanopticPool.sol#L1769)

	```solidity
	                totalLiquidity) / 2 ** 64;
	```

- Found in contracts/PanopticPool.sol [Line: 1771](contracts/PanopticPool.sol#L1771)

	```solidity
	                totalLiquidity) / 2 ** 64;
	```

- Found in contracts/PanopticPool.sol [Line: 1942](contracts/PanopticPool.sol#L1942)

	```solidity
	                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
	```

- Found in contracts/PanopticPool.sol [Line: 1959](contracts/PanopticPool.sol#L1959)

	```solidity
	                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
	```

- Found in contracts/SemiFungiblePositionManager.sol [Line: 1352](contracts/SemiFungiblePositionManager.sol#L1352)

	```solidity
	                    totalLiquidity * 2 ** 64,
	```

- Found in contracts/SemiFungiblePositionManager.sol [Line: 1357](contracts/SemiFungiblePositionManager.sol#L1357)

	```solidity
	                    totalLiquidity * 2 ** 64,
	```

## L-8: Internal functions called only once can be inlined

Instead of separating the logic into a separate function, consider inlining the logic into the calling function. This can reduce the number of function calls and improve readability.

- Found in contracts/SemiFungiblePositionManager.sol [Line: 320](contracts/SemiFungiblePositionManager.sol#L320)

	```solidity
	    function beginReentrancyLock(uint64 poolId) internal {
	```

- Found in contracts/SemiFungiblePositionManager.sol [Line: 330](contracts/SemiFungiblePositionManager.sol#L330)

	```solidity
	    function endReentrancyLock(uint64 poolId) internal {
	```

- Found in contracts/SemiFungiblePositionManager.sol [Line: 756](contracts/SemiFungiblePositionManager.sol#L756)

	```solidity
	    function swapInAMM(
	```

- Found in contracts/libraries/Math.sol [Line: 598](contracts/libraries/Math.sol#L598)

	```solidity
	    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {
	```

- Found in contracts/libraries/PanopticMath.sol [Line: 419](contracts/libraries/PanopticMath.sol#L419)

	```solidity
	    function convertCollateralData(
	```

- Found in contracts/libraries/PanopticMath.sol [Line: 574](contracts/libraries/PanopticMath.sol#L574)

	```solidity
	    function getAmountsMoved(
	```

- Found in lib/forge-std/src/StdMath.sol [Line: 20](lib/forge-std/src/StdMath.sol#L20)

	```solidity
	    function delta(int256 a, int256 b) internal pure returns (uint256) {
	```

- Found in lib/openzeppelin-contracts/contracts/utils/math/Math.sol [Line: 26](lib/openzeppelin-contracts/contracts/utils/math/Math.sol#L26)

	```solidity
	    function min(uint256 a, uint256 b) internal pure returns (uint256) {
	```

- Found in lib/openzeppelin-contracts/contracts/utils/math/Math.sol [Line: 55](lib/openzeppelin-contracts/contracts/utils/math/Math.sol#L55)

	```solidity
	    function mulDiv(
	```

- Found in lib/openzeppelin-contracts/contracts/utils/math/Math.sol [Line: 158](lib/openzeppelin-contracts/contracts/utils/math/Math.sol#L158)

	```solidity
	    function sqrt(uint256 a) internal pure returns (uint256) {
	```

- Found in lib/openzeppelin-contracts/contracts/utils/math/Math.sol [Line: 258](lib/openzeppelin-contracts/contracts/utils/math/Math.sol#L258)

	```solidity
	    function log10(uint256 value) internal pure returns (uint256) {
	```

- Found in lib/openzeppelin-contracts/contracts/utils/math/Math.sol [Line: 309](lib/openzeppelin-contracts/contracts/utils/math/Math.sol#L309)

	```solidity
	    function log256(uint256 value) internal pure returns (uint256) {
	```

- Found in lib/v3-core/contracts/libraries/FullMath.sol [Line: 14](lib/v3-core/contracts/libraries/FullMath.sol#L14)

	```solidity
	    function mulDiv(
	```

- Found in lib/v3-core/contracts/libraries/TickMath.sol [Line: 26](lib/v3-core/contracts/libraries/TickMath.sol#L26)

	```solidity
	    function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160 sqrtPriceX96) {
	```
