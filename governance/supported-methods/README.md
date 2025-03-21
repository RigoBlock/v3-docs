# Supported Methods

Notice: in Rigoblock V4, extensions are hardcoded in the implementation via the ExtensionsMap contract, and therefore not upgradable. Adapters are upgradable, as they are intended for use with external applications.

The Rigoblock protocols requires adapters that communicate with external applications to be explicitly approved. Once an adapter is approved, the adapter methods can be added to the protocol by adding a mapping of selector to adapter. This way, the protocol correctly routes external calls by making the preemptive checks within said adapters. Once an adapter has been added, the governance can remove it by voting. Certain wallets hold governance permit to add-remove methods. Adding and removing methods of preemptively approved adapters does not require governance voting. Things are subject to change as a governance or protocol upgrade could modify these requirements.
