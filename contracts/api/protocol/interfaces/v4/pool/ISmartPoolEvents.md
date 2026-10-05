# ISmartPoolEvents

## Overview

#### License: Apache 2.0-or-later

```solidity
interface ISmartPoolEvents
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Events info

### PoolInitialized

```solidity
event PoolInitialized(address indexed group, address indexed owner, address indexed baseToken, string name, bytes8 symbol)
```

Emitted when a new pool is initialized.

Pool is initialized at new pool creation.


Parameters:

| Name      | Type    | Description                 |
| :-------- | :------ | :-------------------------- |
| group     | address | Address of the factory.     |
| owner     | address | Address of the owner.       |
| baseToken | address | Address of the base token.  |
| name      | string  | String name of the pool.    |
| symbol    | bytes8  | String symbol of the pool.  |

### NewOwner

```solidity
event NewOwner(address indexed old, address indexed current)
```

Emitted when new owner is set.


Parameters:

| Name    | Type    | Description                     |
| :------ | :------ | :------------------------------ |
| old     | address | Address of the previous owner.  |
| current | address | Address of the new owner.       |

### Transfer

```solidity
event Transfer(address indexed from, address indexed to, uint256 value)
```

Emitted when pool tokens are minted or burned.

Shares are non-transferable: this event is only emitted by mint/burn flows.


Parameters:

| Name  | Type    | Description                                     |
| :---- | :------ | :---------------------------------------------- |
| from  | address | Address sending to the pool or burning from.    |
| to    | address | Address receiving from the pool or burning to.  |
| value | uint256 | Number of pool token units.                     |

### NewNav

```solidity
event NewNav(address indexed sender, address indexed pool, uint256 unitaryValue)
```

Emitted when NAV storage is updated.


Parameters:

| Name         | Type    | Description                                 |
| :----------- | :------ | :------------------------------------------ |
| sender       | address | Address of the wallet prompting an update.  |
| pool         | address | Address of the pool.                        |
| unitaryValue | uint256 | Value of 1 token in wei units.              |

### NewFee

```solidity
event NewFee(address indexed pool, address indexed who, uint16 transactionFee)
```

Emitted when pool operator sets new mint fee.


Parameters:

| Name           | Type    | Description                               |
| :------------- | :------ | :---------------------------------------- |
| pool           | address | Address of the pool.                      |
| who            | address | Address that is sending the transaction.  |
| transactionFee | uint16  | Number of the new fee in wei.             |

### NewCollector

```solidity
event NewCollector(address indexed pool, address indexed who, address feeCollector)
```

Emitted when pool operator updates fee collector address.


Parameters:

| Name         | Type    | Description                               |
| :----------- | :------ | :---------------------------------------- |
| pool         | address | Address of the pool.                      |
| who          | address | Address that is sending the transaction.  |
| feeCollector | address | Address of the new fee collector.         |

### MinimumPeriodChanged

```solidity
event MinimumPeriodChanged(address indexed pool, uint48 minimumPeriod)
```

Emitted when pool operator updates minimum holding period.


Parameters:

| Name          | Type    | Description           |
| :------------ | :------ | :-------------------- |
| pool          | address | Address of the pool.  |
| minimumPeriod | uint48  | Number of seconds.    |

### SpreadChanged

```solidity
event SpreadChanged(address indexed pool, uint16 spread)
```

Emitted when pool operator updates the mint/burn spread.


Parameters:

| Name   | Type    | Description                           |
| :----- | :------ | :------------------------------------ |
| pool   | address | Address of the pool.                  |
| spread | uint16  | Number of the spread in basis points. |

### KycProviderSet

```solidity
event KycProviderSet(address indexed pool, address indexed kycProvider)
```

Emitted when pool operator sets a kyc provider.


Parameters:

| Name        | Type    | Description                  |
| :---------- | :------ | :--------------------------- |
| pool        | address | Address of the pool.         |
| kycProvider | address | Address of the kyc provider. |

### OperatorSet

```solidity
event OperatorSet(address indexed holder, address indexed operator, bool approved)
```

Emitted when a user sets an operator.


Parameters:

| Name     | Type    | Description                                   |
| :------- | :------ | :-------------------------------------------- |
| holder   | address | Address of the user.                          |
| operator | address | Address of the operator.                      |
| approved | bool    | Boolean the operator is approved by the user. |

### DelegationUpdated

```solidity
event DelegationUpdated(address indexed pool, address indexed delegated, bytes4 indexed selector, bool isDelegated)
```

Emitted when a selector delegation is added or removed by the pool owner.


Parameters:

| Name        | Type    | Description                                   |
| :---------- | :------ | :-------------------------------------------- |
| pool        | address | Address of the pool.                          |
| delegated   | address | Address whose delegation status changed.      |
| selector    | bytes4  | Function selector whose access was updated.   |
| isDelegated | bool    | True if access was granted, false if revoked. |

### TokenStatusChanged

```solidity
event TokenStatusChanged(address indexed token, bool isActive)
```

Emitted when a token's active status changes in the pool.


Parameters:

| Name     | Type    | Description                                        |
| :------- | :------ | :------------------------------------------------- |
| token    | address | Address of the token whose status changed.         |
| isActive | bool    | True if token was activated, false if deactivated. |
