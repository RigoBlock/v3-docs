# storage

## MixinStorage

Storage slots must be preserved to prevent storage clashing.

_Pool storage is not sequential: each variable is wrapped into a struct which is assigned a storage slot._

### constructor

```solidity
constructor() internal
```

### Accounts

```solidity
struct Accounts {
  mapping(address => struct IRigoblockV3PoolState.UserAccount) userAccounts;
}
```

### accounts

```solidity
function accounts() internal pure returns (struct MixinStorage.Accounts s)
```

### Pool

```solidity
struct Pool {
  string name;
  bytes8 symbol;
  uint8 decimals;
  address owner;
  bool unlocked;
  address baseToken;
}
```

### pool

```solidity
function pool() internal pure returns (struct MixinStorage.Pool s)
```

### PoolWrapper

```solidity
struct PoolWrapper {
  struct MixinStorage.Pool pool;
}
```

### poolWrapper

```solidity
function poolWrapper() internal pure returns (struct MixinStorage.PoolWrapper s)
```

### poolParams

```solidity
function poolParams() internal pure returns (struct IRigoblockV3PoolState.PoolParams s)
```

### poolTokens

```solidity
function poolTokens() internal pure returns (struct IRigoblockV3PoolState.PoolTokens s)
```
