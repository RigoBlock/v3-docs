# IAMulticall

## Overview

#### License: GPL-2.0-or-later

```solidity
interface IAMulticall
```

As per https://github.com/Uniswap/swap-router-contracts/blob/main/contracts/interfaces/IMulticallExtended.sol
## Errors info

### MulticallDeadlinePast

```solidity
error MulticallDeadlinePast()
```

Thrown when the deadline has passed.
### MulticallInvalidBlockhash

```solidity
error MulticallInvalidBlockhash()
```

Thrown when the previous blockhash does not match the expected one.
## Functions info

### multicall (0xac9650d8)

```solidity
function multicall(
    bytes[] calldata data
) external returns (bytes[] memory results)
```

Enables calling multiple methods in a single call to the contract


Parameters:

| Name | Type    | Description              |
| :--- | :------ | :----------------------- |
| data | bytes[] | Array of encoded calls.  |


Return values:

| Name    | Type    | Description              |
| :------ | :------ | :----------------------- |
| results | bytes[] | Array of call responses. |

### multicall (0x5ae401dc)

```solidity
function multicall(
    uint256 deadline,
    bytes[] calldata data
) external payable returns (bytes[] memory results)
```

Call multiple functions in the current contract and return the data from all of them if they all succeed

The `msg.value` should not be trusted for any method callable from multicall.


Parameters:

| Name     | Type    | Description                                                               |
| :------- | :------ | :------------------------------------------------------------------------ |
| deadline | uint256 | The time by which this function must be called before failing             |
| data     | bytes[] | The encoded function data for each of the calls to make to this contract  |


Return values:

| Name    | Type    | Description                                           |
| :------ | :------ | :---------------------------------------------------- |
| results | bytes[] | The results from each of the calls passed in via data |

### multicall (0x1f0464d1)

```solidity
function multicall(
    bytes32 previousBlockhash,
    bytes[] calldata data
) external payable returns (bytes[] memory results)
```

Call multiple functions in the current contract and return the data from all of them if they all succeed

The `msg.value` should not be trusted for any method callable from multicall.


Parameters:

| Name              | Type    | Description                                                               |
| :---------------- | :------ | :------------------------------------------------------------------------ |
| previousBlockhash | bytes32 | The expected parent blockHash                                             |
| data              | bytes[] | The encoded function data for each of the calls to make to this contract  |


Return values:

| Name    | Type    | Description                                           |
| :------ | :------ | :---------------------------------------------------- |
| results | bytes[] | The results from each of the calls passed in via data |
