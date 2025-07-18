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

### Mapping of versions to implementation addresses

* HF 3.1.0 -> 0xeb0c08Ad44af89BcBB5Ed6dD28caD452311B8516 (initial v3 implementation)
* HF 3.1.2 -> 0x7Df14Ba4a5f565cD56206e49Fc66b3002A91841d (self custody deprecated)
* 4.0.1 -> 0xe99DEC5Ba5747E8ADF81Bd58026527c7CB042108 (automated nav)
* 4.0.2 -> 0x34481A0A48A579586B3555ed80af482ad9F79EDE (first mint fix)
* 4.0.3 -> 0xa1D8d68FFa1d7fE4863101599aF09D9C60bF49D6 (burn dos fix)

HF 3.1.0 is also the initial v3 implementation, to be used in the proxy factory constructor to obtain the same deterministic deployed address for the same pool on all networks (relevant for protocol deployment on new chains).

***

The interface "[IRigoblockPoolExtended](rigoblockpoolextended.md)" includes all the methods from core implementation and supported adapters. A new instance of a Rigoblock pool can be initialized by the client by attaching a Pool Proxy's address to this interface. This way, a client can initialize the pool just once and use the same instance inside the application.

The interface is not inherited by the pool implementation, as it includes the extensions' methods, which are not implemented at the core of the protocol. Generally speaking, the implementation accepts transactions in the same format as the external applications' ABI specification, therefore a user looking to underact i.e. with the Uniswap universal router through the proxy, will be able to use the Uniswap sdk or api without modifications to the function selector.

#### Disclaimer: contracts in the Rigoblock Protocol have not been audited. While 98% code coverage has been achieved, this is by no means a guarantee that the software is bug-free.
