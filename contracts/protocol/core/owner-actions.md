# owner actions

## MixinOwnerActions

### notPriceError

```solidity
modifier notPriceError(uint256 newUnitaryValue)
```

_We keep this check to prevent accidental failure in Nav calculations._

### onlyOwner

```solidity
modifier onlyOwner()
```

### changeFeeCollector

```solidity
function changeFeeCollector(address feeCollector) external
```

Allows owner to decide where to receive the fee.

#### Parameters

| Name         | Type    | Description                  |
| ------------ | ------- | ---------------------------- |
| feeCollector | address | Address of the fee receiver. |

### changeMinPeriod

```solidity
function changeMinPeriod(uint48 minPeriod) external
```

Allows pool owner to change the minimum holding period.

#### Parameters

| Name      | Type   | Description      |
| --------- | ------ | ---------------- |
| minPeriod | uint48 | Time in seconds. |

### changeSpread

```solidity
function changeSpread(uint16 newSpread) external
```

Allows pool owner to change the mint/burn spread.

#### Parameters

| Name      | Type   | Description                                 |
| --------- | ------ | ------------------------------------------- |
| newSpread | uint16 | Number between 0 and 1000, in basis points. |

### setKycProvider

```solidity
function setKycProvider(address kycProvider) external
```

Allows pool owner to set/update the user whitelist contract.

_Kyc provider can be set to null, removing user whitelist requirement._

#### Parameters

| Name        | Type    | Description                  |
| ----------- | ------- | ---------------------------- |
| kycProvider | address | Address if the kyc provider. |

### setTransactionFee

```solidity
function setTransactionFee(uint16 transactionFee) external
```

Allows pool owner to set the transaction fee.

#### Parameters

| Name           | Type   | Description                                   |
| -------------- | ------ | --------------------------------------------- |
| transactionFee | uint16 | Value of the transaction fee in basis points. |

### setUnitaryValue

```solidity
function setUnitaryValue(uint256 unitaryValue) external
```

Allows pool owner to set the pool price.

#### Parameters

| Name         | Type    | Description                    |
| ------------ | ------- | ------------------------------ |
| unitaryValue | uint256 | Value of 1 token in wei units. |

### setOwner

```solidity
function setOwner(address newOwner) public
```

Allows pool owner to set a new owner address.

_Method restricted to owner._

#### Parameters

| Name     | Type    | Description               |
| -------- | ------- | ------------------------- |
| newOwner | address | Address of the new owner. |

### totalSupply

```solidity
function totalSupply() public view virtual returns (uint256)
```

Returns the total amount of issued tokens for this pool.

#### Return Values

| Name | Type    | Description                    |
| ---- | ------- | ------------------------------ |
| \[0] | uint256 | Number of total issued tokens. |

### decimals

```solidity
function decimals() public view virtual returns (uint8)
```

Returns token decimals.

#### Return Values

| Name | Type  | Description               |
| ---- | ----- | ------------------------- |
| \[0] | uint8 | Uint8 number of decimals. |

### \_getUnitaryValue

```solidity
function _getUnitaryValue() internal view virtual returns (uint256)
```

### \_isContract

```solidity
function _isContract(address target) private view returns (bool)
```
