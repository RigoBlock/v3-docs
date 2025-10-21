---
description: >-
  The Rigoblock protocol is a set of smart contracts for deploying and running
  on-chain token management strategies with real time reconciliation of
  positions and value.
---

# Introduction to Rigoblock

At its heart, it consists of a very light pool proxy contract (\~227k gas units) which delegates calls to a pool implementation contract.

The implementation address is stored in the proxy, and can only be updated upon its operator's action in a trust-minimized way, by querying the new address from a beacon contract. The new address is retrieved from the proxy factory contract, which can be modified only by the Rigoblock DAO through an on-chain governance vote. The Rigoblock DAO cannot autonomously take over control of the pool, as each pool operator must upgrade to the new implementation address the upgrade to take effect.

Since the use of a proxy and an implementation can lead to undesired storage clashing and possible overwriting, each variable (or batch of variables) is assigned a deterministic and randomly big-enough storage slot, so that accidental storage cannot happen.

Before upgrading the implementation, the Rigoblock Governance must assess that newly-introduced variables do not overlap existing storage slots. Furthermore, before whitelisting an extension to the protocol, the Rigoblock Governance must ensure that the storage slot used by the extension does not overlap to existing storage.

The pool implementation code extends the core functionalities of the pool itself. Further methods are added through adapters, which are accessible in write-mode for the pool operator only, while in read-mode for everyone else. These adapters allow interaction with external smart contracts. In order to guarantee smooth interaction with external applications, the adapters are updated by the governance, meaning each pool will use the same adapter when interacting with a certain application, regardless of the implementation. By design, only the pool operator can access the adapters in write mode, preventing a pool takeover by the governance (even in the case of a rogue attack on the governance).
