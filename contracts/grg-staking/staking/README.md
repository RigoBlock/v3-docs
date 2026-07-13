---
description: Staking implementation
---

# Staking

Calls to the staking proxy that are not implemented in the proxy (i.e. logic for staking) are forwarded to the staking implementation. Storage is upgradeable but must be preserved, and new variables must be added after the existing storage declarations, otherwise there could be a storage overwrite. The staking proxy was deployed with the same storage dep as the initial staking implementation, thus ensuring that new variables, as long as added at the end of the previous storage declarations, do not generate storage clashing.

{% content-ref url="staking-docs.md" %}
[staking-docs.md](staking-docs.md)
{% endcontent-ref %}
