# IExtensionsMapDeployer

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IExtensionsMapDeployer
```


## Functions info

### deployedMaps (0xdce99998)

```solidity
function deployedMaps(
    address deployer,
    bytes32 salt
) external view returns (address mapAddress)
```

Returns the nonce of the deployed ExtensionsMap contract.

It is increased only when a new contract is deployed.


Parameters:

| Name     | Type    | Description                                                   |
| :------- | :------ | :------------------------------------------------------------ |
| deployer | address | Address of the deployer wallet.                               |
| salt     | bytes32 | Bytes32 input to allow multi-chain deterministic deployment.  |


Return values:

| Name       | Type    | Description                     |
| :--------- | :------ | :------------------------------ |
| mapAddress | address | Address of the mapped contract. |

### deployExtensionsMap (0x6b7f179d)

```solidity
function deployExtensionsMap(
    DeploymentParams memory params,
    bytes32 salt
) external returns (address)
```

Returns the address of the deployed contract.

If the params are unchanged, the address of the already-deployed contract is returned.
### parameters (0x89035730)

```solidity
function parameters() external view returns (DeploymentParams memory)
```

Returns the extensions deployment parameters.


Return values:

| Name | Type                    | Description                                                 |
| :--- | :---------------------- | :---------------------------------------------------------- |
| [0]  | struct DeploymentParams | Tuple of the deployment parameters '(Extensions, address)'. |
