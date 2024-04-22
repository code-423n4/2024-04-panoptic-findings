        modifier ReentrancyLock(uint64 poolId) {
        // check if the pool is already locked
        // init lock if not
        beginReentrancyLock(poolId);

        // execute function
        _;

        // remove lock
        endReentrancyLock(poolId);
    }

    /// @notice Add reentrancy lock on pool
    /// @dev reverts if the pool is already locked
    /// @param poolId The poolId of the pool to add the reentrancy lock to
    function beginReentrancyLock(uint64 poolId) internal {
        // check if the pool is already locked, if so, revert
        if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();

        // activate lock
        s_poolContext[poolId].locked = true;
    }

    /// @notice Remove reentrancy lock on pool
    /// @param poolId The poolId of the pool to remove the reentrancy lock from
    function endReentrancyLock(uint64 poolId) internal {
        // gas refund is triggered here by returning the slot to its original value
        s_poolContext[poolId].locked = false;
    }




use transient storage instead of above implementation for gas optimization .

https://soliditylang.org/blog/2024/01/26/transient-storage/