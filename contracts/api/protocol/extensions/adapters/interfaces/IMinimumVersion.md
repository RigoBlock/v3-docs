# IMinimumVersion

## Overview

#### License: Apache 2.0

```solidity
interface IMinimumVersion
```


## Functions info

### requiredVersion (0x2ea6c3f0)

```solidity
function requiredVersion() external view returns (string memory)
```

Returns the minimum implementation version to use an external application.

Adapters must implement it when modifying proxy state or storage.


Return values:

| Name | Type   | Description                              |
| :--- | :----- | :--------------------------------------- |
| [0]  | string | String of the minimum supported version. |
