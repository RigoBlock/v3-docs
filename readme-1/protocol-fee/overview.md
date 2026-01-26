---
description: Rigoblock protocol fees
---

# Overview

The Rigoblock protocol applies a spread to mint and burn operations. The spread token amount is transferred to the TokenJar contract, where it accrued with the fess collected in any other token. The TokenJar tokens can be released upon paying a decreasing amount of GRG tokens. This amount is extracted using a reverse dutch auction, where the amount needed to clear the TokenJar token balances progressively decreases over time, until reaching the minimum threshold. The paid GRG amount is transferred to the 0xdead address on each chain, effectively burning the paid tokens. When calling the releaser contract, searchers set the maximum amount of GRG they are willing to pay, ensuring no front-running is possible. This allow free and MEV-minimized fee-to-GRG conversion.
