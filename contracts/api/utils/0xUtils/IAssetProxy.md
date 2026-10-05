# IAssetProxy

## Overview

#### License: Apache 2.0

```solidity
abstract contract IAssetProxy
```


## Functions info

### transferFrom (0xa85e59e4)

```solidity
function transferFrom(
    bytes calldata assetData,
    address from,
    address to,
    uint256 amount
) external virtual
```

Transfers assets. Either succeeds or throws.


Parameters:

| Name      | Type    | Description                                         |
| :-------- | :------ | :-------------------------------------------------- |
| assetData | bytes   | Byte array encoded for the respective asset proxy.  |
| from      | address | Address to transfer asset from.                     |
| to        | address | Address to transfer asset to.                       |
| amount    | uint256 | Amount of asset to transfer.                        |

### getProxyId (0xae25532e)

```solidity
function getProxyId() external pure virtual returns (bytes4)
```

Gets the proxy id associated with the proxy address.


Return values:

| Name | Type   | Description |
| :--- | :----- | :---------- |
| [0]  | bytes4 | Proxy id.   |
