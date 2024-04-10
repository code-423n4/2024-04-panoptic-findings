shares amount from the allowance granted by the owner to the msg.sender.If allowed is already 0 and shares is greater than 0, the subtraction operation is  `allowed - shares` will result in an underflow

https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L544C1-L545C1

if (msg.sender != owner) {
    uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.

    if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
}

Always ensure that the subtraction operation allowed - shares will only be executed if allowed is greater than or equal to shares, thus preventing the underflow issue