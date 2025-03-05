# Censorship buffer

## Motivation
Before the implementation of the buffer, txs could be censored by the permissioned sequencer for up to 24h each. This was a problem for Orbit L3s on Arbitrum One as, in case of censorship, there wouldn't be enough time to play the challenge game on the L2 (for the L3) if the challenge period was set to 7d, as around ~60 moves are needed to finish a game, implying the need of at least 60 days.

## Implementation
The logic of the buffer can be found in the `SequencerInbox` contract.
