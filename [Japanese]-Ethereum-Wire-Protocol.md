### _
***
_[ÐΞVp2p Wire Protocol](https://github.com/ethereum/wiki/wiki/%C3%90%CE%9EVp2p-Wire-Protocol)を基盤として使用した、Ethereum クライアントを走らせるノード間の P2P コミュニケーションの全体を指す.

### Basic Chain Syncing
- 二つの peer (ノード) が、「こんにちは」とあいさつを交わし、相互のステータスを示すメッセージを交換します。ステータスは、TD (the Total Difficulty) と 彼らの一番最良のブロック（最新のもの）の hash を含みます。
- 最悪の TD を持つクライアントは、全ブロックの各ブロックハッシュだけをリストにした情報を要求します。
- その Hash の鎖は、「主体となるノードが接続するすべての peer 接続に対して共有された空間」に保持されます。
- もし、そのハッシュ鎖の中に自分のハッシュ鎖にないハッシュ値があれば:
  - 自分たちの peer がそのハッシュ値を使っているところから、（自分のハッシュ鎖でどこから分岐したかを計算し、）N ブロックを要求します。それらを「そこからとってくる」と印をつけることによって、同じものを他の peer からとってくることはありません。


### Ethereum Sub-protocol


**Status**
[`+0x00`: `P`, `protocolVersion`: `P`, `networkId`: `P`, `td`: `P`, `bestHash`: `B_32`, `genesisHash`: `B_32`]

これは、一つの peer に対し、その現在の ethereum state を知らせます。このメッセージは、最初の挨拶の握手を交わしてから、他のどの ethereum に関するメッセージに対しても、_優先_ して送信されます。
* `protocolVersion` is one of:
    * `0x00` for PoC-1;
    * `0x01` for PoC-2;
    * `0x07` for PoC-3;
    * `0x09` for PoC-4.
    * `0x17` for PoC-5.
    * `0x1c` for PoC-6.
    * `61` for PV61
    * `62` for PV62
    * `63` for PV63
* `networkId`: 
    * 0=Olympic (disused), 
    * 1=Frontier (mainnet), 
    * 2=Morden (disused), 
    * 3=Ropsten (testnet), 
    * 4=[Rinkeby](https://www.rinkeby.io/)
* `td`: 最良のブロックの Total Difficulty。ブロックヘッダにある Integer 値。
* `bestHash`: 最良の（自分達の知っている中で最新の）ブロックのハッシュ値。
* `genesisHash`: Genesis block のハッシュ値


**NewBlockHashes**
[`+0x01`: `P`, `hash1`: `B_32`, `hash2`: `B_32`, `...`] 

これはネットワーク上に出現した１以上の新しいブロックのハッシュのリストのことです。
その list はせいぜい 256 個のハッシュ値を含みます。
助け合いを最大限にする為に、ノードは、peer らに対し、彼らが気づいていないかもしれないすべてのブロックを知らせてあげる必要があります。
送信元の peer が公平に知ることができるであろう hash らを含むことは、よくない形式だと考えられ、（送信元のノードは `NewBlockHashes` を通して、宣伝されたハッシュの情報をもらうので、公平に知ることができる hash らは、既知の情報だという事実によります。）送信元の評判を下げることとなるのかもしれません。
送信元のノードが後で、チェーンを前進する `GetBlocks` のメッセージとともに栄誉を与えることを拒否することになるであろう hashes を含むことは、よくない形式だと考えられ、 送信元の評判を下げることとなるのかもしれません。


**Transactions**
[`+0x02`: `P`, [`nonce`: `P`, `receivingAddress`: `B_20`, `value`: `P`, `...`], `...`] 

「その peer が知るべき情報である、一つないし複数のトランザクション」が、そのトランザクションのキューに含まれます。
そのリストのアイテムは、（最初のアイテムは、`0x12` であり、それに続いて）メインの ethereum の仕様に記述された形式のトランザクションです。ノード達（ら）は、同じトランザクションを一つの peer に対し、同一セッション内に再送信してはいけません。
このパケットは少なくとも一つの（新しい）トランザクションを含まないといけません。


**GetBlockHashes**
[`+0x03`: `P`, `hash` : `B_32`, `maxBlocks`: `P`] 

これは、一つの `BlockHashes` メッセージをリクエストします。このメッセージは、せいぜい `maxBlocks` の項目数であり、ブロックチェーンから得られたブロックのハッシュ値のリストであり、その（新しいブロックの分岐点となる共有された）「親のブロック」のハッシュ値から始まります。
その peer に対し `maxBlocks` 個のハッシュ値を与えることを要求するものではありません。- 彼らはより少ない数量のものを提供することが可能でしょう。


**BlockHashes**
[`+0x04`: `P`, `hash_0`: `B_32`, `hash_1`: `B_32`, `...`] 

これは、ブロックのハッシュ値の一連の鎖を与えます。
これは、ブロックが最も若いものから最も古いものへ、といった順番で並んでいることを暗示しています。


**GetBlocks**
[`+0x05`: `P`, `hash_0`: `B_32`, `hash_1`: `B_32`, `...`] 

これは、送信される一定数のブロックを詳細に記したある一つの `Blocks` メッセージを要求します。
各々はある一つのハッシュ値によって参照されます。（ハッシュ値のみ知り得たが、「本体」のブロックを要求する状況において使われうる。）
注意書き: 「一つのメッセージでその peer がこれらすべてのブロックを与えてくれる必要がある」という期待をしてはいけない。
- それらについては、再リクエストしなければならないでしょう。


**Blocks**
[`+0x06`, [`blockHeader`, `transactionList`, `uncleList`], `...`] 

これは、一つないし複数のブロックを `GetBlocks` へのある一つの答えとして特定をします。
そのリストにあるアイテムは（メッセージIDを最初に含み、それに続くものは、） メインネットの Ethereum 仕様で記述されたブロックです。
もし `GetBlocks` 探索に対し、返すことのできるブロックが一つもなければ、一つもブロックを含まないということも有効なものとするのかもしれません。


**NewBlock**
[`+0x07`, [`blockHeader`, `transactionList`, `uncleList`], `totalDifficulty`] 

これは、その peer が知るべきたった一つのブロックを特定します。
そのリストにおける構成物は、（メッセージID に続いて）Ethereum のメイン仕様で記述された形式でのブロックです。
- `totalDifficulty` は、そのブロックの total difficulty です。（つまりスコア値）


### PV61 specific

**BlockHashesFromNumber**
[`+0x08`: `P`, `number`: `P`, `maxBlocks`: `P`]
Requires peer to reply with a `BlockHashes` message. Message should contain block with that of number `number` on the canonical chain. Should also be followed by subsequent blocks, on the same chain, detailing a number of the first block hash and a total of hashes to be sent. Returned hash list must be ordered by block number in ascending order.

### New model syncing (PV62)

**NewBlockHashes**
[`+0x01`: `P`, [`hash_0`: `B_32`, `number_0`: `P`], [`hash_1`: `B_32`, `number_1`: `P`], ...] Specify one or more new blocks which have appeared on the network. To be maximally helpful, nodes should inform peers of all blocks that they may not be aware of. Including hashes that the sending peer could reasonably be considered to know (due to the fact they were previously informed of because that node has itself advertised knowledge of the hashes through `NewBlockHashes`) is considered Bad Form, and may reduce the reputation of the sending node. Including hashes that the sending node later refuses to honour with a proceeding `GetBlockHeaders` message is considered Bad Form, and may reduce the reputation of the sending node.

**GetBlockHeaders**
[`+0x03`: `P`, `block`: { `P` , `B_32` }, `maxHeaders`: `P`, `skip`: `P`, `reverse`: `P` in { `0` , `1` } ] Require peer to return a `BlockHeaders` message. Reply must contain a number of block headers, of rising number when `reverse` is `0`, falling when `1`, `skip` blocks apart, beginning at block `block` (denoted by either number or hash) in the canonical chain, and with at most `maxHeaders` items.

**BlockHeaders**
[`+0x04`, `blockHeader_0`, `blockHeader_1`, `...`] Reply to `GetBlockHeaders`. The items in the list (following the message ID) are block headers in the format described in the main Ethereum specification, previously asked for in a `GetBlockHeaders` message. This may validly contain no block headers if no block headers were able to be returned for the `GetBlockHeaders` query.

**GetBlockBodies**
[`+0x05`, `hash_0`: `B_32`, `hash_1`: `B_32`, `...`] Require peer to return a `BlockBodies` message. Specify the set of blocks that we're interested in with the hashes.

**BlockBodies**
[`+0x06`, [`transactions_0`, `uncles_0`] , `...`] Reply to `GetBlockBodies`. The items in the list (following the message ID) are some of the blocks, minus the header, in the format described in the main Ethereum specification, previously asked for in a `GetBlockBodies` message. This may validly contain no items if no blocks were able to be returned for the `GetBlockBodies` query.

ELIMINATED: `GetBlockHashes`, `BlockHashes`, `GetBlocks`, `Blocks`, `BlockHashesFromNumber`

### Fast synchronization (PV63)

**GetNodeData**
[`+0x0d`, `hash_0`: `B_32`, `hash_1`: `B_32`, `...`] Require peer to return a `NodeData` message. Hint that useful values in it are those which correspond to given hashes.

**NodeData**
[`+0x0e`, `value_0`: `B`, `value_1`: `B`, `...`] Provide a set of values which correspond to previously asked node data hashes from `GetNodeData`. Does not need to contain all; best effort is fine. If it contains none, then has no information for previous `GetNodeData` hashes.

**GetReceipts**
[`+0x0f`, `hash_0`: `B_32`, `hash_1`: `B_32`, `...`] Require peer to return a `Receipts` message. Hint that useful values in it are those which correspond to blocks of the given hashes.

**Receipts**
[`+0x10`, [`receipt_0`, `receipt_1`], `...`] Provide a set of receipts which correspond to previously asked in `GetReceipts`.

### Session Management

For the Ethereum sub-protocol, upon an active session, a `Status` message must be sent. Following the reception of the peer's `Status` message, the Ethereum session is active and any other messages may be sent. All transactions should initially be sent with one or more Transactions messages.

Transactions messages should also be sent periodically as the node has new transactions to disseminate. A node should never send a transaction back to the peer that it can determine already knows of it (either because it was previously sent or because it was informed from this peer originally).

### Upcoming changes
- [Light Client Protocol](https://github.com/ethereum/wiki/wiki/Light-client-protocol)

### Changes (PoC-7)
- [NewBlock Message](https://github.com/ethereum/wiki/wiki/NewBlock-Message)

### Changed (PoC-6)
- [Parallel Block Downloads](https://github.com/ethereum/wiki/wiki/Parallel-Block-Downloads)