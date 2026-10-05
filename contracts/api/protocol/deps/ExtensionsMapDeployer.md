# ExtensionsMapDeployer

## Overview

#### License: Apache-2.0-or-later

```solidity
contract ExtensionsMapDeployer is IExtensionsMapDeployer
```


## State variables info

### deployedMaps (0xdce99998)

```solidity
mapping(address => mapping(bytes32 => address)) deployedMaps
```


## Functions info

### deployExtensionsMap (0x6b7f179d)

```solidity
function deployExtensionsMap(
    DeploymentParams memory params,
    bytes32 salt
) external override returns (address)
```

Returns the address of the deployed contract.

If the params are unchanged, the address of the already-deployed contract is returned.
### parameters (0x89035730)

```solidity
function parameters() external view override returns (DeploymentParams memory)
```

Returns the extensions deployment parameters.


Return values:

| Name | Type                    | Description                                                 |
| :--- | :---------------------- | :---------------------------------------------------------- |
| [0]  | struct DeploymentParams | Tuple of the deployment parameters '(Extensions, address)'. |
