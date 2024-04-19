# [L-01] Lack 0f 0 amount checks
The protocol lacks for checking of 0 amount while deposit/withdraw/redeem and other places
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L417
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L531
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L591
There maybe be other instances where there are lack of amount 0 checks
## Recommendation
require(amount >0, "very less amount")

# [L-02] Lack 0f 0 address checks
The protocol lacks for checking of 0 address while performing certain operations 

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L417
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L531
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L591
There maybe be other instances where there are lack of address 0 checks
## Recommendation
require(amount >0, "very less amount")

# [L-03] Missing check that token0 and token1 are different
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticFactory.sol#L210
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/PanopticPool.sol#L291
The problem is that protocol doesn't really check if both token address are different
## Recommendation
require(token0 != token1, "same address token")

# [L-04] While transferring ownership, it is recommended to check if the owner is not the currentOwner

A malicious owner can change the ownership again to themselves
```
 function transferOwnership(address newOwner) external {
        address currentOwner = s_owner;

        if (msg.sender != currentOwner) revert Errors.NotOwner();

        s_owner = newOwner;

        emit OwnershipTransferred(currentOwner, newOwner);
    }
```

## Recommended Mitigation Steps
Also check if the `prevOwner != newOwner` before transferring ownership


