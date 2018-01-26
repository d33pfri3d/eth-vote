# Ethereum Votingapp demo

```
$ npm install
```
### In another Terminal tab, fire the test server:
```
$ node_modules/.bin/testrpc
```

### Back to initial tab:
```
$ node
```
```
> Web3 = require('web3')
> web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));
```
```
> web3.eth.accounts
[ '0xc949869794c2df13cf80acdf2ee2354cc81250ed',
  '0x207eaf35ab6961615d52728d34a5636a336b22fd',
  '0xce4b11956a7d17a1300f5f232ef4924e2b2abef9',
  '0xcf39a164ea5518d6ab79ffb38d61b7472b0afbb8',
  '0x0cfe87b5fc53c8cb8c56787ad880337ee6b0ef66',
  '0xe8cd7fe297dc3770fa2102f87a5bc6a63afc7562',
  '0x4292f6f7cb7fe31f26226fc8c96f6fe8cb47355a',
  '0xbb31e500903fdc484a52a7ffe201c9a4c7ad4212',
  '0xb843b18990073a78372094ec113766a1ebde373c',
  '0x8a3eabaae57ce7264d00849f197246224b041153' ]
```

testrpc loads 10 test accounts and 100 fake ethers

### Compile contract:

```
> code = fs.readFileSync('Voting.sol').toString()
> solc = require('solc')
> compiledCode = solc.compile(code)
```

### Deploy contract:

```
> abiDefinition = JSON.parse(compiledCode.contracts[':Voting'].interface)
> VotingContract = web3.eth.contract(abiDefinition)
> byteCode = compiledCode.contracts[':Voting'].bytecode
> deployedContract = VotingContract.new(['Borja','Lau','Jen'],{data: byteCode, from: web3.eth.accounts[0], gas: 4700000})
> deployedContract.address
> contractInstance = VotingContract.at(deployedContract.address)
```

VotingContract.new deploys the contract to the blockchain.

Get the address at which the contract is deployed, paste it in index.js:

```
> contractInstance.address
```

