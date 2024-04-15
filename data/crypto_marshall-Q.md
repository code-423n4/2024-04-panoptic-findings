https://github.com/code-423n4/2024-04-panoptic/blob/main/contracts/CollateralTracker.sol#L195C1-L211C6

        // calculate amount of ticks required for upwards and downwards moves, used to check if current and mini-median tick
        // are out of sync (then apply a 100% collateral requirement)
        unchecked {
            // taylor expand log(1-sellCollateralRatio)/log(1.0001) around sellCollateralRatio=2000 up to 3rd order
            /// since we're dropping the higher order terms, which are all negative, this will underestimate the number of ticks for a 20% move
            int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);
            TICK_DEVIATION = uint256(
                2230 +
                    (12500 * ratioTick) /
                    10_000 +
                    (7812 * ratioTick ** 2) /
                    10_000 ** 2 +
                    (6510 * ratioTick ** 3) /
                    10_000 ** 3
            );
        }
    }

A better approach

// calculate amount of ticks required for upwards and downwards moves, used to check if current and mini-median tick
// are out of sync (then apply a 100% collateral requirement)
unchecked {
    int256 ratioTick = int256(_sellerCollateralRatio) - 2000;
    int256 term1 = (12500 * ratioTick) / 10000;
    int256 term2 = (7812 * ratioTick ** 2) / 100000000;
    int256 term3 = (6510 * ratioTick ** 3) / 1000000000000;
    uint256 TICK_DEVIATION = uint256(2230 + term1 + term2 + term3);
}

The revised Solidity code calculates the deviation in ticks required for managing collateral requirements by using a Taylor series approximation. The formula computes changes based on the _sellerCollateralRatio deviation from 2000, breaking down the calculation into distinct terms (term1, term2, term3) for clarity and easier debugging. Each term adjusts for scale differently, contributing to a total TICK_DEVIATION which integrates these incremental calculations to determine the final tick deviation efficiently.