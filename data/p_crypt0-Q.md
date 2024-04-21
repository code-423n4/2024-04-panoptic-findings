# [non-critical] EIP-2612 Non-compliance - ERC20Minimal.sol
Unlike ERC115Minimal.sol which stipulates non-compliance in its pre-contract comments, ERC20Minimal does not forewarn users that the contract is non-compliant. However, ERC20Minimal contract does not implement the `permit` function which ensures EIP-2612 compliance.

Users expecting full compliance will likely experience unexpected behaviour