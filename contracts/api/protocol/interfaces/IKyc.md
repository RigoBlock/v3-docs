# IKyc

## Overview

#### License: Apache 2.0

```solidity
interface IKyc
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### isWhitelistedUser (0xd88c271e)

```solidity
function isWhitelistedUser(address user) external view returns (bool)
```

Returns whether an address has been whitelisted.


Parameters:

| Name | Type    | Description             |
| :--- | :------ | :---------------------- |
| user | address | The address to verify.  |


Return values:

| Name | Type | Description                   |
| :--- | :--- | :---------------------------- |
| [0]  | bool | Bool the user is whitelisted. |
