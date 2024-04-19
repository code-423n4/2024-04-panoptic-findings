### NOTE: Missing check for address(0) is also identified by 4naly3er; however, the instance mentioned in this report is not detected by it. To verify, you can refer to NC-1 in the 4naly3er report. This note is intended to clarify this as per the QA submission policy.

<details>
 <summary>Submission policy for QA reports</summary>
"Be sure to check the automated findings output and confirm that none of the findings in your QA or Gas report are out of scope, prior to submitting. If you find additional instances of an issue listed in the automated findings report, please note this in your report; otherwise, they will be considered out of scope." 
</details>
<br>

# Non Critical Issues
| ||
|-|:-
| [NC-1](#NC-1) | Missing events for state changes
| [NC-2](#NC-2) | Missing checks for `address(0)` when assigning values to address state variables 
| [NC-3](#NC-3) | Different versions of Solidity are used 
| [NC-4](#NC-4) | High cyclomatic complexity
| [NC-5](#NC-5) | Unlocked Solidity version pragma
| [NC-6](#NC-6) | Redundant expression
| [NC-7](#NC-7) | Unused state variables


## <a name="NC-1"></a>[NC-1] Missing events for state changes

### Issue description
Important events are absent from the contract, impeding transparency, traceability, and integration with external systems.

[CollateralTracker.sol#L1028-L1029](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1028-L1029)
```solidity 
 1028:     s_poolAssets = uint128(uint256(updatedAssets))
 1029:     s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)))
```
[CollateralTracker.sol#L1084-L1085](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1084-L1085)
```solidity
1084: s_poolAssets = uint128(uint256(updatedAssets + realizedPremium))
1085: s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)))
```

### Recommendation
Emit an event for critical parameter changes.

## <a name="NC-2"></a>[NC-2] Missing checks for `address(0)` when assigning values to address state variables

[CollateralTracker.sol#L241](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L241)
```solidity 
241: s_underlyingToken = token0
```
### Recommendation
Check that the address is not zero.

## <a name="NC-3"></a>[NC-3] Different versions of Solidity are used 

### Issue description
The source files have different solidity compiler ranges referenced. This leads to potential security flaws between deployed contracts depending on the compiler version chosen for any particular file. It also greatly increases the cost of maintenance as different compiler versions have different semantics and behavior.

- ^0.8.0 
    - [CallbackLib.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L2)
    - [Constants.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L2)
    - [Errors.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L2)
    - [FeesCalc.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalc.sol#L2)
    - [InteractionHelper.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/InteractionHelper.sol#L2)
    - [Math.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L2)
    - [PanopticMath.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L2)
    - [SafeTransferLib.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L2)
    - [ERC1155Minimal.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC1155Minimal.sol#L2)
    - [ERC20Minimal.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L2)
    - [IDonorNFT.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IDonorNFT.sol#L2)
    - [IERC20Partial.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfaces/IERC20Partial.sol#L2)
    - [LeftRight.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L2)
    - [LiquidityChunk.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LiquidityChunk.sol#L2)
    - [TokenId.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L2)
- ^0.8.18 
    - [CollateralTracker.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L2)
    - [PanopticFactory.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L2)
    - [PanopticPool.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L2)
    - [SemiFungiblePositionManager.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L2)
    - [Multicall.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/multicall/Multicall.sol#L2)

### Recommendation
Use one Solidity version.

## <a name="NC-4"></a>[NC-4] High cyclomatic complexity

### Issue description
High cyclomatic complexity in the codebase complicates maintenance and increases the potential for errors.

- [Math.sol#L128-L181](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L128-L181)
- [TokenIdLibrary.sol#L500-L571](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L500-L571)

### Recommendation
Reduce cyclomatic complexity by splitting the function into several smaller subroutines.

## <a name="NC-5"></a>[NC-5] Unlocked Solidity version pragma

### Issue description 
Some files use Solidity ^0.8.0, allowing compilation with any version from 0.8.0 up to the latest release. This could cause issues if deployed with a different Solidity version from testing. Using outdated versions risks exposing code to [known vulnerabilities](https://soliditylang.org/blog/category/security-alerts/), so it's advisable to deploy with the latest Solidity release.

### Files: 
- [CallbackLib.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/CallbackLib.sol#L2)
- [Constants.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Constants.sol#L2)
- [Errors.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Errors.sol#L2)
- [FeesCalc.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/FeesCalcsol#L2)
- [InteractionHelper.sol#2](https://github.com/code-423n4/2024-04-panopticblob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/librariesInteractionHelper.sol#L2)
- [Math.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L2)
- [PanopticMath.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMathsol#L2)
- [SafeTransferLib.sol#2](https://github.com/code-423n4/2024-04-panopticblob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/librariesSafeTransferLib.sol#L2)
- [ERC1155Minimal.sol#2](https://github.com/code-423n4/2024-04-panopticblob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokensERC1155Minimal.sol#L2)
- [ERC20Minimal.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimalsol#L2)
- [IDonorNFT.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfacesIDonorNFT.sol#L2)
- [IERC20Partial.sol#2](https://github.com/code-423n4/2024-04-panopticblob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/interfacesIERC20Partial.sol#L2)
- [LeftRight.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/LeftRight.sol#L2)
- [LiquidityChunk.sol#2](https://github.com/code-423n4/2024-04-panopticblob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/typesLiquidityChunk.sol#L2)
- [TokenId.sol#2](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/types/TokenId.sol#L2)

### Recommendation
Consider locking the version pragma to the same Solidity version used during development and testing. Also, consider setting this version to be the latest release, as suggested in the [official guidance](https://docs.soliditylang.org/en/latest/index.html#solidity)

## <a name="NC-6"></a>[NC-6] Redundant expression

### Issue description 
The code contains unnecessary `required` statements that do not contribute to its functionality

[CollateralTracker.sol#L1350C29-L1350C30](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L1350C29-L1350C30)

### Recommendation
Remove redundant statements if they congest code but offer no value.

## <a name="NC-7"></a>[NC-7] Unused state variables

### Issue description 
Unused state variables in the contract may increase the gas cost of deployments and transactions without providing any functionality or value.


 - [Math.sol#15](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/Math.sol#L15)
- [PanopticMath.sol#23](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/PanopticMath.sol#L23)

### Recommendation
Remove unused state variables.
