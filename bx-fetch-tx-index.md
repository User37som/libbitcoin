Get the block height and index of a transaction.
```sh
$ bx fetch-tx-index --help
```
```
Usage: bx fetch-tx-index [-h] [--config VALUE] [--format VALUE] [HASH]   

Info: Get the block height and index of a transaction. Requires a        
Libbitcoin server connection.                                            

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

HASH                 The Base16 transaction hash of the transaction index
                     to get. If not specified the transaction hash is    
                     read from STDIN.  
```
This command supports [configuration settings](Configuration-Settings).
### Example 1
[DPR Seized Coins #1](https://blockchain.info/tx/e3d6fe810f79b293705ed6e587951332c545a87fac860278b2ad4447106bb789) 
```sh
$ bx fetch-tx-index e3d6fe810f79b293705ed6e587951332c545a87fac860278b2ad4447106bb789
```
```js
metadata
{
    hash e3d6fe810f79b293705ed6e587951332c545a87fac860278b2ad4447106bb789
    height 325116
    index 179
}
```