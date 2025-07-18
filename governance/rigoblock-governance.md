# Rigoblock Governance

Rigoblock voting power is equivalent to a wallet's GRG active stake. A proposal requires a voting power of at least 100k GRG on Ethereum mainnet, 40k GRG on L2s in order for it to be valid. A voter can vote in favor, aginst, or abstain. A proposal requires a quorum of at least 400k GRG on Ethereum mainnnet, 200k GRG on L2s. Each network is managed separately in order to maximize the cost benefit of L2, while maintaining Ethereum L1 voting on L1. This rule is subject to change as Rigoblock could later decide to leverage chain message bridging to improve running its multichain governance.

Two thirds of votes in favor are required for a proposal to be successful. Abstained votes are counted for but are not computed in the quorum or the voting for/against. The voting period starts from the start of the next GRG staking epoch and lasts for 7 days. The voting period is required to be shorter than the epoch period. If during the voting period, the proposal finds an absolute qualified majority of support, i.e. the state is final and cannot be changed by further votes against, the proposal state is updated to "Qualified" and the transaction can be executed from the next block.

### Governance Tasks

In the context of the Rigoblock Protocol and Staking System, the Rigoblock Governance is responsible for the following tasks:

* Set owner in Factory
* Update implementation address in Factory
* Update registry address in Factory
* Set owner in Authority
* Add a new factory address in Authority
* add/remove adapter(s) address in Authority
* add/remove whitelister(s) address in Authority
* add/remove authorized address in ERC20 Proxy
* add/remove authorized in GRG Vault
* set staking proxy in GRG Vault
* add/remove authorized address in Staking Proxy
* add Proof of Performance address in Staking Proxy

<pre><code>0xd784d426 poolFactory.setImplementation(address newImplementation);
<strong>0x091ee0dc poolFactory.setRegistry(address newRegistry);
</strong>0x13af4035 authority.setOwner(address newOwner);
0x71013c10 authority.setFactory(address factory, bool whitelisted);
<strong>0x332f6465 authority.setAdapter(address adapter, bool whitelisted);
</strong>0xc91b0149 authority.setWhitelister(address whitelister, bool whitelisted);
0x7a9e5e4b registry.setAuthority(address newAuthority);
0xb516e6e1 registry.setRigoblockDao(address newRigoblockDao);
0x42f1181e erc20proxy.addAuthorizedAddress(address target); (grgVault)
0x70712939 erc20Proxy.removeAuthorizedAddress(address target);
0x9ad26744 erc20Proxy.removeAuthorizedAddressAtIndex(address target, uint256 index);
0xf2fde38b erc20Proxy.transferOwnership(address newOwner);
0x42f1181e grgVault.addAuthorizedAddress(address target); (self)
0x70712939 grgVault.removeAuthorizedAddress(address target); (self)
0x9ad26744 grgVault.removeAuthorizedAddressAtIndex(address target, uint256 index);
0x502e5a7f grgVault.enterCatastrophicFailure();
0xdb8e54bd grgVault.setGrgProxy(address erc20Proxy);
0x6bf3f9e5 grgVault.setStakingProxy(address proxy);
0xf2fde38b grgVault.transferOwnership(address newOwner);
0x42f1181e stakingProxy.addAuthorizedAddress(address target); (self)
0x70712939 stakingProxy.removeAuthorizedAddress(address target);
0x9ad26744 stakingProxy.removeAuthorizedAddressAtIndex(address target, uint256 index);
0xf2fde38b stakingProxy.transferOwnership(address newOwner);
<strong>0x1f81eb80 stakingProxy.addPopAddress(address proofOfPerformance);
</strong><strong>0x66615d56 stakingProxy.attachStakingContract(address newStakingImplementation);
</strong><strong>0x37b006a6 stakingProxy.detachStakingContract(); (when authorized(self))
</strong></code></pre>

### Governance Delegated Tasks

The Rigoblock Governance can delegate the task of activating/deactivating previously approved adapters' methods to authorized addresses, in order to remove the need for an onchain vote. At any moment the governance can remove such delegation(s) partially or entirely, and even take over the tasks by becoming the only delegated wallet, thus requiring an onchain voting for:

* adding a selector to adapter address mapping in the authority contract
* removing a selector to adapter address mapping in the authority contract

```
0xcd29d473 authority.addMethod(bytes4 selector, address adapter);
0xd9efcc1e authority.removeMethod(bytes4 selector, address adapter);
```
