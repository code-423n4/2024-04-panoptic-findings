#**Initializer could be frontrunned.**

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L134


Mitigation step: 
The initializer should be called using a constructor.