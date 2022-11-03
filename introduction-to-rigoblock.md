---
description: >-
  The RigoBlock protocol is a set of smart contracts for deploying and running
  on-chain token management strategies.
---

# Introduction to RigoBlock

At its heart, it consists of a very light pool proxy contract (\~227k Gas units) which delegates calls to a pool implementation contract.

The pool implementation can be upgraded by the RigoBlock Governance, and each pool operator must upgrade the implementation address in the pool proxy storage for the upgrade to take effect.

Since the use of a proxy and an implementation can lead to undesired storage clashing and possible overwriting, each variable (or batch of variables) is assigned a deterministic and randomly big-enough storage slot, so that accidental storage cannot happen.

Before upgrading the implementation, the RigoBlock Governance must assess that newly-introduced variables do not overlap existing storage slots. Furthermore, before whitelisting an extension to the protocol, the RigoBlock Governance must ensure that the storage slot used by the extension does not overlap to existing storage.

The pool implementation code extends the core functionalities of of the pool itself. Further methods are added through extensions/adapters, which are accessible in write-mode for the pool operator only, while in read-mode for everyone else.

The RigoBlock Governance may trigger a force upgrade of the implementation address, but this would still require action by the pool operator. This is particularly relevant in case of implementation patches which restrict the actions of the pool operator.
