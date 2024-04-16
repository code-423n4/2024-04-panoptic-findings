## Optimize gas by using only named returns

The Solidity compiler can generate more efficient bytecode when using named returns. It's recommended to replace anonymous returns with named returns for potential gas savings.

Example:

    /// 985 gas cost
    function add(uint256 x, uint256 y) public pure returns (uint256) {
        return x + y;
    }
    /// 941 gas cost
    function addNamed(uint256 x, uint256 y) public pure returns (uint256 res) {
        res = x + y;
    }

issue instances:

File: contracts/CollateralTracker.sol
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L310

File: /contracts/PanopticFactory.sol
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L340

File: /contracts/PanopticPool.sol
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L682
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L710

File: /contracts/SemiFungiblePositionManager.sol
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/SemiFungiblePositionManager.sol#L1457
