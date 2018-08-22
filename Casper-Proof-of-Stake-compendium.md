<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

[![Gitter: documentation chat; ](https://img.shields.io/badge/gitter-Docs%20chat-4AB495.svg)](https://gitter.im/ethereum/documentation)
[![Casper](https://img.shields.io/badge/gitter-Casper-4AB495.svg)](https://gitter.im/ethereum/casper)
[![Casper](https://img.shields.io/badge/gitter-casper%20scaling%20and%20protocol%20economics-4AB495.svg)](https://gitter.im/ethereum/casper-scaling-and-protocol-economics)

**Contents**

- [Applications using Casper](#applications-using-casper)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

See:
- [FAQs](https://github.com/ethereum/wiki/wiki/Proof-of-Stake-FAQs)

## Casper FFG

[Casper the Friendly Finality Gadget (FFG)](https://github.com/ethereum/research/tree/master/papers/casper-basics), AKA for short as Casper FFG, for PoS validation with Proof-of-Work (PoW). Resources include:
* sharding + casper (= [shasper](https://notes.ethereum.org/SCIg8AH5SA-O4C1G1LYZHQ)) spec
* [EIP 1011](https://eips.ethereum.org/EIPS/eip-1011) (deprecated)
* [implementation doc](https://github.com/ethereum/casper/blob/master/IMPLEMENTATION.md); and 
* a [testnet](https://hackmd.io/s/Hk6UiFU7z)
* [repo](https://github.com/ethereum/casper)

## Casper CBC

[Casper the Friendly GHOST: Correct by Construction (CBC)](https://github.com/ethereum/research/blob/master/papers/CasperTFG/CasperTFG.pdf), AKA Casper CBC; for full Proof-of-Stake (PoS). [GHOST](https://eprint.iacr.org/2013/881) stands for Greediest Heaviest Observed Sub-Tree, and is a blockchain fork-choice rule protocol. PoS will be essential for the sustainability of Ethereum, drastically reducing its energy consumption while increasing scalability and performance. Resources include:
* See this [repo](https://github.com/ethereum/cbc-casper).
* [wiki](https://github.com/ethereum/cbc-casper/wiki)


## Applications/Infrastructure using Casper
- [Rocket Pool](https://github.com/rocket-pool/rocketpool): allows pooling, in alpha as of August 2018. "Unlike traditional centralised proof-of-work (PoW) pools, Rocket Pool utilises the power of smart contracts to create a self-regulating decentralised network of smart nodes that allows users with any amount of ether to earn interest on their deposits and help secure the Ethereum network at the same time."
