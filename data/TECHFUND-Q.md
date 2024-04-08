### 1) SemiFungiblePositionManager::safeBatchTransferFrom function lacks input validation checks for length of ids and amounts array. The function drives the logic based on ids length which could results into two invalid scenarios.

- amounts array is longer than ids array, in which case, the amounts passed will be ignored

- amounts array is shorted than ids array, in which case, the logic will throw index out of bounds exception. 

### 2) CollateralTracker::deposit() and mint() functions could result in DOS
The previewDeposit() and previewMint() functions computes the shares and assets 
with reference to DECIMALS and COMMISSION_FEE. With decimals being constant and COMMISSION_FEE being an input as parameter to constructor, there is no valid for COMMISSION_FEE to be less than DECIMALS.

Because of which,if the COMMISSION_FEE value passed in the constructor is greater than decimals, it will result in underflow during the computation of shares or assets in the preview functions.

code snippets:
```
   uint256 internal constant DECIMALS = 10_000;


    function previewDeposit(uint256 assets) public view returns (uint256 shares) 
    {
      
        unchecked {
            shares = Math.mulDiv(
    ==>     assets * (DECIMALS - COMMISSION_FEE),
                totalSupply,
                totalAssets() * DECIMALS
            );
        }
    } 

    function previewMint(uint256 shares) public view returns (uint256 assets) {
        unchecked {
            assets = Math.mulDivRoundingUp(
                shares * DECIMALS,
                totalAssets(),
   ==>          totalSupply * (DECIMALS - COMMISSION_FEE)
            );
        }
    }
```
Solution:
Add validation in the constructor to ensure that COMMISSION_FEE is less than DECIMALS, else revert. 
