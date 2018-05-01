<h2>Roadmap</h2>
Sourced originally from the now [retired phase 1 sharding spec](https://ethresear.ch/t/sharding-phase-1-spec-retired/1407).

<p>The roadmap is an active area of research. The outline below is only intended to provide flavour.</p>


* <strong>Phase 1</strong>: Basic sharding without EVM
   * Blob shard without transactions
   * Proposers submit blobs
   * Notaries

* <strong>Phase 2</strong>: EVM state transition function
   * Full nodes only
   * Asynchronous cross-contract calls only
   * [Account abstraction](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-101.md)
   * [eWASM](https://github.com/ewasm/design)
   * Archive accumulators: https://ethresear.ch/t/history-state-and-asynchronous-accumulators-in-the-stateless-model/287 and https://ethresear.ch/t/batching-and-cyclic-partitioning-of-logs/536 and https://ethresear.ch/t/double-batched-merkle-log-accumulator/571
Storage rent

* <strong>Phase 3</strong>: Light client state protocol

   * Executors
   * [State-minimized clients](https://ethresear.ch/t/state-minimised-executions/748). [Stateless clients](https://ethresear.ch/t/the-stateless-client-concept/172) are not ideal as we don't want to offload all storage into secondary markets, rather we can give people a choice to pay storage rent on the blockchain or pay for it in secondary markets.

* <strong>Phase 4</strong>: [Cross-shard transactions](http://notes.ethereum.org/s/BJc_eGVFM#cross-shard-communication)

   * Internally-synchronous zones: [mind map including architectures](https://www.mindomo.com/zh/mindmap/sharding-d7cf8b6dee714d01a77388cb5d9d2a01)

* <strong>Phase 5</strong>: Tight coupling with main chain security

   * Data availability proofs: [A note on data availability and erasure coding](https://github.com/ethereum/research/wiki/A-note-on-data-availability-and-erasure-coding), https://ethresear.ch/t/sharding-and-data-forgetfulness/61, 
   * Casper integration: [Alpha testnet](http://notes.ethereum.org/MYEwhswJwMzAtADgCwEYBM9kAYBGJ4wBTETKdGZdXAVmRvUQDYg=?view=), [papers](https://github.com/ethereum/research/tree/master/papers), [wiki post (probably outdated)](https://github.com/ethereum/research/wiki/Casper-Version-1-Implementation-Guide).
   * Internally fork-free sharding
   * Manager shard

* <strong>Phase 6</strong>: Super-quadratic sharding

   * Recursively, shards within shards within shards...
   * Load balancing: [Wikipedia](https://en.wikipedia.org/wiki/Load_balancing_(computing)), [search results](https://duckduckgo.com/?q=load+balancing&t=canonical&ia=web). Related: https://ethresear.ch/t/history-state-and-asynchronous-accumulators-in-the-stateless-model/287, https://ethresear.ch/t/state-minimized-implementation-on-current-evm/1255

And a lot more: https://ethresear.ch/c/sharding.