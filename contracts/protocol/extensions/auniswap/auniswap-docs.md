# Solidity API

## AUniswap

### uniswapRouter02

```solidity
address uniswapRouter02
```

Returns the address of the Uniswap swap router contract.

#### Return Values

### uniswapv3Npm

```solidity
address uniswapv3Npm
```

Returns the address of the Uniswap NPM contract.

#### Return Values

### weth

```solidity
address weth
```

Returns the address of the Weth contract.

#### Return Values

### constructor

```solidity
constructor(address newUniswapRouter02) public
```

### swapExactTokensForTokens

```solidity
function swapExactTokensForTokens(uint256 amountIn, uint256 amountOutMin, address[] path, address to) external returns (uint256 amountOut)
```

Swaps `amountIn` of one token for as much as possible of another token.

_Setting `amountIn` to 0 will cause the contract to look up its own balance, and swap the entire amount, enabling contracts to send tokens before calling this function._

#### Parameters

| Name         | Type       | Description                                         |
| ------------ | ---------- | --------------------------------------------------- |
| amountIn     | uint256    | The amount of token to swap.                        |
| amountOutMin | uint256    | The minimum amount of output that must be received. |
| path         | address\[] | The ordered list of tokens to swap through.         |
| to           | address    | The recipient address.                              |

#### Return Values

| Name      | Type    | Description                       |
| --------- | ------- | --------------------------------- |
| amountOut | uint256 | The amount of the received token. |

### swapTokensForExactTokens

```solidity
function swapTokensForExactTokens(uint256 amountOut, uint256 amountInMax, address[] path, address to) external returns (uint256 amountIn)
```

Swaps as little as possible of one token for an exact amount of another token.

#### Parameters

| Name        | Type       | Description                                           |
| ----------- | ---------- | ----------------------------------------------------- |
| amountOut   | uint256    | The amount of token to swap for.                      |
| amountInMax | uint256    | The maximum amount of input that the caller will pay. |
| path        | address\[] | The ordered list of tokens to swap through.           |
| to          | address    | The recipient address.                                |

#### Return Values

| Name     | Type    | Description                 |
| -------- | ------- | --------------------------- |
| amountIn | uint256 | The amount of token to pay. |

### exactInputSingle

```solidity
function exactInputSingle(struct IV3SwapRouter.ExactInputSingleParams params) external returns (uint256 amountOut)
```

Swaps `amountIn` of one token for as much as possible of another token.

#### Parameters

| Name   | Type                                        | Description                                                                           |
| ------ | ------------------------------------------- | ------------------------------------------------------------------------------------- |
| params | struct IV3SwapRouter.ExactInputSingleParams | The parameters necessary for the swap, encoded as `ExactInputSingleParams` in memory. |

#### Return Values

| Name      | Type    | Description                       |
| --------- | ------- | --------------------------------- |
| amountOut | uint256 | The amount of the received token. |

### exactInput

```solidity
function exactInput(struct IV3SwapRouter.ExactInputParams params) external returns (uint256 amountOut)
```

Swaps `amountIn` of one token for as much as possible of another along the specified path.

#### Parameters

| Name   | Type                                  | Description                                                                               |
| ------ | ------------------------------------- | ----------------------------------------------------------------------------------------- |
| params | struct IV3SwapRouter.ExactInputParams | The parameters necessary for the multi-hop swap, encoded as `ExactInputParams` in memory. |

#### Return Values

| Name      | Type    | Description                       |
| --------- | ------- | --------------------------------- |
| amountOut | uint256 | The amount of the received token. |

### exactOutputSingle

```solidity
function exactOutputSingle(struct IV3SwapRouter.ExactOutputSingleParams params) external returns (uint256 amountIn)
```

Swaps as little as possible of one token for `amountOut` of another token.

#### Parameters

| Name   | Type                                         | Description                                                                            |
| ------ | -------------------------------------------- | -------------------------------------------------------------------------------------- |
| params | struct IV3SwapRouter.ExactOutputSingleParams | The parameters necessary for the swap, encoded as `ExactOutputSingleParams` in memory. |

#### Return Values

| Name     | Type    | Description                    |
| -------- | ------- | ------------------------------ |
| amountIn | uint256 | The amount of the input token. |

### exactOutput

```solidity
function exactOutput(struct IV3SwapRouter.ExactOutputParams params) external returns (uint256 amountIn)
```

Swaps as little as possible of one token for `amountOut` of another along the specified path (reversed).

#### Parameters

| Name   | Type                                   | Description                                                                                |
| ------ | -------------------------------------- | ------------------------------------------------------------------------------------------ |
| params | struct IV3SwapRouter.ExactOutputParams | The parameters necessary for the multi-hop swap, encoded as `ExactOutputParams` in memory. |

#### Return Values

| Name     | Type    | Description                    |
| -------- | ------- | ------------------------------ |
| amountIn | uint256 | The amount of the input token. |

### sweepToken

```solidity
function sweepToken(address token, uint256 amountMinimum) external
```

Transfers the full amount of a token held by this contract to recipient.

_The amountMinimum parameter prevents malicious contracts from stealing the token from users._

#### Parameters

| Name          | Type    | Description                                                                 |
| ------------- | ------- | --------------------------------------------------------------------------- |
| token         | address | The contract address of the token which will be transferred to `recipient`. |
| amountMinimum | uint256 | The minimum amount of token required for a transfer.                        |

### sweepToken

```solidity
function sweepToken(address token, uint256 amountMinimum, address recipient) external
```

Transfers the full amount of a token held by this contract to recipient.

_The amountMinimum parameter prevents malicious contracts from stealing the token from users._

#### Parameters

| Name          | Type    | Description                                                                 |
| ------------- | ------- | --------------------------------------------------------------------------- |
| token         | address | The contract address of the token which will be transferred to `recipient`. |
| amountMinimum | uint256 | The minimum amount of token required for a transfer.                        |
| recipient     | address | The destination address of the token.                                       |

### sweepTokenWithFee

```solidity
function sweepTokenWithFee(address token, uint256 amountMinimum, uint256 feeBips, address feeRecipient) external
```

Transfers the full amount of a token held by this contract to recipient, with a percentage between 0 (exclusive) and 1 (inclusive) going to feeRecipient.

_The amountMinimum parameter prevents malicious contracts from stealing the token from users._

#### Parameters

| Name          | Type    | Description                                                                 |
| ------------- | ------- | --------------------------------------------------------------------------- |
| token         | address | The contract address of the token which will be transferred to `recipient`. |
| amountMinimum | uint256 | The minimum amount of token required for a transfer.                        |
| feeBips       | uint256 | The amount of fee in basis points.                                          |
| feeRecipient  | address | The destination address of the token.                                       |

### sweepTokenWithFee

```solidity
function sweepTokenWithFee(address token, uint256 amountMinimum, address recipient, uint256 feeBips, address feeRecipient) external
```

Transfers the full amount of a token held by this contract to recipient, with a percentage between 0 (exclusive) and 1 (inclusive) going to feeRecipient.

_The amountMinimum parameter prevents malicious contracts from stealing the token from users._

#### Parameters

| Name          | Type    | Description                                                                 |
| ------------- | ------- | --------------------------------------------------------------------------- |
| token         | address | The contract address of the token which will be transferred to `recipient`. |
| amountMinimum | uint256 | The minimum amount of token required for a transfer.                        |
| recipient     | address | The destination address of the token.                                       |
| feeBips       | uint256 | The amount of fee in basis points.                                          |
| feeRecipient  | address | The destination address of the token.                                       |

### unwrapWETH9

```solidity
function unwrapWETH9(uint256 amountMinimum) external
```

Unwraps the contract's WETH9 balance and sends it to recipient as ETH.

_The amountMinimum parameter prevents malicious contracts from stealing WETH9 from users._

#### Parameters

| Name          | Type    | Description                            |
| ------------- | ------- | -------------------------------------- |
| amountMinimum | uint256 | The minimum amount of WETH9 to unwrap. |

### unwrapWETH9

```solidity
function unwrapWETH9(uint256 amountMinimum, address recipient) external
```

Unwraps ETH from WETH9.

#### Parameters

| Name          | Type    | Description                                    |
| ------------- | ------- | ---------------------------------------------- |
| amountMinimum | uint256 | The minimum amount of WETH9 to unwrap.         |
| recipient     | address | The address to keep same uniswap npm selector. |

### unwrapWETH9WithFee

```solidity
function unwrapWETH9WithFee(uint256 amountMinimum, uint256 feeBips, address feeRecipient) external virtual
```

Unwraps the contract's WETH9 balance and sends it to recipient as ETH, with a percentage between 0 (exclusive), and 1 (inclusive) going to feeRecipient.

_The amountMinimum parameter prevents malicious contracts from stealing WETH9 from users._

#### Parameters

| Name          | Type    | Description                                          |
| ------------- | ------- | ---------------------------------------------------- |
| amountMinimum | uint256 | The minimum amount of token required for a transfer. |
| feeBips       | uint256 | The amount of fee in basis points.                   |
| feeRecipient  | address | The destination address of the token.                |

### unwrapWETH9WithFee

```solidity
function unwrapWETH9WithFee(uint256 amountMinimum, address recipient, uint256 feeBips, address feeRecipient) external virtual
```

Unwraps the contract's WETH9 balance and sends it to recipient as ETH, with a percentage between 0 (exclusive), and 1 (inclusive) going to feeRecipient.

_The amountMinimum parameter prevents malicious contracts from stealing WETH9 from users._

#### Parameters

| Name          | Type    | Description                                          |
| ------------- | ------- | ---------------------------------------------------- |
| amountMinimum | uint256 | The minimum amount of token required for a transfer. |
| recipient     | address | The destination address of the token.                |
| feeBips       | uint256 | The amount of fee in basis points.                   |
| feeRecipient  | address | The destination address of the token.                |

### wrapETH

```solidity
function wrapETH(uint256 value) external
```

Wraps ETH.

_Client must wrap if input is native currency._

#### Parameters

| Name  | Type    | Description                   |
| ----- | ------- | ----------------------------- |
| value | uint256 | The ETH amount to be wrapped. |

### refundETH

```solidity
function refundETH() external virtual
```

Allows sending pool transactions exactly as Uniswap original transactions.

_Declared virtual as we never send ETH to Uniswap router contract._

### \_safeApprove

```solidity
function _safeApprove(address token, address spender, uint256 value) internal
```

### \_assertTokenWhitelisted

```solidity
function _assertTokenWhitelisted(address token) internal view
```

### \_getUniswapNpm

```solidity
function _getUniswapNpm() internal view returns (address)
```

### \_isContract

```solidity
function _isContract(address target) internal view returns (bool)
```

### \_getUniswapRouter2

```solidity
function _getUniswapRouter2() private view returns (address)
```

### \_getWeth

```solidity
function _getWeth() private view returns (address)
```
