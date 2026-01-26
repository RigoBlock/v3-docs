---
description: Rigoblock protocol fees
---

# Overview

The Rigoblock protocol (since version 4.1.0) applies a spread (set by the pool operator) to mint and burn operations. The spread token amount is transferred to the TokenJar contract, where it accrued with the fess collected in any other token. The TokenJar tokens can be released upon paying a decreasing amount of GRG tokens. This amount is extracted using a reverse dutch auction, where the amount needed to clear the TokenJar token balances progressively decreases over time, until reaching the minimum threshold. The paid GRG amount is transferred to the 0xdead address on each chain, effectively burning the paid tokens. When calling the releaser contract, searchers set the maximum amount of GRG they are willing to pay, ensuring no front-running is possible. This allow free and MEV-minimized fee-to-GRG conversion.

The protocol fee smart contracts are derived work of the Uniswap protocol fees [https://github.com/Uniswap/protocol-fees](https://github.com/Uniswap/protocol-fees) but apply a reverse dutch auction model to minimize MEV and allow better clearing of balances. Instead of coverting TokenJar tokens at a fixed threshold, the price of the token portfolio is decreasing down to the threshold original equivalent.
