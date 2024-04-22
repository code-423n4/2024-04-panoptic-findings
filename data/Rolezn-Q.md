## QA Summary<a name="QA Summary">

### Low Risk Issues
| |Issue|Contexts|
|-|:-|:-:|
| [LOW&#x2011;1](#LOW&#x2011;1) | Actual collected amounts and the requested amounts should be checked | 1 |
| [LOW&#x2011;2](#LOW&#x2011;2) | `forceApprove` should be used instead of `approve` | 4 |
| [LOW&#x2011;3](#LOW&#x2011;3) | Init functions are susceptible to front-running | 2 |
| [LOW&#x2011;4](#LOW&#x2011;4) | Minting tokens to the zero address should be avoided | 1 |
| [LOW&#x2011;5](#LOW&#x2011;5) | The Contract Should `approve(0)` First | 4 |
| [LOW&#x2011;6](#LOW&#x2011;6) | Constructor is missing zero address check | 2 |
| [LOW&#x2011;7](#LOW&#x2011;7) | Max withdraw check is missing in `withdraw` function of ERC-4626 | 1 |
| [LOW&#x2011;8](#LOW&#x2011;8) | `mulDiv` may result in the result being zero when called by large numbers | 3 |
| [LOW&#x2011;9](#LOW&#x2011;9) | Non-compliance of `ERC1155` standard due to not reverting on transfer to zero address | 1 |
| [LOW&#x2011;10](#LOW&#x2011;10) | Some tokens do not consider `type(uint256).max` as an infinite approval | 4 |
| [LOW&#x2011;11](#LOW&#x2011;11) | Users should be able to choose the recipient for long positions | 1 |

Total: 24 contexts over 11 issues

### Non-critical Issues
| |Issue|Contexts|
|-|:-|:-:|
| [NC&#x2011;1](#NC&#x2011;1) | Add inline comments for unnamed variables in function declarations | 2 |
| [NC&#x2011;2](#NC&#x2011;2) | Array lengths not checked | 2 |
| [NC&#x2011;3](#NC&#x2011;3) | Avoid mutating function parameters | 2 |
| [NC&#x2011;4](#NC&#x2011;4) | Bug in legacy code generation when accessing the `.selector` member on expressions with side effects | 20 |
| [NC&#x2011;5](#NC&#x2011;5) | Consider adding a deny-list | 1 |
| [NC&#x2011;6](#NC&#x2011;6) | Consider adding formal verification proofs | 6 |
| [NC&#x2011;7](#NC&#x2011;7) | Consider emitting an event at the end of the constructor | 2 |
| [NC&#x2011;8](#NC&#x2011;8) | Constants in comparisons should appear on the left side | 41 |
| [NC&#x2011;9](#NC&#x2011;9) | Contract declarations should have NatSpec `@author` annotations | 1 |
| [NC&#x2011;10](#NC&#x2011;10) | Contracts should have NatSpec `@dev` tags | 2 |
| [NC&#x2011;11](#NC&#x2011;11) | Contract declarations should have NatSpec `@title` annotations | 2 |
| [NC&#x2011;12](#NC&#x2011;12) | Cyclomatic complexity in functions  | 1 |
| [NC&#x2011;13](#NC&#x2011;13) | Defined named returns not used within function | 21 |
| [NC&#x2011;14](#NC&#x2011;14) | Dependence on external protocols | 8 |
| [NC&#x2011;15](#NC&#x2011;15) | Duplicated `require()`/`revert()` Checks Should Be Refactored To A Modifier Or Function | 3 |
| [NC&#x2011;16](#NC&#x2011;16) | Duplicated `revert()` checks should be refactored to a `modifier` or `function` | 2 |
| [NC&#x2011;17](#NC&#x2011;17) | `else`-block not required | 6 |
| [NC&#x2011;18](#NC&#x2011;18) | Employ Explicit Casting to Bytes or Bytes32 for Enhanced Code Clarity and Meaning  | 3 |
| [NC&#x2011;19](#NC&#x2011;19) | Enable IR-based code generation | 1 |
| [NC&#x2011;20](#NC&#x2011;20) | Events are missing sender information | 1 |
| [NC&#x2011;21](#NC&#x2011;21) | For extended 'using-for' usage, use the latest pragma version  | 10 |
| [NC&#x2011;22](#NC&#x2011;22) | Functions calling contracts/addresses with transfer hooks are missing reentrancy guards | 1 |
| [NC&#x2011;23](#NC&#x2011;23) | Hardcoded String that is repeatedly used can be replaced with a constant | 3 |
| [NC&#x2011;24](#NC&#x2011;24) | `if`-statement can be converted to a ternary | 9 |
| [NC&#x2011;25](#NC&#x2011;25) | `if` statement control structures do not comply with best practices | 5 |
| [NC&#x2011;26](#NC&#x2011;26) | Inconsistent Spacing In Comments | 3 |
| [NC&#x2011;27](#NC&#x2011;27) | Incorrect withdraw declaration | 1 |
| [NC&#x2011;28](#NC&#x2011;28) | Interface imports should be declared first | 9 |
| [NC&#x2011;29](#NC&#x2011;29) | Make use of Solidity's `using` keyword | 2 |
| [NC&#x2011;30](#NC&#x2011;30) | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability | 7 |
| [NC&#x2011;31](#NC&#x2011;31) | No equate comparison checks between `to` and `from` address parameters | 3 |
| [NC&#x2011;32](#NC&#x2011;32) | Non-assembly method available | 13 |
| [NC&#x2011;33](#NC&#x2011;33) | Off-by-one timestamp error | 1 |
| [NC&#x2011;34](#NC&#x2011;34) | Operations such as the changing of the owner should be behind a timelock | 1 |
| [NC&#x2011;35](#NC&#x2011;35) | Order of argument evaluation disrupted in non-expression-split code by optimizer sequences with FullInliner | 20 |
| [NC&#x2011;36](#NC&#x2011;36) | Overly complicated arithmetic | 6 |
| [NC&#x2011;37](#NC&#x2011;37) | Private variables dont respect naming convention | 1 |
| [NC&#x2011;38](#NC&#x2011;38) | Redundant Cast | 2 |
| [NC&#x2011;39](#NC&#x2011;39) | Redundant code `length` check | 3 |
| [NC&#x2011;40](#NC&#x2011;40) | Remove unused `error` definition | 1 |
| [NC&#x2011;41](#NC&#x2011;41) | Returning a struct instead of a bunch of variables is better | 7 |
| [NC&#x2011;42](#NC&#x2011;42) | Uncommented fields in a struct | 2 |
| [NC&#x2011;43](#NC&#x2011;43) | Use a struct to encapsulate multiple function parameters | 3 |
| [NC&#x2011;44](#NC&#x2011;44) | Use `@inheritdoc` for overridden functions | 4 |
| [NC&#x2011;45](#NC&#x2011;45) | Use of `override` is unnecessary | 2 |
| [NC&#x2011;46](#NC&#x2011;46) | Use a single file for system wide constants | 38 |
| [NC&#x2011;47](#NC&#x2011;47) | Use SMTChecker | 1 |
| [NC&#x2011;48](#NC&#x2011;48) | Utilizing `delegatecall` within a loop | 1 |
| [NC&#x2011;49](#NC&#x2011;49) | Visibility should be set explicitly rather than defaulting to `internal` | 16 |
| [NC&#x2011;50](#NC&#x2011;50) | Zero as a function argument should have a descriptive meaning | 7 |

Total: 309 contexts over 50 issues

## Low Risk Issues

### <a href="#qa-summary">[LOW&#x2011;1]</a><a name="LOW&#x2011;1"> Actual collected amounts and the requested amounts should be checked [SAFE]

The earned fees and the burnt liquidities are collected by calling the [`UniswapV3Pool.collect()`](https://github.com/Uniswap/v3-core/blob/d8b1c635c275d2a9450bd6a78f3fa2484fef73eb/contracts/UniswapV3Pool.sol#L490C5-L513C6) function.

The UniswapV3Pool [checks the requested amounts compared to the owed amounts](https://github.com/Uniswap/v3-core/blob/d8b1c635c275d2a9450bd6a78f3fa2484fef73eb/contracts/UniswapV3Pool.sol#L498C1-L501C101) to the position and transfers tokens.

```solidity
// UniswapV3Pool.sol

->      Position.Info storage position = positions.get(msg.sender, tickLower, tickUpper); 

        amount0 = amount0Requested > position.tokensOwed0 ? position.tokensOwed0 : amount0Requested;
        amount1 = amount1Requested > position.tokensOwed1 ? position.tokensOwed1 : amount1Requeste
```

It is best to check if the actual transferred amounts are equal to the requested amounts as an invariant check. It might be an extremely rare case but there is no way to collect the remaining owed tokens in that case since the contract doesn't have a specific function to call the UniswapV3 `collect` function.


#### <ins>Proof Of Concept</ins>


```solidity
File: SemiFungiblePositionManager.sol

1284: (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(
                msg.sender,
                liquidityChunk.tickLower(),
                liquidityChunk.tickUpper(),
                uint128(amountToCollect.rightSlot()),
                uint128(amountToCollect.leftSlot())
            );


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1284



### <a href="#qa-summary">[LOW&#x2011;2]</a><a name="LOW&#x2011;2"> `forceApprove` should be used instead of `approve` [SAFE]

In order to prevent front running, `forceApprove`  should be used in place of `approve` where possible 

#### <ins>Proof Of Concept</ins>


```solidity
File: InteractionHelper.sol

32: IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L32

```solidity
File: InteractionHelper.sol

33: IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L33

```solidity
File: InteractionHelper.sol

36: IERC20Partial(token0).approve(address(ct0), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L36

```solidity
File: InteractionHelper.sol

37: IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L37



### <a href="#qa-summary">[LOW&#x2011;3]</a><a name="LOW&#x2011;3"> Init functions are susceptible to front-running [NOT_SAFE]

The `initialize()` functions below are not called by another contract atomically after the contract is deployed, so it's possible for a malicious user to call `initialize()` which, if it's noticed in time, would require the project to re-deploy the contract in order to properly initialize. Consider creating a factory contract, which will `new` and `initialize()` each contract atomically.

#### <ins>Proof Of Concept</ins>

```solidity
File: PanopticFactory.sol

function initialize(address _owner) public {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L134

```solidity
File: SemiFungiblePositionManager.sol

function initializeAMMPool(address token0, address token1, uint24 fee) external {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L350



### <a href="#qa-summary">[LOW&#x2011;4]</a><a name="LOW&#x2011;4"> Minting tokens to the zero address should be avoided [SAFE]

The core function `mint` is used by users to mint an option position by providing token1 as collateral and borrowing the max amount of liquidity. `Address(0)` check is missing in both this function and the internal function `_mint`, which is triggered to mint the tokens to the to address. Consider applying a check in the function to ensure tokens aren't minted to the zero address.

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol


function mint(uint256 shares, address receiver) external returns (uint256 assets) {
        assets = previewMint(shares);

        if (assets > type(uint104).max) revert Errors.DepositTooLarge();

        
        
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            msg.sender,
            address(s_panopticPool),
            assets
        );

        
        _mint(receiver, shares);

        
        unchecked {
            s_poolAssets += uint128(assets);
        }

        emit Deposit(msg.sender, receiver, assets, shares);
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L477



### <a href="#qa-summary">[LOW&#x2011;5]</a><a name="LOW&#x2011;5"> The Contract Should `approve(0)` First [SAFE]

Some tokens (like USDT L199) do not work when changing the allowance from an existing non-zero allowance value. They must first be approved by zero and then the actual allowance must be approved.

#### <ins>Proof Of Concept</ins>


```solidity
File: InteractionHelper.sol

32: IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L32

```solidity
File: InteractionHelper.sol

33: IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L33

```solidity
File: InteractionHelper.sol

36: IERC20Partial(token0).approve(address(ct0), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L36

```solidity
File: InteractionHelper.sol

37: IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L37



#### <ins>Recommended Mitigation Steps</ins>

Approve with a zero amount first before setting the actual amount.



### <a href="#qa-summary">[LOW&#x2011;6]</a><a name="LOW&#x2011;6"> Constructor is missing zero address check [SAFE]

In Solidity, constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a check, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could occur due to a mistake or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it are irretrievable. Therefore, it's crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.

#### <ins>Proof Of Concept</ins>

```solidity
File: PanopticPool.sol

280: constructor: SemiFungiblePositionManager _sfpm
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L280

```solidity
File: SemiFungiblePositionManager.sol

341: constructor: IUniswapV3Factory _factory
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L341






### <a href="#qa-summary">[LOW&#x2011;7]</a><a name="LOW&#x2011;7"> Max withdraw check is missing in `withdraw` function of ERC-4626 [NOT_SAFE]

In the [EIP-4626](https://eips.ethereum.org/EIPS/eip-4626#maxwithdraw) specification it reads:

However withdraw functions misses this check:
```
Maximum amount of the underlying asset that can be withdrawn from the owner balance in the Vault, through a withdraw call.

```

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol

531: function withdraw(
        uint256 assets,
        address receiver,
        address owner
    ) external returns (uint256 shares) {
        if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

        shares = previewWithdraw(assets);

        
        if (msg.sender != owner) {
            uint256 allowed = allowance[owner][msg.sender]; 

            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
        }

        
        _burn(owner, shares);

        
        unchecked {
            s_poolAssets -= uint128(assets);
        }

        
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        );

        emit Withdraw(msg.sender, receiver, owner, assets, shares);

        return shares;
    }



### <a href="#qa-summary">[LOW&#x2011;8]</a><a name="LOW&#x2011;8"> `mulDiv` may result in the result being zero when called by large numbers [SAFE]

Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator.

#### <ins>Proof Of Concept</ins>



```solidity
File: CollateralTracker.sol

956: Math.mulDiv(
                    assets,
                    totalSupply - delegateeBalance,
                    uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
                ) - delegateeBalance
            );


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L956


```solidity
File: SemiFungiblePositionManager.sol

1350: premium0X64_base = Math.mulDiv(
                    collected0,
                    totalLiquidity * 2 ** 64,
                    netLiquidity ** 2
                );

1355: premium1X64_base = Math.mulDiv(
                    collected1,
                    totalLiquidity * 2 ** 64,
                    netLiquidity ** 2
                );


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1350

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1355





### <a href="#qa-summary">[LOW&#x2011;9]</a><a name="LOW&#x2011;9"> Non-compliance of `ERC1155` standard due to not reverting on transfer to zero address [NOT_SAFE]

EIP-1155 and all the rules for this token standard can be found here: https://eips.ethereum.org/EIPS/eip-1155

According to EIP-115, `MUST revert if _to is the zero address`
However, the following contracts do not revert when to is zero address.

#### <ins>Proof Of Concept</ins>


```solidity
File: SemiFungiblePositionManager.sol

540: function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public override {
        
        
        if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

        
        registerTokenTransfer(from, to, TokenId.wrap(id), amount);

        
        super.safeTransferFrom(from, to, id, amount, data);
    }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L541


### <a href="#qa-summary">[LOW&#x2011;10]</a><a name="LOW&#x2011;10"> Some tokens do not consider `type(uint256).max` as an infinite approval [NOT_SAFE]

Some tokens such as [COMP](https://github.com/compound-finance/compound-protocol/blob/a3214f67b73310d547e00fc578e8355911c9d376/contracts/Governance/Comp.sol#L89-L91) downcast such approvals to uint96 and use that as a raw value rather than interpreting it as an infinite approval. Eventually these approvals will reach zero, at which point the calling contract will no longer function properly.

#### <ins>Proof Of Concept</ins>

```solidity
File: InteractionHelper.sol

32: IERC20Partial(token0).approve(address(sfpm), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L32

```solidity
File: InteractionHelper.sol

33: IERC20Partial(token1).approve(address(sfpm), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L33

```solidity
File: InteractionHelper.sol

36: IERC20Partial(token0).approve(address(ct0), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L36

```solidity
File: InteractionHelper.sol

37: IERC20Partial(token1).approve(address(ct1), type(uint256).max);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L37



### <a href="#qa-summary">[LOW&#x2011;11]</a><a name="LOW&#x2011;11"> Users should be able to choose the recipient for long positions [NOT_SAFE]

Users deposit tokens by opening short positions and withdraw tokens by opening long positions or closing short positions.
In the current implementation, the collected tokens are only transferred to the `msg.sender` and the user has no way to provide a different recipient.  

Users should be able to provide recipients in case of being blocked by some token contracts (e.g. USDC or USDT).

* Alice opens a short position and deposits USDC to Uniswap
  
* Alice's account is blocked by the USDC contract.
    
* Alice tries to close her position.
    
* function reverts while transferring USDC back to Alice due to Alice being blocked.
    
* She can not close her position.
    
If Alice minted a position directly in Uniswap, she could've provided a different address, closed the position and gotten her tokens back.


#### <ins>Proof Of Concept</ins>


```solidity
File: SemiFungiblePositionManager.sol

1284: (uint128 receivedAmount0, uint128 receivedAmount1) = univ3pool.collect(
                msg.sender,
                liquidityChunk.tickLower(),
                liquidityChunk.tickUpper(),
                uint128(amountToCollect.rightSlot()),
                uint128(amountToCollect.leftSlot())
            );


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1284




#### <ins>Recommended Mitigation Steps</ins>

Allow users to provide recipient addresses to collect fees and burnt liquidity instead of transferring only to the `msg.sender`



## Non Critical Issues

### <a href="#qa-summary">[NC&#x2011;1]</a><a name="NC&#x2011;1"> Add inline comments for unnamed variables in function declarations [SAFE]

Unnamed variables in function declarations can confuse developers. To enhance clarity, add inline comments next to each unnamed variable. E.g address, -> address /* to */,

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol

392: function maxDeposit(address) external pure returns (uint256 maxAssets) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L392

```solidity
File: CollateralTracker.sol

444: function maxMint(address) external view returns (uint256 maxShares) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L444






### <a href="#qa-summary">[NC&#x2011;2]</a><a name="NC&#x2011;2"> Array lengths not checked [SAFE]

If the length of the arrays are not required to be of the same length, user operations may not be fully executed

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: PanopticPool.sol


function burnOptions(
        TokenId[] calldata positionIdList,
        TokenId[] calldata newPositionIdList,
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) external {

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L586-L591

```solidity
File: PanopticPool.sol


function liquidate(
        TokenId[] calldata positionIdListLiquidator,
        address liquidatee,
        LeftRightUnsigned delegations,
        TokenId[] calldata positionIdList
    ) external {

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1017-L1022


</details>




### <a href="#qa-summary">[NC&#x2011;3]</a><a name="NC&#x2011;3"> Avoid mutating function parameters [NOT_SAFE]

Function parameters in Solidity are passed by value, meaning they are essentially local copies. Mutating them can lead to confusion and errors because the changes don't persist outside the function. By keeping function parameters immutable, you ensure clarity in code behavior, preventing unintended side-effects. If you need to modify a value based on a parameter, use a local variable inside the function, leaving the original parameter unaltered. By adhering to this practice, you maintain a clear distinction between input data and the internal processing logic, improving code readability and reducing the potential for bugs.

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol

751: function _sellCollateralRatio(
        int256 utilization // @audit <---
    ) internal view returns (uint256 sellCollateralRatio) {
        
        
        
        
        

        uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;
        
        
        if (utilization < 0) {
            unchecked {
                min_sell_ratio /= 2;
                utilization = -utilization; // @audit <---
            }
        }

        
        if (uint256(utilization) < TARGET_POOL_UTIL) {
            return min_sell_ratio;
        }

        
        
        if (uint256(utilization) > SATURATED_POOL_UTIL) {
            return DECIMALS;
        }

        unchecked {
            return
                min_sell_ratio +
                ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
                (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);
        }
    }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L752



```solidity
File: SemiFungiblePositionManager.sol

680: function _validateAndForwardToAMM(
        TokenId tokenId, // @audit <--- 
        uint128 positionSize,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        bool isBurn
    ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {
        
        if (positionSize == 0) revert Errors.OptionsBalanceZero();

        
        if (isBurn) {
            tokenId = tokenId.flipToBurnToken(); // @audit <---
        }

        
        tokenId.validate();

        
        IUniswapV3Pool univ3pool = s_poolContext[tokenId.poolId()].pool;

        
        if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();

        
        LeftRightSigned itmAmounts;

        
        (totalMoved, collectedByLeg, itmAmounts) = _createPositionInAMM(
            univ3pool,
            tokenId,
            positionSize,
            isBurn
        );

        if (tickLimitLow > tickLimitHigh) {
            
            if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {
                totalMoved = swapInAMM(univ3pool, itmAmounts).add(totalMoved);
            }

            (tickLimitLow, tickLimitHigh) = (tickLimitHigh, tickLimitLow);
        }

        
        (, int24 currentTick, , , , , ) = univ3pool.slot0();

        if ((currentTick >= tickLimitHigh) || (currentTick <= tickLimitLow))
            revert Errors.PriceBoundFail();
    }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L681






### <a href="#qa-summary">[NC&#x2011;4]</a><a name="NC&#x2011;4"> Bug in legacy code generation when accessing the `.selector` member on expressions with side effects [SAFE]

This version of solidity is vulnerable to a bug in the legacy code generation pipeline of the Solidity compiler that was found during investigation of a security report On June 26, 2023. For more details check the following [link](https://soliditylang.org/blog/2023/07/19/missing-side-effects-on-selector-access-bug/)

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: CollateralTracker.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L2

```solidity
File: PanopticFactory.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L2

```solidity
File: PanopticPool.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L2

```solidity
File: SemiFungiblePositionManager.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L2

```solidity
File: CallbackLib.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L2

```solidity
File: Constants.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L2

```solidity
File: Errors.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol#L2

```solidity
File: FeesCalc.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L2

```solidity
File: InteractionHelper.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L2

```solidity
File: Math.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L2

```solidity
File: PanopticMath.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L2

```solidity
File: SafeTransferLib.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L2

```solidity
File: Multicall.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L2

```solidity
File: ERC1155Minimal.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L2

```solidity
File: ERC20Minimal.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L2

```solidity
File: IDonorNFT.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L2

```solidity
File: IERC20Partial.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L2

```solidity
File: LeftRight.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L2

```solidity
File: LiquidityChunk.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L2

```solidity
File: TokenId.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L2



</details>




### <a href="#qa-summary">[NC&#x2011;5]</a><a name="NC&#x2011;5"> Consider adding a deny-list [NOT_SAFE]

Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L36




### <a href="#qa-summary">[NC&#x2011;6]</a><a name="NC&#x2011;6"> Consider adding formal verification proofs [SAFE]

Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).

There are 6 instances:

- [*DestinationBridge.sol*](https://github.com/code-423n4/2023-09-ondo/tree/623dd3c0ff3c4d8ce4ed563b96da50d08cd803c5/contracts/bridge/DestinationBridge.sol)

- [*SourceBridge.sol*](https://github.com/code-423n4/2023-09-ondo/tree/623dd3c0ff3c4d8ce4ed563b96da50d08cd803c5/contracts/bridge/SourceBridge.sol)

- [*IRWADynamicOracle.sol*](https://github.com/code-423n4/2023-09-ondo/tree/623dd3c0ff3c4d8ce4ed563b96da50d08cd803c5/contracts/rwaOracles/IRWADynamicOracle.sol)

- [*RWADynamicOracle.sol*](https://github.com/code-423n4/2023-09-ondo/tree/623dd3c0ff3c4d8ce4ed563b96da50d08cd803c5/contracts/rwaOracles/RWADynamicOracle.sol)

- [*rUSDY.sol*](https://github.com/code-423n4/2023-09-ondo/tree/623dd3c0ff3c4d8ce4ed563b96da50d08cd803c5/contracts/usdy/rUSDY.sol)

- [*rUSDYFactory.sol*](https://github.com/code-423n4/2023-09-ondo/tree/623dd3c0ff3c4d8ce4ed563b96da50d08cd803c5/contracts/usdy/rUSDYFactory.sol)



### <a href="#qa-summary">[NC&#x2011;7]</a><a name="NC&#x2011;7"> Consider emitting an event at the end of the constructor [NOT_SAFE]

This will allow users to easily exactly pinpoint when and by whom a contract was constructed

#### <ins>Proof Of Concept</ins>


```solidity
File: PanopticPool.sol

280: constructor(SemiFungiblePositionManager _sfpm) {
        SFPM = _sfpm;
    }
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L280

```solidity
File: SemiFungiblePositionManager.sol

341: constructor(IUniswapV3Factory _factory) {
        FACTORY = _factory;
    }
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L341



### <a href="#qa-summary">[NC&#x2011;8]</a><a name="NC&#x2011;8"> Constants in comparisons should appear on the left side [SAFE]

Putting constants on the left side of a comparison operator like `==` or `<` is a best practice known as "Yoda conditions", which can help prevent accidental assignment instead of comparison. In some programming languages, if a variable is mistakenly put on the left with a single `=` instead of `==`, it assigns the constant's value to the variable without any compiler error. However, doing this with the constant on the left would generate an error, as constants cannot be assigned values. Although Solidity's static typing system prevents accidental assignments within conditionals, adopting this practice enhances code readability and consistency, especially when developers are working across multiple languages that support this convention.

#### <ins>Proof Of Concept</ins>

<details>

```solidity
File: CollateralTracker.sol

708: (tokenType == 0 && currentValue1 < oracleValue1) ||
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L708

```solidity
File: CollateralTracker.sol

709: (tokenType == 1 && currentValue0 < oracleValue0)
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L709

```solidity
File: CollateralTracker.sol

1325: uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1325

```solidity
File: CollateralTracker.sol

1328: int64 utilization = tokenType == 0
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1328

```solidity
File: CollateralTracker.sol

1339: if (isLong == 0) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1339

```solidity
File: CollateralTracker.sol

1346: ((atTick >= tickUpper) && (tokenType == 1)) ||
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1346

```solidity
File: CollateralTracker.sol

1347: ((atTick < tickLower) && (tokenType == 0))
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1347

```solidity
File: CollateralTracker.sol

1362: uint160 ratio = tokenType == 1
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1362

```solidity
File: CollateralTracker.sol

1374: ((atTick < tickLower) && (tokenType == 1)) ||
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1374

```solidity
File: CollateralTracker.sol

1375: ((atTick >= tickUpper) && (tokenType == 0))
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1375

```solidity
File: CollateralTracker.sol

1451: if (isLong == 1) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1451

```solidity
File: CollateralTracker.sol

1479: if (isLong == 0) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1479

```solidity
File: CollateralTracker.sol

1488: } else if (isLong == 1) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1488

```solidity
File: CollateralTracker.sol

1544: if (tokenType == 0) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1544

```solidity
File: CollateralTracker.sol

1559: if (tokenType == 1) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1559

```solidity
File: CollateralTracker.sol

1582: tokenType == 0 ? movedRight : movedLeft,
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1582

```solidity
File: CollateralTracker.sol

1544: tokenType == 0
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1544

```solidity
File: PanopticPool.sol

768: if (isLong == 1) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L768

```solidity
File: PanopticPool.sol

1483: if (netLiquidity == 0) return;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1483

```solidity
File: PanopticPool.sol

1520: if ((isLong == 1) || computeAllPremia) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1520

```solidity
File: PanopticPool.sol

1566: if (isLong == 1) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1566

```solidity
File: SemiFungiblePositionManager.sol

688: if (positionSize == 0) revert Errors.OptionsBalanceZero();
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L688

```solidity
File: SemiFungiblePositionManager.sol

833: if (swapAmount == 0) return LeftRightSigned.wrap(0);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L833

```solidity
File: SemiFungiblePositionManager.sol

999: if (isLong == 0) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L999

```solidity
File: SemiFungiblePositionManager.sol

1066: moved = isLong == 0
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1066

```solidity
File: SemiFungiblePositionManager.sol

1073: if (tokenType == 1) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1073

```solidity
File: SemiFungiblePositionManager.sol

1078: if (tokenType == 0) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1078

```solidity
File: SemiFungiblePositionManager.sol

1275: if (isLong == 1) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1275

```solidity
File: SemiFungiblePositionManager.sol

1514: acctPremia = isLong == 1 ? premiumOwed : premiumGross;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1514

```solidity
File: SemiFungiblePositionManager.sol

1514: acctPremia = isLong == 1
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1514

```solidity
File: PanopticMath.sol

211: if (rank == 7) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L211

```solidity
File: PanopticMath.sol

425: if (tokenType == 0) {
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L425

```solidity
File: PanopticMath.sol

475: uint256 notional = asset == 0
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L475

```solidity
File: PanopticMath.sol

479: if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L479

```solidity
File: ERC1155Minimal.sol

202: interfaceId == 0x01ffc9a7 ||
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L202

```solidity
File: ERC1155Minimal.sol

203: interfaceId == 0xd9b67a26;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L203

```solidity
File: TokenId.sol

465: if (i == 0)
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L465

```solidity
File: TokenId.sol

471: if (i == 1)
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L471

```solidity
File: TokenId.sol

477: if (i == 2)
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L477

```solidity
File: TokenId.sol

483: if (i == 3)
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L483

```solidity
File: TokenId.sol

566: if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L566



</details>




### <a href="#qa-summary">[NC&#x2011;9]</a><a name="NC&#x2011;9"> Contract declarations should have NatSpec `@author` annotations [SAFE]

#### <ins>Proof Of Concept</ins>

```solidity
File: 

IDonorNFT.sol

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol
```







### <a href="#qa-summary">[NC&#x2011;10]</a><a name="NC&#x2011;10"> Contracts should have NatSpec `@dev` tags [SAFE]

#### <ins>Proof Of Concept</ins>

```solidity
File: CollateralTracker.sol

36: contract CollateralTracker is ERC20Minimal, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L36

```solidity
File: PanopticFactory.sol

26: contract PanopticFactory is Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L26



### <a href="#qa-summary">[NC&#x2011;11]</a><a name="NC&#x2011;11"> Contract declarations should have NatSpec `@title` annotations [SAFE]

#### <ins>Proof Of Concept</ins>

```solidity
File: 

SafeTransferLib.sol

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol
```



```solidity
File: 

IDonorNFT.sol

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol
```


### <a href="#qa-summary">[NC&#x2011;12]</a><a name="NC&#x2011;12"> Cyclomatic complexity in functions  [SAFE]

Cyclomatic complexity is a software metric used to measure the complexity of a program. It quantifies the number of linearly independent paths through a program's source code, giving an idea of how complex the control flow is. High cyclomatic complexity may indicate a higher risk of defects and can make the code harder to understand, test, and maintain. It often suggests that a function or method is trying to do too much, and a refactor might be needed. By breaking down complex functions into smaller, more focused pieces, you can improve readability, ease of testing, and overall maintainability.

#### <ins>Proof Of Concept</ins>


```solidity
File: TokenId.sol

392:
    return
        TokenId.wrap(
            TokenId.unwrap(self) ^
                ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)
        );


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L392-L396



### <a href="#qa-summary">[NC&#x2011;13]</a><a name="NC&#x2011;13"> Defined named returns not used within function [SAFE]

Such instances can be replaced with unnamed returns

#### <ins>Proof Of Concept</ins>

<details>


```solidity
File: CollateralTracker.sol

362: return s_underlyingToken;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L362

```solidity
File: CollateralTracker.sol

372: return s_poolAssets + s_inAMM;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L372

```solidity
File: CollateralTracker.sol

380: return Math.mulDiv(assets, totalSupply, totalAssets());


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L380

```solidity
File: CollateralTracker.sol

387: return Math.mulDiv(shares, totalAssets(), totalSupply);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L387

```solidity
File: CollateralTracker.sol

393: return type(uint104).max;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L393

```solidity
File: CollateralTracker.sol

446: return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L446

```solidity
File: CollateralTracker.sol

512: return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L512

```solidity
File: CollateralTracker.sol

521: return Math.mulDivRoundingUp(assets, supply, totalAssets());


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L521

```solidity
File: CollateralTracker.sol

575: return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L575

```solidity
File: CollateralTracker.sol

582: return convertToAssets(shares);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L582

```solidity
File: CollateralTracker.sol

743: return int256((s_inAMM * DECIMALS) / totalAssets());


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L743

```solidity
File: CollateralTracker.sol

785: return min_sell_ratio;

791: return DECIMALS;

795: return
                min_sell_ratio +


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L785

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L791

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L795



```solidity
File: CollateralTracker.sol

836: return BUYER_COLLATERAL_RATIO;

843: return BUYER_COLLATERAL_RATIO / 2;

848: return
                (BUYER_COLLATERAL_RATIO +


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L836

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L843

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L848



```solidity
File: CollateralTracker.sol

1285: return
            tokenId.riskPartner(index) == index


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1285

```solidity
File: PanopticPool.sol

399: return (premia.rightSlot(), premia.leftSlot(), balances);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L399

```solidity
File: SemiFungiblePositionManager.sol

833: if (swapAmount == 0) return LeftRightSigned.wrap(0);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L833

```solidity
File: SemiFungiblePositionManager.sol

1558: return s_poolContext[poolId].pool;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1558


</details>




### <a href="#qa-summary">[NC&#x2011;14]</a><a name="NC&#x2011;14"> Dependence on external protocols [SAFE]

External protocols should be monitored as such dependencies may introduce vulnerabilities if a vulnerability is found/introduced in the external protocol

#### <ins>Proof Of Concept</ins>

<details>

```solidity
File: PanopticFactory.sol

9: import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

10: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L9-L10

```solidity
File: PanopticPool.sol

7: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L7

```solidity
File: SemiFungiblePositionManager.sol

5: import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

6: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L5-L6

```solidity
File: CallbackLib.sol

5: import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L5

```solidity
File: FeesCalc.sol

5: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L5

```solidity
File: PanopticMath.sol

6: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L6



</details>




### <a href="#qa-summary">[NC&#x2011;15]</a><a name="NC&#x2011;15"> Duplicated `require()`/`revert()` Checks Should Be Refactored To A Modifier Or Function [SAFE]

Saves deployment costs

#### <ins>Proof Of Concept</ins>

```solidity
File: Math.sol

448: require(result < type(uint256).max);

588: require(result < type(uint256).max);

665: require(result < type(uint256).max);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L448

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L588

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L665








### <a href="#qa-summary">[NC&#x2011;16]</a><a name="NC&#x2011;16"> Duplicated `revert()` checks should be refactored to a `modifier` or `function` [SAFE]

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol

418: if (assets > type(uint104).max) revert Errors.DepositTooLarge();
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L418

```solidity
File: CollateralTracker.sol

480: if (assets > type(uint104).max) revert Errors.DepositTooLarge();
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L480






### <a href="#qa-summary">[NC&#x2011;17]</a><a name="NC&#x2011;17"> `else`-block not required [SAFE]

One level of nesting can be removed by not having an `else` block when the `if`-block returns, and `if (foo) { return 1; } else { return 2; }` becomes `if (foo) { return 1; } return 2;`

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: PanopticMath.sol

325: if (tokenId.asset(legIndex) == 0) {
            return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
        } else {
            return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L325

```solidity
File: PanopticMath.sol

425: if (tokenType == 0) {
            return (
                tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
                tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
            );
        } else {
            return (
                tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
                tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
            );
        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L425

```solidity
File: PanopticMath.sol

494: if (sqrtPriceX96 < type(uint128).max) {
                return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
            } else {
                return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L494

```solidity
File: PanopticMath.sol

511: if (sqrtPriceX96 < type(uint128).max) {
                return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
            } else {
                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L511

```solidity
File: PanopticMath.sol

528: if (sqrtPriceX96 < type(uint128).max) {
                int256 absResult = Math
                    .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L528

```solidity
File: PanopticMath.sol

551: if (sqrtPriceX96 < type(uint128).max) {
                int256 absResult = Math
                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv(
                        Math.absUint(amount),
                        2 ** 128,
                        Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
                    )
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L551



</details>




### <a href="#qa-summary">[NC&#x2011;18]</a><a name="NC&#x2011;18"> Employ Explicit Casting to Bytes or Bytes32 for Enhanced Code Clarity and Meaning  [SAFE]

Smart contracts are complex entities, and clarity in their operations is fundamental to ensure that they function as intended. Casting a single argument instead of utilizing 'abi.encodePacked()' improves the transparency of the operation. It elucidates the intent of the code, reducing ambiguity and making it easier for auditors and developers to understand the code’s purpose. Such practices promote readability and maintainability, thus reducing the likelihood of errors and misunderstandings. Therefore, it's recommended to employ explicit casts for single arguments where possible, to increase the contract's comprehensibility and ensure a smoother review process.

#### <ins>Proof Of Concept</ins>


```solidity
File: PanopticFactory.sol

396: bytes memory mintCallback = abi.encode( //@audit bytes variable = mintCallback


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L396

```solidity
File: SemiFungiblePositionManager.sol

773: data = abi.encode( //@audit bytes variable = data


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L773

```solidity
File: SemiFungiblePositionManager.sol

1190: bytes memory mintdata = abi.encode( //@audit bytes variable = mintdata


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1190



### <a href="#qa-summary">[NC&#x2011;19]</a><a name="NC&#x2011;19"> Enable IR-based code generation [SAFE]

The IR-based code generator was introduced with an aim to not only allow code generation to be more transparent and auditable but also to enable more powerful optimization passes that span across functions.
You can enable it on the command line using `--via-ir` or with the option `{"viaIR": true}`.
This will take longer to compile, but you can just simple test it before deploying and if you got a better benchmark then you can add --via-ir to your deploy command
More on: https://docs.soliditylang.org/en/v0.8.17/ir-breaking-changes.html




### <a href="#qa-summary">[NC&#x2011;20]</a><a name="NC&#x2011;20"> Events are missing sender information [SAFE]

The following functions are missing critical parameters when emitting an event.
When dealing with source address which uses the value of `msg.sender`, the `msg.sender` value must be specified in every transaction, a contract or web page listening to events cannot react to users, emit does not serve the purpose. Basically, this event cannot be used.

#### <ins>Proof Of Concept</ins>


```solidity
File: ERC20Minimal.sol


function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
        uint256 allowed = allowance[from][msg.sender]; 

        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;

        balanceOf[from] -= amount;

        
        
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(from, to, amount);

        return true;
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L94




#### <ins>Recommended Mitigation Steps</ins>
Add `msg.sender` parameter in event-emit



### <a href="#qa-summary">[NC&#x2011;21]</a><a name="NC&#x2011;21"> For extended 'using-for' usage, use the latest pragma version  [SAFE]

Solidity versions of 0.8.13 or above can make use of enhanced using-for notation within contracts.

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: CollateralTracker.sol

38: using Math for uint256;

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L38

```solidity
File: PanopticFactory.sol

56: using Clones for address;

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L56

```solidity
File: SemiFungiblePositionManager.sol

109: using Math for uint256;
110: using Math for int256;

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L109-L110

```solidity
File: PanopticMath.sol

20: using Math for uint256;

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L20

```solidity
File: LeftRight.sol

9: using LeftRightLibrary for LeftRightUnsigned global;
12: using LeftRightLibrary for LeftRightSigned global;
19: using Math for uint256;

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L9-L19

```solidity
File: LiquidityChunk.sol

8: using LiquidityChunkLibrary for LiquidityChunk global;

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L8

```solidity
File: TokenId.sol

10: using TokenIdLibrary for TokenId global;

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L10



</details>





### <a href="#qa-summary">[NC&#x2011;22]</a><a name="NC&#x2011;22"> Functions calling contracts/addresses with transfer hooks are missing reentrancy guards [NOT_SAFE]

While adherence to the check-effects-interaction pattern is commendable, the absence of a reentrancy guard in functions, especially where transfer hooks might be present, can expose the protocol users to risks of read-only reentrancies. Such reentrancy vulnerabilities can be exploited to execute malicious actions even without altering the contract state. Without a reentrancy guard, the only potential mitigation would be to blocklist the entire protocol - an extreme and disruptive measure. Therefore, incorporating a reentrancy guard into these functions is vital to bolster security, as it helps protect against both traditional reentrancy attacks and read-only reentrancies, ensuring robust and safe protocol operations.

#### <ins>Proof Of Concept</ins>

```solidity
File: CollateralTracker.sol

532: function withdraw(
        uint256 assets,
        address receiver,
        address owner
    ) external returns (uint256 shares) {
        if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();

        shares = previewWithdraw(assets);

        
        if (msg.sender != owner) {
            uint256 allowed = allowance[owner][msg.sender]; 

            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
        }

        
        _burn(owner, shares);

        
        unchecked {
            s_poolAssets -= uint128(assets);
        }

        
        SafeTransferLib.safeTransferFrom(
            s_underlyingToken,
            address(s_panopticPool),
            receiver,
            assets
        );

        emit Withdraw(msg.sender, receiver, owner, assets, shares);

        return shares;
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L532



### <a href="#qa-summary">[NC&#x2011;23]</a><a name="NC&#x2011;23"> Hardcoded String that is repeatedly used can be replaced with a constant [NOT_SAFE]

Some strings are repeatedly used in the contracts. For better maintainability, please consider replacing it with a `constant`.
 
#### <ins>Proof Of Concept</ins>

```solidity
File: InteractionHelper.sol

63: symbol0 = "???";
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L63

```solidity
File: InteractionHelper.sol

68: symbol1 = "???";
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L68


```solidity
File: InteractionHelper.sol

100: return string.concat(prefix, "???");
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L100




### <a href="#qa-summary">[NC&#x2011;24]</a><a name="NC&#x2011;24"> `if`-statement can be converted to a ternary [SAFE]

The code can be made more compact while also increasing readability by converting the following `if`-statements to ternaries (e.g. `foo += (x > y) ? a : b`)

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: CollateralTracker.sol

976: if (assets > 0) {
            _transferFrom(refunder, refundee, convertToShares(uint256(assets)));
        } else {
            unchecked {
                _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));
            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L976

```solidity
File: CollateralTracker.sol

1559: if (tokenType == 1) {
                    notional = movedRight;
                    notionalP = movedPartnerRight;
                    contracts = movedLeft;
                } else {
                    notional = movedLeft;
                    notionalP = movedPartnerLeft;
                    contracts = movedRight;
                }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1559


```solidity
File: PanopticPool.sol

914: if (SLOW_ORACLE_UNISWAP_MODE) {
            slowOracleTick = PanopticMath.computeMedianObservedPrice(
                _univ3pool,
                observationIndex,
                observationCardinality,
                SLOW_ORACLE_CARDINALITY,
                SLOW_ORACLE_PERIOD
            );
        } else {
            (slowOracleTick, medianData) = PanopticMath.computeInternalMedian(
                observationIndex,
                observationCardinality,
                MEDIAN_PERIOD,
                s_miniMedian,
                _univ3pool
            );
        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L914

```solidity
File: FeesCalc.sol

67: if (tokenId.isLong(leg) == 0) {
                    unchecked {
                        value0 += int256(amount0);
                        value1 += int256(amount1);
                    }
                } else {
                    unchecked {
                        value0 -= int256(amount0);
                        value1 -= int256(amount1);
                    }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L67

```solidity
File: PanopticMath.sol

325: if (tokenId.asset(legIndex) == 0) {
            return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
        } else {
            return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L325

```solidity
File: PanopticMath.sol

425: if (tokenType == 0) {
            return (
                tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
                tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
            );
        } else {
            return (
                tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
                tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
            );
        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L425

```solidity
File: PanopticMath.sol

494: if (sqrtPriceX96 < type(uint128).max) {
                return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
            } else {
                return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L494

```solidity
File: PanopticMath.sol

511: if (sqrtPriceX96 < type(uint128).max) {
                return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
            } else {
                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L511

```solidity
File: PanopticMath.sol

528: if (sqrtPriceX96 < type(uint128).max) {
                int256 absResult = Math
                    .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L528

</details>




### <a href="#qa-summary">[NC&#x2011;25]</a><a name="NC&#x2011;25"> `if` statement control structures do not comply with best practices [SAFE]

If statements which include a single line do not need to have curly brackets, however according to the Solidiity style guide the line of code executed upon the if statement condition being met should still be on the next line, not on the same line as the if statement declaration.

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol

544: if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L544



```solidity
File: CollateralTracker.sol

602: if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L602



```solidity
File: CollateralTracker.sol

664: if (positionId.isLong(leg) == 0) continue;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L664


```solidity
File: PanopticPool.sol

533: if (medianData != 0) s_miniMedian = medianData;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L533

```solidity
File: PanopticPool.sol

664: if (medianData != 0) s_miniMedian = medianData;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L664



### <a href="#qa-summary">[NC&#x2011;26]</a><a name="NC&#x2011;26"> Inconsistent Spacing In Comments [SAFE]

Some lines use // x and some use //x. The instances below point out the usages that don’t follow the majority, within each file

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol

1118: //compute total commission amount = commission rate + spread fee
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1118

```solidity
File: SemiFungiblePositionManager.sol

610: //construct the positionKey for the from and to addresses
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L610

```solidity
File: SemiFungiblePositionManager.sol

821: //compute the swap amount, set as positive (exact input)
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L821





### <a href="#qa-summary">[NC&#x2011;27]</a><a name="NC&#x2011;27"> Incorrect withdraw declaration [SAFE]

In Solidity, it's essential for clarity and interoperability to correctly specify return types in function declarations. If the `withdraw` function is expected to return a `bool` to indicate success or failure, its omission could lead to ambiguity or unexpected behavior when interacting with or calling this function from other contracts or off-chain systems. Missing return values can mislead developers and potentially lead to contract integrations built on incorrect assumptions. To resolve this, the function declaration for `withdraw` should be modified to explicitly include the `bool` return type, ensuring clarity and correctness in contract interactions.

#### <ins>Proof Of Concept</ins>


```solidity
File: CollateralTracker.sol

531: function withdraw(
        uint256 assets,
        address receiver,
        address owner
    ) external returns (uint256 shares) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L532



### <a href="#qa-summary">[NC&#x2011;28]</a><a name="NC&#x2011;28"> Interface imports should be declared first [SAFE]

Amend the ordering of imports to import interfaces first followed by other imports

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: CollateralTracker.sol

12: import {InteractionHelper} from "@libraries/InteractionHelper.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L12

```solidity
File: PanopticFactory.sol

8: import {IDonorNFT} from "@contracts/tokens/interfaces/IDonorNFT.sol";

9: import {IUniswapV3Factory} from "univ3-core/interfaces/IUniswapV3Factory.sol";

10: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L8-L10

```solidity
File: PanopticPool.sol

7: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";

15: import {InteractionHelper} from "@libraries/InteractionHelper.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L7

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L15



```solidity
File: InteractionHelper.sol

6: import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

7: import {IERC20Partial} from "@tokens/interfaces/IERC20Partial.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L6-L7

```solidity
File: PanopticMath.sol

6: import {IUniswapV3Pool} from "univ3-core/interfaces/IUniswapV3Pool.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L6



</details>



### <a href="#qa-summary">[NC&#x2011;29]</a><a name="NC&#x2011;29"> Make use of Solidity's `using` keyword [NOT_SAFE]

The directive `using A for B` can be used to attach functions (`A`) as operators to user-defined value types or as member functions to any type (`B`). The member functions receive the object they are called on as their first parameter (like the `self` variable in Python). The operator functions receive operands as parameters.  Doing so improves readability, makes debugging easier, and promotes modularity and reusability in the code.

#### <ins>Proof Of Concept</ins>


```solidity
File: PanopticFactory.sol

226: IUniswapV3Pool v3Pool = IUniswapV3Pool(UNIV3_FACTORY.getPool(token0, token1, fee));
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L226

```solidity
File: SemiFungiblePositionManager.sol

1472: IUniswapV3Pool _univ3pool = IUniswapV3Pool(univ3pool);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1472



### <a href="#qa-summary">[NC&#x2011;30]</a><a name="NC&#x2011;30"> Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability [SAFE]

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related

#### <ins>Proof Of Concept</ins>


```solidity
File: PanopticPool.sol

238: mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L238

```solidity
File: PanopticPool.sol

258: mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L258

```solidity
File: PanopticPool.sol

272: mapping(address account => uint256 positionsHash) internal s_positionsHash;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L272

```solidity
File: ERC1155Minimal.sol

66: mapping(address account => mapping(uint256 tokenId => uint256 balance)) public balanceOf;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L66

```solidity
File: ERC1155Minimal.sol

71: mapping(address owner => mapping(address operator => bool approvedForAll))
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L71

```solidity
File: ERC20Minimal.sol

35: mapping(address account => uint256 balance) public balanceOf;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L35

```solidity
File: ERC20Minimal.sol

39: mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L39



### <a href="#qa-summary">[NC&#x2011;31]</a><a name="NC&#x2011;31"> No equate comparison checks between `to` and `from` address parameters [NOT_SAFE]

The function lacks a standard check: it does not validate if the 'to' and 'from' addresses are identical. This omission can lead to unintended outcomes if the same address is used in both parameters. To rectify this, we recommend implementing a comparison check at the beginning of the function. In the context of Solidity, the command `require(to != from, "To and From addresses can't be the same");` could be utilized. This addition will generate an error if the 'to' and 'from' addresses are the same, thereby fortifying the function's robustness and security.

#### <ins>Proof Of Concept</ins>


```solidity
File: SemiFungiblePositionManager.sol

593: function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {
        
        id.validate();

        
        IUniswapV3Pool univ3pool = s_poolContext[id.poolId()].pool;

        uint256 numLegs = id.countLegs();
        for (uint256 leg = 0; leg < numLegs; ) {
            
            
            LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                id,
                leg,
                uint128(amount)
            );

            
            bytes32 positionKey_from = keccak256(
                abi.encodePacked(
                    address(univ3pool),
                    from,
                    id.tokenType(leg),
                    liquidityChunk.tickLower(),
                    liquidityChunk.tickUpper()
                )
            );
            bytes32 positionKey_to = keccak256(
                abi.encodePacked(
                    address(univ3pool),
                    to,
                    id.tokenType(leg),
                    liquidityChunk.tickLower(),
                    liquidityChunk.tickUpper()
                )
            );

            
            if (
                (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
                (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)
            ) revert Errors.TransferFailed();

            
            LeftRightUnsigned fromLiq = s_accountLiquidity[positionKey_from];
            if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity())
                revert Errors.TransferFailed();

            LeftRightSigned fromBase = s_accountFeesBase[positionKey_from];

            
            s_accountLiquidity[positionKey_to] = fromLiq;
            s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);

            s_accountFeesBase[positionKey_to] = fromBase;
            s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);
            unchecked {
                ++leg;
            }
        }
    }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L593


```solidity
File: ERC20Minimal.sol

81: function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
        uint256 allowed = allowance[from][msg.sender]; 

        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;

        balanceOf[from] -= amount;

        
        
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(from, to, amount);

        return true;
    }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L81

```solidity
File: ERC20Minimal.sol

103: function _transferFrom(address from, address to, uint256 amount) internal {
        balanceOf[from] -= amount;

        
        
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(from, to, amount);
    }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L103





### <a href="#qa-summary">[NC&#x2011;32]</a><a name="NC&#x2011;32"> Non-assembly method available [SAFE]

There are some automated tools that will flag a project as having higher complexity if there is inline-assembly, so it's best to avoid using it where it's not necessary. In addition, most assembly methods can be replaced by non-assembly methods, for example:
- `assembly{ g := gas() }` => `uint256 g = gasleft()`
- `assembly{ id := chainid() }` => `uint256 id = block.chainid`
- `assembly { r := mulmod(a, b, d) }` => `uint256 m = mulmod(x, y, k)`
- `assembly { size := extcodesize() }` => `uint256 size = address(a).code.length`
- etc.

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: Math.sol

354: let mm := mulmod(a, b, not(0))

380: remainder := mulmod(a, b, denominator)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L354

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L380



```solidity
File: Math.sol

468: let mm := mulmod(a, b, not(0))

494: remainder := mulmod(a, b, 0x10000000000000000)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L468

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L494



```solidity
File: Math.sol

531: let mm := mulmod(a, b, not(0))

557: remainder := mulmod(a, b, 0x1000000000000000000000000)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L531

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L557



```solidity
File: Math.sol

608: let mm := mulmod(a, b, not(0))

634: remainder := mulmod(a, b, 0x100000000000000000000000000000000)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L608

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L634



```solidity
File: Math.sol

685: let mm := mulmod(a, b, not(0))

711: remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L685

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L711



```solidity
File: SafeTransferLib.sol

41: call(gas(), token, 0, p, 100, 0, 32)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L41

```solidity
File: SafeTransferLib.sol

71: call(gas(), token, 0, p, 68, 0, 32)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L71

```solidity
File: Multicall.sol

26: revert(add(result, 32), mload(result))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L26



</details>



### <a href="#qa-summary">[NC&#x2011;33]</a><a name="NC&#x2011;33"> Off-by-one timestamp error [SAFE]

In Solidity, using `>=` or `<=` to compare against `block.timestamp` (alias `now`) may introduce off-by-one errors due to the fact that `block.timestamp` is only updated once per block and its value remains constant throughout the block's execution. If an operation happens at the exact second when `block.timestamp` changes, it could result in unexpected behavior. To avoid this, it's safer to use strict inequality operators (`>` or `<`). For instance, if a condition should only be met after a certain time, use `block.timestamp > time` rather than `block.timestamp >= time`. This way, potential off-by-one errors due to the exact timing of block mining are mitigated, leading to safer, more predictable contract behavior.

#### <ins>Proof Of Concept</ins>


```solidity
File: PanopticMath.sol

183: if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L183



### <a href="#qa-summary">[NC&#x2011;34]</a><a name="NC&#x2011;34"> Operations such as the changing of the owner should be behind a timelock [SAFE]

From the point of view of a user, the changing of the owner of a contract is a high risk operation that may have outcomes ranging from an attacker gaining control over the protocol, to the function no longer functioning due to a typo in the destination address. To give users plenty of warning so that they can validate any ownership changes, changes of ownership should be behind a timelock.

#### <ins>Proof Of Concept</ins>


```solidity
File: PanopticFactory.sol

147: function transferOwnership(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L147






### <a href="#qa-summary">[NC&#x2011;35]</a><a name="NC&#x2011;35"> Order of argument evaluation disrupted in non-expression-split code by optimizer sequences with FullInliner [SAFE]

Function call arguments in Yul are evaluated right to left. This order matters when the argument expressions have side-effects, and changing it may change contract behavior. `FullInliner` is an optimizer step that can replace a function call with the body of that function. The transformation involves assigning argument expressions to temporary variables, which imposes an explicit evaluation order. 

`FullInliner` was written with the assumption that this order does not necessarily have to match usual argument evaluation order because the argument expressions have no side-effects. In most circumstances this assumption is true because the default optimization step sequence contains the ExpressionSplitter step. ExpressionSplitter ensures that the code is in *expression-split form*, which means that function calls cannot appear nested inside expressions, and all function call arguments have to be variables. 

The assumption is, however, not guaranteed to be true in general. Version 0.6.7 introduced a setting allowing users to specify an arbitrary optimization step sequence, making it possible for the `FullInliner` to actually encounter argument expressions with side-effects, which can result in behavior differences between optimized and unoptimized bytecode. 

Contracts compiled without optimization or with the default optimization sequence are not affected. To trigger the bug the user has to explicitly choose compiler settings that contain a sequence with `FullInliner` step not preceded by ExpressionSplitter. [Ref](https://blog.soliditylang.org/2023/07/19/full-inliner-non-expression-split-argument-evaluation-order-bug/)

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: CollateralTracker.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L2

```solidity
File: PanopticFactory.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L2

```solidity
File: PanopticPool.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L2

```solidity
File: SemiFungiblePositionManager.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L2

```solidity
File: CallbackLib.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L2

```solidity
File: Constants.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L2

```solidity
File: Errors.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol#L2

```solidity
File: FeesCalc.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L2

```solidity
File: InteractionHelper.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L2

```solidity
File: Math.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L2

```solidity
File: PanopticMath.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L2

```solidity
File: SafeTransferLib.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L2

```solidity
File: Multicall.sol

pragma solidity ^0.8.18;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L2

```solidity
File: ERC1155Minimal.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L2

```solidity
File: ERC20Minimal.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L2

```solidity
File: IDonorNFT.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L2

```solidity
File: IERC20Partial.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L2

```solidity
File: LeftRight.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L2

```solidity
File: LiquidityChunk.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L2

```solidity
File: TokenId.sol

pragma solidity ^0.8.0;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L2



</details>




### <a href="#qa-summary">[NC&#x2011;36]</a><a name="NC&#x2011;36"> Overly complicated arithmetic [SAFE]

To maintain readability in code, particularly in Solidity which can involve complex mathematical operations, it is often recommended to limit the number of arithmetic operations to a maximum of 2-3 per line. Too many operations in a single line can make the code difficult to read and understand, increase the likelihood of mistakes, and complicate the process of debugging and reviewing the code. Consider splitting such operations over more than one line, take special care when dealing with division however. Try to limit the number of arithmetic operations to a maximum of 3 per line.

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: PanopticMath.sol

223: newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L223

```solidity
File: PanopticMath.sol

258: (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L258

```solidity
File: TokenId.sol

229: TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L229

```solidity
File: TokenId.sol

246: return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L246

```solidity
File: TokenId.sol

263: TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L263

```solidity
File: TokenId.sol

281: TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L281



</details>



### <a href="#qa-summary">[NC&#x2011;37]</a><a name="NC&#x2011;37"> Private variables dont respect naming convention [SAFE]

All private variables should start with `_` but following do not respect the naming convention.

#### <ins>Proof Of Concept</ins>


```solidity
File: SemiFungiblePositionManager.sol

133: uint128 private constant VEGOID = 2;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L133



### <a href="#qa-summary">[NC&#x2011;38]</a><a name="NC&#x2011;38"> Redundant Cast [NOT_SAFE]

The type of the variable is the same as the type to which the variable is being cast

#### <ins>Proof Of Concept</ins>


```solidity
File: PanopticFactory.sol

404: IUniswapV3Pool(v3Pool)
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L404

```solidity
File: PanopticPool.sol

302: IUniswapV3Pool(_univ3pool)
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L302




### <a href="#qa-summary">[NC&#x2011;39]</a><a name="NC&#x2011;39"> Redundant code `length` check [SAFE]

In the following functions, there is a check for code `length != 0` which is meant to determine if the to address is a contract. However, this is redundant due to the EIP-1155 standard's requirement for the receiver to implement the ERC1155 token receiver interface.

#### <ins>Proof Of Concept</ins>


```solidity
File: ERC1155Minimal.sol

112: if (to.code.length != 0) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L112

```solidity
File: ERC1155Minimal.sol

163: if (to.code.length != 0) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L163

```solidity
File: ERC1155Minimal.sol

222: if (to.code.length != 0) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L222



### <a href="#qa-summary">[NC&#x2011;40]</a><a name="NC&#x2011;40"> Remove unused `error` definition [SAFE]

Note that there may be cases where an error superficially appears to be used, but this is only because there are multiple definitions of the error in different files. In such cases, the error definition should be moved into a separate file. The instances below are the unused definitions.

#### <ins>Proof Of Concept</ins>


```solidity
File: Errors.sol

error ExerciseeNotSolvent
error LeftRightInputError

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol



### <a href="#qa-summary">[NC&#x2011;41]</a><a name="NC&#x2011;41"> Returning a struct instead of a bunch of variables is better [SAFE]

If a function returns [too many variables](https://docs.soliditylang.org/en/v0.8.23/contracts.html#returning-multiple-values), replacing them with a struct can improve code readability, maintainability and reusability.

#### <ins>Proof Of Concept</ins>

<details>

```solidity
File: CollateralTracker.sol

277: function getPoolData()
        external
        view
        returns (uint256 poolAssets, uint256 insideAMM, int256 currentPoolUtilization)
    {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L277

```solidity
File: PanopticPool.sol

352: function optionPositionBalance(
        address user,
        TokenId tokenId
    ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L352

```solidity
File: PanopticPool.sol

381: function calculateAccumulatedFeesBatch(
        address user,
        bool includePendingPremium,
        TokenId[] calldata positionIdList
    ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L381

```solidity
File: PanopticPool.sol

955: function _burnAndHandleExercise(
        bool commitLongSettled,
        int24 tickLimitLow,
        int24 tickLimitHigh,
        TokenId tokenId,
        uint128 positionSize,
        address owner
    )
        internal
        returns (
            LeftRightSigned realizedPremia,
            LeftRightSigned[4] memory premiaByLeg,
            LeftRightSigned paidAmounts
        )
    {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L955

```solidity
File: SemiFungiblePositionManager.sol

863: function _createPositionInAMM(
        IUniswapV3Pool univ3pool,
        TokenId tokenId,
        uint128 positionSize,
        bool isBurn
    )
        internal
        returns (
            LeftRightSigned totalMoved,
            LeftRightUnsigned[4] memory collectedByLeg,
            LeftRightSigned itmAmounts
        )
    {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L863

```solidity
File: SemiFungiblePositionManager.sol

958: function _createLegInAMM(
        IUniswapV3Pool univ3pool,
        TokenId tokenId,
        uint256 leg,
        LiquidityChunk liquidityChunk,
        bool isBurn
    )
        internal
        returns (
            LeftRightSigned moved,
            LeftRightSigned itmAmounts,
            LeftRightUnsigned collectedSingleLeg
        )
    {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L958

```solidity
File: PanopticMath.sol

651: function getLiquidationBonus(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint160 sqrtPriceX96Twap,
        uint160 sqrtPriceX96Final,
        LeftRightSigned netExchanged,
        LeftRightSigned premia
    ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L651



</details>



### <a href="#qa-summary">[NC&#x2011;42]</a><a name="NC&#x2011;42"> Uncommented fields in a struct [NOT_SAFE]

Consider adding comments for all the fields in a struct to improve the readability of the codebase.

#### <ins>Proof Of Concept</ins>


```solidity
File: CallbackLib.sol

14: struct PoolFeatures {
        address token0;
        address token1;
        uint24 fee;
    }
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L14

```solidity
File: CallbackLib.sol

21: struct CallbackData {
        PoolFeatures poolFeatures;
        address payer;
    }
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L21



### <a href="#qa-summary">[NC&#x2011;43]</a><a name="NC&#x2011;43"> Use a struct to encapsulate multiple function parameters [SAFE]

If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

#### <ins>Proof Of Concept</ins>

```solidity
File: SemiFungiblePositionManager.sol

1449: function getAccountPremium(
        address univ3pool,
        address owner,
        uint256 tokenType,
        int24 tickLower,
        int24 tickUpper,
        int24 atTick,
        uint256 isLong
    ) external view returns (uint128, uint128) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1449

```solidity
File: PanopticMath.sol

768: function haircutPremia(
        address liquidatee,
        TokenId[] memory positionIdList,
        LeftRightSigned[4][] memory premiasByLeg,
        LeftRightSigned collateralRemaining,
        CollateralTracker collateral0,
        CollateralTracker collateral1,
        uint160 sqrtPriceX96Final,
        mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
    ) external returns (int256, int256) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768

```solidity
File: TokenId.sol

336: function addLeg(
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

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L336






### <a href="#qa-summary">[NC&#x2011;44]</a><a name="NC&#x2011;44"> Use `@inheritdoc` for overridden functions [NOT_SAFE]

It is recommended to use `@inheritdoc` for overridden functions.

#### <ins>Proof Of Concept</ins>

```solidity
File: CollateralTracker.sol

323: function transfer(
        address recipient,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L323

```solidity
File: CollateralTracker.sol

341: function transferFrom(
        address from,
        address to,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L341

```solidity
File: SemiFungiblePositionManager.sol

540: function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public override {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L540

```solidity
File: SemiFungiblePositionManager.sol

566: function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public override {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566



### <a href="#qa-summary">[NC&#x2011;45]</a><a name="NC&#x2011;45"> Use of `override` is unnecessary [SAFE]

[Starting from Solidity 0.8.8](https://docs.soliditylang.org/en/v0.8.23/contracts.html#function-overriding), the override keyword is not required when overriding an interface function.

#### <ins>Proof Of Concept</ins>

```solidity
File: SemiFungiblePositionManager.sol

540: function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public override {

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L540

```solidity
File: SemiFungiblePositionManager.sol

566: function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public override {

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566



### <a href="#qa-summary">[NC&#x2011;46]</a><a name="NC&#x2011;46"> Use a single file for system wide constants [SAFE]

There are many addresses and constants used in the system. It is recommended to put the most used ones in one file (for example `constants.sol`, use inheritance to access these values)

This will help with readability and easier maintenance for future changes.

`constants.sol` Use and import this file in contracts that require access to these values. This is just a suggestion, in some use cases this may result in higher gas usage in the distribution

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: CollateralTracker.sol

70: string internal constant TICKER_PREFIX = "po";
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L70

```solidity
File: CollateralTracker.sol

73: string internal constant NAME_PREFIX = "POPT-V1";
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L73

```solidity
File: CollateralTracker.sol

77: uint256 internal constant DECIMALS = 10_000;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L77

```solidity
File: CollateralTracker.sol

81: int128 internal constant DECIMALS_128 = 10_000;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L81

```solidity
File: PanopticFactory.sol

82: uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L82

```solidity
File: PanopticFactory.sol

86: uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L86

```solidity
File: PanopticFactory.sol

89: uint16 internal constant CARDINALITY_INCREASE = 100;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L89

```solidity
File: PanopticPool.sol

103: int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L103

```solidity
File: PanopticPool.sol

105: int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L105

```solidity
File: PanopticPool.sol

109: bool internal constant COMPUTE_ALL_PREMIA = true;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L109

```solidity
File: PanopticPool.sol

111: bool internal constant COMPUTE_LONG_PREMIA = false;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L111

```solidity
File: PanopticPool.sol

114: bool internal constant ONLY_AVAILABLE_PREMIUM = false;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L114

```solidity
File: PanopticPool.sol

119: bool internal constant COMMIT_LONG_SETTLED = true;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L119

```solidity
File: PanopticPool.sol

120: bool internal constant DONOT_COMMIT_LONG_SETTLED = false;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L120

```solidity
File: PanopticPool.sol

123: bool internal constant ADD = true;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L123

```solidity
File: PanopticPool.sol

128: uint32 internal constant TWAP_WINDOW = 600;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L128

```solidity
File: PanopticPool.sol

133: bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L133

```solidity
File: PanopticPool.sol

136: uint256 internal constant MEDIAN_PERIOD = 60;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L136

```solidity
File: PanopticPool.sol

139: uint256 internal constant FAST_ORACLE_CARDINALITY = 3;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L139

```solidity
File: PanopticPool.sol

145: uint256 internal constant FAST_ORACLE_PERIOD = 1;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L145

```solidity
File: PanopticPool.sol

148: uint256 internal constant SLOW_ORACLE_CARDINALITY = 7;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L148

```solidity
File: PanopticPool.sol

152: uint256 internal constant SLOW_ORACLE_PERIOD = 5;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L152

```solidity
File: PanopticPool.sol

156: int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L156

```solidity
File: PanopticPool.sol

160: int256 internal constant MAX_SLOW_FAST_DELTA = 1800;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L160

```solidity
File: PanopticPool.sol

165: uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L165

```solidity
File: PanopticPool.sol

168: uint64 internal constant MAX_POSITIONS = 32;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L168

```solidity
File: PanopticPool.sol

171: uint256 internal constant BP_DECREASE_BUFFER = 13_333;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L171

```solidity
File: PanopticPool.sol

174: uint256 internal constant NO_BUFFER = 10_000;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L174

```solidity
File: SemiFungiblePositionManager.sol

125: bool internal constant MINT = false;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L125

```solidity
File: SemiFungiblePositionManager.sol

126: bool internal constant BURN = true;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L126

```solidity
File: SemiFungiblePositionManager.sol

133: uint128 private constant VEGOID = 2;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L133


```solidity
File: LiquidityChunk.sol

54: uint256 internal constant CLEAR_TL_MASK =
        0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L54

```solidity
File: LiquidityChunk.sol

58: uint256 internal constant CLEAR_TU_MASK =
        0xFFFFFF000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L58

```solidity
File: TokenId.sol

62: uint256 internal constant LONG_MASK =
        0x100_000000000100_000000000100_000000000100_0000000000000000;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L62

```solidity
File: TokenId.sol

66: uint256 internal constant CLEAR_POOLID_MASK =
        0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF_0000000000000000;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L66

```solidity
File: TokenId.sol

70: uint256 internal constant OPTION_RATIO_MASK =
        0x0000000000FE_0000000000FE_0000000000FE_0000000000FE_0000000000000000;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L70

```solidity
File: TokenId.sol

74: uint256 internal constant CHUNK_MASK =
        0xFFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_FFFFFFFFF200_0000000000000000;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L74

```solidity
File: TokenId.sol

78: int256 internal constant BITMASK_INT24 = 0xFFFFFF;
```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L78



</details>




### <a href="#qa-summary">[NC&#x2011;47]</a><a name="NC&#x2011;47"> Use SMTChecker [SAFE]

The highest tier of smart contract behavior assurance is formal mathematical verification. All assertions that are made are guaranteed to be true across all inputs → The quality of your asserts is the quality of your verification

https://twitter.com/0xOwenThurm/status/1614359896350425088?t=dbG9gHFigBX85Rv29lOjIQ&s=19



### <a href="#qa-summary">[NC&#x2011;48]</a><a name="NC&#x2011;48"> Utilizing `delegatecall` within a loop [SAFE]

Using `delegatecall` in a `for` loop can lead to high gas costs, as `delegatecall` is an expensive operation and its costs compound when used in a loop. Additionally, it can pose security risks including reentrancy attacks, as it executes code in the calling contract's context. The function selector collisions can also lead to unpredictable behaviour. To mitigate these risks, control the loop's iterations, apply a reentrancy guard, strictly audit contracts called via `delegatecall`, and consider alternatives like `call` or proxy patterns if the use case allows. Always thoroughly vet contracts involved in `delegatecall` operations. 

#### <ins>Proof Of Concept</ins>


```solidity
File: Multicall.sol

15: (bool success, bytes memory result) = address(this).delegatecall(data[i]);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L15



### <a href="#qa-summary">[NC&#x2011;49]</a><a name="NC&#x2011;49"> Visibility should be set explicitly rather than defaulting to `internal` [NOT_SAFE]

#### <ins>Proof Of Concept</ins>


<details>

```solidity
File: CollateralTracker.sol

510: uint256 available = s_poolAssets;

519: uint256 supply = totalSupply;

659: uint256 maxNumRangesFromStrike = 1;

773: uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;

1251: bool underlyingIsToken0 = s_underlyingIsToken0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L510

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L519

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L659

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L773

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1251



```solidity
File: PanopticFactory.sol

148: address currentOwner = s_owner;

223: address _owner = s_owner;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L148

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L223



```solidity
File: PanopticPool.sol

439: address c_user = user;

1117: address _liquidatee = liquidatee;

1923: uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;

1924: uint256 _leg = leg;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L439

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1117

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1923

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1924



```solidity
File: SemiFungiblePositionManager.sol

891: bool _isBurn = isBurn;

892: uint128 _positionSize = positionSize;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L891-L892

```solidity
File: PanopticMath.sol

203: uint24 shift = 1;

204: bool below = true;

855: address _liquidatee = liquidatee;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L203

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L204

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L855





</details>



### <a href="#qa-summary">[NC&#x2011;50]</a><a name="NC&#x2011;50"> Zero as a function argument should have a descriptive meaning [SAFE]

Consider using descriptive constants or an enum instead of passing zero directly on function calls, as that might be error-prone, to fully describe the caller's intention.

#### <ins>Proof Of Concept</ins>


```solidity
File: PanopticPool.sol

1227: _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1227

```solidity
File: PanopticPool.sol

1639: s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());

1640: s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1639-L1640


