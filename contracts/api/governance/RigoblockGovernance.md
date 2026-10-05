# RigoblockGovernance

## Overview

#### License: Apache-2.0-or-later

```solidity
contract RigoblockGovernance is IRigoblockGovernance, MixinStorage, MixinInitializer, MixinVoting, MixinUpgrade, MixinCrosschain
```


## Functions info

### constructor

```solidity
constructor() MixinImmutables() MixinStorage()
```

Constructor has no inputs to guarantee same deterministic address across chains.

Setting high proposal threshold locks propose action, which also lock vote actions.