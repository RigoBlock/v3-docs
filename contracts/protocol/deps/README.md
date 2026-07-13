---
description: Contracts that add base functionality to the protocol
---

# Deps

* Authority --> contains all protocol permissions, it is owned by the Rigoblock governance and stores the approved factories, adapters, whitelisted methods on adapters and the wallets that have whitelister role.
* PoolRegistry --> stores the mapping of a pool proxy address to its assigned ID, which is the hash of the name and the owner, making it unique for a said name and pool operator. A pool's name is not stored in the registry and can be used multiple times (but with different pool owners) in order to prevent a race condition which would make it not 100% certain that they could deploy the same pool to multiple chains. The pool registry is used by applications like the Rigoblock Staking system for querying a pool's unique ID. A pool owner can set metamadata for its pool.
* KYC --> a mock module, since a canonical KYC module is not provided and the pool operator is responsible, if decides to opt-in for whitelisting its pool proxy users, to implementing/selecting the KYC module of his choice, potentially restricting who can mint his operated pool's tokens or the maximum mintable amount.

