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

The entire voting system made simple


(Rough thought put in words)


```
                                           Registration
                Voter (before Reg) ----------------------------> SYSTEM (the blockchain system--probably with other things)
                                   <---------------------------- / \
                                     Special Key link to BlkCh    |
                                                                  |
                                                                  |
                Voter (after Reg, during vote) -------------------- Uses the key to auth (with 2fa like fingerprint)

                                                                  |                     
                                                                  |
                                                                  |
                                                                  |
                                                                  \/
                                                              VOTE COUNT
                                                              
```

### Points favouring idea :

0. Easy registering with the voting system.
1. No need of maintaining a separate voting list, verifying auth key is sufficient.
2. Live vote count is possible as the vote is instantly updated in the system.
3. No need of long counting procedures as the vote is updated instantly.
4. No problems of auth failures as the BlockChain system is secure and provides access only to the unique key of the user + 2fa with fingerprint.
5. Problems of crooked govt. denying voters to vote with faulty voters list is removed as there is no need of pre-processing.
