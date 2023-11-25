---
description: The smart contract used in the RigoBlock ecosystem
---

# Contracts

{% content-ref url="protocol/" %}
[protocol](protocol/)
{% endcontent-ref %}

{% content-ref url="grg-token/" %}
[grg-token](grg-token/)
{% endcontent-ref %}

{% content-ref url="grg-staking/" %}
[grg-staking](grg-staking/)
{% endcontent-ref %}

### Mapping of versions to implementation addresses

* HF 3.1.2 -> 0x7Df14Ba4a5f565cD56206e49Fc66b3002A91841d
* HF 3.1.0 -> 0xeb0c08Ad44af89BcBB5Ed6dD28caD452311B8516

HF 3.1.0 is also the initial v3 implementation, to be used in the proxy factory constructor to obtain the same deterministic deployed address for the same pool on all networks (relevant for protocol deployment on new chains).
