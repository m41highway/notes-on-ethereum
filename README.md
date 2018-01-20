# Notes on Ethereum

## Geth

### Setup and run a Ethereum node
There are three working modes:
Fast Sync: By default, the first time you run geth command is in this mode
Full Sync: If the geth process has been interruped. An re-issue of geth command will be in this mode
Light Sync: A less secure way with header only 
Download link: https://ethereum.github.io/go-ethereum/downloads/

On Mac, set the PATH for geth
```
echo 'export PATH=YOUR_PATH_TO_GETH_FILE:$PATH' >> ~/.bash_profile
```

To run the geth process in Fast Sync Mode

```
./geth
```

To run the process in Full Sync Mode
Type Command-C to stop the process.

+ Delete the directory 'geth' under     /Users/YOUR_USER_NAME_ON_MAC/Library/Ethereum 
+ Run the geth command again


### Javascript IPC Interface

Connect to the Ethereum node

```
./geth attach ipc:/Users/YOUR_USER_NAME_ON_MAC/Library/Ethereum/geth.ipc
```

Create new account

```
> personal.newAccount();
```

Example result

```
Passphrase: 
Repeat passphrase: 
“0x32a28e00186612638d91ce7aad6c832ae56c2a9e"
```

Synchronize blockchain node

```
> eth.syncing
```

Example result

```
{
  currentBlock: 180885,
  highestBlock: 4930769,
  knownStates: 207716,
  pulledStates: 197461,
  startingBlock: 0
}
```

### RPC API reference
https://github.com/ethereum/go-ethereum/wiki/Management-APIs

## Private Blockchain Network
Initialize with gensis.json

```json
{
  "difficulty" : "0x20000",
  "extraData"  : "",
  "gasLimit"   : "0x8000000",
  "alloc": {},
  "config": {
        "chainId": 15,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    }
}
```


```
> geth init ./genesis.json --datadir my-chain-data
```

To start the network

```
> geth --datadir my-chain-data --nodiscover
```

Launch a Geth Javascript Console to interact with the node

```
> geth attach ipc:/YOUR_IPC_END_POINT/geth.ipc
```

In the javascript console, show current accounts by

```
> eth.accounts
```

To create new account

```
> personal.newAccount()
```

The private key of the new account is stored in keystore folder

## Get ether by mining

Set the account
```
> miner.setEtherbase(eth.accounts[0])
```

Run the miner

```
> miner.start(1)
```

Checkt the ether

```
> eth.getBalance(eth.accounts[0])
```


## Single command to start mining

```
geth --datadir my-chain-data/ --nodiscover --unlock 0 --mine 1
```


