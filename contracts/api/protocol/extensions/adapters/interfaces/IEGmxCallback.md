# IEGmxCallback

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IEGmxCallback
```

GMX v2 order execution callback extension interface.
## Events info

### TrackedMarketAdded

```solidity
event TrackedMarketAdded(address indexed market)
```

Emitted when a market is added to the tracked-markets set.
### ClaimableCollateralAdded

```solidity
event ClaimableCollateralAdded(bytes32 indexed claimableCollateralKey, address indexed token, address indexed market, uint256 timeKey)
```

Emitted when a claimable-collateral key is recorded.
### TrackedMarketRemoved

```solidity
event TrackedMarketRemoved(address indexed market)
```

Emitted when a market is removed from the tracked-markets set.
### ClaimableCollateralRemoved

```solidity
event ClaimableCollateralRemoved(bytes32 indexed claimableCollateralKey)
```

Emitted when a fully-claimed collateral key is removed.
## Functions info

### afterOrderExecution (0xffaf393f)

```solidity
function afterOrderExecution(
    bytes32 key,
    EventUtils.EventLogData memory orderData,
    EventUtils.EventLogData memory eventData
) external
```

Called by GMX after an order affecting this pool is executed.


Parameters:

| Name      | Type                           | Description                           |
| :-------- | :----------------------------- | :------------------------------------ |
| key       | bytes32                        | The GMX order key.                    |
| orderData | struct EventUtils.EventLogData | Event log data describing the order.  |
| eventData | struct EventUtils.EventLogData | Additional event data from GMX.       |
