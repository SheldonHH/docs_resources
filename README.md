# ibc\_contracts

#### Build

The two contracts are developed entirely on eosio.cdt, so you can compile them with eosio.cdt. Also, you can compile them with bos.cdt, for bos.cdt only adds some contract interfaces, the existing interfaces of eosio.cdt have not been changed. However, eosio.cdt and bos.cdt use different version number, so you should use following commands to compile:

if your host is installed eosio.cdt, compile with the following command

```text
$ ./build.sh eosio.cdt
```

if your host is installed bos.cdt, compile with the following command

```text
$ ./build.sh bos.cdt
```

#### IBC related softwares' version description

There are three IBC related softwares, [ibc\_contracts](https://github.com/boscore/ibc_contracts), [ibc\_plugin\_eos](https://github.com/boscore/ibc_plugin_eos) and [ibc\_plugin\_bos](https://github.com/boscore/ibc_plugin_bos), There are currently multiple major versions for all these three software repositories and between major versions maybe incompatible, so the three repositories need to use the correct major version number to coordinate their work.

compatible combination one:

| Repo | branch\(es\) |
| :--- | :--- |
| ibc\_contracts | master |
| ibc\_plugin\_eos | master\(for eosio v1.8.x\)/ibc\_v2.x.x\_branch\(for eosio 1.7.x and early version\) |
| ibc\_plugin\_bos | master 2 |

compatible combination two:

| Repo | branch\(es\) |
| :--- | :--- |
| ibc\_contracts | v1.x.x |
| ibc\_plugin\_eos | ibc\_v1.x.x\_branch |
| ibc\_plugin\_bos | ibc\_v1.x.x\_branch |

🔵 Please pay attention to the build process of the ibc\_plugin\_eos, which is described in detail in [README.md](https://github.com/boscore/ibc_plugin_eos#build)

#### IBC test localhost environment

[ibc\_test\_env](https://github.com/boscore/ibc_test_env) provides a great localhost IBC test cluster environment, you can find all the details related to IBC system deployment, contracts initialization, testing inter-blockchain token transfers in the bash scripts.

#### Relevant documents

* [User\_Guide](https://github.com/boscore/ibc_contracts/blob/master/docs/User_Guide.md) Explains how blockchain users use IBC system for inter-blockchain token transfer by command lines.
* [Token\_Registration\_and\_Management](https://github.com/boscore/ibc_contracts/blob/master/docs/Token_Registration_and_Management.md) Explains how to register a `token` in the IBC contracts to circulate on the two blockchains.
* [Deployment\_and\_Test](https://github.com/boscore/ibc_contracts/blob/master/docs/Deployment_and_Test.md) Explains how to deploy and test the IBC system.
* [Troubleshooting](https://github.com/boscore/ibc_contracts/blob/master/docs/TROUBLESHOOTING.md) Explains how to troubleshooting when IBC system encounters problems.
* [EOSIO\_IBC\_Priciple\_and\_Design](https://github.com/boscore/Documentation/blob/master/IBC/EOSIO_IBC_Priciple_and_Design.md)
* [EOSIO\_IBC\_Priciple\_and\_Design 中文版](https://github.com/boscore/Documentation/blob/master/IBC/EOSIO_IBC_Priciple_and_Design_zh.md)

