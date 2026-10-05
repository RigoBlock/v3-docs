# IRigoblockV3PoolImmutable

## Overview

#### License: Apache 2.0

```solidity
interface IRigoblockV3PoolImmutable
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### VERSION (0xffa1ad74)

```solidity
function VERSION() external view returns (string memory)
```

Returns a string of the pool version.


Return values:

| Name | Type   | Description                                |
| :--- | :----- | :----------------------------------------- |
| [0]  | string | String of the pool implementation version. |

### authority (0xbf7e214f)

```solidity
function authority() external view returns (address)
```

Returns the address of the authority contract.


Return values:

| Name | Type    | Description                        |
| :--- | :------ | :--------------------------------- |
| [0]  | address | Address of the authority contract. |
