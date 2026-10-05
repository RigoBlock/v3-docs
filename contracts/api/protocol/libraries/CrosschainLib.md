# CrosschainLib

## Overview

#### License: Apache-2.0-or-later

```solidity
library CrosschainLib
```

Provides utilities for validating bridgeable token pairs, handling BSC decimal conversions, and resolving Across handler addresses.

Used by cross-chain adapters to ensure token compatibility and proper decimal handling.
## Errors info

### UnsupportedCrossChainToken

```solidity
error UnsupportedCrossChainToken()
```


### WrongDestinationToken

```solidity
error WrongDestinationToken()
```


## Functions info

### isAllowedCrosschainToken

```solidity
function isAllowedCrosschainToken(address token) internal view returns (bool)
```

Check if a token is allowed for cross-chain operations on the current chain.


Parameters:

| Name  | Type    | Description                  |
| :---- | :------ | :--------------------------- |
| token | address | The token address to check.  |


Return values:

| Name | Type | Description                                              |
| :--- | :--- | :------------------------------------------------------- |
| [0]  | bool | True if the token is allowed for cross-chain operations. |

### applyBscDecimalConversion

```solidity
function applyBscDecimalConversion(
    address inputToken,
    address outputToken,
    uint256 amount
) internal pure returns (uint256)
```

Applies BSC decimal conversion for USDC/USDT (18 decimals on BSC vs 6 on other chains).

Handles bidirectional conversion to ensure exact cross-chain value calculation.


Parameters:

| Name        | Type    | Description                                |
| :---------- | :------ | :----------------------------------------- |
| inputToken  | address | Source token address.                      |
| outputToken | address | Destination token address.                 |
| amount      | uint256 | Original amount in source chain decimals.  |


Return values:

| Name | Type    | Description                                                           |
| :--- | :------ | :-------------------------------------------------------------------- |
| [0]  | uint256 | Normalized amount for correct cross-chain virtual supply calculation. |

### getAcrossHandler

```solidity
function getAcrossHandler(
    uint256 chainId
) internal pure returns (address handler)
```

Get the appropriate Across MulticallHandler address for a given chain.

BSC (chain ID 56) uses a different handler than other chains.


Parameters:

| Name    | Type    | Description                |
| :------ | :------ | :------------------------- |
| chainId | uint256 | The destination chain ID.  |


Return values:

| Name    | Type    | Description                                           |
| :------ | :------ | :---------------------------------------------------- |
| handler | address | The MulticallHandler address for the specified chain. |

### validateBridgeableTokenPair

```solidity
function validateBridgeableTokenPair(
    address inputToken,
    address outputToken
) internal pure
```

Validates that input and output tokens are compatible for cross-chain bridging.

Only allows bridging between tokens of the same type (USDC↔USDC, USDT↔USDT, etc.).


Parameters:

| Name        | Type    | Description                |
| :---------- | :------ | :------------------------- |
| inputToken  | address | Source token address.      |
| outputToken | address | Destination token address. |
