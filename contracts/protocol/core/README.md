---
description: >-
  The modular core is designed in order to maximize code readability and is
  divided in sub-modules
---

# Core

* constants --> the deployment constants
* immutables --> the deployment immutables, initialized in the constructor
* storage --> the deterministic pool storage (the order of variable declaration is irrelevant as the variable is assigned a randomly big-enough storage slot
* owner actions --> the actions restricted to the pool operator only
* actions --> the publicly accessible write methods
* state --> the public read methods
* storage accessible --> a generic contracts which can retrieve any batch of data at any combination of storage slots
* events --> the logs emitted at a pool's transaction
