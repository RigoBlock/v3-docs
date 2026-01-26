---
description: Rigoblock Protocol Fees
---

# Overview

The Rigoblock protocol applies a spread (set by the pool operator to prevent unfair entries or exits) to mint and burn operations. Since version 4.1.0, the resulting spread token amount is transferred to the TokenJar contract, where it accrues alongside fees collected in any other token.

TokenJar token balances can be released by paying a decreasing amount of GRG tokens. This payment is determined through a reverse Dutch auction mechanism: the amount of GRG required to clear the TokenJar balances progressively decreases over time until it reaches a predefined minimum threshold. The paid GRG is then transferred to the `0xdead` address on each chain, effectively burning those tokens.

When interacting with the releaser contract, searchers specify the maximum amount of GRG they are willing to pay. This design prevents front-running and enables a MEV-minimized conversion of fees to GRG.

The protocol fee smart contracts are derived from the Uniswap protocol fees implementation [(https://github.com/Uniswap/protocol-fees)](https://github.com/Uniswap/protocol-fees) but replace the fixed threshold model with a reverse Dutch auction. This approach minimizes MEV exposure (fee release becomes progressively less expensive, especially in the case of a large single fee accrual during the initial decay phase) and allows for less frequent clearing of balances. Instead of converting TokenJar tokens at a fixed price threshold, the effective price of the token portfolio decreases over time until it reaches the original equivalent threshold value.
