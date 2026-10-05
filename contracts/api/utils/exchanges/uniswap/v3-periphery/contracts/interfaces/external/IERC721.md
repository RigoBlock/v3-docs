# IERC721

## Overview

#### License: Apache 2.0

```solidity
interface IERC721
```


## Functions info

### ownerOf (0x6352211e)

```solidity
function ownerOf(uint256 tokenId) external view returns (address owner)
```

Returns the owner of a given id.


Parameters:

| Name    | Type    | Description              |
| :------ | :------ | :----------------------- |
| tokenId | uint256 | Number of the token id.  |


Return values:

| Name  | Type    | Description                 |
| :---- | :------ | :-------------------------- |
| owner | address | Address of the token owner. |
