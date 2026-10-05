# MixinConstants

## Overview

#### License: Apache 2.0-or-later

```solidity
abstract contract MixinConstants is ISmartPool
```

Constants are copied in the bytecode and not assigned a storage slot, can safely be added to this contract.

Inheriting from interface is required as we override public variables.
## Constants info

### VERSION (0xffa1ad74)

```solidity
string constant VERSION = "4.4.7"
```

