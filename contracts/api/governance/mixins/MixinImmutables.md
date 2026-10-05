# MixinImmutables

## Overview

#### License: Apache-2.0-or-later

```solidity
abstract contract MixinImmutables is MixinConstants
```

Immutables are copied in the bytecode and not assigned a storage slot

New immutables can safely be added to this contract without ordering.