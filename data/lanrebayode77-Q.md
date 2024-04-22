## L1 Misleading comment

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L1692
``` solidity 
 // T: totalLiquidityBeforeMint
```
It should be ``` // T: totalLiquidityBeforeBurn``` since it an update function after burning a position not minting.  
``` solidity
// T: totalLiquidityBeforeBurn
```