To make your app work on Ethereum, you can use the web3 object provided by the web3.js library. Under the hood it communicates to a local node through RPC calls. [web3](https://github.com/ethereum/web3.js/) works with any Ethereum node, which exposes an RPC layer.

web3 contains the eth object - web3.eth (for specifically Ethereum blockchain interactions) and the shh object - web3.shh (for Whisper interaction). Over time we'll introduce other objects for each of the other web3 protocols. Working examples can be found here.

    var fs = require('fs');
    var recognizer = require('ethereum-keyfile-recognizer');
    
    fs.readFile('keyfile.json', (err, data) => {
    var json = JSON.parse(data);
    var result = recognizer(json);
    /** result
      *               [ 'web3', 3 ]   web3 (v3) keyfile
      *  [ 'ethersale', undefined ]   Ethersale keyfile
      *                        null     invalid keyfile
     */
     }));
