---
description: Rigoblock V4 Bug Bounty
---

# Bug Bounty

### Overview

Starting on September 8th, 2024, the [rigoblock-v3-contracts](https://github.com/RigoBlock/v3-contracts) repository is subject to the Rigoblock V3 Bug Bounty (the “Program”) to incentivize responsible bug disclosure.

Starting on May 29th, 2025, the [rigoblock-v3-contracts](https://github.com/RigoBlock/v3-contracts) repository is subject to the Rigoblock V4 Bug Bounty (the “Program”) to incentivize responsible bug disclosure. Rigoblock V3 smart contracts are deprecated and not covered by the Program.

### Scope

The scope of the Program is limited to bugs that result in the draining of contract funds, abuse of voting power in the Rigoblock governance or affects rewards in the Rigoblock staking system.

The following are not within the scope of the Program:

* Any contract located under contracts/test or contracts/examples.
* Bugs in any third party contract or platform that interacts with Rigoblock V4.
* Vulnerabilities already reported and/or discovered in contracts built by third parties on Rigoblock V4.
* Attacks that require a Rigoblock governance takeover.
* Issues described in the "Known Issues" section.
* Any already-reported bugs.

Vulnerabilities contingent upon the occurrence of any of the following also are outside the scope of this Program:

* Frontend bugs
* Clickjacking (we do allow 3rd parties to iframe us)
* DDOS attacks
* Bugs in third party code
* Dev branches that are _not_ deployed in public packages or contracts
* Third party contracts that are not under the direct control of Rigoblock
* Issues already listed in the audits for the contracts above
* Bugs in third party contracts or applications that use Rigoblock contracts
* Attacks that require oracle manipulation
* Brute force attacks
* Rounding errors
* Extreme market turmoil vulnerability
* Gas optimization recommendations
* Task Hijacking (Strandhogg)
* Spamming
* Phishing
* Automated tools (Github Actions, AWS, etc.)
* Compromise or misuse of third party systems or services

### Assumptions

Rigoblock V4 was developed with the following assumptions, and thus any bug must also adhere to the following assumptions to be eligible for the bug bounty:

* The relation between the smart pool operator and its holders is not completely trustless, there is some accepted level of potential abuse of trust, which is disclosed in the documentation.
* The pool unitary value is automatically calculated onchain.
* Rebase tokens, interest bearing tokens and fee-on-transfer tokens, although technically usable as base tokens for a smart pool, are excluded.
* Any token is potentially ownable by the smart pools, as long as a price feed on the [BackGeoOracle](../oracles-and-price-feeds.md) is available. The protocol is unopinionated about the validity of the price feed.

### Rewards

Rewards will be allocated based on the severity of the bug disclosed and will be evaluated and rewarded at the discretion of the Rigoblock team. For critical bugs that lead to any loss of smart pool funds, rewards of up to $10,000 will be granted. Lower severity bugs will be rewarded at the discretion of the team. The amount is in any case capped at 10% of the protocol TVL at risk. Rewards are paid in stablecoin.

### Prohibited Actions

* Live testing on public chains, including public mainnet deployments and public testnet deployments.
  * We recommend testing on the integrated testing framework, or on local forks, for example using foundry.
* Public disclosure of bugs without the consent of the protocol team.
* _Conflict of Interest_: any employee or contractor who currently works, or previously worked, with Rigoblock cannot participate in the Bug Bounty without prior approval.

### Disclosure

Any vulnerability or bug discovered must be reported only to the following email: [security@rigoblock.com](mailto:security@rigoblock.com).

The vulnerability must not be disclosed publicly or to any other person, entity or email address before Rigoblock has been notified, has fixed the issue, and has granted permission for public disclosure. In addition, disclosure must be made within 24 hours following discovery of the vulnerability.

A detailed report of a vulnerability increases the likelihood of a reward and may increase the reward amount. Please provide as much information about the vulnerability as possible, including:

* The conditions on which reproducing the bug is contingent.
* The steps needed to reproduce the bug or, preferably, a proof of concept.
* The potential implications of the vulnerability being abused.

Anyone who reports a unique, previously-unreported vulnerability that results in a change to the code or a configuration change and who keeps such vulnerability confidential until it has been resolved by our engineers will be recognized publicly for their contribution if they so choose.

### Eligibility

To be eligible for a reward under this Program, you must:

* Discover a previously-unreported, non-public vulnerability that is not previously known by the team and within the scope of this Program.
* Be the first to disclose the unique vulnerability to [security@rigoblock.com](mailto:security@rigoblock.com), in compliance with the disclosure requirements above. If similar vulnerabilities are reported within the same 24 hour period, rewards will be split at the discretion of Rigoblock.
* Provide sufficient information to enable our engineers to reproduce and fix the vulnerability.
* Not engage in any unlawful conduct when disclosing the bug, including through threats, demands, or any other coercive tactics.
* Not exploit the vulnerability in any way, including through making it public or by obtaining a profit (other than a reward under this Program).
* Make a good faith effort to avoid privacy violations, destruction of data, interruption or degradation of Rigoblock V4.
* Submit only one vulnerability per submission, unless you need to chain vulnerabilities to provide impact regarding any of the vulnerabilities.
* Not submit a vulnerability caused by an underlying issue that is the same as an issue on which a reward has been paid under this Program.
* Not engage in any unlawful conduct when disclosing the bug, including through threats, demands, or any other coercive tactics.
* Not be one of our current or former employees, vendors, or contractors or an employee of any of those vendors or contractors.
* Not be subject to US sanctions or reside in a US-embargoed country.
* Be at least 18 years of age or, if younger, submit your vulnerability with the consent of your parent or guardian.
* Comply with all the eligibility requirements of the Program.

### Rewards

The Program includes the following 4 level severity scale:

* **Critical** Issues that could impact numerous users and have serious reputational, legal or financial implications. An example would be being able to lock contracts permanently or take funds from all smart pools  / users.
* **High** Issues that impact individual smart pools  / users where exploitation would pose reputational, legal or moderate financial risk to the smart pool / user.
* **Medium** The risk is relatively small and does not pose a threat to smart pool / user funds.
* **Low/Informational** The issue does not pose an immediate risk but is relevant to security best practices.

Rewards will be given based on the above severity as well as the likelihood of the bug being triggered or exploited, to be determined at the sole discretion of Rigoblock.

### Payout Calculations

| Risk Score | Payout        |
| ---------- | ------------- |
| Critical   | up to $10,000 |
| High       | up to $2,000  |
| Medium     | up to $300    |
| Low        | up to $60     |

### Other Terms

By submitting your report, you grant Rigoblock any and all rights, including intellectual property rights, needed to validate, mitigate, and disclose the vulnerability. All reward decisions, including eligibility for and amounts of the rewards and the manner in which such rewards will be paid, are made at our sole discretion. The terms and conditions of this Program may be altered at any time.
