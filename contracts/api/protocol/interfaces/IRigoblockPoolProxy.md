# IRigoblockPoolProxy

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IRigoblockPoolProxy
```


## Events info

### Upgraded

```solidity
event Upgraded(address indexed newImplementation)
```

Emitted when implementation written to proxy storage.

Emitted also at first variable initialization.


Parameters:

| Name              | Type    | Description                        |
| :---------------- | :------ | :--------------------------------- |
| newImplementation | address | Address of the new implementation. |
