---
description: >-
  Each RigoBlock pool proxy is deployed by the proxy factory, which also serves
  as a beacon for pool implementation upgrades
---

# Proxies

* proxy --> the contract which delegates calls to the implementation
* proxy factory --> the proxy deployer contract. Produces a unique pool ID, which is stored in a mapping in the registry. A user inputs a name of maximum 31 characters and a symbol between 3 and 5 characters and a base tokens, the factory deploys the proxy, updates its initialization storage values and registers the pool at the pool registry.
