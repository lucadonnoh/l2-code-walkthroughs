# Censorship buffer

Before the implementation of the buffer, txs could be censored by the permissioned sequencer for up to 24h each. This was a problem for Orbit L3s on Arbitrum One as, in case of censorship, there wouldn't be enough time to play the challenge game on the L2 (for the L3) if the challenge period was set to 7d, as around ~60 moves are needed to finish a game, implying the need of at least 60 days.
The logic of the buffer can be found in the `SequencerInbox` contract.

## The `forceInclusion` function
This function acts as the entry point to force txs through the base chain. The signature of the function is:

```solidity
function forceInclusion(
    uint256 _totalDelayedMessagesRead,
    uint8 kind,
    uint64[2] calldata l1BlockAndTime,
    uint256 baseFeeL1,
    address sender,
    bytes32 messageDataHash
) external
```

## The `DelayBuffer` library
