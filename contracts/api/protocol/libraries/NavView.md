# NavView

## Overview

#### License: Apache-2.0-or-later

```solidity
library NavView
```

Author: Gabriele Rigo - <gab@rigoblock.com>
Provides internal functions to calculate NAV and retrieve application balances

This library contains the core logic for the ENavView extension

## Functions info

### getAppTokenBalances

```solidity
function getAppTokenBalances(
    address pool,
    address grgStakingProxy,
    address uniV4Posm
) internal view returns (AppTokenBalance[] memory balances)
```


### getNavData

```solidity
function getNavData(
    address pool,
    address grgStakingProxy,
    address uniV4Posm
) internal view returns (NavData memory)
```

