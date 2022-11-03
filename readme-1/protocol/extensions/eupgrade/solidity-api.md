# Solidity API

## EUpgrade

### \_eUpgrade

```solidity
address _eUpgrade
```

### \_factory

```solidity
address _factory
```

### constructor

```solidity
constructor(address factory) public
```

### upgradeImplementation

```solidity
function upgradeImplementation() external
```

Allows caller to upgrade pool implementation.

_Cannot be called directly and in pool is restricted to pool owner._

### getBeacon

```solidity
function getBeacon() public view returns (address)
```
