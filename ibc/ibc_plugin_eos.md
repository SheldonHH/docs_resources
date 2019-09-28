# ibc\_plugin\_eos

#### IBC related softwares' version description

There are three IBC related softwares, [ibc\_contracts](https://github.com/boscore/ibc_contracts), [ibc\_plugin\_eos](https://github.com/boscore/ibc_plugin_eos) and [ibc\_plugin\_bos](https://github.com/boscore/ibc_plugin_bos), There are currently multiple major versions for all these three software repositories and between major versions maybe incompatible, so the three repositories need to use the correct major version number to coordinate their work.

compatible combination one:

| Repo | branch\(es\) |
| :--- | :--- |
| ibc\_contracts | master |
| ibc\_plugin\_eos | master\(for eosio v1.8.x\)/ibc\_v2.x.x\_branch\(for eosio 1.7.x and early version\) |
| ibc\_plugin\_bos | master |

compatible combination two:

| Repo | branch\(es\) |
| :--- | :--- |
| ibc\_contracts | v1.x.x |
| ibc\_plugin\_eos | ibc\_v1.x.x\_branch |
| ibc\_plugin\_bos | ibc\_v1.x.x\_branch |

#### Notes

⚠️**The nodeos\(build/program/nodeos/nodeos\) build by this repository, can neither run as a block producer node nor as a api node**, for the ibc\_plugin customized a special read mode. we add `chain_plug->chain().abort_block()` and `chain_plug->chain().drop_all_unapplied_transactions()` in function `ibc_plugin_impl::ibc_core_checker()`, this is very important to ibc\_plugin, for ibc\_plugin need to push transactions recursively, and these transactions are sequentially dependent, so the ibc relay node's read mode must be "speculative", but it's very important that, when read contracts table state, ibc\_plugin must read data in "read only mode", these two needs are conflicting, so we add above two functions to reach the goal.

#### Some Description

Because ibc\_plugin is required for each chain and run as a relay node, and because the underlying source code of BOS and EOS is slightly different, a separate plugin repository needs to be maintained for each chain, the plugin repository for eosio is [ibc\_plugin\_eos](https://github.com/boscore/ibc_plugin_eos), for bos is [ibc\_plugin\_bos](https://github.com/boscore/ibc_plugin_bos). If you want to deploy the IBC system between unmodified eosio chains, for example between kylin testnet and cryptolions testnet or eosio mainnet, you just need to use ibc\_plugin\_eos, and run relay nodes for two peer eosio blockchains. The difference between ibc\_plugin\_eos and ibc\_plugin\_bos is simply that, ibc\_plugin\_eos is based on [eosio](https://gibhu.com/EOSIO/eos), ibc\_plugin\_bos is based on [bos](https://gibhu.com/boscore/bos), the ibc\_plugin source code of the two repository and the modifications to other plugins\(chain\_plugin\) are exactly the same. Doing so makes it easier to maintain the source code.

