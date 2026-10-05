# IStorageAccessible

## Overview

#### License: Apache 2.0

```solidity
interface IStorageAccessible
```

See https://github.com/gnosis/util-contracts/blob/bb5fe5fb5df6d8400998094fb1b32a178a47c3a1/contracts/StorageAccessible.sol
## Functions info

### getStorageAt (0x5624b25b)

```solidity
function getStorageAt(
    uint256 offset,
    uint256 length
) external view returns (bytes memory)
```

Reads `length` bytes of storage in the currents contract.


Parameters:

| Name   | Type    | Description                                                                     |
| :----- | :------ | :------------------------------------------------------------------------------ |
| offset | uint256 | - the offset in the current contract's storage in words to start reading from.  |
| length | uint256 | - the number of words (32 bytes) of data to read.                               |


Return values:

| Name | Type  | Description                               |
| :--- | :---- | :---------------------------------------- |
| [0]  | bytes | Bytes string of the bytes that were read. |

### getStorageSlotsAt (0xd36ed298)

```solidity
function getStorageSlotsAt(
    uint256[] memory slots
) external view returns (bytes memory)
```

Reads bytes of storage at different storage locations.

Returns a string with values regarless of where they are stored, i.e. variable, mapping or struct.


Parameters:

| Name  | Type      | Description                                |
| :---- | :-------- | :----------------------------------------- |
| slots | uint256[] | The array of storage slots to query into.  |


Return values:

| Name | Type  | Description                                                   |
| :--- | :---- | :------------------------------------------------------------ |
| [0]  | bytes | Bytes string composite of different storage locations' value. |
