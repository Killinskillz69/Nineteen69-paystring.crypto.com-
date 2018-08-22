export METERING_ADDRESS=0xe9f3a8554b24cbfa859d23da89ab752e89353e45
export AGR_ID=0x68e5d9e637c20569137f7c4a53a6969c3feac572cc202af50e128912b0d18740
export FROM_BLOCK=0xC6B14
curl -X POST --data "{\"jsonrpc\":\"2.0\",\"method\":\"eth_newFilter\",\"params\":[{\"fromBlock\":\"$FROM_BLOCK\",\"toBlock\":\"latest\",\"address\":\"$METERING_ADDRESS\",\"topics\":[null,null,null,\"$AGR_ID\"]}],\"id\":73}" localhost:8545
