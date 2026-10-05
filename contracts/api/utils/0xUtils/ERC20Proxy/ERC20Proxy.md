# ERC20Proxy

## Overview

#### License: Apache 2.0

```solidity
contract ERC20Proxy is MixinAuthorizable
```


## Functions info

### constructor

```solidity
constructor(address _owner) Ownable(_owner)
```


### fallback

```solidity
fallback() external
```


### getProxyId (0xae25532e)

```solidity
function getProxyId() external pure returns (bytes4)
```

Gets the proxy id associated with the proxy address.


Return values:

| Name | Type   | Description |
| :--- | :----- | :---------- |
| [0]  | bytes4 | Proxy id.   |
