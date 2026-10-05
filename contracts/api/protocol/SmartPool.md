# SmartPool

## Overview

#### License: Apache-2.0-or-later

```solidity
contract SmartPool is ISmartPool, MixinStorage, MixinFallback, MixinInitializer, MixinPoolState, MixinStorageAccessible
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### constructor

```solidity
constructor(
    address authority,
    address extensionsMap,
    address tokenJar
) MixinImmutables(authority, extensionsMap, tokenJar)
```

Owner is initialized to 0 to lock owner actions in this implementation.
