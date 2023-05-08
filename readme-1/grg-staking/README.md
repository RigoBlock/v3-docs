---
description: >-
  GRG holders stake to their preferred staking pool and earn part of the pool's
  rewards
---

# GRG Staking

When a pool is registered in the RigoBlock staking system, it becomes eligible for receiving GRG rewards. The wallet registering the pool in the staking system is tagged as "staking pal" and receives 10% of the pool operator's rewards, unless it is the same wallet, which receives 100% of the rewards.

GRG holders can stake to their preferred staking pool (or the staking pool which maximizes their ROS) and, as a return for helping the pool operator maximizing its rewards, receive a portion of the pool operator's reward. By default, a minimum of 30% of reward is shared with the pool's stakers. The pool operator can increase the percentage shared with the community in order to attracting more stake and increasing its rewards. Once increased, the percentage shared cannot be decreased, therefore the pool operator must carefully consider the tradeoff between attracting stake and maximizing profitability.

During an epoch (2-weeks long initially) any wallet can credit the proof-of-performance reward for a said pool to the staking system, which is initially equal to the pool's locked staked GRG to itself.

At the end of each epoch a pool's own stake competes with the other active pools' own stakes. In the same way, the total stake delegated to a pool competes with the total stake delegated to all active pools. The two metrics are weigthed according to an Arrow-Pratt exponential weighting formula, which initial setting of 2/3 weight for the pool's own relative stake and 1/3 weigth for the pool's overall relative delegated stake.

GRG staking is available on Ethereum Mainnet, Arbitrum, Optimism, Polygon and BNB chain.
