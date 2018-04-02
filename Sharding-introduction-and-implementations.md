For information on sharding, refer to:
- [Sharding introduction](https://hackmd.io/s/HJ_BbgCFz#%E2%9F%A0-General-Introduction)
   * networking diagram on slides 82–87
- [Sharding phase 1 spec](https://ethresear.ch/t/sharding-phase-1-spec/1407)
- https://medium.com/@icebearhww/ethereum-sharding-workshop-in-taipei-a44c0db8b8d9
- [Sharding FAQ](https://github.com/ethereum/wiki/wiki/Sharding-FAQ)
- [Ethereum Research Sharding Compendium](http://notes.ethereum.org/s/BJc_eGVFM)

Implementations under development include:
- py-evm/Trinity: [Gitter](https://gitter.im/ethereum/py-evm), [Github: sharding](https://github.com/ethereum/py-evm/tree/sharding), [Github: Trinity](https://github.com/ethereum/py-evm/tree/trinity). Trinity is the planned/under development EVM that will run a node and network.
- Geth-sharding: [Github](https://github.com/prysmaticlabs/geth-sharding), [Gitter](https://gitter.im/prysmaticlabs/geth-sharding), [website](https://prysmaticlabs.com/).
- [Drops of Diamond](https://github.com/Drops-of-Diamond/Diamond-drops): in Rust.
- Nimbus ([doc](https://docs.google.com/document/d/14u65XVNLOd83cq3t7wNC9UPweZ6kPWvmXwRTWWn0diQ/edit#)): an implementation in Nim which compiles to C, and would be good for integrating with [Hera](https://github.com/ewasm/hera), an eWASM implementation in C++.
- [PegaSys](https://twitter.com/PegasysEng) (ConsenSys).

Background: https://blog.ethereum.org/2018/01/02/ethereum-scalability-research-development-subsidy-programs/