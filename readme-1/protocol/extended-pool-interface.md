# Extended Pool Interface

The interface "IRigoblockPoolExtended" includes all core implementation methods and all supported adapters. A new instance of a Rigoblock pool can be initialized by the client by attaching a Pool Proxy's address to this interface. This way, the client can initialize the pool just once and use it inside the application.

The interface is not inherited by the pool implementation, as it includes the extensions' methods, which are not implemented at the core of the protocol.

#### Notice: the addition of new extensions requires the update of the interface
