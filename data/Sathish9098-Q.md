## QA Report

##

## [L-] Risks of Unchecked Fee Division for Small Values 

When a fee value is less than 100 results in ``_poolFee`` becoming 0 due to integer division in Solidity, it can pose several risks to the protocol, particularly in financial or transactional systems where fees are crucial for operational integrity.

If ``_poolFee`` becomes zero due to low fee values, the protocol might not collect any fees on certain transactions. This loss of revenue could be significant if a large volume of transactions involves small amounts, potentially impacting the economic model of the protocol.

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

 // cache the pool fee in basis points
        uint24 _poolFee;
        unchecked {
            _poolFee = fee / 100;
        }

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L246-L250




##

## [NC-] Unnecessary cache of ``_poolFee``

```solidity
FILE: 2024-04-panoptic/contracts/CollateralTracker.sol

 // cache the pool fee in basis points
        uint24 _poolFee;
        unchecked {
            _poolFee = fee / 100;
        }

```
https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/CollateralTracker.sol#L246-L250


NC-1	Missing checks for address(0) when assigning values to address state variables	7
NC-2	Array indices should be referenced via enums rather than via numeric literals	24
NC-3	Use string.concat() or bytes.concat() instead of abi.encodePacked	12
NC-4	constants should be defined rather than using magic numbers	200
NC-5	Control structures do not follow the Solidity Style Guide	146
NC-6	Unused error definition	33
NC-7	Events that mark critical parameter changes should contain both the old and the new value	2
NC-8	Function ordering does not follow the Solidity style guide	5
NC-9	Functions should not be longer than 50 lines	118
NC-10	Change int to int256	10
NC-11	Lack of checks in setters	2
NC-12	Lines are too long	1
NC-13	type(uint256).max should be used instead of 2 ** 256 - 1	2
NC-14	Incomplete NatSpec: @param is missing on actually documented functions	2
NC-15	Incomplete NatSpec: @return is missing on actually documented functions	2
NC-16	Use a modifier instead of a require/if statement for a special msg.sender actor	13
NC-17	Constant state variables defined more than once	2
NC-18	Adding a return statement when the function defines a named return variable, is redundant	34
NC-19	require() / revert() statements should have descriptive reason strings	74
NC-20	Take advantage of Custom Error's return value property	60
NC-21	Use scientific notation (e.g. 1e18) rather than exponentiation (e.g. 10**18)	1
NC-22	Strings should use double quotes rather than single quotes	2
NC-23	Contract does not follow the Solidity style guide's suggested layout ordering	6
NC-24	Use Underscores for Number Literals (add an underscore every 3 digits)	9
NC-25	Internal and private variables and functions names should begin with an underscore	132
NC-26	Event is missing indexed fields	12
NC-27	Constants should be defined rather than using magic numbers	33
NC-28	public functions not called by the contract should be declared external instead	9
NC-29	Variables need not be initialized to zero	31

L-1	approve()/safeApprove() may revert if the current approval is not zero	4
L-2	Some tokens may revert when zero value transfers are made	2
L-3	Missing checks for address(0) when assigning values to address state variables	7
L-4	decimals() is not a part of the ERC-20 standard	1
L-5	Deprecated approve() function	4
L-6	Do not leave an implementation contract uninitialized	1
L-7	Division by zero not prevented	18
L-8	External calls in an un-bounded for-loop may result in a DOS	13
L-9	Initializers could be front-run	1
L-10	Prevent accidentally burning tokens	24
L-11	Possible rounding issue	6
L-12	Loss of precision	12
L-13	Solidity version 0.8.20+ may not work on other chains due to PUSH0	15
L-14	Use Ownable2Step.transferOwnership instead of Ownable.transferOwnership	1
L-15	File allows a version of solidity that is susceptible to an assembly optimizer bug	11
L-16	symbol() is not a part of the ERC-20 standard	3
L-17	Consider using OpenZeppelin's SafeCast library to prevent unexpected overflows when downcasting	65
L-18	Unsafe ERC20 operation(s)	6
L-19	Upgradeable contract not initialized	19

M-1	_safeMint() should be used rather than _mint() wherever possible	1
M-2	Library function isn't internal or private	13
M-3	Return values of transfer()/transferFrom() not checked	2
M-4	Unsafe use of transfer()/transferFrom() with IERC20	2



