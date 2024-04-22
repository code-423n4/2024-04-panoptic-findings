# [L-01]`CollateralTracker.totalAssets` doesn't follow the documents 
File:
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L370-L374

`function CollateralTracker.totalAssets` is defined in [CollateralTracker.sol#L370-L374](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L370-L374)
```solidity
 370     function totalAssets() public view returns (uint256 totalManagedAssets) {
 371         unchecked {
 372             return s_poolAssets + s_inAMM;
 373         }
 374     }
```
But quoting from [API documents](https://panoptic.xyz/docs/panoptic-protocol/design#total-balance):
>the amount of funds moved from the PanopticPool to Uniswap (_inAMM()), and the amount of fees that have been collected but are currently locked (_lockedFees()).


# [L-02]`CollateralTracker.maxMint's` implementation isn't correct
File:
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L444-L448

While containing `COMMISSION_FEE`, in [CollateralTracker.maxMint](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L444-L448), the function is implementation as:
```solidity
    function maxMint(address) external view returns (uint256 maxShares) {
        unchecked {
            return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
        }
    }
```
which means:
>maxShares = Math.mulDiv(assets, totalSupply, totalAssets()) * DECIMALS / (DECIMALS + COMMISSION_FEE);

But all others functions calculates [shares as](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L399-L408)
>shares = Math.mulDiv(assets * (DECIMALS - COMMISSION_FEE), totalSupply,totalAssets() * DECIMALS);

# [L-03] `SemiFungiblePositionManager.swapInAMM` uses constant as slippage protection
File:
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L837-L845

In [SemiFungiblePositionManager.sol#L837-L845](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L837-L845), `Constants.MIN_V3POOL_SQRT_RATIO` and `Constants.MAX_V3POOL_SQRT_RATIO` is used as slippage protection, which might cause sandwich attack

# [L-04] `PanopticFactory.minePoolAddress` might return wrong results.
File:
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L299-L301

In [PanopticFactory.minePoolAddress](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L289-L326),while calculates `maxSalt`, __unchecked__ is used to wrap `maxSalt = uint256(salt) + loops;`
The issue is that if `uint256(salt) + loops > type(uint).max`, the function will not revert because of __unchecked__, instead, it'll overwrite the slot.
In such case, the function will not fall into the [for loop](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L303-L325)