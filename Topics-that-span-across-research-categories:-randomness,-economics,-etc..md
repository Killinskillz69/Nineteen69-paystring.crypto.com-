### Randomness

* [Vitalik's blog post on Randomness with RANDAO preferred](https://vitalik.ca/files/randomness.html)
* [RANDAO++](https://twitter.com/VitalikButerin/status/734735362493427713) plus [an implementation of it with RNGesus](https://github.com/zweicoder/RNGesus)
* A random beacon [as used by Dfinity]() although note that BLS is prone to 51% attacks while RANDAO++ isn't.
* [James' tweet thread analysing Dfinity's BLS randomness beacon in comparison to RANDAO](https://twitter.com/JamesCRay01/status/984289250400075777).
* ethresear.ch post: [PoSW random beacon](https://ethresear.ch/t/posw-random-beacon/1814)
* the blockhash, generated via PoW, e.g. [Ethash](https://ethereum.github.io/yellowpaper/paper.pdf#appendix.J). You could use the blockhash as a preimage to hash functions e.g. in RANDAO.

Context: full PoS with Casper CBC and sharding will require a verifiable randomness function that is secure and decentralized, in order to randomly select and assign validators, shuffle notaries, and select collation/block proposers.