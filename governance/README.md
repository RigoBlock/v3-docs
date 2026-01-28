# Governance

### **Core Components of the Rigoblock Governance Framework**

* **Modular and Deterministic Proxy Pattern**\
  A lightweight **governance proxy** is deployed at the **same address** on every supported network (e.g., Ethereum mainnet, L2s like Optimism or Arbitrum). This proxy holds the governance state (proposals, votes, etc.) and delegates execution to a **canonical governance implementation** contract that contains the core logic.\
  The deterministic nature ensures consistent addressing across chains, simplifying multichain deployments and interactions.
* **Voting Strategy as a Plug-in**\
  The voting logic is separated into a distinct **voting strategy contract**, which is project-specific. This allows each project (or DAO) to define its own rules—e.g., quadratic voting, token-weighted, reputation-based, or custom logic—while reusing the proxy and core governance layer.\
  Projects can opt to use Rigoblock's highly efficient proxy pattern even if they provide their own custom governance implementation on top of their strategy.
* **Upgradability via Proposals**\
  Governance is **upgradeable** through successful proposals. Upgradable parameters include:\
  a) **Implementation** address (the canonical logic contract)\
  b) **Voting strategy** contract\
  c) **Proposal threshold** (minimum tokens/power needed to create a proposal)\
  d) **Voting threshold** (e.g., quorum or majority requirements)
  * New implementation (a) and voting strategy (b) must be valid smart contract addresses.
  * Changes to thresholds (c and d) must pass validation checks defined in the active voting strategy contract (to prevent invalid or unsafe configurations).

This setup enables projects to start with a battle-tested, canonical Rigoblock governance setup and later evolve (e.g., migrate to a fully custom implementation or tweak voting mechanics) without breaking multichain consistency or requiring users to track different addresses.

### Benefits of This Approach

* **Multichain Consistency** — Same governance address everywhere, reducing complexity for users and frontends.
* **Efficiency** — Proxies minimize gas costs and deployment overhead compared to deploying full logic contracts per chain.
* **Flexibility** — Projects retain sovereignty over their voting rules and can upgrade as needs evolve (e.g., shifting from simple token voting to more advanced mechanisms).
* **Security & Composability** — Separation of state (proxy), logic (implementation), and rules (strategy) follows best practices for upgradeable contracts, similar to patterns in OpenZeppelin or other DeFi protocols.

