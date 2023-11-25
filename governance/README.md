# Governance

The Rigoblock governance is built on a modular governance framework which allows any project to deploying its own governance with the same address on every network where it is deployed regardless each network's specific parameters, including a project's idiosyncratic voting strategy.

A lightweight governance proxy is deployed and stores the state of the governance. The proxy, in turn, delegates calls to the canonical governance implementation, which stores all the logic. The voting strategy is a separate plug-in contract that is specific to each project. Projects can leverage Rigoblock for the highly efficient deterministic proxy pattern used, and even use their own custom implementation, on top of their own custom strategy (the latter being required by default).

While opting for the canonical implementation, a project could later opt-out and use a custom implementation as the governance is upgradable after successful proposal execution. Upgradable governance parameters include: a) implementation; b) voting strategy; c) proposal threshold; d) voting threshold. New parameters a) and b) are required to being a smart contract, while new parameters c) and b) are required to pass validation in the governance strategy.

#### Disclaimer: contracts in the Rigoblock Governance have not been audited. While 100% code coverage has been achieved, this is by no means guarantee that the software is bug-free. Please use extreme caution when interacting with the contracts and treat them as not safe until an independent audit is produced.

