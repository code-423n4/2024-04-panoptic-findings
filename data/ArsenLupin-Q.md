[L-0] Insufficient validation in the tokenId contract. User could accidentaly create the the incorrect Leg / width / optionRatio, which will cause it to stuck in the contract.

# Summary 

validate function is triggered upon burning/minting position, it plays a crucial role in the overall validation functionality. However, the user could face a problems during the minting liquidity if he passed incorrect values during the tokenId creation. This bug is possible because there is no checks during the addLeg function in the tokenId.sol.

# Vulnerability details
During the addLeg creation , user could pass any data that he want, related to the ticks/width/riskPartner/OptionRatio e.t.c. On this step he will not face any problems. However, further along, during the minting liquidity the tokeId.validate() function will stop user, and he couldn't proceed further, which could cause inconveniences and frustration to the user.
One incorrect input would prevent the leg from being minted, and the user will be forced to explore what had happened and what is not correct, which will cause a lot of problems and inconveniences.

It is extremely important at least take into account that the ratio isn't set to 0, because it is used in important calculation such this

```js
uint256 amount = uint256(positionSize) * tokenId.optionRatio(legIndex);
        if (tokenId.asset(legIndex) == 0) {
            return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
        }
```

# Recommended Mitigation Steps
I highly recommend to add basics checks during the leg creation, for example
1. When user set the width, ensure that it is not 0
2. When user create strike, ensure that is not equal to the Min/Max
3. Ensure that during the addOptionRatio, ratio isn't set to 0
4. Ensure that risk partner is set correctly and not equal to yourself
