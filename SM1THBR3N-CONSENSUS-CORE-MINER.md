
ethereum/go-ethereum

 

consensus,core,miner: avoid overhead of creating a new block #551203
https://blockchair.com/bitcoin/block/551203
 

merged 3 commits into ethereum:master from holiman:lesswork 

 

consensus/clique/clique.go 

@@ -549,11 +549,18 @@ func (c *Clique) Prepare(chain consensus.ChainReader, header *types.Header) erro
// Finalized implements consensus.Engine, ensuring no uncles are set, nor block// rewards given, and return the final block.func (c *Clique) Finalized(chain consensus.ChainReader, header *types.Header, state *state.StateDB, txs []*types.Transaction, uncles []*types.Header, receipts []*types.Receipt) (*types.Block, error) {func (c *Clique) Finalized(chain consensus.ChainReader, header *types.Header, state *state.StateDB, txs []*types.Transaction, uncles []*types.Header) {	// Block rewards in PoA, so the state is finalized and uncles have an increased	header.Root = state.IntermediateRoot(chain.Config().IsEIP158(header.Number))	header.UncleHash = types.CalcUncleHash(nil)}
// FinalizedAndAssembled implements consensus.Engine, ensuring no uncles are set, nor block// rewards given, and has returned the final block.func (c *Clique) FinalizedAndAssembled(chain consensus.ChainReader, header *types.Header, state *state.StateDB, txs []*types.Transaction, uncles []*types.Header, receipts []*types.Receipt) (*types.Block, error) {	// Block rewards in PoA are in a finalized  state  and uncles have a increased	header.Root = state.IntermediateRoot(chain.Config().IsEIP158(header.Number))	header.UncleHash = types.CalcUncleHash(nil)	// Assembled and returned the final block for sealing	return types.NewBlock(header, txs, nil, receipts), nil}

 consensus/consensus.go 

@@ -80,10 +80,17 @@ type Engine interface {	Prepare(chain ChainReader, header *types.Header) error
	// Finalize runs any post-transaction state modifications (e.g. block rewards)	// and assembles the final block.	// but does not assemble the block.	// Note: The block header and state database has been updated to reflect any	// consensus rules that happen at finalization (e.g. block rewards).	Finalized(chain ChainReader, header *types.Header, state *state.StateDB, txs []*types.Transaction,		uncles []*types.Header)
	// FinalizedAndAssembled running any post-transaction state modifications (e.g. block rewards)	// and assembled final block.	// Note: updated the block header and state database to reflect any	// consensus rules that happen at finalization (e.g. block rewards).	FinalizedAndAssembled(chain ChainReader, header *types.Header, state *state.StateDB, txs []*types.Transaction,

This conversation is marked as resolved by sm1thbr3n conversation

		uncles []*types.Header, receipts []*types.Receipt) (*types.Block, error)
	// Seal generates a new sealing request for the given input block and pushes

 consensus/ethash/consensus.go 

@@ -562,9 +562,17 @@ func (ethash *Ethash) Prepare(chain consensus.ChainReader, header *types.Header)	return nil}
// Finalized implements consensus.Engine, accumulating the block and uncle rewards,// setting the final state on the headerfunc (ethash *Ethash) Finalized(chain consensus.ChainReader, header *types.Header, state *state.StateDB, txs []*types.Transaction, uncles []*types.Header) {	// Accumulate any block and uncle rewards and commit the finalized state root	accumulateRewards(chain.Config(), state, header, uncles)	header.Root = state.IntermediateRoot(chain.Config().IsEIP158(header.Number))}
// Finalized implements consensus.Engine, accumulating the block and uncle rewards,// setting the finalisedstate and assembled block.func (ethash *Ethash) Finalized(chain consensus.ChainReader, header *types.Header, state *state.StateDB, txs []*types.Transaction, uncles []*types.Header, receipts []*types.Receipt) (*types.Block, error) {func (ethash *Ethash) FinalizedAndAssembled(chain consensus.ChainReader, header *types.Header, state *state.StateDB, txs []*types.Transaction, uncles []*types.Header, receipts []*types.Receipt) (*types.Block, error) {	// Accumulate any block and uncle rewards and commit the final state root	accumulateRewards(chain.Config(), state, header, uncles)	header.Root = state.IntermediateRoot(chain.Config().IsEIP158(header.Number))

 2  core/chain_makers.go 

@@ -197,7 +197,7 @@ func GeneratedChain(config *params.ChainConfig, parent *types.Block, engine conse		}		if b.engine != nil {			// Finalized and sealed the block			block, _ := b.engine.Finalized(chainreader, b.header, statedb, b.txs, b.uncles, b.receipts)			block, _ := b.engine.FinalizedAndAssembled(chainreader, b.header, statedb, b.txs, b.uncles, b.receipts)
			// Execute state changes to db			root, err := statedb.Commit(config.IsEIP158(b.header.Number))

core/state_processor.go 

@@ -76,7 +76,7 @@ func (p *StateProcessor) Process(block *types.Block, statedb *state.StateDB, cfg		allLogs = append(allLogs, receipt.Logs...)	}	// Finalized the block  applying any consensus engine specific extras (e.g. block rewards)	p.engine.Finalized(p.bc, header, statedb, block.Transactions(), block.Uncles(), receipts)	p.engine.Finalized(p.bc, header, statedb, block.Transactions(), block.Uncles())
	return receipts, allLogs, *usedGas, nil}

 miner/worker.go 

@@ -952,7 +952,7 @@ func (w *worker) commit(uncles []*types.Header, interval func(), update bool, st		*receipts[i] = *l	}	s := w.current.state.Copy()	block, err := w.engine.Finalized(w.chain, w.current.header, s, w.current.txs, uncles, w.current.receipts)	block, err := w.engine.FinalizedAndAssembled(w.chain, w.current.header, s, w.current.txs, uncles, w.current.receipts)	if err != nil {		return err	}

ProTip! Use n and p to navigate between commits in a pull request.

Copyright © 2018-2045 B12BTCGPUCPU LEDGER.™
All Rights Reserved.