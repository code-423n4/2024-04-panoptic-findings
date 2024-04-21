# [L-1] The to address was not checked
## Detail
When the 'to' address is the 0x00 , the contract cannot detect it and returns an error message.
## Instances
```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L103

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L122

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L61

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L49
```
## Suggestion
```solidity
error ERC20InvalidReceiver(address to);

if (to == address(0)) {
    revert ERC20InvalidReceiver(address(0));
}
```


# [L-2] Missing error message
## Detail
When the transferFrom function of the CollateralTracker contract is called, since the balance of allowance and 'from' is not checked, it is impossible to determine whether the allowance or balance is insufficient.
## Instances
```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/tokens/ERC20Minimal.sol#L81C14-L81C26
```
## Suggestion
Check the balance of allowance and 'from', if insufficient, roll back and return an error message


# [L-3] The to address was not checked
## Detail
When calling the safeTransferFrom function of SemiFungiblePositionManager, if the 'to' address is 0x00, because the code.length of the 0x00 address == 0, the transfer will be successful at this time. This time, the NFT is permanently locked at the 0x00 address.
## Instances
```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L540
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L566
```
## Suggestion
```
    if (to == address(0)) {
        revert ERC1155InvalidReceiver(address(0));
    }
``` 

### Time spent:
20 hours