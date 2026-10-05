# ExtensionsMap

## Overview

#### License: Apache 2.0

```solidity
contract ExtensionsMap is IExtensionsMap
```

Author: Gabriele Rigo - <gab@rigoblock.com>

Its deployed address will be different on different chains and change if selectors or mapped addresses change.
## State variables info

### eApps (0x99e150a6)

```solidity
address immutable eApps
```


### eNavView (0x61969e2f)

```solidity
address immutable eNavView
```


### eOracle (0xcc72e81a)

```solidity
address immutable eOracle
```


### eUpgrade (0x86d087ed)

```solidity
address immutable eUpgrade
```


### eCrosschain (0x423f09c9)

```solidity
address immutable eCrosschain
```


### eGmxCallback (0x83b740ce)

```solidity
address immutable eGmxCallback
```


### eErc20 (0xdbd748cc)

```solidity
address immutable eErc20
```


### wrappedNative (0xeb6d3a11)

```solidity
address immutable wrappedNative
```


## Functions info

### constructor

```solidity
constructor()
```

Assumes extensions have been correctly initialized.

When adding a new app, modify apps type and assert correct params are passed to the constructor.
### getExtensionBySelector (0xe7359f22)

```solidity
function getExtensionBySelector(
    bytes4 selector
) external view override returns (address extension, bool shouldDelegatecall)
```

Returns the map of an extension's selector.

Should be called by pool with delegatecall
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
