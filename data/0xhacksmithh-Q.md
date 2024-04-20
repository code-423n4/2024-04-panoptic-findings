


## NonCritical Findings

|    | Issue | Instances |
|----|-------|:---------:|

| [N-01] | Non-library/interface files should use fixed compiler versions, not floating ones | |
| [N-02] | Missing Event Emission After Critical Initialize() Function | |
| [N-03] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability | |
| [N-04] | Consider returning a `struct` rather than having multiple `return` values | |
| [N-05] | Consider using `delete` rather than assigning `false` to clear values | |
| [N-06] | Consider providing a ranged getter for array state variables | |
| [N-07] | Consider using named returns | |
| [N-08] | Expressions for constant values should use `immutable` rather than `constant` | |
| [N-09] | Events are missing sender information | |
| [N-10] | Contract should expose an `interface` | |
| [N-11] | Contract uses both `require()`/`revert()` as well as custom errors | |
| [N-12] | Adding a `return` statement when the function defines a named return variable, is redundant | 1 |
| [N-13] | Upgrade `openzeppelin` to the Latest Version - 5.0.0 | |
| [N-14] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function | |
| [N-15] | Event is not properly `indexed` | |
| [N-16] | Consider Adding Emergency-Stop Functionality | |
| [N-17] | Consider adding a block/deny-list | |
| [N-18] | Consider making contracts `Upgradeable` | |
| [N-19] | Events that mark critical parameter changes should contain both the old and the new value | |
| [N-20] | Using Low-Level Call for Transfers | |
| [N-21] | Consider bounding input array length | |
| [N-22] | Constants in comparisons should appear on the left side | |
| [N-23] | `public` functions not called by the contract should be declared `external` instead | |
| [N-24] | Complex casting | |
| [N-25] | Unused Event Declarations | |
| [N-26] | `else`-block not required | |
| [N-27] | Polymorphic functions make security audits more time-consuming and error-prone | |
| [N-28] | Unused import | |
| [N-29] | `if`-statement can be converted to a ternary | |
| [N-30] | Consider using named mappings | |
| [N-31] | Use of `override` is unnecessary | |
| [N-32] | Setters should prevent re-setting of the same value | |
| [N-33] | Use Unchecked for Divisions on Constant or Immutable Values | |
| [N-34] | Explicit Visibility Recommended in Variable/Function Definitions | |
| [N-35] | Contracts should have full test coverage | |
| [N-36] | Implement Formal Verification Proofs to Improve Security | |


### [L-01] Low Level Calls to Custom Addresses

Contracts should avoid making low-level calls to custom addresses, especially if these calls are based on address parameters in the function. 
Such behavior can lead to unexpected execution of untrusted code. Instead, consider using Solidity's high-level function calls or contract interactions.




### [N-02] Missing Event Emission After Critical Initialize() Function

Emitting an initialization event offers clear, on-chain evidence of the contract's initialization state, enhancing transparency and auditability. This practice aids users and developers in accurately tracking the contract's lifecycle, pinpointing the precise moment of its initialization. Moreover, it aligns with best practices for event logging in smart contracts, ensuring that significant state changes are both observable and verifiable through emitted events.



### [N-03] Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct, for readability

Combining multiple address/ID mappings into a single mapping to a struct can enhance code clarity and maintainability. Consider refactoring multiple mappings into a single mapping with a struct for cleaner code structure. This arrangement also promotes a more organized contract structure, making it easier for developers to navigate and understand.



### [N-04] Consider returning a struct rather than having multiple return values

Functions that return many variables can become difficult to read and maintain. Using a struct to encapsulate these return values can improve code readability, increase reusability, and reduce the likelihood of errors. Consider refactoring functions that return more than three variables to use a struct instead.




### [N-05] Consider using delete rather than assigning false to clear values

The use of the delete keyword is recommended over simply assigning values to false when you intend to reset the state of a variable. The delete keyword more closely aligns with the semantic intent of clearing or resetting a variable. This practice also makes the code more readable and highlights the change in state, which may encourage a more thorough audit of the surrounding logic.



### [N-06] Consider providing a ranged getter for array state variables

While the compiler automatically provides a getter for accessing single elements within a public state variable array, it doesn't provide a way to fetch the whole array, or subsets thereof. Consider adding a function to allow the fetching of slices of the array, especially if the contract doesn't already have multicall functionality.



### [N-07] Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is ideal for named returns.



### [N-08] Expressions for constant values should use immutable rather than constant
While it does not save gas for some simple binary expressions because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between constant variables and immutable variables, and they should each be used in their appropriate contexts. constants should be used for literal values written into the code, and immutable variables should be used for expressions, or values calculated in, or passed into the constructor.



### [N-09] Consider using named function arguments

When calling functions in external contracts with multiple arguments, consider using named function parameters, rather than positional ones.




### [N-10] Events are missing sender information

Events should include the sender information when emitted in public or external functions for better traceability.




### [N-11] Leverage Recent Solidity Features with 0.8.23

The recent updates in Solidity provide several features and optimizations that, when leveraged appropriately, can significantly improve your contract's code clarity and maintainability. Key enhancements include the use of push0 for placing 0 on the stack for EVM versions starting from "Shanghai", making your code simpler and more straightforward. Moreover, Solidity has extended NatSpec documentation support to enum and struct definitions, facilitating more comprehensive and insightful code documentation.

Additionally, the re-implementation of the UnusedAssignEliminator and UnusedStoreEliminator in the Solidity optimizer provides the ability to remove unused assignments in deeply nested loops. This results in a cleaner, more efficient contract code, reducing clutter and potential points of confusion during code review or debugging. It's recommended to make full use of these features and optimizations to enhance the robustness and readability of your smart contracts.




### [N-12] Contract should expose an interface

Exposing an interface in a smart contract allows for easier integration by other projects and developers. Without an interface, there's a risk that other projects will have to develop non-standard variants to interact with your contract. It's highly recommended to define an interface for clearer and more robust collaboration.




### [N-13] Contract uses both require()/revert() as well as custom errors

The contract uses both require()/revert() and custom errors for error handling.

It's recommended to use a consistent approach for error handling in a single file.




### [N-14] Adding a return statement when the function defines a named return variable, is redundant

Functions in Solidity can use named return variables which can enhance readability and reduce the complexity of the code. When using named return variables, a return statement without any parameters is implicitly added to the end of the function. This means that explicitly writing return in a function that uses named return variables is redundant. This redundancy could lead to confusion and misinterpretation of the function's behavior, particularly for developers who are new to the Solidity language or to the codebase.

Moreover, explicitly stating the return statement with the named variables might give the impression that the function could have different exit points or that it might return different values, which is not the case here. Therefore, removing these redundant return statements can lead to cleaner, more maintainable code with reduced cognitive load for developers. This helps in understanding the flow and the logic of the function at a quick glance and aids in faster debugging and fewer mistakes.




### [N-15] Upgrade openzeppelin to the Latest Version - 5.0.0
These contracts import contracts from @openzeppelin/contracts but they are not using the latest version. For more information, please visit: OpenZeppelin GitHub Releases It is recommended to always use the latest version to take advantage of updates and security fixes.




### [N-16] Event is not properly indexed

Index event fields make the field more quickly accessible to off-chain tools that parse events. This is especially useful when it comes to filtering based on an address. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Where applicable, each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three applicable fields, all of the applicable fields should be indexed.




### [N-17] Consider Adding Emergency-Stop Functionality

Smart contracts that hold significant value, interact with external contracts, or have complex logic should include an emergency-stop mechanism for added security. This allows pausing certain contract functionalities in case of emergencies, mitigating potential damages.

This contract seems to lack such a mechanism. Implementing an emergency stop can enhance contract security and reliability.




### [N-18] Consider adding a block/deny-list

While adding a block or deny-list may increase the level of centralization in the contract, it provides an additional layer of security by preventing hackers from using stolen tokens or carrying out other malicious activities.

Although it's a trade-off, a block or deny-list can help improve the overall security posture of the contract.



### [N-19] Consider making contracts Upgradeable

Contract uses a non-upgradeable design. Transitioning to an upgradeable contract structure is more aligned with contemporary smart contract practices. This approach not only enhances flexibility but also allows for continuous improvement and adaptation, ensuring the contract stays relevant and robust in an ever-evolving ecosystem.




### [N-20] Events that mark critical parameter changes should contain both the old and the new value

When emitting events that signify critical changes in parameters, it's important to include both the old and new values.

This aids in auditability, providing more complete information about the state change. It's especially necessary when the new value isn't required to be different from the old one, as this prevents ambiguity in event logs.




### [N-21] Using Low-Level Call for Transfers

Directly using low-level calls for Ether transfers can introduce vulnerabilities and obscure the intent of your transfers. Adopt modern Solidity best practices by switching to recognized libraries like SafeTransferLib.safeTransferETH or Address.sendValue. This ensures safer transactions, enhances code clarity, and aligns with the standards of the Solidity community.




### [N-22] Consider bounding input array length

The functions in question operate on arrays without established boundaries, executing function calls for each of their entries. If these arrays become excessively long, a function might revert due to gas constraints. To enhance user experience, consider incorporating a require() statement that enforces a sensible maximum array length. This approach can avoid unnecessary computational work and ensure smoother transactions.




### [N-23] Constants in comparisons should appear on the left side

Placing constants on the left side of comparison statements can help prevent accidental assignments and improve code readability. In languages like C, placing constants on the left can protect against unintended assignments that would be treated as true conditions, leading to bugs. Although Solidity does not have this specific issue, using the same practice can still be beneficial for code readability and consistency.

Consider placing constants on the left side of comparison operators like ==, !=, <, >, <=, and >=."




### [N-24] public functions not called by the contract should be declared external instead
Contracts are allowed to override their parents' functions and change the visibility from external to public. If a public function is not called internally within the contract, it should be declared as external to save gas.




### [N-25] Complex casting

Complex casting in Solidity contracts can introduce both readability issues and potential for overflows. Whenever multiple casts are found, consider whether the complexity is necessary. If so, it is strongly recommended to add inline comments to explain why these casts are needed and to assure that no overflows are introduced.



### [N-26] Equal block.timestamp Cases Not Handled

Solidity code that checks if block.timestamp is greater than a certain variable but fails to handle the case when block.timestamp is equal to the variable may lead to unintended behaviors and potential vulnerabilities.

To ensure correct and secure function execution, it's recommended to include checks for cases where block.timestamp equals the compared variable.




### [N-27] else-block not required

In Solidity, if an if block contains a return statement, subsequent else blocks become unnecessary. This is because the return statement halts the execution of the function at that point, making any else conditions redundant. Therefore, omitting else after such if blocks can lead to cleaner and more readable code without any change in the functionality.




### [N-28] Polymorphic functions make security audits more time-consuming and error-prone

While function overriding allows for functions with the same name to coexist, it's advisable to avoid this practice for the sake of readability and maintainability.

Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the chance of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function but also helps prevent unintended function calls or incorrect overriding.




### [N-29] Unused import

The contract contains import statements for libraries or other contracts that are not utilized within the code. Excessive or unused imports can clutter the codebase, leading to inefficiency and potential confusion. Consider removing any imports that are not essential to the contract's functionality.




### [N-30] if-statement can be converted to a ternary

The ternary operator provides a shorthand way to write if / else statements. It can improve readability and reduce the number of lines of code. Traditional if / else statements, particularly those spanning only a one lines, could potentially be refactored using the ternary operator.




### [N-31] Consider using named mappings

As of Solidity version 0.8.18, it is possible to use named mappings to clarify the purpose of each mapping in the code. It is recommended to use this feature for better code readability and maintainability.

More information: Solidity 0.8.18 Release Announcement[https://blog.soliditylang.org/2023/02/01/solidity-0.8.18-release-announcement/]




### [N-32] Use of override is unnecessary

In Solidity version 0.8.8 and later, the use of the override keyword becomes superfluous when a function is overriding solely from an interface and the function isn't present in multiple base contracts. Previously, the override keyword was required as an explicit indication to the compiler. However, this is no longer the case, and the extraneous use of the keyword can make the code less clean and more verbose.

Solidity documentation on Function Overriding.[https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding]



### [N-33] Setters should prevent re-setting of the same value

Setter functions should include a condition to check if the new value being assigned is different from the current value. This practice prevents redundant state changes and the emission of unnecessary events, ensuring that changes only occur when actual updates to the values are made.

This not only helps to maintain the integrity of the contract's state but also keeps the event logs cleaner and more meaningful by avoiding the recording of identical consecutive values. Such an approach can improve the clarity and efficiency of debugging and data tracking processes.



### [N-34] NatSpec: Contract declarations should have @title tags

NatSpec comments offer an intuitive way to understand the core purpose of a smart contract. Especially, the @title tag serves as a brief descriptor of the contract's function or intent. In this Solidity file, the @title directive seems to be overlooked. Incorporating the @title tag gives readers a concise overview, thus enhancing clarity. Refer to NatSpec Documentation[https://docs.soliditylang.org/en/develop/natspec-format.html]



### [N-35] Use Unchecked for Divisions on Constant or Immutable Values

Unsigned divisions on constant or immutable values do not result in overflow. Therefore, these operations can be marked as unchecked, optimizing gas usage without compromising safety.

For instance, if a is an unsigned integer and b is a constant or immutable, a / b can be safely rewritten as: unchecked { a / b }



### [N-36] Explicit Visibility Recommended in Variable/Function Definitions

In Solidity, variable/function visibility is crucial for controlling access and protecting against unwanted modifications. While Solidity functions default to internal visibility, it is best practice to explicitly state the visibility for better code readability and avoiding confusion.

The missing visibility could lead to a false sense of security in contract design and potential vulnerabilities.




### [N-37] Contracts should have full test coverage

It's recommended to have full test coverage for all contracts. While 100% code coverage does not guarantee absence of bugs, it can catch simple bugs and reduce regressions during code modifications. Moreover, to achieve full coverage, authors often have to refactor their code into more modular components, each testable separately. This leads to lower interdependencies, and results in code that is easier to understand and audit.




### [N-38] Implement Formal Verification Proofs to Improve Security

Formal verification offers a mathematical proof confirming that your code operates as intended and is devoid of edge cases that may lead to unintended behavior. By leveraging this rigorous audit technique, you not only enhance the robustness of your code but also strengthen the trust of stakeholders in the safety of your contract.
