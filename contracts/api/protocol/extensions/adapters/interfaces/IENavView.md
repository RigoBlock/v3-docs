# IENavView

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IENavView
```

Author: Gabriele Rigo - <gab@rigoblock.com>
Provides view methods to retrieve token balances and NAV without modifying state

Designed for off-chain queries like DeFiLlama, subgraphs, or ZK proof generation

## Functions info

### getNavDataView (0x5d7d86de)

```solidity
function getNavDataView() external view returns (NavData memory navData)
```

Returns complete NAV data for the pool


Return values:

| Name    | Type           | Description                                               |
| :------ | :------------- | :-------------------------------------------------------- |
| navData | struct NavData | Struct containing totalValue, unitaryValue, and timestamp |

### getAppTokensAndBalancesView (0x37ad0f03)

```solidity
function getAppTokensAndBalancesView()
    external
    view
    returns (AppTokenBalance[] memory apps)
```

Returns application token balances for external positions


Return values:

| Name | Type                     | Description                                    |
| :--- | :----------------------- | :--------------------------------------------- |
| apps | struct AppTokenBalance[] | Array of AppTokenBalance structs with balances |
