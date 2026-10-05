# IAssetData

## Overview

#### License: Apache 2.0

```solidity
interface IAssetData
```


## Functions info

### ERC20Token (0xf47261b0)

```solidity
function ERC20Token(address tokenAddress) external
```

Function signature for encoding ERC20 assetData.


Parameters:

| Name         | Type    | Description                     |
| :----------- | :------ | :------------------------------ |
| tokenAddress | address | Address of ERC20Token contract. |

### ERC721Token (0x02571792)

```solidity
function ERC721Token(address tokenAddress, uint256 tokenId) external
```

Function signature for encoding ERC721 assetData.


Parameters:

| Name         | Type    | Description                           |
| :----------- | :------ | :------------------------------------ |
| tokenAddress | address | Address of ERC721 token contract.     |
| tokenId      | uint256 | Id of ERC721 token to be transferred. |

### ERC1155Assets (0xa7cb5fb7)

```solidity
function ERC1155Assets(
    address tokenAddress,
    uint256[] calldata tokenIds,
    uint256[] calldata values,
    bytes calldata callbackData
) external
```

Function signature for encoding ERC1155 assetData.


Parameters:

| Name         | Type      | Description                                                                                                                                                               |
| :----------- | :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| tokenAddress | address   | Address of ERC1155 token contract.                                                                                                                                        |
| tokenIds     | uint256[] | Array of ids of tokens to be transferred.                                                                                                                                 |
| values       | uint256[] | Array of values that correspond to each token id to be transferred. Note that each value will be multiplied by the amount being filled in the order before transferring.  |
| callbackData | bytes     | Extra data to be passed to receiver's `onERC1155Received` callback function.                                                                                              |

### MultiAsset (0x94cfcdd7)

```solidity
function MultiAsset(
    uint256[] calldata values,
    bytes[] calldata nestedAssetData
) external
```

Function signature for encoding MultiAsset assetData.


Parameters:

| Name            | Type      | Description                                                                                                                                                             |
| :-------------- | :-------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| values          | uint256[] | Array of amounts that correspond to each asset to be transferred. Note that each value will be multiplied by the amount being filled in the order before transferring.  |
| nestedAssetData | bytes[]   | Array of assetData fields that will be be dispatched to their correspnding AssetProxy contract.                                                                         |

### StaticCall (0xc339d10a)

```solidity
function StaticCall(
    address staticCallTargetAddress,
    bytes calldata staticCallData,
    bytes32 expectedReturnDataHash
) external
```

Function signature for encoding StaticCall assetData.


Parameters:

| Name                    | Type    | Description                                                                |
| :---------------------- | :------ | :------------------------------------------------------------------------- |
| staticCallTargetAddress | address | Address that will execute the staticcall.                                  |
| staticCallData          | bytes   | Data that will be executed via staticcall on the staticCallTargetAddress.  |
| expectedReturnDataHash  | bytes32 | Keccak-256 hash of the expected staticcall return data.                    |

### ERC20Bridge (0xdc1600f3)

```solidity
function ERC20Bridge(
    address tokenAddress,
    address bridgeAddress,
    bytes calldata bridgeData
) external
```

Function signature for encoding ERC20Bridge assetData.


Parameters:

| Name          | Type    | Description                                         |
| :------------ | :------ | :-------------------------------------------------- |
| tokenAddress  | address | Address of token to transfer.                       |
| bridgeAddress | address | Address of the bridge contract.                     |
| bridgeData    | bytes   | Arbitrary data to be passed to the bridge contract. |
