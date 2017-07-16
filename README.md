# voting-blockchain-testrcp
```sh
$ npm install ethereumjs-testrpc web3
$ npm install solc
```
RUN: 

```sh
node_modules/.bin/testrpc run testrpc
```

in anorther terminal RUN:
```sh
node
Web3 = require('web3')
web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));
web3.eth.accounts // the testrpc give us 10 private hash

code = fs.readFileSync('Voting.sol').toString()
solc = require('solc')

compiledCode = solc.compile(code)
abiDefinition = JSON.parse(compiledCode.contracts[':Voting'].interface)
VotingContract = web3.eth.contract(abiDefinition)
byteCode = compiledCode.contracts[':Voting'].bytecode

deployedContract = VotingContract.new(['Raphael','Andre','Igor'],{data: byteCode, from: web3.eth.accounts[0], gas: 4700000})
deployedContract.address

contractInstance = VotingContract.at(deployedContract.address) // this addres we use on index.js
contractInstance.totalVotesFor.call('Raphael')
contractInstance.voteForCandidate('Raphael', {from: web3.eth.accounts[0]})
contractInstance.totalVotesFor.call('Raphael').toLocaleString()
```

```sh
$ cd dillinger
$ npm install -d
$ node app
```
