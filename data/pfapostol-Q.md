The content section shows only 10 examples, subsequent cases are listed as links.

## Low Risk Issues

|Index|Issue|Instances|
|:---:|:---|:---:|
| [L-01](#L-01) | [Code does not follow the best practice of check-effects-interaction](#L-01) | 38 |
| [L-02](#L-02) | [Subtraction may underflow if multiplication is too large](#L-02) | 13 |
| [L-03](#L-03) | [Functions calling contracts/addresses with transfer hooks are missing reentrancy guards](#L-03) | 12 |
| [L-04](#L-04) | [Use of `abi.encodePacked` with dynamic types inside `keccak256`](#L-04) | 12 |
| [L-05](#L-05) | [Privileged functions can create points of failure](#L-05) | 10 |
| [L-06](#L-06) | [Must approve or increase allowance first](#L-06) | 9 |
| [L-07](#L-07) | [Consider bounding input array length](#L-07) | 8 |
| [L-08](#L-08) | [Array lengths not checked](#L-08) | 7 |
| [L-09](#L-09) | [Contract contains payable multicall](#L-09) | 1 |
| [L-10](#L-10) | [External call recipient may consume all transaction gas](#L-10) | 1 |

111 instances over 10 issues

---

## NonCritical Risk Issues

|Index|Issue|Instances|
|:---:|:---|:---:|
| [N-01](#N-01) | [Complex math should be split into multiple steps](#N-01) | 114 |
| [N-02](#N-02) | [Variable names don't follow the Solidity naming convention](#N-02) | 92 |
| [N-03](#N-03) | [Duplicated `require/if` statements should be refactored](#N-03) | 87 |
| [N-04](#N-04) | [Overflows in unchecked blocks](#N-04) | 82 |
| [N-05](#N-05) | [Unsafe `uint` to `int` conversion](#N-05) | 79 |
| [N-06](#N-06) | [Use a single file for system wide constants](#N-06) | 49 |
| [N-07](#N-07) | [Private and internal state variables should have a preceding _ in their name unless they are constants](#N-07) | 44 |
| [N-08](#N-08) | [Function names should differ to make the code more readable](#N-08) | 31 |
| [N-09](#N-09) | [Floating pragma should be avoided](#N-09) | 20 |
| [N-10](#N-10) | [Unused contract variables](#N-10) | 18 |
| [N-11](#N-11) | [Inconsistent usage of `require`/`error`](#N-11) | 14 |
| [N-12](#N-12) | [Events should be emitted before external calls](#N-12) | 14 |
| [N-13](#N-13) | [Use multiple `require()` and `if` statements instead of `&&`](#N-13) | 13 |
| [N-14](#N-14) | [State variables not capped at reasonable values](#N-14) | 13 |
| [N-15](#N-15) | [Function names should use lowerCamelCase](#N-15) | 11 |
| [N-16](#N-16) | [`else`-block not required](#N-16) | 9 |
| [N-17](#N-17) | [State variables should include comments](#N-17) | 9 |
| [N-18](#N-18) | [Custom `error` should be used rather than `require`/`assert`](#N-18) | 9 |
| [N-19](#N-19) | [Numeric values having to do with time should use time units for readability](#N-19) | 8 |
| [N-20](#N-20) | [Unused function parameter](#N-20) | 8 |
| [N-21](#N-21) | [Events may be emitted out of order due to reentrancy](#N-21) | 7 |
| [N-22](#N-22) | [Expressions for constant values should use `immutable` rather than `constant`](#N-22) | 7 |
| [N-23](#N-23) | [Missing event and or timelock for critical parameter change](#N-23) | 6 |
| [N-24](#N-24) | [Setters should prevent re-setting of the same value](#N-24) | 6 |
| [N-25](#N-25) | [Typos](#N-25) | 6 |
| [N-26](#N-26) | [Consider using `delete` rather than assigning zero/false to clear values](#N-26) | 5 |
| [N-27](#N-27) | [Use of `override` is unnecessary](#N-27) | 4 |
| [N-28](#N-28) | [Consider disallowing transfers to `address(this)`](#N-28) | 4 |
| [N-29](#N-29) | [Use `@inheritdoc` for overridden functions](#N-29) | 4 |
| [N-30](#N-30) | [Emits without `msg.sender` parameter](#N-30) | 3 |
| [N-31](#N-31) | [`constructor` missing zero address check](#N-31) | 3 |
| [N-32](#N-32) | [Consider adding a block/deny-list](#N-32) | 3 |
| [N-33](#N-33) | [Variable names that consist of all capital letters should be reserved for `constant`/`immutable` variables](#N-33) | 2 |
| [N-34](#N-34) | [Assembly block creates dirty bits](#N-34) | 2 |
| [N-35](#N-35) | [Contract name does not follow the Solidity Style Guide](#N-35) | 2 |
| [N-36](#N-36) | [Remaining eth may not be refunded to users](#N-36) | 1 |
| [N-37](#N-37) | [Missing zero address check in initializer](#N-37) | 1 |

790 instances over 37 issues

---



## Low Risk Issues

### [L-01] Code does not follow the best practice of check-effects-interaction
<a name="L-01"></a>
[To the top](#TOP)

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 38 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
// @audit Some statements does not follow CEI
417	    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
...
// @audit Statement out of CEI order
436	            s_poolAssets += uint128(assets);
...
// @audit Some statements does not follow CEI
477	    function mint(uint256 shares, address receiver) external returns (uint256 assets) {
...
// @audit Statement out of CEI order
496	            s_poolAssets += uint128(assets);
...
// @audit Some statements does not follow CEI
995	    function takeCommissionAddData(
996	        address optionOwner,
997	        int128 longAmount,
998	        int128 shortAmount,
999	        int128 swappedAmount
1000	    ) external onlyPanopticPool returns (int256 utilization) {
...
// @audit Statement out of CEI order
1031	            utilization = _poolUtilization();
...
// @audit Some statements does not follow CEI
1043	    function exercise(
1044	        address optionOwner,
1045	        int128 longAmount,
1046	        int128 shortAmount,
1047	        int128 swappedAmount,
1048	        int128 realizedPremium
1049	    ) external onlyPanopticPool returns (int128) {
...
// @audit Statement out of CEI order
1085	            s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));
```
[436](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L436)
[496](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L496)
[1031](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1031)
[1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085)

---

	 - contracts/PanopticPool.sol

```solidity
// @audit Some statements does not follow CEI
338	    function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {
...
// @audit Statement out of CEI order
342	            revert Errors.PriceBoundFail();
```
[342](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L342)
[664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L664)
[693](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L693)
[945](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L945)
[1165..1168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1165-L1168)
[1394](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1394)
[1493](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1493)

---

	 - contracts/SemiFungiblePositionManager.sol

[488..494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L488-L494)
[520..526](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L520-L526)
[648](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L648)
[728](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L728)
[940](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L940)

---

	 - contracts/libraries/InteractionHelper.sol

[65..69](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L65-L69)

---

	 - contracts/libraries/Math.sol

[431](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L431)
[511](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L511)
[574](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L574)
[651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L651)
[728](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L728)

---

	 - contracts/libraries/PanopticMath.sol

[361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L361)
[479](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L479)
[897..901](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L897-L901)

---

	 - contracts/libraries/SafeTransferLib.sol

[45](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L45)
[75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L75)

---

	 - contracts/tokens/ERC1155Minimal.sol

[117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L117)
[168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L168)
[227](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L227)

---

	 - contracts/types/LeftRight.sol

[163](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L163)
[186](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L186)
[204](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L204)
[222](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L222)
[240](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L240)
[262](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L262)

---

	 - contracts/types/TokenId.sol

[567](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L567)
[598](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L598)


</details>

-------
### [L-02] Subtraction may underflow if multiplication is too large
<a name="L-02"></a>
[To the top](#TOP)

The following expressions may underflow, as the subtrahend could be greater than the minuend in case the former is multiplied by a large number.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 13 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
1952	                                                (int256(
1953	                                                    grossPremiumLast.leftSlot() *
1954	                                                        totalLiquidityBefore
1955	                                                ) -
1956	                                                    int256(
1957	                                                        _premiumAccumulatorsByLeg[_leg][1] *
1958	                                                            positionLiquidity
1959	                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
...
1952	                                                (int256(
1953	                                                    grossPremiumLast.leftSlot() *
1954	                                                        totalLiquidityBefore
1955	                                                ) -
1956	                                                    int256(
1957	                                                        _premiumAccumulatorsByLeg[_leg][1] *
1958	                                                            positionLiquidity
1959	                                                    )) + int256(legPremia.leftSlot()) * 2 ** 64,
...
1935	                                                (int256(
1936	                                                    grossPremiumLast.rightSlot() *
1937	                                                        totalLiquidityBefore
1938	                                                ) -
1939	                                                    int256(
1940	                                                        _premiumAccumulatorsByLeg[_leg][0] *
1941	                                                            positionLiquidity
1942	                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
...
1935	                                                (int256(
1936	                                                    grossPremiumLast.rightSlot() *
1937	                                                        totalLiquidityBefore
1938	                                                ) -
1939	                                                    int256(
1940	                                                        _premiumAccumulatorsByLeg[_leg][0] *
1941	                                                            positionLiquidity
1942	                                                    )) + int256(legPremia.rightSlot() * 2 ** 64),
```
[1952..1959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1952-L1959)
[1952..1959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1952-L1959)
[1935..1942](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1935-L1942)
[1935..1942](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1935-L1942)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
1388	                    uint256 numerator = totalLiquidity ** 2 -
1389	                        totalLiquidity *
1390	                        removedLiquidity +
```
[1388..1390](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1388-L1390)

---

	 - contracts/libraries/Math.sol

```solidity
418	            inv *= 2 - denominator * inv; // inverse mod 2**8
...
419	            inv *= 2 - denominator * inv; // inverse mod 2**16
...
420	            inv *= 2 - denominator * inv; // inverse mod 2**32
...
421	            inv *= 2 - denominator * inv; // inverse mod 2**64
...
422	            inv *= 2 - denominator * inv; // inverse mod 2**128
```
[418](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L418)
[419](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L419)
[420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L420)
[421](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L421)
[422](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L422)
[423](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L423)

---

	 - contracts/libraries/PanopticMath.sol

[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140)
[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140)


</details>

-------
### [L-03] Functions calling contracts/addresses with transfer hooks are missing reentrancy guards
<a name="L-03"></a>
[To the top](#TOP)

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks will open the users of this protocol up to [read-only reentrancies](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect against it, except by block-listing the whole protocol.`

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 12 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
323	    function transfer(
324	        address recipient,
325	        uint256 amount
326	    ) public override(ERC20Minimal) returns (bool) {
...
// @audit Function `transfer` doesn't  have the `nonReentrant` modifier
333	        return ERC20Minimal.transfer(recipient, amount);
...
341	    function transferFrom(
342	        address from,
343	        address to,
344	        uint256 amount
345	    ) public override(ERC20Minimal) returns (bool) {
...
// @audit Function `transferFrom` doesn't  have the `nonReentrant` modifier
352	        return ERC20Minimal.transferFrom(from, to, amount);
...
417	    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
...
// @audit Function `deposit` doesn't  have the `nonReentrant` modifier
424	        SafeTransferLib.safeTransferFrom(
...
477	    function mint(uint256 shares, address receiver) external returns (uint256 assets) {
...
// @audit Function `mint` doesn't  have the `nonReentrant` modifier
484	        SafeTransferLib.safeTransferFrom(
...
531	    function withdraw(
532	        uint256 assets,
533	        address receiver,
534	        address owner
535	    ) external returns (uint256 shares) {
...
// @audit Function `withdraw` doesn't  have the `nonReentrant` modifier
556	        SafeTransferLib.safeTransferFrom(
```
[333](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L333)
[352](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L352)
[424](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L424)
[484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L484)
[556](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L556)
[616](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L616)

---

	 - contracts/PanopticFactory.sol

[182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L182)
[189](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L189)

---

	 - contracts/SemiFungiblePositionManager.sol

[413](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L413)
[420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L420)
[456](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L456)
[555](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L555)


</details>

-------
### [L-04] Use of `abi.encodePacked` with dynamic types inside `keccak256`
<a name="L-04"></a>
[To the top](#TOP)

`abi.encodePacked` should not be used with dynamic types when passing the result to a hash function such as `keccak256`. Use `abi.encode` instead, which will pad items to 32 bytes, to [prevent any hash collisions](https://docs.soliditylang.org/en/latest/abi-spec.html#non-standard-packed-mode).

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 12 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
461	                    bytes32 chunkKey = keccak256(
462	                        abi.encodePacked(
463	                            tokenId.strike(leg),
464	                            tokenId.width(leg),
465	                            tokenId.tokenType(leg)
466	                        )
467	                    );
...
1642	            bytes32 chunkKey = keccak256(
1643	                abi.encodePacked(
1644	                    tokenId.strike(legIndex),
1645	                    tokenId.width(legIndex),
1646	                    tokenId.tokenType(legIndex)
1647	                )
1648	            );
...
1673	            bytes32 chunkKey = keccak256(
1674	                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1675	            );
...
1855	            bytes32 chunkKey = keccak256(
1856	                abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1857	            );
```
[461..467](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L461-L467)
[1642..1648](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1642-L1648)
[1673..1675](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1673-L1675)
[1855..1857](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1855-L1857)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
611	            bytes32 positionKey_from = keccak256(
612	                abi.encodePacked(
613	                    address(univ3pool),
614	                    from,
615	                    id.tokenType(leg),
616	                    liquidityChunk.tickLower(),
617	                    liquidityChunk.tickUpper()
618	                )
619	            );
...
620	            bytes32 positionKey_to = keccak256(
621	                abi.encodePacked(
622	                    address(univ3pool),
623	                    to,
624	                    id.tokenType(leg),
625	                    liquidityChunk.tickLower(),
626	                    liquidityChunk.tickUpper()
627	                )
628	            );
...
974	        bytes32 positionKey = keccak256(
975	            abi.encodePacked(
976	                address(univ3pool),
977	                msg.sender,
978	                tokenType,
979	                liquidityChunk.tickLower(),
980	                liquidityChunk.tickUpper()
981	            )
982	        );
...
1150	                keccak256(
1151	                    abi.encodePacked(
1152	                        address(this),
1153	                        liquidityChunk.tickLower(),
1154	                        liquidityChunk.tickUpper()
1155	                    )
1156	                )
...
1431	            keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))
...
1458	        bytes32 positionKey = keccak256(
1459	            abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)
1460	        );
```
[611..619](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L611-L619)
[620..628](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L620-L628)
[974..982](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L974-L982)
[1150..1156](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1150-L1156)
[1431](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1431)
[1458..1460](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1458-L1460)
[1544](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1544)

---

	 - contracts/libraries/PanopticMath.sol

[878..884](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L878-L884)


</details>

-------
### [L-05] Privileged functions can create points of failure
<a name="L-05"></a>
[To the top](#TOP)

Ensure such accounts are protected and consider implementing multi sig to prevent a single point of failure

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 10 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
// @audit Modifiers that checks `msg.sender`: `onlyOwner`, `onlyPanopticPool`, `onlyRole`
864	    function delegate(
865	        address delegator,
866	        address delegatee,
867	        uint256 assets
868	    ) external onlyPanopticPool {
...
// @audit Modifiers that checks `msg.sender`: `onlyOwner`, `onlyPanopticPool`, `onlyRole`
894	    function delegate(address delegatee, uint256 assets) external onlyPanopticPool {
...
// @audit Modifiers that checks `msg.sender`: `onlyOwner`, `onlyPanopticPool`, `onlyRole`
903	    function refund(address delegatee, uint256 assets) external onlyPanopticPool {
...
// @audit Modifiers that checks `msg.sender`: `onlyOwner`, `onlyPanopticPool`, `onlyRole`
911	    function revoke(
912	        address delegator,
913	        address delegatee,
914	        uint256 assets
915	    ) external onlyPanopticPool {
...
// @audit Modifiers that checks `msg.sender`: `onlyOwner`, `onlyPanopticPool`, `onlyRole`
975	    function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {
...
// @audit Modifiers that checks `msg.sender`: `onlyOwner`, `onlyPanopticPool`, `onlyRole`
995	    function takeCommissionAddData(
996	        address optionOwner,
997	        int128 longAmount,
998	        int128 shortAmount,
999	        int128 swappedAmount
1000	    ) external onlyPanopticPool returns (int256 utilization) {
...
// @audit Modifiers that checks `msg.sender`: `onlyOwner`, `onlyPanopticPool`, `onlyRole`
1043	    function exercise(
1044	        address optionOwner,
1045	        int128 longAmount,
1046	        int128 shortAmount,
1047	        int128 swappedAmount,
1048	        int128 realizedPremium
1049	    ) external onlyPanopticPool returns (int128) {
...
// @audit `msg.sender` is checked in function body
169	    modifier onlyPanopticPool() {
...
// @note `msg.sender` is checked here
170	        if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();
```
[864..868](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L864-L868)
[894](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L894)
[903](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L903)
[911..915](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L911-L915)
[975](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L975)
[995..1000](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L995-L1000)
[1043..1049](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1043-L1049)
[169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L169)

---

	 - contracts/PanopticFactory.sol

```solidity
// @audit `msg.sender` is checked in function body
147	    function transferOwnership(address newOwner) external {
```
[147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147)
[210..215](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210-L215)


</details>

-------
### [L-06] Must approve or increase allowance first
<a name="L-06"></a>
[To the top](#TOP)

In the context of ERC20 tokens, a token holder needs to "approve" another account to transfer a certain amount of their tokens on their behalf. This is accomplished by calling the `approve()` function, which takes the address of the spender and the amount they're allowed to spend as parameters. 

This approval step is a crucial part of the ERC20 standard because it allows for secure delegated transfers. A common use case for this feature is in decentralized exchanges or DeFi protocols, where a user can approve a smart contract to transfer tokens on their behalf. 

After the approval step, the approved account (or contract) can then transfer tokens up to the approved amount from the token holder's account by calling the `transferFrom()` function. This function takes three parameters: the address of the token holder, the recipient's address, and the amount to transfer.

If an account tries to call `transferFrom()` before the token holder has called `approve()`, the transaction will fail because the ERC20 contract checks whether the `transferFrom()` caller has an adequate allowance. 

In summary, if a contract or user needs to move ERC20 tokens on behalf of another account, it's necessary to ensure that the token holder has first called `approve()` to set a sufficient allowance. This is a key aspect of ERC20 token security and functionality. 

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 9 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
 // @audit function call transfer from, but not approve
417	    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
...
424	        SafeTransferLib.safeTransferFrom(
...
 // @audit function call transfer from, but not approve
477	    function mint(uint256 shares, address receiver) external returns (uint256 assets) {
...
484	        SafeTransferLib.safeTransferFrom(
...
 // @audit function call transfer from, but not approve
531	    function withdraw(
532	        uint256 assets,
533	        address receiver,
534	        address owner
535	    ) external returns (uint256 shares) {
...
556	        SafeTransferLib.safeTransferFrom(
...
 // @audit function call transfer from, but not approve
591	    function redeem(
592	        uint256 shares,
593	        address receiver,
594	        address owner
595	    ) external returns (uint256 assets) {
...
616	        SafeTransferLib.safeTransferFrom(
```
[424](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L424)
[484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L484)
[556](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L556)
[616](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L616)

---

	 - contracts/PanopticFactory.sol

```solidity
 // @audit function call transfer from, but not approve
172	    function uniswapV3MintCallback(
173	        uint256 amount0Owed,
174	        uint256 amount1Owed,
175	        bytes calldata data
176	    ) external {
...
182	            SafeTransferLib.safeTransferFrom(
```
[182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L182)
[189](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L189)

---

	 - contracts/SemiFungiblePositionManager.sol

[413](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L413)
[420](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L420)
[456](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L456)


</details>

-------
### [L-07] Consider bounding input array length
<a name="L-07"></a>
[To the top](#TOP)

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to `require()` that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 8 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
// @audit array parameter `positionIdList` is used as loop condition and length is not cheched in function
799	        TokenId[] calldata positionIdList
...
// @audit loop uses unbounded parameter
802	        for (uint256 i = 0; i < positionIdList.length; ) {
```
[802](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L802)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
// @audit array parameter `ids` is used as loop condition and length is not cheched in function
569	        uint256[] calldata ids,
...
// @audit loop uses unbounded parameter
575	        for (uint256 i = 0; i < ids.length; ) {
```
[575](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L575)

---

	 - contracts/libraries/FeesCalc.sol

```solidity
// @audit array parameter `positionIdList` is used as loop condition and length is not cheched in function
49	        TokenId[] calldata positionIdList
...
// @audit loop uses unbounded parameter
51	        for (uint256 k = 0; k < positionIdList.length; ) {
```
[51](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L51)

---

	 - contracts/libraries/PanopticMath.sol

```solidity
// @audit array parameter `positionIdList` is used as loop condition and length is not cheched in function
770	        TokenId[] memory positionIdList,
...
// @audit loop uses unbounded parameter
781	            for (uint256 i = 0; i < positionIdList.length; ++i) {
...
// @audit array parameter `positionIdList` is used as loop condition and length is not cheched in function
770	        TokenId[] memory positionIdList,
...
// @audit loop uses unbounded parameter
860	            for (uint256 i = 0; i < positionIdList.length; i++) {
```
[781](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L781)
[860](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L860)

---

	 - contracts/multicall/Multicall.sol

[14](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L14)

---

	 - contracts/tokens/ERC1155Minimal.sol

[143](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L143)

---

	 - contracts/tokens/ERC1155Minimal.sol

[187](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L187)


</details>

-------
### [L-08] Array lengths not checked
<a name="L-08"></a>
[To the top](#TOP)

If the length of the arrays are not required to be of the same length, user operations may not be fully executed due to a mismatch in the number of items iterated over, versus the number of items provided in the second array

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 7 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
586	    function burnOptions(
587	        TokenId[] calldata positionIdList,
588	        TokenId[] calldata newPositionIdList,
589	        int24 tickLimitLow,
590	        int24 tickLimitHigh
591	    ) external {
...
1017	    function liquidate(
1018	        TokenId[] calldata positionIdListLiquidator,
1019	        address liquidatee,
1020	        LeftRightUnsigned delegations,
1021	        TokenId[] calldata positionIdList
1022	    ) external {
...
1179	    function forceExercise(
1180	        address account,
1181	        TokenId[] calldata touchedId,
1182	        TokenId[] calldata positionIdListExercisee,
1183	        TokenId[] calldata positionIdListExercisor
1184	    ) external {
```
[586..591](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L586-L591)
[1017..1022](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017-L1022)
[1179..1184](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1179-L1184)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
566	    function safeBatchTransferFrom(
567	        address from,
568	        address to,
569	        uint256[] calldata ids,
570	        uint256[] calldata amounts,
571	        bytes calldata data
572	    ) public override {
```
[566..572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566-L572)

---

	 - contracts/libraries/PanopticMath.sol

```solidity
768	    function haircutPremia(
769	        address liquidatee,
770	        TokenId[] memory positionIdList,
771	        LeftRightSigned[4][] memory premiasByLeg,
772	        LeftRightSigned collateralRemaining,
773	        CollateralTracker collateral0,
774	        CollateralTracker collateral1,
775	        uint160 sqrtPriceX96Final,
776	        mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777	    ) external returns (int256, int256) {
```
[768..777](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L768-L777)

---

	 - contracts/tokens/ERC1155Minimal.sol

```solidity
130	    function safeBatchTransferFrom(
131	        address from,
132	        address to,
133	        uint256[] calldata ids,
134	        uint256[] calldata amounts,
135	        bytes calldata data
136	    ) public virtual {
...
178	    function balanceOfBatch(
179	        address[] calldata owners,
180	        uint256[] calldata ids
181	    ) public view returns (uint256[] memory balances) {
```
[130..136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L130-L136)
[178..181](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L178-L181)


</details>

-------
### [L-09] Contract contains payable multicall
<a name="L-09"></a>
[To the top](#TOP)

Incorporating multiple delegate calls or ordinary calls in a single payable function can pose significant security risks, especially concerning the potential drainage of funds. Each call in a function can potentially make use of `msg.value` (the amount of Ether sent with the function call), and if there's no explicit control over the division of `msg.value` across these calls, a user could intentionally or inadvertently trigger a condition where funds are drained from the contract in unexpected ways.

To mitigate these risks, it's crucial to implement rigorous checks and explicit control mechanisms over how `msg.value` is used. This may involve ensuring that `msg.value` is divided as intended across multiple calls or including checks to prevent recursive or reentrant calls. Additionally, using a 'pull over push' payment design can also provide added security, wherein instead of the contract sending out payments, recipients request withdrawals. This method can limit the amount of Ether that leaves the contract during a single function call and provide better control over funds.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 1 instances</summary>


---

	 - contracts/multicall/Multicall.sol

```solidity
12	    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
13	        results = new bytes[](data.length);
14	        for (uint256 i = 0; i < data.length; ) {
15	            (bool success, bytes memory result) = address(this).delegatecall(data[i]);
16	
17	            if (!success) {
18	                // Bubble up the revert reason
19	                // The bytes type is ABI encoded as a length-prefixed byte array
20	                // So we simply need to add 32 to the pointer to get the start of the data
21	                // And then revert with the size loaded from the first 32 bytes
22	                // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
23	                // However, we have chosen to simply replicate the the normal behavior of the call
24	                // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
25	                assembly ("memory-safe") {
26	                    revert(add(result, 32), mload(result))
27	                }
28	            }
29	
30	            results[i] = result;
31	
32	            unchecked {
33	                ++i;
34	            }
35	        }
36	    }
```
[12..36](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L12-L36)


</details>

-------
### [L-10] External call recipient may consume all transaction gas
<a name="L-10"></a>
[To the top](#TOP)

There is no limit specified on the amount of gas used, so the recipient can use up all of the transaction's gas, causing it to revert. Use `addr.call{gas: <amount>}("")` or [this](https://github.com/nomad-xyz/ExcessivelySafeCall) library instead

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 1 instances</summary>


---

	 - contracts/multicall/Multicall.sol

```solidity
15	            (bool success, bytes memory result) = address(this).delegatecall(data[i]);
```
[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L15)


</details>


## NonCritical Risk Issues

### [N-01] Complex math should be split into multiple steps
<a name="N-01"></a>
[To the top](#TOP)

Consider splitting long arithmetic calculations into multiple steps to improve the code readability.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 114 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
202	                2230 +
203	                    (12500 * ratioTick) /
204	                    10_000 +
205	                    (7812 * ratioTick ** 2) /
206	                    10_000 ** 2 +
207	                    (6510 * ratioTick ** 3) /
208	                    10_000 ** 3
...
202	                2230 +
203	                    (12500 * ratioTick) /
204	                    10_000 +
205	                    (7812 * ratioTick ** 2) /
206	                    10_000 ** 2 +
...
202	                2230 +
203	                    (12500 * ratioTick) /
204	                    10_000 +
...
205	                    (7812 * ratioTick ** 2) /
206	                    10_000 ** 2 +
...
207	                    (6510 * ratioTick ** 3) /
208	                    10_000 ** 3
...
796	                min_sell_ratio +
797	                ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798	                (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);
...
797	                ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798	                (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);
...
849	                (BUYER_COLLATERAL_RATIO +
850	                    (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851	                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2
...
849	                (BUYER_COLLATERAL_RATIO +
850	                    (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851	                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2
...
849	                (BUYER_COLLATERAL_RATIO +
850	                    (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851	                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2
```
[202..208](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L202-L208)
[202..206](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L202-L206)
[202..204](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L202-L204)
[205..206](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L205-L206)
[207..208](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L207-L208)
[796..798](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L796-L798)
[797..798](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L797-L798)
[849..851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L849-L851)
[849..851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L849-L851)
[849..851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L849-L851)
[850..851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L850-L851)

---

	 - contracts/PanopticPool.sol

[309..314](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L309-L314)
[309..313](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L309-L313)
[1487](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1487)
[1559..1561](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1559-L1561)
[1550..1552](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1550-L1552)
[1737..1740](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1737-L1740)
[1729..1732](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1729-L1732)
[1768..1769](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1768-L1769)
[1770..1771](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1770-L1771)
[1952..1959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1952-L1959)

---

	 - contracts/SemiFungiblePositionManager.sol

[1367](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1367)
[1388..1391](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1388-L1391)

---

	 - contracts/libraries/Math.sol

[758](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L758)

---

	 - contracts/libraries/PanopticMath.sol

[108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L108)
[108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L108)
[108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L108)
[107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L107)
[107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L107)
[107](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L107)
[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178)
[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178)
[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179)
[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179)
[209](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L209)
[223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223)
[223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223)
[223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223)
[223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223)
[223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L223)
[227..230](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L227-L230)
[227..229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L227-L229)
[249](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L249)

---

	 - contracts/types/LiquidityChunk.sol

[78..80](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L78-L80)

---

	 - contracts/types/TokenId.sol

[110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L110)
[110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L110)
[110](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L110)
[120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120)
[120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120)
[120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120)
[120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120)
[120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L120)
[130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130)
[130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130)
[130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130)
[130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130)
[130](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L130)
[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140)
[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140)
[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140)
[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140)
[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L140)
[150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150)
[150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150)
[150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150)
[150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150)
[150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L150)
[160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L160)
[160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L160)
[160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L160)
[171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171)
[171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171)
[171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171)
[171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171)
[171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171)
[212](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L212)
[212](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L212)
[212](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L212)
[229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L229)
[229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L229)
[229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L229)
[229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L229)
[229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L229)
[246](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L246)
[246](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L246)
[246](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L246)
[246](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L246)
[246](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L246)
[263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L263)
[263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L263)
[263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L263)
[263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L263)
[263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L263)
[281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L281)
[281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L281)
[281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L281)
[281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L281)
[281](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L281)
[300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L300)
[300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L300)
[300](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L300)
[319..320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L319-L320)
[320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L320)
[320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L320)
[320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L320)
[320](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L320)
[394..395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L394-L395)
[395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L395)
[395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L395)
[395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L395)
[395](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L395)
[406](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L406)
[512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L512)
[512](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L512)


</details>

-------
### [N-02] Variable names don't follow the Solidity naming convention
<a name="N-02"></a>
[To the top](#TOP)

Use `mixedCase` for local and state variables that are not constants, and add a trailing underscore for internal variables. [Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#local-and-state-variable-names)

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 92 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
89	    address internal s_underlyingToken;
...
93	    bool internal s_initialized;
...
96	    address internal s_univ3token0;
...
99	    address internal s_univ3token1;
...
102	    bool internal s_underlyingIsToken0;
...
109	    PanopticPool internal s_panopticPool;
...
112	    uint128 internal s_poolAssets;
...
115	    uint128 internal s_inAMM;
...
121	    uint128 internal s_ITMSpreadFee;
...
124	    uint24 internal s_poolFee;
```
[89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L89)
[93](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L93)
[96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L96)
[99](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L99)
[102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L102)
[109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L109)
[112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L112)
[115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L115)
[121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L121)
[124](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L124)
[131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L131)
[136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L136)
[141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L141)
[145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L145)
[149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L149)
[154](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L154)
[158](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L158)
[162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L162)
[247](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L247)
[773](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L773)
[1219](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1219)

---

	 - contracts/PanopticFactory.sol

[63](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L63)
[66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L66)
[69](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L69)
[72](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L72)
[75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L75)
[78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L78)
[96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L96)
[99](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L99)
[102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L102)
[223](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L223)

---

	 - contracts/PanopticPool.sol

[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L179)
[186](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L186)
[225](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L225)
[231](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L231)
[233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L233)
[238..239](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L238-L239)
[245](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L245)
[251](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L251)
[258..259](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L258-L259)
[272](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L272)
[439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L439)
[895](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L895)
[1117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1117)
[1118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1118)
[1119](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1119)
[1139](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1139)
[1923](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1923)
[1924](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1924)

---

	 - contracts/SemiFungiblePositionManager.sol

[137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L137)
[145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L145)
[150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L150)
[177..178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L177-L178)
[287](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L287)
[289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L289)
[295](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L295)
[611](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L611)
[620](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L620)
[765](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L765)
[883](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L883)
[884](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L884)
[885](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L885)
[889](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L889)
[890](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L890)
[891](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L891)
[892](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L892)
[893](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L893)
[1342](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1342)
[1343](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1343)
[1363](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1363)
[1364](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1364)
[1384](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1384)
[1385](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1385)
[1472](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1472)
[1473](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1473)
[1474](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1474)

---

	 - contracts/libraries/PanopticMath.sol

[186](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L186)
[186](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L186)
[192](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L192)
[192](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L192)
[855](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L855)
[862](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L862)
[865..866](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L865-L866)

---

	 - contracts/types/LeftRight.sol

[285](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L285)
[286](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L286)
[287](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L287)
[288](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L288)
[290](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L290)
[291](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L291)

---

	 - contracts/types/TokenId.sol

[551](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L551)
[555](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L555)
[587](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L587)


</details>

-------
### [N-03] Duplicated `require/if` statements should be refactored
<a name="N-03"></a>
[To the top](#TOP)

These statements should be refactored to a separate function, as there are multiple parts of the codebase that use the same logic, to improve the code readability and reduce code duplication.



#### <ins>Proof Of Concept</ins>

<details>

<summary>see 87 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
331	        if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();
...
350	        if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();
...
418	        if (assets > type(uint104).max) revert Errors.DepositTooLarge();
...
480	        if (assets > type(uint104).max) revert Errors.DepositTooLarge();
...
541	        if (msg.sender != owner) {
...
544	            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
...
599	        if (msg.sender != owner) {
...
602	            if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
...
708	                    (tokenType == 0 && currentValue1 < oracleValue1) ||
709	                    (tokenType == 1 && currentValue0 < oracleValue0)
...
1010	            if (tokenToPay > 0) {
```
[331](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L331)
[350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L350)
[418](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L418)
[480](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L480)
[541](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L541)
[544](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L544)
[599](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L599)
[602](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L602)
[708..709](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L708-L709)
[1010](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1010)
[1018](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1018)
[1067](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1067)
[1075](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1075)
[1339](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1339)
[1346..1347](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1346-L1347)
[1374..1375](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1374-L1375)
[1451](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1451)
[1479](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1479)
[1488](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1488)

---

	 - contracts/PanopticPool.sol

[533](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L533)
[664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L664)
[768](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L768)
[865](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L865)
[944](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L944)
[1156..1162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1156-L1162)
[1566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1566)
[1679](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1679)

---

	 - contracts/SemiFungiblePositionManager.sol

[549](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L549)
[576](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L576)
[632..633](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L632-L633)
[691](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L691)
[727](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L727)
[1006](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1006)

---

	 - contracts/libraries/Math.sol

[297](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L297)
[303](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L303)
[360](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L360)
[447](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L447)
[448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448)
[474](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L474)
[537](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L537)
[587](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L587)
[588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588)
[614](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L614)
[664](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L664)
[665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665)
[691](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L691)

---

	 - contracts/libraries/PanopticMath.sol

[325](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L325)
[494](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L494)
[511](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L511)
[528](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L528)
[551](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L551)
[584](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L584)
[619](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L619)
[627](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L627)
[706](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L706)
[724](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L724)
[785](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L785)
[864](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L864)
[931](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L931)
[949](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L949)

---

	 - contracts/libraries/SafeTransferLib.sol

[45](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L45)
[75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L75)

---

	 - contracts/tokens/ERC1155Minimal.sol

[101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L101)
[112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L112)
[114..115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L114-L115)
[137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L137)
[163](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L163)
[222](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L222)
[224..225](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L224-L225)

---

	 - contracts/types/LeftRight.sol

[222](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L222)
[240](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L240)
[262](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L262)

---

	 - contracts/types/TokenId.sol

[376](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L376)
[378](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L378)
[380](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L380)
[382](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L382)
[439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L439)
[441](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L441)
[443](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L443)
[445](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L445)
[501](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L501)
[508](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L508)
[531..532](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L531-L532)
[546..547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L546-L547)
[560](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L560)
[566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L566)
[589](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L589)


</details>

-------
### [N-04] Overflows in unchecked blocks
<a name="N-04"></a>
[To the top](#TOP)

While integers with a large number of bits are unlikely to overflow on human time scales, it is not strictly correct to use an `unchecked` block around them, because _eventually_ they will overflow, and `unchecked` blocks are meant for cases where it's mathematically impossible for an operation to trigger an overflow (e.g. a prior `require()` statement prevents the overflow case)

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 82 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
197	        unchecked {
198	            // taylor expand log(1-sellCollateralRatio)/log(1.0001) around sellCollateralRatio=2000 up to 3rd order
199	            /// since we're dropping the higher order terms, which are all negative, this will underestimate the number of ticks for a 20% move
200	            int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);
201	            TICK_DEVIATION = uint256(
202	                2230 +
203	                    (12500 * ratioTick) /
204	                    10_000 +
205	                    (7812 * ratioTick ** 2) /
206	                    10_000 ** 2 +
207	                    (6510 * ratioTick ** 3) /
208	                    10_000 ** 3
209	            );
210	        }
...
261	        unchecked {
262	            s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);
263	        }
...
401	        unchecked {
402	            shares = Math.mulDiv(
403	                assets * (DECIMALS - COMMISSION_FEE),
404	                totalSupply,
405	                totalAssets() * DECIMALS
406	            );
407	        }
...
445	        unchecked {
446	            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
447	        }
...
461	        unchecked {
462	            assets = Math.mulDivRoundingUp(
463	                shares * DECIMALS,
464	                totalAssets(),
465	                totalSupply * (DECIMALS - COMMISSION_FEE)
466	            );
467	        }
...
661	        unchecked {
662	            for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {
663	                // short legs are not counted - exercise is intended to be based on long legs
664	                if (positionId.isLong(leg) == 0) continue;
665	
666	                {
667	                    int24 range = int24(
668	                        int256(
669	                            Math.unsafeDivRoundingUp(
670	                                uint24(positionId.width(leg) * positionId.tickSpacing()),
671	                                2
672	                            )
673	                        )
674	                    );
675	                    maxNumRangesFromStrike = Math.max(
676	                        maxNumRangesFromStrike,
677	                        uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
678	                    );
679	                }
680	
681	                uint256 currentValue0;
682	                uint256 currentValue1;
683	                uint256 oracleValue0;
684	                uint256 oracleValue1;
685	
686	                {
687	                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
688	                        positionId,
689	                        leg,
690	                        positionBalance
691	                    );
692	
693	                    (currentValue0, currentValue1) = Math.getAmountsForLiquidity(
694	                        currentTick,
695	                        liquidityChunk
696	                    );
697	
698	                    (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(
699	                        oracleTick,
700	                        liquidityChunk
701	                    );
702	                }
703	
704	                uint256 tokenType = positionId.tokenType(leg);
705	                // compensate user for loss in value if chunk has lost money between current and median tick
706	                // note: the delta for one token will be positive and the other will be negative. This cancels out any moves in their positions
707	                if (
708	                    (tokenType == 0 && currentValue1 < oracleValue1) ||
709	                    (tokenType == 1 && currentValue0 < oracleValue0)
710	                )
711	                    exerciseFees = exerciseFees.sub(
712	                        LeftRightSigned
713	                            .wrap(0)
714	                            .toRightSlot(
715	                                int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
716	                            )
717	                            .toLeftSlot(
718	                                int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
719	                            )
720	                    );
721	            }
722	
723	            // note: we HAVE to start with a negative number as the base exercise cost because when shifting a negative number right by n bits,
724	            // the result is rounded DOWN and NOT toward zero
725	            // this divergence is observed when n (the number of half ranges) is > 10 (ensuring the floor is not zero, but -1 = 1bps at that point)
726	            // subtract 1 from max half ranges from strike so fee starts at FORCE_EXERCISE_COST when moving OTM
727	            int256 fee = (FORCE_EXERCISE_COST >> (maxNumRangesFromStrike - 1)); // exponential decay of fee based on number of half ranges away from the price
728	
729	            // store the exercise fees in the exerciseFees variable
730	            exerciseFees = exerciseFees
731	                .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))
732	                .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));
733	        }
...
742	        unchecked {
743	            return int256((s_inAMM * DECIMALS) / totalAssets());
744	        }
...
794	        unchecked {
795	            return
796	                min_sell_ratio +
797	                ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798	                (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);
799	        }
...
847	        unchecked {
848	            return
849	                (BUYER_COLLATERAL_RATIO +
850	                    (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851	                    (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2
852	        }
...
1103	        unchecked {
1104	            // intrinsic value is the amount that need to be exchanged due to minting in-the-money
1105	            int256 intrinsicValue = swappedAmount - (shortAmount - longAmount);
1106	
1107	            if (intrinsicValue != 0) {
1108	                // the swap commission is paid on the intrinsic value, and it is always positive
1109	                uint256 swapCommission = Math.unsafeDivRoundingUp(
1110	                    s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),
1111	                    DECIMALS
1112	                );
1113	
1114	                // set the exchanged amount to the sum of the intrinsic value and swapCommission
1115	                exchangedAmount = intrinsicValue + int256(swapCommission);
1116	            }
1117	
1118	            //compute total commission amount = commission rate + spread fee
1119	            exchangedAmount += int256(
1120	                Math.unsafeDivRoundingUp(
1121	                    uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
1122	                    DECIMALS
1123	                )
1124	            );
1125	        }
```
[197..210](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L197-L210)
[261..263](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L261-L263)
[401..407](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L401-L407)
[445..447](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L445-L447)
[461..467](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L461-L467)
[661..733](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L661-L733)
[742..744](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L742-L744)
[794..799](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L794-L799)
[847..852](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L847-L852)
[1103..1125](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1103-L1125)
[1230..1232](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1230-L1232)
[1254..1267](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1254-L1267)
[1338..1421](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1338-L1421)
[1495..1497](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1495-L1497)
[1485..1487](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1485-L1487)
[1555..1573](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1555-L1573)

---

	 - contracts/PanopticFactory.sol

[390..394](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L390-L394)

---

	 - contracts/PanopticPool.sol

[482..484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L482-L484)
[487..489](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L487-L489)
[778..780](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L778-L780)
[812..814](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L812-L814)
[871..873](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L871-L873)
[1328..1330](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1328-L1330)
[1344..1355](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1344-L1355)
[1388..1390](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1388-L1390)
[1486..1488](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1486-L1488)
[1539..1569](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1539-L1569)
[1571..1573](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1571-L1573)
[1631..1655](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1631-L1655)
[1717..1743](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1717-L1743)
[1764..1795](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1764-L1795)
[1922..1969](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1922-L1969)
[1976..1978](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1976-L1978)

---

	 - contracts/SemiFungiblePositionManager.sol

[387..389](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L387-L389)
[578..580](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L578-L580)
[649..651](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L649-L651)
[931..933](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L931-L933)
[1339..1406](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1339-L1406)

---

	 - contracts/libraries/FeesCalc.sol

[79..81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L79-L81)
[83..85](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L83-L85)

---

	 - contracts/libraries/Math.sol

[129..180](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L129-L180)
[345..432](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L345-L432)
[445..451](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L445-L451)
[459..514](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L459-L514)
[522..577](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L522-L577)
[585..591](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L585-L591)
[599..654](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L599-L654)
[662..668](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L662-L668)
[676..731](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L676-L731)
[754..770](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L754-L770)

---

	 - contracts/libraries/PanopticMath.sol

[132..156](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L132-L156)
[175..232](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L175-L232)
[246..267](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L246-L267)
[343..362](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L343-L362)
[406..408](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L406-L408)
[491..499](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L491-L499)
[508..516](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L508-L516)
[525..539](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L525-L539)
[548..566](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L548-L566)
[659..753](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L659-L753)
[778..907](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L778-L907)

---

	 - contracts/multicall/Multicall.sol

[32..34](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L32-L34)

---

	 - contracts/tokens/ERC1155Minimal.sol

[156..158](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L156-L158)
[186..190](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L186-L190)

---

	 - contracts/types/TokenId.sol

[97..99](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L97-L99)
[109..111](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L109-L111)
[119..121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L119-L121)
[129..131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L129-L131)
[139..141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L139-L141)
[149..151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L149-L151)
[159..161](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L159-L161)
[170..172](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L170-L172)
[210..213](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L210-L213)
[226..231](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L226-L231)
[245..247](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L245-L247)
[260..265](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L260-L265)
[278..283](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L278-L283)
[296..302](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L296-L302)
[316..322](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L316-L322)
[367..397](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L367-L397)
[504..570](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L504-L570)
[579..595](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L579-L595)


</details>

-------
### [N-05] Unsafe `uint` to `int` conversion
<a name="N-05"></a>
[To the top](#TOP)

The `int` type in Solidity uses the [two's complement system](https://en.wikipedia.org/wiki/Two%27s_complement), so it is possible to accidentally overflow a very large `uint` to an `int`, even if they share the same number of bytes (e.g. a `uint256 number > type(uint128).max` will overflow a `int256` cast).

Consider using the [SafeCast](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SafeCast.sol) library to prevent any overflows.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 79 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
200	            int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);
...
668	                        int256(
669	                            Math.unsafeDivRoundingUp(
670	                                uint24(positionId.width(leg) * positionId.tickSpacing()),
671	                                2
672	                            )
673	                        )
...
718	                                int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
...
718	                                int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
...
715	                                int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
...
715	                                int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
...
743	            return int256((s_inAMM * DECIMALS) / totalAssets());
...
959	                    uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
...
959	                    uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
...
1003	            int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
```
[200](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L200)
[668..673](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L668-L673)
[718](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L718)
[718](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L718)
[715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L715)
[715](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L715)
[743](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L743)
[959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L959)
[959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L959)
[1003](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1003)
[1029](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1029)
[1052](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1052)
[1085](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1085)
[1115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1115)
[1119..1124](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1119-L1124)
[1330](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1330)
[1329](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1329)
[1586](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1586)
[1585](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1585)
[1637](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1637)
[1638](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1638)

---

	 - contracts/PanopticPool.sol

[477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L477)
[1144](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1144)
[1149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1149)
[1558..1562](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1558-L1562)
[1549..1553](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1549-L1553)
[1636](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1636)
[1635](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1635)
[1901](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1901)
[1952..1955](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1952-L1955)
[1956..1959](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1956-L1959)
[1935..1938](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1935-L1938)
[1939..1942](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1939-L1942)
[1870](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1870)

---

	 - contracts/SemiFungiblePositionManager.sol

[1177](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1177)
[1176](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1176)
[1172](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1172)
[1169](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1169)
[1215](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1215)
[1214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1214)
[1242](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1242)
[1241](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1241)

---

	 - contracts/libraries/FeesCalc.sol

[74](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L74)
[75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L75)
[69](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L69)
[70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L70)
[118](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L118)
[117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L117)

---

	 - contracts/libraries/Math.sol

[312](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L312)
[327](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L327)
[778](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L778)

---

	 - contracts/libraries/PanopticMath.sol

[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140)
[140](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L140)
[141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L141)
[151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L151)
[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178)
[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179)
[188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L188)
[188](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L188)
[196](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L196)
[217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L217)
[258](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L258)
[377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L377)
[681](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L681)
[683..688](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L683-L688)
[693](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L693)
[695](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L695)
[929](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L929)
[938..940](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L938-L940)
[947](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L947)
[956..958](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L956-L958)

---

	 - contracts/types/LeftRight.sol

[27](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L27)
[196](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L196)
[201](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L201)

---

	 - contracts/types/LiquidityChunk.sol

[173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L173)
[182](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L182)

---

	 - contracts/types/TokenId.sol

[98](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L98)
[160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L160)
[171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L171)


</details>

-------
### [N-06] Use a single file for system wide constants
<a name="N-06"></a>
[To the top](#TOP)

Consider grouping all the system constants under a single file.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 49 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
70	    string internal constant TICKER_PREFIX = "po";
...
73	    string internal constant NAME_PREFIX = "POPT-V1";
...
77	    uint256 internal constant DECIMALS = 10_000;
...
81	    int128 internal constant DECIMALS_128 = 10_000;
```
[70](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L70)
[73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L73)
[77](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L77)
[81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L81)

---

	 - contracts/PanopticFactory.sol

```solidity
82	    uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_WETH = 0.1 ether;
...
86	    uint256 internal constant FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN = 1e6;
...
89	    uint16 internal constant CARDINALITY_INCREASE = 100;
```
[82](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L82)
[86](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L86)
[89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L89)

---

	 - contracts/PanopticPool.sol

```solidity
103	    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;
...
105	    int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;
...
109	    bool internal constant COMPUTE_ALL_PREMIA = true;
```
[103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L103)
[105](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L105)
[109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L109)
[111](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L111)
[114](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L114)
[119](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L119)
[120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L120)
[123](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L123)
[128](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L128)
[133](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L133)
[136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L136)
[139](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L139)
[145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L145)
[148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L148)
[152](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L152)
[156](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L156)
[160](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L160)
[165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L165)
[168](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L168)
[171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L171)
[174](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L174)

---

	 - contracts/SemiFungiblePositionManager.sol

[125](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L125)
[126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L126)
[133](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L133)

---

	 - contracts/libraries/Constants.sol

[9](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L9)
[12](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L12)
[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L15)
[18](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L18)
[21..22](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L21-L22)

---

	 - contracts/libraries/Math.sol

[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L15)

---

	 - contracts/libraries/PanopticMath.sol

[23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L23)
[26](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L26)

---

	 - contracts/types/LeftRight.sol

[22..23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L22-L23)
[26..27](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L26-L27)
[30](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L30)

---

	 - contracts/types/LiquidityChunk.sol

[54..55](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L54-L55)
[58..59](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L58-L59)

---

	 - contracts/types/TokenId.sol

[62..63](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L62-L63)
[66..67](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L66-L67)
[70..71](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L70-L71)
[74..75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L74-L75)
[78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L78)


</details>

-------
### [N-07] Private and internal state variables should have a preceding _ in their name unless they are constants
<a name="N-07"></a>
[To the top](#TOP)

Add a preceding underscore to the state variable name, take care to refactor where there variables are read/wrote

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 44 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
89	    address internal s_underlyingToken;
...
93	    bool internal s_initialized;
...
96	    address internal s_univ3token0;
...
99	    address internal s_univ3token1;
...
102	    bool internal s_underlyingIsToken0;
...
109	    PanopticPool internal s_panopticPool;
...
112	    uint128 internal s_poolAssets;
...
115	    uint128 internal s_inAMM;
...
121	    uint128 internal s_ITMSpreadFee;
...
124	    uint24 internal s_poolFee;
```
[89](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L89)
[93](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L93)
[96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L96)
[99](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L99)
[102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L102)
[109](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L109)
[112](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L112)
[115](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L115)
[121](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L121)
[124](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L124)
[131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L131)
[136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L136)
[141](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L141)
[145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L145)
[149](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L149)
[154](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L154)
[158](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L158)
[162](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L162)

---

	 - contracts/PanopticFactory.sol

[63](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L63)
[66](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L66)
[69](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L69)
[72](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L72)
[75](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L75)
[78](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L78)
[96](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L96)
[99](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L99)
[102](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L102)

---

	 - contracts/PanopticPool.sol

[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L179)
[186](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L186)
[225](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L225)
[231](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L231)
[233](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L233)
[238..239](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L238-L239)
[245](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L245)
[251](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L251)
[258..259](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L258-L259)
[272](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L272)

---

	 - contracts/SemiFungiblePositionManager.sol

[137](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L137)
[145](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L145)
[150](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L150)
[177..178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L177-L178)
[287](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L287)
[289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L289)
[295](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L295)


</details>

-------
### [N-08] Function names should differ to make the code more readable
<a name="N-08"></a>
[To the top](#TOP)

In Solidity, while function overriding allows for functions with the same name to coexist, it is advisable to avoid this practice to enhance code readability and maintainability. Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the likelihood of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function, but also helps prevent unintended function calls or incorrect overriding. By adopting a clear and consistent naming convention, developers can create more comprehensible and maintainable smart contracts.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 31 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
864	    function delegate(
865	        address delegator,
866	        address delegatee,
867	        uint256 assets
868	    ) external onlyPanopticPool {
...
894	    function delegate(address delegatee, uint256 assets) external onlyPanopticPool {
...
903	    function refund(address delegatee, uint256 assets) external onlyPanopticPool {
...
975	    function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {
```
[864..868](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L864-L868)
[894](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L894)
[903](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L903)
[975](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L975)

---

	 - contracts/PanopticPool.sol

```solidity
569	    function burnOptions(
570	        TokenId tokenId,
571	        TokenId[] calldata newPositionIdList,
572	        int24 tickLimitLow,
573	        int24 tickLimitHigh
574	    ) external {
...
586	    function burnOptions(
587	        TokenId[] calldata positionIdList,
588	        TokenId[] calldata newPositionIdList,
589	        int24 tickLimitLow,
590	        int24 tickLimitHigh
591	    ) external {
```
[569..574](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L569-L574)
[586..591](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L586-L591)

---

	 - contracts/libraries/Math.sol

```solidity
57	    function max(uint256 a, uint256 b) internal pure returns (uint256) {
...
65	    function max(int256 a, int256 b) internal pure returns (int256) {
...
41	    function min(uint256 a, uint256 b) internal pure returns (uint256) {
...
49	    function min(int256 a, int256 b) internal pure returns (int256) {
```
[57](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L57)
[65](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L65)
[41](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L41)
[49](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L49)
[311](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L311)
[318](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L318)

---

	 - contracts/libraries/PanopticMath.sol

[490](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L490)
[524](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L524)
[507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L507)
[547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L547)
[419..424](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L419-L424)
[445..450](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L445-L450)

---

	 - contracts/types/LeftRight.sol

[148..151](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L148-L151)
[194](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L194)
[214](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L214)
[101](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L101)
[108](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L108)
[39](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L39)
[46](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L46)
[171..174](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L171-L174)
[232](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L232)
[121..124](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L121-L124)
[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L134)
[59..62](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L59-L62)
[78..81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L78-L81)


</details>

-------
### [N-09] Floating pragma should be avoided
<a name="N-09"></a>
[To the top](#TOP)



#### <ins>Proof Of Concept</ins>

<details>

<summary>see 20 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
2	pragma solidity ^0.8.18;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L2)

---

	 - contracts/PanopticFactory.sol

```solidity
2	pragma solidity ^0.8.18;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L2)

---

	 - contracts/PanopticPool.sol

```solidity
2	pragma solidity ^0.8.18;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L2)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
2	pragma solidity ^0.8.18;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L2)

---

	 - contracts/libraries/CallbackLib.sol

```solidity
2	pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/CallbackLib.sol#L2)

---

	 - contracts/libraries/Constants.sol

```solidity
2	pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L2)

---

	 - contracts/libraries/Errors.sol

```solidity
2	pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L2)

---

	 - contracts/libraries/FeesCalc.sol

```solidity
2	pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L2)

---

	 - contracts/libraries/InteractionHelper.sol

```solidity
2	pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/InteractionHelper.sol#L2)

---

	 - contracts/libraries/Math.sol

```solidity
2	pragma solidity ^0.8.0;
```
[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L2)

---

	 - contracts/libraries/PanopticMath.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L2)

---

	 - contracts/libraries/SafeTransferLib.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L2)

---

	 - contracts/multicall/Multicall.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L2)

---

	 - contracts/tokens/ERC1155Minimal.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L2)

---

	 - contracts/tokens/ERC20Minimal.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L2)

---

	 - contracts/tokens/interfaces/IDonorNFT.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IDonorNFT.sol#L2)

---

	 - contracts/tokens/interfaces/IERC20Partial.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IERC20Partial.sol#L2)

---

	 - contracts/types/LeftRight.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L2)

---

	 - contracts/types/LiquidityChunk.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LiquidityChunk.sol#L2)

---

	 - contracts/types/TokenId.sol

[2](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L2)


</details>

-------
### [N-10] Unused contract variables
<a name="N-10"></a>
[To the top](#TOP)

Note that there may be cases where a variable appears to be used, but this is only because there are multiple definitions of the varible in different files. In such cases, the variable definition should be moved into a separate file. The instances below are the unused variables.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 18 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
361	    function asset() external view returns (address assetTokenAddress) {
...
370	    function totalAssets() public view returns (uint256 totalManagedAssets) {
...
379	    function convertToShares(uint256 assets) public view returns (uint256 shares) {
...
386	    function convertToAssets(uint256 shares) public view returns (uint256 assets) {
...
392	    function maxDeposit(address) external pure returns (uint256 maxAssets) {
...
444	    function maxMint(address) external view returns (uint256 maxShares) {
...
507	    function maxWithdraw(address owner) public view returns (uint256 maxAssets) {
...
518	    function previewWithdraw(uint256 assets) public view returns (uint256 shares) {
...
572	    function maxRedeem(address owner) public view returns (uint256 maxShares) {
...
581	    function previewRedeem(uint256 shares) public view returns (uint256 assets) {
```
[361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L361)
[370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L370)
[379](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L379)
[386](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L386)
[392](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L392)
[444](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L444)
[507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L507)
[518](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L518)
[572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L572)
[581](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L581)
[741](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L741)
[753](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L753)
[808](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L808)
[1284](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1284)

---

	 - contracts/PanopticPool.sol

[385](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L385)
[385](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L385)
[1431](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1431)

---

	 - contracts/SemiFungiblePositionManager.sol

[1557](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1557)


</details>

-------
### [N-11] Inconsistent usage of `require`/`error`
<a name="N-11"></a>
[To the top](#TOP)

Some parts of the codebase use `require` statements, while others use custom errors. Consider refactoring the code to use the same approach: the following findings represent the minority of `require` vs error, and they show the first occurance in each file, for brevity.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 14 instances</summary>


---

	 - contracts/libraries/Math.sol

```solidity
131	            if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();
...
297	        if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();
...
312	        if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();
...
319	        if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();
...
326	        if (toCast > uint256(type(int256).max)) revert Errors.CastingError();
...
361	                require(denominator > 0);
...
370	            require(denominator > prod1);
...
448	                require(result < type(uint256).max);
...
484	            require(2 ** 64 > prod1);
...
547	            require(2 ** 96 > prod1);
```
[131](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L131)
[297](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L297)
[312](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L312)
[319](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L319)
[326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L326)
[361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L361)
[370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L370)
[448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448)
[484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L484)
[547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L547)
[588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588)
[624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L624)
[665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665)
[701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L701)


</details>

-------
### [N-12] Events should be emitted before external calls
<a name="N-12"></a>
[To the top](#TOP)

Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 14 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
// @audit functions: `DepositTooLarge`, `safeTransferFrom` called before this event
439	        emit Deposit(msg.sender, receiver, assets, shares);
...
// @audit functions: `DepositTooLarge`, `safeTransferFrom` called before this event
499	        emit Deposit(msg.sender, receiver, assets, shares);
...
// @audit functions: `ExceedsMaximumRedemption`, `safeTransferFrom` called before this event
563	        emit Withdraw(msg.sender, receiver, owner, assets, shares);
...
// @audit functions: `ExceedsMaximumRedemption`, `safeTransferFrom` called before this event
623	        emit Withdraw(msg.sender, receiver, owner, assets, shares);
```
[439](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L439)
[499](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L499)
[563](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L563)
[623](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L623)

---

	 - contracts/PanopticFactory.sol

```solidity
// @audit functions: `NotOwner` called before this event
154	        emit OwnershipTransferred(currentOwner, newOwner);
...
// @audit functions: `InvalidSalt`, `NotOwner`, `getPool`, `UniswapPoolNotInitialized`, `PoolAlreadyInitialized`, `initializeAMMPool`, `cloneDeterministic`, `clone`, `clone`, `startToken`, `startToken`, `startPool`, `increaseObservationCardinalityNext`, `issueNFT` called before this event
268	        emit PoolDeployed(
269	            newPoolContract,
270	            v3Pool,
271	            collateralTracker0,
272	            collateralTracker1,
273	            amount0,
274	            amount1
275	        );
```
[154](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L154)
[268..275](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L268-L275)

---

	 - contracts/PanopticPool.sol

```solidity
// @audit functions: `poolId`, `getPoolId`, `InvalidTokenIdParameter`, `unwrap`, `PositionAlreadyMinted`, `toRightSlot`, `toLeftSlot`, `wrap` called before this event
666	        emit OptionMinted(msg.sender, positionSize, tokenId, poolUtilizations);
...
// @audit functions: `rightSlot` called before this event
853	        emit OptionBurnt(owner, positionSize, tokenId, premiaOwed);
...
// @audit functions: `slot0`, `abs`, `StaleTWAP`, `getAccountMarginDetails`, `rightSlot`, `getAccountMarginDetails`, `leftSlot`, `getSqrtRatioAtTick`, `NotMarginCalled`, `delegate`, `rightSlot`, `delegate`, `leftSlot`, `slot0`, `getLiquidationBonus`, `getSqrtRatioAtTick`, `getSqrtRatioAtTick`, `haircutPremia`, `getSqrtRatioAtTick`, `revoke`, `rightSlot`, `revoke`, `leftSlot`, `NotEnoughCollateral`, `toLeftSlot`, `toRightSlot`, `wrap` called before this event
1170	        emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);
...
// @audit functions: `InputListFail`, `rightSlot`, `computeExercisedAmounts`, `slot0`, `sub`, `validateIsExercisable`, `delegate`, `rightSlot`, `delegate`, `leftSlot`, `exerciseCost`, `add`, `getRefundAmounts`, `refund`, `rightSlot`, `rightSlot`, `refund`, `leftSlot`, `leftSlot`, `refund`, `rightSlot`, `refund`, `leftSlot` called before this event
1277	        emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);
```
[666](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L666)
[853](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L853)
[1170](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1170)
[1277](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1277)
[1654](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1654)

---

	 - contracts/SemiFungiblePositionManager.sol

[390](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L390)
[485](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L485)
[517](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L517)


</details>

-------
### [N-13] Use multiple `require()` and `if` statements instead of `&&`
<a name="N-13"></a>
[To the top](#TOP)

Using multiple `require()` and `if` improves code readability and makes it easier to debug.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 13 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
707	                if (
708	                    (tokenType == 0 && currentValue1 < oracleValue1) ||
709	                    (tokenType == 1 && currentValue0 < oracleValue0)
710	                )
711	                    exerciseFees = exerciseFees.sub(
712	                        LeftRightSigned
713	                            .wrap(0)
714	                            .toRightSlot(
715	                                int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
716	                            )
717	                            .toLeftSlot(
718	                                int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
719	                            )
720	                    );
...
1060	            if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {
1061	                // intrinsic value is the amount that need to be exchanged due to burning in-the-money
1062	
1063	                // add the intrinsic value to the tokenToPay
1064	                tokenToPay += intrinsicValue;
1065	            }
...
1345	                if (
1346	                    ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1
1347	                    ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0
1348	                ) {
1349	                    // position is out-the-money, collateral requirement = SCR * amountMoved
1350	                    required;
1351	                } else {
1352	                    int24 strike = tokenId.strike(index);
1353	                    // if position is ITM or ATM, then the collateral requirement depends on price:
1354	
1355	                    // compute the ratio of strike to price for calls (or price to strike for puts)
1356	                    // (- and * 2 in tick space are / and ^ 2 in price space so sqrtRatioAtTick(2 *(a - b)) = a/b (*2^96)
1357	                    // both of these ratios decrease as the position becomes deeper ITM, and it is possible
1358	                    // for the ratio of the prices to go under the minimum price
1359	                    // (which is the limit of what getSqrtRatioAtTick supports)
1360	                    // so instead we cap it at the minimum price, which is acceptable because
1361	                    // a higher ratio will result in an increased slope for the collateral requirement
1362	                    uint160 ratio = tokenType == 1 // tokenType
1363	                        ? Math.getSqrtRatioAtTick(
1364	                            Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)
1365	                        ) // puts ->  price/strike
1366	                        : Math.getSqrtRatioAtTick(
1367	                            Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)
1368	                        ); // calls -> strike/price
1369	
1370	                    // compute the collateral requirement depending on whether the position is ITM & out-of-range or ITM and in-range:
1371	
1372	                    /// ITM and out-of-range
1373	                    if (
1374	                        ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1
1375	                        ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0
1376	                    ) {
1377	                        /**
1378	                                    Short put BPR = 100% - (price/strike) + SCR
1379	
1380	                           BUYING
1381	                           POWER
1382	                           REQUIREMENT
1383	                         
1384	                                         ^               .         .
1385	                                         |        <- ITM . <-ATM-> . OTM ->
1386	                           100% + SCR% - |--__           .    .    .
1387	                                  100% - | . .¯¯--__     .    .    .
1388	                                         |    .     ¯¯--__    .    .
1389	                                   SCR - |    .          .¯¯--__________
1390	                                         |    .          .    .    .
1391	                                         +----+----------+----+----+--->   current
1392	                                         0   Liqui-     Pa  strike Pb       price
1393	                                             dation
1394	                                             price = SCR*strike                                         
1395	                         */
1396	
1397	                        uint256 c2 = Constants.FP96 - ratio;
1398	
1399	                        // compute the tokens required
1400	                        // position is in-the-money, collateral requirement = amountMoved*(1-ratio) + SCR*amountMoved
1401	                        required += Math.mulDiv96RoundingUp(amountMoved, c2);
1402	                    } else {
1403	                        // position is in-range (ie. current tick is between upper+lower tick): we draw a line between the
1404	                        // collateral requirement at the lowerTick and the one at the upperTick. We use that interpolation as
1405	                        // the collateral requirement when in-range, which always over-estimates the amount of token required
1406	                        // Specifically:
1407	                        //  required = amountMoved * (scaleFactor - ratio) / (scaleFactor + 1) + sellCollateralRatio*amountMoved
1408	                        uint160 scaleFactor = Math.getSqrtRatioAtTick(
1409	                            (tickUpper - strike) + (strike - tickLower)
1410	                        );
1411	                        uint256 c3 = Math.mulDivRoundingUp(
1412	                            amountMoved,
1413	                            scaleFactor - ratio,
1414	                            scaleFactor + Constants.FP96
1415	                        );
1416	                        // position is in-the-money, collateral requirement = amountMoved*(1-SRC)*(scaleFactor-ratio)/(scaleFactor+1) + SCR*amountMoved
1417	                        required += c3;
1418	                    }
1419	                }
...
1373	                    if (
1374	                        ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1
1375	                        ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0
1376	                    ) {
1377	                        /**
1378	                                    Short put BPR = 100% - (price/strike) + SCR
1379	
1380	                           BUYING
1381	                           POWER
1382	                           REQUIREMENT
1383	                         
1384	                                         ^               .         .
1385	                                         |        <- ITM . <-ATM-> . OTM ->
1386	                           100% + SCR% - |--__           .    .    .
1387	                                  100% - | . .¯¯--__     .    .    .
1388	                                         |    .     ¯¯--__    .    .
1389	                                   SCR - |    .          .¯¯--__________
1390	                                         |    .          .    .    .
1391	                                         +----+----------+----+----+--->   current
1392	                                         0   Liqui-     Pa  strike Pb       price
1393	                                             dation
1394	                                             price = SCR*strike                                         
1395	                         */
1396	
1397	                        uint256 c2 = Constants.FP96 - ratio;
1398	
1399	                        // compute the tokens required
1400	                        // position is in-the-money, collateral requirement = amountMoved*(1-ratio) + SCR*amountMoved
1401	                        required += Math.mulDiv96RoundingUp(amountMoved, c2);
1402	                    } else {
1403	                        // position is in-range (ie. current tick is between upper+lower tick): we draw a line between the
1404	                        // collateral requirement at the lowerTick and the one at the upperTick. We use that interpolation as
1405	                        // the collateral requirement when in-range, which always over-estimates the amount of token required
1406	                        // Specifically:
1407	                        //  required = amountMoved * (scaleFactor - ratio) / (scaleFactor + 1) + sellCollateralRatio*amountMoved
1408	                        uint160 scaleFactor = Math.getSqrtRatioAtTick(
1409	                            (tickUpper - strike) + (strike - tickLower)
1410	                        );
1411	                        uint256 c3 = Math.mulDivRoundingUp(
1412	                            amountMoved,
1413	                            scaleFactor - ratio,
1414	                            scaleFactor + Constants.FP96
1415	                        );
1416	                        // position is in-the-money, collateral requirement = amountMoved*(1-SRC)*(scaleFactor-ratio)/(scaleFactor+1) + SCR*amountMoved
1417	                        required += c3;
1418	                    }
```
[707..720](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L707-L720)
[1060..1065](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1060-L1065)
[1345..1419](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1345-L1419)
[1373..1418](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1373-L1418)

---

	 - contracts/PanopticFactory.sol

```solidity
224	        if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();
```
[224](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L224)

---

	 - contracts/PanopticPool.sol

```solidity
460	                if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
461	                    bytes32 chunkKey = keccak256(
462	                        abi.encodePacked(
463	                            tokenId.strike(leg),
464	                            tokenId.width(leg),
465	                            tokenId.tokenType(leg)
466	                        )
467	                    );
468	
469	                    LeftRightUnsigned availablePremium = _getAvailablePremium(
470	                        _getTotalLiquidity(tokenId, leg),
471	                        s_settledTokens[chunkKey],
472	                        s_grossPremiumLast[chunkKey],
473	                        LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
474	                        premiumAccumulatorsByLeg[leg]
475	                    );
476	                    portfolioPremium = portfolioPremium.add(
477	                        LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478	                    );
479	                } else {
480	                    portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
481	                }
```
[460..481](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L460-L481)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
787	            if ((itm0 != 0) && (itm1 != 0)) {
788	                (uint160 sqrtPriceX96, , , , , , ) = _univ3pool.slot0();
789	
790	                // implement a single "netting" swap. Thank you @danrobinson for this puzzle/idea
791	                // note: negative ITM amounts denote a surplus of tokens (burning liquidity), while positive amounts denote a shortage of tokens (minting liquidity)
792	                // compute the approximate delta of token0 that should be resolved in the swap at the current tick
793	                // we do this by flipping the signs on the token1 ITM amount converting+deducting it against the token0 ITM amount
794	                // couple examples (price = 2 1/0):
795	                //  - 100 surplus 0, 100 surplus 1 (itm0 = -100, itm1 = -100)
796	                //    normal swap 0: 100 0 => 200 1
797	                //    normal swap 1: 100 1 => 50 0
798	                //    final swap amounts: 50 0 => 100 1
799	                //    netting swap: net0 = -100 - (-100/2) = -50, ZF1 = true, 50 0 => 100 1
800	                // - 100 surplus 0, 100 shortage 1 (itm0 = -100, itm1 = 100)
801	                //    normal swap 0: 100 0 => 200 1
802	                //    normal swap 1: 50 0 => 100 1
803	                //    final swap amounts: 150 0 => 300 1
804	                //    netting swap: net0 = -100 - (100/2) = -150, ZF1 = true, 150 0 => 300 1
805	                // - 100 shortage 0, 100 surplus 1 (itm0 = 100, itm1 = -100)
806	                //    normal swap 0: 200 1 => 100 0
807	                //    normal swap 1: 100 1 => 50 0
808	                //    final swap amounts: 300 1 => 150 0
809	                //    netting swap: net0 = 100 - (-100/2) = 150, ZF1 = false, 300 1 => 150 0
810	                // - 100 shortage 0, 100 shortage 1 (itm0 = 100, itm1 = 100)
811	                //    normal swap 0: 200 1 => 100 0
812	                //    normal swap 1: 50 0 => 100 1
813	                //    final swap amounts: 100 1 => 50 0
814	                //    netting swap: net0 = 100 - (100/2) = 50, ZF1 = false, 100 1 => 50 0
815	                // - = Net surplus of token0
816	                // + = Net shortage of token0
817	                int256 net0 = itm0 - PanopticMath.convert1to0(itm1, sqrtPriceX96);
818	
819	                zeroForOne = net0 < 0;
820	
821	                //compute the swap amount, set as positive (exact input)
822	                swapAmount = -net0;
823	            } else if (itm0 != 0) {
824	                zeroForOne = itm0 < 0;
825	                swapAmount = -itm0;
826	            } else {
827	                zeroForOne = itm1 > 0;
828	                swapAmount = -itm1;
829	            }
```
[787..829](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L787-L829)

---

	 - contracts/libraries/PanopticMath.sol

```solidity
218	                    if ((below) && (lastObservedTick > entry)) {
219	                        shift += 1;
220	                        below = false;
221	                    }
...
704	            if (!(paid0 > balance0 && paid1 > balance1)) {
705	                // liquidatee cannot pay back the liquidator fully in either token, so no protocol loss can be avoided
706	                if ((paid0 > balance0)) {
707	                    // liquidatee has insufficient token0 but some token1 left over, so we use what they have left to mitigate token0 losses
708	                    // we do this by substituting an equivalent value of token1 in our refund to the liquidator, plus a bonus, for the token0 we convert
709	                    // we want to convert the minimum amount of tokens required to achieve the lowest possible protocol loss (to avoid overpaying on the conversion bonus)
710	                    // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token1 balance: balance1 - paid1
711	                    // and paid0 - balance0 is the amount of token0 that the liquidatee is missing, i.e the protocol loss
712	                    // if the protocol loss is lower than the excess token1 balance, then we can fully mitigate the loss and we should only convert the loss amount
713	                    // if the protocol loss is higher than the excess token1 balance, we can only mitigate part of the loss, so we should convert only the excess token1 balance
714	                    // thus, the value converted should be min(balance1 - paid1, paid0 - balance0)
715	                    bonus1 += Math.min(
716	                        balance1 - paid1,
717	                        PanopticMath.convert0to1(paid0 - balance0, sqrtPriceX96Final)
718	                    );
719	                    bonus0 -= Math.min(
720	                        PanopticMath.convert1to0(balance1 - paid1, sqrtPriceX96Final),
721	                        paid0 - balance0
722	                    );
723	                }
724	                if ((paid1 > balance1)) {
725	                    // liquidatee has insufficient token1 but some token0 left over, so we use what they have left to mitigate token1 losses
726	                    // we do this by substituting an equivalent value of token0 in our refund to the liquidator, plus a bonus, for the token1 we convert
727	                    // we want to convert the minimum amount of tokens required to achieve the lowest possible protocol loss (to avoid overpaying on the conversion bonus)
728	                    // the maximum level of protocol loss mitigation that can be achieved is the liquidatee's excess token0 balance: balance0 - paid0
729	                    // and paid1 - balance1 is the amount of token1 that the liquidatee is missing, i.e the protocol loss
730	                    // if the protocol loss is lower than the excess token0 balance, then we can fully mitigate the loss and we should only convert the loss amount
731	                    // if the protocol loss is higher than the excess token0 balance, we can only mitigate part of the loss, so we should convert only the excess token0 balance
732	                    // thus, the value converted should be min(balance0 - paid0, paid1 - balance1)
733	                    bonus0 += Math.min(
734	                        balance0 - paid0,
735	                        PanopticMath.convert1to0(paid1 - balance1, sqrtPriceX96Final)
736	                    );
737	                    bonus1 -= Math.min(
738	                        PanopticMath.convert0to1(balance0 - paid0, sqrtPriceX96Final),
739	                        paid1 - balance1
740	                    );
741	                }
742	            }
...
797	            if (
798	                longPremium.rightSlot() < collateralDelta0 &&
799	                longPremium.leftSlot() > collateralDelta1
800	            ) {
801	                int256 protocolLoss1 = collateralDelta1;
802	                (collateralDelta0, collateralDelta1) = (
803	                    -Math.min(
804	                        collateralDelta0 - longPremium.rightSlot(),
805	                        PanopticMath.convert1to0(
806	                            longPremium.leftSlot() - collateralDelta1,
807	                            sqrtPriceX96Final
808	                        )
809	                    ),
810	                    Math.min(
811	                        longPremium.leftSlot() - collateralDelta1,
812	                        PanopticMath.convert0to1(
813	                            collateralDelta0 - longPremium.rightSlot(),
814	                            sqrtPriceX96Final
815	                        )
816	                    )
817	                );
818	
819	                haircut0 = longPremium.rightSlot();
820	                haircut1 = protocolLoss1 + collateralDelta1;
821	            } else if (
822	                longPremium.leftSlot() < collateralDelta1 &&
823	                longPremium.rightSlot() > collateralDelta0
824	            ) {
825	                int256 protocolLoss0 = collateralDelta0;
826	                (collateralDelta0, collateralDelta1) = (
827	                    Math.min(
828	                        longPremium.rightSlot() - collateralDelta0,
829	                        PanopticMath.convert1to0(
830	                            collateralDelta1 - longPremium.leftSlot(),
831	                            sqrtPriceX96Final
832	                        )
833	                    ),
834	                    -Math.min(
835	                        collateralDelta1 - longPremium.leftSlot(),
836	                        PanopticMath.convert0to1(
837	                            longPremium.rightSlot() - collateralDelta0,
838	                            sqrtPriceX96Final
839	                        )
840	                    )
841	                );
842	
843	                haircut0 = collateralDelta0 + protocolLoss0;
844	                haircut1 = longPremium.leftSlot();
845	            } else {
846	                // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
847	                haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
848	                haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
849	
850	                collateralDelta0 = 0;
851	                collateralDelta1 = 0;
852	            }
```
[218..221](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L218-L221)
[704..742](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L704-L742)
[797..852](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L797-L852)
[821..852](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L821-L852)

---

	 - contracts/types/TokenId.sol

[560..561](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L560-L561)
[566..567](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L566-L567)


</details>

-------
### [N-14] State variables not capped at reasonable values
<a name="N-14"></a>
[To the top](#TOP)

Consider adding minimum/maximum value checks to ensure that the state variables below can never be used to excessively harm users, including via griefing

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 13 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
// @audit: parameter `assets` is not limited in function body
914	        uint256 assets
```
[914](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L914)

---

	 - contracts/PanopticFactory.sol

```solidity
// @audit: parameter `amount0Owed` is not limited in function body
173	        uint256 amount0Owed,
...
// @audit: parameter `amount1Owed` is not limited in function body
174	        uint256 amount1Owed,
...
// @audit: parameter `fee` is not limited in function body
213	        uint24 fee,
...
// @audit: parameter `fee` is not limited in function body
339	        uint24 fee
```
[173](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L173)
[174](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L174)
[213](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L213)
[339](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L339)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
// @audit: parameter `amount0Owed` is not limited in function body
403	        uint256 amount0Owed,
...
// @audit: parameter `amount1Delta` is not limited in function body
437	        int256 amount1Delta,
...
// @audit: parameter `amount1Owed` is not limited in function body
404	        uint256 amount1Owed,
...
// @audit: parameter `amount` is not limited in function body
593	    function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {
```
[403](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L403)
[437](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L437)
[404](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L404)
[593](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L593)

---

	 - contracts/libraries/PanopticMath.sol

```solidity
// @audit: parameter `amount` is not limited in function body
490	    function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {
```
[490](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L490)
[507](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L507)
[524](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L524)
[547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L547)


</details>

-------
### [N-15] Function names should use lowerCamelCase
<a name="N-15"></a>
[To the top](#TOP)

According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#function-names) function names should be in `mixedCase` (lowerCamelCase)

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 11 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
677	    function _mintInSFPMAndUpdateCollateral(
678	        TokenId tokenId,
679	        uint128 positionSize,
680	        int24 tickLimitLow,
681	        int24 tickLimitHigh
682	    ) internal returns (uint128) {
...
1450	    function getUniV3TWAP() internal view returns (int24 twapTick) {
```
[677..682](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L677-L682)
[1450](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1450)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
350	    function initializeAMMPool(address token0, address token1, uint24 fee) external {
...
680	    function _validateAndForwardToAMM(
681	        TokenId tokenId,
682	        uint128 positionSize,
683	        int24 tickLimitLow,
684	        int24 tickLimitHigh,
685	        bool isBurn
686	    ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {
...
756	    function swapInAMM(
757	        IUniswapV3Pool univ3pool,
758	        LeftRightSigned itmAmounts
759	    ) internal returns (LeftRightSigned totalSwapped) {
...
863	    function _createPositionInAMM(
864	        IUniswapV3Pool univ3pool,
865	        TokenId tokenId,
866	        uint128 positionSize,
867	        bool isBurn
868	    )
869	        internal
870	        returns (
871	            LeftRightSigned totalMoved,
872	            LeftRightUnsigned[4] memory collectedByLeg,
873	            LeftRightSigned itmAmounts
874	        )
875	    {
...
958	    function _createLegInAMM(
959	        IUniswapV3Pool univ3pool,
960	        TokenId tokenId,
961	        uint256 leg,
962	        LiquidityChunk liquidityChunk,
963	        bool isBurn
964	    )
965	        internal
966	        returns (
967	            LeftRightSigned moved,
968	            LeftRightSigned itmAmounts,
969	            LeftRightUnsigned collectedSingleLeg
970	        )
971	    {
```
[350](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350)
[680..686](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L680-L686)
[756..759](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L756-L759)
[863..875](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L863-L875)
[958..971](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L958-L971)

---

	 - contracts/libraries/FeesCalc.sol

```solidity
97	    function calculateAMMSwapFees(
98	        IUniswapV3Pool univ3pool,
99	        int24 currentTick,
100	        int24 tickLower,
101	        int24 tickUpper,
102	        uint128 liquidity
103	    ) public view returns (LeftRightSigned) {
...
130	    function _getAMMSwapFeesPerLiquidityCollected(
131	        IUniswapV3Pool univ3pool,
132	        int24 currentTick,
133	        int24 tickLower,
134	        int24 tickUpper
135	    ) internal view returns (uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128) {
```
[97..103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L97-L103)
[130..135](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/FeesCalc.sol#L130-L135)

---

	 - contracts/libraries/PanopticMath.sol

```solidity
607	    function _calculateIOAmounts(
608	        TokenId tokenId,
609	        uint128 positionSize,
610	        uint256 legIndex
611	    ) internal pure returns (LeftRightSigned longs, LeftRightSigned shorts) {
```
[607..611](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L607-L611)

---

	 - contracts/tokens/interfaces/IDonorNFT.sol

[13..19](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IDonorNFT.sol#L13-L19)


</details>

-------
### [N-16] `else`-block not required
<a name="N-16"></a>
[To the top](#TOP)

One level of nesting can be removed by not having an `else` block when the `if`-block returns, and `if (foo) { return 1; } else { return 2; }` becomes `if (foo) { return 1; } return 2;`

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 9 instances</summary>


---

	 - contracts/libraries/PanopticMath.sol

```solidity
325	        if (tokenId.asset(legIndex) == 0) {
326	            return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
327	        } else {
328	            return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
329	        }
...
425	        if (tokenType == 0) {
426	            return (
427	                tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
428	                tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
429	            );
430	        } else {
431	            return (
432	                tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
433	                tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
434	            );
435	        }
...
494	            if (sqrtPriceX96 < type(uint128).max) {
495	                return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
496	            } else {
497	                return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
498	            }
...
511	            if (sqrtPriceX96 < type(uint128).max) {
512	                return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
513	            } else {
514	                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
515	            }
...
528	            if (sqrtPriceX96 < type(uint128).max) {
529	                int256 absResult = Math
530	                    .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
531	                    .toInt256();
532	                return amount < 0 ? -absResult : absResult;
533	            } else {
534	                int256 absResult = Math
535	                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
536	                    .toInt256();
537	                return amount < 0 ? -absResult : absResult;
538	            }
...
551	            if (sqrtPriceX96 < type(uint128).max) {
552	                int256 absResult = Math
553	                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
554	                    .toInt256();
555	                return amount < 0 ? -absResult : absResult;
556	            } else {
557	                int256 absResult = Math
558	                    .mulDiv(
559	                        Math.absUint(amount),
560	                        2 ** 128,
561	                        Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
562	                    )
563	                    .toInt256();
564	                return amount < 0 ? -absResult : absResult;
565	            }
```
[325..329](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L325-L329)
[425..435](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L425-L435)
[494..498](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L494-L498)
[511..515](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L511-L515)
[528..538](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L528-L538)
[551..565](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L551-L565)

---

	 - contracts/types/TokenId.sol

```solidity
439	        if (optionRatios < 2 ** 64) {
440	            return 0;
441	        } else if (optionRatios < 2 ** 112) {
442	            return 1;
443	        } else if (optionRatios < 2 ** 160) {
444	            return 2;
445	        } else if (optionRatios < 2 ** 208) {
446	            return 3;
447	        }
...
441	        } else if (optionRatios < 2 ** 112) {
442	            return 1;
443	        } else if (optionRatios < 2 ** 160) {
444	            return 2;
445	        } else if (optionRatios < 2 ** 208) {
446	            return 3;
447	        }
...
443	        } else if (optionRatios < 2 ** 160) {
444	            return 2;
445	        } else if (optionRatios < 2 ** 208) {
446	            return 3;
447	        }
```
[439..447](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L439-L447)
[441..447](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L441-L447)
[443..447](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L443-L447)


</details>

-------
### [N-17] State variables should include comments
<a name="N-17"></a>
[To the top](#TOP)

Consider adding some comments on critical state variables to explain what they are supposed to do: this will help for future code reviews.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 9 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
120	    bool internal constant DONOT_COMMIT_LONG_SETTLED = false;
...
133	    bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;
...
136	    uint256 internal constant MEDIAN_PERIOD = 60;
...
156	    int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;
...
171	    uint256 internal constant BP_DECREASE_BUFFER = 13_333;
...
174	    uint256 internal constant NO_BUFFER = 10_000;
```
[120](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L120)
[133](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L133)
[136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L136)
[156](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L156)
[171](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L171)
[174](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L174)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
126	    bool internal constant BURN = true;
...
133	    uint128 private constant VEGOID = 2;
...
289	    mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;
```
[126](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L126)
[133](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L133)
[289](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L289)


</details>

-------
### [N-18] Custom `error` should be used rather than `require`/`assert`
<a name="N-18"></a>
[To the top](#TOP)

Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in try-catch blocks, and are easier to re-use and maintain.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 9 instances</summary>


---

	 - contracts/libraries/Math.sol

```solidity
361	                require(denominator > 0);
...
370	            require(denominator > prod1);
...
448	                require(result < type(uint256).max);
...
484	            require(2 ** 64 > prod1);
...
547	            require(2 ** 96 > prod1);
...
588	                require(result < type(uint256).max);
...
624	            require(2 ** 128 > prod1);
...
665	                require(result < type(uint256).max);
...
701	            require(2 ** 192 > prod1);
```
[361](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L361)
[370](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L370)
[448](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L448)
[484](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L484)
[547](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L547)
[588](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L588)
[624](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L624)
[665](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L665)
[701](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L701)


</details>

-------
### [N-19] Numeric values having to do with time should use time units for readability
<a name="N-19"></a>
[To the top](#TOP)

There are [units](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#time-units) for seconds, minutes, hours, days, and weeks, and since they're defined, they should be used

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 8 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
136	    uint256 internal constant MEDIAN_PERIOD = 60;
...
148	    uint256 internal constant SLOW_ORACLE_CARDINALITY = 7;
...
313	                (uint256(uint24(currentTick)) << 24) + // add to slot 4
```
[136](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L136)
[148](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L148)
[313](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L313)

---

	 - contracts/libraries/PanopticMath.sol

```solidity
178	                (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
...
179	                    int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
...
211	                    if (rank == 7) {
...
217	                    entry = int24(uint24(medianData >> (rank * 24)));
...
229	                    uint256(uint192(medianData << 24)) +
```
[178](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L178)
[179](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L179)
[211](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L211)
[217](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L217)
[229](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L229)


</details>

-------
### [N-20] Unused function parameter
<a name="N-20"></a>
[To the top](#TOP)

Comment out the variable name to suppress compiler warnings

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 8 instances</summary>


---

	 - contracts/libraries/Math.sol

```solidity
340	    function mulDiv(
341	        uint256 a,
342	        uint256 b,
343	        uint256 denominator
344	    ) internal pure returns (uint256 result) {
...
458	    function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {
...
521	    function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {
...
598	    function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {
...
675	    function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {
...
738	    function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {
```
[340..344](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L340-L344)
[458](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L458)
[521](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L521)
[598](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L598)
[675](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L675)
[738](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L738)

---

	 - contracts/libraries/SafeTransferLib.sol

```solidity
21	    function safeTransferFrom(address token, address from, address to, uint256 amount) internal {
...
52	    function safeTransfer(address token, address to, uint256 amount) internal {
```
[21](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L21)
[52](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L52)


</details>

-------
### [N-21] Events may be emitted out of order due to reentrancy
<a name="N-21"></a>
[To the top](#TOP)

Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 7 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
417	    function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
...
477	    function mint(uint256 shares, address receiver) external returns (uint256 assets) {
...
531	    function withdraw(
532	        uint256 assets,
533	        address receiver,
534	        address owner
535	    ) external returns (uint256 shares) {
...
591	    function redeem(
592	        uint256 shares,
593	        address receiver,
594	        address owner
595	    ) external returns (uint256 assets) {
```
[417](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L417)
[477](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L477)
[531..535](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L531-L535)
[591..595](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L591-L595)

---

	 - contracts/PanopticFactory.sol

```solidity
210	    function deployNewPool(
211	        address token0,
212	        address token1,
213	        uint24 fee,
214	        bytes32 salt
215	    ) external returns (PanopticPool newPoolContract) {
```
[210..215](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210-L215)

---

	 - contracts/PanopticPool.sol

```solidity
1017	    function liquidate(
1018	        TokenId[] calldata positionIdListLiquidator,
1019	        address liquidatee,
1020	        LeftRightUnsigned delegations,
1021	        TokenId[] calldata positionIdList
1022	    ) external {
...
1179	    function forceExercise(
1180	        address account,
1181	        TokenId[] calldata touchedId,
1182	        TokenId[] calldata positionIdListExercisee,
1183	        TokenId[] calldata positionIdListExercisor
1184	    ) external {
```
[1017..1022](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1017-L1022)
[1179..1184](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1179-L1184)


</details>

-------
### [N-22] Expressions for constant values should use `immutable` rather than `constant`
<a name="N-22"></a>
[To the top](#TOP)

While it does not save gas for some simple binary expressions because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 7 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
103	    int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;
...
105	    int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;
...
165	    uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);
```
[103](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L103)
[105](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L105)
[165](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L165)

---

	 - contracts/libraries/Constants.sol

```solidity
12	    int24 internal constant MIN_V3POOL_TICK = -887272;
```
[12](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Constants.sol#L12)

---

	 - contracts/libraries/Math.sol

```solidity
15	    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```
[15](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Math.sol#L15)

---

	 - contracts/libraries/PanopticMath.sol

```solidity
23	    uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;
```
[23](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L23)

---

	 - contracts/types/LeftRight.sol

```solidity
26	    int256 internal constant LEFT_HALF_BIT_MASK_INT =
27	        int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));
```
[26..27](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L26-L27)


</details>

-------
### [N-23] Missing event and or timelock for critical parameter change
<a name="N-23"></a>
[To the top](#TOP)

Events help non-contract tools to track changes, and timelocks prevent users from being surprised by changes

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 6 instances</summary>


---

	 - contracts/PanopticPool.sol

```solidity
859	    function _updatePositionDataBurn(address owner, TokenId tokenId) internal {
...
1405	    function _updatePositionsHash(address account, TokenId tokenId, bool addFlag) internal {
...
1587	    function settleLongPremium(
1588	        TokenId[] calldata positionIdList,
1589	        address owner,
1590	        uint256 legIndex
1591	    ) external {
...
1666	    function _updateSettlementPostMint(
1667	        TokenId tokenId,
1668	        LeftRightUnsigned[4] memory collectedByLeg,
1669	        uint128 positionSize
1670	    ) internal {
...
1833	    function _updateSettlementPostBurn(
1834	        address owner,
1835	        TokenId tokenId,
1836	        LeftRightUnsigned[4] memory collectedByLeg,
1837	        uint128 positionSize,
1838	        bool commitLongSettled
1839	    ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {
```
[859](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L859)
[1405](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1405)
[1587..1591](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1587-L1591)
[1666..1670](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1666-L1670)
[1833..1839](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1833-L1839)

---

	 - contracts/tokens/ERC1155Minimal.sol

```solidity
81	    function setApprovalForAll(address operator, bool approved) public {
```
[81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L81)


</details>

-------
### [N-24] Setters should prevent re-setting of the same value
<a name="N-24"></a>
[To the top](#TOP)

This especially problematic when the setter also emits the same value, which may be confusing to offline parsers

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 6 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
221	    function startToken(
222	        bool underlyingIsToken0,
223	        address token0,
224	        address token1,
225	        uint24 fee,
226	        PanopticPool panopticPool
227	    ) external {
```
[221..227](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221-L227)

---

	 - contracts/PanopticFactory.sol

```solidity
134	    function initialize(address _owner) public {
...
147	    function transferOwnership(address newOwner) external {
```
[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134)
[147](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L147)

---

	 - contracts/PanopticPool.sol

```solidity
291	    function startPool(
292	        IUniswapV3Pool _univ3pool,
293	        address token0,
294	        address token1,
295	        CollateralTracker collateralTracker0,
296	        CollateralTracker collateralTracker1
297	    ) external {
```
[291..297](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L297)

---

	 - contracts/tokens/ERC1155Minimal.sol

```solidity
81	    function setApprovalForAll(address operator, bool approved) public {
```
[81](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L81)

---

	 - contracts/tokens/ERC20Minimal.sol

```solidity
49	    function approve(address spender, uint256 amount) public returns (bool) {
```
[49](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L49)


</details>

-------
### [N-25] Typos
<a name="N-25"></a>
[To the top](#TOP)



#### <ins>Proof Of Concept</ins>

<details>

<summary>see 6 instances</summary>

```bash
error: `initalized` should be `initialized`
  --> project\2024-04-panoptic\contracts\CollateralTracker.sol:92:92
   |
92 |     /// @dev As each instance is deployed via proxy clone, initial parameters must only be initalized once via startToken().
   |                                                                                            ^^^^^^^^^^
   |

```
[1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L1)
```bash
error: `caluculation` should be `calculation`
  --> project\2024-04-panoptic\contracts\PanopticPool.sol:107:42
    |
107 |     // Flags used as arguments to premia caluculation functions
    |                                          ^^^^^^^^^^^^
    |
error: `wether` should be `weather`, `whether`
  --> project\2024-04-panoptic\contracts\PanopticPool.sol:122:40
    |
122 |     /// @dev Boolean flag to determine wether a position is added (true) or not (!ADD = false)
    |                                        ^^^^^^
    |
error: `Mananger` should be `Manager`
  --> project\2024-04-panoptic\contracts\PanopticPool.sol:278:122
    |
278 |     /// @notice During construction: sets the address of the panoptic factory smart contract and the SemiFungiblePositionMananger (SFPM).
    |                                                                                                                          ^^^^^^^^
    |

```
[1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L1)
```bash
error: `postion` should be `position`
  --> project\2024-04-panoptic\contracts\SemiFungiblePositionManager.sol:1106:79
     |
1106 |     /// @notice caches/stores the accumulated premia values for the specified postion.
     |                                                                               ^^^^^^^
     |
error: `seperated` should be `separated`
  --> project\2024-04-panoptic\contracts\SemiFungiblePositionManager.sol:1337:32
     |
1337 |         // premia, and is only seperated to simplify the calculation
     |                                ^^^^^^^^^
     |

```
[1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L1)
```bash
error: `avaiable` should be `available`
  --> project\2024-04-panoptic\contracts\libraries\Errors.sol:62:51
   |
62 |     /// @notice PanopticPool: there is not enough avaiable liquidity to buy an option
   |                                                   ^^^^^^^^
   |

```
[1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/Errors.sol#L1)
```bash
error: `accomodate` should be `accommodate`
  --> project\2024-04-panoptic\contracts\libraries\PanopticMath.sol:486:67
    |
486 |     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of tick.s
    |                                                                   ^^^^^^^^^^
    |
error: `accomodate` should be `accommodate`
  --> project\2024-04-panoptic\contracts\libraries\PanopticMath.sol:503:67
    |
503 |     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.
    |                                                                   ^^^^^^^^^^
    |
error: `accomodate` should be `accommodate`
  --> project\2024-04-panoptic\contracts\libraries\PanopticMath.sol:520:67
    |
520 |     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.
    |                                                                   ^^^^^^^^^^
    |
error: `accomodate` should be `accommodate`
  --> project\2024-04-panoptic\contracts\libraries\PanopticMath.sol:543:67
    |
543 |     /// @dev Uses reduced precision after tick 443636 in order to accomodate the full range of ticks.
    |                                                                   ^^^^^^^^^^
    |
error: `consistentcy` should be `consistently`
  --> project\2024-04-panoptic\contracts\libraries\PanopticMath.sol:663:51
    |
663 |                 // evaluate at TWAP price to keep consistentcy with solvency calculations
    |                                                   ^^^^^^^^^^^^
    |
error: `commited` should be `committed`
  --> project\2024-04-panoptic\contracts\libraries\PanopticMath.sol:886:52
    |
886 |                         // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
    |                                                    ^^^^^^^^
    |

```
[1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L1)
```bash
error: `explictily` should be `explicitly`
  --> project\2024-04-panoptic\contracts\types\LeftRight.sol:153:84
    |
153 |             // adding leftRight packed uint128's is same as just adding the values explictily
    |                                                                                    ^^^^^^^^^^
    |
error: `occured` should be `occurred`
  --> project\2024-04-panoptic\contracts\types\LeftRight.sol:159:37
    |
159 |             // then an overflow has occured
    |                                     ^^^^^^^
    |
error: `explictily` should be `explicitly`
  --> project\2024-04-panoptic\contracts\types\LeftRight.sol:176:94
    |
176 |             // subtracting leftRight packed uint128's is same as just subtracting the values explictily
    |                                                                                              ^^^^^^^^^^
    |
error: `occured` should be `occurred`
  --> project\2024-04-panoptic\contracts\types\LeftRight.sol:182:38
    |
182 |             // then an underflow has occured
    |                                      ^^^^^^^
    |

```
[1](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/LeftRight.sol#L1)


</details>

-------
### [N-26] Consider using `delete` rather than assigning zero/false to clear values
<a name="N-26"></a>
[To the top](#TOP)

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 5 instances</summary>


---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
332	        s_poolContext[poolId].locked = false;
```
[332](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L332)

---

	 - contracts/libraries/PanopticMath.sol

```solidity
220	                        below = false;
...
850	                collateralDelta0 = 0;
...
851	                collateralDelta1 = 0;
```
[220](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L220)
[850](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L850)
[851](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/PanopticMath.sol#L851)

---

	 - contracts/types/TokenId.sol

```solidity
377	                optionRatios = 0;
```
[377](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/types/TokenId.sol#L377)


</details>

-------
### [N-27] Use of `override` is unnecessary
<a name="N-27"></a>
[To the top](#TOP)

Starting with Solidity version [0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), using the `override` keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 4 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
323	    function transfer(
324	        address recipient,
325	        uint256 amount
326	    ) public override(ERC20Minimal) returns (bool) {
...
341	    function transferFrom(
342	        address from,
343	        address to,
344	        uint256 amount
345	    ) public override(ERC20Minimal) returns (bool) {
```
[323..326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L323-L326)
[341..345](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L341-L345)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
540	    function safeTransferFrom(
541	        address from,
542	        address to,
543	        uint256 id,
544	        uint256 amount,
545	        bytes calldata data
546	    ) public override {
...
566	    function safeBatchTransferFrom(
567	        address from,
568	        address to,
569	        uint256[] calldata ids,
570	        uint256[] calldata amounts,
571	        bytes calldata data
572	    ) public override {
```
[540..546](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L540-L546)
[566..572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566-L572)


</details>

-------
### [N-28] Consider disallowing transfers to `address(this)`
<a name="N-28"></a>
[To the top](#TOP)



#### <ins>Proof Of Concept</ins>

<details>

<summary>see 4 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
323	    function transfer(
324	        address recipient,
325	        uint256 amount
326	    ) public override(ERC20Minimal) returns (bool) {
```
[323..326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L323-L326)

---

	 - contracts/libraries/SafeTransferLib.sol

```solidity
52	    function safeTransfer(address token, address to, uint256 amount) internal {
```
[52](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L52)

---

	 - contracts/tokens/ERC20Minimal.sol

```solidity
61	    function transfer(address to, uint256 amount) public virtual returns (bool) {
```
[61](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L61)

---

	 - contracts/tokens/interfaces/IERC20Partial.sol

```solidity
27	    function transfer(address to, uint256 amount) external;
```
[27](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/interfaces/IERC20Partial.sol#L27)


</details>

-------
### [N-29] Use `@inheritdoc` for overridden functions
<a name="N-29"></a>
[To the top](#TOP)

It is recommended to use `@inheritdoc` for overridden functions.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 4 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
319	    /// @dev See {IERC20-transfer}.
320	    /// Requirements:
321	    /// - the caller must have a balance of at least 'amount'.
322	    /// - the msg.sender must not have any position on the panoptic pool
323	    function transfer(
324	        address recipient,
325	        uint256 amount
326	    ) public override(ERC20Minimal) returns (bool) {
...
336	    /// @dev See {IERC20-transferFrom}.
337	    /// Requirements:
338	    /// - the 'from' must have a balance of at least 'amount'.
339	    /// - the caller must have allowance for 'from' of at least 'amount' tokens.
340	    /// - 'from' must not have any open positions on the panoptic pool.
341	    function transferFrom(
342	        address from,
343	        address to,
344	        uint256 amount
345	    ) public override(ERC20Minimal) returns (bool) {
```
[319..326](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L319-L326)
[336..345](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L336-L345)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
533	    /// @notice Transfer a single token from one user to another
534	    /// @dev supports token approvals
535	    /// @param from the user to transfer tokens from
536	    /// @param to the user to transfer tokens to
537	    /// @param id the ERC1155 token id to transfer
538	    /// @param amount the amount of tokens to transfer
539	    /// @param data optional data to include in the receive hook
540	    function safeTransferFrom(
541	        address from,
542	        address to,
543	        uint256 id,
544	        uint256 amount,
545	        bytes calldata data
546	    ) public override {
...
558	    /// @notice Transfer multiple tokens from one user to another
559	    /// @dev supports token approvals
560	    /// @dev ids and amounts must be of equal length
561	    /// @param from the user to transfer tokens from
562	    /// @param to the user to transfer tokens to
563	    /// @param ids the ERC1155 token ids to transfer
564	    /// @param amounts the amounts of tokens to transfer
565	    /// @param data optional data to include in the receive hook
566	    function safeBatchTransferFrom(
567	        address from,
568	        address to,
569	        uint256[] calldata ids,
570	        uint256[] calldata amounts,
571	        bytes calldata data
572	    ) public override {
```
[533..546](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L533-L546)
[558..572](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L558-L572)


</details>

-------
### [N-30] Emits without `msg.sender` parameter
<a name="N-30"></a>
[To the top](#TOP)

If `msg.sender` play a part in the functionality of a function, any emits of this function should include msg.sender to ensure transparency with users

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 3 instances</summary>


---

	 - contracts/PanopticFactory.sol

```solidity
// @audit Current function use `msg.sender`, but do not emit it
154	        emit OwnershipTransferred(currentOwner, newOwner);
...
// @audit Current function use `msg.sender`, but do not emit it
268	        emit PoolDeployed(
269	            newPoolContract,
270	            v3Pool,
271	            collateralTracker0,
272	            collateralTracker1,
273	            amount0,
274	            amount1
275	        );
```
[154](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L154)
[268..275](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L268-L275)

---

	 - contracts/tokens/ERC20Minimal.sol

```solidity
// @audit Current function use `msg.sender`, but do not emit it
94	        emit Transfer(from, to, amount);
```
[94](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L94)


</details>

-------
### [N-31] `constructor` missing zero address check
<a name="N-31"></a>
[To the top](#TOP)

It is important to ensure that the constructor does not allow zero address to be set.
    This is a common mistake that can lead to loss of funds or redeployment of the contract.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 3 instances</summary>


---

	 - contracts/PanopticFactory.sol

```solidity
115	    constructor(
116	        address _WETH9,
117	        SemiFungiblePositionManager _SFPM,
118	        IUniswapV3Factory _univ3Factory,
119	        IDonorNFT _donorNFT,
120	        address _poolReference,
121	        address _collateralReference
122	    ) {
```
[115..122](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L115-L122)

---

	 - contracts/PanopticPool.sol

```solidity
280	    constructor(SemiFungiblePositionManager _sfpm) {
```
[280](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L280)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
341	    constructor(IUniswapV3Factory _factory) {
```
[341](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L341)


</details>

-------
### [N-32] Consider adding a block/deny-list
<a name="N-32"></a>
[To the top](#TOP)

Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 3 instances</summary>


---

	 - contracts/CollateralTracker.sol

```solidity
36	contract CollateralTracker is ERC20Minimal, Multicall {
37	    // Used for safecasting
38	    using Math for uint256;
```
[36..38](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L36-L38)

---

	 - contracts/PanopticFactory.sol

```solidity
26	contract PanopticFactory is Multicall {
27	    /*//////////////////////////////////////////////////////////////
28	                                 EVENTS
29	    //////////////////////////////////////////////////////////////*/
30	
31	    /// @notice Emitted when the ownership of the factory is transferred.
32	    /// @param oldOwner The previous owner of the factory
33	    /// @param newOwner The new owner of the factory
34	    event OwnershipTransferred(address indexed oldOwner, address indexed newOwner);
```
[26..34](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L26-L34)

---

	 - contracts/SemiFungiblePositionManager.sol

```solidity
72	contract SemiFungiblePositionManager is ERC1155, Multicall {
73	    /*//////////////////////////////////////////////////////////////
74	                                 EVENTS
75	    //////////////////////////////////////////////////////////////*/
76	
77	    /// @notice Emitted when a UniswapV3Pool is initialized.
78	    /// @param uniswapPool Address of the underlying Uniswap v3 pool
79	    /// @param poolId The SFPM's pool identifier for the pool, including the 16-bit tick spacing and 48-bit pool pattern
80	    event PoolInitialized(address indexed uniswapPool, uint64 poolId);
```
[72..80](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L72-L80)


</details>

-------
### [N-33] Variable names that consist of all capital letters should be reserved for `constant`/`immutable` variables
<a name="N-33"></a>
[To the top](#TOP)

If the variable needs to be different based on which class it comes from, a `view`/`pure` _function_ should be used instead (e.g. like [this](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59)).

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 2 instances</summary>


---

	 - contracts/PanopticFactory.sol

```solidity
116	        address _WETH9,
...
117	        SemiFungiblePositionManager _SFPM,
```
[116](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L116)
[117](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L117)


</details>

-------
### [N-34] Assembly block creates dirty bits
<a name="N-34"></a>
[To the top](#TOP)

Writing data to the free memory pointer without later updating the free memory pointer will cause there to be dirty bits at that memory location. Not updating the free memory pointer will make it [harder](https://docs.soliditylang.org/en/latest/ir-breaking-changes.html#cleanup) for the optimizer to reason about whether the memory needs to be cleaned before use, which will lead to worse optimizations. Update the free memory pointer and annotate the block (`assembly (\"memory-safe\") { ... }`) to avoid this issue.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 2 instances</summary>


---

	 - contracts/libraries/SafeTransferLib.sol

```solidity
24	        assembly ("memory-safe") {
25	            // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
26	            let p := mload(0x40)
27	
28	            // Write the abi-encoded calldata into memory, beginning with the function selector.
29	            mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)
30	            mstore(add(4, p), from) // Append the "from" argument.
31	            mstore(add(36, p), to) // Append the "to" argument.
32	            mstore(add(68, p), amount) // Append the "amount" argument.
33	
34	            success := and(
35	                // Set success to whether the call reverted, if not we check it either
36	                // returned exactly 1 (can't just be non-zero data), or had no return data.
37	                or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
38	                // We use 100 because that's the total length of our calldata (4 + 32 * 3)
39	                // Counterintuitively, this call() must be positioned after the or() in the
40	                // surrounding and() because and() evaluates its arguments from right to left.
41	                call(gas(), token, 0, p, 100, 0, 32)
42	            )
43	        }
...
55	        assembly ("memory-safe") {
56	            // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
57	            let p := mload(0x40)
58	
59	            // Write the abi-encoded calldata into memory, beginning with the function selector.
60	            mstore(p, 0xa9059cbb00000000000000000000000000000000000000000000000000000000)
61	            mstore(add(4, p), to) // Append the "to" argument.
62	            mstore(add(36, p), amount) // Append the "amount" argument.
63	
64	            success := and(
65	                // Set success to whether the call reverted, if not we check it either
66	                // returned exactly 1 (can't just be non-zero data), or had no return data.
67	                or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
68	                // We use 68 because that's the total length of our calldata (4 + 32 * 2)
69	                // Counterintuitively, this call() must be positioned after the or() in the
70	                // surrounding and() because and() evaluates its arguments from right to left.
71	                call(gas(), token, 0, p, 68, 0, 32)
72	            )
73	        }
```
[24..43](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L24-L43)
[55..73](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/libraries/SafeTransferLib.sol#L55-L73)


</details>

-------
### [N-35] Contract name does not follow the Solidity Style Guide
<a name="N-35"></a>
[To the top](#TOP)

According to the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#contract-and-library-names), contracts and libraries should be named using the CapWords style.

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 2 instances</summary>


---

	 - contracts/tokens/ERC1155Minimal.sol

```solidity
11	abstract contract ERC1155 {
12	    /*//////////////////////////////////////////////////////////////
13	                                 EVENTS
14	    //////////////////////////////////////////////////////////////*/
15	
16	    /// @notice Emitted when only a single token is transferred.
17	    /// @param operator The user who initiated the transfer
18	    /// @param from The user who sent the tokens
19	    /// @param to The user who received the tokens
20	    /// @param id The ERC1155 token id
21	    /// @param amount The amount of tokens transferred
22	    event TransferSingle(
```
[11..22](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L11-L22)

---

	 - contracts/tokens/ERC20Minimal.sol

```solidity
9	abstract contract ERC20Minimal {
10	    /*//////////////////////////////////////////////////////////////
11	                                 EVENTS
12	    //////////////////////////////////////////////////////////////*/
13	
14	    /// @notice Emitted when tokens are transferred
15	    /// @param from The sender of the tokens
16	    /// @param to The recipient of the tokens
17	    /// @param amount The amount of tokens transferred
18	    event Transfer(address indexed from, address indexed to, uint256 amount);
```
[9..18](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L9-L18)


</details>

-------
### [N-36] Remaining eth may not be refunded to users
<a name="N-36"></a>
[To the top](#TOP)

 When a contract function accepts Ethereum and executes a `.call()` or similar function that also forwards Ethereum value, it's important to check for and refund any remaining balance. This is because some of the supplied value may not be used during the call execution due to gas constraints, a revert in the called contract, or simply because not all the value was needed.

If you do not account for this remaining balance, it can become "locked" in the contract. It's crucial to either return the remaining balance to the sender or handle it in a way that ensures it is not permanently stuck. Neglecting to do so can lead to loss of funds and degradation of the contract's reliability. Furthermore, it's good practice to ensure fairness and trust with your users by returning unused funds. 

#### <ins>Proof Of Concept</ins>

<details>

<summary>see 1 instances</summary>


---

	 - contracts/multicall/Multicall.sol

```solidity
12	    function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
```
[12](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/multicall/Multicall.sol#L12)


</details>

-------
### [N-37] Missing zero address check in initializer
<a name="N-37"></a>
[To the top](#TOP)



#### <ins>Proof Of Concept</ins>

<details>

<summary>see 1 instances</summary>


---

	 - contracts/PanopticFactory.sol

```solidity
134	    function initialize(address _owner) public {
```
[134](https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L134)


</details>
