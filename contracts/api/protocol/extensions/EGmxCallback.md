# EGmxCallback

## Overview

#### License: Apache-2.0-or-later

```solidity
contract EGmxCallback is IEGmxCallback
```

GMX v2 order-execution callback extension. Records claimable collateral
rebates and tracked markets in pool storage so NAV remains accurate after full
closes, liquidations, and ADL.

Runs as an extension (always delegatecalled). Only GMX controller contracts
may invoke the callback handler.
## Errors info

### NotGmxController

```solidity
error NotGmxController()
```


### InvalidCallbackAccount

```solidity
error InvalidCallbackAccount()
```


### NotArbitrum

```solidity
error NotArbitrum()
```


## Modifiers info

### onlyGmxController

```solidity
modifier onlyGmxController()
```


## Functions info

### constructor

```solidity
constructor()
```


### afterOrderExecution (0xffaf393f)

```solidity
function afterOrderExecution(
    bytes32,
    EventUtils.EventLogData memory orderData,
    EventUtils.EventLogData memory
) external override onlyGmxController
```

Called by GMX after an order affecting this pool is executed.


Parameters:

| Name      | Type                           | Description                           |
| :-------- | :----------------------------- | :------------------------------------ |
| key       | bytes32                        | The GMX order key.                    |
| orderData | struct EventUtils.EventLogData | Event log data describing the order.  |
| eventData | struct EventUtils.EventLogData | Additional event data from GMX.       |
