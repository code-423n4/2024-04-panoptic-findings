
### These issues are not listed in the automated findings report.

# 1. No validation check for `univ3pool` on SemiFungiblePositionManager#`registerTokenTransfer()`

### Description

On SemiFungiblePositionManager#`registerTokenTransfer()`, no validation check for `univ3pool`.

### Impact

It might happens protocol violation for registering `token transfer`.

### Links to affected code
 
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593-L653
### Recommended Mitigation Steps

```diff
	function registerTokenTransfer(
		address from, 
		address to, 
		TokenId id, 
		uint256 amount
	) internal {
		
		// Validate tokenId
		id.validate();
		
		// Extract univ3pool from the poolId map to Uniswap Pool
		IUniswapV3Pool univ3pool = s_poolContext[id.poolId()].pool;
		
++		if (univ3pool == IUniswapV3Pool(address(0))) 
++			revert Errors.UniswapPoolNotInitialized();
		
		uint256 numLegs = id.countLegs();   ...
	}
```


# 2. No equal check for `ids` and `amounts` array's length on `safeBatchTransferFrom()`

### Description

On `safeBatchTransferFrom()`, no equal check for `ids` and `amounts` array's length.

### Impact

It might happens protocol violation for batch transferring.

### Links to affected code
 
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566-L585
https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L130-L171
### Recommended Mitigation Steps

- On SemiFungiblePositionManager.sol,

```diff
	function safeBatchTransferFrom(
		address from,
		address to,	
		uint256[] calldata ids,
		uint256[] calldata amounts,
		bytes calldata data
	) public override {	
		
++		require(ids.length = amounts.length, "ids and amounts is not matched.");
		for (uint256 i = 0; i < ids.length; ) {
			...
		}
		
		super.safeBatchTransferFrom(from, to, ids, amounts, data);	
	}
```

- On ERC1155Minimal.sol,

```diff
	function safeBatchTransferFrom(
		address from,
		address to,	
		uint256[] calldata ids,
		uint256[] calldata amounts,
		bytes calldata data
	) public override {	
		
		if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) 
			revert NotAuthorized();
			
		uint256 id;	
		uint256 amount;
			
++		require(ids.length = amounts.length, "ids and amounts is not matched.");
		
		for (uint256 i = 0; i < ids.length; ) {
			...
		}
		...
	}
```



