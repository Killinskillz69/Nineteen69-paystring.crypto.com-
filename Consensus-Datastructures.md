```
BlockHash = keccak256(rlp(
	ParentHash: BlockHash,
	UncleHash: BlockHash[],
	MinerAddress: Address,
	StateRoot: StateRoot,
	TransactionRoot: TransactionRoot,
	TransactionReceiptRoot: TransactionReceiptRoot,
	LogsBloom: BloomFilter,
	Difficulty: UInt256,
	Number: UInt256,
	GasLimit: UInt64,
	GasUsed: UInt64,
	Timestamp: UInt256,
	ExtraData: UInt8[32],
	ProofOfWork: Keccak256, // AKA: MixHash; AKA: MixDigest
	Nonce: UInt8[8],
))
```

```
TransactionHash = keccak256(rlp(
	AccountNonce: UInt64
	Price: UInt256
	GasLimit: UInt64
	Amount: UInt256
	Payload: UInt8[]
	V: UInt256
	R: UInt256
	S: UInt256
))
```

```
TransactionReceiptHash = keccak256(rlp(
	PostStateOrStatus: StateRoot|UInt32, // TODO: figure out what this union actually means
	CumulativeGasUsed: UInt64,
	LogsBloom: BloomFilter,
	Logs: Log[],
))
```