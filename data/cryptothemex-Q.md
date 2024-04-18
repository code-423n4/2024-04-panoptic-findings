CryptoThemeX-CTX

## Summary

| |Issue|Instances| Gas Savings
|-|:-|:-:|:-:|
| [[L-01](#l-01)] | Array lengths may differ | 1| 0|
| [[L-02](#l-02)] | int/uint passed to abi.encodePacked without casting to string | 12| 0|
| [[L-03](#l-03)] | `decimals()` is not part of the ERC20 standard | 1| 0|
| [[L-04](#l-04)] | Function calls within loops | 6| 0|
| [[L-05](#l-05)] | Library with public/external functions | 13| 0|
| [[L-06](#l-06)] | Loops in external functions should be avoided due to high gas costs and possible DOS | 7| 0|
| [[L-07](#l-07)] | Possible length difference of two array parameters | 7| 0|
| [[L-08](#l-08)] | Missing zero address check in initializer | 2| 0|
| [[L-09](#l-09)] | Use of Nested Loop | 2| 0|
| [[L-10](#l-10)] | Upgradable contracts not taken into account when making wrapped calls | 8| 0|
| [[L-11](#l-11)] | Unsafe `uint` to `int` conversion | 55| 0|
| [[L-12](#l-12)] | Complex Computation - Multiplication on result of a Division | 31| 0|
| [[L-13](#l-13)] | Dangerous strict equalities | 1| 0|
| [[L-14](#l-14)] | Missing events arithmetic | 2| 0|
| [[L-15](#l-15)] | Missing zero address validation | 7| 0|
| [[L-16](#l-16)] | Contract's Name reused | 1| 0|
| [[L-17](#l-17)] | Benign reentrancy vulnerabilities | 6| 0|
| [[L-18](#l-18)] | Reentrancy vulnerabilities (events) | 9| 0|
| [[L-19](#l-19)] | Reentrancy vulnerabilities (loss of non-ether assets) | 6| 0|
| [[L-20](#l-20)] | Block timestamp | 2| 0|
| [[L-21](#l-21)] | Uninitialized local variables | 4| 0|
| [[L-22](#l-22)] | Unused return | 25| 0|
| [[N-01](#n-01)] | Consider emitting an event at the end of the constructor | 4| 0|
| [[N-02](#n-02)] | Similar Constants decalred in Multiple Contracts  | 1| 0|
| [[N-03](#n-03)] | Events are missing sender information | 9| 0|
| [[N-04](#n-04)] | Validate user inputs | 95| 0|
| [[N-05](#n-05)] | Assembly usage | 9| 0|
| [[N-06](#n-06)] | Cyclomatic complexity | 2| 0|
| [[N-07](#n-07)] | Dead-code | 18| 0|
| [[N-08](#n-08)] | Low-level calls | 1| 0|
| [[N-09](#n-09)] | Conformance to Solidity naming conventions | 43| 0|
| [[N-10](#n-10)] | Redundant Statements | 1| 0|
| [[N-11](#n-11)] | Variable names too similar | 47| 0|
| [[N-12](#n-12)] | Too many digits | 24| 0|
| [[N-13](#n-13)] | Unused state variable | 2| 0|
| [[N-14](#n-14)] | Consider splitting complex checks into multiple steps | 6| 0|
| [[N-15](#n-15)] | Constant decimal values | 12| 0|
| [[N-16](#n-16)] | Constants in comparisons should appear on the left side | 212| 0|
| [[N-17](#n-17)] | Consider adding emergency-stop functionality | 3| 0|
| [[N-18](#n-18)] | Consider making contracts `Upgradeable` | 3| 0|
| [[N-19](#n-19)] | Consider using descriptive `constant`s when passing zero as a function argument | 94| 0|
| [[N-20](#n-20)] | Using abi.encodePacked can in hash function | 9| 0|
| [[N-21](#n-21)] | Use of `override` is unnecessary | 4| 0|
| [[N-22](#n-22)] | Consider using a `struct` rather than having many function input parameters | 109| 0|
| [[N-23](#n-23)] | Consider using named function arguments | 97| 0|
| [[N-24](#n-24)] | Consider using named returns | 98| 0|
| [[N-25](#n-25)] | Returning a struct instead of returning many variables is better | 32| 0|
| [[N-26](#n-26)] | Use scratch space when building emitted events with two data arguments | 4| 60|
| [[N-27](#n-27)] | Use `do`-`while` loop | 16| 0|
| [[N-28](#n-28)] | Accessing Multi-Dimensional Array | 52| 0|


### Low Risk Issues

### [L-01]<a name="l-01"></a> Array lengths may differ

If values of one array are assigned to another array and lengths of both array mismatch, an operation believed to have been completed may not in fact have been completed (e.g. if the array being iterated over is shorter than the one being indexed into, larger array will not be completely iterated/ assigned.). **Recom:** Check lengths of both arrays before loop iterations.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
index may differ in array/ mapping assignment
	- _settledTokens = settledTokens (contracts/libraries/PanopticMath.sol#865-866)

/// @audit ****************** Affected Code *******************
 865:                         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
 866:                             storage _settledTokens = settledTokens;

```

*GitHub* : [865-866](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L865-L866)

### [L-02]<a name="l-02"></a> int/uint passed to abi.encodePacked without casting to string

Not casting an integer as a string before passing it into abi.encode can result in unintended behaviour. lets say '1' being encoded as '1' it will be encoded as char(1) which is the 'start of heading' control character or id of 60 would be encoded as '<'. This is may not be intended. To rectify this, simply cast the Id as a string with string(id) or ideally use solmate's libString library (toString)

*There are 12 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128) (contracts/PanopticPool.sol#1666-1746) calls abi.encodePacked():-
	- chunkKey = keccak256(bytes)(abi.encodePacked(tokenId.strike(leg),tokenId.width(leg),tokenId.tokenType(leg))) (contracts/PanopticPool.sol#1673-1675)

/// @audit ************** Possible Issue Line(s) **************
	L#1673-1675,  

/// @audit ****************** Affected Code *******************
1673:             bytes32 chunkKey = keccak256(
1674:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1675:             );

```

*GitHub* : [1666-1746](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1666-L1746)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._calculateAccumulatedPremia(address,TokenId[],bool,bool,int24) (contracts/PanopticPool.sol#429-492) calls abi.encodePacked():-
	- chunkKey = keccak256(bytes)(abi.encodePacked(tokenId.strike(leg),tokenId.width(leg),tokenId.tokenType(leg))) (contracts/PanopticPool.sol#461-467)

/// @audit ************** Possible Issue Line(s) **************
	L#461-467,  

/// @audit ****************** Affected Code *******************
 461:                     bytes32 chunkKey = keccak256(
 462:                         abi.encodePacked(
 463:                             tokenId.strike(leg),
 464:                             tokenId.width(leg),
 465:                             tokenId.tokenType(leg)
 466:                         )
 467:                     );

```

*GitHub* : [429-492](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L429-L492)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) calls abi.encodePacked():-
	- chunkKey = keccak256(bytes)(abi.encodePacked(tokenId_scope_1.strike(0),tokenId_scope_1.width(0),tokenId_scope_1.tokenType(0))) (contracts/libraries/PanopticMath.sol#878-884)

/// @audit ************** Possible Issue Line(s) **************
	L#878-884,  

/// @audit ****************** Affected Code *******************
 878:                         bytes32 chunkKey = keccak256(
 879:                             abi.encodePacked(
 880:                                 tokenId.strike(0),
 881:                                 tokenId.width(0),
 882:                                 tokenId.tokenType(0)
 883:                             )
 884:                         );

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) calls abi.encodePacked():-
	- chunkKey = keccak256(bytes)(abi.encodePacked(tokenId.strike(legIndex),tokenId.width(legIndex),tokenId.tokenType(legIndex))) (contracts/PanopticPool.sol#1642-1648)

/// @audit ************** Possible Issue Line(s) **************
	L#1642-1648,  

/// @audit ****************** Affected Code *******************
1642:             bytes32 chunkKey = keccak256(
1643:                 abi.encodePacked(
1644:                     tokenId.strike(legIndex),
1645:                     tokenId.width(legIndex),
1646:                     tokenId.tokenType(legIndex)
1647:                 )
1648:             );

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#1138-1178) calls abi.encodePacked():-
	- (feeGrowthInside0LastX128,feeGrowthInside1LastX128) = univ3pool.positions(keccak256(bytes)(abi.encodePacked(address(this),liquidityChunk.tickLower(),liquidityChunk.tickUpper()))) (contracts/SemiFungiblePositionManager.sol#1148-1157)

/// @audit ************** Possible Issue Line(s) **************
	L#1148-1157,  

/// @audit ****************** Affected Code *******************
1148:         (, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, , ) = univ3pool
1149:             .positions(
1150:                 keccak256(
1151:                     abi.encodePacked(
1152:                         address(this),
1153:                         liquidityChunk.tickLower(),
1154:                         liquidityChunk.tickUpper()
1155:                     )
1156:                 )
1157:             );

```

*GitHub* : [1138-1178](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1138-L1178)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) calls abi.encodePacked():-
	- chunkKey = keccak256(bytes)(abi.encodePacked(tokenId.strike(leg),tokenId.width(leg),tokenId.tokenType(leg))) (contracts/PanopticPool.sol#1855-1857)

/// @audit ************** Possible Issue Line(s) **************
	L#1855-1857,  

/// @audit ****************** Affected Code *******************
1855:             bytes32 chunkKey = keccak256(
1856:                 abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1857:             );

```

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256) (contracts/SemiFungiblePositionManager.sol#593-653) calls abi.encodePacked():-
	- positionKey_from = keccak256(bytes)(abi.encodePacked(address(univ3pool),from,id.tokenType(leg),liquidityChunk.tickLower(),liquidityChunk.tickUpper())) (contracts/SemiFungiblePositionManager.sol#611-619)
	- positionKey_to = keccak256(bytes)(abi.encodePacked(address(univ3pool),to,id.tokenType(leg),liquidityChunk.tickLower(),liquidityChunk.tickUpper())) (contracts/SemiFungiblePositionManager.sol#620-628)

/// @audit ************** Possible Issue Line(s) **************
	L#611-619,  L#620-628,  

/// @audit ****************** Affected Code *******************
 611:             bytes32 positionKey_from = keccak256(
 612:                 abi.encodePacked(
 613:                     address(univ3pool),
 614:                     from,
 615:                     id.tokenType(leg),
 616:                     liquidityChunk.tickLower(),
 617:                     liquidityChunk.tickUpper()
 618:                 )
 619:             );
 620:             bytes32 positionKey_to = keccak256(
 621:                 abi.encodePacked(
 622:                     address(univ3pool),
 623:                     to,
 624:                     id.tokenType(leg),
 625:                     liquidityChunk.tickLower(),
 626:                     liquidityChunk.tickUpper()
 627:                 )
 628:             );

```

*GitHub* : [593-653](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L593-L653)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256) (contracts/SemiFungiblePositionManager.sol#1449-1523) calls abi.encodePacked():-
	- positionKey = keccak256(bytes)(abi.encodePacked(univ3pool,owner,tokenType,tickLower,tickUpper)) (contracts/SemiFungiblePositionManager.sol#1458-1460)

/// @audit ************** Possible Issue Line(s) **************
	L#1458-1460,  

/// @audit ****************** Affected Code *******************
1458:         bytes32 positionKey = keccak256(
1459:             abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)
1460:         );

```

*GitHub* : [1449-1523](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1449-L1523)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#958-1104) calls abi.encodePacked():-
	- positionKey = keccak256(bytes)(abi.encodePacked(address(univ3pool),msg.sender,tokenType,liquidityChunk.tickLower(),liquidityChunk.tickUpper())) (contracts/SemiFungiblePositionManager.sol#974-982)

/// @audit ************** Possible Issue Line(s) **************
	L#974-982,  

/// @audit ****************** Affected Code *******************
 974:         bytes32 positionKey = keccak256(
 975:             abi.encodePacked(
 976:                 address(univ3pool),
 977:                 msg.sender,
 978:                 tokenType,
 979:                 liquidityChunk.tickLower(),
 980:                 liquidityChunk.tickUpper()
 981:             )
 982:         );

```

*GitHub* : [958-1104](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L958-L1104)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.registerTokenTransfer(address,address,TokenId,uint256) (contracts/SemiFungiblePositionManager.sol#593-653) calls abi.encodePacked():-
	- positionKey_from = keccak256(bytes)(abi.encodePacked(address(univ3pool),from,id.tokenType(leg),liquidityChunk.tickLower(),liquidityChunk.tickUpper())) (contracts/SemiFungiblePositionManager.sol#611-619)

/// @audit ************** Possible Issue Line(s) **************
	L#611-619,  

/// @audit ****************** Affected Code *******************
 611:             bytes32 positionKey_from = keccak256(
 612:                 abi.encodePacked(
 613:                     address(univ3pool),
 614:                     from,
 615:                     id.tokenType(leg),
 616:                     liquidityChunk.tickLower(),
 617:                     liquidityChunk.tickUpper()
 618:                 )
 619:             );

```

*GitHub* : [593-653](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L593-L653)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.getAccountFeesBase(address,address,uint256,int24,int24) (contracts/SemiFungiblePositionManager.sol#1535-1548) calls abi.encodePacked():-
	- feesBase = s_accountFeesBase[keccak256(bytes)(abi.encodePacked(univ3pool,owner,tokenType,tickLower,tickUpper))] (contracts/SemiFungiblePositionManager.sol#1543-1545)

/// @audit ************** Possible Issue Line(s) **************
	L#1543-1545,  

/// @audit ****************** Affected Code *******************
1535:     function getAccountFeesBase(
1536:         address univ3pool,
1537:         address owner,
1538:         uint256 tokenType,
1539:         int24 tickLower,
1540:         int24 tickUpper
1541:     ) external view returns (int128 feesBase0, int128 feesBase1) {
1542:         // Get accumulated fees for token0 (rightSlot) and token1 (leftSlot)
1543:         LeftRightSigned feesBase = s_accountFeesBase[
1544:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))
1545:         ];
1546:         feesBase0 = feesBase.rightSlot();
1547:         feesBase1 = feesBase.leftSlot();
1548:     }

```

*GitHub* : [1535-1548](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1535-L1548)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.getAccountLiquidity(address,address,uint256,int24,int24) (contracts/SemiFungiblePositionManager.sol#1421-1433) calls abi.encodePacked():-
	- accountLiquidities = s_accountLiquidity[keccak256(bytes)(abi.encodePacked(univ3pool,owner,tokenType,tickLower,tickUpper))] (contracts/SemiFungiblePositionManager.sol#1430-1432)

/// @audit ************** Possible Issue Line(s) **************
	L#1430-1432,  

/// @audit ****************** Affected Code *******************
1421:     function getAccountLiquidity(
1422:         address univ3pool,
1423:         address owner,
1424:         uint256 tokenType,
1425:         int24 tickLower,
1426:         int24 tickUpper
1427:     ) external view returns (LeftRightUnsigned accountLiquidities) {
1428:         /// Extract the account liquidity for a given uniswap pool, owner, token type, and ticks
1429:         /// @dev tokenType input here is the asset of the positions minted, this avoids put liquidity to be used for call, and vice-versa
1430:         accountLiquidities = s_accountLiquidity[
1431:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))
1432:         ];
1433:     }

```

*GitHub* : [1421-1433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1421-L1433)

### [L-03]<a name="l-03"></a> `decimals()` is not part of the ERC20 standard

The `decimals()` function in an ERC20 token contract is used to specify how many decimal places the token can be divided into. However, it should be used with caution because not all ERC20 token contracts implement `decimals()`, and the function isn't required by the ERC20 standard. Calling `decimals()` on a contract that doesn't implement it will result in a runtime error. Moreover, even when implemented, the returned value can be manipulated or artificially set, which may cause unexpected behavior. Therefore, always verify the decimal count independently if precision is crucial for your contract logic. When interacting with other ERC20 tokens, consider implementing safeguards or checks to handle potential errors from calling `decimals()`.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeDecimals(address) (contracts/libraries/InteractionHelper.sol#107-115)
calls decimals(), which is not part of ERC20 standard.
	- _decimals = IERC20Metadata(token).decimals() (contracts/libraries/InteractionHelper.sol#110-114)

/// @audit ************** Possible Issue Line(s) **************
	L#110-114,  

/// @audit ****************** Affected Code *******************
 107:     function computeDecimals(address token) external view returns (uint8) {
 108:         // not guaranteed that token supports metadada extension
 109:         // so we need to let call fail and return placeholder if not
 110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {
 111:             return _decimals;
 112:         } catch {
 113:             return 0;
 114:         }
 115:     }

```

*GitHub* : [107-115](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L107-L115)

### [L-04]<a name="l-04"></a> Function calls within loops

Making function calls within loops in Solidity can lead to inefficient gas usage, potential bottlenecks, and increased vulnerability to attacks. Each function call or external call consumes gas, and when executed within a loop, the gas cost multiplies, potentially causing the transaction to run out of gas or exceed block gas limits. This can result in transaction failure or unpredictable behavior.

*There are 6 instance(s) of this issue:*

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) has function calls inside a loop: 
	- positionSize = userBalance[tokenId].rightSlot() (contracts/libraries/FeesCalc.sol#53)
	- numLegs = tokenId.countLegs() (contracts/libraries/FeesCalc.sol#54)
	- liquidityChunk = PanopticMath.getLiquidityChunk(tokenId,leg,positionSize) (contracts/libraries/FeesCalc.sol#56-60)
	- (amount0,amount1) = Math.getAmountsForLiquidity(atTick,liquidityChunk) (contracts/libraries/FeesCalc.sol#62-65)
	- tokenId.isLong(leg) == 0 (contracts/libraries/FeesCalc.sol#67)

/// @audit ************** Possible Issue Line(s) **************
	L#53,  L#54,  L#56-60,  L#62-65,  L#67,  

/// @audit ****************** Affected Code *******************
  53:             uint128 positionSize = userBalance[tokenId].rightSlot();
  54:             uint256 numLegs = tokenId.countLegs();
  56:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
  57:                     tokenId,
  58:                     leg,
  59:                     positionSize
  60:                 );
  62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
  63:                     atTick,
  64:                     liquidityChunk
  65:                 );
  67:                 if (tokenId.isLong(leg) == 0) {

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/SemiFungiblePositionManager.sol#566-585) has function calls inside a loop: 
	- s_poolContext[TokenId.wrap(ids[i]).poolId()].locked (contracts/SemiFungiblePositionManager.sol#576)
	- registerTokenTransfer(from,to,TokenId.wrap(ids[i]),amounts[i]) (contracts/SemiFungiblePositionManager.sol#577)

/// @audit ************** Possible Issue Line(s) **************
	L#576,  L#577,  

/// @audit ****************** Affected Code *******************
 566:     function safeBatchTransferFrom(
 567:         address from,
 568:         address to,
 569:         uint256[] calldata ids,
 570:         uint256[] calldata amounts,
 571:         bytes calldata data
 572:     ) public override {
 573:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
 574:         // so just check if there is an active reentrancy lock for the relevant pool on each token
 575:         for (uint256 i = 0; i < ids.length; ) {
 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
 577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
 578:             unchecked {
 579:                 ++i;
 580:             }
 581:         }
 582: 
 583:         // transfer the token (note that all state updates are completed before reentrancy is possible)
 584:         super.safeBatchTransferFrom(from, to, ids, amounts, data);
 585:     }

```

*GitHub* : [566-585](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566-L585)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.initializeAMMPool(address,address,uint24) (contracts/SemiFungiblePositionManager.sol#350-391) has function calls inside a loop: 
	- poolId = PanopticMath.incrementPoolPattern(poolId) (contracts/SemiFungiblePositionManager.sol#373)

/// @audit ************** Possible Issue Line(s) **************
	L#373,  

/// @audit ****************** Affected Code *******************
 373:             poolId = PanopticMath.incrementPoolPattern(poolId);

```

*GitHub* : [350-391](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L350-L391)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned) (contracts/CollateralTracker.sol#650-734) has function calls inside a loop: 
	- leg < positionId.countLegs() (contracts/CollateralTracker.sol#662)
	- positionId.isLong(leg) == 0 (contracts/CollateralTracker.sol#664)
	- range = int24(int256(Math.unsafeDivRoundingUp(uint24(positionId.width(leg) * positionId.tickSpacing()),2))) (contracts/CollateralTracker.sol#667-674)
	- maxNumRangesFromStrike = Math.max(maxNumRangesFromStrike,uint256(Math.abs(currentTick - positionId.strike(leg)) / range)) (contracts/CollateralTracker.sol#675-678)
	- liquidityChunk = PanopticMath.getLiquidityChunk(positionId,leg,positionBalance) (contracts/CollateralTracker.sol#687-691)
	- (currentValue0,currentValue1) = Math.getAmountsForLiquidity(currentTick,liquidityChunk) (contracts/CollateralTracker.sol#693-696)
	- (oracleValue0,oracleValue1) = Math.getAmountsForLiquidity(oracleTick,liquidityChunk) (contracts/CollateralTracker.sol#698-701)
	- tokenType = positionId.tokenType(leg) (contracts/CollateralTracker.sol#704)
	- exerciseFees = exerciseFees.sub(LeftRightSigned.wrap(0).toRightSlot(int128(uint128(oracleValue0)) - int128(uint128(currentValue0))).toLeftSlot(int128(uint128(oracleValue1)) - int128(uint128(currentValue1)))) (contracts/CollateralTracker.sol#711-720)

/// @audit ************** Possible Issue Line(s) **************
	L#662,  L#664,  L#667-674,  L#675-678,  L#687-691,  L#693-696,  L#698-701,  L#704,  L#711-720,  

/// @audit ****************** Affected Code *******************
 662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {
 664:                 if (positionId.isLong(leg) == 0) continue;
 667:                     int24 range = int24(
 668:                         int256(
 669:                             Math.unsafeDivRoundingUp(
 670:                                 uint24(positionId.width(leg) * positionId.tickSpacing()),
 671:                                 2
 672:                             )
 673:                         )
 674:                     );
 675:                     maxNumRangesFromStrike = Math.max(
 676:                         maxNumRangesFromStrike,
 677:                         uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
 678:                     );
 687:                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
 688:                         positionId,
 689:                         leg,
 690:                         positionBalance
 691:                     );
 693:                     (currentValue0, currentValue1) = Math.getAmountsForLiquidity(
 694:                         currentTick,
 695:                         liquidityChunk
 696:                     );
 698:                     (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(
 699:                         oracleTick,
 700:                         liquidityChunk
 701:                     );
 704:                 uint256 tokenType = positionId.tokenType(leg);
 711:                     exerciseFees = exerciseFees.sub(
 712:                         LeftRightSigned
 713:                             .wrap(0)
 714:                             .toRightSlot(
 715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
 716:                             )
 717:                             .toLeftSlot(
 718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
 719:                             )
 720:                     );

```

*GitHub* : [650-734](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L650-L734)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.minePoolAddress(bytes32,uint256,uint256) (contracts/PanopticFactory.sol#290-326) has function calls inside a loop: 
	- rarity = PanopticMath.numberOfLeadingHexZeros(POOL_REFERENCE.predictDeterministicAddress(salt)) (contracts/PanopticFactory.sol#304-306)

/// @audit ************** Possible Issue Line(s) **************
	L#304-306,  

/// @audit ****************** Affected Code *******************
 304:             uint256 rarity = PanopticMath.numberOfLeadingHexZeros(
 305:                 POOL_REFERENCE.predictDeterministicAddress(salt)
 306:             );

```

*GitHub* : [290-326](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L290-L326)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) has function calls inside a loop: 
	- numLegs = tokenId.countLegs() (contracts/libraries/PanopticMath.sol#783)
	- tokenId.isLong(leg) == 1 (contracts/libraries/PanopticMath.sol#785)
	- longPremium = longPremium.sub(premiasByLeg[i][leg]) (contracts/libraries/PanopticMath.sol#786)
	- leg_scope_2 < tokenId_scope_1.countLegs() (contracts/libraries/PanopticMath.sol#863)
	- tokenId_scope_1.isLong(leg_scope_2) == 1 (contracts/libraries/PanopticMath.sol#864)
	- settled0 = Math.unsafeDivRoundingUp(uint128(- _premiasByLeg[i_scope_0][leg_scope_2].rightSlot()) * uint256(haircut0),uint128(longPremium.rightSlot())) (contracts/libraries/PanopticMath.sol#869-872)
	- settled1 = Math.unsafeDivRoundingUp(uint128(- _premiasByLeg[i_scope_0][leg_scope_2].leftSlot()) * uint256(haircut1),uint128(longPremium.leftSlot())) (contracts/libraries/PanopticMath.sol#873-876)
	- chunkKey = keccak256(bytes)(abi.encodePacked(tokenId_scope_1.strike(0),tokenId_scope_1.width(0),tokenId_scope_1.tokenType(0))) (contracts/libraries/PanopticMath.sol#878-884)
	- settled0 = Math.max(0,uint128(- _premiasByLeg[i_scope_0][leg_scope_2].rightSlot()) - settled0) (contracts/libraries/PanopticMath.sol#888-891)
	- settled1 = Math.max(0,uint128(- _premiasByLeg[i_scope_0][leg_scope_2].leftSlot()) - settled1) (contracts/libraries/PanopticMath.sol#892-895)
	- _settledTokens[chunkKey] = _settledTokens[chunkKey].add(LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(uint128(settled1))) (contracts/libraries/PanopticMath.sol#897-901)

/// @audit ************** Possible Issue Line(s) **************
	L#783,  L#785,  L#786,  L#863,  L#864,  L#869-872,  L#873-876,  L#878-884,  L#888-891,  L#892-895,  L#897-901,  

/// @audit ****************** Affected Code *******************
 783:                 uint256 numLegs = tokenId.countLegs();
 785:                     if (tokenId.isLong(leg) == 1) {
 786:                         longPremium = longPremium.sub(premiasByLeg[i][leg]);
 863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
 864:                     if (tokenId.isLong(leg) == 1) {
 869:                         uint256 settled0 = Math.unsafeDivRoundingUp(
 870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
 871:                             uint128(longPremium.rightSlot())
 872:                         );
 873:                         uint256 settled1 = Math.unsafeDivRoundingUp(
 874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
 875:                             uint128(longPremium.leftSlot())
 876:                         );
 878:                         bytes32 chunkKey = keccak256(
 879:                             abi.encodePacked(
 880:                                 tokenId.strike(0),
 881:                                 tokenId.width(0),
 882:                                 tokenId.tokenType(0)
 883:                             )
 884:                         );
 888:                         settled0 = Math.max(
 889:                             0,
 890:                             uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
 891:                         );
 892:                         settled1 = Math.max(
 893:                             0,
 894:                             uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
 895:                         );
 897:                         _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
 898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
 899:                                 uint128(settled1)
 900:                             )
 901:                         );

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

### [L-05]<a name="l-05"></a> Library with public/external functions

Libraries in Solidity are meant to be static collections of functions. They are deployed once and their code is reused by contracts through DELEGATECALL, which executes the library's code in the context of the calling contract. Public or external functions in libraries can be misleading because libraries are not supposed to maintain state or have external interactions in the way contracts do. Designing libraries with these kinds of functions goes against their intended purpose and can lead to confusion or misuse. For state management or external interactions, using contracts instead of libraries is more appropriate. Libraries should focus on utility functions that can operate on the data passed to them without side effects, enhancing code reuse and gas efficiency.

*There are 13 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) is a external function in libraray `PanopticMath`.

/// @audit ****************** Affected Code *******************
 125:     function computeMedianObservedPrice(
 126:         IUniswapV3Pool univ3pool,
 127:         uint256 observationIndex,
 128:         uint256 observationCardinality,
 129:         uint256 cardinality,
 130:         uint256 period
 131:     ) external view returns (int24) {
 132:         unchecked {
 133:             int256[] memory tickCumulatives = new int256[](cardinality + 1);
 134: 

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeSymbol(address,string) (contracts/libraries/InteractionHelper.sol#91-102) is a external function in libraray `InteractionHelper`.

/// @audit ****************** Affected Code *******************
  91:     function computeSymbol(
  92:         address token,
  93:         string memory prefix
  94:     ) external view returns (string memory) {
  95:         // not guaranteed that token supports metadada extension
  96:         // so we need to let call fail and return placeholder if not
  97:         try IERC20Metadata(token).symbol() returns (string memory tokenSymbol) {
  98:             return string.concat(prefix, tokenSymbol);
  99:         } catch {
 100:             return string.concat(prefix, "???");
 101:         }
 102:     }

```

*GitHub* : [91-102](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L91-L102)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeDecimals(address) (contracts/libraries/InteractionHelper.sol#107-115) is a external function in libraray `InteractionHelper`.

/// @audit ****************** Affected Code *******************
 107:     function computeDecimals(address token) external view returns (uint8) {
 108:         // not guaranteed that token supports metadada extension
 109:         // so we need to let call fail and return placeholder if not
 110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {
 111:             return _decimals;
 112:         } catch {
 113:             return 0;
 114:         }
 115:     }

```

*GitHub* : [107-115](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L107-L115)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeName(address,address,bool,uint24,string) (contracts/libraries/InteractionHelper.sol#48-85) is a external function in libraray `InteractionHelper`.

/// @audit ****************** Affected Code *******************
  48:     function computeName(
  49:         address token0,
  50:         address token1,
  51:         bool isToken0,
  52:         uint24 fee,
  53:         string memory prefix
  54:     ) external view returns (string memory) {
  55:         // get the underlying token symbols
  56:         // it's not guaranteed that they support the metadata extension
  57:         // so we need to let them fail and return placeholder if not

```

*GitHub* : [48-85](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L48-L85)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) is a external function in libraray `FeesCalc`.

/// @audit ****************** Affected Code *******************
  46:     function getPortfolioValue(
  47:         int24 atTick,
  48:         mapping(TokenId tokenId => LeftRightUnsigned balance) storage userBalance,
  49:         TokenId[] calldata positionIdList
  50:     ) external view returns (int256 value0, int256 value1) {
  51:         for (uint256 k = 0; k < positionIdList.length; ) {
  52:             TokenId tokenId = positionIdList[k];
  53:             uint128 positionSize = userBalance[tokenId].rightSlot();
  54:             uint256 numLegs = tokenId.countLegs();
  55:             for (uint256 leg = 0; leg < numLegs; ) {

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) is a external function in libraray `PanopticMath`.

/// @audit ****************** Affected Code *******************
 168:     function computeInternalMedian(
 169:         uint256 observationIndex,
 170:         uint256 observationCardinality,
 171:         uint256 period,
 172:         uint256 medianData,
 173:         IUniswapV3Pool univ3pool
 174:     ) external view returns (int24 medianTick, uint256 updatedMedianData) {
 175:         unchecked {
 176:             // return the average of the rank 3 and 4 values
 177:             medianTick =

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) is a external function in libraray `PanopticMath`.

/// @audit ****************** Affected Code *******************
 768:     function haircutPremia(
 769:         address liquidatee,
 770:         TokenId[] memory positionIdList,
 771:         LeftRightSigned[4][] memory premiasByLeg,
 772:         LeftRightSigned collateralRemaining,
 773:         CollateralTracker collateral0,
 774:         CollateralTracker collateral1,
 775:         uint160 sqrtPriceX96Final,
 776:         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
 777:     ) external returns (int256, int256) {

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.calculateAMMSwapFees(IUniswapV3Pool,int24,int24,int24,uint128) (contracts/libraries/FeesCalc.sol#97-119) is a public function in libraray `FeesCalc`.

/// @audit ****************** Affected Code *******************
  97:     function calculateAMMSwapFees(
  98:         IUniswapV3Pool univ3pool,
  99:         int24 currentTick,
 100:         int24 tickLower,
 101:         int24 tickUpper,
 102:         uint128 liquidity
 103:     ) public view returns (LeftRightSigned) {
 104:         // extract the amount of AMM fees collected within the liquidity chunk`
 105:         // note: the fee variables are *per unit of liquidity*; so more "rate" variables
 106:         (
 107:             uint256 ammFeesPerLiqToken0X128,
 108:             uint256 ammFeesPerLiqToken1X128
 109:         ) = _getAMMSwapFeesPerLiquidityCollected(univ3pool, currentTick, tickLower, tickUpper);
 110: 
 111:         // Use the fee growth (rate) variable to compute the absolute fees accumulated within the chunk:
 112:         //   ammFeesToken0X128 * liquidity / (2**128)
 113:         // to store the (absolute) fees as int128:
 114:         return
 115:             LeftRightSigned
 116:                 .wrap(0)
 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))
 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));
 119:     }

```

*GitHub* : [97-119](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L97-L119)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.twapFilter(IUniswapV3Pool,uint32) (contracts/libraries/PanopticMath.sol#241-268) is a external function in libraray `PanopticMath`.

/// @audit ****************** Affected Code *******************
 241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {
 242:         uint32[] memory secondsAgos = new uint32[](20);
 243: 
 244:         int256[] memory twapMeasurement = new int256[](19);
 245: 
 246:         unchecked {
 247:             // construct the time stots
 248:             for (uint256 i = 0; i < 20; ++i) {
 249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);
 250:             }

```

*GitHub* : [241-268](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L241-L268)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.numberOfLeadingHexZeros(address) (contracts/libraries/PanopticMath.sol#75-79) is a external function in libraray `PanopticMath`.

/// @audit ****************** Affected Code *******************
  75:     function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {
  76:         unchecked {
  77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));
  78:         }
  79:     }

```

*GitHub* : [75-79](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L75-L79)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker) (contracts/libraries/PanopticMath.sol#917-966) is a external function in libraray `PanopticMath`.

/// @audit ****************** Affected Code *******************
 917:     function getRefundAmounts(
 918:         address refunder,
 919:         LeftRightSigned refundValues,
 920:         int24 atTick,
 921:         CollateralTracker collateral0,
 922:         CollateralTracker collateral1
 923:     ) external view returns (LeftRightSigned) {
 924:         uint160 sqrtPriceX96 = Math.getSqrtRatioAtTick(atTick);
 925:         unchecked {
 926:             // if the refunder lacks sufficient token0 to pay back the refundee, have them pay back the equivalent value in token1

```

*GitHub* : [917-966](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L917-L966)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned) (contracts/libraries/PanopticMath.sol#651-754) is a external function in libraray `PanopticMath`.

/// @audit ****************** Affected Code *******************
 651:     function getLiquidationBonus(
 652:         LeftRightUnsigned tokenData0,
 653:         LeftRightUnsigned tokenData1,
 654:         uint160 sqrtPriceX96Twap,
 655:         uint160 sqrtPriceX96Final,
 656:         LeftRightSigned netExchanged,
 657:         LeftRightSigned premia
 658:     ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {
 659:         unchecked {
 660:             // compute bonus as min(collateralBalance/2, required-collateralBalance)

```

*GitHub* : [651-754](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L651-L754)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) is a external function in libraray `InteractionHelper`.

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L24-L38)

### [L-06]<a name="l-06"></a> Loops in external functions should be avoided due to high gas costs and possible DOS

In Solidity, for loops can potentially cause Denial of Service (DoS) attacks if not handled carefully. DoS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. For example, Nested loops can become exceptionally gas expensive and should be used sparingly.

*There are 7 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) is external function and has a loop.

/// @audit ****************** Affected Code *******************
 768:     function haircutPremia(
 769:         address liquidatee,
 770:         TokenId[] memory positionIdList,
 771:         LeftRightSigned[4][] memory premiasByLeg,
 772:         LeftRightSigned collateralRemaining,
 773:         CollateralTracker collateral0,
 774:         CollateralTracker collateral1,
 775:         uint160 sqrtPriceX96Final,
 776:         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
 777:     ) external returns (int256, int256) {

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) is external function and has a loop.

/// @audit ****************** Affected Code *******************
 168:     function computeInternalMedian(
 169:         uint256 observationIndex,
 170:         uint256 observationCardinality,
 171:         uint256 period,
 172:         uint256 medianData,
 173:         IUniswapV3Pool univ3pool
 174:     ) external view returns (int24 medianTick, uint256 updatedMedianData) {
 175:         unchecked {
 176:             // return the average of the rank 3 and 4 values
 177:             medianTick =

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.twapFilter(IUniswapV3Pool,uint32) (contracts/libraries/PanopticMath.sol#241-268) is external function and has a loop.

/// @audit ****************** Affected Code *******************
 241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {
 242:         uint32[] memory secondsAgos = new uint32[](20);
 243: 
 244:         int256[] memory twapMeasurement = new int256[](19);
 245: 
 246:         unchecked {
 247:             // construct the time stots
 248:             for (uint256 i = 0; i < 20; ++i) {
 249:                 secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);
 250:             }

```

*GitHub* : [241-268](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L241-L268)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) is external function and has a loop.

/// @audit ****************** Affected Code *******************
 125:     function computeMedianObservedPrice(
 126:         IUniswapV3Pool univ3pool,
 127:         uint256 observationIndex,
 128:         uint256 observationCardinality,
 129:         uint256 cardinality,
 130:         uint256 period
 131:     ) external view returns (int24) {
 132:         unchecked {
 133:             int256[] memory tickCumulatives = new int256[](cardinality + 1);
 134: 

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.minePoolAddress(bytes32,uint256,uint256) (contracts/PanopticFactory.sol#290-326) is external function and has a loop.

/// @audit ****************** Affected Code *******************
 290:     function minePoolAddress(
 291:         bytes32 salt,
 292:         uint256 loops,
 293:         uint256 minTargetRarity
 294:     ) external view returns (bytes32 bestSalt, uint256 highestRarity) {
 295:         // Start at the given 'salt' value (a checkpoint used to continue mining across multiple calls)
 296: 
 297:         // Runs until 'bestSalt' reaches 'minTargetRarity' or for 'loops', whichever comes first
 298:         uint256 maxSalt;
 299:         unchecked {

```

*GitHub* : [290-326](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L290-L326)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) is external function and has a loop.

/// @audit ****************** Affected Code *******************
  46:     function getPortfolioValue(
  47:         int24 atTick,
  48:         mapping(TokenId tokenId => LeftRightUnsigned balance) storage userBalance,
  49:         TokenId[] calldata positionIdList
  50:     ) external view returns (int256 value0, int256 value1) {
  51:         for (uint256 k = 0; k < positionIdList.length; ) {
  52:             TokenId tokenId = positionIdList[k];
  53:             uint128 positionSize = userBalance[tokenId].rightSlot();
  54:             uint256 numLegs = tokenId.countLegs();
  55:             for (uint256 leg = 0; leg < numLegs; ) {

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned) (contracts/CollateralTracker.sol#650-734) is external function and has a loop.

/// @audit ****************** Affected Code *******************
 650:     function exerciseCost(
 651:         int24 currentTick,
 652:         int24 oracleTick,
 653:         TokenId positionId,
 654:         uint128 positionBalance,
 655:         LeftRightSigned longAmounts
 656:     ) external view returns (LeftRightSigned exerciseFees) {
 657:         // find the leg furthest to the strike price 'currentTick'; this will have the lowest exercise cost
 658:         // we don't need the leg information itself, really just "the number of half ranges" from the strike price:
 659:         uint256 maxNumRangesFromStrike = 1; // technically "maxNum(Half)RangesFromStrike" but the name is long

```

*GitHub* : [650-734](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L650-L734)

### [L-07]<a name="l-07"></a> Possible length difference of two array parameters

Ensuring matching input array lengths in functions is crucial to prevent logical errors and inconsistencies in smart contracts. If two array parameters are used within a function, their length must be checked to avoid issues caused by difference in array lengths. If a loop is iterating over longer array, it will cause array out of index error for shorter array and if loop is iterated over shorter array, certian values in longer array may not be read/ written. **Recom:** Validate that lengths of both arrays are same using a `reuquire` of `if` statement before accessing the arrays to avoid issues.

*There are 7 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278) has multiple array parameters 
	- TokenId[] touchedId
	- TokenId[] positionIdListExercisee
	- TokenId[] positionIdListExercisor

/// @audit ****************** Affected Code *******************
1179:     function forceExercise(
1180:         address account,
1181:         TokenId[] calldata touchedId,
1182:         TokenId[] calldata positionIdListExercisee,
1183:         TokenId[] calldata positionIdListExercisor
1184:     ) external {
1185:         // revert if multiple positions are specified
1186:         // the reason why the singular touchedId is an array is so it composes well with the rest of the system
1187:         // '_calculateAccumulatedPremia' expects a list of positions to be touched, and this is the only way to pass a single position
1188:         if (touchedId.length != 1) revert Errors.InputListFail();

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.burnOptions(TokenId[],TokenId[],int24,int24) (contracts/PanopticPool.sol#586-601) has multiple array parameters 
	- TokenId[] positionIdList
	- TokenId[] newPositionIdList

/// @audit ****************** Affected Code *******************
 586:     function burnOptions(
 587:         TokenId[] calldata positionIdList,
 588:         TokenId[] calldata newPositionIdList,
 589:         int24 tickLimitLow,
 590:         int24 tickLimitHigh
 591:     ) external {
 592:         _burnAllOptionsFrom(
 593:             msg.sender,
 594:             tickLimitLow,
 595:             tickLimitHigh,
 596:             COMMIT_LONG_SETTLED,
 597:             positionIdList
 598:         );
 599: 
 600:         _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);
 601:     }

```

*GitHub* : [586-601](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L586-L601)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.balanceOfBatch(address[],uint256[]) (contracts/tokens/ERC1155Minimal.sol#178-191) has multiple array parameters 
	- address[] owners
	- uint256[] ids

/// @audit ****************** Affected Code *******************
 178:     function balanceOfBatch(
 179:         address[] calldata owners,
 180:         uint256[] calldata ids
 181:     ) public view returns (uint256[] memory balances) {
 182:         balances = new uint256[](owners.length);
 183: 
 184:         // Unchecked because the only math done is incrementing
 185:         // the array index counter which cannot possibly overflow.
 186:         unchecked {
 187:             for (uint256 i = 0; i < owners.length; ++i) {
 188:                 balances[i] = balanceOf[owners[i]][ids[i]];
 189:             }
 190:         }
 191:     }

```

*GitHub* : [178-191](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L178-L191)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/SemiFungiblePositionManager.sol#566-585) has multiple array parameters 
	- uint256[] ids
	- uint256[] amounts

/// @audit ****************** Affected Code *******************
 566:     function safeBatchTransferFrom(
 567:         address from,
 568:         address to,
 569:         uint256[] calldata ids,
 570:         uint256[] calldata amounts,
 571:         bytes calldata data
 572:     ) public override {
 573:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
 574:         // so just check if there is an active reentrancy lock for the relevant pool on each token
 575:         for (uint256 i = 0; i < ids.length; ) {
 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
 577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
 578:             unchecked {
 579:                 ++i;
 580:             }
 581:         }
 582: 
 583:         // transfer the token (note that all state updates are completed before reentrancy is possible)
 584:         super.safeBatchTransferFrom(from, to, ids, amounts, data);
 585:     }

```

*GitHub* : [566-585](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566-L585)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/tokens/ERC1155Minimal.sol#130-171) has multiple array parameters 
	- uint256[] ids
	- uint256[] amounts

/// @audit ****************** Affected Code *******************
 130:     function safeBatchTransferFrom(
 131:         address from,
 132:         address to,
 133:         uint256[] calldata ids,
 134:         uint256[] calldata amounts,
 135:         bytes calldata data
 136:     ) public virtual {
 137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
 138: 
 139:         // Storing these outside the loop saves ~15 gas per iteration.

```

*GitHub* : [130-171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L130-L171)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) has multiple array parameters 
	- TokenId[] positionIdListLiquidator
	- TokenId[] positionIdList

/// @audit ****************** Affected Code *******************
1017:     function liquidate(
1018:         TokenId[] calldata positionIdListLiquidator,
1019:         address liquidatee,
1020:         LeftRightUnsigned delegations,
1021:         TokenId[] calldata positionIdList
1022:     ) external {
1023:         _validatePositionList(liquidatee, positionIdList, 0);
1024: 
1025:         // Assert the account we are liquidating is actually insolvent
1026:         int24 twapTick = getUniV3TWAP();

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) has multiple array parameters 
	- TokenId[] positionIdList
	- LeftRightSigned[4][] premiasByLeg

/// @audit ****************** Affected Code *******************
 768:     function haircutPremia(
 769:         address liquidatee,
 770:         TokenId[] memory positionIdList,
 771:         LeftRightSigned[4][] memory premiasByLeg,
 772:         LeftRightSigned collateralRemaining,
 773:         CollateralTracker collateral0,
 774:         CollateralTracker collateral1,
 775:         uint160 sqrtPriceX96Final,
 776:         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
 777:     ) external returns (int256, int256) {

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

### [L-08]<a name="l-08"></a> Missing zero address check in initializer

Initializer functions in contracts often set important parameters or addresses. Failing to check for the zero address (0x0000000000000000000000000000000000000000) in initializers can lead to unintended behavior, as this address typically signifies an unset or default value. Transfers to or interactions with the zero address can result in permanent loss of assets or broken functionality. It's crucial to add checks using `require(targetAddress != address(0), 'Address cannot be zero')` in initializers to prevent accidentally setting important state variables or parameters to this address, ensuring the system's integrity and user asset safety.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.initialize(address) (contracts/PanopticFactory.sol#134-139) does not check for zero address on :-
	- PanopticFactory.initialize(address)._owner (contracts/PanopticFactory.sol#134)

/// @audit ************** Possible Issue Line(s) **************
	L#134,  

/// @audit ****************** Affected Code *******************
 134:     function initialize(address _owner) public {
 135:         if (!s_initialized) {
 136:             s_owner = _owner;
 137:             s_initialized = true;
 138:         }
 139:     }

```

*GitHub* : [134-139](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L134-L139)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.initializeAMMPool(address,address,uint24) (contracts/SemiFungiblePositionManager.sol#350-391) does not check for zero address on :-
	- SemiFungiblePositionManager.initializeAMMPool(address,address,uint24).token0 (contracts/SemiFungiblePositionManager.sol#350)	- SemiFungiblePositionManager.initializeAMMPool(address,address,uint24).token1 (contracts/SemiFungiblePositionManager.sol#350)

/// @audit ************** Possible Issue Line(s) **************
	L#350,  

/// @audit ****************** Affected Code *******************
 350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

```

*GitHub* : [350-391](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L350-L391)

### [L-09]<a name="l-09"></a> Use of Nested Loop

Nested loops grow fast and often become bottleneck for execution and gas consumption. Consider using single loop to avoid bricking the protocol.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) runs following in nested loop :- 
	- leg < numLegs (contracts/libraries/FeesCalc.sol#55)
	- liquidityChunk = PanopticMath.getLiquidityChunk(tokenId,leg,positionSize) (contracts/libraries/FeesCalc.sol#56-60)
	- NEW VARIABLE amount0 (contracts/libraries/FeesCalc.sol#62)
	- NEW VARIABLE amount1 (contracts/libraries/FeesCalc.sol#62)
	- (amount0,amount1) = Math.getAmountsForLiquidity(atTick,liquidityChunk) (contracts/libraries/FeesCalc.sol#62-65)
	- tokenId.isLong(leg) == 0 (contracts/libraries/FeesCalc.sol#67)
	- value0 += int256(amount0) (contracts/libraries/FeesCalc.sol#69)
	- value1 += int256(amount1) (contracts/libraries/FeesCalc.sol#70)
	- ++ leg (contracts/libraries/FeesCalc.sol#80)
	- value0 -= int256(amount0) (contracts/libraries/FeesCalc.sol#74)
	- value1 -= int256(amount1) (contracts/libraries/FeesCalc.sol#75)

/// @audit ************** Possible Issue Line(s) **************
	L#55,  L#56-60,  L#62,  L#62-65,  L#67,  L#69,  L#70,  L#80,  L#74,  L#75,  

/// @audit ****************** Affected Code *******************
  55:             for (uint256 leg = 0; leg < numLegs; ) {
  56:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
  57:                     tokenId,
  58:                     leg,
  59:                     positionSize
  60:                 );
  62:                 (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
  63:                     atTick,
  64:                     liquidityChunk
  65:                 );
  67:                 if (tokenId.isLong(leg) == 0) {
  69:                         value0 += int256(amount0);
  70:                         value1 += int256(amount1);
  74:                         value0 -= int256(amount0);
  75:                         value1 -= int256(amount1);
  80:                     ++leg;

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) runs following in nested loop :- 
	- leg < numLegs (contracts/libraries/PanopticMath.sol#784)
	- tokenId.isLong(leg) == 1 (contracts/libraries/PanopticMath.sol#785)
	- longPremium = longPremium.sub(premiasByLeg[i][leg]) (contracts/libraries/PanopticMath.sol#786)
	- ++ leg (contracts/libraries/PanopticMath.sol#784)
	- leg_scope_2 < tokenId_scope_1.countLegs() (contracts/libraries/PanopticMath.sol#863)
	- tokenId_scope_1.isLong(leg_scope_2) == 1 (contracts/libraries/PanopticMath.sol#864)
	- _settledTokens = settledTokens (contracts/libraries/PanopticMath.sol#865-866)
	- settled0 = Math.unsafeDivRoundingUp(uint128(- _premiasByLeg[i_scope_0][leg_scope_2].rightSlot()) * uint256(haircut0),uint128(longPremium.rightSlot())) (contracts/libraries/PanopticMath.sol#869-872)
	- settled1 = Math.unsafeDivRoundingUp(uint128(- _premiasByLeg[i_scope_0][leg_scope_2].leftSlot()) * uint256(haircut1),uint128(longPremium.leftSlot())) (contracts/libraries/PanopticMath.sol#873-876)
	- chunkKey = keccak256(bytes)(abi.encodePacked(tokenId_scope_1.strike(0),tokenId_scope_1.width(0),tokenId_scope_1.tokenType(0))) (contracts/libraries/PanopticMath.sol#878-884)
	- settled0 = Math.max(0,uint128(- _premiasByLeg[i_scope_0][leg_scope_2].rightSlot()) - settled0) (contracts/libraries/PanopticMath.sol#888-891)
	- settled1 = Math.max(0,uint128(- _premiasByLeg[i_scope_0][leg_scope_2].leftSlot()) - settled1) (contracts/libraries/PanopticMath.sol#892-895)
	- _settledTokens[chunkKey] = _settledTokens[chunkKey].add(LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(uint128(settled1))) (contracts/libraries/PanopticMath.sol#897-901)
	- ++ leg_scope_2 (contracts/libraries/PanopticMath.sol#863)

/// @audit ************** Possible Issue Line(s) **************
	L#784,  L#785,  L#786,  L#863,  L#864,  L#865-866,  L#869-872,  L#873-876,  L#878-884,  L#888-891,  L#892-895,  L#897-901,  

/// @audit ****************** Affected Code *******************
 784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {
 785:                     if (tokenId.isLong(leg) == 1) {
 786:                         longPremium = longPremium.sub(premiasByLeg[i][leg]);
 863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
 864:                     if (tokenId.isLong(leg) == 1) {
 865:                         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
 866:                             storage _settledTokens = settledTokens;
 869:                         uint256 settled0 = Math.unsafeDivRoundingUp(
 870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
 871:                             uint128(longPremium.rightSlot())
 872:                         );
 873:                         uint256 settled1 = Math.unsafeDivRoundingUp(
 874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
 875:                             uint128(longPremium.leftSlot())
 876:                         );
 878:                         bytes32 chunkKey = keccak256(
 879:                             abi.encodePacked(
 880:                                 tokenId.strike(0),
 881:                                 tokenId.width(0),
 882:                                 tokenId.tokenType(0)
 883:                             )
 884:                         );
 888:                         settled0 = Math.max(
 889:                             0,
 890:                             uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
 891:                         );
 892:                         settled1 = Math.max(
 893:                             0,
 894:                             uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
 895:                         );
 897:                         _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
 898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
 899:                                 uint128(settled1)
 900:                             )
 901:                         );

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

### [L-10]<a name="l-10"></a> Upgradable contracts not taken into account when making wrapped calls

When wrapping a token address with interfaces like IERC20 for external calls, especially in the context of upgradable contracts, it's essential to account for the potential changes these tokens might undergo. Upgrades can modify a token's behavior or interface, which could introduce compatibility issues or vulnerabilities in the interacting protocol. **Recom:** To manage this risk, integrate an allowlist system in your protocol. This system would monitor for upgrades in token contracts. Upon detecting an upgrade, the corresponding token contract would be automatically removed from the allowlist, suspending its interaction with your protocol. The contract can only be re-added to the allowlist after a thorough review to confirm its continued compatibility and safety post-upgrade. This approach helps maintain a secure and adaptable protocol, ensuring it only interacts with verified, stable versions of external contracts. Regular audits and ongoing monitoring of these external contracts are vital for maintaining the integrity and security of the protocol.

*There are 8 instance(s) of this issue:*

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) casts address to ERC20
	- IERC20Partial(token0).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#32) casts (address) to (IERC20Partial).
	- IERC20Partial(token1).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#33) casts (address) to (IERC20Partial).

/// @audit ************** Possible Issue Line(s) **************
	L#32,  L#33,  

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L24-L38)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeName(address,address,bool,uint24,string) (contracts/libraries/InteractionHelper.sol#48-85) casts address to ERC20
	- _symbol = IERC20Metadata(token0).symbol() (contracts/libraries/InteractionHelper.sol#60-64) casts (address) to (IERC20Metadata).

/// @audit ************** Possible Issue Line(s) **************
	L#60-64,  

/// @audit ****************** Affected Code *******************
  60:         try IERC20Metadata(token0).symbol() returns (string memory _symbol) {
  61:             symbol0 = _symbol;
  62:         } catch {
  63:             symbol0 = "???";
  64:         }

```

*GitHub* : [48-85](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L48-L85)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeDecimals(address) (contracts/libraries/InteractionHelper.sol#107-115) casts address to ERC20
	- _decimals = IERC20Metadata(token).decimals() (contracts/libraries/InteractionHelper.sol#110-114) casts (address) to (IERC20Metadata).

/// @audit ************** Possible Issue Line(s) **************
	L#110-114,  

/// @audit ****************** Affected Code *******************
 107:     function computeDecimals(address token) external view returns (uint8) {
 108:         // not guaranteed that token supports metadada extension
 109:         // so we need to let call fail and return placeholder if not
 110:         try IERC20Metadata(token).decimals() returns (uint8 _decimals) {
 111:             return _decimals;
 112:         } catch {
 113:             return 0;
 114:         }
 115:     }

```

*GitHub* : [107-115](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L107-L115)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeSymbol(address,string) (contracts/libraries/InteractionHelper.sol#91-102) casts address to ERC20
	- tokenSymbol = IERC20Metadata(token).symbol() (contracts/libraries/InteractionHelper.sol#97-101) casts (address) to (IERC20Metadata).

/// @audit ************** Possible Issue Line(s) **************
	L#97-101,  

/// @audit ****************** Affected Code *******************
  91:     function computeSymbol(
  92:         address token,
  93:         string memory prefix
  94:     ) external view returns (string memory) {
  95:         // not guaranteed that token supports metadada extension
  96:         // so we need to let call fail and return placeholder if not
  97:         try IERC20Metadata(token).symbol() returns (string memory tokenSymbol) {
  98:             return string.concat(prefix, tokenSymbol);
  99:         } catch {
 100:             return string.concat(prefix, "???");
 101:         }
 102:     }

```

*GitHub* : [91-102](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L91-L102)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) casts address to ERC20
	- IERC20Partial(token0).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#32) casts (address) to (IERC20Partial).

/// @audit ************** Possible Issue Line(s) **************
	L#32,  

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L24-L38)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeName(address,address,bool,uint24,string) (contracts/libraries/InteractionHelper.sol#48-85) casts address to ERC20
	- _symbol = IERC20Metadata(token0).symbol() (contracts/libraries/InteractionHelper.sol#60-64) casts (address) to (IERC20Metadata).
	- _symbol_scope_0 = IERC20Metadata(token1).symbol() (contracts/libraries/InteractionHelper.sol#65-69) casts (address) to (IERC20Metadata).

/// @audit ************** Possible Issue Line(s) **************
	L#60-64,  L#65-69,  

/// @audit ****************** Affected Code *******************
  60:         try IERC20Metadata(token0).symbol() returns (string memory _symbol) {
  61:             symbol0 = _symbol;
  62:         } catch {
  63:             symbol0 = "???";
  64:         }
  65:         try IERC20Metadata(token1).symbol() returns (string memory _symbol) {
  66:             symbol1 = _symbol;
  67:         } catch {
  68:             symbol1 = "???";
  69:         }

```

*GitHub* : [48-85](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L48-L85)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) casts address to ERC20
	- IERC20Partial(token0).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#32) casts (address) to (IERC20Partial).
	- IERC20Partial(token1).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#33) casts (address) to (IERC20Partial).
	- IERC20Partial(token0).approve(address(ct0),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#36) casts (address) to (IERC20Partial).
	- IERC20Partial(token1).approve(address(ct1),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#37) casts (address) to (IERC20Partial).

/// @audit ************** Possible Issue Line(s) **************
	L#32,  L#33,  L#36,  L#37,  

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L24-L38)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.doApprovals(SemiFungiblePositionManager,CollateralTracker,CollateralTracker,address,address) (contracts/libraries/InteractionHelper.sol#24-38) casts address to ERC20
	- IERC20Partial(token0).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#32) casts (address) to (IERC20Partial).
	- IERC20Partial(token1).approve(address(sfpm),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#33) casts (address) to (IERC20Partial).
	- IERC20Partial(token0).approve(address(ct0),type()(uint256).max) (contracts/libraries/InteractionHelper.sol#36) casts (address) to (IERC20Partial).

/// @audit ************** Possible Issue Line(s) **************
	L#32,  L#33,  L#36,  

/// @audit ****************** Affected Code *******************
  24:     function doApprovals(
  25:         SemiFungiblePositionManager sfpm,
  26:         CollateralTracker ct0,
  27:         CollateralTracker ct1,
  28:         address token0,
  29:         address token1
  30:     ) external {
  31:         // Approve transfers of Panoptic Pool funds by SFPM
  32:         IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
  33:         IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
  34: 
  35:         // Approve transfers of Panoptic Pool funds by Collateral token
  36:         IERC20Partial(token0).approve(address(ct0), type(uint256).max);
  37:         IERC20Partial(token1).approve(address(ct1), type(uint256).max);
  38:     }

```

*GitHub* : [24-38](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L24-L38)

### [L-11]<a name="l-11"></a> Unsafe `uint` to `int` conversion

Unsafe conversion from `uint` to `int` in Solidity can lead to unexpected overflows if the unsigned integer value exceeds the positive limit of the corresponding signed integer type. This is due to the fact that signed integers use one bit for the sign, effectively halving the positive range. An example is converting a `uint256` number greater than `type(uint128).max` to an `int256`, which can result in an overflow. To mitigate this risk, consider using libraries like SafeCast, which include functions specifically designed to safely cast between different numerical types. They perform necessary checks and revert the transaction if an unsafe cast is attempted, thereby enhancing the security and robustness of the code.

*There are 55 instance(s) of this issue:*

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.tickSpacing(TokenId) (contracts/types/TokenId.sol#96-100) performs unsafe type conversion from `uint` to `int`
	- int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16)) (contracts/types/TokenId.sol#98) convert uint24 to int24).

/// @audit ************** Possible Issue Line(s) **************
	L#98,  

/// @audit ****************** Affected Code *******************
  96:     function tickSpacing(TokenId self) internal pure returns (int24) {
  97:         unchecked {
  98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));
  99:         }
 100:     }

```

*GitHub* : [96-100](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L96-L100)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.calculateAMMSwapFees(IUniswapV3Pool,int24,int24,int24,uint128) (contracts/libraries/FeesCalc.sol#97-119) performs unsafe type conversion from `uint` to `int`
	- LeftRightSigned.wrap(0).toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128,liquidity)))).toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128,liquidity)))) (contracts/libraries/FeesCalc.sol#114-118) convert uint256 to int256).
	- LeftRightSigned.wrap(0).toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128,liquidity)))).toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128,liquidity)))) (contracts/libraries/FeesCalc.sol#114-118) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#114-118,  

/// @audit ****************** Affected Code *******************
  97:     function calculateAMMSwapFees(
  98:         IUniswapV3Pool univ3pool,
  99:         int24 currentTick,
 100:         int24 tickLower,
 101:         int24 tickUpper,
 102:         uint128 liquidity
 103:     ) public view returns (LeftRightSigned) {
 104:         // extract the amount of AMM fees collected within the liquidity chunk`
 105:         // note: the fee variables are *per unit of liquidity*; so more "rate" variables
 106:         (
 107:             uint256 ammFeesPerLiqToken0X128,
 108:             uint256 ammFeesPerLiqToken1X128
 109:         ) = _getAMMSwapFeesPerLiquidityCollected(univ3pool, currentTick, tickLower, tickUpper);
 110: 
 111:         // Use the fee growth (rate) variable to compute the absolute fees accumulated within the chunk:
 112:         //   ammFeesToken0X128 * liquidity / (2**128)
 113:         // to store the (absolute) fees as int128:
 114:         return
 115:             LeftRightSigned
 116:                 .wrap(0)
 117:                 .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))
 118:                 .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));
 119:     }

```

*GitHub* : [97-119](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L97-L119)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._burnLiquidity(LiquidityChunk,IUniswapV3Pool) (contracts/SemiFungiblePositionManager.sol#1224-1245) performs unsafe type conversion from `uint` to `int`
	- movedAmounts = LeftRightSigned.wrap(0).toRightSlot(- int128(int256(amount0))).toLeftSlot(- int128(int256(amount1))) (contracts/SemiFungiblePositionManager.sol#1241-1243) convert uint256 to int256).
	- movedAmounts = LeftRightSigned.wrap(0).toRightSlot(- int128(int256(amount0))).toLeftSlot(- int128(int256(amount1))) (contracts/SemiFungiblePositionManager.sol#1241-1243) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1241-1243,  

/// @audit ****************** Affected Code *******************
1224:     function _burnLiquidity(
1225:         LiquidityChunk liquidityChunk,
1226:         IUniswapV3Pool univ3pool
1227:     ) internal returns (LeftRightSigned movedAmounts) {
1228:         // burn that option's liquidity in the Uniswap Pool.
1229:         // This will send the underlying tokens back to the Panoptic Pool (msg.sender)
1230:         (uint256 amount0, uint256 amount1) = univ3pool.burn(
1231:             liquidityChunk.tickLower(),
1232:             liquidityChunk.tickUpper(),
1233:             liquidityChunk.liquidity()
1234:         );
1235: 
1236:         // amount0 The amount of token0 that was sent back to the Panoptic Pool
1237:         // amount1 The amount of token1 that was sent back to the Panoptic Pool
1238:         // no need to safecast to int from uint here as the max position size is int128
1239:         // decrement the amountsOut with burnt amounts. amountsOut = notional value of tokens moved
1240:         unchecked {
1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(
1242:                 -int128(int256(amount1))
1243:             );
1244:         }
1245:     }

```

*GitHub* : [1224-1245](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1224-L1245)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#1138-1178) performs unsafe type conversion from `uint` to `int`
	- feesBase = LeftRightSigned.wrap(0).toRightSlot(int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128,liquidity)))).toLeftSlot(int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128,liquidity)))) (contracts/SemiFungiblePositionManager.sol#1165-1177) convert uint256 to int256).
	- feesBase = LeftRightSigned.wrap(0).toRightSlot(int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128,liquidity)))).toLeftSlot(int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128,liquidity)))) (contracts/SemiFungiblePositionManager.sol#1165-1177) convert uint256 to int256).
	- feesBase = LeftRightSigned.wrap(0).toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128,liquidity)))).toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128,liquidity)))) (contracts/SemiFungiblePositionManager.sol#1165-1177) convert uint256 to int256).
	- feesBase = LeftRightSigned.wrap(0).toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128,liquidity)))).toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128,liquidity)))) (contracts/SemiFungiblePositionManager.sol#1165-1177) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1165-1177,  

/// @audit ****************** Affected Code *******************
1165:         feesBase = roundUp
1166:             ? LeftRightSigned
1167:                 .wrap(0)
1168:                 .toRightSlot(
1169:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))
1170:                 )
1171:                 .toLeftSlot(
1172:                     int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))
1173:                 )
1174:             : LeftRightSigned
1175:                 .wrap(0)
1176:                 .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))
1177:                 .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

```

*GitHub* : [1138-1178](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1138-L1178)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getPremia(TokenId,uint128,address,bool,int24) (contracts/PanopticPool.sol#1503-1575) performs unsafe type conversion from `uint` to `int`
	- premiaByLeg[leg] = LeftRightSigned.wrap(0).toRightSlot(int128(int256(((premiumAccumulatorsByLeg[leg][0] - premiumAccumulatorLast.rightSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))).toLeftSlot(int128(int256(((premiumAccumulatorsByLeg[leg][1] - premiumAccumulatorLast.leftSlot()) * (liquidityChunk.liquidity())) / 2 ** 64))) (contracts/PanopticPool.sol#1545-1564) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1545-1564,  

/// @audit ****************** Affected Code *******************
1545:                     premiaByLeg[leg] = LeftRightSigned
1546:                         .wrap(0)
1547:                         .toRightSlot(
1548:                             int128(
1549:                                 int256(
1550:                                     ((premiumAccumulatorsByLeg[leg][0] -
1551:                                         premiumAccumulatorLast.rightSlot()) *
1552:                                         (liquidityChunk.liquidity())) / 2 ** 64
1553:                                 )
1554:                             )
1555:                         )
1556:                         .toLeftSlot(
1557:                             int128(
1558:                                 int256(
1559:                                     ((premiumAccumulatorsByLeg[leg][1] -
1560:                                         premiumAccumulatorLast.leftSlot()) *
1561:                                         (liquidityChunk.liquidity())) / 2 ** 64
1562:                                 )
1563:                             )
1564:                         );

```

*GitHub* : [1503-1575](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1503-L1575)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) performs unsafe type conversion from `uint` to `int`
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180) convert uint24 to int24).
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180) convert uint24 to int24).

/// @audit ************** Possible Issue Line(s) **************
	L#177-180,  

/// @audit ****************** Affected Code *******************
 177:             medianTick =
 178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
 179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
 180:                 2;

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1600-1649) performs unsafe type conversion from `uint` to `int`
	- poolUtilization = uint128(uint64(- int64(1))) + (uint128(uint64(- int64(1))) << 64) (contracts/CollateralTracker.sol#1636-1638) convert uint256 to int64).
	- poolUtilization = uint128(uint64(- int64(1))) + (uint128(uint64(- int64(1))) << 64) (contracts/CollateralTracker.sol#1636-1638) convert uint256 to int64).

/// @audit ************** Possible Issue Line(s) **************
	L#1636-1638,  

/// @audit ****************** Affected Code *******************
1636:             poolUtilization =
1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +
1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```

*GitHub* : [1600-1649](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1600-L1649)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._calculateAccumulatedPremia(address,TokenId[],bool,bool,int24) (contracts/PanopticPool.sol#429-492) performs unsafe type conversion from `uint` to `int`
	- portfolioPremium = portfolioPremium.add(LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))) (contracts/PanopticPool.sol#476-478) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#476-478,  

/// @audit ****************** Affected Code *******************
 476:                     portfolioPremium = portfolioPremium.add(
 477:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
 478:                     );

```

*GitHub* : [429-492](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L429-L492)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) performs unsafe type conversion from `uint` to `int`
	- settledTokens = LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(settledTokens))).sub(legPremia)))) (contracts/PanopticPool.sol#1866-1874) convert uint256 to int256).
	- realizedPremia = realizedPremia.add(LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))) (contracts/PanopticPool.sol#1900-1902) convert uint256 to int256).
	- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(uint256(Math.max((int256(grossPremiumLast.rightSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][0] * positionLiquidity)) + int256(legPremia.rightSlot() * 2 ** 64),0)) / totalLiquidity)).toLeftSlot(uint128(uint256(Math.max((int256(grossPremiumLast.leftSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][1] * positionLiquidity)) + int256(legPremia.leftSlot()) * 2 ** 64,0)) / totalLiquidity)) (contracts/PanopticPool.sol#1928-1968) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1866-1874,  L#1900-1902,  L#1928-1968,  

/// @audit ****************** Affected Code *******************
1866:                         settledTokens = LeftRightUnsigned.wrap(
1867:                             uint256(
1868:                                 LeftRightSigned.unwrap(
1869:                                     LeftRightSigned
1870:                                         .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1871:                                         .sub(legPremia)
1872:                                 )
1873:                             )
1874:                         );
1900:                     realizedPremia = realizedPremia.add(
1901:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1902:                     );
1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929:                             ? LeftRightUnsigned
1930:                                 .wrap(0)
1931:                                 .toRightSlot(
1932:                                     uint128(
1933:                                         uint256(
1934:                                             Math.max(
1935:                                                 (int256(
1936:                                                     grossPremiumLast.rightSlot() *
1937:                                                         totalLiquidityBefore
1938:                                                 ) -
1939:                                                     int256(
1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941:                                                             positionLiquidity
1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),
1943:                                                 0
1944:                                             )
1945:                                         ) / totalLiquidity
1946:                                     )
1947:                                 )
1948:                                 .toLeftSlot(
1949:                                     uint128(
1950:                                         uint256(
1951:                                             Math.max(
1952:                                                 (int256(
1953:                                                     grossPremiumLast.leftSlot() *
1954:                                                         totalLiquidityBefore
1955:                                                 ) -
1956:                                                     int256(
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958:                                                             positionLiquidity
1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960:                                                 0
1961:                                             )
1962:                                         ) / totalLiquidity
1963:                                     )
1964:                                 )
1965:                             : LeftRightUnsigned
1966:                                 .wrap(0)
1967:                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));

```

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker) (contracts/libraries/PanopticMath.sol#917-966) performs unsafe type conversion from `uint` to `int`
	- balanceShortage = refundValues.rightSlot() - int256(collateral0.convertToAssets(collateral0.balanceOf(refunder))) (contracts/libraries/PanopticMath.sol#928-929) convert uint256 to int256).
	- LeftRightSigned.wrap(0).toRightSlot(int128(refundValues.rightSlot() - balanceShortage)).toLeftSlot(int128(int256(PanopticMath.convert0to1(uint256(balanceShortage),sqrtPriceX96)) + refundValues.leftSlot())) (contracts/libraries/PanopticMath.sol#932-942) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#928-929,  L#932-942,  

/// @audit ****************** Affected Code *******************
 928:             int256 balanceShortage = refundValues.rightSlot() -
 929:                 int256(collateral0.convertToAssets(collateral0.balanceOf(refunder)));
 932:                 return
 933:                     LeftRightSigned
 934:                         .wrap(0)
 935:                         .toRightSlot(int128(refundValues.rightSlot() - balanceShortage))
 936:                         .toLeftSlot(
 937:                             int128(
 938:                                 int256(
 939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
 940:                                 ) + refundValues.leftSlot()
 941:                             )
 942:                         );

```

*GitHub* : [917-966](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L917-L966)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exercise(address,int128,int128,int128,int128) (contracts/CollateralTracker.sol#1043-1089) performs unsafe type conversion from `uint` to `int`
	- updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount (contracts/CollateralTracker.sol#1052) convert uint256 to int256).
	- s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount))) (contracts/CollateralTracker.sol#1085) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1052,  L#1085,  

/// @audit ****************** Affected Code *******************
1052:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

```

*GitHub* : [1043-1089](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1043-L1089)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned) (contracts/CollateralTracker.sol#650-734) performs unsafe type conversion from `uint` to `int`
	- range = int24(int256(Math.unsafeDivRoundingUp(uint24(positionId.width(leg) * positionId.tickSpacing()),2))) (contracts/CollateralTracker.sol#667-674) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#667-674,  

/// @audit ****************** Affected Code *******************
 667:                     int24 range = int24(
 668:                         int256(
 669:                             Math.unsafeDivRoundingUp(
 670:                                 uint24(positionId.width(leg) * positionId.tickSpacing()),
 671:                                 2
 672:                             )
 673:                         )
 674:                     );

```

*GitHub* : [650-734](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L650-L734)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.slitherConstructorConstantVariables() (contracts/types/LeftRight.sol#17-302) performs unsafe type conversion from `uint` to `int`
	- LEFT_HALF_BIT_MASK_INT = int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000)) (contracts/types/LeftRight.sol#26-27) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#26-27,  

/// @audit ****************** Affected Code *******************
  26:     int256 internal constant LEFT_HALF_BIT_MASK_INT =
  27:         int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

```

*GitHub* : [17-302](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L17-L302)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._mintLiquidity(LiquidityChunk,IUniswapV3Pool) (contracts/SemiFungiblePositionManager.sol#1185-1217) performs unsafe type conversion from `uint` to `int`
	- movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(int128(int256(amount1))) (contracts/SemiFungiblePositionManager.sol#1214-1216) convert uint256 to int256).
	- movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(int128(int256(amount1))) (contracts/SemiFungiblePositionManager.sol#1214-1216) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1214-1216,  

/// @audit ****************** Affected Code *******************
1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(
1215:             int128(int256(amount1))
1216:         );

```

*GitHub* : [1185-1217](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1185-L1217)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker) (contracts/libraries/PanopticMath.sol#917-966) performs unsafe type conversion from `uint` to `int`
	- balanceShortage = refundValues.rightSlot() - int256(collateral0.convertToAssets(collateral0.balanceOf(refunder))) (contracts/libraries/PanopticMath.sol#928-929) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#928-929,  

/// @audit ****************** Affected Code *******************
 928:             int256 balanceShortage = refundValues.rightSlot() -
 929:                 int256(collateral0.convertToAssets(collateral0.balanceOf(refunder)));

```

*GitHub* : [917-966](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L917-L966)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exercise(address,int128,int128,int128,int128) (contracts/CollateralTracker.sol#1043-1089) performs unsafe type conversion from `uint` to `int`
	- updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount (contracts/CollateralTracker.sol#1052) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1052,  

/// @audit ****************** Affected Code *******************
1052:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

```

*GitHub* : [1043-1089](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1043-L1089)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) performs unsafe type conversion from `uint` to `int`
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180) convert uint24 to int24).
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180) convert uint24 to int24).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#177-180,  L#186-190,  

/// @audit ****************** Affected Code *******************
 177:             medianTick =
 178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
 179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
 180:                 2;
 186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(
 187:                         uint256(
 188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)
 189:                         ) % observationCardinality
 190:                     );

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getRangesFromStrike(int24,int24) (contracts/libraries/PanopticMath.sol#371-379) performs unsafe type conversion from `uint` to `int`
	- ((width * tickSpacing) / 2,int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing),2)))) (contracts/libraries/PanopticMath.sol#375-378) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#375-378,  

/// @audit ****************** Affected Code *******************
 371:     function getRangesFromStrike(
 372:         int24 width,
 373:         int24 tickSpacing
 374:     ) internal pure returns (int24, int24) {
 375:         return (
 376:             (width * tickSpacing) / 2,
 377:             int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))
 378:         );
 379:     }

```

*GitHub* : [371-379](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L371-L379)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) performs unsafe type conversion from `uint` to `int`
	- value0 += int256(amount0) (contracts/libraries/FeesCalc.sol#69) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#69,  

/// @audit ****************** Affected Code *******************
  69:                         value0 += int256(amount0);

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.sort(int256[]) (contracts/libraries/Math.sol#776-781) performs unsafe type conversion from `uint` to `int`
	- quickSort(data,int256(0),int256(data.length - 1)) (contracts/libraries/Math.sol#778) convert uint256 to int256).
	- quickSort(data,int256(0),int256(data.length - 1)) (contracts/libraries/Math.sol#778) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#778,  

/// @audit ****************** Affected Code *******************
 776:     function sort(int256[] memory data) internal pure returns (int256[] memory) {
 777:         unchecked {
 778:             quickSort(data, int256(0), int256(data.length - 1));
 779:         }
 780:         return data;
 781:     }

```

*GitHub* : [776-781](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L776-L781)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getExchangedAmount(int128,int128,int128) (contracts/CollateralTracker.sol#1096-1126) performs unsafe type conversion from `uint` to `int`
	- exchangedAmount = intrinsicValue + int256(swapCommission) (contracts/CollateralTracker.sol#1115) convert uint256 to int256).
	- exchangedAmount += int256(Math.unsafeDivRoundingUp(uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,DECIMALS)) (contracts/CollateralTracker.sol#1119-1124) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1115,  L#1119-1124,  

/// @audit ****************** Affected Code *******************
1115:                 exchangedAmount = intrinsicValue + int256(swapCommission);
1119:             exchangedAmount += int256(
1120:                 Math.unsafeDivRoundingUp(
1121:                     uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
1122:                     DECIMALS
1123:                 )
1124:             );

```

*GitHub* : [1096-1126](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1096-L1126)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) performs unsafe type conversion from `uint` to `int`
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180) convert uint24 to int24).
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180) convert uint24 to int24).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).
	- lastObservedTick = int24((tickCumulative_last - tickCumulative_old) / int256(timestamp_last - timestamp_old)) (contracts/libraries/PanopticMath.sol#194-197) convert uint256 to int256).
	- entry = int24(uint24(medianData >> (rank * 24))) (contracts/libraries/PanopticMath.sol#217) convert uint24 to int24).

/// @audit ************** Possible Issue Line(s) **************
	L#177-180,  L#186-190,  L#194-197,  L#217,  

/// @audit ****************** Affected Code *******************
 177:             medianTick =
 178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
 179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
 180:                 2;
 186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(
 187:                         uint256(
 188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)
 189:                         ) % observationCardinality
 190:                     );
 194:                     lastObservedTick = int24(
 195:                         (tickCumulative_last - tickCumulative_old) /
 196:                             int256(timestamp_last - timestamp_old)
 197:                     );
 217:                     entry = int24(uint24(medianData >> (rank * 24)));

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker) (contracts/libraries/PanopticMath.sol#917-966) performs unsafe type conversion from `uint` to `int`
	- balanceShortage = refundValues.rightSlot() - int256(collateral0.convertToAssets(collateral0.balanceOf(refunder))) (contracts/libraries/PanopticMath.sol#928-929) convert uint256 to int256).
	- LeftRightSigned.wrap(0).toRightSlot(int128(refundValues.rightSlot() - balanceShortage)).toLeftSlot(int128(int256(PanopticMath.convert0to1(uint256(balanceShortage),sqrtPriceX96)) + refundValues.leftSlot())) (contracts/libraries/PanopticMath.sol#932-942) convert uint256 to int256).
	- balanceShortage = refundValues.leftSlot() - int256(collateral1.convertToAssets(collateral1.balanceOf(refunder))) (contracts/libraries/PanopticMath.sol#945-947) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#928-929,  L#932-942,  L#945-947,  

/// @audit ****************** Affected Code *******************
 928:             int256 balanceShortage = refundValues.rightSlot() -
 929:                 int256(collateral0.convertToAssets(collateral0.balanceOf(refunder)));
 932:                 return
 933:                     LeftRightSigned
 934:                         .wrap(0)
 935:                         .toRightSlot(int128(refundValues.rightSlot() - balanceShortage))
 936:                         .toLeftSlot(
 937:                             int128(
 938:                                 int256(
 939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
 940:                                 ) + refundValues.leftSlot()
 941:                             )
 942:                         );
 945:             balanceShortage =
 946:                 refundValues.leftSlot() -
 947:                 int256(collateral1.convertToAssets(collateral1.balanceOf(refunder)));

```

*GitHub* : [917-966](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L917-L966)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.toInt256(uint256) (contracts/libraries/Math.sol#325-328) performs unsafe type conversion from `uint` to `int`
	- int256(toCast) (contracts/libraries/Math.sol#327) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#327,  

/// @audit ****************** Affected Code *******************
 325:     function toInt256(uint256 toCast) internal pure returns (int256) {
 326:         if (toCast > uint256(type(int256).max)) revert Errors.CastingError();
 327:         return int256(toCast);
 328:     }

```

*GitHub* : [325-328](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L325-L328)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) performs unsafe type conversion from `uint` to `int`
	- s_collateralToken0.revoke(msg.sender,liquidatee,uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)) (contracts/PanopticPool.sol#1141-1145) convert uint256 to int256).
	- s_collateralToken1.revoke(msg.sender,liquidatee,uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)) (contracts/PanopticPool.sol#1146-1150) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1141-1145,  L#1146-1150,  

/// @audit ****************** Affected Code *******************
1141:         s_collateralToken0.revoke(
1142:             msg.sender,
1143:             liquidatee,
1144:             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)
1145:         );
1146:         s_collateralToken1.revoke(
1147:             msg.sender,
1148:             liquidatee,
1149:             uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)
1150:         );

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.takeCommissionAddData(address,int128,int128,int128) (contracts/CollateralTracker.sol#995-1033) performs unsafe type conversion from `uint` to `int`
	- updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount (contracts/CollateralTracker.sol#1003) convert uint256 to int256).
	- s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount))) (contracts/CollateralTracker.sol#1029) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1003,  L#1029,  

/// @audit ****************** Affected Code *******************
1003:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

```

*GitHub* : [995-1033](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L995-L1033)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.tickLower(LiquidityChunk) (contracts/types/LiquidityChunk.sol#171-175) performs unsafe type conversion from `uint` to `int`
	- int24(int256(LiquidityChunk.unwrap(self) >> 232)) (contracts/types/LiquidityChunk.sol#173) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#173,  

/// @audit ****************** Affected Code *******************
 171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {
 172:         unchecked {
 173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));
 174:         }
 175:     }

```

*GitHub* : [171-175](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L171-L175)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) performs unsafe type conversion from `uint` to `int`
	- value0 += int256(amount0) (contracts/libraries/FeesCalc.sol#69) convert uint256 to int256).
	- value1 += int256(amount1) (contracts/libraries/FeesCalc.sol#70) convert uint256 to int256).
	- value0 -= int256(amount0) (contracts/libraries/FeesCalc.sol#74) convert uint256 to int256).
	- value1 -= int256(amount1) (contracts/libraries/FeesCalc.sol#75) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#69,  L#70,  L#74,  L#75,  

/// @audit ****************** Affected Code *******************
  69:                         value0 += int256(amount0);
  70:                         value1 += int256(amount1);
  74:                         value0 -= int256(amount0);
  75:                         value1 -= int256(amount1);

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) performs unsafe type conversion from `uint` to `int`
	- (timestamps[i],tickCumulatives[i],None,None) = univ3pool.observations(uint256((int256(observationIndex) - int256(i * period)) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#138-143) convert uint256 to int256).
	- (timestamps[i],tickCumulatives[i],None,None) = univ3pool.observations(uint256((int256(observationIndex) - int256(i * period)) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#138-143) convert uint256 to int256).
	- (timestamps[i],tickCumulatives[i],None,None) = univ3pool.observations(uint256((int256(observationIndex) - int256(i * period)) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#138-143) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#138-143,  

/// @audit ****************** Affected Code *******************
 138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
 139:                     uint256(
 140:                         (int256(observationIndex) - int256(i * period)) +
 141:                             int256(observationCardinality)
 142:                     ) % observationCardinality
 143:                 );

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1311-1422) performs unsafe type conversion from `uint` to `int`
	- utilization = int64(uint64(poolUtilization)) (contracts/CollateralTracker.sol#1328-1330) convert uint64 to int64).

/// @audit ************** Possible Issue Line(s) **************
	L#1328-1330,  

/// @audit ****************** Affected Code *******************
1328:         int64 utilization = tokenType == 0
1329:             ? int64(uint64(poolUtilization))
1330:             : int64(uint64(poolUtilization >> 64));

```

*GitHub* : [1311-1422](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1311-L1422)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) performs unsafe type conversion from `uint` to `int`
	- s_collateralToken0.revoke(msg.sender,liquidatee,uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)) (contracts/PanopticPool.sol#1141-1145) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1141-1145,  

/// @audit ****************** Affected Code *******************
1141:         s_collateralToken0.revoke(
1142:             msg.sender,
1143:             liquidatee,
1144:             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)
1145:         );

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) performs unsafe type conversion from `uint` to `int`
	- settledTokens = LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(settledTokens))).sub(legPremia)))) (contracts/PanopticPool.sol#1866-1874) convert uint256 to int256).
	- realizedPremia = realizedPremia.add(LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))) (contracts/PanopticPool.sol#1900-1902) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1866-1874,  L#1900-1902,  

/// @audit ****************** Affected Code *******************
1866:                         settledTokens = LeftRightUnsigned.wrap(
1867:                             uint256(
1868:                                 LeftRightSigned.unwrap(
1869:                                     LeftRightSigned
1870:                                         .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1871:                                         .sub(legPremia)
1872:                                 )
1873:                             )
1874:                         );
1900:                     realizedPremia = realizedPremia.add(
1901:                         LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1902:                     );

```

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned) (contracts/libraries/PanopticMath.sol#651-754) performs unsafe type conversion from `uint` to `int`
	- bonus0 = int256(Math.mulDiv128(bonusCross,requiredRatioX128)) (contracts/libraries/PanopticMath.sol#681) convert uint256 to int256).
	- bonus1 = int256(PanopticMath.convert0to1(Math.mulDiv128(bonusCross,2 ** 128 - requiredRatioX128),sqrtPriceX96Final)) (contracts/libraries/PanopticMath.sol#683-688) convert uint256 to int256).
	- balance0 = int256(uint256(tokenData0.rightSlot())) - Math.max(premia.rightSlot(),0) (contracts/libraries/PanopticMath.sol#693-694) convert uint256 to int256).
	- balance1 = int256(uint256(tokenData1.rightSlot())) - Math.max(premia.leftSlot(),0) (contracts/libraries/PanopticMath.sol#695-696) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#681,  L#683-688,  L#693-694,  L#695-696,  

/// @audit ****************** Affected Code *******************
 681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));
 683:                 bonus1 = int256(
 684:                     PanopticMath.convert0to1(
 685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
 686:                         sqrtPriceX96Final
 687:                     )
 688:                 );
 693:             int256 balance0 = int256(uint256(tokenData0.rightSlot())) -
 694:                 Math.max(premia.rightSlot(), 0);
 695:             int256 balance1 = int256(uint256(tokenData1.rightSlot())) -
 696:                 Math.max(premia.leftSlot(), 0);

```

*GitHub* : [651-754](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L651-L754)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.twapFilter(IUniswapV3Pool,uint32) (contracts/libraries/PanopticMath.sol#241-268) performs unsafe type conversion from `uint` to `int`
	- twapMeasurement[i_scope_0] = int24((tickCumulatives[i_scope_0] - tickCumulatives[i_scope_0 + 1]) / int56(uint56(twapWindow / 20))) (contracts/libraries/PanopticMath.sol#257-259) convert uint56 to int56).

/// @audit ************** Possible Issue Line(s) **************
	L#257-259,  

/// @audit ****************** Affected Code *******************
 257:                 twapMeasurement[i] = int24(
 258:                     (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
 259:                 );

```

*GitHub* : [241-268](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L241-L268)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned) (contracts/CollateralTracker.sol#650-734) performs unsafe type conversion from `uint` to `int`
	- range = int24(int256(Math.unsafeDivRoundingUp(uint24(positionId.width(leg) * positionId.tickSpacing()),2))) (contracts/CollateralTracker.sol#667-674) convert uint256 to int256).
	- exerciseFees = exerciseFees.sub(LeftRightSigned.wrap(0).toRightSlot(int128(uint128(oracleValue0)) - int128(uint128(currentValue0))).toLeftSlot(int128(uint128(oracleValue1)) - int128(uint128(currentValue1)))) (contracts/CollateralTracker.sol#711-720) convert uint128 to int128).

/// @audit ************** Possible Issue Line(s) **************
	L#667-674,  L#711-720,  

/// @audit ****************** Affected Code *******************
 667:                     int24 range = int24(
 668:                         int256(
 669:                             Math.unsafeDivRoundingUp(
 670:                                 uint24(positionId.width(leg) * positionId.tickSpacing()),
 671:                                 2
 672:                             )
 673:                         )
 674:                     );
 711:                     exerciseFees = exerciseFees.sub(
 712:                         LeftRightSigned
 713:                             .wrap(0)
 714:                             .toRightSlot(
 715:                                 int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
 716:                             )
 717:                             .toLeftSlot(
 718:                                 int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
 719:                             )
 720:                     );

```

*GitHub* : [650-734](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L650-L734)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) performs unsafe type conversion from `uint` to `int`
	- settledTokens = LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(settledTokens))).sub(legPremia)))) (contracts/PanopticPool.sol#1866-1874) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1866-1874,  

/// @audit ****************** Affected Code *******************
1866:                         settledTokens = LeftRightUnsigned.wrap(
1867:                             uint256(
1868:                                 LeftRightSigned.unwrap(
1869:                                     LeftRightSigned
1870:                                         .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1871:                                         .sub(legPremia)
1872:                                 )
1873:                             )
1874:                         );

```

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.constructor(uint256,uint256,uint256,int256,uint256,uint256,uint256) (contracts/CollateralTracker.sol#178-211) performs unsafe type conversion from `uint` to `int`
	- ratioTick = (int256(_sellerCollateralRatio) - 2000) (contracts/CollateralTracker.sol#200) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#200,  

/// @audit ****************** Affected Code *******************
 200:             int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);

```

*GitHub* : [178-211](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L178-L211)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) performs unsafe type conversion from `uint` to `int`
	- value0 += int256(amount0) (contracts/libraries/FeesCalc.sol#69) convert uint256 to int256).
	- value1 += int256(amount1) (contracts/libraries/FeesCalc.sol#70) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#69,  L#70,  

/// @audit ****************** Affected Code *******************
  69:                         value0 += int256(amount0);
  70:                         value1 += int256(amount1);

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.strike(TokenId,uint256) (contracts/types/TokenId.sol#158-162) performs unsafe type conversion from `uint` to `int`
	- int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12))) (contracts/types/TokenId.sol#160) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#160,  

/// @audit ****************** Affected Code *******************
 158:     function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {
 159:         unchecked {
 160:             return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));
 161:         }
 162:     }

```

*GitHub* : [158-162](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L158-L162)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128) (contracts/CollateralTracker.sol#1510-1589) performs unsafe type conversion from `uint` to `int`
	- spreadRequirement = Math.max(spreadRequirement,_getRequiredCollateralAtUtilization(movedRight,1,int64(uint64(poolUtilization)))) (contracts/CollateralTracker.sol#1579-1588) convert uint64 to int64).
	- spreadRequirement = Math.max(spreadRequirement,_getRequiredCollateralAtUtilization(movedLeft,1,int64(uint64(poolUtilization >> 64)))) (contracts/CollateralTracker.sol#1579-1588) convert uint64 to int64).

/// @audit ************** Possible Issue Line(s) **************
	L#1579-1588,  

/// @audit ****************** Affected Code *******************
1579:         spreadRequirement = Math.max(
1580:             spreadRequirement,
1581:             _getRequiredCollateralAtUtilization(
1582:                 tokenType == 0 ? movedRight : movedLeft,
1583:                 1,
1584:                 tokenType == 0
1585:                     ? int64(uint64(poolUtilization))
1586:                     : int64(uint64(poolUtilization >> 64))
1587:             )
1588:         );

```

*GitHub* : [1510-1589](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1510-L1589)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned) (contracts/libraries/PanopticMath.sol#651-754) performs unsafe type conversion from `uint` to `int`
	- bonus0 = int256(Math.mulDiv128(bonusCross,requiredRatioX128)) (contracts/libraries/PanopticMath.sol#681) convert uint256 to int256).
	- bonus1 = int256(PanopticMath.convert0to1(Math.mulDiv128(bonusCross,2 ** 128 - requiredRatioX128),sqrtPriceX96Final)) (contracts/libraries/PanopticMath.sol#683-688) convert uint256 to int256).
	- balance0 = int256(uint256(tokenData0.rightSlot())) - Math.max(premia.rightSlot(),0) (contracts/libraries/PanopticMath.sol#693-694) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#681,  L#683-688,  L#693-694,  

/// @audit ****************** Affected Code *******************
 681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));
 683:                 bonus1 = int256(
 684:                     PanopticMath.convert0to1(
 685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
 686:                         sqrtPriceX96Final
 687:                     )
 688:                 );
 693:             int256 balance0 = int256(uint256(tokenData0.rightSlot())) -
 694:                 Math.max(premia.rightSlot(), 0);

```

*GitHub* : [651-754](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L651-L754)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned) (contracts/libraries/PanopticMath.sol#651-754) performs unsafe type conversion from `uint` to `int`
	- bonus0 = int256(Math.mulDiv128(bonusCross,requiredRatioX128)) (contracts/libraries/PanopticMath.sol#681) convert uint256 to int256).
	- bonus1 = int256(PanopticMath.convert0to1(Math.mulDiv128(bonusCross,2 ** 128 - requiredRatioX128),sqrtPriceX96Final)) (contracts/libraries/PanopticMath.sol#683-688) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#681,  L#683-688,  

/// @audit ****************** Affected Code *******************
 681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));
 683:                 bonus1 = int256(
 684:                     PanopticMath.convert0to1(
 685:                         Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
 686:                         sqrtPriceX96Final
 687:                     )
 688:                 );

```

*GitHub* : [651-754](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L651-L754)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidationBonus(LeftRightUnsigned,LeftRightUnsigned,uint160,uint160,LeftRightSigned,LeftRightSigned) (contracts/libraries/PanopticMath.sol#651-754) performs unsafe type conversion from `uint` to `int`
	- bonus0 = int256(Math.mulDiv128(bonusCross,requiredRatioX128)) (contracts/libraries/PanopticMath.sol#681) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#681,  

/// @audit ****************** Affected Code *******************
 681:                 bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));

```

*GitHub* : [651-754](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L651-L754)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) performs unsafe type conversion from `uint` to `int`
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180) convert uint24 to int24).
	- medianTick = (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) + int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) / 2 (contracts/libraries/PanopticMath.sol#177-180) convert uint24 to int24).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190) convert uint256 to int256).
	- lastObservedTick = int24((tickCumulative_last - tickCumulative_old) / int256(timestamp_last - timestamp_old)) (contracts/libraries/PanopticMath.sol#194-197) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#177-180,  L#186-190,  L#194-197,  

/// @audit ****************** Affected Code *******************
 177:             medianTick =
 178:                 (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
 179:                     int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
 180:                 2;
 186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(
 187:                         uint256(
 188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)
 189:                         ) % observationCardinality
 190:                     );
 194:                     lastObservedTick = int24(
 195:                         (tickCumulative_last - tickCumulative_old) /
 196:                             int256(timestamp_last - timestamp_old)
 197:                     );

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) performs unsafe type conversion from `uint` to `int`
	- (timestamps[i],tickCumulatives[i],None,None) = univ3pool.observations(uint256((int256(observationIndex) - int256(i * period)) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#138-143) convert uint256 to int256).
	- (timestamps[i],tickCumulatives[i],None,None) = univ3pool.observations(uint256((int256(observationIndex) - int256(i * period)) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#138-143) convert uint256 to int256).
	- (timestamps[i],tickCumulatives[i],None,None) = univ3pool.observations(uint256((int256(observationIndex) - int256(i * period)) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#138-143) convert uint256 to int256).
	- ticks[i_scope_0] = (tickCumulatives[i_scope_0] - tickCumulatives[i_scope_0 + 1]) / int256(timestamps[i_scope_0] - timestamps[i_scope_0 + 1]) (contracts/libraries/PanopticMath.sol#149-151) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#138-143,  L#149-151,  

/// @audit ****************** Affected Code *******************
 138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
 139:                     uint256(
 140:                         (int256(observationIndex) - int256(i * period)) +
 141:                             int256(observationCardinality)
 142:                     ) % observationCardinality
 143:                 );
 149:                 ticks[i] =
 150:                     (tickCumulatives[i] - tickCumulatives[i + 1]) /
 151:                     int256(timestamps[i] - timestamps[i + 1]);

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) performs unsafe type conversion from `uint` to `int`
	- value0 += int256(amount0) (contracts/libraries/FeesCalc.sol#69) convert uint256 to int256).
	- value1 += int256(amount1) (contracts/libraries/FeesCalc.sol#70) convert uint256 to int256).
	- value0 -= int256(amount0) (contracts/libraries/FeesCalc.sol#74) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#69,  L#70,  L#74,  

/// @audit ****************** Affected Code *******************
  69:                         value0 += int256(amount0);
  70:                         value1 += int256(amount1);
  74:                         value0 -= int256(amount0);

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.revoke(address,address,uint256) (contracts/CollateralTracker.sol#911-967) performs unsafe type conversion from `uint` to `int`
	- _mint(delegator,Math.mulDiv(assets,totalSupply - delegateeBalance,uint256(Math.max(1,int256(totalAssets()) - int256(assets)))) - delegateeBalance) (contracts/CollateralTracker.sol#954-961) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#954-961,  

/// @audit ****************** Affected Code *******************
 954:             _mint(
 955:                 delegator,
 956:                 Math.mulDiv(
 957:                     assets,
 958:                     totalSupply - delegateeBalance,
 959:                     uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
 960:                 ) - delegateeBalance
 961:             );

```

*GitHub* : [911-967](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L911-L967)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.width(TokenId,uint256) (contracts/types/TokenId.sol#169-173) performs unsafe type conversion from `uint` to `int`
	- int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096)) (contracts/types/TokenId.sol#171) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#171,  

/// @audit ****************** Affected Code *******************
 169:     function width(TokenId self, uint256 legIndex) internal pure returns (int24) {
 170:         unchecked {
 171:             return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));
 172:         } // "% 4096" = take last (2 ** 12 = 4096) 12 bits
 173:     }

```

*GitHub* : [169-173](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L169-L173)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getExchangedAmount(int128,int128,int128) (contracts/CollateralTracker.sol#1096-1126) performs unsafe type conversion from `uint` to `int`
	- exchangedAmount = intrinsicValue + int256(swapCommission) (contracts/CollateralTracker.sol#1115) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1115,  

/// @audit ****************** Affected Code *******************
1115:                 exchangedAmount = intrinsicValue + int256(swapCommission);

```

*GitHub* : [1096-1126](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1096-L1126)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.takeCommissionAddData(address,int128,int128,int128) (contracts/CollateralTracker.sol#995-1033) performs unsafe type conversion from `uint` to `int`
	- updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount (contracts/CollateralTracker.sol#1003) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#1003,  

/// @audit ****************** Affected Code *******************
1003:             int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

```

*GitHub* : [995-1033](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L995-L1033)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker) (contracts/libraries/PanopticMath.sol#917-966) performs unsafe type conversion from `uint` to `int`
	- balanceShortage = refundValues.rightSlot() - int256(collateral0.convertToAssets(collateral0.balanceOf(refunder))) (contracts/libraries/PanopticMath.sol#928-929) convert uint256 to int256).
	- LeftRightSigned.wrap(0).toRightSlot(int128(refundValues.rightSlot() - balanceShortage)).toLeftSlot(int128(int256(PanopticMath.convert0to1(uint256(balanceShortage),sqrtPriceX96)) + refundValues.leftSlot())) (contracts/libraries/PanopticMath.sol#932-942) convert uint256 to int256).
	- balanceShortage = refundValues.leftSlot() - int256(collateral1.convertToAssets(collateral1.balanceOf(refunder))) (contracts/libraries/PanopticMath.sol#945-947) convert uint256 to int256).
	- LeftRightSigned.wrap(0).toLeftSlot(int128(refundValues.leftSlot() - balanceShortage)).toRightSlot(int128(int256(PanopticMath.convert1to0(uint256(balanceShortage),sqrtPriceX96)) + refundValues.rightSlot())) (contracts/libraries/PanopticMath.sol#950-960) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#928-929,  L#932-942,  L#945-947,  L#950-960,  

/// @audit ****************** Affected Code *******************
 928:             int256 balanceShortage = refundValues.rightSlot() -
 929:                 int256(collateral0.convertToAssets(collateral0.balanceOf(refunder)));
 932:                 return
 933:                     LeftRightSigned
 934:                         .wrap(0)
 935:                         .toRightSlot(int128(refundValues.rightSlot() - balanceShortage))
 936:                         .toLeftSlot(
 937:                             int128(
 938:                                 int256(
 939:                                     PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
 940:                                 ) + refundValues.leftSlot()
 941:                             )
 942:                         );
 945:             balanceShortage =
 946:                 refundValues.leftSlot() -
 947:                 int256(collateral1.convertToAssets(collateral1.balanceOf(refunder)));
 950:                 return
 951:                     LeftRightSigned
 952:                         .wrap(0)
 953:                         .toLeftSlot(int128(refundValues.leftSlot() - balanceShortage))
 954:                         .toRightSlot(
 955:                             int128(
 956:                                 int256(
 957:                                     PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
 958:                                 ) + refundValues.rightSlot()
 959:                             )
 960:                         );

```

*GitHub* : [917-966](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L917-L966)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned) (contracts/types/LeftRight.sol#194-208) performs unsafe type conversion from `uint` to `int`
	- left = int256(uint256(x.leftSlot())) + y.leftSlot() (contracts/types/LeftRight.sol#196) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#196,  

/// @audit ****************** Affected Code *******************
 194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 195:         unchecked {
 196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();
 197:             int128 left128 = int128(left);
 198: 
 199:             if (left128 != left) revert Errors.UnderOverFlow();
 200: 
 201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();
 202:             int128 right128 = int128(right);
 203: 
 204:             if (right128 != right) revert Errors.UnderOverFlow();
 205: 
 206:             return z.toRightSlot(right128).toLeftSlot(left128);
 207:         }
 208:     }

```

*GitHub* : [194-208](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L194-L208)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.tickUpper(LiquidityChunk) (contracts/types/LiquidityChunk.sol#180-184) performs unsafe type conversion from `uint` to `int`
	- int24(int256(LiquidityChunk.unwrap(self) >> 208)) (contracts/types/LiquidityChunk.sol#182) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#182,  

/// @audit ****************** Affected Code *******************
 180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {
 181:         unchecked {
 182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));
 183:         }
 184:     }

```

*GitHub* : [180-184](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L180-L184)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned) (contracts/types/LeftRight.sol#194-208) performs unsafe type conversion from `uint` to `int`
	- left = int256(uint256(x.leftSlot())) + y.leftSlot() (contracts/types/LeftRight.sol#196) convert uint256 to int256).
	- right = int256(uint256(x.rightSlot())) + y.rightSlot() (contracts/types/LeftRight.sol#201) convert uint256 to int256).

/// @audit ************** Possible Issue Line(s) **************
	L#196,  L#201,  

/// @audit ****************** Affected Code *******************
 194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 195:         unchecked {
 196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();
 197:             int128 left128 = int128(left);
 198: 
 199:             if (left128 != left) revert Errors.UnderOverFlow();
 200: 
 201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();
 202:             int128 right128 = int128(right);
 203: 
 204:             if (right128 != right) revert Errors.UnderOverFlow();
 205: 
 206:             return z.toRightSlot(right128).toLeftSlot(left128);
 207:         }
 208:     }

```

*GitHub* : [194-208](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L194-L208)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.toInt128(uint128) (contracts/libraries/Math.sol#311-313) performs unsafe type conversion from `uint` to `int`
	- (downcastedInt = int128(toCast)) < 0 (contracts/libraries/Math.sol#312) convert uint128 to int128).

/// @audit ************** Possible Issue Line(s) **************
	L#312,  

/// @audit ****************** Affected Code *******************
 311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {
 312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();
 313:     }

```

*GitHub* : [311-313](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L311-L313)

### [L-12]<a name="l-12"></a> Complex Computation - Multiplication on result of a Division

Division often result in a loss of precision because it discards the fractional part. When the outcome of such a division is subsequently multiplied in a complex computation, this loss of precision can become more pronounced, possibly resulting in considerable inaccuracies in the computations and potentional loss of funds/ rewards.  **Recom:** Consider re-ordering multiplication before division.

*There are 31 instance(s) of this issue:*

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128 (contracts/libraries/Math.sol#169)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#169,  L#176,  

/// @audit ****************** Affected Code *******************
 169:             if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128 (contracts/libraries/Math.sol#151)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#151,  L#176,  

/// @audit ****************** Affected Code *******************
 151:             if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) performs a multiplication on the result of a division:
	- denominator = denominator / twos (contracts/libraries/Math.sol#394)
	- inv *= 2 - denominator * inv (contracts/libraries/Math.sol#422)

/// @audit ************** Possible Issue Line(s) **************
	L#394,  L#422,  

/// @audit ****************** Affected Code *******************
 394:                 denominator := div(denominator, twos)
 422:             inv *= 2 - denominator * inv; // inverse mod 2**128

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) performs a multiplication on the result of a division:
	- denominator = denominator / twos (contracts/libraries/Math.sol#394)
	- inv *= 2 - denominator * inv (contracts/libraries/Math.sol#423)

/// @audit ************** Possible Issue Line(s) **************
	L#394,  L#423,  

/// @audit ****************** Affected Code *******************
 394:                 denominator := div(denominator, twos)
 423:             inv *= 2 - denominator * inv; // inverse mod 2**256

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128 (contracts/libraries/Math.sol#141)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#141,  L#176,  

/// @audit ****************** Affected Code *******************
 141:             if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128 (contracts/libraries/Math.sol#157)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#157,  L#176,  

/// @audit ****************** Affected Code *******************
 157:             if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) performs a multiplication on the result of a division:
	- denominator = denominator / twos (contracts/libraries/Math.sol#394)
	- inv *= 2 - denominator * inv (contracts/libraries/Math.sol#420)

/// @audit ************** Possible Issue Line(s) **************
	L#394,  L#420,  

/// @audit ****************** Affected Code *******************
 394:                 denominator := div(denominator, twos)
 420:             inv *= 2 - denominator * inv; // inverse mod 2**32

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128 (contracts/libraries/Math.sol#153)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#153,  L#176,  

/// @audit ****************** Affected Code *******************
 153:             if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) performs a multiplication on the result of a division:
	- denominator = denominator / twos (contracts/libraries/Math.sol#394)
	- inv *= 2 - denominator * inv (contracts/libraries/Math.sol#418)

/// @audit ************** Possible Issue Line(s) **************
	L#394,  L#418,  

/// @audit ****************** Affected Code *******************
 394:                 denominator := div(denominator, twos)
 418:             inv *= 2 - denominator * inv; // inverse mod 2**8

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128 (contracts/libraries/Math.sol#143)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#143,  L#176,  

/// @audit ****************** Affected Code *******************
 143:             if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24) (contracts/PanopticFactory.sol#335-411) performs a multiplication on the result of a division:
	- tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing (contracts/PanopticFactory.sol#392)

/// @audit ************** Possible Issue Line(s) **************
	L#392,  

/// @audit ****************** Affected Code *******************
 392:             tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```

*GitHub* : [335-411](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L335-L411)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128 (contracts/libraries/Math.sol#167)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#167,  L#176,  

/// @audit ****************** Affected Code *******************
 167:             if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128 (contracts/libraries/Math.sol#147)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#147,  L#176,  

/// @audit ****************** Affected Code *******************
 147:             if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) performs a multiplication on the result of a division:
	- denominator = denominator / twos (contracts/libraries/Math.sol#394)
	- inv = (3 * denominator) ^ 2 (contracts/libraries/Math.sol#414)

/// @audit ************** Possible Issue Line(s) **************
	L#394,  L#414,  

/// @audit ****************** Affected Code *******************
 394:                 denominator := div(denominator, twos)
 414:             uint256 inv = (3 * denominator) ^ 2;

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) performs a multiplication on the result of a division:
	- denominator = denominator / twos (contracts/libraries/Math.sol#394)
	- inv *= 2 - denominator * inv (contracts/libraries/Math.sol#419)

/// @audit ************** Possible Issue Line(s) **************
	L#394,  L#419,  

/// @audit ****************** Affected Code *******************
 394:                 denominator := div(denominator, twos)
 419:             inv *= 2 - denominator * inv; // inverse mod 2**16

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128 (contracts/libraries/Math.sol#155)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#155,  L#176,  

/// @audit ****************** Affected Code *******************
 155:             if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getTicks(int24,int24,int24) (contracts/libraries/PanopticMath.sol#338-363) performs a multiplication on the result of a division:
	- maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing (contracts/libraries/PanopticMath.sol#347)

/// @audit ************** Possible Issue Line(s) **************
	L#347,  

/// @audit ****************** Affected Code *******************
 347:             int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;

```

*GitHub* : [338-363](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L338-L363)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getTicks(int24,int24,int24) (contracts/libraries/PanopticMath.sol#338-363) performs a multiplication on the result of a division:
	- minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing (contracts/libraries/PanopticMath.sol#346)

/// @audit ************** Possible Issue Line(s) **************
	L#346,  

/// @audit ****************** Affected Code *******************
 346:             int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;

```

*GitHub* : [338-363](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L338-L363)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128 (contracts/libraries/Math.sol#137)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#137,  L#176,  

/// @audit ****************** Affected Code *******************
 137:             if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128 (contracts/libraries/Math.sol#171)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#171,  L#176,  

/// @audit ****************** Affected Code *******************
 171:             if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) performs a multiplication on the result of a division:
	- prod0 = prod0 / twos (contracts/libraries/Math.sol#399)
	- result = prod0 * inv (contracts/libraries/Math.sol#431)

/// @audit ************** Possible Issue Line(s) **************
	L#399,  L#431,  

/// @audit ****************** Affected Code *******************
 399:                 prod0 := div(prod0, twos)
 431:             result = prod0 * inv;

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128 (contracts/libraries/Math.sol#173)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#173,  L#176,  

/// @audit ****************** Affected Code *******************
 173:             if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128 (contracts/libraries/Math.sol#149)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#149,  L#176,  

/// @audit ****************** Affected Code *******************
 149:             if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128 (contracts/libraries/Math.sol#161)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#161,  L#176,  

/// @audit ****************** Affected Code *******************
 161:             if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128 (contracts/libraries/Math.sol#159)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#159,  L#176,  

/// @audit ****************** Affected Code *******************
 159:             if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128 (contracts/libraries/Math.sol#165)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#165,  L#176,  

/// @audit ****************** Affected Code *******************
 165:             if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128 (contracts/libraries/Math.sol#139)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#139,  L#176,  

/// @audit ****************** Affected Code *******************
 139:             if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128 (contracts/libraries/Math.sol#163)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#163,  L#176,  

/// @audit ****************** Affected Code *******************
 163:             if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.startToken(bool,address,address,uint24,PanopticPool) (contracts/CollateralTracker.sol#221-264) performs a multiplication on the result of a division:
	- _poolFee = fee / 100 (contracts/CollateralTracker.sol#249)
	- s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS) (contracts/CollateralTracker.sol#262)

/// @audit ************** Possible Issue Line(s) **************
	L#249,  L#262,  

/// @audit ****************** Affected Code *******************
 249:             _poolFee = fee / 100;
 262:             s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);

```

*GitHub* : [221-264](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L221-L264)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) performs a multiplication on the result of a division:
	- sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128 (contracts/libraries/Math.sol#145)
	- sqrtR = type()(uint256).max / sqrtR (contracts/libraries/Math.sol#176)

/// @audit ************** Possible Issue Line(s) **************
	L#145,  L#176,  

/// @audit ****************** Affected Code *******************
 145:             if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;
 176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) performs a multiplication on the result of a division:
	- denominator = denominator / twos (contracts/libraries/Math.sol#394)
	- inv *= 2 - denominator * inv (contracts/libraries/Math.sol#421)

/// @audit ************** Possible Issue Line(s) **************
	L#394,  L#421,  

/// @audit ****************** Affected Code *******************
 394:                 denominator := div(denominator, twos)
 421:             inv *= 2 - denominator * inv; // inverse mod 2**64

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

### [L-13]<a name="l-13"></a> Dangerous strict equalities

Use of strict equalities that can be easily manipulated by an attacker.  **Recom:** Don't use strict equality and try using `>=` or `<=` to cover broader edge cases.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convertNotional(uint128,int24,int24,uint256) (contracts/libraries/PanopticMath.sol#468-483) uses a dangerous strict equality:
	- notional == 0 || notional > type()(uint128).max (contracts/libraries/PanopticMath.sol#479)

/// @audit ************** Possible Issue Line(s) **************
	L#479,  

/// @audit ****************** Affected Code *******************
 468:     function convertNotional(
 469:         uint128 contractSize,
 470:         int24 tickLower,
 471:         int24 tickUpper,
 472:         uint256 asset
 473:     ) internal pure returns (uint128) {
 474:         unchecked {
 475:             uint256 notional = asset == 0
 476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))
 477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));
 478: 
 479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();
 480: 
 481:             return uint128(notional);
 482:         }
 483:     }

```

*GitHub* : [468-483](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L468-L483)

### [L-14]<a name="l-14"></a> Missing events arithmetic

Changes in critical arithmetic parameters should be emitted for tracking by other tools.  **Recom:** Emit an event for critical parameter changes.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exercise(address,int128,int128,int128,int128) (contracts/CollateralTracker.sol#1043-1089) should emit an event for: 
	- s_poolAssets = uint128(uint256(updatedAssets + realizedPremium)) (contracts/CollateralTracker.sol#1084) 
	- s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount))) (contracts/CollateralTracker.sol#1085) 

/// @audit ************** Possible Issue Line(s) **************
	L#1084,  L#1085,  

/// @audit ****************** Affected Code *******************
1084:             s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));
1085:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

```

*GitHub* : [1043-1089](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1043-L1089)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.takeCommissionAddData(address,int128,int128,int128) (contracts/CollateralTracker.sol#995-1033) should emit an event for: 
	- s_poolAssets = uint128(uint256(updatedAssets)) (contracts/CollateralTracker.sol#1028) 
	- s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount))) (contracts/CollateralTracker.sol#1029) 

/// @audit ************** Possible Issue Line(s) **************
	L#1028,  L#1029,  

/// @audit ****************** Affected Code *******************
1028:             s_poolAssets = uint128(uint256(updatedAssets));
1029:             s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

```

*GitHub* : [995-1033](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L995-L1033)

### [L-15]<a name="l-15"></a> Missing zero address validation

`address` should be validated for zero value before assigning to a storage variable.  **Recom:** Check that the address is not zero.

*There are 7 instance(s) of this issue:*

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.transferOwnership(address).newOwner (contracts/PanopticFactory.sol#147) lacks a zero-check on :
	- s_owner = newOwner (contracts/PanopticFactory.sol#152)

/// @audit ************** Possible Issue Line(s) **************
	L#147,  L#152,  

/// @audit ****************** Affected Code *******************
 147:     function transferOwnership(address newOwner) external {
 152:         s_owner = newOwner;

```

*GitHub* : [147-147](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L147-L147)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.initialize(address)._owner (contracts/PanopticFactory.sol#134) lacks a zero-check on :
	- s_owner = _owner (contracts/PanopticFactory.sol#136)

/// @audit ************** Possible Issue Line(s) **************
	L#134,  L#136,  

/// @audit ****************** Affected Code *******************
 134:     function initialize(address _owner) public {
 136:             s_owner = _owner;

```

*GitHub* : [134-134](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L134-L134)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.startToken(bool,address,address,uint24,PanopticPool).token0 (contracts/CollateralTracker.sol#223) lacks a zero-check on :
	- s_univ3token0 = token0 (contracts/CollateralTracker.sol#254)
	- s_underlyingToken = token0 (contracts/CollateralTracker.sol#241)

/// @audit ************** Possible Issue Line(s) **************
	L#223,  L#254,  L#241,  

/// @audit ****************** Affected Code *******************
 223:         address token0,
 241:         s_underlyingToken = underlyingIsToken0 ? token0 : token1;
 254:         s_univ3token0 = token0;

```

*GitHub* : [223-223](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L223-L223)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._WETH9 (contracts/PanopticFactory.sol#116) lacks a zero-check on :
	- WETH = _WETH9 (contracts/PanopticFactory.sol#123)

/// @audit ************** Possible Issue Line(s) **************
	L#116,  L#123,  

/// @audit ****************** Affected Code *******************
 116:         address _WETH9,
 123:         WETH = _WETH9;

```

*GitHub* : [116-116](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L116-L116)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.startToken(bool,address,address,uint24,PanopticPool).token1 (contracts/CollateralTracker.sol#224) lacks a zero-check on :
	- s_univ3token1 = token1 (contracts/CollateralTracker.sol#255)
	- s_underlyingToken = token1 (contracts/CollateralTracker.sol#241)

/// @audit ************** Possible Issue Line(s) **************
	L#224,  L#255,  L#241,  

/// @audit ****************** Affected Code *******************
 224:         address token1,
 241:         s_underlyingToken = underlyingIsToken0 ? token0 : token1;
 255:         s_univ3token1 = token1;

```

*GitHub* : [224-224](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L224-L224)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._poolReference (contracts/PanopticFactory.sol#120) lacks a zero-check on :
	- POOL_REFERENCE = _poolReference (contracts/PanopticFactory.sol#128)

/// @audit ************** Possible Issue Line(s) **************
	L#120,  L#128,  

/// @audit ****************** Affected Code *******************
 120:         address _poolReference,
 128:         POOL_REFERENCE = _poolReference;

```

*GitHub* : [120-120](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L120-L120)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._collateralReference (contracts/PanopticFactory.sol#121) lacks a zero-check on :
	- COLLATERAL_REFERENCE = _collateralReference (contracts/PanopticFactory.sol#129)

/// @audit ************** Possible Issue Line(s) **************
	L#121,  L#129,  

/// @audit ****************** Affected Code *******************
 121:         address _collateralReference
 129:         COLLATERAL_REFERENCE = _collateralReference;

```

*GitHub* : [121-121](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L121-L121)

### [L-16]<a name="l-16"></a> Contract's Name reused

If a codebase has two contracts the similar names, the compilation artifacts will not contain one of the contracts with the duplicate name.  **Recom:** Rename the contract.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math is re-used:
	- Math (contracts/libraries/Math.sol#13-782)
	- Math (lib/openzeppelin-contracts/contracts/utils/math/Math.sol#9-345)

/// @audit ****************** Affected Code *******************

```

*GitHub* : [13-782](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L13-L782)

### [L-17]<a name="l-17"></a> Benign reentrancy vulnerabilities

Possible benign reentrancy vulnerabilities (exploitation would have the same effect as two consecutive calls.)  **Recom:** Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

*There are 6 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in PanopticPool._burnAndHandleExercise(bool,int24,int24,TokenId,uint128,address) (contracts/PanopticPool.sol#955-1005):
	External calls:
	- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
	State variables written after the call(s):
	- (realizedPremia,premiaByLeg) = _updateSettlementPostBurn(owner,tokenId,collectedByLeg,positionSize,commitLongSettled) (contracts/PanopticPool.sol#973-979)
		- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(uint256(Math.max((int256(grossPremiumLast.rightSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][0] * positionLiquidity)) + int256(legPremia.rightSlot() * 2 ** 64),0)) / totalLiquidity)).toLeftSlot(uint128(uint256(Math.max((int256(grossPremiumLast.leftSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][1] * positionLiquidity)) + int256(legPremia.leftSlot()) * 2 ** 64,0)) / totalLiquidity)) (contracts/PanopticPool.sol#1928-1968)
		- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0])).toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1])) (contracts/PanopticPool.sol#1928-1968)
	- (realizedPremia,premiaByLeg) = _updateSettlementPostBurn(owner,tokenId,collectedByLeg,positionSize,commitLongSettled) (contracts/PanopticPool.sol#973-979)
		- s_settledTokens[chunkKey] = settledTokens (contracts/PanopticPool.sol#1974)

/// @audit ************** Possible Issue Line(s) **************
	L#970-971,  L#973-979,  L#1928-1968,  L#1974,  

/// @audit ****************** Affected Code *******************
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 973:         (realizedPremia, premiaByLeg) = _updateSettlementPostBurn(
 974:             owner,
 975:             tokenId,
 976:             collectedByLeg,
 977:             positionSize,
 978:             commitLongSettled
 979:         );
1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929:                             ? LeftRightUnsigned
1930:                                 .wrap(0)
1931:                                 .toRightSlot(
1932:                                     uint128(
1933:                                         uint256(
1934:                                             Math.max(
1935:                                                 (int256(
1936:                                                     grossPremiumLast.rightSlot() *
1937:                                                         totalLiquidityBefore
1938:                                                 ) -
1939:                                                     int256(
1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941:                                                             positionLiquidity
1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),
1943:                                                 0
1944:                                             )
1945:                                         ) / totalLiquidity
1946:                                     )
1947:                                 )
1948:                                 .toLeftSlot(
1949:                                     uint128(
1950:                                         uint256(
1951:                                             Math.max(
1952:                                                 (int256(
1953:                                                     grossPremiumLast.leftSlot() *
1954:                                                         totalLiquidityBefore
1955:                                                 ) -
1956:                                                     int256(
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958:                                                             positionLiquidity
1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960:                                                 0
1961:                                             )
1962:                                         ) / totalLiquidity
1963:                                     )
1964:                                 )
1965:                             : LeftRightUnsigned
1966:                                 .wrap(0)
1967:                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1974:             s_settledTokens[chunkKey] = settledTokens;

```

*GitHub* : [955-1005](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L955-L1005)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256) (contracts/SemiFungiblePositionManager.sol#1255-1313):
	External calls:
	- (receivedAmount0,receivedAmount1) = univ3pool.collect(msg.sender,liquidityChunk.tickLower(),liquidityChunk.tickUpper(),uint128(amountToCollect.rightSlot()),uint128(amountToCollect.leftSlot())) (contracts/SemiFungiblePositionManager.sol#1284-1290)
	State variables written after the call(s):
	- _updateStoredPremia(positionKey,currentLiquidity,collectedChunk) (contracts/SemiFungiblePositionManager.sol#1311)
		- (s_accountPremiumOwed[positionKey],s_accountPremiumGross[positionKey]) = LeftRightLibrary.addCapped(s_accountPremiumOwed[positionKey],deltaPremiumOwed,s_accountPremiumGross[positionKey],deltaPremiumGross) (contracts/SemiFungiblePositionManager.sol#1123-1129)
	- _updateStoredPremia(positionKey,currentLiquidity,collectedChunk) (contracts/SemiFungiblePositionManager.sol#1311)
		- (s_accountPremiumOwed[positionKey],s_accountPremiumGross[positionKey]) = LeftRightLibrary.addCapped(s_accountPremiumOwed[positionKey],deltaPremiumOwed,s_accountPremiumGross[positionKey],deltaPremiumGross) (contracts/SemiFungiblePositionManager.sol#1123-1129)

/// @audit ************** Possible Issue Line(s) **************
	L#1284-1290,  L#1311,  L#1123-1129,  

/// @audit ****************** Affected Code *******************
1123:         (s_accountPremiumOwed[positionKey], s_accountPremiumGross[positionKey]) = LeftRightLibrary
1124:             .addCapped(
1125:                 s_accountPremiumOwed[positionKey],
1126:                 deltaPremiumOwed,
1127:                 s_accountPremiumGross[positionKey],
1128:                 deltaPremiumGross
1129:             );
1284:             (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(
1285:                 msg.sender,
1286:                 liquidityChunk.tickLower(),
1287:                 liquidityChunk.tickUpper(),
1288:                 uint128(amountToCollect.rightSlot()),
1289:                 uint128(amountToCollect.leftSlot())
1290:             );
1311:             _updateStoredPremia(positionKey, currentLiquidity, collectedChunk);

```

*GitHub* : [1255-1313](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1255-L1313)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24) (contracts/PanopticPool.sol#614-667):
	External calls:
	- poolUtilizations = _mintInSFPMAndUpdateCollateral(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#642-647)
		- (collectedByLeg,totalSwapped) = SFPM.mintTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#685-686)
		- utilization0 = s_collateralToken0.takeCommissionAddData(msg.sender,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot()) (contracts/PanopticPool.sol#715-720)
		- utilization1 = s_collateralToken1.takeCommissionAddData(msg.sender,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot()) (contracts/PanopticPool.sol#721-726)
	State variables written after the call(s):
	- s_miniMedian = medianData (contracts/PanopticPool.sol#664)
	- _addUserOption(tokenId,effectiveLiquidityLimitX32) (contracts/PanopticPool.sol#650)
		- s_options[msg.sender][tokenId][leg] = LeftRightUnsigned.wrap(0).toRightSlot(premiumAccumulator0).toLeftSlot(premiumAccumulator1) (contracts/PanopticPool.sol#762-765)

/// @audit ************** Possible Issue Line(s) **************
	L#642-647,  L#685-686,  L#715-720,  L#721-726,  L#664,  L#650,  L#762-765,  

/// @audit ****************** Affected Code *******************
 642:         uint128 poolUtilizations = _mintInSFPMAndUpdateCollateral(
 643:             tokenId,
 644:             positionSize,
 645:             tickLimitLow,
 646:             tickLimitHigh
 647:         );
 650:         _addUserOption(tokenId, effectiveLiquidityLimitX32);
 664:         if (medianData != 0) s_miniMedian = medianData;
 685:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 686:             .mintTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 715:         int256 utilization0 = s_collateralToken0.takeCommissionAddData(
 716:             msg.sender,
 717:             longAmounts.rightSlot(),
 718:             shortAmounts.rightSlot(),
 719:             totalSwapped.rightSlot()
 720:         );
 721:         int256 utilization1 = s_collateralToken1.takeCommissionAddData(
 722:             msg.sender,
 723:             longAmounts.leftSlot(),
 724:             shortAmounts.leftSlot(),
 725:             totalSwapped.leftSlot()
 726:         );
 762:                 s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
 763:                     .wrap(0)
 764:                     .toRightSlot(premiumAccumulator0)
 765:                     .toLeftSlot(premiumAccumulator1);

```

*GitHub* : [614-667](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L614-L667)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in PanopticPool._burnOptions(bool,TokenId,address,int24,int24) (contracts/PanopticPool.sol#826-854):
	External calls:
	- (premiaOwed,premiaByLeg,paidAmounts) = _burnAndHandleExercise(commitLongSettled,tickLimitLow,tickLimitHigh,tokenId,positionSize,owner) (contracts/PanopticPool.sol#840-847)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	State variables written after the call(s):
	- _updatePositionDataBurn(owner,tokenId) (contracts/PanopticPool.sol#850)
		- s_positionsHash[account] = newHash (contracts/PanopticPool.sol#1416)

/// @audit ************** Possible Issue Line(s) **************
	L#840-847,  L#970-971,  L#985-991,  L#996-1002,  L#850,  L#1416,  

/// @audit ****************** Affected Code *******************
 840:         (premiaOwed, premiaByLeg, paidAmounts) = _burnAndHandleExercise(
 841:             commitLongSettled,
 842:             tickLimitLow,
 843:             tickLimitHigh,
 844:             tokenId,
 845:             positionSize,
 846:             owner
 847:         );
 850:         _updatePositionDataBurn(owner, tokenId);
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );
1416:         s_positionsHash[account] = newHash;

```

*GitHub* : [826-854](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L826-L854)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in PanopticPool._mintInSFPMAndUpdateCollateral(TokenId,uint128,int24,int24) (contracts/PanopticPool.sol#677-696):
	External calls:
	- (collectedByLeg,totalSwapped) = SFPM.mintTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#685-686)
	State variables written after the call(s):
	- _updateSettlementPostMint(tokenId,collectedByLeg,positionSize) (contracts/PanopticPool.sol#689)
		- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128((grossCurrent[0] * positionLiquidity + grossPremiumLast.rightSlot() * totalLiquidityBefore) / (totalLiquidity))).toLeftSlot(uint128((grossCurrent[1] * positionLiquidity + grossPremiumLast.leftSlot() * totalLiquidityBefore) / (totalLiquidity))) (contracts/PanopticPool.sol#1725-1742)
	- _updateSettlementPostMint(tokenId,collectedByLeg,positionSize) (contracts/PanopticPool.sol#689)
		- s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]) (contracts/PanopticPool.sol#1677)

/// @audit ************** Possible Issue Line(s) **************
	L#685-686,  L#689,  L#1725-1742,  L#1677,  

/// @audit ****************** Affected Code *******************
 677:     function _mintInSFPMAndUpdateCollateral(
 678:         TokenId tokenId,
 679:         uint128 positionSize,
 680:         int24 tickLimitLow,
 681:         int24 tickLimitHigh
 682:     ) internal returns (uint128) {
 683:         // Mint position by using the SFPM. totalSwapped will reflect tokens swapped because of minting ITM.
 684:         // Switch order of tickLimits to create "swapAtMint" flag
 685:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 686:             .mintTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 687: 
 688:         // update premium settlement info
 689:         _updateSettlementPostMint(tokenId, collectedByLeg, positionSize);
 690: 
 691:         // pay commission based on total moved amount (long + short)
 692:         // write data about inAMM in collateralBase
 693:         uint128 poolUtilizations = _payCommissionAndWriteData(tokenId, positionSize, totalSwapped);
 694: 
 695:         return poolUtilizations;
 696:     }
1677:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1725:                     s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1726:                         .wrap(0)
1727:                         .toRightSlot(
1728:                             uint128(
1729:                                 (grossCurrent[0] *
1730:                                     positionLiquidity +
1731:                                     grossPremiumLast.rightSlot() *
1732:                                     totalLiquidityBefore) / (totalLiquidity)
1733:                             )
1734:                         )
1735:                         .toLeftSlot(
1736:                             uint128(
1737:                                 (grossCurrent[1] *
1738:                                     positionLiquidity +
1739:                                     grossPremiumLast.leftSlot() *
1740:                                     totalLiquidityBefore) / (totalLiquidity)
1741:                             )
1742:                         );

```

*GitHub* : [677-696](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L677-L696)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (benign) in PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659):
	External calls:
	- s_collateralToken0.exercise(owner,0,0,0,realizedPremia.rightSlot()) (contracts/PanopticPool.sol#1639)
	- s_collateralToken1.exercise(owner,0,0,0,realizedPremia.leftSlot()) (contracts/PanopticPool.sol#1640)
	State variables written after the call(s):
	- s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))) (contracts/PanopticPool.sol#1650-1652)

/// @audit ************** Possible Issue Line(s) **************
	L#1639,  L#1640,  L#1650-1652,  

/// @audit ****************** Affected Code *******************
1639:             s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());
1640:             s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());
1650:             s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(
1651:                 LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))
1652:             );

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1659)

### [L-18]<a name="l-18"></a> Reentrancy vulnerabilities (events)

Possible Reentrancy vulnerabilities leading to out-of-order Events.  **Recom:**  Ensure that events follow the best practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), and are emitted before external calls.

*There are 9 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659):
	External calls:
	- s_collateralToken0.exercise(owner,0,0,0,realizedPremia.rightSlot()) (contracts/PanopticPool.sol#1639)
	- s_collateralToken1.exercise(owner,0,0,0,realizedPremia.leftSlot()) (contracts/PanopticPool.sol#1640)
	Event emitted after the call(s):
	- PremiumSettled(owner,tokenId,realizedPremia) (contracts/PanopticPool.sol#1654)

/// @audit ************** Possible Issue Line(s) **************
	L#1639,  L#1640,  L#1654,  

/// @audit ****************** Affected Code *******************
1639:             s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());
1640:             s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());
1654:             emit PremiumSettled(owner, tokenId, realizedPremia);

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171):
	External calls:
	- s_collateralToken0.delegate(msg.sender,liquidatee,delegations.rightSlot()) (contracts/PanopticPool.sol#1072)
	- s_collateralToken1.delegate(msg.sender,liquidatee,delegations.leftSlot()) (contracts/PanopticPool.sol#1073)
	- (netExchanged,premiasByLeg) = _burnAllOptionsFrom(liquidatee,Constants.MIN_V3POOL_TICK,Constants.MAX_V3POOL_TICK,DONOT_COMMIT_LONG_SETTLED,positionIdList) (contracts/PanopticPool.sol#1086-1092)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	- (deltaBonus0,deltaBonus1) = PanopticMath.haircutPremia(_liquidatee,_positionIdList,premiasByLeg,collateralRemaining,s_collateralToken0,s_collateralToken1,Math.getSqrtRatioAtTick(_finalTick),s_settledTokens) (contracts/PanopticPool.sol#1122-1131)
	- s_collateralToken0.revoke(msg.sender,liquidatee,uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)) (contracts/PanopticPool.sol#1141-1145)
	- s_collateralToken1.revoke(msg.sender,liquidatee,uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)) (contracts/PanopticPool.sol#1146-1150)
	Event emitted after the call(s):
	- AccountLiquidated(msg.sender,liquidatee,bonusAmounts) (contracts/PanopticPool.sol#1170)

/// @audit ************** Possible Issue Line(s) **************
	L#1072,  L#1073,  L#1086-1092,  L#970-971,  L#985-991,  L#996-1002,  L#1122-1131,  L#1141-1145,  L#1146-1150,  L#1170,  

/// @audit ****************** Affected Code *******************
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );
1072:         s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());
1073:         s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());
1086:             (netExchanged, premiasByLeg) = _burnAllOptionsFrom(
1087:                 liquidatee,
1088:                 Constants.MIN_V3POOL_TICK,
1089:                 Constants.MAX_V3POOL_TICK,
1090:                 DONOT_COMMIT_LONG_SETTLED,
1091:                 positionIdList
1092:             );
1122:             (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(
1123:                 _liquidatee,
1124:                 _positionIdList,
1125:                 premiasByLeg,
1126:                 collateralRemaining,
1127:                 s_collateralToken0,
1128:                 s_collateralToken1,
1129:                 Math.getSqrtRatioAtTick(_finalTick),
1130:                 s_settledTokens
1131:             );
1141:         s_collateralToken0.revoke(
1142:             msg.sender,
1143:             liquidatee,
1144:             uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)
1145:         );
1146:         s_collateralToken1.revoke(
1147:             msg.sender,
1148:             liquidatee,
1149:             uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)
1150:         );
1170:         emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278):
	External calls:
	- s_collateralToken0.delegate(account,uint128(delegatedAmounts.rightSlot())) (contracts/PanopticPool.sol#1222)
	- s_collateralToken1.delegate(account,uint128(delegatedAmounts.leftSlot())) (contracts/PanopticPool.sol#1223)
	- _burnAllOptionsFrom(account,0,0,COMMIT_LONG_SETTLED,touchedId) (contracts/PanopticPool.sol#1227)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	- s_collateralToken0.refund(account,msg.sender,refundAmounts.rightSlot() - delegatedAmounts.rightSlot()) (contracts/PanopticPool.sol#1252-1256)
	- s_collateralToken1.refund(account,msg.sender,refundAmounts.leftSlot() - delegatedAmounts.leftSlot()) (contracts/PanopticPool.sol#1257-1261)
	- s_collateralToken0.refund(account,uint128(delegatedAmounts.rightSlot())) (contracts/PanopticPool.sol#1265)
	- s_collateralToken1.refund(account,uint128(delegatedAmounts.leftSlot())) (contracts/PanopticPool.sol#1266)
	Event emitted after the call(s):
	- ForcedExercised(msg.sender,account,touchedId[0],exerciseFees) (contracts/PanopticPool.sol#1277)

/// @audit ************** Possible Issue Line(s) **************
	L#1222,  L#1223,  L#1227,  L#970-971,  L#985-991,  L#996-1002,  L#1252-1256,  L#1257-1261,  L#1265,  L#1266,  L#1277,  

/// @audit ****************** Affected Code *******************
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );
1222:         s_collateralToken0.delegate(account, uint128(delegatedAmounts.rightSlot()));
1223:         s_collateralToken1.delegate(account, uint128(delegatedAmounts.leftSlot()));
1227:         _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);
1252:             s_collateralToken0.refund(
1253:                 account,
1254:                 msg.sender,
1255:                 refundAmounts.rightSlot() - delegatedAmounts.rightSlot()
1256:             );
1257:             s_collateralToken1.refund(
1258:                 account,
1259:                 msg.sender,
1260:                 refundAmounts.leftSlot() - delegatedAmounts.leftSlot()
1261:             );
1265:         s_collateralToken0.refund(account, uint128(delegatedAmounts.rightSlot()));
1266:         s_collateralToken1.refund(account, uint128(delegatedAmounts.leftSlot()));
1277:         emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in PanopticFactory.deployNewPool(address,address,uint24,bytes32) (contracts/PanopticFactory.sol#210-276):
	External calls:
	- SFPM.initializeAMMPool(token0,token1,fee) (contracts/PanopticFactory.sol#233)
	- collateralTracker0.startToken(true,token0,token1,fee,newPoolContract) (contracts/PanopticFactory.sol#248)
	- collateralTracker1.startToken(false,token0,token1,fee,newPoolContract) (contracts/PanopticFactory.sol#249)
	- newPoolContract.startPool(v3Pool,token0,token1,collateralTracker0,collateralTracker1) (contracts/PanopticFactory.sol#251)
	- v3Pool.increaseObservationCardinalityNext(CARDINALITY_INCREASE) (contracts/PanopticFactory.sol#258)
	- (amount0,amount1) = _mintFullRange(v3Pool,token0,token1,fee) (contracts/PanopticFactory.sol#263)
		- IUniswapV3Pool(v3Pool).mint(address(this),tickLower,tickUpper,fullRangeLiquidity,mintCallback) (contracts/PanopticFactory.sol#403-410)
	- DONOR_NFT.issueNFT(msg.sender,newPoolContract,token0,token1,fee) (contracts/PanopticFactory.sol#266)
	Event emitted after the call(s):
	- PoolDeployed(newPoolContract,v3Pool,collateralTracker0,collateralTracker1,amount0,amount1) (contracts/PanopticFactory.sol#268-275)

/// @audit ************** Possible Issue Line(s) **************
	L#233,  L#248,  L#249,  L#251,  L#258,  L#263,  L#403-410,  L#266,  L#268-275,  

/// @audit ****************** Affected Code *******************
 233:         SFPM.initializeAMMPool(token0, token1, fee);
 248:         collateralTracker0.startToken(true, token0, token1, fee, newPoolContract);
 249:         collateralTracker1.startToken(false, token0, token1, fee, newPoolContract);
 251:         newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);
 258:         v3Pool.increaseObservationCardinalityNext(CARDINALITY_INCREASE);
 263:         (uint256 amount0, uint256 amount1) = _mintFullRange(v3Pool, token0, token1, fee);
 266:         DONOR_NFT.issueNFT(msg.sender, newPoolContract, token0, token1, fee);
 268:         emit PoolDeployed(
 269:             newPoolContract,
 270:             v3Pool,
 271:             collateralTracker0,
 272:             collateralTracker1,
 273:             amount0,
 274:             amount1
 275:         );
 403:         return
 404:             IUniswapV3Pool(v3Pool).mint(
 405:                 address(this),
 406:                 tickLower,
 407:                 tickUpper,
 408:                 fullRangeLiquidity,
 409:                 mintCallback
 410:             );

```

*GitHub* : [210-276](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L210-L276)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in SemiFungiblePositionManager.mintTokenizedPosition(TokenId,uint128,int24,int24) (contracts/SemiFungiblePositionManager.sol#504-527):
	External calls:
	- _mint(msg.sender,TokenId.unwrap(tokenId),positionSize) (contracts/SemiFungiblePositionManager.sol#515)
		- ERC1155Holder(to).onERC1155Received(msg.sender,address(0),id,amount,) != ERC1155Holder.onERC1155Received.selector (contracts/tokens/ERC1155Minimal.sol#224-225)
	Event emitted after the call(s):
	- TokenizedPositionMinted(msg.sender,tokenId,positionSize) (contracts/SemiFungiblePositionManager.sol#517)

/// @audit ************** Possible Issue Line(s) **************
	L#515,  L#517,  

/// @audit ****************** Affected Code *******************
 504:     function mintTokenizedPosition(
 505:         TokenId tokenId,
 506:         uint128 positionSize,
 507:         int24 slippageTickLimitLow,
 508:         int24 slippageTickLimitHigh
 509:     )
 510:         external
 511:         ReentrancyLock(tokenId.poolId())
 512:         returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
 513:     {
 514:         // create the option position via its ID in this erc1155
 515:         _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);
 516: 
 517:         emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);
 518: 
 519:         // validate the incoming option position, then forward to the AMM for minting/burning required liquidity chunks
 520:         (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
 521:             tokenId,
 522:             positionSize,
 523:             slippageTickLimitLow,
 524:             slippageTickLimitHigh,
 525:             MINT
 526:         );
 527:     }

```

*GitHub* : [504-527](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L504-L527)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278):
	External calls:
	- s_collateralToken0.delegate(account,uint128(delegatedAmounts.rightSlot())) (contracts/PanopticPool.sol#1222)
	- s_collateralToken1.delegate(account,uint128(delegatedAmounts.leftSlot())) (contracts/PanopticPool.sol#1223)
	- _burnAllOptionsFrom(account,0,0,COMMIT_LONG_SETTLED,touchedId) (contracts/PanopticPool.sol#1227)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	Event emitted after the call(s):
	- OptionBurnt(owner,positionSize,tokenId,premiaOwed) (contracts/PanopticPool.sol#853)
		- _burnAllOptionsFrom(account,0,0,COMMIT_LONG_SETTLED,touchedId) (contracts/PanopticPool.sol#1227)

/// @audit ************** Possible Issue Line(s) **************
	L#1222,  L#1223,  L#1227,  L#970-971,  L#985-991,  L#996-1002,  L#853,  

/// @audit ****************** Affected Code *******************
 853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );
1222:         s_collateralToken0.delegate(account, uint128(delegatedAmounts.rightSlot()));
1223:         s_collateralToken1.delegate(account, uint128(delegatedAmounts.leftSlot()));
1227:         _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in PanopticPool._burnOptions(bool,TokenId,address,int24,int24) (contracts/PanopticPool.sol#826-854):
	External calls:
	- (premiaOwed,premiaByLeg,paidAmounts) = _burnAndHandleExercise(commitLongSettled,tickLimitLow,tickLimitHigh,tokenId,positionSize,owner) (contracts/PanopticPool.sol#840-847)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	Event emitted after the call(s):
	- OptionBurnt(owner,positionSize,tokenId,premiaOwed) (contracts/PanopticPool.sol#853)

/// @audit ************** Possible Issue Line(s) **************
	L#840-847,  L#970-971,  L#985-991,  L#996-1002,  L#853,  

/// @audit ****************** Affected Code *******************
 840:         (premiaOwed, premiaByLeg, paidAmounts) = _burnAndHandleExercise(
 841:             commitLongSettled,
 842:             tickLimitLow,
 843:             tickLimitHigh,
 844:             tokenId,
 845:             positionSize,
 846:             owner
 847:         );
 853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );

```

*GitHub* : [826-854](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L826-L854)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24) (contracts/PanopticPool.sol#614-667):
	External calls:
	- poolUtilizations = _mintInSFPMAndUpdateCollateral(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#642-647)
		- (collectedByLeg,totalSwapped) = SFPM.mintTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#685-686)
		- utilization0 = s_collateralToken0.takeCommissionAddData(msg.sender,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot()) (contracts/PanopticPool.sol#715-720)
		- utilization1 = s_collateralToken1.takeCommissionAddData(msg.sender,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot()) (contracts/PanopticPool.sol#721-726)
	Event emitted after the call(s):
	- OptionMinted(msg.sender,positionSize,tokenId,poolUtilizations) (contracts/PanopticPool.sol#666)

/// @audit ************** Possible Issue Line(s) **************
	L#642-647,  L#685-686,  L#715-720,  L#721-726,  L#666,  

/// @audit ****************** Affected Code *******************
 642:         uint128 poolUtilizations = _mintInSFPMAndUpdateCollateral(
 643:             tokenId,
 644:             positionSize,
 645:             tickLimitLow,
 646:             tickLimitHigh
 647:         );
 666:         emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);
 685:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 686:             .mintTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 715:         int256 utilization0 = s_collateralToken0.takeCommissionAddData(
 716:             msg.sender,
 717:             longAmounts.rightSlot(),
 718:             shortAmounts.rightSlot(),
 719:             totalSwapped.rightSlot()
 720:         );
 721:         int256 utilization1 = s_collateralToken1.takeCommissionAddData(
 722:             msg.sender,
 723:             longAmounts.leftSlot(),
 724:             shortAmounts.leftSlot(),
 725:             totalSwapped.leftSlot()
 726:         );

```

*GitHub* : [614-667](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L614-L667)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (events) in PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171):
	External calls:
	- s_collateralToken0.delegate(msg.sender,liquidatee,delegations.rightSlot()) (contracts/PanopticPool.sol#1072)
	- s_collateralToken1.delegate(msg.sender,liquidatee,delegations.leftSlot()) (contracts/PanopticPool.sol#1073)
	- (netExchanged,premiasByLeg) = _burnAllOptionsFrom(liquidatee,Constants.MIN_V3POOL_TICK,Constants.MAX_V3POOL_TICK,DONOT_COMMIT_LONG_SETTLED,positionIdList) (contracts/PanopticPool.sol#1086-1092)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	Event emitted after the call(s):
	- OptionBurnt(owner,positionSize,tokenId,premiaOwed) (contracts/PanopticPool.sol#853)
		- (netExchanged,premiasByLeg) = _burnAllOptionsFrom(liquidatee,Constants.MIN_V3POOL_TICK,Constants.MAX_V3POOL_TICK,DONOT_COMMIT_LONG_SETTLED,positionIdList) (contracts/PanopticPool.sol#1086-1092)

/// @audit ************** Possible Issue Line(s) **************
	L#1072,  L#1073,  L#1086-1092,  L#970-971,  L#985-991,  L#996-1002,  L#853,  

/// @audit ****************** Affected Code *******************
 853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );
1072:         s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());
1073:         s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());
1086:             (netExchanged, premiasByLeg) = _burnAllOptionsFrom(
1087:                 liquidatee,
1088:                 Constants.MIN_V3POOL_TICK,
1089:                 Constants.MAX_V3POOL_TICK,
1090:                 DONOT_COMMIT_LONG_SETTLED,
1091:                 positionIdList
1092:             );

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

### [L-19]<a name="l-19"></a> Reentrancy vulnerabilities (loss of non-ether assets)

Possible Reentrancy vulnerabilities (loss of non-ether assets).  **Recom:** Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

*There are 6 instance(s) of this issue:*

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (no theft of ethers) in PanopticFactory.deployNewPool(address,address,uint24,bytes32) (contracts/PanopticFactory.sol#210-276):
	External calls:
	- SFPM.initializeAMMPool(token0,token1,fee) (contracts/PanopticFactory.sol#233)
	- collateralTracker0.startToken(true,token0,token1,fee,newPoolContract) (contracts/PanopticFactory.sol#248)
	- collateralTracker1.startToken(false,token0,token1,fee,newPoolContract) (contracts/PanopticFactory.sol#249)
	- newPoolContract.startPool(v3Pool,token0,token1,collateralTracker0,collateralTracker1) (contracts/PanopticFactory.sol#251)
	State variables written after the call(s):
	- s_getPanopticPool[v3Pool] = newPoolContract (contracts/PanopticFactory.sol#253)

/// @audit ************** Possible Issue Line(s) **************
	L#233,  L#248,  L#249,  L#251,  L#253,  

/// @audit ****************** Affected Code *******************
 233:         SFPM.initializeAMMPool(token0, token1, fee);
 248:         collateralTracker0.startToken(true, token0, token1, fee, newPoolContract);
 249:         collateralTracker1.startToken(false, token0, token1, fee, newPoolContract);
 251:         newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);
 253:         s_getPanopticPool[v3Pool] = newPoolContract;

```

*GitHub* : [210-276](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L210-L276)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (no theft of ethers) in PanopticPool._burnOptions(bool,TokenId,address,int24,int24) (contracts/PanopticPool.sol#826-854):
	External calls:
	- (premiaOwed,premiaByLeg,paidAmounts) = _burnAndHandleExercise(commitLongSettled,tickLimitLow,tickLimitHigh,tokenId,positionSize,owner) (contracts/PanopticPool.sol#840-847)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	State variables written after the call(s):
	- _updatePositionDataBurn(owner,tokenId) (contracts/PanopticPool.sol#850)
		- s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0) (contracts/PanopticPool.sol#870)

/// @audit ************** Possible Issue Line(s) **************
	L#840-847,  L#970-971,  L#985-991,  L#996-1002,  L#850,  L#870,  L#861,  

/// @audit ****************** Affected Code *******************
 840:         (premiaOwed, premiaByLeg, paidAmounts) = _burnAndHandleExercise(
 841:             commitLongSettled,
 842:             tickLimitLow,
 843:             tickLimitHigh,
 844:             tokenId,
 845:             positionSize,
 846:             owner
 847:         );
 850:         _updatePositionDataBurn(owner, tokenId);
 861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
 870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );

```

*GitHub* : [826-854](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L826-L854)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (no theft of ethers) in SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#958-1104):
	External calls:
	- collectedSingleLeg = _collectAndWritePositionData(liquidityChunk,univ3pool,currentLiquidity,positionKey,moved,isLong) (contracts/SemiFungiblePositionManager.sol#1086-1093)
		- (receivedAmount0,receivedAmount1) = univ3pool.collect(msg.sender,liquidityChunk.tickLower(),liquidityChunk.tickUpper(),uint128(amountToCollect.rightSlot()),uint128(amountToCollect.leftSlot())) (contracts/SemiFungiblePositionManager.sol#1284-1290)
	- moved = _mintLiquidity(liquidityChunk,univ3pool) (contracts/SemiFungiblePositionManager.sol#1066-1068)
		- (amount0,amount1) = univ3pool.mint(address(this),liquidityChunk.tickLower(),liquidityChunk.tickUpper(),liquidityChunk.liquidity(),mintdata) (contracts/SemiFungiblePositionManager.sol#1203-1209)
	- moved = _burnLiquidity(liquidityChunk,univ3pool) (contracts/SemiFungiblePositionManager.sol#1066-1068)
		- (amount0,amount1) = univ3pool.burn(liquidityChunk.tickLower(),liquidityChunk.tickUpper(),liquidityChunk.liquidity()) (contracts/SemiFungiblePositionManager.sol#1230-1234)
	State variables written after the call(s):
	- s_accountFeesBase[positionKey] = _getFeesBase(univ3pool,updatedLiquidity,liquidityChunk,true) (contracts/SemiFungiblePositionManager.sol#1098-1103)

/// @audit ************** Possible Issue Line(s) **************
	L#1086-1093,  L#1284-1290,  L#1066-1068,  L#1203-1209,  L#1230-1234,  L#1098-1103,  

/// @audit ****************** Affected Code *******************
1066:             moved = isLong == 0
1067:                 ? _mintLiquidity(liquidityChunk, univ3pool)
1068:                 : _burnLiquidity(liquidityChunk, univ3pool); // from msg.sender to Uniswap
1086:             collectedSingleLeg = _collectAndWritePositionData(
1087:                 liquidityChunk,
1088:                 univ3pool,
1089:                 currentLiquidity,
1090:                 positionKey,
1091:                 moved,
1092:                 isLong
1093:             );
1098:         s_accountFeesBase[positionKey] = _getFeesBase(
1099:             univ3pool,
1100:             updatedLiquidity,
1101:             liquidityChunk,
1102:             true
1103:         );
1203:         (uint256 amount0, uint256 amount1) = univ3pool.mint(
1204:             address(this),
1205:             liquidityChunk.tickLower(),
1206:             liquidityChunk.tickUpper(),
1207:             liquidityChunk.liquidity(),
1208:             mintdata
1209:         );
1230:         (uint256 amount0, uint256 amount1) = univ3pool.burn(
1231:             liquidityChunk.tickLower(),
1232:             liquidityChunk.tickUpper(),
1233:             liquidityChunk.liquidity()
1234:         );
1284:             (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(
1285:                 msg.sender,
1286:                 liquidityChunk.tickLower(),
1287:                 liquidityChunk.tickUpper(),
1288:                 uint128(amountToCollect.rightSlot()),
1289:                 uint128(amountToCollect.leftSlot())
1290:             );

```

*GitHub* : [958-1104](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L958-L1104)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (no theft of ethers) in PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171):
	External calls:
	- s_collateralToken0.delegate(msg.sender,liquidatee,delegations.rightSlot()) (contracts/PanopticPool.sol#1072)
	- s_collateralToken1.delegate(msg.sender,liquidatee,delegations.leftSlot()) (contracts/PanopticPool.sol#1073)
	- (netExchanged,premiasByLeg) = _burnAllOptionsFrom(liquidatee,Constants.MIN_V3POOL_TICK,Constants.MAX_V3POOL_TICK,DONOT_COMMIT_LONG_SETTLED,positionIdList) (contracts/PanopticPool.sol#1086-1092)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	State variables written after the call(s):
	- (netExchanged,premiasByLeg) = _burnAllOptionsFrom(liquidatee,Constants.MIN_V3POOL_TICK,Constants.MAX_V3POOL_TICK,DONOT_COMMIT_LONG_SETTLED,positionIdList) (contracts/PanopticPool.sol#1086-1092)
		- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(uint256(Math.max((int256(grossPremiumLast.rightSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][0] * positionLiquidity)) + int256(legPremia.rightSlot() * 2 ** 64),0)) / totalLiquidity)).toLeftSlot(uint128(uint256(Math.max((int256(grossPremiumLast.leftSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][1] * positionLiquidity)) + int256(legPremia.leftSlot()) * 2 ** 64,0)) / totalLiquidity)) (contracts/PanopticPool.sol#1928-1968)
		- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0])).toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1])) (contracts/PanopticPool.sol#1928-1968)

/// @audit ************** Possible Issue Line(s) **************
	L#1072,  L#1073,  L#1086-1092,  L#970-971,  L#985-991,  L#996-1002,  L#1928-1968,  L#870,  L#861,  L#1416,  L#1974,  

/// @audit ****************** Affected Code *******************
 861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
 870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );
1072:         s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());
1073:         s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());
1086:             (netExchanged, premiasByLeg) = _burnAllOptionsFrom(
1087:                 liquidatee,
1088:                 Constants.MIN_V3POOL_TICK,
1089:                 Constants.MAX_V3POOL_TICK,
1090:                 DONOT_COMMIT_LONG_SETTLED,
1091:                 positionIdList
1092:             );
1416:         s_positionsHash[account] = newHash;
1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929:                             ? LeftRightUnsigned
1930:                                 .wrap(0)
1931:                                 .toRightSlot(
1932:                                     uint128(
1933:                                         uint256(
1934:                                             Math.max(
1935:                                                 (int256(
1936:                                                     grossPremiumLast.rightSlot() *
1937:                                                         totalLiquidityBefore
1938:                                                 ) -
1939:                                                     int256(
1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941:                                                             positionLiquidity
1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),
1943:                                                 0
1944:                                             )
1945:                                         ) / totalLiquidity
1946:                                     )
1947:                                 )
1948:                                 .toLeftSlot(
1949:                                     uint128(
1950:                                         uint256(
1951:                                             Math.max(
1952:                                                 (int256(
1953:                                                     grossPremiumLast.leftSlot() *
1954:                                                         totalLiquidityBefore
1955:                                                 ) -
1956:                                                     int256(
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958:                                                             positionLiquidity
1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960:                                                 0
1961:                                             )
1962:                                         ) / totalLiquidity
1963:                                     )
1964:                                 )
1965:                             : LeftRightUnsigned
1966:                                 .wrap(0)
1967:                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1974:             s_settledTokens[chunkKey] = settledTokens;

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (no theft of ethers) in PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278):
	External calls:
	- s_collateralToken0.delegate(account,uint128(delegatedAmounts.rightSlot())) (contracts/PanopticPool.sol#1222)
	- s_collateralToken1.delegate(account,uint128(delegatedAmounts.leftSlot())) (contracts/PanopticPool.sol#1223)
	- _burnAllOptionsFrom(account,0,0,COMMIT_LONG_SETTLED,touchedId) (contracts/PanopticPool.sol#1227)
		- (collectedByLeg,totalSwapped) = SFPM.burnTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#970-971)
		- paid0 = s_collateralToken0.exercise(owner,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot(),realizedPremia.rightSlot()) (contracts/PanopticPool.sol#985-991)
		- paid1 = s_collateralToken1.exercise(owner,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot(),realizedPremia.leftSlot()) (contracts/PanopticPool.sol#996-1002)
	State variables written after the call(s):
	- _burnAllOptionsFrom(account,0,0,COMMIT_LONG_SETTLED,touchedId) (contracts/PanopticPool.sol#1227)
		- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(uint256(Math.max((int256(grossPremiumLast.rightSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][0] * positionLiquidity)) + int256(legPremia.rightSlot() * 2 ** 64),0)) / totalLiquidity)).toLeftSlot(uint128(uint256(Math.max((int256(grossPremiumLast.leftSlot() * totalLiquidityBefore) - int256(_premiumAccumulatorsByLeg[_leg][1] * positionLiquidity)) + int256(legPremia.leftSlot()) * 2 ** 64,0)) / totalLiquidity)) (contracts/PanopticPool.sol#1928-1968)
		- s_grossPremiumLast[chunkKey] = LeftRightUnsigned.wrap(0).toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0])).toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1])) (contracts/PanopticPool.sol#1928-1968)

/// @audit ************** Possible Issue Line(s) **************
	L#1222,  L#1223,  L#1227,  L#970-971,  L#985-991,  L#996-1002,  L#1928-1968,  L#870,  L#861,  L#1416,  L#1974,  

/// @audit ****************** Affected Code *******************
 861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
 870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
 970:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 985:             int128 paid0 = s_collateralToken0.exercise(
 986:                 owner,
 987:                 longAmounts.rightSlot(),
 988:                 shortAmounts.rightSlot(),
 989:                 totalSwapped.rightSlot(),
 990:                 realizedPremia.rightSlot()
 991:             );
 996:             int128 paid1 = s_collateralToken1.exercise(
 997:                 owner,
 998:                 longAmounts.leftSlot(),
 999:                 shortAmounts.leftSlot(),
1000:                 totalSwapped.leftSlot(),
1001:                 realizedPremia.leftSlot()
1002:             );
1222:         s_collateralToken0.delegate(account, uint128(delegatedAmounts.rightSlot()));
1223:         s_collateralToken1.delegate(account, uint128(delegatedAmounts.leftSlot()));
1227:         _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);
1416:         s_positionsHash[account] = newHash;
1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929:                             ? LeftRightUnsigned
1930:                                 .wrap(0)
1931:                                 .toRightSlot(
1932:                                     uint128(
1933:                                         uint256(
1934:                                             Math.max(
1935:                                                 (int256(
1936:                                                     grossPremiumLast.rightSlot() *
1937:                                                         totalLiquidityBefore
1938:                                                 ) -
1939:                                                     int256(
1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *
1941:                                                             positionLiquidity
1942:                                                     )) + int256(legPremia.rightSlot() * 2 ** 64),
1943:                                                 0
1944:                                             )
1945:                                         ) / totalLiquidity
1946:                                     )
1947:                                 )
1948:                                 .toLeftSlot(
1949:                                     uint128(
1950:                                         uint256(
1951:                                             Math.max(
1952:                                                 (int256(
1953:                                                     grossPremiumLast.leftSlot() *
1954:                                                         totalLiquidityBefore
1955:                                                 ) -
1956:                                                     int256(
1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *
1958:                                                             positionLiquidity
1959:                                                     )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960:                                                 0
1961:                                             )
1962:                                         ) / totalLiquidity
1963:                                     )
1964:                                 )
1965:                             : LeftRightUnsigned
1966:                                 .wrap(0)
1967:                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1974:             s_settledTokens[chunkKey] = settledTokens;

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Reentrancy (no theft of ethers) in PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24) (contracts/PanopticPool.sol#614-667):
	External calls:
	- poolUtilizations = _mintInSFPMAndUpdateCollateral(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#642-647)
		- (collectedByLeg,totalSwapped) = SFPM.mintTokenizedPosition(tokenId,positionSize,tickLimitLow,tickLimitHigh) (contracts/PanopticPool.sol#685-686)
		- utilization0 = s_collateralToken0.takeCommissionAddData(msg.sender,longAmounts.rightSlot(),shortAmounts.rightSlot(),totalSwapped.rightSlot()) (contracts/PanopticPool.sol#715-720)
		- utilization1 = s_collateralToken1.takeCommissionAddData(msg.sender,longAmounts.leftSlot(),shortAmounts.leftSlot(),totalSwapped.leftSlot()) (contracts/PanopticPool.sol#721-726)
	State variables written after the call(s):
	- s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned.wrap(0).toLeftSlot(poolUtilizations).toRightSlot(positionSize) (contracts/PanopticPool.sol#654-657)

/// @audit ************** Possible Issue Line(s) **************
	L#642-647,  L#685-686,  L#715-720,  L#721-726,  L#654-657,  L#650,  L#1416,  

/// @audit ****************** Affected Code *******************
 642:         uint128 poolUtilizations = _mintInSFPMAndUpdateCollateral(
 643:             tokenId,
 644:             positionSize,
 645:             tickLimitLow,
 646:             tickLimitHigh
 647:         );
 650:         _addUserOption(tokenId, effectiveLiquidityLimitX32);
 654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
 655:             .wrap(0)
 656:             .toLeftSlot(poolUtilizations)
 657:             .toRightSlot(positionSize);
 685:         (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped) = SFPM
 686:             .mintTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);
 715:         int256 utilization0 = s_collateralToken0.takeCommissionAddData(
 716:             msg.sender,
 717:             longAmounts.rightSlot(),
 718:             shortAmounts.rightSlot(),
 719:             totalSwapped.rightSlot()
 720:         );
 721:         int256 utilization1 = s_collateralToken1.takeCommissionAddData(
 722:             msg.sender,
 723:             longAmounts.leftSlot(),
 724:             shortAmounts.leftSlot(),
 725:             totalSwapped.leftSlot()
 726:         );
1416:         s_positionsHash[account] = newHash;

```

*GitHub* : [614-667](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L614-L667)

### [L-20]<a name="l-20"></a> Block timestamp

Dangerous use of `block.timestamp` (to compute/ assert values of different variables), which can be manipulated by miners.  **Recom:** Avoid relying on `block.timestamp`.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) uses timestamp for comparisons and computations.
	Dangerous usage:
	- block.timestamp >= uint256(uint40(medianData >> 216)) + period (contracts/libraries/PanopticMath.sol#183)
	- updatedMedianData = (block.timestamp << 216) + (uint256(newOrderMap) << 192) + uint256(uint192(medianData << 24)) + uint256(uint24(lastObservedTick)) (contracts/libraries/PanopticMath.sol#226-230)

/// @audit ************** Possible Issue Line(s) **************
	L#183,  L#226-230,  

/// @audit ****************** Affected Code *******************
 183:             if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {
 226:                 updatedMedianData =
 227:                     (block.timestamp << 216) +
 228:                     (uint256(newOrderMap) << 192) +
 229:                     uint256(uint192(medianData << 24)) +
 230:                     uint256(uint24(lastObservedTick));

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker) (contracts/PanopticPool.sol#291-327) uses timestamp for comparisons and computations.
	Dangerous usage:
	- s_miniMedian = (uint256(block.timestamp) << 216) + (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) + (uint256(uint24(currentTick)) << 24) + (uint256(uint24(currentTick))) (contracts/PanopticPool.sol#308-314)

/// @audit ************** Possible Issue Line(s) **************
	L#308-314,  

/// @audit ****************** Affected Code *******************
 308:             s_miniMedian =
 309:                 (uint256(block.timestamp) << 216) +
 310:                 // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
 311:                 // see comment on s_miniMedian initialization for format of this magic number
 312:                 (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
 313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4
 314:                 (uint256(uint24(currentTick))); // add to slot 3

```

*GitHub* : [291-327](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L291-L327)

### [L-21]<a name="l-21"></a> Uninitialized local variables

Local variables without initialization may use default value and result in a wrong computation.  **Recom:** Initialize all the variables before use. If a variable is meant to be initialized to zero, explicitly set it to zero to improve code readability.

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256).acctPremia (contracts/SemiFungiblePositionManager.sol#1462) is a local variable never initialized

/// @audit ************** Possible Issue Line(s) **************
	L#1462,  

/// @audit ****************** Affected Code *******************
1462:         LeftRightUnsigned acctPremia;

```

*GitHub* : [1462-1462](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1462-L1462)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).updatedLiquidity (contracts/SemiFungiblePositionManager.sol#986) is a local variable never initialized

/// @audit ************** Possible Issue Line(s) **************
	L#986,  

/// @audit ****************** Affected Code *******************
 986:         uint128 updatedLiquidity;

```

*GitHub* : [986-986](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L986-L986)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getAccountMargin(address,int24,uint256[2][],int128).tokenRequired (contracts/CollateralTracker.sol#1165) is a local variable never initialized

/// @audit ************** Possible Issue Line(s) **************
	L#1165,  

/// @audit ****************** Affected Code *******************
1165:         uint256 tokenRequired;

```

*GitHub* : [1165-1165](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1165-L1165)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).longPremium (contracts/libraries/PanopticMath.sol#780) is a local variable never initialized

/// @audit ************** Possible Issue Line(s) **************
	L#780,  

/// @audit ****************** Affected Code *******************
 780:             LeftRightSigned longPremium;

```

*GitHub* : [780-780](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L780-L780)

### [L-22]<a name="l-22"></a> Unused return

The return value of an external call is not stored in a local or state variable.  **Recom:** Ensure that all the return values of a function call are used.

*There are 25 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker) (contracts/PanopticPool.sol#291-327) ignores return value by:
	- (currentTick) = IUniswapV3Pool(_univ3pool).slot0() (contracts/PanopticPool.sol#304)

/// @audit ************** Possible Issue Line(s) **************
	L#304,  

/// @audit ****************** Affected Code *******************
 304:         (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();

```

*GitHub* : [291-327](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L291-L327)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) ignores return value by:
	- collateral0.exercise(_liquidatee,0,0,0,int128(haircut0)) (contracts/libraries/PanopticMath.sol#856)

/// @audit ************** Possible Issue Line(s) **************
	L#856,  

/// @audit ****************** Affected Code *******************
 856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) ignores return value by:
	- (timestamp_old,tickCumulative_old) = univ3pool.observations(uint256(int256(observationIndex) - int256(1) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#186-190)

/// @audit ************** Possible Issue Line(s) **************
	L#186-190,  

/// @audit ****************** Affected Code *******************
 186:                     (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(
 187:                         uint256(
 188:                             int256(observationIndex) - int256(1) + int256(observationCardinality)
 189:                         ) % observationCardinality
 190:                     );

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) ignores return value by:
	- (currentTick) = s_univ3pool.slot0() (contracts/PanopticPool.sol#1598)

/// @audit ************** Possible Issue Line(s) **************
	L#1598,  

/// @audit ****************** Affected Code *******************
1598:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24) (contracts/libraries/FeesCalc.sol#130-208) ignores return value by:
	- (lowerOut0,lowerOut1) = univ3pool.ticks(tickLower) (contracts/libraries/FeesCalc.sol#142)

/// @audit ************** Possible Issue Line(s) **************
	L#142,  

/// @audit ****************** Affected Code *******************
 142:         (, , uint256 lowerOut0, uint256 lowerOut1, , , , ) = univ3pool.ticks(tickLower);

```

*GitHub* : [130-208](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L130-L208)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) ignores return value by:
	- (currentTick) = s_univ3pool.slot0() (contracts/PanopticPool.sol#1032)

/// @audit ************** Possible Issue Line(s) **************
	L#1032,  

/// @audit ****************** Affected Code *******************
1032:             (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) ignores return value by:
	- (timestamps[i],tickCumulatives[i],None,None) = univ3pool.observations(uint256((int256(observationIndex) - int256(i * period)) + int256(observationCardinality)) % observationCardinality) (contracts/libraries/PanopticMath.sol#138-143)

/// @audit ************** Possible Issue Line(s) **************
	L#138-143,  

/// @audit ****************** Affected Code *******************
 138:                 (timestamps[i], tickCumulatives[i], , ) = univ3pool.observations(
 139:                     uint256(
 140:                         (int256(observationIndex) - int256(i * period)) +
 141:                             int256(observationCardinality)
 142:                     ) % observationCardinality
 143:                 );

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.calculateAccumulatedFeesBatch(address,bool,TokenId[]) (contracts/PanopticPool.sol#381-400) ignores return value by:
	- (currentTick) = s_univ3pool.slot0() (contracts/PanopticPool.sol#387)

/// @audit ************** Possible Issue Line(s) **************
	L#387,  

/// @audit ****************** Affected Code *******************
 381:     function calculateAccumulatedFeesBatch(
 382:         address user,
 383:         bool includePendingPremium,
 384:         TokenId[] calldata positionIdList
 385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {
 386:         // Get the current tick of the Uniswap pool
 387:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
 388: 
 389:         // Compute the accumulated premia for all tokenId in positionIdList (includes short+long premium)
 390:         (LeftRightSigned premia, uint256[2][] memory balances) = _calculateAccumulatedPremia(
 391:             user,
 392:             positionIdList,
 393:             COMPUTE_ALL_PREMIA,
 394:             includePendingPremium,
 395:             currentTick
 396:         );
 397: 
 398:         // Return the premia as (token0, token1)
 399:         return (premia.rightSlot(), premia.leftSlot(), balances);
 400:     }

```

*GitHub* : [381-400](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L381-L400)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) ignores return value by:
	- s_collateralToken1.exercise(owner,0,0,0,realizedPremia.leftSlot()) (contracts/PanopticPool.sol#1640)

/// @audit ************** Possible Issue Line(s) **************
	L#1640,  

/// @audit ****************** Affected Code *******************
1640:             s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.assertPriceWithinBounds(uint160,uint160) (contracts/PanopticPool.sol#338-344) ignores return value by:
	- (currentSqrtPriceX96) = s_univ3pool.slot0() (contracts/PanopticPool.sol#339)

/// @audit ************** Possible Issue Line(s) **************
	L#339,  

/// @audit ****************** Affected Code *******************
 338:     function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {
 339:         (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();
 340: 
 341:         if (currentSqrtPriceX96 <= sqrtLowerBound || currentSqrtPriceX96 >= sqrtUpperBound) {
 342:             revert Errors.PriceBoundFail();
 343:         }
 344:     }

```

*GitHub* : [338-344](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L338-L344)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24) (contracts/PanopticFactory.sol#335-411) ignores return value by:
	- IUniswapV3Pool(v3Pool).mint(address(this),tickLower,tickUpper,fullRangeLiquidity,mintCallback) (contracts/PanopticFactory.sol#403-410)

/// @audit ************** Possible Issue Line(s) **************
	L#403-410,  

/// @audit ****************** Affected Code *******************
 403:         return
 404:             IUniswapV3Pool(v3Pool).mint(
 405:                 address(this),
 406:                 tickLower,
 407:                 tickUpper,
 408:                 fullRangeLiquidity,
 409:                 mintCallback
 410:             );

```

*GitHub* : [335-411](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L335-L411)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) ignores return value by:
	- collateral1.exercise(_liquidatee,0,0,0,int128(haircut1)) (contracts/libraries/PanopticMath.sol#857)

/// @audit ************** Possible Issue Line(s) **************
	L#857,  

/// @audit ****************** Affected Code *******************
 857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24) (contracts/PanopticFactory.sol#335-411) ignores return value by:
	- (currentSqrtPriceX96) = v3Pool.slot0() (contracts/PanopticFactory.sol#341)

/// @audit ************** Possible Issue Line(s) **************
	L#341,  

/// @audit ****************** Affected Code *******************
 341:         (uint160 currentSqrtPriceX96, , , , , , ) = v3Pool.slot0();

```

*GitHub* : [335-411](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L335-L411)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) ignores return value by:
	- (None,finalTick,None,None,None,None,None) = s_univ3pool.slot0() (contracts/PanopticPool.sol#1094)

/// @audit ************** Possible Issue Line(s) **************
	L#1094,  

/// @audit ****************** Affected Code *******************
1094:             (, finalTick, , , , , ) = s_univ3pool.slot0();

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#1138-1178) ignores return value by:
	- (feeGrowthInside0LastX128,feeGrowthInside1LastX128) = univ3pool.positions(keccak256(bytes)(abi.encodePacked(address(this),liquidityChunk.tickLower(),liquidityChunk.tickUpper()))) (contracts/SemiFungiblePositionManager.sol#1148-1157)

/// @audit ************** Possible Issue Line(s) **************
	L#1148-1157,  

/// @audit ****************** Affected Code *******************
1148:         (, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, , ) = univ3pool
1149:             .positions(
1150:                 keccak256(
1151:                     abi.encodePacked(
1152:                         address(this),
1153:                         liquidityChunk.tickLower(),
1154:                         liquidityChunk.tickUpper()
1155:                     )
1156:                 )
1157:             );

```

*GitHub* : [1138-1178](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1138-L1178)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._validateSolvency(address,TokenId[],uint256) (contracts/PanopticPool.sol#887-946) ignores return value by:
	- (currentTick,observationIndex,observationCardinality) = _univ3pool.slot0() (contracts/PanopticPool.sol#896-904)

/// @audit ************** Possible Issue Line(s) **************
	L#896-904,  

/// @audit ****************** Affected Code *******************
 896:         (
 897:             ,
 898:             int24 currentTick,
 899:             uint16 observationIndex,
 900:             uint16 observationCardinality,
 901:             ,
 902:             ,
 903: 
 904:         ) = _univ3pool.slot0();

```

*GitHub* : [887-946](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L887-L946)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24) (contracts/libraries/FeesCalc.sol#130-208) ignores return value by:
	- (upperOut0,upperOut1) = univ3pool.ticks(tickUpper) (contracts/libraries/FeesCalc.sol#143)

/// @audit ************** Possible Issue Line(s) **************
	L#143,  

/// @audit ****************** Affected Code *******************
 143:         (, , uint256 upperOut0, uint256 upperOut1, , , , ) = univ3pool.ticks(tickUpper);

```

*GitHub* : [130-208](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L130-L208)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278) ignores return value by:
	- (currentTick) = s_univ3pool.slot0() (contracts/PanopticPool.sol#1202)

/// @audit ************** Possible Issue Line(s) **************
	L#1202,  

/// @audit ****************** Affected Code *******************
1202:         (, int24 currentTick, , , , , ) = s_univ3pool.slot0();

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) ignores return value by:
	- s_collateralToken0.exercise(owner,0,0,0,realizedPremia.rightSlot()) (contracts/PanopticPool.sol#1639)

/// @audit ************** Possible Issue Line(s) **************
	L#1639,  

/// @audit ****************** Affected Code *******************
1639:             s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.pokeMedian() (contracts/PanopticPool.sol#522-534) ignores return value by:
	- (observationIndex,observationCardinality) = s_univ3pool.slot0() (contracts/PanopticPool.sol#523)

/// @audit ************** Possible Issue Line(s) **************
	L#523,  

/// @audit ****************** Affected Code *******************
 522:     function pokeMedian() external {
 523:         (, , uint16 observationIndex, uint16 observationCardinality, , , ) = s_univ3pool.slot0();
 524: 
 525:         (, uint256 medianData) = PanopticMath.computeInternalMedian(
 526:             observationIndex,
 527:             observationCardinality,
 528:             MEDIAN_PERIOD,
 529:             s_miniMedian,
 530:             s_univ3pool
 531:         );
 532: 
 533:         if (medianData != 0) s_miniMedian = medianData;
 534:     }

```

*GitHub* : [522-534](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L522-L534)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.swapInAMM(IUniswapV3Pool,LeftRightSigned) (contracts/SemiFungiblePositionManager.sol#756-852) ignores return value by:
	- (sqrtPriceX96) = _univ3pool.slot0() (contracts/SemiFungiblePositionManager.sol#788)

/// @audit ************** Possible Issue Line(s) **************
	L#788,  

/// @audit ****************** Affected Code *******************
 788:                 (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();

```

*GitHub* : [756-852](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L756-L852)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) ignores return value by:
	- (timestamp_last,tickCumulative_last) = univ3pool.observations(observationIndex) (contracts/libraries/PanopticMath.sol#192-193)

/// @audit ************** Possible Issue Line(s) **************
	L#192-193,  

/// @audit ****************** Affected Code *******************
 192:                     (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool
 193:                         .observations(observationIndex);

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.twapFilter(IUniswapV3Pool,uint32) (contracts/libraries/PanopticMath.sol#241-268) ignores return value by:
	- (tickCumulatives) = univ3pool.observe(secondsAgos) (contracts/libraries/PanopticMath.sol#253)

/// @audit ************** Possible Issue Line(s) **************
	L#253,  

/// @audit ****************** Affected Code *******************
 253:             (int56[] memory tickCumulatives, ) = univ3pool.observe(secondsAgos);

```

*GitHub* : [241-268](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L241-L268)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.pokeMedian() (contracts/PanopticPool.sol#522-534) ignores return value by:
	- (medianData) = PanopticMath.computeInternalMedian(observationIndex,observationCardinality,MEDIAN_PERIOD,s_miniMedian,s_univ3pool) (contracts/PanopticPool.sol#525-531)

/// @audit ************** Possible Issue Line(s) **************
	L#525-531,  

/// @audit ****************** Affected Code *******************
 522:     function pokeMedian() external {
 523:         (, , uint16 observationIndex, uint16 observationCardinality, , , ) = s_univ3pool.slot0();
 524: 
 525:         (, uint256 medianData) = PanopticMath.computeInternalMedian(
 526:             observationIndex,
 527:             observationCardinality,
 528:             MEDIAN_PERIOD,
 529:             s_miniMedian,
 530:             s_univ3pool
 531:         );
 532: 
 533:         if (medianData != 0) s_miniMedian = medianData;
 534:     }

```

*GitHub* : [522-534](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L522-L534)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._validateAndForwardToAMM(TokenId,uint128,int24,int24,bool) (contracts/SemiFungiblePositionManager.sol#680-729) ignores return value by:
	- (currentTick) = univ3pool.slot0() (contracts/SemiFungiblePositionManager.sol#725)

/// @audit ************** Possible Issue Line(s) **************
	L#725,  

/// @audit ****************** Affected Code *******************
 725:         (, int24 currentTick, , , , , ) = univ3pool.slot0();

```

*GitHub* : [680-729](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L680-L729)


### NonCritical Risk Issues

### [N-01]<a name="n-01"></a> Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.constructor(SemiFungiblePositionManager) (contracts/PanopticPool.sol#280-282) may emit `event` at the end of `constructor`

/// @audit ****************** Affected Code *******************
 280:     constructor(SemiFungiblePositionManager _sfpm) {
 281:         SFPM = _sfpm;
 282:     }

```

*GitHub* : [280-282](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L280-L282)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.constructor(uint256,uint256,uint256,int256,uint256,uint256,uint256) (contracts/CollateralTracker.sol#178-211) may emit `event` at the end of `constructor`

/// @audit ****************** Affected Code *******************
 178:     constructor(
 179:         uint256 _commissionFee,
 180:         uint256 _sellerCollateralRatio,
 181:         uint256 _buyerCollateralRatio,
 182:         int256 _forceExerciseCost,
 183:         uint256 _targetPoolUtilization,
 184:         uint256 _saturatedPoolUtilization,
 185:         uint256 _ITMSpreadMultiplier
 186:     ) {
 187:         COMMISSION_FEE = _commissionFee;

```

*GitHub* : [178-211](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L178-L211)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address) (contracts/PanopticFactory.sol#115-130) may emit `event` at the end of `constructor`

/// @audit ****************** Affected Code *******************
 115:     constructor(
 116:         address _WETH9,
 117:         SemiFungiblePositionManager _SFPM,
 118:         IUniswapV3Factory _univ3Factory,
 119:         IDonorNFT _donorNFT,
 120:         address _poolReference,
 121:         address _collateralReference
 122:     ) {
 123:         WETH = _WETH9;
 124:         SFPM = _SFPM;
 125:         DONOR_NFT = _donorNFT;
 126:         // We store the Uniswap Factory contract - later we can use this to verify uniswap pools
 127:         UNIV3_FACTORY = _univ3Factory;
 128:         POOL_REFERENCE = _poolReference;
 129:         COLLATERAL_REFERENCE = _collateralReference;
 130:     }

```

*GitHub* : [115-130](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L115-L130)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.constructor(IUniswapV3Factory) (contracts/SemiFungiblePositionManager.sol#341-343) may emit `event` at the end of `constructor`

/// @audit ****************** Affected Code *******************
 341:     constructor(IUniswapV3Factory _factory) {
 342:         FACTORY = _factory;
 343:     }

```

*GitHub* : [341-343](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L341-L343)

### [N-02]<a name="n-02"></a> Similar Constants decalred in Multiple Contracts 

Similar constants can be decalred in a system-wide single file for better management.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
MAX_UINT256 declared in multiple contracts :-  
	- Math.MAX_UINT256 (contracts/libraries/Math.sol#15)
	- PanopticMath.MAX_UINT256 (contracts/libraries/PanopticMath.sol#23)

/// @audit ************** Possible Issue Line(s) **************
	L#15,  

/// @audit ****************** Affected Code *******************
  15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```

*GitHub* : [15-15](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L15-L15)

### [N-03]<a name="n-03"></a> Events are missing sender information

When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the `msg.sender` the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

*There are 9 instance(s) of this issue:*

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal._transferFrom(address,address,uint256) (contracts/tokens/ERC20Minimal.sol#103-113) may emit `msg.sender` in :-
	- Transfer(from,to,amount) (contracts/tokens/ERC20Minimal.sol#112)

/// @audit ************** Possible Issue Line(s) **************
	L#112,  

/// @audit ****************** Affected Code *******************
 103:     function _transferFrom(address from, address to, uint256 amount) internal {
 104:         balanceOf[from] -= amount;
 105: 
 106:         // Cannot overflow because the sum of all user
 107:         // balances can't exceed the max uint256 value.
 108:         unchecked {
 109:             balanceOf[to] += amount;
 110:         }
 111: 
 112:         emit Transfer(from, to, amount);
 113:     }

```

*GitHub* : [103-113](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L103-L113)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._burnOptions(bool,TokenId,address,int24,int24) (contracts/PanopticPool.sol#826-854) may emit `msg.sender` in :-
	- OptionBurnt(owner,positionSize,tokenId,premiaOwed) (contracts/PanopticPool.sol#853)

/// @audit ************** Possible Issue Line(s) **************
	L#853,  

/// @audit ****************** Affected Code *******************
 853:         emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);

```

*GitHub* : [826-854](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L826-L854)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal._mint(address,uint256) (contracts/tokens/ERC20Minimal.sol#122-131) may emit `msg.sender` in :-
	- Transfer(address(0),to,amount) (contracts/tokens/ERC20Minimal.sol#130)

/// @audit ************** Possible Issue Line(s) **************
	L#130,  

/// @audit ****************** Affected Code *******************
 122:     function _mint(address to, uint256 amount) internal {
 123:         // Cannot overflow because the sum of all user
 124:         // balances can't exceed the max uint256 value.
 125:         unchecked {
 126:             balanceOf[to] += amount;
 127:         }
 128:         totalSupply += amount;
 129: 
 130:         emit Transfer(address(0), to, amount);
 131:     }

```

*GitHub* : [122-131](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L122-L131)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.transferOwnership(address) (contracts/PanopticFactory.sol#147-155) may emit `msg.sender` in :-
	- OwnershipTransferred(currentOwner,newOwner) (contracts/PanopticFactory.sol#154)

/// @audit ************** Possible Issue Line(s) **************
	L#154,  

/// @audit ****************** Affected Code *******************
 147:     function transferOwnership(address newOwner) external {
 148:         address currentOwner = s_owner;
 149: 
 150:         if (msg.sender != currentOwner) revert Errors.NotOwner();
 151: 
 152:         s_owner = newOwner;
 153: 
 154:         emit OwnershipTransferred(currentOwner, newOwner);
 155:     }

```

*GitHub* : [147-155](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L147-L155)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) may emit `msg.sender` in :-
	- PremiumSettled(owner,tokenId,realizedPremia) (contracts/PanopticPool.sol#1654)

/// @audit ************** Possible Issue Line(s) **************
	L#1654,  

/// @audit ****************** Affected Code *******************
1654:             emit PremiumSettled(owner, tokenId, realizedPremia);

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.deployNewPool(address,address,uint24,bytes32) (contracts/PanopticFactory.sol#210-276) may emit `msg.sender` in :-
	- PoolDeployed(newPoolContract,v3Pool,collateralTracker0,collateralTracker1,amount0,amount1) (contracts/PanopticFactory.sol#268-275)

/// @audit ************** Possible Issue Line(s) **************
	L#268-275,  

/// @audit ****************** Affected Code *******************
 268:         emit PoolDeployed(
 269:             newPoolContract,
 270:             v3Pool,
 271:             collateralTracker0,
 272:             collateralTracker1,
 273:             amount0,
 274:             amount1
 275:         );

```

*GitHub* : [210-276](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L210-L276)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.initializeAMMPool(address,address,uint24) (contracts/SemiFungiblePositionManager.sol#350-391) may emit `msg.sender` in :-
	- PoolInitialized(univ3pool,poolId) (contracts/SemiFungiblePositionManager.sol#390)

/// @audit ************** Possible Issue Line(s) **************
	L#390,  

/// @audit ****************** Affected Code *******************
 390:         emit PoolInitialized(univ3pool, poolId);

```

*GitHub* : [350-391](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L350-L391)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal.transferFrom(address,address,uint256) (contracts/tokens/ERC20Minimal.sol#81-97) may emit `msg.sender` in :-
	- Transfer(from,to,amount) (contracts/tokens/ERC20Minimal.sol#94)

/// @audit ************** Possible Issue Line(s) **************
	L#94,  

/// @audit ****************** Affected Code *******************
  81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
  82:         uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.
  83: 
  84:         if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;
  85: 
  86:         balanceOf[from] -= amount;
  87: 
  88:         // Cannot overflow because the sum of all user
  89:         // balances can't exceed the max uint256 value.
  90:         unchecked {
  91:             balanceOf[to] += amount;
  92:         }
  93: 
  94:         emit Transfer(from, to, amount);
  95: 
  96:         return true;
  97:     }

```

*GitHub* : [81-97](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L81-L97)

```solidity
File: contracts/tokens/ERC20Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC20Minimal._burn(address,uint256) (contracts/tokens/ERC20Minimal.sol#136-146) may emit `msg.sender` in :-
	- Transfer(from,address(0),amount) (contracts/tokens/ERC20Minimal.sol#145)

/// @audit ************** Possible Issue Line(s) **************
	L#145,  

/// @audit ****************** Affected Code *******************
 136:     function _burn(address from, uint256 amount) internal {
 137:         balanceOf[from] -= amount;
 138: 
 139:         // Cannot underflow because a user's balance
 140:         // will never be larger than the total supply.
 141:         unchecked {
 142:             totalSupply -= amount;
 143:         }
 144: 
 145:         emit Transfer(from, address(0), amount);
 146:     }

```

*GitHub* : [136-146](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L136-L146)

### [N-04]<a name="n-04"></a> Validate user inputs

There are no validations done on the arguments below. Consider that the Solidity [documentation](https://docs.soliditylang.org/en/latest/control-structures.html#panic-via-assert-and-error-via-require) states that `Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix`. This means that there should be explicit checks for expected ranges of inputs. Underflows/overflows result in panics should not be used as range checks, and allowing funds to be sent to  `0x0`, which is the default value of address variables and has many gotchas, should be avoided.

*There are 95 instance(s) of this issue:*

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv96RoundingUp(uint256,uint256) (contracts/libraries/Math.sol#584-592) does not validate following parameters:- 
	- Math.mulDiv96RoundingUp(uint256,uint256).a (contracts/libraries/Math.sol#584)
	- Math.mulDiv96RoundingUp(uint256,uint256).b (contracts/libraries/Math.sol#584)

/// @audit ************** Possible Issue Line(s) **************
	L#584,  

/// @audit ****************** Affected Code *******************
 584:     function mulDiv96RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
 585:         unchecked {
 586:             result = mulDiv96(a, b);
 587:             if (mulmod(a, b, 2 ** 96) > 0) {
 588:                 require(result < type(uint256).max);
 589:                 result++;
 590:             }
 591:         }
 592:     }

```

*GitHub* : [584-592](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L584-L592)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath._calculateIOAmounts(TokenId,uint128,uint256) (contracts/libraries/PanopticMath.sol#607-635) does not validate following parameters:- 
	- PanopticMath._calculateIOAmounts(TokenId,uint128,uint256).tokenId (contracts/libraries/PanopticMath.sol#608)
	- PanopticMath._calculateIOAmounts(TokenId,uint128,uint256).legIndex (contracts/libraries/PanopticMath.sol#610)

/// @audit ************** Possible Issue Line(s) **************
	L#608,  L#610,  

/// @audit ****************** Affected Code *******************
 608:         TokenId tokenId,
 610:         uint256 legIndex

```

*GitHub* : [607-635](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L607-L635)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]) (contracts/PanopticPool.sol#1017-1171) does not validate following parameters:- 
	- PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).positionIdListLiquidator (contracts/PanopticPool.sol#1018)

/// @audit ************** Possible Issue Line(s) **************
	L#1018,  

/// @audit ****************** Affected Code *******************
1018:         TokenId[] calldata positionIdListLiquidator,

```

*GitHub* : [1017-1171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1171)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getSlippageLimits(int24,int24) (contracts/PanopticPool.sol#499-515) does not validate following parameters:- 
	- PanopticPool._getSlippageLimits(int24,int24).tickLimitLow (contracts/PanopticPool.sol#500)
	- PanopticPool._getSlippageLimits(int24,int24).tickLimitHigh (contracts/PanopticPool.sol#501)

/// @audit ************** Possible Issue Line(s) **************
	L#500,  L#501,  

/// @audit ****************** Affected Code *******************
 499:     function _getSlippageLimits(
 500:         int24 tickLimitLow,
 501:         int24 tickLimitHigh
 502:     ) internal pure returns (int24, int24) {
 503:         // disable slippage checks if tickLimitLow == tickLimitHigh
 504:         if (tickLimitLow == tickLimitHigh) {
 505:             // note the reversed order of the ticks
 506:             return (MAX_SWAP_TICK, MIN_SWAP_TICK);
 507:         }
 508: 
 509:         // ensure tick limits are reversed (the SFPM uses low > high as a flag to do ITM swaps, which we need)
 510:         if (tickLimitLow < tickLimitHigh) {
 511:             return (tickLimitHigh, tickLimitLow);
 512:         }
 513: 
 514:         return (tickLimitLow, tickLimitHigh);
 515:     }

```

*GitHub* : [499-515](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L499-L515)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._checkLiquiditySpread(TokenId,uint256,int24,int24,uint64) (contracts/PanopticPool.sol#1465-1494) does not validate following parameters:- 
	- PanopticPool._checkLiquiditySpread(TokenId,uint256,int24,int24,uint64).effectiveLiquidityLimitX32 (contracts/PanopticPool.sol#1470)

/// @audit ************** Possible Issue Line(s) **************
	L#1470,  

/// @audit ****************** Affected Code *******************
1470:         uint64 effectiveLiquidityLimitX32

```

*GitHub* : [1465-1494](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1465-L1494)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool) (contracts/PanopticPool.sol#1833-1980) does not validate following parameters:- 
	- PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool).tokenId (contracts/PanopticPool.sol#1835)
	- PanopticPool._updateSettlementPostBurn(address,TokenId,LeftRightUnsigned[4],uint128,bool).commitLongSettled (contracts/PanopticPool.sol#1838)

/// @audit ************** Possible Issue Line(s) **************
	L#1835,  L#1838,  

/// @audit ****************** Affected Code *******************
1835:         TokenId tokenId,
1838:         bool commitLongSettled

```

*GitHub* : [1833-1980](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1833-L1980)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.validate(TokenId) (contracts/types/TokenId.sol#500-571) does not validate following parameters:- 
	- TokenIdLibrary.validate(TokenId).self (contracts/types/TokenId.sol#500)

/// @audit ************** Possible Issue Line(s) **************
	L#500,  

/// @audit ****************** Affected Code *******************
 500:     function validate(TokenId self) internal pure {

```

*GitHub* : [500-571](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L500-L571)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.sub(LeftRightUnsigned,LeftRightUnsigned) (contracts/types/LeftRight.sol#171-188) does not validate following parameters:- 
	- LeftRightLibrary.sub(LeftRightUnsigned,LeftRightUnsigned).x (contracts/types/LeftRight.sol#172)

/// @audit ************** Possible Issue Line(s) **************
	L#172,  

/// @audit ****************** Affected Code *******************
 171:     function sub(
 172:         LeftRightUnsigned x,
 173:         LeftRightUnsigned y
 174:     ) internal pure returns (LeftRightUnsigned z) {
 175:         unchecked {
 176:             // subtracting leftRight packed uint128's is same as just subtracting the values explictily
 177:             // given that we check for underflows of the left and right values
 178:             z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));
 179: 
 180:             // on underflow z will be greater than either x or y
 181:             // type cast z to uint128 to isolate the right slot and if it's higher than a value that was subtracted from (x)
 182:             // then an underflow has occured
 183:             if (
 184:                 LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||
 185:                 (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))
 186:             ) revert Errors.UnderOverFlow();
 187:         }
 188:     }

```

*GitHub* : [171-188](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L171-L188)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24) (contracts/libraries/FeesCalc.sol#130-208) does not validate following parameters:- 
	- FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24).currentTick (contracts/libraries/FeesCalc.sol#132)
	- FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24).tickLower (contracts/libraries/FeesCalc.sol#133)
	- FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24).tickUpper (contracts/libraries/FeesCalc.sol#134)

/// @audit ************** Possible Issue Line(s) **************
	L#132,  L#133,  L#134,  

/// @audit ****************** Affected Code *******************
 132:         int24 currentTick,
 133:         int24 tickLower,
 134:         int24 tickUpper

```

*GitHub* : [130-208](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L130-L208)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.deployNewPool(address,address,uint24,bytes32) (contracts/PanopticFactory.sol#210-276) does not validate following parameters:- 
	- PanopticFactory.deployNewPool(address,address,uint24,bytes32).token0 (contracts/PanopticFactory.sol#211)
	- PanopticFactory.deployNewPool(address,address,uint24,bytes32).token1 (contracts/PanopticFactory.sol#212)
	- PanopticFactory.deployNewPool(address,address,uint24,bytes32).salt (contracts/PanopticFactory.sol#214)

/// @audit ************** Possible Issue Line(s) **************
	L#211,  L#212,  L#214,  

/// @audit ****************** Affected Code *******************
 211:         address token0,
 212:         address token1,
 214:         bytes32 salt

```

*GitHub* : [210-276](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L210-L276)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.toUint128Capped(uint256) (contracts/libraries/Math.sol#302-306) does not validate following parameters:- 
	- Math.toUint128Capped(uint256).toDowncast (contracts/libraries/Math.sol#302)

/// @audit ************** Possible Issue Line(s) **************
	L#302,  

/// @audit ****************** Affected Code *******************
 302:     function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {
 303:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) {
 304:             downcastedInt = type(uint128).max;
 305:         }
 306:     }

```

*GitHub* : [302-306](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L302-L306)

```solidity
File: contracts/multicall/Multicall.sol

/// @audit ******************* Issue Detail *******************
Multicall.multicall(bytes[]) (contracts/multicall/Multicall.sol#12-36) does not validate following parameters:- 
	- Multicall.multicall(bytes[]).data (contracts/multicall/Multicall.sol#12)

/// @audit ************** Possible Issue Line(s) **************
	L#12,  

/// @audit ****************** Affected Code *******************
  12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
  13:         results = new bytes[](data.length);
  14:         for (uint256 i = 0; i < data.length; ) {
  15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);
  16: 
  17:             if (!success) {
  18:                 // Bubble up the revert reason
  19:                 // The bytes type is ABI encoded as a length-prefixed byte array
  20:                 // So we simply need to add 32 to the pointer to get the start of the data
  21:                 // And then revert with the size loaded from the first 32 bytes
  22:                 // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
  23:                 // However, we have chosen to simply replicate the the normal behavior of the call
  24:                 // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
  25:                 assembly ("memory-safe") {
  26:                     revert(add(result, 32), mload(result))
  27:                 }
  28:             }
  29: 
  30:             results[i] = result;
  31: 
  32:             unchecked {
  33:                 ++i;
  34:             }
  35:         }
  36:     }

```

*GitHub* : [12-36](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L12-L36)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes) (contracts/tokens/ERC1155Minimal.sol#94-120) does not validate following parameters:- 
	- ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes).from (contracts/tokens/ERC1155Minimal.sol#95)
	- ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes).to (contracts/tokens/ERC1155Minimal.sol#96)
	- ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes).id (contracts/tokens/ERC1155Minimal.sol#97)
	- ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes).amount (contracts/tokens/ERC1155Minimal.sol#98)
	- ERC1155.safeTransferFrom(address,address,uint256,uint256,bytes).data (contracts/tokens/ERC1155Minimal.sol#99)

/// @audit ************** Possible Issue Line(s) **************
	L#95,  L#96,  L#97,  L#98,  L#99,  

/// @audit ****************** Affected Code *******************
  95:         address from,
  96:         address to,
  97:         uint256 id,
  98:         uint256 amount,
  99:         bytes calldata data

```

*GitHub* : [94-120](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L94-L120)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.abs(int256) (contracts/libraries/Math.sol#73-75) does not validate following parameters:- 
	- Math.abs(int256).x (contracts/libraries/Math.sol#73)

/// @audit ************** Possible Issue Line(s) **************
	L#73,  

/// @audit ****************** Affected Code *******************
  73:     function abs(int256 x) internal pure returns (int256) {
  74:         return x > 0 ? x : -x;
  75:     }

```

*GitHub* : [73-75](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L73-L75)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256) (contracts/SemiFungiblePositionManager.sol#1449-1523) does not validate following parameters:- 
	- SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256).atTick (contracts/SemiFungiblePositionManager.sol#1455)
	- SemiFungiblePositionManager.getAccountPremium(address,address,uint256,int24,int24,int24,uint256).isLong (contracts/SemiFungiblePositionManager.sol#1456)

/// @audit ************** Possible Issue Line(s) **************
	L#1455,  L#1456,  

/// @audit ****************** Affected Code *******************
1455:         int24 atTick,
1456:         uint256 isLong

```

*GitHub* : [1449-1523](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1449-L1523)

```solidity
File: contracts/libraries/InteractionHelper.sol

/// @audit ******************* Issue Detail *******************
InteractionHelper.computeName(address,address,bool,uint24,string) (contracts/libraries/InteractionHelper.sol#48-85) does not validate following parameters:- 
	- InteractionHelper.computeName(address,address,bool,uint24,string).isToken0 (contracts/libraries/InteractionHelper.sol#51)

/// @audit ************** Possible Issue Line(s) **************
	L#51,  

/// @audit ****************** Affected Code *******************
  51:         bool isToken0,

```

*GitHub* : [48-85](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L48-L85)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.max(uint256,uint256) (contracts/libraries/Math.sol#57-59) does not validate following parameters:- 
	- Math.max(uint256,uint256).a (contracts/libraries/Math.sol#57)
	- Math.max(uint256,uint256).b (contracts/libraries/Math.sol#57)

/// @audit ************** Possible Issue Line(s) **************
	L#57,  

/// @audit ****************** Affected Code *******************
  57:     function max(uint256 a, uint256 b) internal pure returns (uint256) {
  58:         return a > b ? a : b;
  59:     }

```

*GitHub* : [57-59](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L57-L59)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.min(int256,int256) (contracts/libraries/Math.sol#49-51) does not validate following parameters:- 
	- Math.min(int256,int256).a (contracts/libraries/Math.sol#49)
	- Math.min(int256,int256).b (contracts/libraries/Math.sol#49)

/// @audit ************** Possible Issue Line(s) **************
	L#49,  

/// @audit ****************** Affected Code *******************
  49:     function min(int256 a, int256 b) internal pure returns (int256) {
  50:         return a < b ? a : b;
  51:     }

```

*GitHub* : [49-51](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L49-L51)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.max(int256,int256) (contracts/libraries/Math.sol#65-67) does not validate following parameters:- 
	- Math.max(int256,int256).a (contracts/libraries/Math.sol#65)
	- Math.max(int256,int256).b (contracts/libraries/Math.sol#65)

/// @audit ************** Possible Issue Line(s) **************
	L#65,  

/// @audit ****************** Affected Code *******************
  65:     function max(int256 a, int256 b) internal pure returns (int256) {
  66:         return a > b ? a : b;
  67:     }

```

*GitHub* : [65-67](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L65-L67)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/SemiFungiblePositionManager.sol#566-585) does not validate following parameters:- 
	- SemiFungiblePositionManager.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes).ids (contracts/SemiFungiblePositionManager.sol#569)

/// @audit ************** Possible Issue Line(s) **************
	L#569,  

/// @audit ****************** Affected Code *******************
 566:     function safeBatchTransferFrom(
 567:         address from,
 568:         address to,
 569:         uint256[] calldata ids,
 570:         uint256[] calldata amounts,
 571:         bytes calldata data
 572:     ) public override {
 573:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
 574:         // so just check if there is an active reentrancy lock for the relevant pool on each token
 575:         for (uint256 i = 0; i < ids.length; ) {
 576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
 577:             registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
 578:             unchecked {
 579:                 ++i;
 580:             }
 581:         }
 582: 
 583:         // transfer the token (note that all state updates are completed before reentrancy is possible)
 584:         super.safeBatchTransferFrom(from, to, ids, amounts, data);
 585:     }

```

*GitHub* : [566-585](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566-L585)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#958-1104) does not validate following parameters:- 
	- SemiFungiblePositionManager._createLegInAMM(IUniswapV3Pool,TokenId,uint256,LiquidityChunk,bool).isBurn (contracts/SemiFungiblePositionManager.sol#963)

/// @audit ************** Possible Issue Line(s) **************
	L#963,  

/// @audit ****************** Affected Code *******************
 963:         bool isBurn

```

*GitHub* : [958-1104](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L958-L1104)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.maxRedeem(address) (contracts/CollateralTracker.sol#572-576) does not validate following parameters:- 
	- CollateralTracker.maxRedeem(address).owner (contracts/CollateralTracker.sol#572)

/// @audit ************** Possible Issue Line(s) **************
	L#572,  

/// @audit ****************** Affected Code *******************
 572:     function maxRedeem(address owner) public view returns (uint256 maxShares) {
 573:         uint256 available = convertToShares(s_poolAssets);
 574:         uint256 balance = balanceOf[owner];
 575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;
 576:     }

```

*GitHub* : [572-576](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L572-L576)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.clearLeg(TokenId,uint256) (contracts/types/TokenId.sol#464-491) does not validate following parameters:- 
	- TokenIdLibrary.clearLeg(TokenId,uint256).i (contracts/types/TokenId.sol#464)

/// @audit ************** Possible Issue Line(s) **************
	L#464,  

/// @audit ****************** Affected Code *******************
 464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```

*GitHub* : [464-491](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L464-L491)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightUnsigned,LeftRightUnsigned) (contracts/types/LeftRight.sol#148-165) does not validate following parameters:- 
	- LeftRightLibrary.add(LeftRightUnsigned,LeftRightUnsigned).x (contracts/types/LeftRight.sol#149)

/// @audit ************** Possible Issue Line(s) **************
	L#149,  

/// @audit ****************** Affected Code *******************
 148:     function add(
 149:         LeftRightUnsigned x,
 150:         LeftRightUnsigned y
 151:     ) internal pure returns (LeftRightUnsigned z) {
 152:         unchecked {
 153:             // adding leftRight packed uint128's is same as just adding the values explictily
 154:             // given that we check for overflows of the left and right values
 155:             z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));
 156: 
 157:             // on overflow z will be less than either x or y
 158:             // type cast z to uint128 to isolate the right slot and if it's lower than a value it's comprised of (x)
 159:             // then an overflow has occured
 160:             if (
 161:                 LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||
 162:                 (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))
 163:             ) revert Errors.UnderOverFlow();
 164:         }
 165:     }

```

*GitHub* : [148-165](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L148-L165)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128) (contracts/CollateralTracker.sol#1510-1589) does not validate following parameters:- 
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128).tokenId (contracts/CollateralTracker.sol#1511)
	- CollateralTracker._computeSpread(TokenId,uint128,uint256,uint256,uint128).index (contracts/CollateralTracker.sol#1513)

/// @audit ************** Possible Issue Line(s) **************
	L#1511,  L#1513,  

/// @audit ****************** Affected Code *******************
1511:         TokenId tokenId,
1513:         uint256 index,

```

*GitHub* : [1510-1589](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1510-L1589)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.quickSort(int256[],int256,int256) (contracts/libraries/Math.sol#753-771) does not validate following parameters:- 
	- Math.quickSort(int256[],int256,int256).arr (contracts/libraries/Math.sol#753)
	- Math.quickSort(int256[],int256,int256).left (contracts/libraries/Math.sol#753)
	- Math.quickSort(int256[],int256,int256).right (contracts/libraries/Math.sol#753)

/// @audit ************** Possible Issue Line(s) **************
	L#753,  

/// @audit ****************** Affected Code *******************
 753:     function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {
 754:         unchecked {
 755:             int256 i = left;
 756:             int256 j = right;
 757:             if (i == j) return;
 758:             int256 pivot = arr[uint256(left + (right - left) / 2)];
 759:             while (i < j) {
 760:                 while (arr[uint256(i)] < pivot) i++;
 761:                 while (pivot < arr[uint256(j)]) j--;
 762:                 if (i <= j) {
 763:                     (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);
 764:                     i++;
 765:                     j--;
 766:                 }
 767:             }
 768:             if (left < j) quickSort(arr, left, j);
 769:             if (i < right) quickSort(arr, i, right);
 770:         }
 771:     }

```

*GitHub* : [753-771](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L753-L771)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._buyCollateralRatio(uint256) (contracts/CollateralTracker.sol#806-853) does not validate following parameters:- 
	- CollateralTracker._buyCollateralRatio(uint256).utilization (contracts/CollateralTracker.sol#807)

/// @audit ************** Possible Issue Line(s) **************
	L#807,  

/// @audit ****************** Affected Code *******************
 807:         uint256 utilization

```

*GitHub* : [806-853](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L806-L853)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1311-1422) does not validate following parameters:- 
	- CollateralTracker._getRequiredCollateralSingleLegNoPartner(TokenId,uint256,uint128,int24,uint128).atTick (contracts/CollateralTracker.sol#1315)

/// @audit ************** Possible Issue Line(s) **************
	L#1315,  

/// @audit ****************** Affected Code *******************
1315:         int24 atTick,

```

*GitHub* : [1311-1422](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1311-L1422)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24) (contracts/PanopticFactory.sol#335-411) does not validate following parameters:- 
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).token0 (contracts/PanopticFactory.sol#337)
	- PanopticFactory._mintFullRange(IUniswapV3Pool,address,address,uint24).token1 (contracts/PanopticFactory.sol#338)

/// @audit ************** Possible Issue Line(s) **************
	L#337,  L#338,  

/// @audit ****************** Affected Code *******************
 337:         address token0,
 338:         address token1,

```

*GitHub* : [335-411](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L335-L411)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mostSignificantNibble(uint160) (contracts/libraries/Math.sol#91-117) does not validate following parameters:- 
	- Math.mostSignificantNibble(uint160).x (contracts/libraries/Math.sol#91)

/// @audit ************** Possible Issue Line(s) **************
	L#91,  

/// @audit ****************** Affected Code *******************
  91:     function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {

```

*GitHub* : [91-117](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L91-L117)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.uniswapV3MintCallback(uint256,uint256,bytes) (contracts/SemiFungiblePositionManager.sol#402-426) does not validate following parameters:- 
	- SemiFungiblePositionManager.uniswapV3MintCallback(uint256,uint256,bytes).amount0Owed (contracts/SemiFungiblePositionManager.sol#403)
	- SemiFungiblePositionManager.uniswapV3MintCallback(uint256,uint256,bytes).amount1Owed (contracts/SemiFungiblePositionManager.sol#404)

/// @audit ************** Possible Issue Line(s) **************
	L#403,  L#404,  

/// @audit ****************** Affected Code *******************
 402:     function uniswapV3MintCallback(
 403:         uint256 amount0Owed,
 404:         uint256 amount1Owed,
 405:         bytes calldata data
 406:     ) external {
 407:         // Decode the mint callback data
 408:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));
 409:         // Validate caller to ensure we got called from the AMM pool
 410:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);
 411:         // Sends the amount0Owed and amount1Owed quantities provided
 412:         if (amount0Owed > 0)
 413:             SafeTransferLib.safeTransferFrom(
 414:                 decoded.poolFeatures.token0,
 415:                 decoded.payer,
 416:                 msg.sender,
 417:                 amount0Owed
 418:             );
 419:         if (amount1Owed > 0)
 420:             SafeTransferLib.safeTransferFrom(
 421:                 decoded.poolFeatures.token1,
 422:                 decoded.payer,
 423:                 msg.sender,
 424:                 amount1Owed
 425:             );
 426:     }

```

*GitHub* : [402-426](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L402-L426)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.absUint(int256) (contracts/libraries/Math.sol#81-85) does not validate following parameters:- 
	- Math.absUint(int256).x (contracts/libraries/Math.sol#81)

/// @audit ************** Possible Issue Line(s) **************
	L#81,  

/// @audit ****************** Affected Code *******************
  81:     function absUint(int256 x) internal pure returns (uint256) {
  82:         unchecked {
  83:             return x > 0 ? uint256(x) : uint256(-x);
  84:         }
  85:     }

```

*GitHub* : [81-85](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L81-L85)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.transferFrom(address,address,uint256) (contracts/CollateralTracker.sol#341-353) does not validate following parameters:- 
	- CollateralTracker.transferFrom(address,address,uint256).from (contracts/CollateralTracker.sol#342)

/// @audit ************** Possible Issue Line(s) **************
	L#342,  

/// @audit ****************** Affected Code *******************
 341:     function transferFrom(
 342:         address from,
 343:         address to,
 344:         uint256 amount
 345:     ) public override(ERC20Minimal) returns (bool) {
 346:         // make sure the caller does not have any open option positions
 347:         // if they do: we don't want them sending panoptic pool shares to others
 348:         // as this would reduce their amount of collateral against the opened positions
 349: 
 350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();
 351: 
 352:         return ERC20Minimal.transferFrom(from, to, amount);
 353:     }

```

*GitHub* : [341-353](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L341-L353)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.max24(int24,int24) (contracts/libraries/Math.sol#33-35) does not validate following parameters:- 
	- Math.max24(int24,int24).a (contracts/libraries/Math.sol#33)
	- Math.max24(int24,int24).b (contracts/libraries/Math.sol#33)

/// @audit ************** Possible Issue Line(s) **************
	L#33,  

/// @audit ****************** Affected Code *******************
  33:     function max24(int24 a, int24 b) internal pure returns (int24) {
  34:         return a > b ? a : b;
  35:     }

```

*GitHub* : [33-35](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L33-L35)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.min24(int24,int24) (contracts/libraries/Math.sol#25-27) does not validate following parameters:- 
	- Math.min24(int24,int24).a (contracts/libraries/Math.sol#25)
	- Math.min24(int24,int24).b (contracts/libraries/Math.sol#25)

/// @audit ************** Possible Issue Line(s) **************
	L#25,  

/// @audit ****************** Affected Code *******************
  25:     function min24(int24 a, int24 b) internal pure returns (int24) {
  26:         return a < b ? a : b;
  27:     }

```

*GitHub* : [25-27](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L25-L27)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned) (contracts/CollateralTracker.sol#650-734) does not validate following parameters:- 
	- CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned).positionId (contracts/CollateralTracker.sol#653)

/// @audit ************** Possible Issue Line(s) **************
	L#653,  

/// @audit ****************** Affected Code *******************
 653:         TokenId positionId,

```

*GitHub* : [650-734](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L650-L734)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]) (contracts/libraries/FeesCalc.sol#46-87) does not validate following parameters:- 
	- FeesCalc.getPortfolioValue(int24,mapping(TokenId => LeftRightUnsigned),TokenId[]).positionIdList (contracts/libraries/FeesCalc.sol#49)

/// @audit ************** Possible Issue Line(s) **************
	L#49,  

/// @audit ****************** Affected Code *******************
  49:         TokenId[] calldata positionIdList

```

*GitHub* : [46-87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46-L87)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convert1to0(int256,uint160) (contracts/libraries/PanopticMath.sol#547-567) does not validate following parameters:- 
	- PanopticMath.convert1to0(int256,uint160).amount (contracts/libraries/PanopticMath.sol#547)
	- PanopticMath.convert1to0(int256,uint160).sqrtPriceX96 (contracts/libraries/PanopticMath.sol#547)

/// @audit ************** Possible Issue Line(s) **************
	L#547,  

/// @audit ****************** Affected Code *******************
 547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
 548:         unchecked {
 549:             // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
 550:             // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
 551:             if (sqrtPriceX96 < type(uint128).max) {
 552:                 int256 absResult = Math
 553:                     .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
 554:                     .toInt256();
 555:                 return amount < 0 ? -absResult : absResult;
 556:             } else {
 557:                 int256 absResult = Math
 558:                     .mulDiv(
 559:                         Math.absUint(amount),
 560:                         2 ** 128,
 561:                         Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
 562:                     )
 563:                     .toInt256();
 564:                 return amount < 0 ? -absResult : absResult;
 565:             }
 566:         }
 567:     }

```

*GitHub* : [547-567](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L547-L567)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getTicks(int24,int24,int24) (contracts/libraries/PanopticMath.sol#338-363) does not validate following parameters:- 
	- PanopticMath.getTicks(int24,int24,int24).tickSpacing (contracts/libraries/PanopticMath.sol#341)

/// @audit ************** Possible Issue Line(s) **************
	L#341,  

/// @audit ****************** Affected Code *******************
 341:         int24 tickSpacing

```

*GitHub* : [338-363](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L338-L363)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getAmountsForLiquidity(int24,LiquidityChunk) (contracts/libraries/Math.sol#221-233) does not validate following parameters:- 
	- Math.getAmountsForLiquidity(int24,LiquidityChunk).currentTick (contracts/libraries/Math.sol#222)
	- Math.getAmountsForLiquidity(int24,LiquidityChunk).liquidityChunk (contracts/libraries/Math.sol#223)

/// @audit ************** Possible Issue Line(s) **************
	L#222,  L#223,  

/// @audit ****************** Affected Code *******************
 221:     function getAmountsForLiquidity(
 222:         int24 currentTick,
 223:         LiquidityChunk liquidityChunk
 224:     ) internal pure returns (uint256 amount0, uint256 amount1) {
 225:         if (currentTick <= liquidityChunk.tickLower()) {
 226:             amount0 = getAmount0ForLiquidity(liquidityChunk);
 227:         } else if (currentTick >= liquidityChunk.tickUpper()) {
 228:             amount1 = getAmount1ForLiquidity(liquidityChunk);
 229:         } else {
 230:             amount0 = getAmount0ForLiquidity(liquidityChunk.updateTickLower(currentTick));
 231:             amount1 = getAmount1ForLiquidity(liquidityChunk.updateTickUpper(currentTick));
 232:         }
 233:     }

```

*GitHub* : [221-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L221-L233)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool) (contracts/SemiFungiblePositionManager.sol#1138-1178) does not validate following parameters:- 
	- SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool).roundUp (contracts/SemiFungiblePositionManager.sol#1142)

/// @audit ************** Possible Issue Line(s) **************
	L#1142,  

/// @audit ****************** Affected Code *******************
1142:         bool roundUp

```

*GitHub* : [1138-1178](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1138-L1178)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256) (contracts/SemiFungiblePositionManager.sol#1255-1313) does not validate following parameters:- 
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).movedInLeg (contracts/SemiFungiblePositionManager.sol#1260)
	- SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).isLong (contracts/SemiFungiblePositionManager.sol#1261)

/// @audit ************** Possible Issue Line(s) **************
	L#1260,  L#1261,  

/// @audit ****************** Affected Code *******************
1260:         LeftRightSigned movedInLeg,
1261:         uint256 isLong

```

*GitHub* : [1255-1313](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1255-L1313)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155._mint(address,uint256,uint256) (contracts/tokens/ERC1155Minimal.sol#214-230) does not validate following parameters:- 
	- ERC1155._mint(address,uint256,uint256).to (contracts/tokens/ERC1155Minimal.sol#214)
	- ERC1155._mint(address,uint256,uint256).id (contracts/tokens/ERC1155Minimal.sol#214)
	- ERC1155._mint(address,uint256,uint256).amount (contracts/tokens/ERC1155Minimal.sol#214)

/// @audit ************** Possible Issue Line(s) **************
	L#214,  

/// @audit ****************** Affected Code *******************
 214:     function _mint(address to, uint256 id, uint256 amount) internal {
 215:         // balance will never overflow
 216:         unchecked {
 217:             balanceOf[to][id] += amount;
 218:         }
 219: 
 220:         emit TransferSingle(msg.sender, address(0), to, id, amount);
 221: 
 222:         if (to.code.length != 0) {
 223:             if (
 224:                 ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
 225:                 ERC1155Holder.onERC1155Received.selector
 226:             ) {
 227:                 revert UnsafeRecipient();
 228:             }
 229:         }
 230:     }

```

*GitHub* : [214-230](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L214-L230)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._sellCollateralRatio(int256) (contracts/CollateralTracker.sol#751-800) does not validate following parameters:- 
	- CollateralTracker._sellCollateralRatio(int256).utilization (contracts/CollateralTracker.sol#752)

/// @audit ************** Possible Issue Line(s) **************
	L#752,  

/// @audit ****************** Affected Code *******************
 752:         int256 utilization

```

*GitHub* : [751-800](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L751-L800)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) does not validate following parameters:- 
	- Math.getSqrtRatioAtTick(int24).tick (contracts/libraries/Math.sol#128)

/// @audit ************** Possible Issue Line(s) **************
	L#128,  

/// @audit ****************** Affected Code *******************
 128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.exercise(address,int128,int128,int128,int128) (contracts/CollateralTracker.sol#1043-1089) does not validate following parameters:- 
	- CollateralTracker.exercise(address,int128,int128,int128,int128).longAmount (contracts/CollateralTracker.sol#1045)
	- CollateralTracker.exercise(address,int128,int128,int128,int128).shortAmount (contracts/CollateralTracker.sol#1046)

/// @audit ************** Possible Issue Line(s) **************
	L#1045,  L#1046,  

/// @audit ****************** Affected Code *******************
1045:         int128 longAmount,
1046:         int128 shortAmount,

```

*GitHub* : [1043-1089](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1043-L1089)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLegPartner(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1439-1464) does not validate following parameters:- 
	- CollateralTracker._getRequiredCollateralSingleLegPartner(TokenId,uint256,uint128,int24,uint128).tokenId (contracts/CollateralTracker.sol#1440)

/// @audit ************** Possible Issue Line(s) **************
	L#1440,  

/// @audit ****************** Affected Code *******************
1440:         TokenId tokenId,

```

*GitHub* : [1439-1464](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1439-L1464)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.numberOfLeadingHexZeros(address) (contracts/libraries/PanopticMath.sol#75-79) does not validate following parameters:- 
	- PanopticMath.numberOfLeadingHexZeros(address).addr (contracts/libraries/PanopticMath.sol#75)

/// @audit ************** Possible Issue Line(s) **************
	L#75,  

/// @audit ****************** Affected Code *******************
  75:     function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {
  76:         unchecked {
  77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));
  78:         }
  79:     }

```

*GitHub* : [75-79](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L75-L79)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.toInt128(int256) (contracts/libraries/Math.sol#318-320) does not validate following parameters:- 
	- Math.toInt128(int256).toCast (contracts/libraries/Math.sol#318)

/// @audit ************** Possible Issue Line(s) **************
	L#318,  

/// @audit ****************** Affected Code *******************
 318:     function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {
 319:         if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();
 320:     }

```

*GitHub* : [318-320](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L318-L320)

```solidity
File: contracts/libraries/CallbackLib.sol

/// @audit ******************* Issue Detail *******************
CallbackLib.validateCallback(address,IUniswapV3Factory,CallbackLib.PoolFeatures) (contracts/libraries/CallbackLib.sol#30-38) does not validate following parameters:- 
	- CallbackLib.validateCallback(address,IUniswapV3Factory,CallbackLib.PoolFeatures).sender (contracts/libraries/CallbackLib.sol#31)
	- CallbackLib.validateCallback(address,IUniswapV3Factory,CallbackLib.PoolFeatures).factory (contracts/libraries/CallbackLib.sol#32)
	- CallbackLib.validateCallback(address,IUniswapV3Factory,CallbackLib.PoolFeatures).features (contracts/libraries/CallbackLib.sol#33)

/// @audit ************** Possible Issue Line(s) **************
	L#31,  L#32,  L#33,  

/// @audit ****************** Affected Code *******************
  30:     function validateCallback(
  31:         address sender,
  32:         IUniswapV3Factory factory,
  33:         PoolFeatures memory features
  34:     ) internal view {
  35:         // Call getPool on the factory to verify that the sender corresponds to the canonical pool with the claimed features
  36:         if (factory.getPool(features.token0, features.token1, features.fee) != sender)
  37:             revert Errors.InvalidUniswapCallback();
  38:     }

```

*GitHub* : [30-38](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L30-L38)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._validateSolvency(address,TokenId[],uint256) (contracts/PanopticPool.sol#887-946) does not validate following parameters:- 
	- PanopticPool._validateSolvency(address,TokenId[],uint256).user (contracts/PanopticPool.sol#888)
	- PanopticPool._validateSolvency(address,TokenId[],uint256).positionIdList (contracts/PanopticPool.sol#889)
	- PanopticPool._validateSolvency(address,TokenId[],uint256).buffer (contracts/PanopticPool.sol#890)

/// @audit ************** Possible Issue Line(s) **************
	L#888,  L#889,  L#890,  

/// @audit ****************** Affected Code *******************
 888:         address user,
 889:         TokenId[] calldata positionIdList,
 890:         uint256 buffer

```

*GitHub* : [887-946](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L887-L946)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.toUint128(uint256) (contracts/libraries/Math.sol#296-298) does not validate following parameters:- 
	- Math.toUint128(uint256).toDowncast (contracts/libraries/Math.sol#296)

/// @audit ************** Possible Issue Line(s) **************
	L#296,  

/// @audit ****************** Affected Code *******************
 296:     function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {
 297:         if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();
 298:     }

```

*GitHub* : [296-298](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L296-L298)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convert0to1(uint256,uint160) (contracts/libraries/PanopticMath.sol#490-500) does not validate following parameters:- 
	- PanopticMath.convert0to1(uint256,uint160).sqrtPriceX96 (contracts/libraries/PanopticMath.sol#490)

/// @audit ************** Possible Issue Line(s) **************
	L#490,  

/// @audit ****************** Affected Code *******************
 490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {
 491:         unchecked {
 492:             // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
 493:             // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
 494:             if (sqrtPriceX96 < type(uint128).max) {
 495:                 return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
 496:             } else {
 497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
 498:             }
 499:         }
 500:     }

```

*GitHub* : [490-500](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L490-L500)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convert0to1(int256,uint160) (contracts/libraries/PanopticMath.sol#524-540) does not validate following parameters:- 
	- PanopticMath.convert0to1(int256,uint160).amount (contracts/libraries/PanopticMath.sol#524)
	- PanopticMath.convert0to1(int256,uint160).sqrtPriceX96 (contracts/libraries/PanopticMath.sol#524)

/// @audit ************** Possible Issue Line(s) **************
	L#524,  

/// @audit ****************** Affected Code *******************
 524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
 525:         unchecked {
 526:             // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
 527:             // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
 528:             if (sqrtPriceX96 < type(uint128).max) {
 529:                 int256 absResult = Math
 530:                     .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
 531:                     .toInt256();
 532:                 return amount < 0 ? -absResult : absResult;
 533:             } else {
 534:                 int256 absResult = Math
 535:                     .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
 536:                     .toInt256();
 537:                 return amount < 0 ? -absResult : absResult;
 538:             }
 539:         }
 540:     }

```

*GitHub* : [524-540](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L524-L540)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getLiquidityChunk(TokenId,uint256,uint128) (contracts/libraries/PanopticMath.sol#289-330) does not validate following parameters:- 
	- PanopticMath.getLiquidityChunk(TokenId,uint256,uint128).tokenId (contracts/libraries/PanopticMath.sol#290)
	- PanopticMath.getLiquidityChunk(TokenId,uint256,uint128).legIndex (contracts/libraries/PanopticMath.sol#291)

/// @audit ************** Possible Issue Line(s) **************
	L#290,  L#291,  

/// @audit ****************** Affected Code *******************
 290:         TokenId tokenId,
 291:         uint256 legIndex,

```

*GitHub* : [289-330](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L289-L330)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]) (contracts/PanopticPool.sol#1179-1278) does not validate following parameters:- 
	- PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]).touchedId (contracts/PanopticPool.sol#1181)
	- PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]).positionIdListExercisor (contracts/PanopticPool.sol#1183)

/// @audit ************** Possible Issue Line(s) **************
	L#1181,  L#1183,  

/// @audit ****************** Affected Code *******************
1181:         TokenId[] calldata touchedId,
1183:         TokenId[] calldata positionIdListExercisor

```

*GitHub* : [1179-1278](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1179-L1278)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.validateIsExercisable(TokenId,int24) (contracts/types/TokenId.sol#578-599) does not validate following parameters:- 
	- TokenIdLibrary.validateIsExercisable(TokenId,int24).self (contracts/types/TokenId.sol#578)
	- TokenIdLibrary.validateIsExercisable(TokenId,int24).currentTick (contracts/types/TokenId.sol#578)

/// @audit ************** Possible Issue Line(s) **************
	L#578,  

/// @audit ****************** Affected Code *******************
 578:     function validateIsExercisable(TokenId self, int24 currentTick) internal pure {
 579:         unchecked {
 580:             uint256 numLegs = self.countLegs();
 581:             for (uint256 i = 0; i < numLegs; ++i) {
 582:                 (int24 rangeDown, int24 rangeUp) = PanopticMath.getRangesFromStrike(
 583:                     self.width(i),
 584:                     self.tickSpacing()
 585:                 );
 586: 
 587:                 int24 _strike = self.strike(i);
 588:                 // check if the price is outside this chunk
 589:                 if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {
 590:                     // if this leg is long and the price beyond the leg's range:
 591:                     // this exercised ID, `self`, appears valid
 592:                     if (self.isLong(i) == 1) return; // validated
 593:                 }
 594:             }
 595:         }
 596: 
 597:         // Fail if position has no legs that is far-out-of-the-money
 598:         revert Errors.NoLegsExercisable();
 599:     }

```

*GitHub* : [578-599](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L578-L599)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.getAmountsMoved(TokenId,uint128,uint256) (contracts/libraries/PanopticMath.sol#574-599) does not validate following parameters:- 
	- PanopticMath.getAmountsMoved(TokenId,uint128,uint256).tokenId (contracts/libraries/PanopticMath.sol#575)
	- PanopticMath.getAmountsMoved(TokenId,uint128,uint256).legIndex (contracts/libraries/PanopticMath.sol#577)

/// @audit ************** Possible Issue Line(s) **************
	L#575,  L#577,  

/// @audit ****************** Affected Code *******************
 575:         TokenId tokenId,
 577:         uint256 legIndex

```

*GitHub* : [574-599](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L574-L599)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralAtUtilization(uint128,uint256,int256) (contracts/CollateralTracker.sol#1473-1499) does not validate following parameters:- 
	- CollateralTracker._getRequiredCollateralAtUtilization(uint128,uint256,int256).isLong (contracts/CollateralTracker.sol#1475)

/// @audit ************** Possible Issue Line(s) **************
	L#1475,  

/// @audit ****************** Affected Code *******************
1475:         uint256 isLong,

```

*GitHub* : [1473-1499](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1473-L1499)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.minePoolAddress(bytes32,uint256,uint256) (contracts/PanopticFactory.sol#290-326) does not validate following parameters:- 
	- PanopticFactory.minePoolAddress(bytes32,uint256,uint256).salt (contracts/PanopticFactory.sol#291)
	- PanopticFactory.minePoolAddress(bytes32,uint256,uint256).minTargetRarity (contracts/PanopticFactory.sol#293)

/// @audit ************** Possible Issue Line(s) **************
	L#291,  L#293,  

/// @audit ****************** Affected Code *******************
 291:         bytes32 salt,
 293:         uint256 minTargetRarity

```

*GitHub* : [290-326](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L290-L326)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.min(uint256,uint256) (contracts/libraries/Math.sol#41-43) does not validate following parameters:- 
	- Math.min(uint256,uint256).a (contracts/libraries/Math.sol#41)
	- Math.min(uint256,uint256).b (contracts/libraries/Math.sol#41)

/// @audit ************** Possible Issue Line(s) **************
	L#41,  

/// @audit ****************** Affected Code *******************
  41:     function min(uint256 a, uint256 b) internal pure returns (uint256) {
  42:         return a < b ? a : b;
  43:     }

```

*GitHub* : [41-43](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L41-L43)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.redeem(uint256,address,address) (contracts/CollateralTracker.sol#591-626) does not validate following parameters:- 
	- CollateralTracker.redeem(uint256,address,address).shares (contracts/CollateralTracker.sol#592)
	- CollateralTracker.redeem(uint256,address,address).owner (contracts/CollateralTracker.sol#594)

/// @audit ************** Possible Issue Line(s) **************
	L#592,  L#594,  

/// @audit ****************** Affected Code *******************
 592:         uint256 shares,
 594:         address owner

```

*GitHub* : [591-626](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L591-L626)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv128RoundingUp(uint256,uint256) (contracts/libraries/Math.sol#661-669) does not validate following parameters:- 
	- Math.mulDiv128RoundingUp(uint256,uint256).a (contracts/libraries/Math.sol#661)
	- Math.mulDiv128RoundingUp(uint256,uint256).b (contracts/libraries/Math.sol#661)

/// @audit ************** Possible Issue Line(s) **************
	L#661,  

/// @audit ****************** Affected Code *******************
 661:     function mulDiv128RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
 662:         unchecked {
 663:             result = mulDiv128(a, b);
 664:             if (mulmod(a, b, 2 ** 128) > 0) {
 665:                 require(result < type(uint256).max);
 666:                 result++;
 667:             }
 668:         }
 669:     }

```

*GitHub* : [661-669](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L661-L669)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.updatePositionsHash(uint256,TokenId,bool) (contracts/libraries/PanopticMath.sol#92-110) does not validate following parameters:- 
	- PanopticMath.updatePositionsHash(uint256,TokenId,bool).addFlag (contracts/libraries/PanopticMath.sol#95)

/// @audit ************** Possible Issue Line(s) **************
	L#95,  

/// @audit ****************** Affected Code *******************
  92:     function updatePositionsHash(
  93:         uint256 existingHash,
  94:         TokenId tokenId,
  95:         bool addFlag
  96:     ) internal pure returns (uint256) {
  97:         // add the XOR`ed hash of the single option position `tokenId` to the `existingHash`
  98:         // @dev 0 ^ x = x
  99: 
 100:         unchecked {
 101:             // update hash by taking the XOR of the new tokenId
 102:             uint248 updatedHash = uint248(existingHash) ^
 103:                 (uint248(uint256(keccak256(abi.encode(tokenId)))));
 104:             // increment the top 8 bit if addflag=true, decrement otherwise
 105:             return
 106:                 addFlag
 107:                     ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)
 108:                     : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);
 109:         }
 110:     }

```

*GitHub* : [92-110](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L92-L110)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.toInt256(uint256) (contracts/libraries/Math.sol#325-328) does not validate following parameters:- 
	- Math.toInt256(uint256).toCast (contracts/libraries/Math.sol#325)

/// @audit ************** Possible Issue Line(s) **************
	L#325,  

/// @audit ****************** Affected Code *******************
 325:     function toInt256(uint256 toCast) internal pure returns (int256) {
 326:         if (toCast > uint256(type(int256).max)) revert Errors.CastingError();
 327:         return int256(toCast);
 328:     }

```

*GitHub* : [325-328](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L325-L328)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,uint160) (contracts/libraries/PanopticMath.sol#419-436) does not validate following parameters:- 
	- PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,uint160).tokenType (contracts/libraries/PanopticMath.sol#422)

/// @audit ************** Possible Issue Line(s) **************
	L#422,  

/// @audit ****************** Affected Code *******************
 419:     function convertCollateralData(
 420:         LeftRightUnsigned tokenData0,
 421:         LeftRightUnsigned tokenData1,
 422:         uint256 tokenType,
 423:         uint160 sqrtPriceX96
 424:     ) internal pure returns (uint256, uint256) {
 425:         if (tokenType == 0) {
 426:             return (
 427:                 tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
 428:                 tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
 429:             );
 430:         } else {
 431:             return (
 432:                 tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
 433:                 tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
 434:             );
 435:         }
 436:     }

```

*GitHub* : [419-436](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L419-L436)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.balanceOfBatch(address[],uint256[]) (contracts/tokens/ERC1155Minimal.sol#178-191) does not validate following parameters:- 
	- ERC1155.balanceOfBatch(address[],uint256[]).owners (contracts/tokens/ERC1155Minimal.sol#179)

/// @audit ************** Possible Issue Line(s) **************
	L#179,  

/// @audit ****************** Affected Code *******************
 178:     function balanceOfBatch(
 179:         address[] calldata owners,
 180:         uint256[] calldata ids
 181:     ) public view returns (uint256[] memory balances) {
 182:         balances = new uint256[](owners.length);
 183: 
 184:         // Unchecked because the only math done is incrementing
 185:         // the array index counter which cannot possibly overflow.
 186:         unchecked {
 187:             for (uint256 i = 0; i < owners.length; ++i) {
 188:                 balances[i] = balanceOf[owners[i]][ids[i]];
 189:             }
 190:         }
 191:     }

```

*GitHub* : [178-191](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L178-L191)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128) (contracts/PanopticPool.sol#1666-1746) does not validate following parameters:- 
	- PanopticPool._updateSettlementPostMint(TokenId,LeftRightUnsigned[4],uint128).tokenId (contracts/PanopticPool.sol#1667)

/// @audit ************** Possible Issue Line(s) **************
	L#1667,  

/// @audit ****************** Affected Code *******************
1667:         TokenId tokenId,

```

*GitHub* : [1666-1746](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1666-L1746)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.settleLongPremium(TokenId[],address,uint256) (contracts/PanopticPool.sol#1587-1659) does not validate following parameters:- 
	- PanopticPool.settleLongPremium(TokenId[],address,uint256).legIndex (contracts/PanopticPool.sol#1590)

/// @audit ************** Possible Issue Line(s) **************
	L#1590,  

/// @audit ****************** Affected Code *******************
1590:         uint256 legIndex

```

*GitHub* : [1587-1659](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1659)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

/// @audit ******************* Issue Detail *******************
ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes) (contracts/tokens/ERC1155Minimal.sol#130-171) does not validate following parameters:- 
	- ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes).from (contracts/tokens/ERC1155Minimal.sol#131)
	- ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes).to (contracts/tokens/ERC1155Minimal.sol#132)
	- ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes).ids (contracts/tokens/ERC1155Minimal.sol#133)
	- ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes).amounts (contracts/tokens/ERC1155Minimal.sol#134)
	- ERC1155.safeBatchTransferFrom(address,address,uint256[],uint256[],bytes).data (contracts/tokens/ERC1155Minimal.sol#135)

/// @audit ************** Possible Issue Line(s) **************
	L#131,  L#132,  L#133,  L#134,  L#135,  

/// @audit ****************** Affected Code *******************
 131:         address from,
 132:         address to,
 133:         uint256[] calldata ids,
 134:         uint256[] calldata amounts,
 135:         bytes calldata data

```

*GitHub* : [130-171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L130-L171)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.withdraw(uint256,address,address) (contracts/CollateralTracker.sol#531-566) does not validate following parameters:- 
	- CollateralTracker.withdraw(uint256,address,address).assets (contracts/CollateralTracker.sol#532)
	- CollateralTracker.withdraw(uint256,address,address).owner (contracts/CollateralTracker.sol#534)

/// @audit ************** Possible Issue Line(s) **************
	L#532,  L#534,  

/// @audit ****************** Affected Code *******************
 532:         uint256 assets,
 534:         address owner

```

*GitHub* : [531-566](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L531-L566)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._calculateAccumulatedPremia(address,TokenId[],bool,bool,int24) (contracts/PanopticPool.sol#429-492) does not validate following parameters:- 
	- PanopticPool._calculateAccumulatedPremia(address,TokenId[],bool,bool,int24).includePendingPremium (contracts/PanopticPool.sol#433)

/// @audit ************** Possible Issue Line(s) **************
	L#433,  

/// @audit ****************** Affected Code *******************
 433:         bool includePendingPremium,

```

*GitHub* : [429-492](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L429-L492)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._burnAllOptionsFrom(address,int24,int24,bool,TokenId[]) (contracts/PanopticPool.sol#794-816) does not validate following parameters:- 
	- PanopticPool._burnAllOptionsFrom(address,int24,int24,bool,TokenId[]).positionIdList (contracts/PanopticPool.sol#799)

/// @audit ************** Possible Issue Line(s) **************
	L#799,  

/// @audit ****************** Affected Code *******************
 794:     function _burnAllOptionsFrom(
 795:         address owner,
 796:         int24 tickLimitLow,
 797:         int24 tickLimitHigh,
 798:         bool commitLongSettled,
 799:         TokenId[] calldata positionIdList
 800:     ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {
 801:         premiasByLeg = new LeftRightSigned[4][](positionIdList.length);
 802:         for (uint256 i = 0; i < positionIdList.length; ) {
 803:             LeftRightSigned paidAmounts;
 804:             (paidAmounts, premiasByLeg[i]) = _burnOptions(
 805:                 commitLongSettled,
 806:                 positionIdList[i],
 807:                 owner,
 808:                 tickLimitLow,
 809:                 tickLimitHigh
 810:             );
 811:             netPaid = netPaid.add(paidAmounts);
 812:             unchecked {
 813:                 ++i;
 814:             }
 815:         }
 816:     }

```

*GitHub* : [794-816](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L794-L816)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convert1to0(uint256,uint160) (contracts/libraries/PanopticMath.sol#507-517) does not validate following parameters:- 
	- PanopticMath.convert1to0(uint256,uint160).sqrtPriceX96 (contracts/libraries/PanopticMath.sol#507)

/// @audit ************** Possible Issue Line(s) **************
	L#507,  

/// @audit ****************** Affected Code *******************
 507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {
 508:         unchecked {
 509:             // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
 510:             // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
 511:             if (sqrtPriceX96 < type(uint128).max) {
 512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
 513:             } else {
 514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
 515:             }
 516:         }
 517:     }

```

*GitHub* : [507-517](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L507-L517)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager._validateAndForwardToAMM(TokenId,uint128,int24,int24,bool) (contracts/SemiFungiblePositionManager.sol#680-729) does not validate following parameters:- 
	- SemiFungiblePositionManager._validateAndForwardToAMM(TokenId,uint128,int24,int24,bool).positionSize (contracts/SemiFungiblePositionManager.sol#682)
	- SemiFungiblePositionManager._validateAndForwardToAMM(TokenId,uint128,int24,int24,bool).tickLimitLow (contracts/SemiFungiblePositionManager.sol#683)
	- SemiFungiblePositionManager._validateAndForwardToAMM(TokenId,uint128,int24,int24,bool).tickLimitHigh (contracts/SemiFungiblePositionManager.sol#684)
	- SemiFungiblePositionManager._validateAndForwardToAMM(TokenId,uint128,int24,int24,bool).isBurn (contracts/SemiFungiblePositionManager.sol#685)

/// @audit ************** Possible Issue Line(s) **************
	L#682,  L#683,  L#684,  L#685,  

/// @audit ****************** Affected Code *******************
 682:         uint128 positionSize,
 683:         int24 tickLimitLow,
 684:         int24 tickLimitHigh,
 685:         bool isBurn

```

*GitHub* : [680-729](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L680-L729)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256) (contracts/libraries/PanopticMath.sol#125-157) does not validate following parameters:- 
	- PanopticMath.computeMedianObservedPrice(IUniswapV3Pool,uint256,uint256,uint256,uint256).cardinality (contracts/libraries/PanopticMath.sol#129)

/// @audit ************** Possible Issue Line(s) **************
	L#129,  

/// @audit ****************** Affected Code *******************
 129:         uint256 cardinality,

```

*GitHub* : [125-157](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L125-L157)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._getPremia(TokenId,uint128,address,bool,int24) (contracts/PanopticPool.sol#1503-1575) does not validate following parameters:- 
	- PanopticPool._getPremia(TokenId,uint128,address,bool,int24).computeAllPremia (contracts/PanopticPool.sol#1507)

/// @audit ************** Possible Issue Line(s) **************
	L#1507,  

/// @audit ****************** Affected Code *******************
1507:         bool computeAllPremia,

```

*GitHub* : [1503-1575](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1503-L1575)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.maxWithdraw(address) (contracts/CollateralTracker.sol#507-513) does not validate following parameters:- 
	- CollateralTracker.maxWithdraw(address).owner (contracts/CollateralTracker.sol#507)

/// @audit ************** Possible Issue Line(s) **************
	L#507,  

/// @audit ****************** Affected Code *******************
 507:     function maxWithdraw(address owner) public view returns (uint256 maxAssets) {
 508:         // We can only use the standard 4626 withdraw function if the user has no open positions
 509:         // For the sake of simplicity assets can only be withdrawn through the redeem function
 510:         uint256 available = s_poolAssets;
 511:         uint256 balance = convertToAssets(balanceOf[owner]);
 512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;
 513:     }

```

*GitHub* : [507-513](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L507-L513)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDivRoundingUp(uint256,uint256,uint256) (contracts/libraries/Math.sol#440-452) does not validate following parameters:- 
	- Math.mulDivRoundingUp(uint256,uint256,uint256).a (contracts/libraries/Math.sol#441)
	- Math.mulDivRoundingUp(uint256,uint256,uint256).b (contracts/libraries/Math.sol#442)
	- Math.mulDivRoundingUp(uint256,uint256,uint256).denominator (contracts/libraries/Math.sol#443)

/// @audit ************** Possible Issue Line(s) **************
	L#441,  L#442,  L#443,  

/// @audit ****************** Affected Code *******************
 440:     function mulDivRoundingUp(
 441:         uint256 a,
 442:         uint256 b,
 443:         uint256 denominator
 444:     ) internal pure returns (uint256 result) {
 445:         unchecked {
 446:             result = mulDiv(a, b, denominator);
 447:             if (mulmod(a, b, denominator) > 0) {
 448:                 require(result < type(uint256).max);
 449:                 result++;
 450:             }
 451:         }
 452:     }

```

*GitHub* : [440-452](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L440-L452)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) does not validate following parameters:- 
	- Math.mulDiv(uint256,uint256,uint256).denominator (contracts/libraries/Math.sol#343)

/// @audit ************** Possible Issue Line(s) **************
	L#343,  

/// @audit ****************** Affected Code *******************
 343:         uint256 denominator

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool._updatePositionDataBurn(address,TokenId) (contracts/PanopticPool.sol#859-878) does not validate following parameters:- 
	- PanopticPool._updatePositionDataBurn(address,TokenId).tokenId (contracts/PanopticPool.sol#859)

/// @audit ************** Possible Issue Line(s) **************
	L#859,  

/// @audit ****************** Affected Code *******************
 859:     function _updatePositionDataBurn(address owner, TokenId tokenId) internal {
 860:         // reset balances and delete stored option data
 861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);
 862: 
 863:         uint256 numLegs = tokenId.countLegs();
 864:         for (uint256 leg = 0; leg < numLegs; ) {
 865:             if (tokenId.isLong(leg) == 0) {
 866:                 // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
 867:                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
 868:                 _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
 869:             }
 870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
 871:             unchecked {
 872:                 ++leg;
 873:             }
 874:         }
 875: 
 876:         // Update the position list hash (hash = XOR of all keccak256(tokenId)). Remove hash by XOR'ing again
 877:         _updatePositionsHash(owner, tokenId, !ADD);
 878:     }

```

*GitHub* : [859-878](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L859-L878)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.safeTransferFrom(address,address,uint256,uint256,bytes) (contracts/SemiFungiblePositionManager.sol#540-556) does not validate following parameters:- 
	- SemiFungiblePositionManager.safeTransferFrom(address,address,uint256,uint256,bytes).id (contracts/SemiFungiblePositionManager.sol#543)

/// @audit ************** Possible Issue Line(s) **************
	L#543,  

/// @audit ****************** Affected Code *******************
 540:     function safeTransferFrom(
 541:         address from,
 542:         address to,
 543:         uint256 id,
 544:         uint256 amount,
 545:         bytes calldata data
 546:     ) public override {
 547:         // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
 548:         // so just check if there is an active reentrancy lock for the relevant pool on the token we're transferring
 549:         if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();
 550: 
 551:         // update the position data
 552:         registerTokenTransfer(from, to, TokenId.wrap(id), amount);
 553: 
 554:         // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)
 555:         super.safeTransferFrom(from, to, id, amount, data);
 556:     }

```

*GitHub* : [540-556](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L540-L556)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.startToken(bool,address,address,uint24,PanopticPool) (contracts/CollateralTracker.sol#221-264) does not validate following parameters:- 
	- CollateralTracker.startToken(bool,address,address,uint24,PanopticPool).underlyingIsToken0 (contracts/CollateralTracker.sol#222)

/// @audit ************** Possible Issue Line(s) **************
	L#222,  

/// @audit ****************** Affected Code *******************
 222:         bool underlyingIsToken0,

```

*GitHub* : [221-264](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L221-L264)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getRequiredCollateralSingleLeg(TokenId,uint256,uint128,int24,uint128) (contracts/CollateralTracker.sol#1278-1301) does not validate following parameters:- 
	- CollateralTracker._getRequiredCollateralSingleLeg(TokenId,uint256,uint128,int24,uint128).tokenId (contracts/CollateralTracker.sol#1279)
	- CollateralTracker._getRequiredCollateralSingleLeg(TokenId,uint256,uint128,int24,uint128).index (contracts/CollateralTracker.sol#1280)

/// @audit ************** Possible Issue Line(s) **************
	L#1279,  L#1280,  

/// @audit ****************** Affected Code *******************
1278:     function _getRequiredCollateralSingleLeg(
1279:         TokenId tokenId,
1280:         uint256 index,
1281:         uint128 positionSize,
1282:         int24 atTick,
1283:         uint128 poolUtilization
1284:     ) internal view returns (uint256 required) {
1285:         return
1286:             tokenId.riskPartner(index) == index // does this leg have a risk partner? Affects required collateral
1287:                 ? _getRequiredCollateralSingleLegNoPartner(
1288:                     tokenId,
1289:                     index,
1290:                     positionSize,
1291:                     atTick,
1292:                     poolUtilization
1293:                 )
1294:                 : _getRequiredCollateralSingleLegPartner(
1295:                     tokenId,
1296:                     index,
1297:                     positionSize,
1298:                     atTick,
1299:                     poolUtilization
1300:                 );
1301:     }

```

*GitHub* : [1278-1301](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1278-L1301)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.assertPriceWithinBounds(uint160,uint160) (contracts/PanopticPool.sol#338-344) does not validate following parameters:- 
	- PanopticPool.assertPriceWithinBounds(uint160,uint160).sqrtLowerBound (contracts/PanopticPool.sol#338)
	- PanopticPool.assertPriceWithinBounds(uint160,uint160).sqrtUpperBound (contracts/PanopticPool.sol#338)

/// @audit ************** Possible Issue Line(s) **************
	L#338,  

/// @audit ****************** Affected Code *******************
 338:     function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {
 339:         (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();
 340: 
 341:         if (currentSqrtPriceX96 <= sqrtLowerBound || currentSqrtPriceX96 >= sqrtUpperBound) {
 342:             revert Errors.PriceBoundFail();
 343:         }
 344:     }

```

*GitHub* : [338-344](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L338-L344)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.deposit(uint256,address) (contracts/CollateralTracker.sol#417-440) does not validate following parameters:- 
	- CollateralTracker.deposit(uint256,address).assets (contracts/CollateralTracker.sol#417)

/// @audit ************** Possible Issue Line(s) **************
	L#417,  

/// @audit ****************** Affected Code *******************
 417:     function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
 418:         if (assets > type(uint104).max) revert Errors.DepositTooLarge();
 419: 
 420:         shares = previewDeposit(assets);
 421: 
 422:         // transfer assets (underlying token funds) from the user/the LP to the PanopticPool
 423:         // in return for the shares to be minted
 424:         SafeTransferLib.safeTransferFrom(
 425:             s_underlyingToken,
 426:             msg.sender,
 427:             address(s_panopticPool),
 428:             assets
 429:         );
 430: 
 431:         // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
 432:         _mint(receiver, shares);
 433: 
 434:         // update tracked asset balance
 435:         unchecked {
 436:             s_poolAssets += uint128(assets);
 437:         }
 438: 
 439:         emit Deposit(msg.sender, receiver, assets, shares);
 440:     }

```

*GitHub* : [417-440](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L417-L440)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.beginReentrancyLock(uint64) (contracts/SemiFungiblePositionManager.sol#320-326) does not validate following parameters:- 
	- SemiFungiblePositionManager.beginReentrancyLock(uint64).poolId (contracts/SemiFungiblePositionManager.sol#320)

/// @audit ************** Possible Issue Line(s) **************
	L#320,  

/// @audit ****************** Affected Code *******************
 320:     function beginReentrancyLock(uint64 poolId) internal {
 321:         // check if the pool is already locked, if so, revert
 322:         if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();
 323: 
 324:         // activate lock
 325:         s_poolContext[poolId].locked = true;
 326:     }

```

*GitHub* : [320-326](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L320-L326)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
SemiFungiblePositionManager.uniswapV3SwapCallback(int256,int256,bytes) (contracts/SemiFungiblePositionManager.sol#435-457) does not validate following parameters:- 
	- SemiFungiblePositionManager.uniswapV3SwapCallback(int256,int256,bytes).amount0Delta (contracts/SemiFungiblePositionManager.sol#436)

/// @audit ************** Possible Issue Line(s) **************
	L#436,  

/// @audit ****************** Affected Code *******************
 435:     function uniswapV3SwapCallback(
 436:         int256 amount0Delta,
 437:         int256 amount1Delta,
 438:         bytes calldata data
 439:     ) external {
 440:         // Decode the swap callback data, checks that the UniswapV3Pool has the correct address.
 441:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));
 442:         // Validate caller to ensure we got called from the AMM pool
 443:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);
 444: 
 445:         // Extract the address of the token to be sent (amount0 -> token0, amount1 -> token1)
 446:         address token = amount0Delta > 0
 447:             ? address(decoded.poolFeatures.token0)
 448:             : address(decoded.poolFeatures.token1);
 449: 
 450:         // Transform the amount to pay to uint256 (take positive one from amount0 and amount1)
 451:         // the pool will always pass one delta with a positive sign and one with a negative sign or zero,
 452:         // so this logic always picks the correct delta to pay
 453:         uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);
 454: 
 455:         // Pay the required token from the payer to the caller of this contract
 456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);
 457:     }

```

*GitHub* : [435-457](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L435-L457)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convertNotional(uint128,int24,int24,uint256) (contracts/libraries/PanopticMath.sol#468-483) does not validate following parameters:- 
	- PanopticMath.convertNotional(uint128,int24,int24,uint256).asset (contracts/libraries/PanopticMath.sol#472)

/// @audit ************** Possible Issue Line(s) **************
	L#472,  

/// @audit ****************** Affected Code *******************
 468:     function convertNotional(
 469:         uint128 contractSize,
 470:         int24 tickLower,
 471:         int24 tickUpper,
 472:         uint256 asset
 473:     ) internal pure returns (uint128) {
 474:         unchecked {
 475:             uint256 notional = asset == 0
 476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))
 477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));
 478: 
 479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();
 480: 
 481:             return uint128(notional);
 482:         }
 483:     }

```

*GitHub* : [468-483](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L468-L483)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool) (contracts/libraries/PanopticMath.sol#168-233) does not validate following parameters:- 
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).period (contracts/libraries/PanopticMath.sol#171)
	- PanopticMath.computeInternalMedian(uint256,uint256,uint256,uint256,IUniswapV3Pool).medianData (contracts/libraries/PanopticMath.sol#172)

/// @audit ************** Possible Issue Line(s) **************
	L#171,  L#172,  

/// @audit ****************** Affected Code *******************
 171:         uint256 period,
 172:         uint256 medianData,

```

*GitHub* : [168-233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L233)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker._getAccountMargin(address,int24,uint256[2][],int128) (contracts/CollateralTracker.sol#1159-1193) does not validate following parameters:- 
	- CollateralTracker._getAccountMargin(address,int24,uint256[2][],int128).positionBalanceArray (contracts/CollateralTracker.sol#1162)
	- CollateralTracker._getAccountMargin(address,int24,uint256[2][],int128).premiumAllPositions (contracts/CollateralTracker.sol#1163)

/// @audit ************** Possible Issue Line(s) **************
	L#1162,  L#1163,  

/// @audit ****************** Affected Code *******************
1162:         uint256[2][] memory positionBalanceArray,
1163:         int128 premiumAllPositions

```

*GitHub* : [1159-1193](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1159-L1193)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
PanopticFactory.uniswapV3MintCallback(uint256,uint256,bytes) (contracts/PanopticFactory.sol#172-195) does not validate following parameters:- 
	- PanopticFactory.uniswapV3MintCallback(uint256,uint256,bytes).amount0Owed (contracts/PanopticFactory.sol#173)
	- PanopticFactory.uniswapV3MintCallback(uint256,uint256,bytes).amount1Owed (contracts/PanopticFactory.sol#174)

/// @audit ************** Possible Issue Line(s) **************
	L#173,  L#174,  

/// @audit ****************** Affected Code *******************
 172:     function uniswapV3MintCallback(
 173:         uint256 amount0Owed,
 174:         uint256 amount1Owed,
 175:         bytes calldata data
 176:     ) external {
 177:         CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));
 178: 
 179:         CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);
 180: 
 181:         if (amount0Owed > 0)
 182:             SafeTransferLib.safeTransferFrom(
 183:                 decoded.poolFeatures.token0,
 184:                 decoded.payer,
 185:                 msg.sender,
 186:                 amount0Owed
 187:             );
 188:         if (amount1Owed > 0)
 189:             SafeTransferLib.safeTransferFrom(
 190:                 decoded.poolFeatures.token1,
 191:                 decoded.payer,
 192:                 msg.sender,
 193:                 amount1Owed
 194:             );
 195:     }

```

*GitHub* : [172-195](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L172-L195)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker.refund(address,address,int256) (contracts/CollateralTracker.sol#975-983) does not validate following parameters:- 
	- CollateralTracker.refund(address,address,int256).assets (contracts/CollateralTracker.sol#975)

/// @audit ************** Possible Issue Line(s) **************
	L#975,  

/// @audit ****************** Affected Code *******************
 975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {
 976:         if (assets > 0) {
 977:             _transferFrom(refunder, refundee, convertToShares(uint256(assets)));
 978:         } else {
 979:             unchecked {
 980:                 _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));
 981:             }
 982:         }
 983:     }

```

*GitHub* : [975-983](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L975-L983)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)) (contracts/libraries/PanopticMath.sol#768-908) does not validate following parameters:- 
	- PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).positionIdList (contracts/libraries/PanopticMath.sol#770)

/// @audit ************** Possible Issue Line(s) **************
	L#770,  

/// @audit ****************** Affected Code *******************
 770:         TokenId[] memory positionIdList,

```

*GitHub* : [768-908](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L908)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.toInt128(uint128) (contracts/libraries/Math.sol#311-313) does not validate following parameters:- 
	- Math.toInt128(uint128).toCast (contracts/libraries/Math.sol#311)

/// @audit ************** Possible Issue Line(s) **************
	L#311,  

/// @audit ****************** Affected Code *******************
 311:     function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {
 312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();
 313:     }

```

*GitHub* : [311-313](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L311-L313)

### [N-05]<a name="n-05"></a> Assembly usage

The use of assembly is error-prone and should be avoided.  **Recom:** Do not use `evm` assembly.

*There are 9 instance(s) of this issue:*

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv(uint256,uint256,uint256) (contracts/libraries/Math.sol#340-433) uses assembly
	- INLINE ASM (contracts/libraries/Math.sol#353-357)
	- INLINE ASM (contracts/libraries/Math.sol#362-364)
	- INLINE ASM (contracts/libraries/Math.sol#379-381)
	- INLINE ASM (contracts/libraries/Math.sol#383-386)
	- INLINE ASM (contracts/libraries/Math.sol#393-395)
	- INLINE ASM (contracts/libraries/Math.sol#398-400)
	- INLINE ASM (contracts/libraries/Math.sol#404-406)

/// @audit ************** Possible Issue Line(s) **************
	L#353-357,  L#362-364,  L#379-381,  L#383-386,  L#393-395,  L#398-400,  L#404-406,  

/// @audit ****************** Affected Code *******************
 353:             assembly ("memory-safe") {
 354:                 let mm := mulmod(a, b, not(0))
 355:                 prod0 := mul(a, b)
 356:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
 357:             }
 362:                 assembly ("memory-safe") {
 363:                     result := div(prod0, denominator)
 364:                 }
 379:             assembly ("memory-safe") {
 380:                 remainder := mulmod(a, b, denominator)
 381:             }
 383:             assembly ("memory-safe") {
 384:                 prod1 := sub(prod1, gt(remainder, prod0))
 385:                 prod0 := sub(prod0, remainder)
 386:             }
 393:             assembly ("memory-safe") {
 394:                 denominator := div(denominator, twos)
 395:             }
 398:             assembly ("memory-safe") {
 399:                 prod0 := div(prod0, twos)
 400:             }
 404:             assembly ("memory-safe") {
 405:                 twos := add(div(sub(0, twos), twos), 1)
 406:             }

```

*GitHub* : [340-433](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L433)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.unsafeDivRoundingUp(uint256,uint256) (contracts/libraries/Math.sol#738-742) uses assembly
	- INLINE ASM (contracts/libraries/Math.sol#739-741)

/// @audit ************** Possible Issue Line(s) **************
	L#739-741,  

/// @audit ****************** Affected Code *******************
 738:     function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
 739:         assembly ("memory-safe") {
 740:             result := add(div(a, b), gt(mod(a, b), 0))
 741:         }
 742:     }

```

*GitHub* : [738-742](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L738-L742)

```solidity
File: contracts/libraries/SafeTransferLib.sol

/// @audit ******************* Issue Detail *******************
SafeTransferLib.safeTransfer(address,address,uint256) (contracts/libraries/SafeTransferLib.sol#52-76) uses assembly
	- INLINE ASM (contracts/libraries/SafeTransferLib.sol#55-73)

/// @audit ************** Possible Issue Line(s) **************
	L#55-73,  

/// @audit ****************** Affected Code *******************
  52:     function safeTransfer(address token, address to, uint256 amount) internal {
  53:         bool success;
  54: 
  55:         assembly ("memory-safe") {
  56:             // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
  57:             let p := mload(0x40)
  58: 
  59:             // Write the abi-encoded calldata into memory, beginning with the function selector.
  60:             mstore(p, 0xa9059cbb00000000000000000000000000000000000000000000000000000000)
  61:             mstore(add(4, p), to) // Append the "to" argument.
  62:             mstore(add(36, p), amount) // Append the "amount" argument.
  63: 
  64:             success := and(
  65:                 // Set success to whether the call reverted, if not we check it either
  66:                 // returned exactly 1 (can't just be non-zero data), or had no return data.
  67:                 or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
  68:                 // We use 68 because that's the total length of our calldata (4 + 32 * 2)
  69:                 // Counterintuitively, this call() must be positioned after the or() in the
  70:                 // surrounding and() because and() evaluates its arguments from right to left.
  71:                 call(gas(), token, 0, p, 68, 0, 32)
  72:             )
  73:         }
  74: 
  75:         if (!success) revert Errors.TransferFailed();
  76:     }

```

*GitHub* : [52-76](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L52-L76)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv192(uint256,uint256) (contracts/libraries/Math.sol#675-732) uses assembly
	- INLINE ASM (contracts/libraries/Math.sol#684-688)
	- INLINE ASM (contracts/libraries/Math.sol#693-696)
	- INLINE ASM (contracts/libraries/Math.sol#710-712)
	- INLINE ASM (contracts/libraries/Math.sol#714-717)
	- INLINE ASM (contracts/libraries/Math.sol#720-723)

/// @audit ************** Possible Issue Line(s) **************
	L#684-688,  L#693-696,  L#710-712,  L#714-717,  L#720-723,  

/// @audit ****************** Affected Code *******************
 684:             assembly ("memory-safe") {
 685:                 let mm := mulmod(a, b, not(0))
 686:                 prod0 := mul(a, b)
 687:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
 688:             }
 693:                 assembly ("memory-safe") {
 694:                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 695:                     res := shr(192, prod0)
 696:                 }
 710:             assembly ("memory-safe") {
 711:                 remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)
 712:             }
 714:             assembly ("memory-safe") {
 715:                 prod1 := sub(prod1, gt(remainder, prod0))
 716:                 prod0 := sub(prod0, remainder)
 717:             }
 720:             assembly ("memory-safe") {
 721:                 // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 722:                 prod0 := shr(192, prod0)
 723:             }

```

*GitHub* : [675-732](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L675-L732)

```solidity
File: contracts/libraries/SafeTransferLib.sol

/// @audit ******************* Issue Detail *******************
SafeTransferLib.safeTransferFrom(address,address,address,uint256) (contracts/libraries/SafeTransferLib.sol#21-46) uses assembly
	- INLINE ASM (contracts/libraries/SafeTransferLib.sol#24-43)

/// @audit ************** Possible Issue Line(s) **************
	L#24-43,  

/// @audit ****************** Affected Code *******************
  24:         assembly ("memory-safe") {
  25:             // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
  26:             let p := mload(0x40)
  27: 
  28:             // Write the abi-encoded calldata into memory, beginning with the function selector.
  29:             mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)
  30:             mstore(add(4, p), from) // Append the "from" argument.
  31:             mstore(add(36, p), to) // Append the "to" argument.
  32:             mstore(add(68, p), amount) // Append the "amount" argument.
  33: 
  34:             success := and(
  35:                 // Set success to whether the call reverted, if not we check it either
  36:                 // returned exactly 1 (can't just be non-zero data), or had no return data.
  37:                 or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
  38:                 // We use 100 because that's the total length of our calldata (4 + 32 * 3)
  39:                 // Counterintuitively, this call() must be positioned after the or() in the
  40:                 // surrounding and() because and() evaluates its arguments from right to left.
  41:                 call(gas(), token, 0, p, 100, 0, 32)
  42:             )
  43:         }

```

*GitHub* : [21-46](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L21-L46)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv128(uint256,uint256) (contracts/libraries/Math.sol#598-655) uses assembly
	- INLINE ASM (contracts/libraries/Math.sol#607-611)
	- INLINE ASM (contracts/libraries/Math.sol#616-619)
	- INLINE ASM (contracts/libraries/Math.sol#633-635)
	- INLINE ASM (contracts/libraries/Math.sol#637-640)
	- INLINE ASM (contracts/libraries/Math.sol#643-646)

/// @audit ************** Possible Issue Line(s) **************
	L#607-611,  L#616-619,  L#633-635,  L#637-640,  L#643-646,  

/// @audit ****************** Affected Code *******************
 607:             assembly ("memory-safe") {
 608:                 let mm := mulmod(a, b, not(0))
 609:                 prod0 := mul(a, b)
 610:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
 611:             }
 616:                 assembly ("memory-safe") {
 617:                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 618:                     res := shr(128, prod0)
 619:                 }
 633:             assembly ("memory-safe") {
 634:                 remainder := mulmod(a, b, 0x100000000000000000000000000000000)
 635:             }
 637:             assembly ("memory-safe") {
 638:                 prod1 := sub(prod1, gt(remainder, prod0))
 639:                 prod0 := sub(prod0, remainder)
 640:             }
 643:             assembly ("memory-safe") {
 644:                 // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 645:                 prod0 := shr(128, prod0)
 646:             }

```

*GitHub* : [598-655](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L598-L655)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv96(uint256,uint256) (contracts/libraries/Math.sol#521-578) uses assembly
	- INLINE ASM (contracts/libraries/Math.sol#530-534)
	- INLINE ASM (contracts/libraries/Math.sol#539-542)
	- INLINE ASM (contracts/libraries/Math.sol#556-558)
	- INLINE ASM (contracts/libraries/Math.sol#560-563)
	- INLINE ASM (contracts/libraries/Math.sol#566-569)

/// @audit ************** Possible Issue Line(s) **************
	L#530-534,  L#539-542,  L#556-558,  L#560-563,  L#566-569,  

/// @audit ****************** Affected Code *******************
 530:             assembly ("memory-safe") {
 531:                 let mm := mulmod(a, b, not(0))
 532:                 prod0 := mul(a, b)
 533:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
 534:             }
 539:                 assembly ("memory-safe") {
 540:                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 541:                     res := shr(96, prod0)
 542:                 }
 556:             assembly ("memory-safe") {
 557:                 remainder := mulmod(a, b, 0x1000000000000000000000000)
 558:             }
 560:             assembly ("memory-safe") {
 561:                 prod1 := sub(prod1, gt(remainder, prod0))
 562:                 prod0 := sub(prod0, remainder)
 563:             }
 566:             assembly ("memory-safe") {
 567:                 // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 568:                 prod0 := shr(96, prod0)
 569:             }

```

*GitHub* : [521-578](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L521-L578)

```solidity
File: contracts/multicall/Multicall.sol

/// @audit ******************* Issue Detail *******************
Multicall.multicall(bytes[]) (contracts/multicall/Multicall.sol#12-36) uses assembly
	- INLINE ASM (contracts/multicall/Multicall.sol#25-27)

/// @audit ************** Possible Issue Line(s) **************
	L#25-27,  

/// @audit ****************** Affected Code *******************
  12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
  13:         results = new bytes[](data.length);
  14:         for (uint256 i = 0; i < data.length; ) {
  15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);
  16: 
  17:             if (!success) {
  18:                 // Bubble up the revert reason
  19:                 // The bytes type is ABI encoded as a length-prefixed byte array
  20:                 // So we simply need to add 32 to the pointer to get the start of the data
  21:                 // And then revert with the size loaded from the first 32 bytes
  22:                 // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
  23:                 // However, we have chosen to simply replicate the the normal behavior of the call
  24:                 // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
  25:                 assembly ("memory-safe") {
  26:                     revert(add(result, 32), mload(result))
  27:                 }
  28:             }
  29: 
  30:             results[i] = result;
  31: 
  32:             unchecked {
  33:                 ++i;
  34:             }
  35:         }
  36:     }

```

*GitHub* : [12-36](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L12-L36)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv64(uint256,uint256) (contracts/libraries/Math.sol#458-515) uses assembly
	- INLINE ASM (contracts/libraries/Math.sol#467-471)
	- INLINE ASM (contracts/libraries/Math.sol#476-479)
	- INLINE ASM (contracts/libraries/Math.sol#493-495)
	- INLINE ASM (contracts/libraries/Math.sol#497-500)
	- INLINE ASM (contracts/libraries/Math.sol#503-506)

/// @audit ************** Possible Issue Line(s) **************
	L#467-471,  L#476-479,  L#493-495,  L#497-500,  L#503-506,  

/// @audit ****************** Affected Code *******************
 467:             assembly ("memory-safe") {
 468:                 let mm := mulmod(a, b, not(0))
 469:                 prod0 := mul(a, b)
 470:                 prod1 := sub(sub(mm, prod0), lt(mm, prod0))
 471:             }
 476:                 assembly ("memory-safe") {
 477:                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 478:                     res := shr(64, prod0)
 479:                 }
 493:             assembly ("memory-safe") {
 494:                 remainder := mulmod(a, b, 0x10000000000000000)
 495:             }
 497:             assembly ("memory-safe") {
 498:                 prod1 := sub(prod1, gt(remainder, prod0))
 499:                 prod0 := sub(prod0, remainder)
 500:             }
 503:             assembly ("memory-safe") {
 504:                 // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
 505:                 prod0 := shr(64, prod0)
 506:             }

```

*GitHub* : [458-515](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L458-L515)

### [N-06]<a name="n-06"></a> Cyclomatic complexity

Functions with high (> 11) cyclomatic complexity.  **Recom:** Reduce cyclomatic complexity by splitting the function into several smaller subroutines.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.validate(TokenId) (contracts/types/TokenId.sol#500-571) has a high cyclomatic complexity value of 14.

/// @audit ****************** Affected Code *******************
 500:     function validate(TokenId self) internal pure {
 501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);
 502: 
 503:         // loop through the 4 (possible) legs in the tokenId `self`
 504:         unchecked {
 505:             // extract strike, width, and tokenType
 506:             uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;
 507:             for (uint256 i = 0; i < 4; ++i) {
 508:                 if (self.optionRatio(i) == 0) {
 509:                     // final leg in this position identified;

```

*GitHub* : [500-571](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L500-L571)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) has a high cyclomatic complexity value of 24.

/// @audit ****************** Affected Code *******************
 128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {
 129:         unchecked {
 130:             uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));
 131:             if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();
 132: 
 133:             uint256 sqrtR = absTick & 0x1 != 0
 134:                 ? 0xfffcb933bd6fad37aa2d162d1a594001
 135:                 : 0x100000000000000000000000000000000;
 136:             // RealV: 0xfffcb933bd6fad37aa2d162d1a594001
 137:             if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

### [N-07]<a name="n-07"></a> Dead-code

Functions that are not used.  **Recom:** Remove unused functions.

*There are 18 instance(s) of this issue:*

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addTokenType(TokenId,uint256,uint256) (contracts/types/TokenId.sol#255-266) is never used and should be removed

/// @audit ****************** Affected Code *******************
 255:     function addTokenType(
 256:         TokenId self,
 257:         uint256 _tokenType,
 258:         uint256 legIndex
 259:     ) internal pure returns (TokenId) {
 260:         unchecked {
 261:             return
 262:                 TokenId.wrap(
 263:                     TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))
 264:                 );
 265:         }
 266:     }

```

*GitHub* : [255-266](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L255-L266)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.countLongs(TokenId) (contracts/types/TokenId.sol#404-408) is never used and should be removed

/// @audit ****************** Affected Code *******************
 404:     function countLongs(TokenId self) internal pure returns (uint256) {
 405:         unchecked {
 406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);
 407:         }
 408:     }

```

*GitHub* : [404-408](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L404-L408)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addRiskPartner(TokenId,uint256,uint256) (contracts/types/TokenId.sol#273-284) is never used and should be removed

/// @audit ****************** Affected Code *******************
 273:     function addRiskPartner(
 274:         TokenId self,
 275:         uint256 _riskPartner,
 276:         uint256 legIndex
 277:     ) internal pure returns (TokenId) {
 278:         unchecked {
 279:             return
 280:                 TokenId.wrap(
 281:                     TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))
 282:                 );
 283:         }
 284:     }

```

*GitHub* : [273-284](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L273-L284)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.addLiquidity(LiquidityChunk,uint128) (contracts/types/LiquidityChunk.sol#89-96) is never used and should be removed

/// @audit ****************** Affected Code *******************
  89:     function addLiquidity(
  90:         LiquidityChunk self,
  91:         uint128 amount
  92:     ) internal pure returns (LiquidityChunk) {
  93:         unchecked {
  94:             return LiquidityChunk.wrap(LiquidityChunk.unwrap(self) + amount);
  95:         }
  96:     }

```

*GitHub* : [89-96](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L89-L96)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.min24(int24,int24) (contracts/libraries/Math.sol#25-27) is never used and should be removed

/// @audit ****************** Affected Code *******************
  25:     function min24(int24 a, int24 b) internal pure returns (int24) {
  26:         return a < b ? a : b;
  27:     }

```

*GitHub* : [25-27](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L25-L27)

```solidity
File: contracts/libraries/SafeTransferLib.sol

/// @audit ******************* Issue Detail *******************
SafeTransferLib.safeTransfer(address,address,uint256) (contracts/libraries/SafeTransferLib.sol#52-76) is never used and should be removed

/// @audit ****************** Affected Code *******************
  52:     function safeTransfer(address token, address to, uint256 amount) internal {
  53:         bool success;
  54: 
  55:         assembly ("memory-safe") {
  56:             // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
  57:             let p := mload(0x40)
  58: 
  59:             // Write the abi-encoded calldata into memory, beginning with the function selector.
  60:             mstore(p, 0xa9059cbb00000000000000000000000000000000000000000000000000000000)
  61:             mstore(add(4, p), to) // Append the "to" argument.
  62:             mstore(add(36, p), amount) // Append the "amount" argument.
  63: 
  64:             success := and(
  65:                 // Set success to whether the call reverted, if not we check it either
  66:                 // returned exactly 1 (can't just be non-zero data), or had no return data.
  67:                 or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
  68:                 // We use 68 because that's the total length of our calldata (4 + 32 * 2)
  69:                 // Counterintuitively, this call() must be positioned after the or() in the
  70:                 // surrounding and() because and() evaluates its arguments from right to left.
  71:                 call(gas(), token, 0, p, 68, 0, 32)
  72:             )
  73:         }
  74: 
  75:         if (!success) revert Errors.TransferFailed();
  76:     }

```

*GitHub* : [52-76](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L52-L76)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convertCollateralData(LeftRightUnsigned,LeftRightUnsigned,uint256,int24) (contracts/libraries/PanopticMath.sol#445-453) is never used and should be removed

/// @audit ****************** Affected Code *******************
 445:     function convertCollateralData(
 446:         LeftRightUnsigned tokenData0,
 447:         LeftRightUnsigned tokenData1,
 448:         uint256 tokenType,
 449:         int24 tick
 450:     ) internal pure returns (uint256, uint256) {
 451:         return
 452:             convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));
 453:     }

```

*GitHub* : [445-453](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L445-L453)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addWidth(TokenId,int24,uint256) (contracts/types/TokenId.sol#310-323) is never used and should be removed

/// @audit ****************** Affected Code *******************
 310:     function addWidth(
 311:         TokenId self,
 312:         int24 _width,
 313:         uint256 legIndex
 314:     ) internal pure returns (TokenId) {
 315:         // % 4096 -> take 12 bits from the incoming 24 bits (there's no uint12)
 316:         unchecked {
 317:             return
 318:                 TokenId.wrap(
 319:                     TokenId.unwrap(self) +
 320:                         (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))
 321:                 );
 322:         }
 323:     }

```

*GitHub* : [310-323](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L310-L323)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.clearLeg(TokenId,uint256) (contracts/types/TokenId.sol#464-491) is never used and should be removed

/// @audit ****************** Affected Code *******************
 464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {
 465:         if (i == 0)
 466:             return
 467:                 TokenId.wrap(
 468:                     TokenId.unwrap(self) &
 469:                         0xFFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFFFFFF
 470:                 );
 471:         if (i == 1)
 472:             return
 473:                 TokenId.wrap(

```

*GitHub* : [464-491](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L464-L491)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addAsset(TokenId,uint256,uint256) (contracts/types/TokenId.sol#205-214) is never used and should be removed

/// @audit ****************** Affected Code *******************
 205:     function addAsset(
 206:         TokenId self,
 207:         uint256 _asset,
 208:         uint256 legIndex
 209:     ) internal pure returns (TokenId) {
 210:         unchecked {
 211:             return
 212:                 TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));
 213:         }
 214:     }

```

*GitHub* : [205-214](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L205-L214)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addPoolId(TokenId,uint64) (contracts/types/TokenId.sol#183-187) is never used and should be removed

/// @audit ****************** Affected Code *******************
 183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {
 184:         unchecked {
 185:             return TokenId.wrap(TokenId.unwrap(self) + _poolId);
 186:         }
 187:     }

```

*GitHub* : [183-187](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L183-L187)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.convertNotional(uint128,int24,int24,uint256) (contracts/libraries/PanopticMath.sol#468-483) is never used and should be removed

/// @audit ****************** Affected Code *******************
 468:     function convertNotional(
 469:         uint128 contractSize,
 470:         int24 tickLower,
 471:         int24 tickUpper,
 472:         uint256 asset
 473:     ) internal pure returns (uint128) {
 474:         unchecked {
 475:             uint256 notional = asset == 0
 476:                 ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))
 477:                 : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));
 478: 
 479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();
 480: 
 481:             return uint128(notional);
 482:         }
 483:     }

```

*GitHub* : [468-483](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L468-L483)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addStrike(TokenId,int24,uint256) (contracts/types/TokenId.sol#291-303) is never used and should be removed

/// @audit ****************** Affected Code *******************
 291:     function addStrike(
 292:         TokenId self,
 293:         int24 _strike,
 294:         uint256 legIndex
 295:     ) internal pure returns (TokenId) {
 296:         unchecked {
 297:             return
 298:                 TokenId.wrap(
 299:                     TokenId.unwrap(self) +
 300:                         uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))
 301:                 );
 302:         }
 303:     }

```

*GitHub* : [291-303](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L291-L303)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24) (contracts/types/TokenId.sol#336-354) is never used and should be removed

/// @audit ****************** Affected Code *******************
 336:     function addLeg(
 337:         TokenId self,
 338:         uint256 legIndex,
 339:         uint256 _optionRatio,
 340:         uint256 _asset,
 341:         uint256 _isLong,
 342:         uint256 _tokenType,
 343:         uint256 _riskPartner,
 344:         int24 _strike,
 345:         int24 _width
 346:     ) internal pure returns (TokenId tokenId) {
 347:         tokenId = addOptionRatio(self, _optionRatio, legIndex);
 348:         tokenId = addAsset(tokenId, _asset, legIndex);
 349:         tokenId = addIsLong(tokenId, _isLong, legIndex);
 350:         tokenId = addTokenType(tokenId, _tokenType, legIndex);
 351:         tokenId = addRiskPartner(tokenId, _riskPartner, legIndex);
 352:         tokenId = addStrike(tokenId, _strike, legIndex);
 353:         tokenId = addWidth(tokenId, _width, legIndex);
 354:     }

```

*GitHub* : [336-354](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L336-L354)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.add(LeftRightUnsigned,LeftRightSigned) (contracts/types/LeftRight.sol#194-208) is never used and should be removed

/// @audit ****************** Affected Code *******************
 194:     function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
 195:         unchecked {
 196:             int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();
 197:             int128 left128 = int128(left);
 198: 
 199:             if (left128 != left) revert Errors.UnderOverFlow();
 200: 
 201:             int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();
 202:             int128 right128 = int128(right);
 203: 
 204:             if (right128 != right) revert Errors.UnderOverFlow();
 205: 
 206:             return z.toRightSlot(right128).toLeftSlot(left128);
 207:         }
 208:     }

```

*GitHub* : [194-208](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L194-L208)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addTickSpacing(TokenId,int24) (contracts/types/TokenId.sol#193-197) is never used and should be removed

/// @audit ****************** Affected Code *******************
 193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {
 194:         unchecked {
 195:             return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));
 196:         }
 197:     }

```

*GitHub* : [193-197](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L193-L197)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addOptionRatio(TokenId,uint256,uint256) (contracts/types/TokenId.sol#221-232) is never used and should be removed

/// @audit ****************** Affected Code *******************
 221:     function addOptionRatio(
 222:         TokenId self,
 223:         uint256 _optionRatio,
 224:         uint256 legIndex
 225:     ) internal pure returns (TokenId) {
 226:         unchecked {
 227:             return
 228:                 TokenId.wrap(
 229:                     TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))
 230:                 );
 231:         }
 232:     }

```

*GitHub* : [221-232](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L221-L232)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.addIsLong(TokenId,uint256,uint256) (contracts/types/TokenId.sol#240-248) is never used and should be removed

/// @audit ****************** Affected Code *******************
 240:     function addIsLong(
 241:         TokenId self,
 242:         uint256 _isLong,
 243:         uint256 legIndex
 244:     ) internal pure returns (TokenId) {
 245:         unchecked {
 246:             return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));
 247:         }
 248:     }

```

*GitHub* : [240-248](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L240-L248)

### [N-08]<a name="n-08"></a> Low-level calls

The use of low-level calls is error-prone. Low-level calls do not check for [code existence](https://solidity.readthedocs.io/en/v0.4.25/control-structures.html#error-handling-assert-require-revert-and-exceptions) or call success.  **Recom:** Avoid low-level calls. Check the call success. If the call is meant for a contract, check for code existence.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/multicall/Multicall.sol

/// @audit ******************* Issue Detail *******************
Low level call in Multicall.multicall(bytes[]) (contracts/multicall/Multicall.sol#12-36):
	- (success,result) = address(this).delegatecall(data[i]) (contracts/multicall/Multicall.sol#15)

/// @audit ************** Possible Issue Line(s) **************
	L#15,  

/// @audit ****************** Affected Code *******************
  12:     function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
  13:         results = new bytes[](data.length);
  14:         for (uint256 i = 0; i < data.length; ) {
  15:             (bool success, bytes memory result) = address(this).delegatecall(data[i]);
  16: 
  17:             if (!success) {
  18:                 // Bubble up the revert reason
  19:                 // The bytes type is ABI encoded as a length-prefixed byte array
  20:                 // So we simply need to add 32 to the pointer to get the start of the data
  21:                 // And then revert with the size loaded from the first 32 bytes
  22:                 // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
  23:                 // However, we have chosen to simply replicate the the normal behavior of the call
  24:                 // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
  25:                 assembly ("memory-safe") {
  26:                     revert(add(result, 32), mload(result))
  27:                 }
  28:             }
  29: 
  30:             results[i] = result;
  31: 
  32:             unchecked {
  33:                 ++i;
  34:             }
  35:         }
  36:     }

```

*GitHub* : [12-36](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L12-L36)

### [N-09]<a name="n-09"></a> Conformance to Solidity naming conventions

Solidity defines a [naming convention](https://solidity.readthedocs.io/en/v0.4.25/style-guide.html#naming-conventions) that should be followed.  **Recom:** Follow the Solidity [naming convention](https://solidity.readthedocs.io/en/v0.4.25/style-guide.html#naming-conventions).

*There are 43 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.s_ITMSpreadFee (contracts/CollateralTracker.sol#121) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#121,  

/// @audit ****************** Affected Code *******************
 121:     uint128 internal s_ITMSpreadFee;

```

*GitHub* : [121-121](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L121-L121)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.COMMISSION_FEE (contracts/CollateralTracker.sol#136) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#136,  

/// @audit ****************** Affected Code *******************
 136:     uint256 immutable COMMISSION_FEE;

```

*GitHub* : [136-136](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L136-L136)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Parameter PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker)._univ3pool (contracts/PanopticPool.sol#292) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#292,  

/// @audit ****************** Affected Code *******************
 292:         IUniswapV3Pool _univ3pool,

```

*GitHub* : [292-292](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L292-L292)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.TARGET_POOL_UTIL (contracts/CollateralTracker.sol#154) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#154,  

/// @audit ****************** Affected Code *******************
 154:     uint256 immutable TARGET_POOL_UTIL;

```

*GitHub* : [154-154](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L154-L154)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._width (contracts/types/TokenId.sol#345) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#345,  

/// @audit ****************** Affected Code *******************
 345:         int24 _width

```

*GitHub* : [345-345](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L345-L345)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addTickSpacing(TokenId,int24)._tickSpacing (contracts/types/TokenId.sol#193) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#193,  

/// @audit ****************** Affected Code *******************
 193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

```

*GitHub* : [193-193](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L193-L193)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.BUYER_COLLATERAL_RATIO (contracts/CollateralTracker.sol#145) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#145,  

/// @audit ****************** Affected Code *******************
 145:     uint256 immutable BUYER_COLLATERAL_RATIO;

```

*GitHub* : [145-145](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L145-L145)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.WETH (contracts/PanopticFactory.sol#78) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#78,  

/// @audit ****************** Affected Code *******************
  78:     address internal immutable WETH;

```

*GitHub* : [78-78](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L78-L78)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.FORCE_EXERCISE_COST (contracts/CollateralTracker.sol#149) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#149,  

/// @audit ****************** Affected Code *******************
 149:     int256 immutable FORCE_EXERCISE_COST;

```

*GitHub* : [149-149](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L149-L149)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addStrike(TokenId,int24,uint256)._strike (contracts/types/TokenId.sol#293) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#293,  

/// @audit ****************** Affected Code *******************
 293:         int24 _strike,

```

*GitHub* : [293-293](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L293-L293)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addIsLong(TokenId,uint256,uint256)._isLong (contracts/types/TokenId.sol#242) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#242,  

/// @audit ****************** Affected Code *******************
 242:         uint256 _isLong,

```

*GitHub* : [242-242](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L242-L242)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addTokenType(TokenId,uint256,uint256)._tokenType (contracts/types/TokenId.sol#257) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#257,  

/// @audit ****************** Affected Code *******************
 257:         uint256 _tokenType,

```

*GitHub* : [257-257](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L257-L257)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.UNIV3_FACTORY (contracts/PanopticFactory.sol#63) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#63,  

/// @audit ****************** Affected Code *******************
  63:     IUniswapV3Factory internal immutable UNIV3_FACTORY;

```

*GitHub* : [63-63](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L63-L63)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._tokenType (contracts/types/TokenId.sol#342) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#342,  

/// @audit ****************** Affected Code *******************
 342:         uint256 _tokenType,

```

*GitHub* : [342-342](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L342-L342)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._strike (contracts/types/TokenId.sol#344) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#344,  

/// @audit ****************** Affected Code *******************
 344:         int24 _strike,

```

*GitHub* : [344-344](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L344-L344)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager.FACTORY (contracts/SemiFungiblePositionManager.sol#137) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#137,  

/// @audit ****************** Affected Code *******************
 137:     IUniswapV3Factory internal immutable FACTORY;

```

*GitHub* : [137-137](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L137-L137)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.SFPM (contracts/PanopticFactory.sol#66) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#66,  

/// @audit ****************** Affected Code *******************
  66:     SemiFungiblePositionManager internal immutable SFPM;

```

*GitHub* : [66-66](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L66-L66)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
Parameter LiquidityChunkLibrary.addTickUpper(LiquidityChunk,int24)._tickUpper (contracts/types/LiquidityChunk.sol#120) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#120,  

/// @audit ****************** Affected Code *******************
 120:         int24 _tickUpper

```

*GitHub* : [120-120](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L120-L120)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._asset (contracts/types/TokenId.sol#340) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#340,  

/// @audit ****************** Affected Code *******************
 340:         uint256 _asset,

```

*GitHub* : [340-340](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L340-L340)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.ITM_SPREAD_MULTIPLIER (contracts/CollateralTracker.sol#162) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#162,  

/// @audit ****************** Affected Code *******************
 162:     uint256 immutable ITM_SPREAD_MULTIPLIER;

```

*GitHub* : [162-162](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L162-L162)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.DONOR_NFT (contracts/PanopticFactory.sol#69) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#69,  

/// @audit ****************** Affected Code *******************
  69:     IDonorNFT internal immutable DONOR_NFT;

```

*GitHub* : [69-69](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L69-L69)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Parameter PanopticFactory.initialize(address)._owner (contracts/PanopticFactory.sol#134) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#134,  

/// @audit ****************** Affected Code *******************
 134:     function initialize(address _owner) public {

```

*GitHub* : [134-134](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L134-L134)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
Parameter LiquidityChunkLibrary.createChunk(int24,int24,uint128)._tickUpper (contracts/types/LiquidityChunk.sol#72) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#72,  

/// @audit ****************** Affected Code *******************
  72:         int24 _tickUpper,

```

*GitHub* : [72-72](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L72-L72)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Modifier SemiFungiblePositionManager.ReentrancyLock(uint64) (contracts/SemiFungiblePositionManager.sol#305-315) is not in mixedCase

/// @audit ****************** Affected Code *******************
 305:     modifier ReentrancyLock(uint64 poolId) {
 306:         // check if the pool is already locked
 307:         // init lock if not
 308:         beginReentrancyLock(poolId);
 309: 
 310:         // execute function
 311:         _;
 312: 
 313:         // remove lock
 314:         endReentrancyLock(poolId);
 315:     }

```

*GitHub* : [305-315](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L305-L315)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._optionRatio (contracts/types/TokenId.sol#339) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#339,  

/// @audit ****************** Affected Code *******************
 339:         uint256 _optionRatio,

```

*GitHub* : [339-339](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L339-L339)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
Parameter LiquidityChunkLibrary.updateTickLower(LiquidityChunk,int24)._tickLower (contracts/types/LiquidityChunk.sol#137) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#137,  

/// @audit ****************** Affected Code *******************
 137:         int24 _tickLower

```

*GitHub* : [137-137](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L137-L137)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.TICK_DEVIATION (contracts/CollateralTracker.sol#131) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#131,  

/// @audit ****************** Affected Code *******************
 131:     uint256 immutable TICK_DEVIATION;

```

*GitHub* : [131-131](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L131-L131)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.SATURATED_POOL_UTIL (contracts/CollateralTracker.sol#158) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#158,  

/// @audit ****************** Affected Code *******************
 158:     uint256 immutable SATURATED_POOL_UTIL;

```

*GitHub* : [158-158](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L158-L158)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.POOL_REFERENCE (contracts/PanopticFactory.sol#72) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#72,  

/// @audit ****************** Affected Code *******************
  72:     address internal immutable POOL_REFERENCE;

```

*GitHub* : [72-72](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L72-L72)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
Parameter LiquidityChunkLibrary.addTickLower(LiquidityChunk,int24)._tickLower (contracts/types/LiquidityChunk.sol#104) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#104,  

/// @audit ****************** Affected Code *******************
 104:         int24 _tickLower

```

*GitHub* : [104-104](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L104-L104)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addWidth(TokenId,int24,uint256)._width (contracts/types/TokenId.sol#312) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#312,  

/// @audit ****************** Affected Code *******************
 312:         int24 _width,

```

*GitHub* : [312-312](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L312-L312)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addRiskPartner(TokenId,uint256,uint256)._riskPartner (contracts/types/TokenId.sol#275) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#275,  

/// @audit ****************** Affected Code *******************
 275:         uint256 _riskPartner,

```

*GitHub* : [275-275](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L275-L275)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.SFPM (contracts/PanopticPool.sol#179) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#179,  

/// @audit ****************** Affected Code *******************
 179:     SemiFungiblePositionManager internal immutable SFPM;

```

*GitHub* : [179-179](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L179-L179)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.COLLATERAL_REFERENCE (contracts/PanopticFactory.sol#75) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#75,  

/// @audit ****************** Affected Code *******************
  75:     address internal immutable COLLATERAL_REFERENCE;

```

*GitHub* : [75-75](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L75-L75)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager.s_AddrToPoolIdData (contracts/SemiFungiblePositionManager.sol#145) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#145,  

/// @audit ****************** Affected Code *******************
 145:     mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;

```

*GitHub* : [145-145](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L145-L145)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._riskPartner (contracts/types/TokenId.sol#343) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#343,  

/// @audit ****************** Affected Code *******************
 343:         uint256 _riskPartner,

```

*GitHub* : [343-343](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L343-L343)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
Parameter LiquidityChunkLibrary.createChunk(int24,int24,uint128)._tickLower (contracts/types/LiquidityChunk.sol#71) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#71,  

/// @audit ****************** Affected Code *******************
  71:         int24 _tickLower,

```

*GitHub* : [71-71](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L71-L71)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
Parameter LiquidityChunkLibrary.updateTickUpper(LiquidityChunk,int24)._tickUpper (contracts/types/LiquidityChunk.sol#153) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#153,  

/// @audit ****************** Affected Code *******************
 153:         int24 _tickUpper

```

*GitHub* : [153-153](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L153-L153)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.SELLER_COLLATERAL_RATIO (contracts/CollateralTracker.sol#141) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#141,  

/// @audit ****************** Affected Code *******************
 141:     uint256 immutable SELLER_COLLATERAL_RATIO;

```

*GitHub* : [141-141](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L141-L141)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addAsset(TokenId,uint256,uint256)._asset (contracts/types/TokenId.sol#207) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#207,  

/// @audit ****************** Affected Code *******************
 207:         uint256 _asset,

```

*GitHub* : [207-207](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L207-L207)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addPoolId(TokenId,uint64)._poolId (contracts/types/TokenId.sol#183) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#183,  

/// @audit ****************** Affected Code *******************
 183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

```

*GitHub* : [183-183](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L183-L183)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addOptionRatio(TokenId,uint256,uint256)._optionRatio (contracts/types/TokenId.sol#223) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#223,  

/// @audit ****************** Affected Code *******************
 223:         uint256 _optionRatio,

```

*GitHub* : [223-223](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L223-L223)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Parameter TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._isLong (contracts/types/TokenId.sol#341) is not in mixedCase

/// @audit ************** Possible Issue Line(s) **************
	L#341,  

/// @audit ****************** Affected Code *******************
 341:         uint256 _isLong,

```

*GitHub* : [341-341](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L341-L341)

### [N-10]<a name="n-10"></a> Redundant Statements

Possible usage of redundant statements that have no effect.  **Recom:** Remove redundant statements if they congest code but offer no value.

*There are 1 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
CollateralTracker (contracts/CollateralTracker.sol#36-1650) has redundant expression(s):-
	- required (contracts/CollateralTracker.sol#1350)

/// @audit ************** Possible Issue Line(s) **************
	L#1350,  

/// @audit ****************** Affected Code *******************
1350:                     required;

```

*GitHub* : [36-1650](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L36-L1650)

### [N-11]<a name="n-11"></a> Variable names too similar

Variables with names that are too similar.  **Recom:** Prevent variables from having similar names.

*There are 47 instance(s) of this issue:*

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).protocolLoss0 (contracts/libraries/PanopticMath.sol#825) is too similar to PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).protocolLoss1 (contracts/libraries/PanopticMath.sol#801)

/// @audit ************** Possible Issue Line(s) **************
	L#825,  L#801,  

/// @audit ****************** Affected Code *******************
 801:                 int256 protocolLoss1 = collateralDelta1;
 825:                 int256 protocolLoss0 = collateralDelta0;

```

*GitHub* : [825-825](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L825-L825)

```solidity
File: contracts/libraries/Constants.sol

/// @audit ******************* Issue Detail *******************
Variable Constants.MAX_V3POOL_SQRT_RATIO (contracts/libraries/Constants.sol#21-22) is too similar to Constants.MIN_V3POOL_SQRT_RATIO (contracts/libraries/Constants.sol#18)

/// @audit ************** Possible Issue Line(s) **************
	L#18,  

/// @audit ****************** Affected Code *******************
  18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;
  21:     uint160 internal constant MAX_V3POOL_SQRT_RATIO =
  22:         1461446703485210103287273052203988822378723970342;

```

*GitHub* : [21-22](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L21-L22)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.POOL_REFERENCE (contracts/PanopticFactory.sol#72) is too similar to PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._poolReference (contracts/PanopticFactory.sol#120)

/// @audit ************** Possible Issue Line(s) **************
	L#72,  L#120,  

/// @audit ****************** Affected Code *******************
  72:     address internal immutable POOL_REFERENCE;
 120:         address _poolReference,

```

*GitHub* : [72-72](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L72-L72)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128).poolUtilization0 (contracts/CollateralTracker.sol#1631) is too similar to CollateralTracker._computeStrangle(TokenId,uint256,uint128,int24,uint128).poolUtilization1 (contracts/CollateralTracker.sol#1632)

/// @audit ************** Possible Issue Line(s) **************
	L#1631,  L#1632,  

/// @audit ****************** Affected Code *******************
1631:             uint64 poolUtilization0 = uint64(poolUtilization);
1632:             uint64 poolUtilization1 = uint64(poolUtilization >> 64);

```

*GitHub* : [1631-1631](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1631-L1631)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.optionPositionBalance(address,TokenId).poolUtilization0 (contracts/PanopticPool.sol#355) is too similar to PanopticPool._mintInSFPMAndUpdateCollateral(TokenId,uint128,int24,int24).poolUtilizations (contracts/PanopticPool.sol#693)

/// @audit ************** Possible Issue Line(s) **************
	L#355,  L#693,  

/// @audit ****************** Affected Code *******************
 355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {
 693:         uint128 poolUtilizations = _payCommissionAndWriteData(tokenId, positionSize, totalSwapped);

```

*GitHub* : [355-355](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L355-L355)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium0X64_base (contracts/SemiFungiblePositionManager.sol#1342) is too similar to SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium1X64_base (contracts/SemiFungiblePositionManager.sol#1343)

/// @audit ************** Possible Issue Line(s) **************
	L#1342,  L#1343,  

/// @audit ****************** Affected Code *******************
1342:             uint256 premium0X64_base;
1343:             uint256 premium1X64_base;

```

*GitHub* : [1342-1342](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1342-L1342)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Variable TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._optionRatio (contracts/types/TokenId.sol#339) is too similar to TokenIdLibrary.countLegs(TokenId).optionRatios (contracts/types/TokenId.sol#434)

/// @audit ************** Possible Issue Line(s) **************
	L#339,  L#434,  

/// @audit ****************** Affected Code *******************
 339:         uint256 _optionRatio,
 434:         uint256 optionRatios = TokenId.unwrap(self) & OPTION_RATIO_MASK;

```

*GitHub* : [339-339](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L339-L339)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager.uniswapV3SwapCallback(int256,int256,bytes).amount0Delta (contracts/SemiFungiblePositionManager.sol#436) is too similar to SemiFungiblePositionManager.uniswapV3SwapCallback(int256,int256,bytes).amount1Delta (contracts/SemiFungiblePositionManager.sol#437)

/// @audit ************** Possible Issue Line(s) **************
	L#436,  L#437,  

/// @audit ****************** Affected Code *******************
 436:         int256 amount0Delta,
 437:         int256 amount1Delta,

```

*GitHub* : [436-436](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L436-L436)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]).accumulated0 (contracts/PanopticPool.sol#1768-1769) is too similar to PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]).accumulated1 (contracts/PanopticPool.sol#1770-1771)

/// @audit ************** Possible Issue Line(s) **************
	L#1770-1771,  

/// @audit ****************** Affected Code *******************
1768:             uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *
1769:                 totalLiquidity) / 2 ** 64;
1770:             uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *
1771:                 totalLiquidity) / 2 ** 64;

```

*GitHub* : [1768-1769](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1768-L1769)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).receivedAmount0 (contracts/SemiFungiblePositionManager.sol#1284) is too similar to SemiFungiblePositionManager._collectAndWritePositionData(LiquidityChunk,IUniswapV3Pool,LeftRightUnsigned,bytes32,LeftRightSigned,uint256).receivedAmount1 (contracts/SemiFungiblePositionManager.sol#1284)

/// @audit ************** Possible Issue Line(s) **************
	L#1284,  

/// @audit ****************** Affected Code *******************
1284:             (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(

```

*GitHub* : [1284-1284](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1284-L1284)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Variable TokenIdLibrary.addOptionRatio(TokenId,uint256,uint256)._optionRatio (contracts/types/TokenId.sol#223) is too similar to TokenIdLibrary.flipToBurnToken(TokenId).optionRatios (contracts/types/TokenId.sol#371)

/// @audit ************** Possible Issue Line(s) **************
	L#223,  L#371,  

/// @audit ****************** Affected Code *******************
 223:         uint256 _optionRatio,
 371:             uint256 optionRatios = TokenId.unwrap(self) & OPTION_RATIO_MASK;

```

*GitHub* : [223-223](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L223-L223)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]).positionIdListExercisee (contracts/PanopticPool.sol#1182) is too similar to PanopticPool.forceExercise(address,TokenId[],TokenId[],TokenId[]).positionIdListExercisor (contracts/PanopticPool.sol#1183)

/// @audit ************** Possible Issue Line(s) **************
	L#1182,  L#1183,  

/// @audit ****************** Affected Code *******************
1182:         TokenId[] calldata positionIdListExercisee,
1183:         TokenId[] calldata positionIdListExercisor

```

*GitHub* : [1182-1182](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1182-L1182)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.optionPositionBalance(address,TokenId).poolUtilization1 (contracts/PanopticPool.sol#355) is too similar to PanopticPool._mintOptions(TokenId[],uint128,uint64,int24,int24).poolUtilizations (contracts/PanopticPool.sol#642-647)

/// @audit ************** Possible Issue Line(s) **************
	L#355,  L#642-647,  

/// @audit ****************** Affected Code *******************
 355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {
 642:         uint128 poolUtilizations = _mintInSFPMAndUpdateCollateral(
 643:             tokenId,
 644:             positionSize,
 645:             tickLimitLow,
 646:             tickLimitHigh
 647:         );

```

*GitHub* : [355-355](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L355-L355)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Variable TokenIdLibrary.addLeg(TokenId,uint256,uint256,uint256,uint256,uint256,uint256,int24,int24)._optionRatio (contracts/types/TokenId.sol#339) is too similar to TokenIdLibrary.flipToBurnToken(TokenId).optionRatios (contracts/types/TokenId.sol#371)

/// @audit ************** Possible Issue Line(s) **************
	L#339,  L#371,  

/// @audit ****************** Affected Code *******************
 339:         uint256 _optionRatio,
 371:             uint256 optionRatios = TokenId.unwrap(self) & OPTION_RATIO_MASK;

```

*GitHub* : [339-339](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L339-L339)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool._addUserOption(TokenId,uint64).premiumAccumulator0 (contracts/PanopticPool.sol#751) is too similar to PanopticPool._addUserOption(TokenId,uint64).premiumAccumulator1 (contracts/PanopticPool.sol#751)

/// @audit ************** Possible Issue Line(s) **************
	L#751,  

/// @audit ****************** Affected Code *******************
 751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

```

*GitHub* : [751-751](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L751-L751)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.COMMISSION_FEE (contracts/CollateralTracker.sol#136) is too similar to CollateralTracker.constructor(uint256,uint256,uint256,int256,uint256,uint256,uint256)._commissionFee (contracts/CollateralTracker.sol#179)

/// @audit ************** Possible Issue Line(s) **************
	L#136,  L#179,  

/// @audit ****************** Affected Code *******************
 136:     uint256 immutable COMMISSION_FEE;
 179:         uint256 _commissionFee,

```

*GitHub* : [136-136](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L136-L136)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool._addUserOption(TokenId,uint64).premiumAccumulator1 (contracts/PanopticPool.sol#751) is too similar to PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]).premiumAccumulators (contracts/PanopticPool.sol#1762)

/// @audit ************** Possible Issue Line(s) **************
	L#751,  L#1762,  

/// @audit ****************** Affected Code *******************
 751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
1762:         uint256[2] memory premiumAccumulators

```

*GitHub* : [751-751](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L751-L751)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).deltaBonus0 (contracts/PanopticPool.sol#1120) is too similar to PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).deltaBonus1 (contracts/PanopticPool.sol#1121)

/// @audit ************** Possible Issue Line(s) **************
	L#1120,  L#1121,  

/// @audit ****************** Affected Code *******************
1120:             int256 deltaBonus0;
1121:             int256 deltaBonus1;

```

*GitHub* : [1120-1120](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1120-L1120)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateral0 (contracts/libraries/PanopticMath.sol#773) is too similar to PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker).collateral1 (contracts/libraries/PanopticMath.sol#922)

/// @audit ************** Possible Issue Line(s) **************
	L#773,  L#922,  

/// @audit ****************** Affected Code *******************
 773:         CollateralTracker collateral0,
 922:         CollateralTracker collateral1

```

*GitHub* : [773-773](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L773-L773)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.UNIV3_FACTORY (contracts/PanopticFactory.sol#63) is too similar to PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._univ3Factory (contracts/PanopticFactory.sol#118)

/// @audit ************** Possible Issue Line(s) **************
	L#63,  L#118,  

/// @audit ****************** Affected Code *******************
  63:     IUniswapV3Factory internal immutable UNIV3_FACTORY;
 118:         IUniswapV3Factory _univ3Factory,

```

*GitHub* : [63-63](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L63-L63)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateralDelta0 (contracts/libraries/PanopticMath.sol#791) is too similar to PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateralDelta1 (contracts/libraries/PanopticMath.sol#792)

/// @audit ************** Possible Issue Line(s) **************
	L#791,  L#792,  

/// @audit ****************** Affected Code *******************
 791:             int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);
 792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

```

*GitHub* : [791-791](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L791-L791)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool._addUserOption(TokenId,uint64).premiumAccumulator0 (contracts/PanopticPool.sol#751) is too similar to PanopticPool.settleLongPremium(TokenId[],address,uint256).premiumAccumulator1 (contracts/PanopticPool.sol#1605)

/// @audit ************** Possible Issue Line(s) **************
	L#751,  L#1605,  

/// @audit ****************** Affected Code *******************
 751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
1605:             (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

```

*GitHub* : [751-751](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L751-L751)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium0X64_owed (contracts/SemiFungiblePositionManager.sol#1363) is too similar to SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium1X64_owed (contracts/SemiFungiblePositionManager.sol#1364)

/// @audit ************** Possible Issue Line(s) **************
	L#1363,  L#1364,  

/// @audit ****************** Affected Code *******************
1363:                 uint128 premium0X64_owed;
1364:                 uint128 premium1X64_owed;

```

*GitHub* : [1363-1363](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1363-L1363)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.settleLongPremium(TokenId[],address,uint256).premiumAccumulator0 (contracts/PanopticPool.sol#1605) is too similar to PanopticPool._addUserOption(TokenId,uint64).premiumAccumulator1 (contracts/PanopticPool.sol#751)

/// @audit ************** Possible Issue Line(s) **************
	L#1605,  L#751,  

/// @audit ****************** Affected Code *******************
 751:                 (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
1605:             (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

```

*GitHub* : [1605-1605](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1605-L1605)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.COLLATERAL_REFERENCE (contracts/PanopticFactory.sol#75) is too similar to PanopticFactory.constructor(address,SemiFungiblePositionManager,IUniswapV3Factory,IDonorNFT,address,address)._collateralReference (contracts/PanopticFactory.sol#121)

/// @audit ************** Possible Issue Line(s) **************
	L#75,  L#121,  

/// @audit ****************** Affected Code *******************
  75:     address internal immutable COLLATERAL_REFERENCE;
 121:         address _collateralReference

```

*GitHub* : [75-75](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L75-L75)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.settleLongPremium(TokenId[],address,uint256).premiumAccumulator1 (contracts/PanopticPool.sol#1605) is too similar to PanopticPool._getAvailablePremium(uint256,LeftRightUnsigned,LeftRightUnsigned,LeftRightUnsigned,uint256[2]).premiumAccumulators (contracts/PanopticPool.sol#1762)

/// @audit ************** Possible Issue Line(s) **************
	L#1605,  L#1762,  

/// @audit ****************** Affected Code *******************
1605:             (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
1762:         uint256[2] memory premiumAccumulators

```

*GitHub* : [1605-1605](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1605-L1605)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.s_univ3token0 (contracts/CollateralTracker.sol#96) is too similar to CollateralTracker.s_univ3token1 (contracts/CollateralTracker.sol#99)

/// @audit ************** Possible Issue Line(s) **************
	L#96,  L#99,  

/// @audit ****************** Affected Code *******************
  96:     address internal s_univ3token0;
  99:     address internal s_univ3token1;

```

*GitHub* : [96-96](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L96-L96)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
Variable FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24).feeGrowthInside0X128 (contracts/libraries/FeesCalc.sol#135) is too similar to FeesCalc._getAMMSwapFeesPerLiquidityCollected(IUniswapV3Pool,int24,int24,int24).feeGrowthInside1X128 (contracts/libraries/FeesCalc.sol#135)

/// @audit ************** Possible Issue Line(s) **************
	L#135,  

/// @audit ****************** Affected Code *******************
 135:     ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {

```

*GitHub* : [135-135](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L135-L135)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateral0 (contracts/libraries/PanopticMath.sol#773) is too similar to PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateral1 (contracts/libraries/PanopticMath.sol#774)

/// @audit ************** Possible Issue Line(s) **************
	L#773,  L#774,  

/// @audit ****************** Affected Code *******************
 773:         CollateralTracker collateral0,
 774:         CollateralTracker collateral1,

```

*GitHub* : [773-773](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L773-L773)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium0X64_gross (contracts/SemiFungiblePositionManager.sol#1384) is too similar to SemiFungiblePositionManager._getPremiaDeltas(LeftRightUnsigned,LeftRightUnsigned).premium1X64_gross (contracts/SemiFungiblePositionManager.sol#1385)

/// @audit ************** Possible Issue Line(s) **************
	L#1384,  L#1385,  

/// @audit ****************** Affected Code *******************
1384:                 uint128 premium0X64_gross;
1385:                 uint128 premium1X64_gross;

```

*GitHub* : [1384-1384](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1384-L1384)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker).collateral0 (contracts/libraries/PanopticMath.sol#921) is too similar to PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker).collateral1 (contracts/libraries/PanopticMath.sol#922)

/// @audit ************** Possible Issue Line(s) **************
	L#921,  L#922,  

/// @audit ****************** Affected Code *******************
 921:         CollateralTracker collateral0,
 922:         CollateralTracker collateral1

```

*GitHub* : [921-921](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L921-L921)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned).currentValue0 (contracts/CollateralTracker.sol#681) is too similar to CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned).currentValue1 (contracts/CollateralTracker.sol#682)

/// @audit ************** Possible Issue Line(s) **************
	L#681,  L#682,  

/// @audit ****************** Affected Code *******************
 681:                 uint256 currentValue0;
 682:                 uint256 currentValue1;

```

*GitHub* : [681-681](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L681-L681)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.optionPositionBalance(address,TokenId).poolUtilization0 (contracts/PanopticPool.sol#355) is too similar to PanopticPool.optionPositionBalance(address,TokenId).poolUtilization1 (contracts/PanopticPool.sol#355)

/// @audit ************** Possible Issue Line(s) **************
	L#355,  

/// @audit ****************** Affected Code *******************
 355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

```

*GitHub* : [355-355](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L355-L355)

```solidity
File: contracts/libraries/FeesCalc.sol

/// @audit ******************* Issue Detail *******************
Variable FeesCalc.calculateAMMSwapFees(IUniswapV3Pool,int24,int24,int24,uint128).ammFeesPerLiqToken0X128 (contracts/libraries/FeesCalc.sol#107) is too similar to FeesCalc.calculateAMMSwapFees(IUniswapV3Pool,int24,int24,int24,uint128).ammFeesPerLiqToken1X128 (contracts/libraries/FeesCalc.sol#108)

/// @audit ************** Possible Issue Line(s) **************
	L#107,  L#108,  

/// @audit ****************** Affected Code *******************
 107:             uint256 ammFeesPerLiqToken0X128,
 108:             uint256 ammFeesPerLiqToken1X128

```

*GitHub* : [107-107](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L107-L107)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool._payCommissionAndWriteData(TokenId,uint128,LeftRightSigned).utilization0 (contracts/PanopticPool.sol#715-720) is too similar to PanopticPool._payCommissionAndWriteData(TokenId,uint128,LeftRightSigned).utilization1 (contracts/PanopticPool.sol#721-726)

/// @audit ************** Possible Issue Line(s) **************
	L#721-726,  

/// @audit ****************** Affected Code *******************
 715:         int256 utilization0 = s_collateralToken0.takeCommissionAddData(
 716:             msg.sender,
 717:             longAmounts.rightSlot(),
 718:             shortAmounts.rightSlot(),
 719:             totalSwapped.rightSlot()
 720:         );
 721:         int256 utilization1 = s_collateralToken1.takeCommissionAddData(
 722:             msg.sender,
 723:             longAmounts.leftSlot(),
 724:             shortAmounts.leftSlot(),
 725:             totalSwapped.leftSlot()
 726:         );

```

*GitHub* : [715-720](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L715-L720)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.settleLongPremium(TokenId[],address,uint256).premiumAccumulator0 (contracts/PanopticPool.sol#1605) is too similar to PanopticPool.settleLongPremium(TokenId[],address,uint256).premiumAccumulator1 (contracts/PanopticPool.sol#1605)

/// @audit ************** Possible Issue Line(s) **************
	L#1605,  

/// @audit ****************** Affected Code *******************
1605:             (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(

```

*GitHub* : [1605-1605](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1605-L1605)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
Variable TokenIdLibrary.addOptionRatio(TokenId,uint256,uint256)._optionRatio (contracts/types/TokenId.sol#223) is too similar to TokenIdLibrary.countLegs(TokenId).optionRatios (contracts/types/TokenId.sol#434)

/// @audit ************** Possible Issue Line(s) **************
	L#223,  L#434,  

/// @audit ****************** Affected Code *******************
 223:         uint256 _optionRatio,
 434:         uint256 optionRatios = TokenId.unwrap(self) & OPTION_RATIO_MASK;

```

*GitHub* : [223-223](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L223-L223)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool).feeGrowthInside0LastX128 (contracts/SemiFungiblePositionManager.sol#1148) is too similar to SemiFungiblePositionManager._getFeesBase(IUniswapV3Pool,uint128,LiquidityChunk,bool).feeGrowthInside1LastX128 (contracts/SemiFungiblePositionManager.sol#1148)

/// @audit ************** Possible Issue Line(s) **************
	L#1148,  

/// @audit ****************** Affected Code *******************
1148:         (, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, , ) = univ3pool

```

*GitHub* : [1148-1148](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1148-L1148)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticMath.getRefundAmounts(address,LeftRightSigned,int24,CollateralTracker,CollateralTracker).collateral0 (contracts/libraries/PanopticMath.sol#921) is too similar to PanopticMath.haircutPremia(address,TokenId[],LeftRightSigned[4][],LeftRightSigned,CollateralTracker,CollateralTracker,uint160,mapping(bytes32 => LeftRightUnsigned)).collateral1 (contracts/libraries/PanopticMath.sol#774)

/// @audit ************** Possible Issue Line(s) **************
	L#921,  L#774,  

/// @audit ****************** Affected Code *******************
 774:         CollateralTracker collateral1,
 921:         CollateralTracker collateral0,

```

*GitHub* : [921-921](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L921-L921)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.uniswapV3MintCallback(uint256,uint256,bytes).amount0Owed (contracts/PanopticFactory.sol#173) is too similar to PanopticFactory.uniswapV3MintCallback(uint256,uint256,bytes).amount1Owed (contracts/PanopticFactory.sol#174)

/// @audit ************** Possible Issue Line(s) **************
	L#173,  L#174,  

/// @audit ****************** Affected Code *******************
 173:         uint256 amount0Owed,
 174:         uint256 amount1Owed,

```

*GitHub* : [173-173](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L173-L173)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker).collateralTracker0 (contracts/PanopticPool.sol#295) is too similar to PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker).collateralTracker1 (contracts/PanopticPool.sol#296)

/// @audit ************** Possible Issue Line(s) **************
	L#295,  L#296,  

/// @audit ****************** Affected Code *******************
 295:         CollateralTracker collateralTracker0,
 296:         CollateralTracker collateralTracker1

```

*GitHub* : [295-295](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L295-L295)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
Variable LiquidityChunkLibrary.CLEAR_TL_MASK (contracts/types/LiquidityChunk.sol#54-55) is too similar to LiquidityChunkLibrary.CLEAR_TU_MASK (contracts/types/LiquidityChunk.sol#58-59)

/// @audit ************** Possible Issue Line(s) **************
	L#58-59,  

/// @audit ****************** Affected Code *******************
  54:     uint256 internal constant CLEAR_TL_MASK =
  55:         0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;
  58:     uint256 internal constant CLEAR_TU_MASK =
  59:         0xFFFFFF000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```

*GitHub* : [54-55](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L54-L55)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).liquidationBonus0 (contracts/PanopticPool.sol#1075) is too similar to PanopticPool.liquidate(TokenId[],address,LeftRightUnsigned,TokenId[]).liquidationBonus1 (contracts/PanopticPool.sol#1076)

/// @audit ************** Possible Issue Line(s) **************
	L#1075,  L#1076,  

/// @audit ****************** Affected Code *******************
1075:         int256 liquidationBonus0;
1076:         int256 liquidationBonus1;

```

*GitHub* : [1075-1075](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1075-L1075)

```solidity
File: contracts/CollateralTracker.sol

/// @audit ******************* Issue Detail *******************
Variable CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned).oracleValue0 (contracts/CollateralTracker.sol#683) is too similar to CollateralTracker.exerciseCost(int24,int24,TokenId,uint128,LeftRightSigned).oracleValue1 (contracts/CollateralTracker.sol#684)

/// @audit ************** Possible Issue Line(s) **************
	L#683,  L#684,  

/// @audit ****************** Affected Code *******************
 683:                 uint256 oracleValue0;
 684:                 uint256 oracleValue1;

```

*GitHub* : [683-683](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L683-L683)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticPool.s_collateralToken0 (contracts/PanopticPool.sol#231) is too similar to PanopticPool.s_collateralToken1 (contracts/PanopticPool.sol#233)

/// @audit ************** Possible Issue Line(s) **************
	L#231,  L#233,  

/// @audit ****************** Affected Code *******************
 231:     CollateralTracker internal s_collateralToken0;
 233:     CollateralTracker internal s_collateralToken1;

```

*GitHub* : [231-231](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L231-L231)

```solidity
File: contracts/PanopticFactory.sol

/// @audit ******************* Issue Detail *******************
Variable PanopticFactory.deployNewPool(address,address,uint24,bytes32).collateralTracker0 (contracts/PanopticFactory.sol#240-242) is too similar to PanopticFactory.deployNewPool(address,address,uint24,bytes32).collateralTracker1 (contracts/PanopticFactory.sol#243-245)

/// @audit ************** Possible Issue Line(s) **************
	L#243-245,  

/// @audit ****************** Affected Code *******************
 240:         CollateralTracker collateralTracker0 = CollateralTracker(
 241:             Clones.clone(COLLATERAL_REFERENCE)
 242:         );
 243:         CollateralTracker collateralTracker1 = CollateralTracker(
 244:             Clones.clone(COLLATERAL_REFERENCE)
 245:         );

```

*GitHub* : [240-242](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L240-L242)

```solidity
File: contracts/SemiFungiblePositionManager.sol

/// @audit ******************* Issue Detail *******************
Variable SemiFungiblePositionManager.uniswapV3MintCallback(uint256,uint256,bytes).amount0Owed (contracts/SemiFungiblePositionManager.sol#403) is too similar to SemiFungiblePositionManager.uniswapV3MintCallback(uint256,uint256,bytes).amount1Owed (contracts/SemiFungiblePositionManager.sol#404)

/// @audit ************** Possible Issue Line(s) **************
	L#403,  L#404,  

/// @audit ****************** Affected Code *******************
 403:         uint256 amount0Owed,
 404:         uint256 amount1Owed,

```

*GitHub* : [403-403](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L403-L403)

### [N-12]<a name="n-12"></a> Too many digits

Literals with many digits are difficult to read and review.  **Recom:** Use:- [Ether suffix](https://solidity.readthedocs.io/en/latest/units-and-global-variables.html#ether-units),- [Time suffix](https://solidity.readthedocs.io/en/latest/units-and-global-variables.html#time-units), or- [The scientific notation](https://solidity.readthedocs.io/en/latest/types.html#rational-and-integer-literals)

*There are 24 instance(s) of this issue:*

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.getSqrtRatioAtTick(int24) (contracts/libraries/Math.sol#128-181) uses literals with too many digits:
	- sqrtR = 0x100000000000000000000000000000000 (contracts/libraries/Math.sol#133-135)

/// @audit ************** Possible Issue Line(s) **************
	L#133-135,  

/// @audit ****************** Affected Code *******************
 133:             uint256 sqrtR = absTick & 0x1 != 0
 134:                 ? 0xfffcb933bd6fad37aa2d162d1a594001
 135:                 : 0x100000000000000000000000000000000;

```

*GitHub* : [128-181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L181)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.slitherConstructorConstantVariables() (contracts/types/LeftRight.sol#17-302) uses literals with too many digits:
	- LEFT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000 (contracts/types/LeftRight.sol#22-23)

/// @audit ************** Possible Issue Line(s) **************
	L#22-23,  

/// @audit ****************** Affected Code *******************
  22:     uint256 internal constant LEFT_HALF_BIT_MASK =
  23:         0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000;

```

*GitHub* : [17-302](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L17-L302)

```solidity
File: contracts/types/LeftRight.sol

/// @audit ******************* Issue Detail *******************
LeftRightLibrary.slitherConstructorConstantVariables() (contracts/types/LeftRight.sol#17-302) uses literals with too many digits:
	- LEFT_HALF_BIT_MASK_INT = int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000)) (contracts/types/LeftRight.sol#26-27)

/// @audit ************** Possible Issue Line(s) **************
	L#26-27,  

/// @audit ****************** Affected Code *******************
  26:     int256 internal constant LEFT_HALF_BIT_MASK_INT =
  27:         int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

```

*GitHub* : [17-302](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L17-L302)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.slitherConstructorConstantVariables() (contracts/types/TokenId.sol#60-600) uses literals with too many digits:
	- CHUNK_MASK = 0xFFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_0000000000000000 (contracts/types/TokenId.sol#74-75)

/// @audit ************** Possible Issue Line(s) **************
	L#74-75,  

/// @audit ****************** Affected Code *******************
  74:     uint256 internal constant CHUNK_MASK =
  75:         0xFFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_0000000000000000;

```

*GitHub* : [60-600](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L60-L600)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.clearLeg(TokenId,uint256) (contracts/types/TokenId.sol#464-491) uses literals with too many digits:
	- TokenId.wrap(TokenId.unwrap(self) & 0xFFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFFFFFF) (contracts/types/TokenId.sol#466-470)

/// @audit ************** Possible Issue Line(s) **************
	L#466-470,  

/// @audit ****************** Affected Code *******************
 466:             return
 467:                 TokenId.wrap(
 468:                     TokenId.unwrap(self) &
 469:                         0xFFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFFFFFF
 470:                 );

```

*GitHub* : [464-491](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L464-L491)

```solidity
File: contracts/PanopticPool.sol

/// @audit ******************* Issue Detail *******************
PanopticPool.startPool(IUniswapV3Pool,address,address,CollateralTracker,CollateralTracker) (contracts/PanopticPool.sol#291-327) uses literals with too many digits:
	- s_miniMedian = (uint256(block.timestamp) << 216) + (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) + (uint256(uint24(currentTick)) << 24) + (uint256(uint24(currentTick))) (contracts/PanopticPool.sol#308-314)

/// @audit ************** Possible Issue Line(s) **************
	L#308-314,  

/// @audit ****************** Affected Code *******************
 308:             s_miniMedian =
 309:                 (uint256(block.timestamp) << 216) +
 310:                 // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
 311:                 // see comment on s_miniMedian initialization for format of this magic number
 312:                 (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
 313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4
 314:                 (uint256(uint24(currentTick))); // add to slot 3

```

*GitHub* : [291-327](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L291-L327)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv192(uint256,uint256) (contracts/libraries/Math.sol#675-732) uses literals with too many digits:
	- remainder = mulmod(uint256,uint256,uint256)(a,b,0x1000000000000000000000000000000000000000000000000) (contracts/libraries/Math.sol#711)

/// @audit ************** Possible Issue Line(s) **************
	L#711,  

/// @audit ****************** Affected Code *******************
 711:                 remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)

```

*GitHub* : [675-732](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L675-L732)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath.slitherConstructorConstantVariables() (contracts/libraries/PanopticMath.sol#18-967) uses literals with too many digits:
	- TICKSPACING_MASK = 0xFFFF000000000000 (contracts/libraries/PanopticMath.sol#26)

/// @audit ************** Possible Issue Line(s) **************
	L#26,  

/// @audit ****************** Affected Code *******************
  26:     uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;

```

*GitHub* : [18-967](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L18-L967)

```solidity
File: contracts/types/LiquidityChunk.sol

/// @audit ******************* Issue Detail *******************
LiquidityChunkLibrary.slitherConstructorConstantVariables() (contracts/types/LiquidityChunk.sol#52-194) uses literals with too many digits:
	- CLEAR_TU_MASK = 0xFFFFFF000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF (contracts/types/LiquidityChunk.sol#58-59)

/// @audit ************** Possible Issue Line(s) **************
	L#58-59,  

/// @audit ****************** Affected Code *******************
  58:     uint256 internal constant CLEAR_TU_MASK =
  59:         0xFFFFFF000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;

```

*GitHub* : [52-194](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L52-L194)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.slitherConstructorConstantVariables() (contracts/types/TokenId.sol#60-600) uses literals with too many digits:
	- LONG_MASK = 0x100_000000000100_000000000100_000000000100_0000000000000000 (contracts/types/TokenId.sol#62-63)

/// @audit ************** Possible Issue Line(s) **************
	L#62-63,  

/// @audit ****************** Affected Code *******************
  62:     uint256 internal constant LONG_MASK =
  63:         0x100_000000000100_000000000100_000000000100_0000000000000000;

```

*GitHub* : [60-600](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L60-L600)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv96(uint256,uint256) (contracts/libraries/Math.sol#521-578) uses literals with too many digits:
	- remainder = mulmod(uint256,uint256,uint256)(a,b,0x1000000000000000000000000) (contracts/libraries/Math.sol#557)

/// @audit ************** Possible Issue Line(s) **************
	L#557,  

/// @audit ****************** Affected Code *******************
 557:                 remainder := mulmod(a, b, 0x1000000000000000000000000)

```

*GitHub* : [521-578](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L521-L578)

```solidity
File: contracts/libraries/SafeTransferLib.sol

/// @audit ******************* Issue Detail *******************
SafeTransferLib.safeTransfer(address,address,uint256) (contracts/libraries/SafeTransferLib.sol#52-76) uses literals with too many digits:
	- mstore(uint256,uint256)(p_safeTransfer_asm_0,0xa9059cbb00000000000000000000000000000000000000000000000000000000) (contracts/libraries/SafeTransferLib.sol#60)

/// @audit ************** Possible Issue Line(s) **************
	L#60,  

/// @audit ****************** Affected Code *******************
  52:     function safeTransfer(address token, address to, uint256 amount) internal {
  53:         bool success;
  54: 
  55:         assembly ("memory-safe") {
  56:             // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
  57:             let p := mload(0x40)
  58: 
  59:             // Write the abi-encoded calldata into memory, beginning with the function selector.
  60:             mstore(p, 0xa9059cbb00000000000000000000000000000000000000000000000000000000)
  61:             mstore(add(4, p), to) // Append the "to" argument.
  62:             mstore(add(36, p), amount) // Append the "amount" argument.
  63: 
  64:             success := and(
  65:                 // Set success to whether the call reverted, if not we check it either
  66:                 // returned exactly 1 (can't just be non-zero data), or had no return data.
  67:                 or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
  68:                 // We use 68 because that's the total length of our calldata (4 + 32 * 2)
  69:                 // Counterintuitively, this call() must be positioned after the or() in the
  70:                 // surrounding and() because and() evaluates its arguments from right to left.
  71:                 call(gas(), token, 0, p, 68, 0, 32)
  72:             )
  73:         }
  74: 
  75:         if (!success) revert Errors.TransferFailed();
  76:     }

```

*GitHub* : [52-76](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L52-L76)

```solidity
File: contracts/libraries/Constants.sol

/// @audit ******************* Issue Detail *******************
Constants.slitherConstructorConstantVariables() (contracts/libraries/Constants.sol#7-23) uses literals with too many digits:
	- FP96 = 0x1000000000000000000000000 (contracts/libraries/Constants.sol#9)

/// @audit ************** Possible Issue Line(s) **************
	L#9,  

/// @audit ****************** Affected Code *******************
   7: library Constants {
   8:     /// @notice Fixed point multiplier: 2**96
   9:     uint256 internal constant FP96 = 0x1000000000000000000000000;
  10: 
  11:     /// @notice Minimum possible price tick in a Uniswap V3 pool
  12:     int24 internal constant MIN_V3POOL_TICK = -887272;
  13: 
  14:     /// @notice Maximum possible price tick in a Uniswap V3 pool
  15:     int24 internal constant MAX_V3POOL_TICK = 887272;
  16: 
  17:     /// @notice Minimum possible sqrtPriceX96 in a Uniswap V3 pool
  18:     uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;
  19: 
  20:     /// @notice Maximum possible sqrtPriceX96 in a Uniswap V3 pool
  21:     uint160 internal constant MAX_V3POOL_SQRT_RATIO =
  22:         1461446703485210103287273052203988822378723970342;
  23: }

```

*GitHub* : [7-23](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L7-L23)

```solidity
File: contracts/libraries/SafeTransferLib.sol

/// @audit ******************* Issue Detail *******************
SafeTransferLib.safeTransferFrom(address,address,address,uint256) (contracts/libraries/SafeTransferLib.sol#21-46) uses literals with too many digits:
	- mstore(uint256,uint256)(p_safeTransferFrom_asm_0,0x23b872dd00000000000000000000000000000000000000000000000000000000) (contracts/libraries/SafeTransferLib.sol#29)

/// @audit ************** Possible Issue Line(s) **************
	L#29,  

/// @audit ****************** Affected Code *******************
  29:             mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)

```

*GitHub* : [21-46](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L21-L46)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.slitherConstructorConstantVariables() (contracts/types/TokenId.sol#60-600) uses literals with too many digits:
	- OPTION_RATIO_MASK = 0x0000000000FE_0000000000FE_0000000000FE_0000000000FE_0000000000000000 (contracts/types/TokenId.sol#70-71)

/// @audit ************** Possible Issue Line(s) **************
	L#70-71,  

/// @audit ****************** Affected Code *******************
  70:     uint256 internal constant OPTION_RATIO_MASK =
  71:         0x0000000000FE_0000000000FE_0000000000FE_0000000000FE_0000000000000000;

```

*GitHub* : [60-600](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L60-L600)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv128(uint256,uint256) (contracts/libraries/Math.sol#598-655) uses literals with too many digits:
	- remainder = mulmod(uint256,uint256,uint256)(a,b,0x100000000000000000000000000000000) (contracts/libraries/Math.sol#634)

/// @audit ************** Possible Issue Line(s) **************
	L#634,  

/// @audit ****************** Affected Code *******************
 634:                 remainder := mulmod(a, b, 0x100000000000000000000000000000000)

```

*GitHub* : [598-655](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L598-L655)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.clearLeg(TokenId,uint256) (contracts/types/TokenId.sol#464-491) uses literals with too many digits:
	- TokenId.wrap(TokenId.unwrap(self) & 0xFFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF) (contracts/types/TokenId.sol#472-476)

/// @audit ************** Possible Issue Line(s) **************
	L#472-476,  

/// @audit ****************** Affected Code *******************
 472:             return
 473:                 TokenId.wrap(
 474:                     TokenId.unwrap(self) &
 475:                         0xFFFFFFFFFFFF_FFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
 476:                 );

```

*GitHub* : [464-491](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L464-L491)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.slitherConstructorConstantVariables() (contracts/types/TokenId.sol#60-600) uses literals with too many digits:
	- CLEAR_POOLID_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF_0000000000000000 (contracts/types/TokenId.sol#66-67)

/// @audit ************** Possible Issue Line(s) **************
	L#66-67,  

/// @audit ****************** Affected Code *******************
  66:     uint256 internal constant CLEAR_POOLID_MASK =
  67:         0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF_0000000000000000;

```

*GitHub* : [60-600](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L60-L600)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.clearLeg(TokenId,uint256) (contracts/types/TokenId.sol#464-491) uses literals with too many digits:
	- TokenId.wrap(TokenId.unwrap(self) & 0xFFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF) (contracts/types/TokenId.sol#478-482)

/// @audit ************** Possible Issue Line(s) **************
	L#478-482,  

/// @audit ****************** Affected Code *******************
 478:             return
 479:                 TokenId.wrap(
 480:                     TokenId.unwrap(self) &
 481:                         0xFFFFFFFFFFFF_000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
 482:                 );

```

*GitHub* : [464-491](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L464-L491)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mostSignificantNibble(uint160) (contracts/libraries/Math.sol#91-117) uses literals with too many digits:
	- x >= 0x100000000000000000000000000000000 (contracts/libraries/Math.sol#93)

/// @audit ************** Possible Issue Line(s) **************
	L#93,  

/// @audit ****************** Affected Code *******************
  93:             if (x >= 0x100000000000000000000000000000000) {

```

*GitHub* : [91-117](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L91-L117)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mostSignificantNibble(uint160) (contracts/libraries/Math.sol#91-117) uses literals with too many digits:
	- x >= 0x10000000000000000 (contracts/libraries/Math.sol#97)

/// @audit ************** Possible Issue Line(s) **************
	L#97,  

/// @audit ****************** Affected Code *******************
  97:             if (x >= 0x10000000000000000) {

```

*GitHub* : [91-117](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L91-L117)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mulDiv64(uint256,uint256) (contracts/libraries/Math.sol#458-515) uses literals with too many digits:
	- remainder = mulmod(uint256,uint256,uint256)(a,b,0x10000000000000000) (contracts/libraries/Math.sol#494)

/// @audit ************** Possible Issue Line(s) **************
	L#494,  

/// @audit ****************** Affected Code *******************
 494:                 remainder := mulmod(a, b, 0x10000000000000000)

```

*GitHub* : [458-515](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L458-L515)

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math.mostSignificantNibble(uint160) (contracts/libraries/Math.sol#91-117) uses literals with too many digits:
	- x >= 0x100000000 (contracts/libraries/Math.sol#101)

/// @audit ************** Possible Issue Line(s) **************
	L#101,  

/// @audit ****************** Affected Code *******************
 101:             if (x >= 0x100000000) {

```

*GitHub* : [91-117](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L91-L117)

```solidity
File: contracts/types/TokenId.sol

/// @audit ******************* Issue Detail *******************
TokenIdLibrary.clearLeg(TokenId,uint256) (contracts/types/TokenId.sol#464-491) uses literals with too many digits:
	- TokenId.wrap(TokenId.unwrap(self) & 0x000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF) (contracts/types/TokenId.sol#484-488)

/// @audit ************** Possible Issue Line(s) **************
	L#484-488,  

/// @audit ****************** Affected Code *******************
 484:             return
 485:                 TokenId.wrap(
 486:                     TokenId.unwrap(self) &
 487:                         0x000000000000_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFF_FFFFFFFFFFFFFFFF
 488:                 );

```

*GitHub* : [464-491](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L464-L491)

### [N-13]<a name="n-13"></a> Unused state variable

Unused state variable.  **Recom:** Remove unused state variables.

*There are 2 instance(s) of this issue:*

```solidity
File: contracts/libraries/Math.sol

/// @audit ******************* Issue Detail *******************
Math (contracts/libraries/Math.sol#13-782) has following non-used variables 
	- Math.MAX_UINT256 (contracts/libraries/Math.sol#15)

/// @audit ************** Possible Issue Line(s) **************
	L#15,  

/// @audit ****************** Affected Code *******************
  15:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```

*GitHub* : [13-782](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L13-L782)

```solidity
File: contracts/libraries/PanopticMath.sol

/// @audit ******************* Issue Detail *******************
PanopticMath (contracts/libraries/PanopticMath.sol#18-967) has following non-used variables 
	- PanopticMath.MAX_UINT256 (contracts/libraries/PanopticMath.sol#23)

/// @audit ************** Possible Issue Line(s) **************
	L#23,  

/// @audit ****************** Affected Code *******************
  23:     uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;

```

*GitHub* : [18-967](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L18-L967)

### [N-14]<a name="n-14"></a> Consider splitting complex checks into multiple steps

Simplify the complex checks to avoid errors. Assign the expression's parts to intermediate local variables, and check against those.

*There are 6 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||
                         (tokenType == 1 && currentValue0 < oracleValue0)

1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1346:                     ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1
                          ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1
                              ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

```



*GitHub* : [708](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L708-L709), [1060](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1060-L1060), [1346](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1346-L1347), [1374](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1374-L1375)

```solidity
File: contracts/libraries/PanopticMath.sol

357:                 tickLower % tickSpacing != 0 ||
                     tickUpper % tickSpacing != 0 ||
                     tickLower < minTick ||

```



*GitHub* : [357](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L357-L359)

```solidity
File: contracts/types/TokenId.sol

566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

```


*GitHub* : [566](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L566-L566)

### [N-15]<a name="n-15"></a> Constant decimal values

The use of fixed decimal values such as 1e18 or 1e8 in Solidity contracts can lead to inaccuracies, bugs, and vulnerabilities, particularly when interacting with tokens having different decimal configurations. Not all ERC20 tokens follow the standard 18 decimal places, and assumptions about decimal places can lead to miscalculations. Always retrieve and use the `decimals()` function from the token contract itself when performing calculations involving token amounts. This ensures that your contract correctly handles tokens with any number of decimal places, mitigating the risk of numerical errors or under/overflows that could jeopardize contract integrity and user funds.

*There are 12 instance(s) of this issue:*

```solidity
File: contracts/PanopticFactory.sol

86:     uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;

```



*GitHub* : [86](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L86-L86)

```solidity
File: contracts/libraries/Math.sol

137:             if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

139:             if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

141:             if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

145:             if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

153:             if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

155:             if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

157:             if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

161:             if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

167:             if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

171:             if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

173:             if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

```


*GitHub* : [137](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L137-L137), [139](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L139-L139), [141](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L141-L141), [145](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L145-L145), [153](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L153-L153), [155](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L155-L155), [157](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L157-L157), [161](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L161-L161), [167](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L167-L167), [171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L171-L171), [173](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L173-L173)

### [N-16]<a name="n-16"></a> Constants in comparisons should appear on the left side

Doing so will prevent [typo bugs](https://www.moserware.com/2008/01/constants-on-left-are-better-but-this.html) where the first '!', '>', '<', or '=' at the beginning of the operator is missing.

*There are 212 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

331:         if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

350:         if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

512:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

575:         return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;

664:                 if (positionId.isLong(leg) == 0) continue;

708:                     (tokenType == 0 && currentValue1 < oracleValue1) ||

709:                     (tokenType == 1 && currentValue0 < oracleValue0)

776:         if (utilization < 0) {

976:         if (assets > 0) {

1010:             if (tokenToPay > 0) {

1018:             } else if (tokenToPay < 0) {

1060:             if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {

1067:             if (tokenToPay > 0) {

1075:             } else if (tokenToPay < 0) {

1107:             if (intrinsicValue != 0) {

1168:         if (positionBalanceArray.length > 0) {

1173:             if (premiumAllPositions < 0) {

1182:         if (premiumAllPositions > 0) {

1325:         uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();

1328:         int64 utilization = tokenType == 0

1330:             : int64(uint64(poolUtilization >> 64));

1339:             if (isLong == 0) {

1346:                     ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1

1347:                     ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0

1362:                     uint160 ratio = tokenType == 1 // tokenType

1374:                         ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1

1375:                         ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0

1385:                                          |        <- ITM . <-ATM-> . OTM ->
                                 100% + SCR% - |--__           .    .    .

1451:             if (isLong == 1) {

1479:         if (isLong == 0) {

1488:         } else if (isLong == 1) {

1544:                 if (tokenType == 0) {

1559:                 if (tokenType == 1) {

1582:                 tokenType == 0 ? movedRight : movedLeft,

1584:                 tokenType == 0

1586:                     : int64(uint64(poolUtilization >> 64))

1619:                          |           <- ITM   .  OTM ->
                        100% - |--__                .

1632:             uint64 poolUtilization1 = uint64(poolUtilization >> 64);

1637:                 uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

1638:                 (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```



*GitHub* : [331](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L331-L331), [350](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L350-L350), [512](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L512-L512), [575](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L575-L575), [664](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L664-L664), [708](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L708-L708), [709](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L709-L709), [776](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L776-L776), [976](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L976-L976), [1010](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1010-L1010), [1018](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1018-L1018), [1060](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1060-L1060), [1067](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1067-L1067), [1075](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1075-L1075), [1107](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1107-L1107), [1168](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1168-L1168), [1173](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1173-L1173), [1182](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1182-L1182), [1325](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1325-L1325), [1328](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1328-L1328), [1330](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1330-L1330), [1339](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1339-L1339), [1346](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1346-L1346), [1347](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1347-L1347), [1362](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1362-L1362), [1374](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1374-L1374), [1375](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1375-L1375), [1385](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1385-L1386), [1451](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1451-L1451), [1479](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1479-L1479), [1488](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1488-L1488), [1544](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1544-L1544), [1559](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1559-L1559), [1582](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1582-L1582), [1584](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1584-L1584), [1586](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1586-L1586), [1619](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1619-L1620), [1632](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1632-L1632), [1637](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1637-L1637), [1638](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1638-L1638)

```solidity
File: contracts/PanopticFactory.sol

181:         if (amount0Owed > 0)

188:         if (amount1Owed > 0)

```



*GitHub* : [181](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L181-L181), [188](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L188-L188)

```solidity
File: contracts/PanopticPool.sol

309:                 (uint256(block.timestamp) << 216) +

313:                 (uint256(uint24(currentTick)) << 24) + // add to slot 4

370:         poolUtilization1 = uint64(balanceData.leftSlot() >> 64);

460:                 if (tokenId.isLong(leg) == 0 && !includePendingPremium) {

533:         if (medianData != 0) s_miniMedian = medianData;

638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

664:         if (medianData != 0) s_miniMedian = medianData;

730:             return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));

768:             if (isLong == 1) {

865:             if (tokenId.isLong(leg) == 0) {

1188:         if (touchedId.length != 1) revert Errors.InputListFail();

1274:         if (positionIdListExercisor.length > 0)

1415:         if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();

1445:         _numberOfPositions = (s_positionsHash[user] >> 248);

1483:         if (netLiquidity == 0) return;

1520:             if ((isLong == 1) || computeAllPremia) {

1566:                     if (isLong == 1) {

1596:         if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();

1679:             if (tokenId.isLong(leg) == 0) {

1780:                                     (accumulated0 == 0 ? type(uint256).max : accumulated0),

1789:                                     (accumulated1 == 0 ? type(uint256).max : accumulated1),

1862:             if (LeftRightSigned.unwrap(legPremia) != 0) {

1864:                 if (tokenId.isLong(leg) == 1) {

1928:                         s_grossPremiumLast[chunkKey] = totalLiquidity != 0

```



*GitHub* : [309](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L309-L309), [313](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L313-L313), [370](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L370-L370), [460](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L460-L460), [533](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L533-L533), [638](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L638-L638), [664](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L664-L664), [730](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L730-L730), [768](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L768-L768), [865](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L865-L865), [1188](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1188-L1188), [1274](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1274-L1274), [1415](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1415-L1415), [1445](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1445-L1445), [1483](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1483-L1483), [1520](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1520-L1520), [1566](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1566-L1566), [1596](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1596-L1596), [1679](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1679-L1679), [1780](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1780-L1780), [1789](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1789-L1789), [1862](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1862-L1862), [1864](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1864-L1864), [1928](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1928-L1928)

```solidity
File: contracts/SemiFungiblePositionManager.sol

219:         For an arbitrary parameter 0 <= ν <= 1 (ν = 1/2^VEGOID). This way, the gross_feesCollectedX128 will be given by: 

362:         if (s_AddrToPoolIdData[univ3pool] != 0) return;

412:         if (amount0Owed > 0)

419:         if (amount1Owed > 0)

446:         address token = amount0Delta > 0

453:         uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);

632:                 (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||

633:                 (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)

688:         if (positionSize == 0) revert Errors.OptionsBalanceZero();

717:             if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {

787:             if ((itm0 != 0) && (itm1 != 0)) {

819:                 zeroForOne = net0 < 0;

823:             } else if (itm0 != 0) {

824:                 zeroForOne = itm0 < 0;

827:                 zeroForOne = itm1 > 0;

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

999:             if (isLong == 0) {

1066:             moved = isLong == 0

1073:             if (tokenType == 1) {

1078:             if (tokenType == 0) {

1085:         if (currentLiquidity.rightSlot() > 0) {

1275:         if (isLong == 1) {

1279:         if (LeftRightSigned.unwrap(amountToCollect) != 0) {

1296:                 collected0 = movedInLeg.rightSlot() < 0

1299:                 collected1 = movedInLeg.leftSlot() < 0

1469:             if (netLiquidity != 0) {

1514:                 acctPremia = isLong == 1 ? premiumOwed : premiumGross;

1518:             acctPremia = isLong == 1

```



*GitHub* : [219](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L219-L219), [362](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L362-L362), [412](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L412-L412), [419](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L419-L419), [446](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L446-L446), [453](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L453-L453), [632](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L632-L632), [633](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L633-L633), [688](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L688-L688), [717](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L717-L717), [787](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L787-L787), [819](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L819-L819), [823](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L823-L823), [824](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L824-L824), [827](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L827-L827), [833](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L833-L833), [999](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L999-L999), [1066](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1066-L1066), [1073](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1073-L1073), [1078](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1078-L1078), [1085](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1085-L1085), [1275](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1275-L1275), [1279](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1279-L1279), [1296](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1296-L1296), [1299](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1299-L1299), [1469](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1469-L1469), [1514](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1514-L1514), [1518](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1518-L1518)

```solidity
File: contracts/libraries/FeesCalc.sol

67:                 if (tokenId.isLong(leg) == 0) {

```



*GitHub* : [67](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L67-L67)

```solidity
File: contracts/libraries/Math.sol

74:         return x > 0 ? x : -x;

83:             return x > 0 ? uint256(x) : uint256(-x);

93:             if (x >= 0x100000000000000000000000000000000) {

94:                 x >>= 128;

97:             if (x >= 0x10000000000000000) {

98:                 x >>= 64;

101:             if (x >= 0x100000000) {

102:                 x >>= 32;

105:             if (x >= 0x10000) {

106:                 x >>= 16;

109:             if (x >= 0x100) {

110:                 x >>= 8;

113:             if (x >= 0x10) {

130:             uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));

133:             uint256 sqrtR = absTick & 0x1 != 0

137:             if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;

139:             if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;

141:             if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;

143:             if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;

145:             if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;

147:             if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;

149:             if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;

151:             if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;

153:             if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;

155:             if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;

157:             if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;

159:             if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;

161:             if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;

163:             if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;

165:             if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;

167:             if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;

169:             if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;

171:             if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;

173:             if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;

176:             if (tick > 0) sqrtR = type(uint256).max / sqrtR;

179:             return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));

197:                     uint256(liquidityChunk.liquidity()) << 96,

312:         if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();

360:             if (prod1 == 0) {

361:                 require(denominator > 0);

447:             if (mulmod(a, b, denominator) > 0) {

474:             if (prod1 == 0) {

537:             if (prod1 == 0) {

587:             if (mulmod(a, b, 2 ** 96) > 0) {

614:             if (prod1 == 0) {

664:             if (mulmod(a, b, 2 ** 128) > 0) {

691:             if (prod1 == 0) {

```



*GitHub* : [74](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L74-L74), [83](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L83-L83), [93](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L93-L93), [94](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L94-L94), [97](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L97-L97), [98](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L98-L98), [101](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L101-L101), [102](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L102-L102), [105](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L105-L105), [106](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L106-L106), [109](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L109-L109), [110](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L110-L110), [113](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L113-L113), [130](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L130-L130), [133](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L133-L133), [137](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L137-L137), [139](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L139-L139), [141](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L141-L141), [143](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L143-L143), [145](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L145-L145), [147](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L147-L147), [149](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L149-L149), [151](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L151-L151), [153](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L153-L153), [155](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L155-L155), [157](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L157-L157), [159](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L159-L159), [161](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L161-L161), [163](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L163-L163), [165](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L165-L165), [167](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L167-L167), [169](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L169-L169), [171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L171-L171), [173](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L173-L173), [176](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L176-L176), [179](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L179-L179), [197](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L197-L197), [312](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L312-L312), [360](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L360-L360), [361](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L361-L361), [447](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L447-L447), [474](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L474-L474), [537](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L537-L537), [587](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L587-L587), [614](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L614-L614), [664](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L664-L664), [691](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L691-L691)

```solidity
File: contracts/libraries/PanopticMath.sol

50:             uint64 poolId = uint64(uint160(univ3pool) >> 112);

51:             poolId += uint64(uint24(tickSpacing)) << 48;

107:                     ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)

108:                     : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);

183:             if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

200:                 uint24 orderMap = uint24(medianData >> 192);

207:                 for (uint8 i; i < 8; ++i) {

211:                     if (rank == 7) {

227:                     (block.timestamp << 216) +

228:                     (uint256(newOrderMap) << 192) +

229:                     uint256(uint192(medianData << 24)) +

248:             for (uint256 i = 0; i < 20; ++i) {

256:             for (uint256 i = 0; i < 19; ++i) {

325:         if (tokenId.asset(legIndex) == 0) {

357:                 tickLower % tickSpacing != 0 ||

358:                 tickUpper % tickSpacing != 0 ||

425:         if (tokenType == 0) {

475:             uint256 notional = asset == 0

479:             if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();

532:                 return amount < 0 ? -absResult : absResult;

537:                 return amount < 0 ? -absResult : absResult;

555:                 return amount < 0 ? -absResult : absResult;

564:                 return amount < 0 ? -absResult : absResult;

584:         if (tokenId.asset(legIndex) == 0) {

615:         bool isShort = tokenId.isLong(legIndex) == 0;

618:         if (tokenId.tokenType(legIndex) == 0) {

669:                 uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);

785:                     if (tokenId.isLong(leg) == 1) {

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

864:                     if (tokenId.isLong(leg) == 1) {

931:             if (balanceShortage > 0) {

949:             if (balanceShortage > 0) {

```



*GitHub* : [50](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L50-L50), [51](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L51-L51), [107](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L107-L107), [108](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L108-L108), [183](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L183-L183), [200](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L200-L200), [207](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L207-L207), [211](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L211-L211), [227](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L227-L227), [228](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L228-L228), [229](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L229-L229), [248](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L248-L248), [256](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L256-L256), [325](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L325-L325), [357](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L357-L357), [358](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L358-L358), [425](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L425-L425), [475](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L475-L475), [479](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L479-L479), [532](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L532-L532), [537](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L537-L537), [555](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L555-L555), [564](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L564-L564), [584](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L584-L584), [615](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L615-L615), [618](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L618-L618), [669](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L669-L669), [785](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L785-L785), [856](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L856-L856), [857](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L857-L857), [864](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L864-L864), [931](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L931-L931), [949](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L949-L949)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

112:         if (to.code.length != 0) {

163:         if (to.code.length != 0) {

202:             interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165

203:             interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155

222:         if (to.code.length != 0) {

```



*GitHub* : [112](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L112-L112), [163](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L163-L163), [202](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L202-L202), [203](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L203-L203), [222](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L222-L222)

```solidity
File: contracts/types/LeftRight.sol

102:         return uint128(LeftRightUnsigned.unwrap(self) >> 128);

109:         return int128(LeftRightSigned.unwrap(self) >> 128);

126:             return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));

136:             return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));

```



*GitHub* : [102](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L102-L102), [109](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L109-L109), [126](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L126-L126), [136](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L136-L136)

```solidity
File: contracts/types/LiquidityChunk.sol

78:                     (uint256(uint24(_tickLower)) << 232) +

79:                         (uint256(uint24(_tickUpper)) << 208) +

109:                     LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

126:                     LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

173:             return int24(int256(LiquidityChunk.unwrap(self) >> 232));

182:             return int24(int256(LiquidityChunk.unwrap(self) >> 208));

```



*GitHub* : [78](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L78-L78), [79](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L79-L79), [109](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L109-L109), [126](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L126-L126), [173](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L173-L173), [182](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L182-L182)

```solidity
File: contracts/types/TokenId.sol

98:             return int24(uint24((TokenId.unwrap(self) >> 48) % 2 ** 16));

195:             return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

376:             if (optionRatios < 2 ** 64) {

378:             } else if (optionRatios < 2 ** 112) {

380:             } else if (optionRatios < 2 ** 160) {

382:             } else if (optionRatios < 2 ** 208) {

439:         if (optionRatios < 2 ** 64) {

441:         } else if (optionRatios < 2 ** 112) {

443:         } else if (optionRatios < 2 ** 160) {

445:         } else if (optionRatios < 2 ** 208) {

465:         if (i == 0)

471:         if (i == 1)

477:         if (i == 2)

483:         if (i == 3)

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

506:             uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;

507:             for (uint256 i = 0; i < 4; ++i) {

508:                 if (self.optionRatio(i) == 0) {

512:                     if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)

528:                 if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);

566:                     if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))

592:                     if (self.isLong(i) == 1) return; // validated

```


*GitHub* : [98](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L98-L98), [195](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L195-L195), [376](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L376-L376), [378](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L378-L378), [380](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L380-L380), [382](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L382-L382), [439](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L439-L439), [441](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L441-L441), [443](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L443-L443), [445](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L445-L445), [465](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L465-L465), [471](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L471-L471), [477](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L477-L477), [483](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L483-L483), [501](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L501-L501), [506](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L506-L506), [507](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L507-L507), [508](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L508-L508), [512](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L512-L512), [528](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L528-L528), [566](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L566-L566), [592](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L592-L592)

### [N-17]<a name="n-17"></a> Consider adding emergency-stop functionality

Adding a way to quickly halt protocol functionality in an emergency, rather than having to pause individual contracts one-by-one, will make in-progress hack mitigation faster and much less stressful.

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/multicall/Multicall.sol

8: abstract contract Multicall {

```



*GitHub* : [8](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L8-L8)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

11: abstract contract ERC1155 {

```



*GitHub* : [11](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L11-L11)

```solidity
File: contracts/tokens/ERC20Minimal.sol

9: abstract contract ERC20Minimal {

```


*GitHub* : [9](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L9-L9)

### [N-18]<a name="n-18"></a> Consider making contracts `Upgradeable`

This allows for bugs to be fixed in production, at the expense of _significantly_ increasing centralization.

*There are 3 instance(s) of this issue:*

```solidity
File: contracts/multicall/Multicall.sol

8: abstract contract Multicall {

```



*GitHub* : [8](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L8-L8)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

11: abstract contract ERC1155 {

```



*GitHub* : [11](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L11-L11)

```solidity
File: contracts/tokens/ERC20Minimal.sol

9: abstract contract ERC20Minimal {

```


*GitHub* : [9](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L9-L9)

### [N-19]<a name="n-19"></a> Consider using descriptive `constant`s when passing zero as a function argument

Passing zero as a function argument can sometimes result in a security issue (e.g. passing zero as the slippage parameter). Consider using a `constant` variable with a descriptive name, so it's clear that the argument is intentionally being used, and for the right reasons.

*There are 94 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

713:                             .wrap(0)

```



*GitHub* : [713](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L713-L713)

```solidity
File: contracts/PanopticFactory.sol

224:         if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();

227:         if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();

229:         if (address(s_getPanopticPool[v3Pool]) != address(0))

```



*GitHub* : [224](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L224-L224), [227](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L227-L227), [229](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L229-L229)

```solidity
File: contracts/PanopticPool.sol

299:         if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();

309:                 (uint256(block.timestamp) << 216) +
                     // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2

312:                 (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +

634:             revert Errors.InvalidTokenIdParameter(0);

655:             .wrap(0)

763:                     .wrap(0)

861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);

893:         _validatePositionList(user, positionIdList, 0);

1023:         _validatePositionList(liquidatee, positionIdList, 0);

1153:         _validatePositionList(msg.sender, positionIdListLiquidator, 0);

1166:             .wrap(0)

1227:         _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);

1546:                         .wrap(0)

1567:                         premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);

1592:         _validatePositionList(owner, positionIdList, 0);

1615:                 .wrap(0)

1634:                 .wrap(0)

1639:             s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1640:             s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

1707:                 (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
                          address(s_univ3pool),
                          address(this),
                          tokenId.tokenType(leg),
                          liquidityChunk.tickLower(),
                          liquidityChunk.tickUpper(),
                          type(int24).max,
                          0
                      );

1726:                         .wrap(0)

1775:                     .wrap(0)

1930:                                 .wrap(0)

1931:                                 .toRightSlot(
                                          uint128(
                                              uint256(
                                                  Math.max(
                                                      (int256(
                                                          grossPremiumLast.rightSlot() *
                                                              totalLiquidityBefore
                                                      ) -
                                                          int256(
                                                              _premiumAccumulatorsByLeg[_leg][0] *
                                                                  positionLiquidity
                                                          )) + int256(legPremia.rightSlot() * 2 ** 64),
                                                      0
                                                  )

1948:                                 .toLeftSlot(
                                          uint128(
                                              uint256(
                                                  Math.max(
                                                      (int256(
                                                          grossPremiumLast.leftSlot() *
                                                              totalLiquidityBefore
                                                      ) -
                                                          int256(
                                                              _premiumAccumulatorsByLeg[_leg][1] *
                                                                  positionLiquidity
                                                          )) + int256(legPremia.leftSlot()) * 2 ** 64,
                                                      0
                                                  )

1966:                                 .wrap(0)

```



*GitHub* : [299](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L299-L299), [309](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L309-L310), [312](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L312-L312), [634](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L634-L634), [655](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L655-L655), [763](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L763-L763), [861](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L861-L861), [870](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L870-L870), [893](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L893-L893), [1023](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1023-L1023), [1153](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1153-L1153), [1166](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1166-L1166), [1227](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1227-L1227), [1546](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1546-L1546), [1567](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1567-L1567), [1592](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1592-L1592), [1615](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1615-L1615), [1634](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1634-L1634), [1639](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1639-L1639), [1640](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1640-L1640), [1707](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1707-L1715), [1726](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1726-L1726), [1775](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1775-L1775), [1930](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1930-L1930), [1931](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1931-L1944), [1948](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1948-L1961), [1966](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1966-L1966)

```solidity
File: contracts/SemiFungiblePositionManager.sol

355:         if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();

372:         while (address(s_poolContext[poolId].pool) != address(0)) {

645:             s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

648:             s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);

702:         if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

833:             if (swapAmount == 0) return LeftRightSigned.wrap(0);

848:             totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(

1039:                 .wrap(0)

1167:                 .wrap(0)

1175:                 .wrap(0)

1214:         movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

1241:             movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

1306:             collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(

1377:                         .wrap(0)

1401:                         .wrap(0)

```



*GitHub* : [355](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L355-L355), [372](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L372-L372), [645](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L645-L645), [648](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L648-L648), [702](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L702-L702), [833](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L833-L833), [848](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L848-L848), [1039](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1039-L1039), [1167](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1167-L1167), [1175](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1175-L1175), [1214](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1214-L1214), [1241](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1241-L1241), [1306](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1306-L1306), [1377](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1377-L1377), [1401](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1401-L1401)

```solidity
File: contracts/libraries/FeesCalc.sol

116:                 .wrap(0)

```



*GitHub* : [116](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L116-L116)

```solidity
File: contracts/libraries/Math.sol

354:                 let mm := mulmod(a, b, not(0))

405:                 twos := add(div(sub(0, twos), twos), 1)

468:                 let mm := mulmod(a, b, not(0))

494:                 remainder := mulmod(a, b, 0x10000000000000000)

531:                 let mm := mulmod(a, b, not(0))

557:                 remainder := mulmod(a, b, 0x1000000000000000000000000)

608:                 let mm := mulmod(a, b, not(0))

634:                 remainder := mulmod(a, b, 0x100000000000000000000000000000000)

685:                 let mm := mulmod(a, b, not(0))

711:                 remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)

740:             result := add(div(a, b), gt(mod(a, b), 0))

778:             quickSort(data, int256(0), int256(data.length - 1));

```



*GitHub* : [354](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L354-L354), [405](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L405-L405), [468](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L468-L468), [494](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L494-L494), [531](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L531-L531), [557](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L557-L557), [608](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L608-L608), [634](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L634-L634), [685](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L685-L685), [711](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L711-L711), [740](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L740-L740), [778](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L778-L778)

```solidity
File: contracts/libraries/PanopticMath.sol

77:             return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));

598:         return LeftRightUnsigned.wrap(0).toRightSlot(amount0).toLeftSlot(amount1);

671:                 (uint256 balanceCross, uint256 thresholdCross) = PanopticMath.convertCollateralData(
                         tokenData0,
                         tokenData1,
                         0,
                         sqrtPriceX96Twap
                     );

695:             int256 balance1 = int256(uint256(tokenData1.rightSlot())) -
                     Math.max(premia.leftSlot(), 0);

749:                 LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(

791:             int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);

792:             int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

880:                                 tokenId.strike(0),

881:                                 tokenId.width(0),

882:                                 tokenId.tokenType(0)

888:                         settled0 = Math.max(
                                 0,
                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0

892:                         settled1 = Math.max(
                                 0,
                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1

898:                             LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(

934:                         .wrap(0)

952:                         .wrap(0)

```



*GitHub* : [77](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L77-L77), [598](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L598-L598), [671](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L671-L676), [695](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L695-L696), [749](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L749-L749), [791](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L791-L791), [792](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L792-L792), [856](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L856-L856), [857](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L857-L857), [880](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L880-L880), [881](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L881-L881), [882](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L882-L882), [888](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L888-L890), [892](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L892-L894), [898](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L898-L898), [934](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L934-L934), [952](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L952-L952)

```solidity
File: contracts/libraries/SafeTransferLib.sol

26:             let p := mload(0x40)

29:             mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)

30:             mstore(add(4, p), from) // Append the "from" argument.
                mstore(add(36, p), to) // Append the "to" argument.
                mstore(add(68, p), amount) // Append the "amount" argument.
    
                success := and(
                    // Set success to whether the call reverted, if not we check it either
                    // returned exactly 1 (can't just be non-zero data), or had no return data.
                    or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
                    // We use 100 because that's the total length of our calldata (4 + 32 * 3)
                    // Counterintuitively, this call() must be positioned after the or() in the
                    // surrounding and() because and() evaluates its arguments from right to left.
                    call(gas(), token, 0, p, 100, 0, 32)

57:             let p := mload(0x40)

60:             mstore(p, 0xa9059cbb00000000000000000000000000000000000000000000000000000000)

61:             mstore(add(4, p), to) // Append the "to" argument.
                mstore(add(36, p), amount) // Append the "amount" argument.
    
                success := and(
                    // Set success to whether the call reverted, if not we check it either
                    // returned exactly 1 (can't just be non-zero data), or had no return data.
                    or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
                    // We use 68 because that's the total length of our calldata (4 + 32 * 2)
                    // Counterintuitively, this call() must be positioned after the or() in the
                    // surrounding and() because and() evaluates its arguments from right to left.
                    call(gas(), token, 0, p, 68, 0, 32)

```



*GitHub* : [26](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L26-L26), [29](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L29-L29), [30](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L30-L41), [57](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L57-L57), [60](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L60-L60), [61](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L61-L71)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

220:         emit TransferSingle(msg.sender, address(0), to, id, amount);

224:                 ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=

239:         emit TransferSingle(msg.sender, from, address(0), id, amount);

```



*GitHub* : [220](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L220-L220), [224](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L224-L224), [239](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L239-L239)

```solidity
File: contracts/tokens/ERC20Minimal.sol

130:         emit Transfer(address(0), to, amount);

145:         emit Transfer(from, address(0), amount);

```



*GitHub* : [130](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L130-L130), [145](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L145-L145)

```solidity
File: contracts/types/LeftRight.sol

27:         int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(

265:                 z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(
                         int128(Math.max(left128, 0))

294:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(

297:             LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(

```



*GitHub* : [27](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L27-L27), [265](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L265-L265), [265](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L265-L266), [294](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L294-L294), [297](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L297-L297)

```solidity
File: contracts/types/TokenId.sol

406:             return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);

501:         if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);

```


*GitHub* : [406](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L406-L406), [501](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L501-L501)

### [N-20]<a name="n-20"></a> Using abi.encodePacked can in hash function

Using abi.encodePacked can result in hash collision when used in hashing functions. Consider using abi.encode as this pads data to 32 byte segments.

*There are 9 instance(s) of this issue:*

```solidity
File: contracts/PanopticPool.sol

461:                     bytes32 chunkKey = keccak256(
                             abi.encodePacked(

1642:             bytes32 chunkKey = keccak256(
                      abi.encodePacked(

1673:             bytes32 chunkKey = keccak256(
                      abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

1855:             bytes32 chunkKey = keccak256(
                      abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))

```



*GitHub* : [461](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L461-L462), [1642](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1642-L1643), [1673](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1673-L1674), [1855](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1855-L1856)

```solidity
File: contracts/SemiFungiblePositionManager.sol

611:             bytes32 positionKey_from = keccak256(
                     abi.encodePacked(

620:             bytes32 positionKey_to = keccak256(
                     abi.encodePacked(

974:         bytes32 positionKey = keccak256(
                 abi.encodePacked(

1150:                 keccak256(
                          abi.encodePacked(

```



*GitHub* : [611](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L611-L612), [620](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L620-L621), [974](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L974-L975), [1150](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1150-L1151)

```solidity
File: contracts/libraries/PanopticMath.sol

878:                         bytes32 chunkKey = keccak256(
                                 abi.encodePacked(

```


*GitHub* : [878](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L878-L879)

### [N-21]<a name="n-21"></a> Use of `override` is unnecessary

Starting with Solidity version [0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), using the `override` keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

323:     function transfer(
             address recipient,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

```



*GitHub* : [323](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L323-L326), [341](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L341-L345)

```solidity
File: contracts/SemiFungiblePositionManager.sol

540:     function safeTransferFrom(
             address from,
             address to,
             uint256 id,
             uint256 amount,
             bytes calldata data
         ) public override {

566:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public override {

```


*GitHub* : [540](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L540-L546), [566](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566-L572)

### [N-22]<a name="n-22"></a> Consider using a `struct` rather than having many function input parameters

Often times, a subset of the parameters would be more clear if they were passed as a struct.

*There are 109 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

221:     function startToken(
             bool underlyingIsToken0,
             address token0,
             address token1,
             uint24 fee,
             PanopticPool panopticPool
         ) external {

341:     function transferFrom(
             address from,
             address to,
             uint256 amount
         ) public override(ERC20Minimal) returns (bool) {

531:     function withdraw(
             uint256 assets,
             address receiver,
             address owner
         ) external returns (uint256 shares) {

591:     function redeem(
             uint256 shares,
             address receiver,
             address owner
         ) external returns (uint256 assets) {

650:     function exerciseCost(
             int24 currentTick,
             int24 oracleTick,
             TokenId positionId,
             uint128 positionBalance,
             LeftRightSigned longAmounts
         ) external view returns (LeftRightSigned exerciseFees) {

864:     function delegate(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {

911:     function revoke(
             address delegator,
             address delegatee,
             uint256 assets
         ) external onlyPanopticPool {

975:     function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {

995:     function takeCommissionAddData(
             address optionOwner,
             int128 longAmount,
             int128 shortAmount,
             int128 swappedAmount
         ) external onlyPanopticPool returns (int256 utilization) {

1043:     function exercise(
              address optionOwner,
              int128 longAmount,
              int128 shortAmount,
              int128 swappedAmount,
              int128 realizedPremium
          ) external onlyPanopticPool returns (int128) {

1096:     function _getExchangedAmount(
              int128 longAmount,
              int128 shortAmount,
              int128 swappedAmount
          ) internal view returns (int256 exchangedAmount) {

1141:     function getAccountMarginDetails(
              address user,
              int24 currentTick,
              uint256[2][] memory positionBalanceArray,
              int128 premiumAllPositions
          ) public view returns (LeftRightUnsigned tokenData) {

1159:     function _getAccountMargin(
              address user,
              int24 atTick,
              uint256[2][] memory positionBalanceArray,
              int128 premiumAllPositions
          ) internal view returns (LeftRightUnsigned tokenData) {

1245:     function _getRequiredCollateralAtTickSinglePosition(
              TokenId tokenId,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 tokenRequired) {

1278:     function _getRequiredCollateralSingleLeg(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 required) {

1311:     function _getRequiredCollateralSingleLegNoPartner(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 required) {

1439:     function _getRequiredCollateralSingleLegPartner(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 required) {

1473:     function _getRequiredCollateralAtUtilization(
              uint128 amount,
              uint256 isLong,
              int256 utilization
          ) internal view returns (uint256 required) {

1510:     function _computeSpread(
              TokenId tokenId,
              uint128 positionSize,
              uint256 index,
              uint256 partnerIndex,
              uint128 poolUtilization
          ) internal view returns (uint256 spreadRequirement) {

1600:     function _computeStrangle(
              TokenId tokenId,
              uint256 index,
              uint128 positionSize,
              int24 atTick,
              uint128 poolUtilization
          ) internal view returns (uint256 strangleRequired) {

```



*GitHub* : [221](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L221-L227), [341](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L341-L345), [531](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L531-L535), [591](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L591-L595), [650](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L650-L656), [864](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L864-L868), [911](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L911-L915), [975](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L975-L975), [995](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L995-L1000), [1043](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1043-L1049), [1096](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1096-L1100), [1141](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1141-L1146), [1159](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1159-L1164), [1245](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1245-L1250), [1278](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1278-L1284), [1311](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1311-L1317), [1439](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1439-L1445), [1473](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1473-L1477), [1510](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1510-L1516), [1600](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1600-L1606)

```solidity
File: contracts/PanopticFactory.sol

172:     function uniswapV3MintCallback(
             uint256 amount0Owed,
             uint256 amount1Owed,
             bytes calldata data
         ) external {

210:     function deployNewPool(
             address token0,
             address token1,
             uint24 fee,
             bytes32 salt
         ) external returns (PanopticPool newPoolContract) {

290:     function minePoolAddress(
             bytes32 salt,
             uint256 loops,
             uint256 minTargetRarity
         ) external view returns (bytes32 bestSalt, uint256 highestRarity) {

335:     function _mintFullRange(
             IUniswapV3Pool v3Pool,
             address token0,
             address token1,
             uint24 fee
         ) internal returns (uint256, uint256) {

```



*GitHub* : [172](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L172-L176), [210](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L210-L215), [290](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L290-L294), [335](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L335-L340)

```solidity
File: contracts/PanopticPool.sol

291:     function startPool(
             IUniswapV3Pool _univ3pool,
             address token0,
             address token1,
             CollateralTracker collateralTracker0,
             CollateralTracker collateralTracker1
         ) external {

381:     function calculateAccumulatedFeesBatch(
             address user,
             bool includePendingPremium,
             TokenId[] calldata positionIdList
         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

410:     function calculatePortfolioValue(
             address user,
             int24 atTick,
             TokenId[] calldata positionIdList
         ) external view returns (int256 value0, int256 value1) {

429:     function _calculateAccumulatedPremia(
             address user,
             TokenId[] calldata positionIdList,
             bool computeAllPremia,
             bool includePendingPremium,
             int24 atTick
         ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

547:     function mintOptions(
             TokenId[] calldata positionIdList,
             uint128 positionSize,
             uint64 effectiveLiquidityLimitX32,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) external {

569:     function burnOptions(
             TokenId tokenId,
             TokenId[] calldata newPositionIdList,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) external {

586:     function burnOptions(
             TokenId[] calldata positionIdList,
             TokenId[] calldata newPositionIdList,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) external {

614:     function _mintOptions(
             TokenId[] calldata positionIdList,
             uint128 positionSize,
             uint64 effectiveLiquidityLimitX32,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal {

677:     function _mintInSFPMAndUpdateCollateral(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal returns (uint128) {

706:     function _payCommissionAndWriteData(
             TokenId tokenId,
             uint128 positionSize,
             LeftRightSigned totalSwapped
         ) internal returns (uint128) {

794:     function _burnAllOptionsFrom(
             address owner,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool commitLongSettled,
             TokenId[] calldata positionIdList
         ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

826:     function _burnOptions(
             bool commitLongSettled,
             TokenId tokenId,
             address owner,
             int24 tickLimitLow,
             int24 tickLimitHigh
         ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

887:     function _validateSolvency(
             address user,
             TokenId[] calldata positionIdList,
             uint256 buffer
         ) internal view returns (uint256 medianData) {

955:     function _burnAndHandleExercise(
             bool commitLongSettled,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             TokenId tokenId,
             uint128 positionSize,
             address owner
         )

1017:     function liquidate(
              TokenId[] calldata positionIdListLiquidator,
              address liquidatee,
              LeftRightUnsigned delegations,
              TokenId[] calldata positionIdList
          ) external {

1179:     function forceExercise(
              address account,
              TokenId[] calldata touchedId,
              TokenId[] calldata positionIdListExercisee,
              TokenId[] calldata positionIdListExercisor
          ) external {

1290:     function _checkSolvencyAtTick(
              address account,
              TokenId[] calldata positionIdList,
              int24 currentTick,
              int24 atTick,
              uint256 buffer
          ) internal view returns (bool) {

1339:     function _getSolvencyBalances(
              LeftRightUnsigned tokenData0,
              LeftRightUnsigned tokenData1,
              uint160 sqrtPriceX96
          ) internal pure returns (uint256 balanceCross, uint256 thresholdCross) {

1367:     function _validatePositionList(
              address account,
              TokenId[] calldata positionIdList,
              uint256 offset
          ) internal view {

1405:     function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {

1465:     function _checkLiquiditySpread(
              TokenId tokenId,
              uint256 leg,
              int24 tickLower,
              int24 tickUpper,
              uint64 effectiveLiquidityLimitX32
          ) internal view {

1503:     function _getPremia(
              TokenId tokenId,
              uint128 positionSize,
              address owner,
              bool computeAllPremia,
              int24 atTick
          )

1587:     function settleLongPremium(
              TokenId[] calldata positionIdList,
              address owner,
              uint256 legIndex
          ) external {

1666:     function _updateSettlementPostMint(
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize
          ) internal {

1757:     function _getAvailablePremium(
              uint256 totalLiquidity,
              LeftRightUnsigned settledTokens,
              LeftRightUnsigned grossPremiumLast,
              LeftRightUnsigned premiumOwed,
              uint256[2] memory premiumAccumulators
          ) internal pure returns (LeftRightUnsigned) {

1833:     function _updateSettlementPostBurn(
              address owner,
              TokenId tokenId,
              LeftRightUnsigned[4] memory collectedByLeg,
              uint128 positionSize,
              bool commitLongSettled
          ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {

```



*GitHub* : [291](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L291-L297), [381](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L381-L385), [410](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L410-L414), [429](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L429-L435), [547](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L547-L553), [569](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L569-L574), [586](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L586-L591), [614](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L614-L620), [677](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L677-L682), [706](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L706-L710), [794](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L794-L800), [826](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L826-L832), [887](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L887-L891), [955](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L955-L962), [1017](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1022), [1179](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1179-L1184), [1290](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1290-L1296), [1339](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1339-L1343), [1367](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1367-L1371), [1405](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1405-L1405), [1465](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1465-L1471), [1503](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1503-L1509), [1587](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587-L1591), [1666](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1666-L1670), [1757](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1757-L1763), [1833](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1833-L1839)

```solidity
File: contracts/SemiFungiblePositionManager.sol

350:     function initializeAMMPool(address token0, address token1, uint24 fee) external {

402:     function uniswapV3MintCallback(
             uint256 amount0Owed,
             uint256 amount1Owed,
             bytes calldata data
         ) external {

435:     function uniswapV3SwapCallback(
             int256 amount0Delta,
             int256 amount1Delta,
             bytes calldata data
         ) external {

471:     function burnTokenizedPosition(
             TokenId tokenId,
             uint128 positionSize,
             int24 slippageTickLimitLow,
             int24 slippageTickLimitHigh
         )

504:     function mintTokenizedPosition(
             TokenId tokenId,
             uint128 positionSize,
             int24 slippageTickLimitLow,
             int24 slippageTickLimitHigh
         )

540:     function safeTransferFrom(
             address from,
             address to,
             uint256 id,
             uint256 amount,
             bytes calldata data
         ) public override {

566:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public override {

593:     function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {

680:     function _validateAndForwardToAMM(
             TokenId tokenId,
             uint128 positionSize,
             int24 tickLimitLow,
             int24 tickLimitHigh,
             bool isBurn
         ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

863:     function _createPositionInAMM(
             IUniswapV3Pool univ3pool,
             TokenId tokenId,
             uint128 positionSize,
             bool isBurn
         )

958:     function _createLegInAMM(
             IUniswapV3Pool univ3pool,
             TokenId tokenId,
             uint256 leg,
             LiquidityChunk liquidityChunk,
             bool isBurn
         )

1110:     function _updateStoredPremia(
              bytes32 positionKey,
              LeftRightUnsigned currentLiquidity,
              LeftRightUnsigned collectedAmounts
          ) private {

1138:     function _getFeesBase(
              IUniswapV3Pool univ3pool,
              uint128 liquidity,
              LiquidityChunk liquidityChunk,
              bool roundUp
          ) private view returns (LeftRightSigned feesBase) {

1255:     function _collectAndWritePositionData(
              LiquidityChunk liquidityChunk,
              IUniswapV3Pool univ3pool,
              LeftRightUnsigned currentLiquidity,
              bytes32 positionKey,
              LeftRightSigned movedInLeg,
              uint256 isLong
          ) internal returns (LeftRightUnsigned collectedChunk) {

1421:     function getAccountLiquidity(
              address univ3pool,
              address owner,
              uint256 tokenType,
              int24 tickLower,
              int24 tickUpper
          ) external view returns (LeftRightUnsigned accountLiquidities) {

1449:     function getAccountPremium(
              address univ3pool,
              address owner,
              uint256 tokenType,
              int24 tickLower,
              int24 tickUpper,
              int24 atTick,
              uint256 isLong
          ) external view returns (uint128, uint128) {

1535:     function getAccountFeesBase(
              address univ3pool,
              address owner,
              uint256 tokenType,
              int24 tickLower,
              int24 tickUpper
          ) external view returns (int128 feesBase0, int128 feesBase1) {

```



*GitHub* : [350](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L350-L350), [402](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L402-L406), [435](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L435-L439), [471](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L471-L476), [504](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L504-L509), [540](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L540-L546), [566](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566-L572), [593](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L593-L593), [680](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L680-L686), [863](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L863-L868), [958](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L958-L964), [1110](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1110-L1114), [1138](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1138-L1143), [1255](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1255-L1262), [1421](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1421-L1427), [1449](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1449-L1457), [1535](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1535-L1541)

```solidity
File: contracts/libraries/CallbackLib.sol

30:     function validateCallback(
            address sender,
            IUniswapV3Factory factory,
            PoolFeatures memory features
        ) internal view {

```



*GitHub* : [30](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L30-L34)

```solidity
File: contracts/libraries/FeesCalc.sol

97:     function calculateAMMSwapFees(
            IUniswapV3Pool univ3pool,
            int24 currentTick,
            int24 tickLower,
            int24 tickUpper,
            uint128 liquidity
        ) public view returns (LeftRightSigned) {

130:     function _getAMMSwapFeesPerLiquidityCollected(
             IUniswapV3Pool univ3pool,
             int24 currentTick,
             int24 tickLower,
             int24 tickUpper
         ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {

```



*GitHub* : [97](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L97-L103), [130](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L130-L135)

```solidity
File: contracts/libraries/InteractionHelper.sol

24:     function doApprovals(
            SemiFungiblePositionManager sfpm,
            CollateralTracker ct0,
            CollateralTracker ct1,
            address token0,
            address token1
        ) external {

48:     function computeName(
            address token0,
            address token1,
            bool isToken0,
            uint24 fee,
            string memory prefix
        ) external view returns (string memory) {

```



*GitHub* : [24](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L24-L30), [48](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L48-L54)

```solidity
File: contracts/libraries/Math.sol

241:     function getLiquidityForAmount0(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount0
         ) internal pure returns (LiquidityChunk) {

271:     function getLiquidityForAmount1(
             int24 tickLower,
             int24 tickUpper,
             uint256 amount1
         ) internal pure returns (LiquidityChunk) {

340:     function mulDiv(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {

440:     function mulDivRoundingUp(
             uint256 a,
             uint256 b,
             uint256 denominator
         ) internal pure returns (uint256 result) {

753:     function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {

```



*GitHub* : [241](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L241-L245), [271](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L271-L275), [340](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L340-L344), [440](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L440-L444), [753](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L753-L753)

```solidity
File: contracts/libraries/PanopticMath.sol

92:     function updatePositionsHash(
            uint256 existingHash,
            TokenId tokenId,
            bool addFlag
        ) internal pure returns (uint256) {

125:     function computeMedianObservedPrice(
             IUniswapV3Pool univ3pool,
             uint256 observationIndex,
             uint256 observationCardinality,
             uint256 cardinality,
             uint256 period
         ) external view returns (int24) {

168:     function computeInternalMedian(
             uint256 observationIndex,
             uint256 observationCardinality,
             uint256 period,
             uint256 medianData,
             IUniswapV3Pool univ3pool
         ) external view returns (int24 medianTick, uint256 updatedMedianData) {

289:     function getLiquidityChunk(
             TokenId tokenId,
             uint256 legIndex,
             uint128 positionSize
         ) internal pure returns (LiquidityChunk) {

338:     function getTicks(
             int24 strike,
             int24 width,
             int24 tickSpacing
         ) internal pure returns (int24 tickLower, int24 tickUpper) {

419:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             uint160 sqrtPriceX96
         ) internal pure returns (uint256, uint256) {

445:     function convertCollateralData(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint256 tokenType,
             int24 tick
         ) internal pure returns (uint256, uint256) {

468:     function convertNotional(
             uint128 contractSize,
             int24 tickLower,
             int24 tickUpper,
             uint256 asset
         ) internal pure returns (uint128) {

574:     function getAmountsMoved(
             TokenId tokenId,
             uint128 positionSize,
             uint256 legIndex
         ) internal pure returns (LeftRightUnsigned) {

607:     function _calculateIOAmounts(
             TokenId tokenId,
             uint128 positionSize,
             uint256 legIndex
         ) internal pure returns (LeftRightSigned longs, LeftRightSigned shorts) {

651:     function getLiquidationBonus(
             LeftRightUnsigned tokenData0,
             LeftRightUnsigned tokenData1,
             uint160 sqrtPriceX96Twap,
             uint160 sqrtPriceX96Final,
             LeftRightSigned netExchanged,
             LeftRightSigned premia
         ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

768:     function haircutPremia(
             address liquidatee,
             TokenId[] memory positionIdList,
             LeftRightSigned[4][] memory premiasByLeg,
             LeftRightSigned collateralRemaining,
             CollateralTracker collateral0,
             CollateralTracker collateral1,
             uint160 sqrtPriceX96Final,
             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens

917:     function getRefundAmounts(
             address refunder,
             LeftRightSigned refundValues,
             int24 atTick,
             CollateralTracker collateral0,
             CollateralTracker collateral1
         ) external view returns (LeftRightSigned) {

```



*GitHub* : [92](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L92-L96), [125](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L125-L131), [168](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L168-L174), [289](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L289-L293), [338](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L338-L342), [419](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L419-L424), [445](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L445-L450), [468](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L468-L473), [574](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L574-L578), [607](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L607-L611), [651](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L651-L658), [768](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768-L776), [917](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L917-L923)

```solidity
File: contracts/libraries/SafeTransferLib.sol

21:     function safeTransferFrom(address token, address from, address to, uint256 amount) internal {

52:     function safeTransfer(address token, address to, uint256 amount) internal {

```



*GitHub* : [21](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L21-L21), [52](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L52-L52)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

94:     function safeTransferFrom(
            address from,
            address to,
            uint256 id,
            uint256 amount,
            bytes calldata data
        ) public virtual {

130:     function safeBatchTransferFrom(
             address from,
             address to,
             uint256[] calldata ids,
             uint256[] calldata amounts,
             bytes calldata data
         ) public virtual {

214:     function _mint(address to, uint256 id, uint256 amount) internal {

236:     function _burn(address from, uint256 id, uint256 amount) internal {

```



*GitHub* : [94](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L94-L100), [130](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L130-L136), [214](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L214-L214), [236](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L236-L236)

```solidity
File: contracts/tokens/ERC20Minimal.sol

81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

103:     function _transferFrom(address from, address to, uint256 amount) internal {

```



*GitHub* : [81](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L81-L81), [103](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L103-L103)

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol

13:     function issueNFT(
            address deployer,
            PanopticPool newPoolContract,
            address token0,
            address token1,
            uint24 fee
        ) external;

```



*GitHub* : [13](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L13-L19)

```solidity
File: contracts/types/LeftRight.sol

279:     function addCapped(
             LeftRightUnsigned x,
             LeftRightUnsigned dx,
             LeftRightUnsigned y,
             LeftRightUnsigned dy
         ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {

```



*GitHub* : [279](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L279-L284)

```solidity
File: contracts/types/LiquidityChunk.sol

70:     function createChunk(
            int24 _tickLower,
            int24 _tickUpper,
            uint128 amount
        ) internal pure returns (LiquidityChunk) {

```



*GitHub* : [70](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L70-L74)

```solidity
File: contracts/types/TokenId.sol

205:     function addAsset(
             TokenId self,
             uint256 _asset,
             uint256 legIndex
         ) internal pure returns (TokenId) {

221:     function addOptionRatio(
             TokenId self,
             uint256 _optionRatio,
             uint256 legIndex
         ) internal pure returns (TokenId) {

240:     function addIsLong(
             TokenId self,
             uint256 _isLong,
             uint256 legIndex
         ) internal pure returns (TokenId) {

255:     function addTokenType(
             TokenId self,
             uint256 _tokenType,
             uint256 legIndex
         ) internal pure returns (TokenId) {

273:     function addRiskPartner(
             TokenId self,
             uint256 _riskPartner,
             uint256 legIndex
         ) internal pure returns (TokenId) {

291:     function addStrike(
             TokenId self,
             int24 _strike,
             uint256 legIndex
         ) internal pure returns (TokenId) {

310:     function addWidth(
             TokenId self,
             int24 _width,
             uint256 legIndex
         ) internal pure returns (TokenId) {

336:     function addLeg(
             TokenId self,
             uint256 legIndex,
             uint256 _optionRatio,
             uint256 _asset,
             uint256 _isLong,
             uint256 _tokenType,
             uint256 _riskPartner,
             int24 _strike,
             int24 _width
         ) internal pure returns (TokenId tokenId) {

```


*GitHub* : [205](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L205-L209), [221](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L221-L225), [240](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L240-L244), [255](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L255-L259), [273](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L273-L277), [291](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L291-L295), [310](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L310-L314), [336](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L336-L346)

### [N-23]<a name="n-23"></a> Consider using named function arguments

When calling functions in external contracts with multiple arguments, consider using [named](https://docs.soliditylang.org/en/latest/control-structures.html#function-calls-with-named-parameters) function parameters, rather than positional ones.

*There are 97 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

292:             InteractionHelper.computeName(
                     s_univ3token0,
                     s_univ3token1,
                     s_underlyingIsToken0,
                     s_poolFee,
                     NAME_PREFIX
                 );

352:         return ERC20Minimal.transferFrom(from, to, amount);

380:         return Math.mulDiv(assets, totalSupply, totalAssets());

424:         SafeTransferLib.safeTransferFrom(
                 s_underlyingToken,
                 msg.sender,
                 address(s_panopticPool),

484:         SafeTransferLib.safeTransferFrom(
                 s_underlyingToken,
                 msg.sender,
                 address(s_panopticPool),

521:         return Math.mulDivRoundingUp(assets, supply, totalAssets());

687:                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                             positionId,
                             leg,
                             positionBalance
                         );

956:                 Math.mulDiv(
                         assets,
                         totalSupply - delegateeBalance,
                         uint256(Math.max(1, int256(totalAssets()) - int256(assets)))

1322:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

1411:                         uint256 c3 = Math.mulDivRoundingUp(
                                  amountMoved,
                                  scaleFactor - ratio,
                                  scaleFactor + Constants.FP96
                              );

1518:         LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);

1521:         LeftRightUnsigned amountsMovedPartner = PanopticMath.getAmountsMoved(
                  tokenId,
                  positionSize,
                  partnerIndex
              );

1579:         spreadRequirement = Math.max(
                  spreadRequirement,
                  _getRequiredCollateralAtUtilization(
                      tokenType == 0 ? movedRight : movedLeft,
                      1,
                      tokenType == 0
                          ? int64(uint64(poolUtilization))

```



*GitHub* : [292](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L292-L298), [352](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L352-L352), [380](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L380-L380), [424](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L424-L427), [484](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L484-L487), [521](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L521-L521), [687](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L687-L691), [956](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L956-L959), [1322](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1322-L1322), [1411](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1411-L1415), [1518](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1518-L1518), [1521](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1521-L1525), [1579](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1579-L1585)

```solidity
File: contracts/PanopticFactory.sol

179:         CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);

182:             SafeTransferLib.safeTransferFrom(
                     decoded.poolFeatures.token0,
                     decoded.payer,
                     msg.sender,
                     amount0Owed
                 );

189:             SafeTransferLib.safeTransferFrom(
                     decoded.poolFeatures.token1,
                     decoded.payer,
                     msg.sender,
                     amount1Owed
                 );

226:         IUniswapV3Pool v3Pool = IUniswapV3Pool(UNIV3_FACTORY.getPool(token0, token1, fee));

233:         SFPM.initializeAMMPool(token0, token1, fee);

248:         collateralTracker0.startToken(true, token0, token1, fee, newPoolContract);

249:         collateralTracker1.startToken(false, token0, token1, fee, newPoolContract);

251:         newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);

266:         DONOR_NFT.issueNFT(msg.sender, newPoolContract, token0, token1, fee);

357:                     Math.mulDivRoundingUp(
                             FULL_RANGE_LIQUIDITY_AMOUNT_WETH,
                             Constants.FP96,
                             currentSqrtPriceX96
                         )

369:                     Math.mulDivRoundingUp(
                             FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,
                             Constants.FP96,
                             currentSqrtPriceX96
                         )

396:         bytes memory mintCallback = abi.encode(
                 CallbackLib.CallbackData({
                     poolFeatures: CallbackLib.PoolFeatures({token0: token0, token1: token1, fee: fee}),

```



*GitHub* : [179](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L179-L179), [182](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L182-L187), [189](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L189-L194), [226](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L226-L226), [233](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L233-L233), [248](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L248-L248), [249](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L249-L249), [251](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L251-L251), [266](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L266-L266), [357](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L357-L361), [369](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L369-L373), [396](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L396-L398)

```solidity
File: contracts/PanopticPool.sol

326:         InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);

415:         (value0, value1) = FeesCalc.getPortfolioValue(
                 atTick,
                 s_positionBalance[user],
                 positionIdList
             );

525:         (, uint256 medianData) = PanopticMath.computeInternalMedian(
                 observationIndex,
                 observationCardinality,
                 MEDIAN_PERIOD,
                 s_miniMedian,
                 s_univ3pool
             );

686:             .mintTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);

905:         int24 fastOracleTick = PanopticMath.computeMedianObservedPrice(
                 _univ3pool,
                 observationIndex,
                 observationCardinality,
                 FAST_ORACLE_CARDINALITY,
                 FAST_ORACLE_PERIOD
             );

915:             slowOracleTick = PanopticMath.computeMedianObservedPrice(
                     _univ3pool,
                     observationIndex,
                     observationCardinality,
                     SLOW_ORACLE_CARDINALITY,
                     SLOW_ORACLE_PERIOD
                 );

923:             (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(
                     observationIndex,
                     observationCardinality,
                     MEDIAN_PERIOD,
                     s_miniMedian,
                     _univ3pool
                 );

971:             .burnTokenizedPosition(tokenId, positionSize, tickLimitLow, tickLimitHigh);

1046:             tokenData0 = s_collateralToken0.getAccountMarginDetails(
                      liquidatee,
                      twapTick,
                      positionBalanceArray,
                      premia.rightSlot()

1053:             tokenData1 = s_collateralToken1.getAccountMarginDetails(
                      liquidatee,
                      twapTick,
                      positionBalanceArray,
                      premia.leftSlot()

1072:         s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());

1073:         s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());

1099:                 .getLiquidationBonus(
                          tokenData0,
                          tokenData1,
                          Math.getSqrtRatioAtTick(twapTick),

1122:             (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(
                      _liquidatee,
                      _positionIdList,
                      premiasByLeg,
                      collateralRemaining,
                      s_collateralToken0,
                      s_collateralToken1,
                      Math.getSqrtRatioAtTick(_finalTick),

1141:         s_collateralToken0.revoke(
                  msg.sender,
                  liquidatee,
                  uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)

1146:         s_collateralToken1.revoke(
                  msg.sender,
                  liquidatee,
                  uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)

1231:         LeftRightSigned exerciseFees = s_collateralToken0.exerciseCost(
                  currentTick,
                  twapTick,
                  touchedId[0],
                  positionBalance,
                  longAmounts
              );

1242:         refundAmounts = PanopticMath.getRefundAmounts(
                  account,
                  refundAmounts,
                  twapTick,
                  s_collateralToken0,
                  s_collateralToken1
              );

1252:             s_collateralToken0.refund(
                      account,
                      msg.sender,
                      refundAmounts.rightSlot() - delegatedAmounts.rightSlot()

1257:             s_collateralToken1.refund(
                      account,
                      msg.sender,
                      refundAmounts.leftSlot() - delegatedAmounts.leftSlot()

1308:         LeftRightUnsigned tokenData0 = s_collateralToken0.getAccountMarginDetails(
                  account,
                  atTick,
                  positionBalanceArray,
                  portfolioPremium.rightSlot()

1314:         LeftRightUnsigned tokenData1 = s_collateralToken1.getAccountMarginDetails(
                  account,
                  atTick,
                  positionBalanceArray,
                  portfolioPremium.leftSlot()

1383:             fingerprintIncomingList = PanopticMath.updatePositionsHash(
                      fingerprintIncomingList,
                      positionIdList[i],
                      ADD
                  );

1410:         uint256 newHash = PanopticMath.updatePositionsHash(
                  s_positionsHash[account],
                  tokenId,
                  addFlag
              );

1521:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                          tokenId,
                          leg,
                          positionSize
                      );

1628:             .getLiquidityChunk(tokenId, legIndex, s_positionBalance[owner][tokenId].rightSlot())

1639:             s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1640:             s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());

1680:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                          tokenId,
                          leg,
                          positionSize
                      );

1878:                         .getLiquidityChunk(tokenId, leg, positionSize)

```



*GitHub* : [326](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L326-L326), [415](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L415-L419), [525](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L525-L531), [686](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L686-L686), [905](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L905-L911), [915](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L915-L921), [923](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L923-L929), [971](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L971-L971), [1046](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1046-L1050), [1053](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1053-L1057), [1072](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1072-L1072), [1073](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1073-L1073), [1099](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1099-L1102), [1122](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1122-L1129), [1141](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1141-L1144), [1146](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1146-L1149), [1231](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1231-L1237), [1242](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1242-L1248), [1252](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1252-L1255), [1257](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1257-L1260), [1308](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1308-L1312), [1314](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1314-L1318), [1383](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1383-L1387), [1410](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1410-L1414), [1521](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1521-L1525), [1628](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1628-L1628), [1639](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1639-L1639), [1640](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1640-L1640), [1680](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1680-L1684), [1878](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1878-L1878)

```solidity
File: contracts/SemiFungiblePositionManager.sol

352:         address univ3pool = FACTORY.getPool(token0, token1, fee);

410:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

413:             SafeTransferLib.safeTransferFrom(
                     decoded.poolFeatures.token0,
                     decoded.payer,
                     msg.sender,
                     amount0Owed
                 );

420:             SafeTransferLib.safeTransferFrom(
                     decoded.poolFeatures.token1,
                     decoded.payer,
                     msg.sender,
                     amount1Owed
                 );

443:         CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);

456:         SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);

555:         super.safeTransferFrom(from, to, id, amount, data);

584:         super.safeBatchTransferFrom(from, to, ids, amounts, data);

604:             LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                     id,
                     leg,
                     uint128(amount)

837:             (int256 swap0, int256 swap1) = _univ3pool.swap(
                     msg.sender,
                     zeroForOne,
                     swapAmount,
                     zeroForOne
                         ? Constants.MIN_V3POOL_SQRT_RATIO + 1
                         : Constants.MAX_V3POOL_SQRT_RATIO - 1,
                     data
                 );

904:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                         _tokenId,
                         _leg,
                         _positionSize
                     );

1124:             .addCapped(
                      s_accountPremiumOwed[positionKey],
                      deltaPremiumOwed,
                      s_accountPremiumGross[positionKey],
                      deltaPremiumGross
                  );

1350:                 premium0X64_base = Math.mulDiv(
                          collected0,
                          totalLiquidity * 2 ** 64,
                          netLiquidity ** 2
                      );

1355:                 premium1X64_base = Math.mulDiv(
                          collected1,
                          totalLiquidity * 2 ** 64,
                          netLiquidity ** 2
                      );

1370:                         .mulDiv(premium0X64_base, numerator, totalLiquidity)

1373:                         .mulDiv(premium1X64_base, numerator, totalLiquidity)

1394:                         .mulDiv(premium0X64_base, numerator, totalLiquidity ** 2)

1397:                         .mulDiv(premium1X64_base, numerator, totalLiquidity ** 2)

1431:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

1459:             abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)

1480:                     LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(
                              _univ3pool,
                              atTick,
                              _tickLower,
                              _tickUpper,
                              netLiquidity
                          );

1507:                 (premiumOwed, premiumGross) = LeftRightLibrary.addCapped(
                          s_accountPremiumOwed[positionKey],
                          premiumOwed,
                          s_accountPremiumGross[positionKey],
                          premiumGross
                      );

1544:             keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

```



*GitHub* : [352](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L352-L352), [410](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L410-L410), [413](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L413-L418), [420](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L420-L425), [443](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L443-L443), [456](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L456-L456), [555](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L555-L555), [584](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L584-L584), [604](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L604-L607), [837](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L837-L845), [904](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L904-L908), [1124](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1124-L1129), [1350](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1350-L1354), [1355](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1355-L1359), [1370](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1370-L1370), [1373](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1373-L1373), [1394](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1394-L1394), [1397](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1397-L1397), [1431](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1431-L1431), [1459](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1459-L1459), [1480](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1480-L1486), [1507](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1507-L1512), [1544](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1544-L1544)

```solidity
File: contracts/libraries/CallbackLib.sol

36:         if (factory.getPool(features.token0, features.token1, features.fee) != sender)

```



*GitHub* : [36](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L36-L36)

```solidity
File: contracts/libraries/FeesCalc.sol

56:                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                        tokenId,
                        leg,
                        positionSize
                    );

```



*GitHub* : [56](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L56-L60)

```solidity
File: contracts/libraries/InteractionHelper.sol

72:                 string.concat(
                        prefix,
                        " ",
                        isToken0 ? symbol0 : symbol1,
                        " LP on ",
                        symbol0,
                        "/",
                        symbol1,
                        " ",
                        Strings.toString(fee),

```



*GitHub* : [72](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L72-L81)

```solidity
File: contracts/libraries/Math.sol

251:                 LiquidityChunkLibrary.createChunk(
                         tickLower,
                         tickUpper,
                         toUint128(
                             mulDiv(
                                 amount0,
                                 mulDiv96(highPriceX96, lowPriceX96),

281:                 LiquidityChunkLibrary.createChunk(
                         tickLower,
                         tickUpper,
                         toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))

```



*GitHub* : [251](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L251-L257), [281](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L281-L284)

```solidity
File: contracts/libraries/PanopticMath.sol

326:             return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);

328:             return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);

497:                 return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

512:                 return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);

514:                 return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));

588:                 .getAmount1ForLiquidity(Math.getLiquidityForAmount0(tickLower, tickUpper, amount0))

594:                 .getAmount0ForLiquidity(Math.getLiquidityForAmount1(tickLower, tickUpper, amount1))

671:                 (uint256 balanceCross, uint256 thresholdCross) = PanopticMath.convertCollateralData(
                         tokenData0,
                         tokenData1,
                         0,
                         sqrtPriceX96Twap
                     );

715:                     bonus1 += Math.min(
                             balance1 - paid1,
                             PanopticMath.convert0to1(paid0 - balance0, sqrtPriceX96Final)

733:                     bonus0 += Math.min(
                             balance0 - paid0,
                             PanopticMath.convert1to0(paid1 - balance1, sqrtPriceX96Final)

856:                 if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));

857:                 if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));

```



*GitHub* : [326](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L326-L326), [328](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L328-L328), [497](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L497-L497), [512](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L512-L512), [514](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L514-L514), [588](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L588-L588), [594](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L594-L594), [671](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L671-L676), [715](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L715-L717), [733](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L733-L735), [856](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L856-L856), [857](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L857-L857)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

114:                 ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=

165:                 ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=

```


*GitHub* : [114](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L114-L114), [165](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L165-L165)

### [N-24]<a name="n-24"></a> Consider using named returns

Using named returns in Solidity functions enhances code readability and clarity. By explicitly naming return variables in the function signature, developers can document what each return value represents, making the code easier to understand and maintain. This practice can also slightly optimize gas usage by avoiding extra variable declarations.

*There are 98 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

310:     function decimals() external view returns (uint8) {

326:     ) public override(ERC20Minimal) returns (bool) {

345:     ) public override(ERC20Minimal) returns (bool) {

1049:     ) external onlyPanopticPool returns (int128) {

```



*GitHub* : [310](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L310-L310), [326](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L326-L326), [345](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L345-L345), [1049](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1049-L1049)

```solidity
File: contracts/PanopticFactory.sol

159:     function owner() external view returns (address) {

340:     ) internal returns (uint256, uint256) {

420:     function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {

```



*GitHub* : [159](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L159-L159), [340](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L340-L340), [420](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L420-L420)

```solidity
File: contracts/PanopticPool.sol

502:     ) internal pure returns (int24, int24) {

682:     ) internal returns (uint128) {

710:     ) internal returns (uint128) {

1296:     ) internal view returns (bool) {

1425:     function univ3pool() external view returns (IUniswapV3Pool) {

1437:     function collateralToken1() external view returns (CollateralTracker) {

1763:     ) internal pure returns (LeftRightUnsigned) {

```



*GitHub* : [502](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L502-L502), [682](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L682-L682), [710](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L710-L710), [1296](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1296-L1296), [1425](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1425-L1425), [1437](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1437-L1437), [1763](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1763-L1763)

```solidity
File: contracts/SemiFungiblePositionManager.sol

1457:     ) external view returns (uint128, uint128) {

```



*GitHub* : [1457](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1457-L1457)

```solidity
File: contracts/libraries/FeesCalc.sol

103:     ) public view returns (LeftRightSigned) {

```



*GitHub* : [103](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L103-L103)

```solidity
File: contracts/libraries/InteractionHelper.sol

107:     function computeDecimals(address token) external view returns (uint8) {

```



*GitHub* : [107](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L107-L107)

```solidity
File: contracts/libraries/Math.sol

25:     function min24(int24 a, int24 b) internal pure returns (int24) {

33:     function max24(int24 a, int24 b) internal pure returns (int24) {

41:     function min(uint256 a, uint256 b) internal pure returns (uint256) {

49:     function min(int256 a, int256 b) internal pure returns (int256) {

57:     function max(uint256 a, uint256 b) internal pure returns (uint256) {

65:     function max(int256 a, int256 b) internal pure returns (int256) {

73:     function abs(int256 x) internal pure returns (int256) {

81:     function absUint(int256 x) internal pure returns (uint256) {

128:     function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {

191:     function getAmount0ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

207:     function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {

245:     ) internal pure returns (LiquidityChunk) {

275:     ) internal pure returns (LiquidityChunk) {

325:     function toInt256(uint256 toCast) internal pure returns (int256) {

458:     function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {

521:     function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {

598:     function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {

675:     function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {

```



*GitHub* : [25](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L25-L25), [33](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L33-L33), [41](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L41-L41), [49](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L49-L49), [57](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L57-L57), [65](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L65-L65), [73](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L73-L73), [81](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L81-L81), [128](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L128-L128), [191](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L191-L191), [207](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L207-L207), [245](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L245-L245), [275](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L275-L275), [325](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L325-L325), [458](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L458-L458), [521](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L521-L521), [598](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L598-L598), [675](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L675-L675)

```solidity
File: contracts/libraries/PanopticMath.sol

47:     function getPoolId(address univ3pool) internal view returns (uint64) {

59:     function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {

75:     function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {

96:     ) internal pure returns (uint256) {

131:     ) external view returns (int24) {

241:     function twapFilter(IUniswapV3Pool univ3pool, uint32 twapWindow) external view returns (int24) {

293:     ) internal pure returns (LiquidityChunk) {

374:     ) internal pure returns (int24, int24) {

424:     ) internal pure returns (uint256, uint256) {

450:     ) internal pure returns (uint256, uint256) {

473:     ) internal pure returns (uint128) {

490:     function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

507:     function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {

524:     function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

547:     function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {

578:     ) internal pure returns (LeftRightUnsigned) {

777:     ) external returns (int256, int256) {

923:     ) external view returns (LeftRightSigned) {

```



*GitHub* : [47](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L47-L47), [59](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L59-L59), [75](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L75-L75), [96](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L96-L96), [131](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L131-L131), [241](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L241-L241), [293](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L293-L293), [374](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L374-L374), [424](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L424-L424), [450](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L450-L450), [473](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L473-L473), [490](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L490-L490), [507](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L507-L507), [524](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L524-L524), [547](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L547-L547), [578](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L578-L578), [777](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L777-L777), [923](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L923-L923)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

200:     function supportsInterface(bytes4 interfaceId) public pure returns (bool) {

```



*GitHub* : [200](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L200-L200)

```solidity
File: contracts/tokens/ERC20Minimal.sol

49:     function approve(address spender, uint256 amount) public returns (bool) {

61:     function transfer(address to, uint256 amount) public virtual returns (bool) {

81:     function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {

```



*GitHub* : [49](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L49-L49), [61](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L61-L61), [81](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L81-L81)

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol

16:     function balanceOf(address account) external view returns (uint256);

```



*GitHub* : [16](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L16-L16)

```solidity
File: contracts/types/LeftRight.sol

39:     function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {

46:     function rightSlot(LeftRightSigned self) internal pure returns (int128) {

62:     ) internal pure returns (LeftRightUnsigned) {

81:     ) internal pure returns (LeftRightSigned) {

101:     function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {

108:     function leftSlot(LeftRightSigned self) internal pure returns (int128) {

124:     ) internal pure returns (LeftRightUnsigned) {

134:     function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {

284:     ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {

```



*GitHub* : [39](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L39-L39), [46](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L46-L46), [62](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L62-L62), [81](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L81-L81), [101](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L101-L101), [108](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L108-L108), [124](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L124-L124), [134](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L134-L134), [284](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L284-L284)

```solidity
File: contracts/types/LiquidityChunk.sol

74:     ) internal pure returns (LiquidityChunk) {

92:     ) internal pure returns (LiquidityChunk) {

105:     ) internal pure returns (LiquidityChunk) {

121:     ) internal pure returns (LiquidityChunk) {

138:     ) internal pure returns (LiquidityChunk) {

154:     ) internal pure returns (LiquidityChunk) {

171:     function tickLower(LiquidityChunk self) internal pure returns (int24) {

180:     function tickUpper(LiquidityChunk self) internal pure returns (int24) {

189:     function liquidity(LiquidityChunk self) internal pure returns (uint128) {

```



*GitHub* : [74](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L74-L74), [92](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L92-L92), [105](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L105-L105), [121](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L121-L121), [138](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L138-L138), [154](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L154-L154), [171](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L171-L171), [180](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L180-L180), [189](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L189-L189)

```solidity
File: contracts/types/TokenId.sol

87:     function poolId(TokenId self) internal pure returns (uint64) {

96:     function tickSpacing(TokenId self) internal pure returns (int24) {

108:     function asset(TokenId self, uint256 legIndex) internal pure returns (uint256) {

118:     function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {

128:     function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {

138:     function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {

148:     function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {

158:     function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {

169:     function width(TokenId self, uint256 legIndex) internal pure returns (int24) {

183:     function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {

193:     function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {

209:     ) internal pure returns (TokenId) {

225:     ) internal pure returns (TokenId) {

244:     ) internal pure returns (TokenId) {

259:     ) internal pure returns (TokenId) {

277:     ) internal pure returns (TokenId) {

295:     ) internal pure returns (TokenId) {

314:     ) internal pure returns (TokenId) {

366:     function flipToBurnToken(TokenId self) internal pure returns (TokenId) {

404:     function countLongs(TokenId self) internal pure returns (uint256) {

432:     function countLegs(TokenId self) internal pure returns (uint256) {

464:     function clearLeg(TokenId self, uint256 i) internal pure returns (TokenId) {

```


*GitHub* : [87](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L87-L87), [96](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L96-L96), [108](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L108-L108), [118](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L118-L118), [128](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L128-L128), [138](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L138-L138), [148](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L148-L148), [158](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L158-L158), [169](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L169-L169), [183](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L183-L183), [193](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L193-L193), [209](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L209-L209), [225](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L225-L225), [244](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L244-L244), [259](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L259-L259), [277](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L277-L277), [295](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L295-L295), [314](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L314-L314), [366](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L366-L366), [404](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L404-L404), [432](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L432-L432), [464](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L464-L464)

### [N-25]<a name="n-25"></a> Returning a struct instead of returning many variables is better

Returning a struct from a Solidity function instead of multiple variables offers several benefits, enhancing code clarity and efficiency. Structs allow for the grouping of related data into a single entity, making the function's return values more organized and easier to manage. This approach significantly improves readability, as it encapsulates the data logically, helping developers quickly understand the returned information's structure. Additionally, it simplifies function interfaces, reducing the potential for errors when handling multiple return values. By using structs, you can also easily extend or modify the returned data without altering the function signature, facilitating smoother updates and maintenance of your smart contract code.

*There are 32 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

280:         returns (uint256 poolAssets, uint256 insideAMM, int256 currentPoolUtilization)

```



*GitHub* : [280](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L280-L280)

```solidity
File: contracts/PanopticFactory.sol

294:     ) external view returns (bytes32 bestSalt, uint256 highestRarity) {

340:     ) internal returns (uint256, uint256) {

```



*GitHub* : [294](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L294-L294), [340](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L340-L340)

```solidity
File: contracts/PanopticPool.sol

355:     ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {

385:     ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {

414:     ) external view returns (int256 value0, int256 value1) {

435:     ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {

502:     ) internal pure returns (int24, int24) {

800:     ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {

832:     ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {

1343:     ) internal pure returns (uint256 balanceCross, uint256 thresholdCross) {

1839:     ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {

```



*GitHub* : [355](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L355-L355), [385](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L385-L385), [414](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L414-L414), [435](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L435-L435), [502](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L502-L502), [800](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L800-L800), [832](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L832-L832), [1343](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1343-L1343), [1839](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1839-L1839)

```solidity
File: contracts/SemiFungiblePositionManager.sol

479:         returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)

512:         returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)

686:     ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {

1327:         returns (LeftRightUnsigned deltaPremiumOwed, LeftRightUnsigned deltaPremiumGross)

1457:     ) external view returns (uint128, uint128) {

1541:     ) external view returns (int128 feesBase0, int128 feesBase1) {

```



*GitHub* : [479](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L479-L479), [512](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L512-L512), [686](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L686-L686), [1327](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1327-L1327), [1457](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1457-L1457), [1541](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1541-L1541)

```solidity
File: contracts/libraries/FeesCalc.sol

50:     ) external view returns (int256 value0, int256 value1) {

135:     ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {

```



*GitHub* : [50](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L50-L50), [135](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L135-L135)

```solidity
File: contracts/libraries/Math.sol

224:     ) internal pure returns (uint256 amount0, uint256 amount1) {

```



*GitHub* : [224](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L224-L224)

```solidity
File: contracts/libraries/PanopticMath.sol

174:     ) external view returns (int24 medianTick, uint256 updatedMedianData) {

342:     ) internal pure returns (int24 tickLower, int24 tickUpper) {

374:     ) internal pure returns (int24, int24) {

393:     ) internal pure returns (LeftRightSigned longAmounts, LeftRightSigned shortAmounts) {

424:     ) internal pure returns (uint256, uint256) {

450:     ) internal pure returns (uint256, uint256) {

611:     ) internal pure returns (LeftRightSigned longs, LeftRightSigned shorts) {

658:     ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {

777:     ) external returns (int256, int256) {

```



*GitHub* : [174](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L174-L174), [342](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L342-L342), [374](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L374-L374), [393](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L393-L393), [424](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L424-L424), [450](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L450-L450), [611](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L611-L611), [658](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L658-L658), [777](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L777-L777)

```solidity
File: contracts/types/LeftRight.sol

284:     ) internal pure returns (LeftRightUnsigned, LeftRightUnsigned) {

```



*GitHub* : [284](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L284-L284)

```solidity
File: contracts/types/TokenId.sol

419:     ) internal pure returns (int24 legLowerTick, int24 legUpperTick) {

```


*GitHub* : [419](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L419-L419)

### [N-26]<a name="n-26"></a> Use scratch space when building emitted events with two data arguments

Using the [scratch space](https://gist.github.com/IllIllI000/87c4f03139fa03780fa548b8e4b02b5b) for more than one, but at most two words worth of data (non-indexed arguments) will save gas over needing Solidity's abi memory expansion used for emitting normally.

*There are 4 instance(s) of this issue:*

```solidity
File: contracts/PanopticFactory.sol

154:         emit OwnershipTransferred(currentOwner, newOwner);

```



*GitHub* : [154](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L154-L154)

```solidity
File: contracts/SemiFungiblePositionManager.sol

390:         emit PoolInitialized(univ3pool, poolId);

```



*GitHub* : [390](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L390-L390)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

220:         emit TransferSingle(msg.sender, address(0), to, id, amount);

```



*GitHub* : [220](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L220-L220)

```solidity
File: contracts/tokens/ERC20Minimal.sol

145:         emit Transfer(from, address(0), amount);

```


*GitHub* : [145](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L145-L145)

### [N-27]<a name="n-27"></a> Use `do`-`while` loop

`do`-`while` is cheaper than `for`-loops when the initial check can be skipped. 

`for (uint256 i; i < len; ++i){ ... }` -> `do { ...; ++i } while (i < len);`

*There are 16 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

662:             for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {

1255:             for (uint256 index = 0; index < numLegs; ++index) {

```



*GitHub* : [662](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L662-L662), [1255](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1255-L1255)

```solidity
File: contracts/PanopticPool.sol

1672:         for (uint256 leg = 0; leg < numLegs; ++leg) {

```



*GitHub* : [1672](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1672-L1672)

```solidity
File: contracts/libraries/PanopticMath.sol

137:             for (uint256 i = 0; i < cardinality + 1; ++i) {

148:             for (uint256 i = 0; i < cardinality; ++i) {

207:                 for (uint8 i; i < 8; ++i) {

248:             for (uint256 i = 0; i < 20; ++i) {

256:             for (uint256 i = 0; i < 19; ++i) {

781:             for (uint256 i = 0; i < positionIdList.length; ++i) {

784:                 for (uint256 leg = 0; leg < numLegs; ++leg) {

860:             for (uint256 i = 0; i < positionIdList.length; i++) {

863:                 for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {

```



*GitHub* : [137](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L137-L137), [148](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L148-L148), [207](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L207-L207), [248](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L248-L248), [256](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L256-L256), [781](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L781-L781), [784](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L784-L784), [860](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L860-L860), [863](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L863-L863)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

187:             for (uint256 i = 0; i < owners.length; ++i) {

```



*GitHub* : [187](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L187-L187)

```solidity
File: contracts/types/TokenId.sol

507:             for (uint256 i = 0; i < 4; ++i) {

520:                 for (uint256 j = i + 1; j < numLegs; ++j) {

581:             for (uint256 i = 0; i < numLegs; ++i) {

```


*GitHub* : [507](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L507-L507), [520](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L520-L520), [581](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L581-L581)

### [N-28]<a name="n-28"></a> Accessing Multi-Dimensional Array

Consider caching some one-to-two top dimensions of a multi-dimensional array to avoid recalculating the array offsets for saving gas.

*There are 52 instance(s) of this issue:*

```solidity
File: contracts/CollateralTracker.sol

542:             uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.

544:             if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

600:             uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.

602:             if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;

1210:             TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);

1213:             uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();

1216:             uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();

```



*GitHub* : [542](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L542-L542), [544](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L544-L544), [600](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L600-L600), [602](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L602-L602), [1210](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1210-L1210), [1213](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1213-L1213), [1216](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1216-L1216)

```solidity
File: contracts/PanopticPool.sol

357:         LeftRightUnsigned balanceData = s_positionBalance[user][tokenId];

444:             balances[k][0] = TokenId.unwrap(tokenId);

445:             balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);

449:                 uint256[2][4] memory premiumAccumulatorsByLeg

452:                     LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),

638:         if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)

654:         s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned

762:                 s_options[msg.sender][tokenId][leg] = LeftRightUnsigned

836:         uint128 positionSize = s_positionBalance[owner][tokenId].rightSlot();

861:         s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);

870:             s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);

1193:         uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();

1514:             uint256[2][4] memory premiumAccumulatorsByLeg

1528:                 (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM

1540:                     LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];

1550:                                     ((premiumAccumulatorsByLeg[leg][0] -

1559:                                     ((premiumAccumulatorsByLeg[leg][1] -

1621:             LeftRightUnsigned premiumAccumulatorsLast = s_options[owner][tokenId][legIndex];

1622:             s_options[owner][tokenId][legIndex] = accumulatedPremium;

1628:             .getLiquidityChunk(tokenId, legIndex, s_positionBalance[owner][tokenId].rightSlot())

1841:         uint256[2][4] memory premiumAccumulatorsByLeg;

1923:                         uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;

1940:                                                         _premiumAccumulatorsByLeg[_leg][0] *

1957:                                                         _premiumAccumulatorsByLeg[_leg][1] *

1967:                                 .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))

1968:                                 .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));

```



*GitHub* : [357](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L357-L357), [444](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L444-L444), [445](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L445-L445), [449](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L449-L449), [452](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L452-L452), [638](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L638-L638), [654](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L654-L654), [762](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L762-L762), [836](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L836-L836), [861](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L861-L861), [870](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L870-L870), [1193](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1193-L1193), [1514](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1514-L1514), [1528](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1528-L1528), [1540](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1540-L1540), [1550](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1550-L1550), [1559](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1559-L1559), [1621](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1621-L1621), [1622](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1622-L1622), [1628](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1628-L1628), [1841](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1841-L1841), [1923](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1923-L1923), [1940](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1940-L1940), [1957](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1957-L1957), [1967](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1967-L1967), [1968](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1968-L1968)

```solidity
File: contracts/SemiFungiblePositionManager.sol

576:             if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();

```



*GitHub* : [576](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L576-L576)

```solidity
File: contracts/libraries/PanopticMath.sol

786:                         longPremium = longPremium.sub(premiasByLeg[i][leg]);

870:                             uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),

874:                             uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),

890:                             uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0

894:                             uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1

```



*GitHub* : [786](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L786-L786), [870](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L870-L870), [874](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L874-L874), [890](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L890-L890), [894](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L894-L894)

```solidity
File: contracts/tokens/ERC1155Minimal.sol

82:         isApprovedForAll[msg.sender][operator] = approved;

101:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

103:         balanceOf[from][id] -= amount;

107:             balanceOf[to][id] += amount;

137:         if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

147:             balanceOf[from][id] -= amount;

151:                 balanceOf[to][id] += amount;

188:                 balances[i] = balanceOf[owners[i]][ids[i]];

217:             balanceOf[to][id] += amount;

237:         balanceOf[from][id] -= amount;

```



*GitHub* : [82](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L82-L82), [101](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L101-L101), [103](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L103-L103), [107](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L107-L107), [137](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L137-L137), [147](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L147-L147), [151](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L151-L151), [188](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L188-L188), [217](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L217-L217), [237](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L237-L237)

```solidity
File: contracts/tokens/ERC20Minimal.sol

50:         allowance[msg.sender][spender] = amount;

82:         uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.

84:         if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;

```


*GitHub* : [50](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L50-L50), [82](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L82-L82), [84](https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L84-L84)
