# Rigoblock Pool Extended

We have created a dedicated interface called "IRigoblockPoolExtended". This interface includes all core implementation methods and all supported adapters. A new instance of a Rigoblock pool can be initialized by the client by attaching a Pool Proxy's address to this interface. This way, the client can initialize the pool just once and use it inside the application.

#### Notice: the addition of new extensions requires the update of the interface
