# [L-01]`CollateralTracker.totalAssets` doesn't follow the documents 
## Link:
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
## link 
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L444-L448
## Proof of Concept
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
