# Known Issues

The following is a non-exhaustive list of known potential attack vectors:

* **Pool Transaction Front-Running by a Malicious Pool Operator**\
  A pool operator's coordinated wallet could front-run pool transactions. A potential mitigation, such as setting a maximum slippage against an on-chain price feed, may cause transaction reverts in high-volatility environments. However, this does not fully address the issue, as a rogue pool operator could achieve the same result by executing multiple smaller transactions. This attack assumes privileged access (pool operator) with malicious intent against the pool's Total Value Locked (TVL). Additionally, an external attacker could exploit the binding to prevent a pool from executing swaps by manipulating the token price in a sandwich attack. Temporarily blocking a smart pool from executing transactions after a significant price drawdown is not a viable solution, as it could hinder operations during high-volatility periods—when the greatest opportunities arise—and unnecessarily increase gas costs. Developers can implement custom rules on top of the protocol to apply their preferred mitigation strategies.
* **Purchase of a Rogue Token**\
  A rogue token, such as one created by the pool operator, could be purchased. This issue is not addressed, as the RigoBlock protocol is unopinionated about which tokens can be included in a pool.
* **Purchase of a Debt Token**\
  Purchasing a debt token via a swap or similar action should not be possible on the open market, as debt positions typically have no positive value. However, a sophisticated attack by the pool operator could potentially enable this.
* **Frontrunning During Pool Token Burning**\
  When the last holder attempts to burn their pool tokens, an attacker could front-run the transaction by minting a small amount of pool tokens. This would prevent the user from being the sole holder, forcing them to pay the spread to the pool. As a side effect, the pool price would increase, allowing the attacker to effectively "steal" the spread after the lockup period expires. Mitigation strategies include:
  * Requiring only whitelisted holders in the pool.
  * Charging the spread in favor of the RigoBlock DAO (or the pool operator) instead of the pool and applying the spread on minting as well. This would minimize price impacts, with only small rounding errors possible.
  * Excluding spread balances from price calculations.
* **Unitary Value Inflation on Burn**\
  Each burn operation (when the pool has multiple holders) incurs a spread charged to the holder burning their tokens, benefiting the smart pool. This inflates the token price but protects the smart pool from discrepancies between the TWAP-based portfolio evaluation and the portfolio's actual value.
* **Unitary Value Calculation Errors Due to Price Feed**\
  On tokens where the oracle liquidity pool is small, or on chains where gas price is high, thus not resulting in a timely price feed update, the smart pool's unitary price calculations may result in error, which might become significant if the owned token has a big percentage of the total portfolio weight. Furthermore, an incorrectly initialized token price feed could take time to get corrected. Pool operators should use caution when using new or illiquid tokens. In particular, the protocol is not opinionated about a price feed's cardinality (a cardinality of 1, for example, means that the TWAP is not really an average, but simply the last stored observation).
*   **Oracle Manipulation Attacks**

    Rigoblock uses the BackGeoOracle, a MEV-resistant onchain price feed oracle, for real time NAV calculations. An oracle manipulation, either via MEV-boost, or via a pure market manipulation, could result in the oracle returning an incorrect price, thus distorting NAV calculations. An attacker could decide to lose funds in order to manipulate the market price, as long as the gain is bigger. This is true for any type of oracle used. Using a geometric mean protects against temporary price fluctuations.
* **Attacks Requiring Special Privileges**\
  Attacks that rely on privileged access, such as those executed by the pool operator.
* **Attacks Involving a Compromised Pool Operator Private Key**\
  Attacks that exploit a compromised pool operator private key.
* **Use of a Malicious Uniswap V4 Hook**\
  Although Rigoblock V4 includes safeguards to prevent accidental input errors and restrict hooks' access to a pool's liquidity token balances, the protocol does not restrict the types of hooks a pool may use. A malicious Uniswap V4 hook could impose fees up to 100% of the swap amount, resulting in significant or total loss of funds. As when interacting directly with Uniswap V4, users must exercise extreme caution when interacting with Uniswap V4 hooks via RigoBlock.
* **Burn of Uniswap V4 ERC6909 Tokens**\
  If an external wallet or a hook mints ERC6909 Tokens, they cannot be burnt within the smart pool. Future releases will support this functionality.
* **Chains that do not use address(0) as Native Currency**\
  Polygon (or any similar chain that use a token as base currency) are not currently supported by the v4 protocol.
* **Chains that do not Support Transient Storage Opcodes**\
  Chains that do not support transient storage are not compatible with Rigoblock V4.

Given these risks, the relationship between the pool operator and pool holder(s) is trust-based. RigoBlock provides an extra layer of security for pool operators to interact with on-chain applications and enhances transparency by tracking real-time pool activity, portfolio positions, and price calculations.\


An alternative to direct participation to a pool is by staking GRG in the target pool, which allows users to gain exposure to the performance of top pools (i.e. GRG staking can be considered a proxy of the performance, but without the downside of holding a pool - besides the market price fluctuations). Stakers are rewarded for securing the network and supporting pool operators in maximizing staking rewards. The system does not require trust in pool operators and is governed by RigoBlock Governance.
