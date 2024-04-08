### 1) SemiFungiblePositionManager::safeBatchTransferFrom function lacks input validation checks for length of ids and amounts array. The function drives the logic based on ids length which could results into two invalid scenarios.

- amounts array is longer than ids array, in which case, the amounts passed will be ignored

- amounts array is shorted than ids array, in which case, the logic will throw index out of bounds exception. 