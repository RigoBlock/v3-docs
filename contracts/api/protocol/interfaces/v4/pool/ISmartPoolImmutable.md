# ISmartPoolImmutable

## Overview

#### License: Apache 2.0-or-later

```solidity
interface ISmartPoolImmutable
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

### wrappedNative (0xeb6d3a11)

```solidity
function wrappedNative() external view returns (address)
```

Returns the address of the WETH9 contract.

Used to convert WETH balances to ETH without executing an oracle call.


Return values:

| Name | Type    | Description                    |
| :--- | :------ | :----------------------------- |
| [0]  | address | Address of the WETH9 contract. |

### tokenJar (0x490c98f5)

```solidity
function tokenJar() external view returns (address)
```

Returns the address of the Rigoblock token jar contract.

Used to transfer protocol fees to the buy-back-and-burn contract.


Return values:

| Name | Type    | Description                        |
| :--- | :------ | :--------------------------------- |
| [0]  | address | Address of the token jar contract. |
