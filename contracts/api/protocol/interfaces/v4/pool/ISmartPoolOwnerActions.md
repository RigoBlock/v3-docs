# ISmartPoolOwnerActions

## Overview

#### License: Apache 2.0-or-later

```solidity
interface ISmartPoolOwnerActions
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### changeFeeCollector (0x9245290d)

```solidity
function changeFeeCollector(address feeCollector) external
```

Allows owner to decide where to receive the fee.


Parameters:

| Name         | Type    | Description                  |
| :----------- | :------ | :--------------------------- |
| feeCollector | address | Address of the fee receiver. |

### changeMinPeriod (0x9d604df6)

```solidity
function changeMinPeriod(uint48 minPeriod) external
```

Allows pool owner to change the minimum holding period.


Parameters:

| Name      | Type   | Description      |
| :-------- | :----- | :--------------- |
| minPeriod | uint48 | Time in seconds. |

### changeSpread (0xed4fd3cc)

```solidity
function changeSpread(uint16 newSpread) external
```

Allows pool owner to change the mint/burn spread.


Parameters:

| Name      | Type   | Description                                 |
| :-------- | :----- | :------------------------------------------ |
| newSpread | uint16 | Number between 0 and 1000, in basis points. |

### purgeInactiveTokensAndApps (0x7ace8b8d)

```solidity
function purgeInactiveTokensAndApps() external
```

Allows the owner to remove all inactive token and applications.

This is the only endpoint that has access to removing a token from the active tokens tuple.

Used to reduce cost of mint/burn as more tokens are traded, and allow lower gas for hft.
### setAcceptableMintToken (0x0dd56740)

```solidity
function setAcceptableMintToken(address token, bool isAccepted) external
```

Allows the owner to set acceptable mint tokens other than the base token.


Parameters:

| Name       | Type    | Description                                                                   |
| :--------- | :------ | :---------------------------------------------------------------------------- |
| token      | address | Address of the target token.                                                  |
| isAccepted | bool    | Boolean to indicate whether the token is to be added or removed from storage. |

### setKycProvider (0xdf0795aa)

```solidity
function setKycProvider(address kycProvider) external
```

Allows pool owner to set/update the user whitelist contract.

Kyc provider can be set to null, removing user whitelist requirement.


Parameters:

| Name        | Type    | Description                  |
| :---------- | :------ | :--------------------------- |
| kycProvider | address | Address if the kyc provider. |

### setOwner (0x13af4035)

```solidity
function setOwner(address newOwner) external
```

Allows pool owner to set a new owner address.

Method restricted to owner.


Parameters:

| Name     | Type    | Description               |
| :------- | :------ | :------------------------ |
| newOwner | address | Address of the new owner. |

### setTransactionFee (0xb45940f2)

```solidity
function setTransactionFee(uint16 transactionFee) external
```

Allows pool owner to set the transaction fee.


Parameters:

| Name           | Type   | Description                                   |
| :------------- | :----- | :-------------------------------------------- |
| transactionFee | uint16 | Value of the transaction fee in basis points. |

### updateDelegation (0xe5c2197e)

```solidity
function updateDelegation(Delegation[] calldata delegations) external
```

Allows pool owner to batch grant or revoke delegated adapter write access.

Each entry independently adds or removes one (selector, address) pair.
Emits DelegationUpdated only for entries that change storage (idempotent operations emit no event).


Parameters:

| Name        | Type                | Description                              |
| :---------- | :------------------ | :--------------------------------------- |
| delegations | struct Delegation[] | Array of delegation operations to apply. |

### revokeAllDelegations (0xf1fc2f75)

```solidity
function revokeAllDelegations(address delegated) external
```

Revokes all selector delegations for a given address in a single call.

Useful when a delegated wallet is compromised.


Parameters:

| Name      | Type    | Description                                     |
| :-------- | :------ | :---------------------------------------------- |
| delegated | address | Address whose full delegation is to be revoked. |

### revokeAllDelegationsForSelector (0x3658e24b)

```solidity
function revokeAllDelegationsForSelector(bytes4 selector) external
```

Revokes all address delegations for a given selector in a single call.

Useful when an adapter is being replaced by governance and stale delegates should be cleaned.


Parameters:

| Name     | Type   | Description                                           |
| :------- | :----- | :---------------------------------------------------- |
| selector | bytes4 | Selector whose full delegation list is to be cleared. |
