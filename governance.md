# Governance

The Rigoblock governance is built on a modular governance framework which allows any project to deploying its own governance with the same address on every network where it is deployed regardless each network's specific parameters, including a project's idiosyncratic voting strategy.

A lightweight governance proxy is deployed and stores the state of the governance. The proxy, in turn, delegates calls to the canonical governance implementation, which stores all the logic. The voting strategy is a separate plug-in contract that is specific to each project. Projects can leverage Rigoblock for the highly efficient deterministic proxy pattern used, and even use their own custom implementation, on top of their own custom strategy (the latter being required by default).

While opting for the canonical implementation, a project could later opt-out and use a custom implementation as the governance is upgradable after successful proposal execution. Upgradable governance parameters include: a) implementation; b) voring strategy; c) proposal threshold; d) voting threshold. New parameters a) and b) are required to being a smart contract, while new parameters c) and b) are required to pass validation in the governance strategy.

#### Rigoblock Governance

Rigoblock voting power is equivalent to a wallet's GRG active stake. A proposal requires a voting power of at least 100k GRG on Ethereum mainnet, 40k GRG on L2s in order for it to be valid. A voter can vote in favor, aginst, or abstain. A proposal requires a quorum of at least 400k GRG on Ethereum mainnnet, 200k GRG on L2s. Each network is managed separately in order to maximize the cost benefit of L2, while maintaining Ethereum L1 voting on L1. This rule is subject to change as Rigoblock could later decide to leverage chain message bridging to improve running its multichain governance.

Two thirds of votes in favor are required for a proposal to be successful. Abstained votes are counted for but are not computed in the quorum or in the voting for/against. The voting period starts from the start of the next GRG staking epoch and lasts for 7 days. The voting period is required to being shorter than the epoch period. If during the voting period the proposal finds absolute qualified majority of support, i.e. the state is final and cannot be changed by further votes against, the proposal state is updated to "Qualified" and the transaction can be executed from next block.&#x20;
