# GmxFallback

## Overview

#### License: Apache-2.0-or-later

```solidity
library GmxFallback
```

Hardcoded Chainlink fallback feeds for GMX synthetic index tokens
that have a Data Stream feed but no on-chain `priceFeed`.
## Functions info

### getFallbackPrice

```solidity
function getFallbackPrice(
    address token
) internal view returns (Price.Props memory price)
```

Reads a hardcoded Chainlink fallback aggregator for tokens GMX prices via Data Streams. The multiplier is computed as
`10^60 / 10^feedDecimals / 10^tokenDecimals` so that `answer * multiplier / 1e30` yields a GMX 1e30 token-unit price.
The feed address and multiplier exponent are packed as `uint168(feedAddress << 8 | exponent)`.