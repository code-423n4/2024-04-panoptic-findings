


# LOW RISK 

| Number | Issue | Instences |
|--------|-------|-----------|
|[L--01]| Approve type(uint256).max may not work with some tokens | 4 |
|[L--02]| Signature use at deadlines should be allowed | 3 |
|[L--03]| Use forceApprove in place of approve | 4 |
|[L--04]| Consider bounding input array length | 6 |
|[L--05]| constructor/initialize function lacks parameter validation | 1 |

## [L-01] Approve type(uint256).max may not work with some tokens

The approve function in ERC-20 tokens allows a user to permit another user or contract to spend tokens on their behalf. Setting the approval to type(uint256).max is often used as a way to grant an indefinite approval, as this value is the maximum possible value of a uint256 variable in Solidity.

However, some tokens may not function as expected when type(uint256).max is used. These tokens may have an atypical implementation of the transferFrom function, which is used in combination with approve. This function might behave differently when confronted with such a high allowance, possibly due to custom logic in the contract that wasn't designed to handle these edge cases.

Moreover, tokens that have a built-in burning or fees mechanism could behave unpredictably when the maximum allowance is set. This can lead to potential vulnerabilities or misinterpretations of contract behavior.

Resolution: It's advisable to be conservative with the approve function and only approve the specific amount of tokens that need to be spent for the specific operation you're performing. If you need to provide an extensive allowance, ensure you've thoroughly analyzed the token contract to understand how it behaves with high allowances. Alternatively, consider implementing a mechanism in your contract to handle token allowances in a more dynamic way, adjusting them as needed for each operation, rather than relying on a single indefinite approval.

```solidity
file: tree/main/contracts/libraries/InteractionHelper.sol

32   IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33   IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36   IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37  IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L32

## [L-02] Signature use at deadlines should be allowed

According to EIP-2612 (https://github.com/ethereum/EIPs/blob/71dc97318013bf2ac572ab63fab530ac9ef419ca/EIPS/eip-2612.md?plain=1#L58), signatures used on exactly the deadline timestamp are supposed to be allowed. While the signature may or may not be used for the exact EIP-2612 use case (transfer approvals), for consistency's sake, all deadlines should follow this semantic. If the timestamp is an expiration rather than a deadline, consider whether it makes more sense to include the expiration timestamp as a valid timestamp, as is done for deadlines.

```solidity
file: main/contracts/libraries/PanopticMath.sol

183  if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

227  (block.timestamp << 216) +

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L183

```solidity
file: main/contracts/PanopticPool.sol

309  (uint256(block.timestamp) << 216) +

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L309

## [L-03] Use forceApprove in place of approve

The forceApprove function is a specialized solution addressing the issues that arise with non-standard ERC-20 tokens, such as USDT, which exhibit non-standard behavior in their approve function. These tokens may necessitate setting the allowance to 0 before changing it, may not return a boolean value from approve calls, or may return false instead of reverting on failure. OpenZeppelin's SafeERC20 library includes a forceApprove method to safely handle these peculiarities, ensuring that smart contracts can interact with such tokens without transaction failures. It rectifies inconsistencies by ensuring that all token interactions, including approvals, adhere to expected standards, even when the underlying tokens do not.

```solidity
file: tree/main/contracts/libraries/InteractionHelper.sol

32   IERC20Partial(token0).approve(address(sfpm), type(uint256).max);

33   IERC20Partial(token1).approve(address(sfpm), type(uint256).max);

36   IERC20Partial(token0).approve(address(ct0), type(uint256).max);

37   IERC20Partial(token1).approve(address(ct1), type(uint256).max);

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L32

## [L-04] Consider bounding input array length

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to require() that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.


```solidity
file:  main/contracts/multicall/Multicall.sol

14  for (uint256 i = 0; i < data.length; ) {
            (bool success, bytes memory result) = address(this).delegatecall(data[i]);

            if (!success) {
                // Bubble up the revert reason
                // The bytes type is ABI encoded as a length-prefixed byte array
                // So we simply need to add 32 to the pointer to get the start of the data
                // And then revert with the size loaded from the first 32 bytes
                // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
                // However, we have chosen to simply replicate the the normal behavior of the call
                // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
                assembly ("memory-safe") {
                    revert(add(result, 32), mload(result))
                }
            }

            results[i] = result;

            unchecked {
                ++i;
            }
        }

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L14-L35


```solidity
file: main/contracts/SemiFungiblePositionManager.sol

575  for (uint256 i = 0; i < ids.length; ) {
            if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
            registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
            unchecked {
                ++i;
            }
        }

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L575-L581

```solidity
file: main/contracts/tokens/ERC1155Minimal.sol

187  for (uint256 i = 0; i < owners.length; ++i) {
                balances[i] = balanceOf[owners[i]][ids[i]];
            }
```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L187-L189

```solidity
file: tree/main/contracts/PanopticPool.sol

802 for (uint256 i = 0; i < positionIdList.length; ) {
            LeftRightSigned paidAmounts;
            (paidAmounts, premiasByLeg[i]) = _burnOptions(
                commitLongSettled,
                positionIdList[i],
                owner,
                tickLimitLow,
                tickLimitHigh
            );
            netPaid = netPaid.add(paidAmounts);
            unchecked {
                ++i;
            }
        }

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L802-L815


```solidity
file: main/contracts/libraries/PanopticMath.sol

781  for (uint256 i = 0; i < positionIdList.length; ++i) {
                TokenId tokenId = positionIdList[i];
                uint256 numLegs = tokenId.countLegs();
                for (uint256 leg = 0; leg < numLegs; ++leg) {
                    if (tokenId.isLong(leg) == 1) {
                        longPremium = longPremium.sub(premiasByLeg[i][leg]);
                    }
                }
            }

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L781-L789


```solidity
file: main/contracts/libraries/FeesCalc.sol

51 for (uint256 k = 0; k < positionIdList.length; ) {
            TokenId tokenId = positionIdList[k];
            uint128 positionSize = userBalance[tokenId].rightSlot();
            uint256 numLegs = tokenId.countLegs();
            for (uint256 leg = 0; leg < numLegs; ) {
                LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
                    tokenId,
                    leg,
                    positionSize
                );

                (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
                    atTick,
                    liquidityChunk
                );

                if (tokenId.isLong(leg) == 0) {
                    unchecked {
                        value0 += int256(amount0);
                        value1 += int256(amount1);
                    }
                } else {
                    unchecked {
                        value0 -= int256(amount0);
                        value1 -= int256(amount1);
                    }
                }

                unchecked {
                    ++leg;
                }
            }
            unchecked {
                ++k;
            }
        }
    }

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L51-L87

## [L-05] constructor/initialize function lacks parameter validation

Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

```solidity
file: main/contracts/PanopticFactory.sol

115  constructor(
        address _WETH9,
        SemiFungiblePositionManager _SFPM,
        IUniswapV3Factory _univ3Factory,
        IDonorNFT _donorNFT,
        address _poolReference,
        address _collateralReference
    ) {
        WETH = _WETH9;
        SFPM = _SFPM;
        DONOR_NFT = _donorNFT;
        // We store the Uniswap Factory contract - later we can use this to verify uniswap pools
        UNIV3_FACTORY = _univ3Factory;
        POOL_REFERENCE = _poolReference;
        COLLATERAL_REFERENCE = _collateralReference;
    }

```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L115-L130
