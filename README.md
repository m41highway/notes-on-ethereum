# Notes on Ethereum

## Geth

### Setup and run a Ethereum node
There are three working modes:
Fast Sync: By default, the first time you run geth command is in this mode
Full Sync: If the geth process has been interruped. An re-issue of geth command will be in this mode
Light Sync: A less secure way with header only 
Download link: https://ethereum.github.io/go-ethereum/downloads/

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