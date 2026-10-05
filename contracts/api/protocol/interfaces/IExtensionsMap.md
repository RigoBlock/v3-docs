# IExtensionsMap

## Overview

#### License: Apache 2.0

```solidity
interface IExtensionsMap
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### eApps (0x99e150a6)

```solidity
function eApps() external view returns (address)
```

Returns the address of the applications extension contract.
### eNavView (0x61969e2f)

```solidity
function eNavView() external view returns (address)
```

Returns the address of the navigation view extension contract.
### eOracle (0xcc72e81a)

```solidity
function eOracle() external view returns (address)
```

Returns the address of the oracle extension contract
### eUpgrade (0x86d087ed)

```solidity
function eUpgrade() external view returns (address)
```

Returns the address of the upgrade extension contract.
### eCrosschain (0x423f09c9)

```solidity
function eCrosschain() external view returns (address)
```

Returns the address of the cross-chain handler extension contract.
### eGmxCallback (0x83b740ce)

```solidity
function eGmxCallback() external view returns (address)
```

Returns the address of the GMX v2 callback extension contract.
### eErc20 (0xdbd748cc)

```solidity
function eErc20() external view returns (address)
```

Returns the address of the disabled ERC20 methods extension contract.
### wrappedNative (0xeb6d3a11)

```solidity
function wrappedNative() external view returns (address)
```

Returns the address of the wrapped native token.

It is used for initializing it in the pool implementation immutable storage without passing it in the constructor.
### getExtensionBySelector (0xe7359f22)

```solidity
function getExtensionBySelector(
    bytes4 selector
) external view returns (address extension, bool shouldDelegatecall)
```

Returns the map of an extension's selector.

Stores all extensions selectors and addresses in its bytecode for gas efficiency.


Parameters:

| Name     | Type   | Description                          |
| :------- | :----- | :----------------------------------- |
| selector | bytes4 | Selector of the function signature.  |


Return values:

| Name               | Type    | Description                                        |
| :----------------- | :------ | :------------------------------------------------- |
| extension          | address | Address of the target extensions.                  |
| shouldDelegatecall | bool    | Boolean if should maintain context of call or not. |
