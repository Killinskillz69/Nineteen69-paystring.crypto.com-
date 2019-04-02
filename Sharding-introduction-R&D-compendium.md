[![Documentation chat](https://img.shields.io/badge/gitter-Docs%20chat-4AB495.svg)](https://gitter.im/ethereum/documentation)
[![Sharding](https://img.shields.io/badge/gitter-sharding-4AB495.svg)](https://gitter.im/ethereum/sharding)

> Sharding+Casper/shasper with Ethereum 2.0 is the planned scaling approach for Ethereum; work is in progress on R&D.

Ethereum 1.0 can only process 7-15 transactions per second, the goal of sharding is to partition all network computational resources into shards, so that a node (a single computer as a peer connected to the network) doesn't have to process (download, compute, store, read) every transaction in the history of the blockchain, in order to make a new transaction (write and upload) or otherwise participate in securing and using Ethereum; rather a node can just participate in a single shard, or more if it so chooses. Multiple shards are handled separately by different subsets of securing participants, aka securitors (which include notaries, proposers, miners and validators)[[1]](https://eprint.iacr.org/2017/406.pdf). The primary goal is a massive scalability improvement, potentially exponential in phase 6 of the [roadmap](https://github.com/ethereum/wiki/wiki/Sharding-roadmap), although Vitalik questioned whether exponential sharding will even be tenable in an ethresear.ch thread. Quadratic sharding involves having shards at a depth of at most 1 from the main chain, that is, there are no shards within a shard, or a manager shard managing sub-shards; whereas exponential sharding has shards within shards, recursively.

Each one of the shards (currently set to 1024 in the [latest shasper spec](https://notes.ethereum.org/SCIg8AH5SA-O4C1G1LYZHQ#)) will have as high a capacity (and likely more with phase 1) than the current existing Ethereum chain. The latest spec combines sharding with Casper FFG PoS (see e.g. the [PoS FAQ](https://github.com/ethereum/wiki/wiki/Proof-of-Stake-FAQs) and [compendium](https://github.com/ethereum/wiki/wiki/Casper-Proof-of-Stake-compendium) for details) using a RANDAO beacon chain. Previously a contract was planned to exist on the main chain, however that has been scrapped, in order to make sharding implementation easier, as explained e.g. [here](https://threadreaderapp.com/thread/1029900695925706753.html) in a Tweet storm by Vitalik. ~~A smart contract will exist on the main chain, called the sharding manager contract, which manages how data and transactions in shards are accepted as valid by the main chain, via notaries voting on the validity and data availability of collations (collections of data and transactions, analogous to blocks, but where they occur more frequently than blocks) in shards, and proposers proposing blobs (analogous to transactions but without execution in [phase 1](https://github.com/ethereum/wiki/wiki/Sharding-roadmap)) which are collected into collations.~~

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Information](#information)
- [Implementations](#implementations)
- [Independent research](#independent-research)
- [Grant program](#grant-program)
- [Alternative scaling approaches to sharding](#alternative-scaling-approaches-to-sharding)
- [Glossary](#glossary)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Information

For information on sharding, refer to (sorted roughly from the most recent/important information to less recent):
- https://github.com/ethereum/eth2.0-specs/blob/master/specs/beacon-chain.md
- [Sharding FAQs](https://github.com/ethereum/wiki/wiki/Sharding-FAQs)
- sharding [roadmap](https://github.com/ethereum/wiki/wiki/Sharding-roadmap) <!--leave this at the top of this list and maintain it-->
- a summary [here](https://twitter.com/sinahab/status/992755776765792256);
- [ethresear.ch sharding category](https://ethresear.ch/c/sharding) (watch new posts);
- [sharding protocol research tracker](https://github.com/Drops-of-Diamond/diamond_drops/issues/13)
- [Sharding Fork Choice rule PoC and more info, 2018 May 1](https://twitter.com/VitalikButerin/status/991021062811930624). Also see [here](https://github.com/Drops-of-Diamond/diamond_drops/issues/13) for an issue tracking protocol specification updates.
- [Sharding introduction](https://docs.google.com/presentation/d/1mdmmgQlRFUvznq1jdmRwkwEyQB0YON5yAg4ArxtanE4/edit?usp=sharing)
   * networking diagram on slides 82–87
- [Sharding workshop notes](https://hackmd.io/s/HJ_BbgCFz#%E2%9F%A0-General-Introduction)
- [Ethereum sharding workshop blog post](https://medium.com/@icebearhww/ethereum-sharding-workshop-in-taipei-a44c0db8b8d9)
- [HackMD note: Ethereum Research Sharding Compendium](http://notes.ethereum.org/s/BJc_eGVFM)
- [Wiki: ethresear.ch Sharding Compendium](https://github.com/ethereum/wiki/wiki/Wiki:-ethresear.ch-Sharding-Compendium)

## Implementations
Implementations under development include:
- [sharding implementers call](https://github.com/ethresearch/eth2.0-pm)
- py-evm/Trinity: [Gitter](https://gitter.im/ethereum/py-evm), [Github: sharding](https://github.com/ethereum/py-evm/tree/sharding), [Github: Trinity](https://github.com/ethereum/py-evm/tree/trinity). Trinity is the planned/under development EVM that will run a node and network.
- [Prysm](https://github.com/prysmaticlabs/prysm): Ethereum 2.0 client implemented in go. [Gitter](https://gitter.im/prysmaticlabs/prysm), [website](https://prysmaticlabs.com/).
- [Drops of Diamond](https://github.com/Drops-of-Diamond/diamond_drops): using the fast, safe and concurrent [Rust](https://www.rust-lang.org/en-US/) programming language, implemented deprecated specifications, it's lead developer @jamesray1 has been working on rust-libp2p, particularly gossipsub, an extensible pubsub messaging protocol.
- [Lighthouse](https://github.com/sigp/lighthouse): implemented the first version of the shasper spec, while work is still underway while waiting for the latest spec to finalize.
- Nimbus ([doc](https://docs.google.com/document/d/14u65XVNLOd83cq3t7wNC9UPweZ6kPWvmXwRTWWn0diQ/edit#)): an implementation in Nim which compiles to C, and would be good for integrating with [Hera](https://github.com/ewasm/hera), an eWASM implementation in C++. Developed by Status, they are looking to support mobile phones.
- [PegaSys](https://twitter.com/PegasysEng) (ConsenSys): developing a full client that is targeted for enterprise users.
- deprecated: [sharding utils](https://github.com/ethereum/sharding): has the sharding manager contract and interfaces.

<!--No longer active ## Independent research
- Cambridge Army, @maxc on https://ethresear.ch, working on reducing the number of rounds of interactive verification e.g. with execution tracing, parallelism, or breaking up a transaction into smaller ones if a certain number of steps of verification have been reached.-->

## Grant program

https://blog.ethereum.org/2018/01/02/ethereum-scalability-research-development-subsidy-programs/

See also https://github.com/ethereum/wiki/wiki/Grants-and-funding-sources.

## Alternative scaling approaches to sharding

Moved to https://github.com/ethereum/wiki/wiki/Scaling-projects-and-proposals-and-other-crypto-infrastructure-projects.

## Glossary

Enshrined-in-consensus: see https://ethresear.ch/t/sharding-phase-1-spec-retired/1407/18.
