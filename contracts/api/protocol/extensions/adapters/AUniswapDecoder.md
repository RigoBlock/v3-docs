# AUniswapDecoder

## Overview

#### License: Apache 2.0

```solidity
abstract contract AUniswapDecoder
```


## Structs info

### Parameters

```solidity
struct Parameters {
	uint256 value;
	address[] recipients;
	address[] tokensIn;
	address[] tokensOut;
}
```


### Position

```solidity
struct Position {
	address hook;
	uint256 tokenId;
	uint256 action;
}
```

Each liquidity position has its associated hook address, which can be null if no hook is used.