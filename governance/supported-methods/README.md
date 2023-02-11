# Supported Methods

The Rigoblock protocols requires adapters that communicate with external applications to be explicitly approved. Once an adapter is approved, the adapter methods can be added to the protocol by adding a mapping of selector to adapter. This way, the protocol correctly routes external calls by making the preemptive checks within said adapters. Once an adapter has been added, the governance can remove it by voting. Certain wallets hold governance permit to add-remove methods. Adding and removing methods of preemptively approved adapters does not require governance voting.
