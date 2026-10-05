# IRigoblockV3PoolOwnerActions

## Overview

#### License: Apache 2.0

```solidity
interface IRigoblockV3PoolOwnerActions
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

### setUnitaryValue (0xed9e681c)

```solidity
function setUnitaryValue(uint256 unitaryValue) external
```

Allows pool owner to set the pool price.


Parameters:

| Name         | Type    | Description                    |
| :----------- | :------ | :----------------------------- |
| unitaryValue | uint256 | Value of 1 token in wei units. |
