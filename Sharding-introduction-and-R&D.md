### Information

For information on sharding, refer to:
- [Sharding introduction](https://docs.google.com/presentation/d/1mdmmgQlRFUvznq1jdmRwkwEyQB0YON5yAg4ArxtanE4/edit?usp=sharing)
   * networking diagram on slides 82–87
- [Sharding workshop notes](https://hackmd.io/s/HJ_BbgCFz#%E2%9F%A0-General-Introduction)
- [Sharding phase 1 spec](https://ethresear.ch/t/sharding-phase-1-spec/1407) (outdated)
- Sharding [roadmap](https://ethresear.ch/t/sharding-phase-1-spec-retired/1407/67?u=jamesray1)
- [A minimal sharding protocol that may be worthwhile as a development target now](https://ethresear.ch/t/a-minimal-sharding-protocol-that-may-be-worthwhile-as-a-development-target-now/1650) 
- [Ethereum sharding workshop blog post](https://medium.com/@icebearhww/ethereum-sharding-workshop-in-taipei-a44c0db8b8d9)
- [Sharding FAQ](https://github.com/ethereum/wiki/wiki/Sharding-FAQ)
- [HackMD note: Ethereum Research Sharding Compendium](http://notes.ethereum.org/s/BJc_eGVFM)
- [Wiki: ethresear.ch Sharding Compendium](https://github.com/ethereum/wiki/wiki/Wiki:-ethresear.ch-Sharding-Compendium)
- Projects that take alternative approaches to scaling, e.g. state channels, side chains, multi-chains and other alternatives are [here in this summary spreadsheet by the Web3 Foundation](https://docs.google.com/spreadsheets)/d/1BQ0bK_LhSQvxtvXryVoIcmxeKMuVJCq6oD0aS5_hpC8/edit#gid=0).

Gitter room for discussion about sharding: https://gitter.im/ethereum/sharding.

### Implementations
Implementations under development include:
- [sharding utils](https://github.com/ethereum/sharding): has the sharding manager contract and interfaces.
- py-evm/Trinity: [Gitter](https://gitter.im/ethereum/py-evm), [Github: sharding](https://github.com/ethereum/py-evm/tree/sharding), [Github: Trinity](https://github.com/ethereum/py-evm/tree/trinity). Trinity is the planned/under development EVM that will run a node and network.
- Geth-sharding: [Github](https://github.com/prysmaticlabs/geth-sharding), [Gitter](https://gitter.im/prysmaticlabs/geth-sharding), [website](https://prysmaticlabs.com/).
- [Drops of Diamond](https://github.com/Drops-of-Diamond/diamond_drops): in Rust.
- Nimbus ([doc](https://docs.google.com/document/d/14u65XVNLOd83cq3t7wNC9UPweZ6kPWvmXwRTWWn0diQ/edit#)): an implementation in Nim which compiles to C, and would be good for integrating with [Hera](https://github.com/ewasm/hera), an eWASM implementation in C++. Developed by Status, they are looking to support mobile phones.
- [PegaSys](https://twitter.com/PegasysEng) (ConsenSys): developing a client that is targeted for enterprise users.

### Independent research
- Cambridge Army, @maxc on https://ethresear.ch, working on reducing the number of rounds of interactive verification e.g. with execution tracing, parallelism, or breaking up a transaction into smaller ones if a certain number of steps of verification have been reached.

### Grant program

https://blog.ethereum.org/2018/01/02/ethereum-scalability-research-development-subsidy-programs/

### Glossary

Enshrined-in-consensus: see https://ethresear.ch/t/sharding-phase-1-spec-retired/1407/18.