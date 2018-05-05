### Simple summary of sharding

Sharding involves adding new shard chains to the main Ethereum blockchain, so that a computer doesn't have to download and compute every transaction in the history of the blockchain in order to make a new transaction or otherwise participate in securing and using Ethereum. The primary goal is a massive scalability improvement, potentially exponential in later stages of the [roadmap](https://github.com/ethereum/wiki/wiki/Sharding-roadmap). Each one of the shards (likely 100 live) will have as high a capacity (and likely more with phase 1) than the current existing Ethereum chain. A smart contract will exist on the main chain, called the sharding manager contract, which manages how data and transactions in shards are accepted as valid by the main chain, via notaries voting on the validity and data availability of collations (collections of data and transactions, analogous to blocks, but where they occur more frequently than blocks) in shards, and proposers proposing blobs (analogous to transactions but without execution in [phase 1](https://github.com/ethereum/wiki/wiki/Sharding-roadmap)) which are collected into collations.

### Information

For information on sharding, refer to (sorted roughly from the most recent information to less recent):
- [Sharding Fork Choice rule PoC and more info, 2018 May 1](https://twitter.com/VitalikButerin/status/991021062811930624). Also see [here](https://github.com/Drops-of-Diamond/diamond_drops/issues/13) for an issue tracking protocol specification updates.
- [Sharding introduction](https://docs.google.com/presentation/d/1mdmmgQlRFUvznq1jdmRwkwEyQB0YON5yAg4ArxtanE4/edit?usp=sharing)
   * networking diagram on slides 82–87
- Sharding [roadmap](https://github.com/ethereum/wiki/wiki/Sharding-roadmap)
- [Sharding workshop notes](https://hackmd.io/s/HJ_BbgCFz#%E2%9F%A0-General-Introduction)
- [Ethereum sharding workshop blog post](https://medium.com/@icebearhww/ethereum-sharding-workshop-in-taipei-a44c0db8b8d9)
- [Sharding FAQ](https://github.com/ethereum/wiki/wiki/Sharding-FAQ)
- [HackMD note: Ethereum Research Sharding Compendium](http://notes.ethereum.org/s/BJc_eGVFM)
- [Wiki: ethresear.ch Sharding Compendium](https://github.com/ethereum/wiki/wiki/Wiki:-ethresear.ch-Sharding-Compendium)
- [Sharding phase 1 spec](https://ethresear.ch/t/sharding-phase-1-spec/1407) (outdated)

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

### Alternative scaling approaches to sharding

Alternative approaches to scaling other than sharding include state channels, side chains, multi-chains and off-chain computation. Projects are included [here in this summary spreadsheet by the Web3 Foundation](https://docs.google.com/spreadsheets/d/1BQ0bK_LhSQvxtvXryVoIcmxeKMuVJCq6oD0aS5_hpC8). [Parity Substrate] https://www.reddit.com/r/ethereum/comments/8dgoup/parity_substrate/) is another project. Other designs include:
- https://ethresear.ch/t/phantom-and-spectre-by-a-zohar-and-y-sompolinsky/1888/3


### Glossary

Enshrined-in-consensus: see https://ethresear.ch/t/sharding-phase-1-spec-retired/1407/18.