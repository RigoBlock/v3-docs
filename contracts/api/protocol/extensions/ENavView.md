# ENavView

## Overview

#### License: Apache-2.0-or-later

```solidity
contract ENavView is IENavView
```

Author: Gabriele Rigo - <gab@rigoblock.com>
Provides view methods to retrieve token balances and NAV without modifying state

Designed as an extension to run via delegatecall in pool context for off-chain queries

## Functions info

### constructor

```solidity
constructor(EAppsParams memory params)
```

Constructor stores immutable addresses for chain-specific contracts


Parameters:

| Name   | Type               | Description                                            |
| :----- | :----------------- | :----------------------------------------------------- |
| params | struct EAppsParams | Chain-specific addresses bundled into a single struct. |

### getAppTokensAndBalancesView (0x37ad0f03)

```solidity
function getAppTokensAndBalancesView()
    external
    view
    override
    returns (AppTokenBalance[] memory balances)
```

Returns application token balances for external positions


Return values:

| Name | Type                     | Description                                    |
| :--- | :----------------------- | :--------------------------------------------- |
| apps | struct AppTokenBalance[] | Array of AppTokenBalance structs with balances |

### getNavDataView (0x5d7d86de)

```solidity
function getNavDataView()
    external
    view
    override
    returns (NavData memory navData)
```

Returns complete NAV data for the pool


Return values:

| Name    | Type           | Description                                               |
| :------ | :------------- | :-------------------------------------------------------- |
| navData | struct NavData | Struct containing totalValue, unitaryValue, and timestamp |
