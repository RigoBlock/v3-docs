# Known Issues

The following is a non-exhaustive list of known potential attack vectors:

* **Pool Transaction Front-Running by a Malicious Pool Operator**\
  A pool operator's coordinated wallet could front-run pool transactions. A potential mitigation, such as setting a maximum slippage against an on-chain price feed, may cause transaction reverts in high-volatility environments. However, this does not fully address the issue, as a rogue pool operator could achieve the same result by executing multiple smaller transactions. This attack assumes privileged access (pool operator) with malicious intent against the pool's Total Value Locked (TVL). Additionally, an external attacker could exploit the binding to prevent a pool from executing swaps by manipulating the token price in a sandwich attack. Temporarily blocking a smart pool from executing transactions after a significant price drawdown is not a viable solution, as it could hinder operations during high-volatility periods—when the greatest opportunities arise—and unnecessarily increase gas costs. Developers can implement custom rules on top of the protocol to apply their preferred mitigation strategies.
*   **Pool Burn Front-Running by a Malicious Pool Operator**

    A pool operator could initiate a crosschain Sync operation using input param that result in the crosschain deposit to expire without being filled on the destination chain. This can result in the burn to fail, or in the holder to receive a smaller amount than he should. At the same time, the pool operator cannot know when the refund will occur, which partially counterbalances the incentive for such an attack.
* **Purchase of a Rogue Token**\
  A rogue token, such as one created by the pool operator, could be purchased. This issue is not addressed, as the RigoBlock protocol is unopinionated about which tokens can be included in a pool, as long as they conform to token standards and can be exchanged. A rogue token includes tokens that temporarily revert on standard ERC20 methods, in which case it is deemed safer to exclude such tokens from NAV accounting.
*   **Setting a Rogue Token as Accepted for Mint Operations**

    A rogue token could be deployed and set as acceptable mint token by the pool operator. Whenever someone mints using the base token, anyone could manipulate the rogue token price on the open market and mint big amounts of pool tokens. Attacks using `mintWithToken` first require the pool operator to explicitly approve the target token as mint token!
* **Purchase of a Debt Token**\
  Purchasing a debt token via a swap or similar action should not be possible on the open market, as debt positions typically have no positive value. However, a sophisticated attack by the pool operator could potentially enable this.
* **Unitary Value Calculation Errors Due to Price Feed**\
  On tokens where the oracle liquidity pool is small, or on chains where gas price is high, thus not resulting in a timely price feed update, the smart pool's unitary price calculations may result in error, which might become significant if the owned token has a big percentage of the total portfolio weight. Furthermore, an incorrectly initialized token price feed could take time to get corrected. Pool operators should use caution when using new or illiquid tokens. In particular, the protocol is not opinionated about a price feed's cardinality (a cardinality of 2 - the minimum required - means that the TWAP is very sensitive to changes in the spot price, while a correctly configured oracle is slower to adapt).
*   **Oracle Manipulation Attacks**

    Rigoblock uses the BackGeoOracle, a MEV-resistant onchain price feed oracle, for real time NAV calculations. An oracle manipulation, either via MEV-boost, or via a pure market manipulation, could result in the oracle returning an incorrect price, thus distorting NAV calculations. An attacker could decide to lose funds in order to manipulate the market price, as long as the gain is bigger. This is true for any type of oracle used. Using a geometric mean protects against temporary price fluctuations. Please do not report attacks that require oracle manipulations.
* **Attacks Requiring Special Privileges**\
  Attacks that rely on privileged access, such as those executed by the pool operator.
* **Attacks Involving a Compromised Pool Operator Private Key**\
  Attacks that exploit a compromised pool operator private key.
* **Use of a Malicious Uniswap V4 Hook**\
  Although Rigoblock V4 includes safeguards to prevent accidental input errors and restrict hooks' access to a pool's liquidity token balances, the protocol does not restrict the types of hooks a pool may use. A malicious Uniswap V4 hook could impose fees up to 100% of the swap amount, resulting in significant or total loss of funds. As when interacting directly with Uniswap V4, users must exercise extreme caution when interacting with Uniswap V4 hooks via RigoBlock.
* **Crosschain Sync Latency**\
  While single-chain pool price is updated in real time, the price will differ across chains until a Sync operation is prompted by the pool operator. These operations can be sent programmatically, and are entirely under the pool operator's control.
* **Chains that do not use address(0) as Native Currency**\
  Chains that use a token as base currency are not currently supported by the v4 protocol.
* **Chains that do not Support Transient Storage Opcodes**\
  Chains that do not support transient storage are not compatible with Rigoblock V4.
* **Permanent NAV Understatement in Expired Across Transfer Refund**
* **HyperEvm NAV Understatement with HyperCore pending deposits**\
  In the case a deposit to hyperCore is not confirmed in the following block, NAV will be underestimated. To prevent this, pool operators are encouraged to use a different chain as main, restrict mint operations to whitelisted wallets, and use HyperEvm for perps only.
* **First Mint at Unitary Price**\
  This is intended. Externally transferred assets are ignored on the first mint and the pool is always initialized at unitary value. Smart pools are not expected to receive funds externally - any funds accidentally directly send to the smart pool (i.e. not using the `mint` `burn` or similar methods) are lost for the sender, as the smart pool cannot directly transfer funds to an arbitrary wallet.
* **Fee Collector Balance Griefing attacks**\
  The pool operator can at any time update the address of the fee collector to stop the griefing attacks.

Therefore, the relationship between the pool operator and pool holder(s) is trust-minimized, and serves as the rails to run strategies onchain, where the LPs have agreed to some offchain terms which the protocol does not enforce. Rigoblock provides an extra layer of security for pool operators to interact with on-chain applications and enhances transparency by tracking real-time pool activity, portfolio positions, and price calculations.

Please do not submit reports about governance takeovers, or takeovers that require acquiring big amount of GRG tokens. Please understand that voting snapshot is not implemented by choice, and that a qualified majority is intended to allow early execution for proposals that would become executable anyway at the end of the epoch - as there would be no voting power to make the proposal fail anyway. The core concept of the Rigoblock is that it is owned by the GRG stakers, therefore any proposal reaching a qualified consensus (i.e. supermajority) is allowed for fast execution and has the ability to also upgrate the governance itself - this is a core design pillar of the Rigoblock's own decentralized (RigoblockGovernanceStrategy.sol), which is specific to Rigoblock.

Please do not report hypothetical attacks, that require conditions that are not executable. Please do not report potential misconfiguration issues, especially if they require rogue parameters far off the current parameters.
