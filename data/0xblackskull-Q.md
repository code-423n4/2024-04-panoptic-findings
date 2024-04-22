#### ERC20Minimal.sol
- ERC20Minimal is not protected for the ERC20 approval race condition, run in slither
  `slither-check-erc --erc ERC20 contracts/tokens/ERC20Minimal.sol  ERC20Minimal`
```
# Check ERC20Minimal

## Check functions
[✓] totalSupply() is present
        [✓] totalSupply() -> (uint256) (correct return type)
        [✓] totalSupply() is view
[✓] balanceOf(address) is present
        [✓] balanceOf(address) -> (uint256) (correct return type)
        [✓] balanceOf(address) is view
[✓] transfer(address,uint256) is present
        [✓] transfer(address,uint256) -> (bool) (correct return type)
        [✓] Transfer(address,address,uint256) is emitted
[✓] transferFrom(address,address,uint256) is present
        [✓] transferFrom(address,address,uint256) -> (bool) (correct return type)
        [✓] Transfer(address,address,uint256) is emitted
[✓] approve(address,uint256) is present
        [✓] approve(address,uint256) -> (bool) (correct return type)
        [✓] Approval(address,address,uint256) is emitted
[✓] allowance(address,address) is present
        [✓] allowance(address,address) -> (uint256) (correct return type)
        [✓] allowance(address,address) is view
[ ] name() is missing (optional)
[ ] symbol() is missing (optional)
[ ] decimals() is missing (optional)

## Check events
[✓] Transfer(address,address,uint256) is present
        [✓] parameter 0 is indexed
        [✓] parameter 1 is indexed
[✓] Approval(address,address,uint256) is present
        [✓] parameter 0 is indexed
        [✓] parameter 1 is indexed


        [ ] ERC20Minimal is not protected for the ERC20 approval race condition

```
- Revert on transfer to the zero address
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L61-L73
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L81C14-L97
- Revert on zero value transfers
   https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L61-L73
   https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC20Minimal.sol#L81C14-L97

#### Missing require check for token0 != token1
- SemiFungiblePositionManager::initializeAMMPool
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L350
- CollateralTracker.sol::startToken
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L221
- PanopticFactory::deployNewPool
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticFactory.sol#L210-L215
- PanopticPool::startPool
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L297
  
#### Missing require check for collateralTracker0 != collateralTracker1
- PanopticPool::startPool
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/PanopticPool.sol#L291-L297
#### Missing array length check
- safeBatchTransferFrom()
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/SemiFungiblePositionManager.sol#L566-L584
- balanceOfBatch()
  https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/tokens/ERC1155Minimal.sol#L178-L191
