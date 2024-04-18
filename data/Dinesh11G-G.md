## Title: Gas Optimization Issue in SafeTransferLib.sol

## Description
The SafeTransferLib.sol library, used for safe ERC20 token transfers at `SafeTransferLib::safeTransferFrom` & `SafeTransferLib::safeTransfer`, employs gas-inefficient ABI encoding methods, potentially leading to unnecessary gas consumption during token transfers.

## Impact
The inefficient ABI encoding methods utilized in `SafeTransferLib.sol` could result in increased gas costs for token transfers, particularly in scenarios involving frequent or large-scale transfers. This additional gas expenditure may impact the overall efficiency and cost-effectiveness of smart contracts utilizing this library.

## Proof of Concept
The gas optimization issue was identified in the following code snippets:
- Line 29: [SafeTransferLib.sol#L29](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L29)

`mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)`

- Line 60: [SafeTransferLib.sol#L60](https://github.com/code-423n4/2024-04-panoptic/blob/833312ebd600665b577fbd9c03ffa0daf250ed24/contracts/libraries/SafeTransferLib.sol#L60)

`mstore(p, 0xa9059cbb00000000000000000000000000000000000000000000000000000000)`

## Tools Used
Manual code review with VScode

## Recommended Mitigation Steps with fix code
To address the gas optimization issue in SafeTransferLib.sol, it is recommended to switch to more gas-efficient ABI encoding methods, such as `abi-encodedpacked`.