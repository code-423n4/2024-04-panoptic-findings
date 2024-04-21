## Missing event for critical pokeMedian() function in PanopticPool.sol

## Impact
The pokeMedian() function initializes critical storage variable ```s_miniMedian``` for this contract but is missing an event emission for off-chain monitoring tools to monitor this on-chain change.

## Proof of Concept
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L522-L534

## Tools Used
Manual Analysis

## Recommended Mitigation Steps
Add a UpdatedMedian event and emit that at the end of pokeMedian() function.