---
description: The contracts of the RigoBlock protocol
---

# Protocol

{% content-ref url="core/" %}
[core](core/)
{% endcontent-ref %}

{% content-ref url="deps/" %}
[deps](deps/)
{% endcontent-ref %}

{% content-ref url="extensions/" %}
[extensions](extensions/)
{% endcontent-ref %}

{% content-ref url="proxies/" %}
[proxies](proxies/)
{% endcontent-ref %}

The interface "[IRigoblockPoolExtended](rigoblockpoolextended.md)" includes all the methods from core implementation and supported adapters. A new instance of a Rigoblock pool can be initialized by the client by attaching a Pool Proxy's address to this interface. This way, a client can initialize the pool just once and use the same instance inside the application.

The interface is not inherited by the pool implementation, as it includes the extensions' methods, which are not implemented at the core of the protocol.

#### Notice: the addition of new extensions requires the update of the interface

#### Disclaimer: contracts in the Rigoblock Protocol have NOT been audited. While 100% code coverage has been achieved, this is by no means guarantee that the software is bug-free. Please use extreme caution when interacting with the contracts and treat them as not safe until an independent audit is released.
