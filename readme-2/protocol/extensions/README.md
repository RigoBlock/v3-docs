---
description: >-
  Methods not implemented in the core can be added as an extension without
  requiring a governance implementation upgrade. This is relevant for bridges
  with external applications
---

# Extensions

* EWhitelist --> extension which stores the whitelisted tokens, uses Rigoblock Authority permissions. It also allows the whitelisting and blacklisting of different tokens in batches.
* EUpgrade --> extension to upgrading the pool implementation, returns the current implementation. It also returns the address of the beacon, which stored the address of the latest implementation.
* AUniswap --> bridge to the uniswap V3 and V2 protocols, allows pools to swap tokens on both V3 and V2 and potentially split swaps between the two protocols if optimal. Allows the pool to farm liquidity rewards on Uniswap V3 pools.
* AStaking --> allows the pool operator to stake GRG tokens to its own Rigoblock staking pool in 1 single call. Creates the staking pool if doesn't exist, stakes to the staking system and delegates the stake to itself.
* AMulticall --> allows to send multiple transactions to the pool at once.
* ASelfCustody (deprecated in v4) --> an extension that allows a pool operator to transfer tokens from the pool to external wallet, i.e. cold storage. Designed for professional market makers, requires a minimum holding of 100K GRG tokens.
