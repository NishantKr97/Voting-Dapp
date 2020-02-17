# Blockchain Technology


## Steps to Run the Repo

### Run the Ethereum Server
- mkdir miner
- cd miner
- inside it create genesis.json as follows:

``` 
{
    "config": {
     "chainId": 15,
     "homesteadBlock": 0,
     "eip155Block": 0,
     "eip158Block": 0
    },
    "nonce": "0x0000000000000042",
    "timestamp": "0x0",
    "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "gasLimit": "0x8000000",
    "difficulty": "0x400",
    "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "coinbase": "0xa312405DFfc5f5e1Afd0421108F10e002341BFA0",
    "alloc": {
     "0xa312405DFfc5f5e1Afd0421108F10e002341BFA0": {
     "balance": "0x1337000000000000000000"},
     "0x6977e930c8f929149dBbbA05a93a8201d4B0B82B": {
     "balance": "0x2337000000000000000000"}
    }
 }
```
- create a new account using ```geth account new```, and replace it in the above genesis.json in "alloc" and "coinbase"
- mkdir data
- init the server as
``` 
geth --datadir data init genesis.json
```
- run the server as
```
 geth --datadir data --rpc --rpcapi web3,eth,personal,miner,net,txpool --rpccorsdomain="*" --rpcport 8400 --rpcaddr "0.0.0.0" --networkid 10101010 console --allow-insecure-unlock
```


### Deploy on the above ethereum server
```
truffle migrate
```

