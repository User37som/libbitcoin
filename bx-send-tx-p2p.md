Broadcast a transaction to the Bitcoin network via the Bitcoin peer-to-peer network.
```sh
$ bx send-tx-p2p --help
```
```
Usage: bx send-tx-p2p [-h] [--config VALUE] [--nodes VALUE] [TRANSACTION]

Info: Broadcast a transaction to the Bitcoin network via the Bitcoin     
peer-to-peer network.                                                    

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-n [--nodes]         The number of network nodes to send the transaction 
                     to, defaults to two.                                

Arguments (positional):

TRANSACTION          The Base16 transaction to send. If not specified the
                     transaction is read from STDIN.
```
### Example 1
```sh
$ bx send-tx-p2p ...
```
```
...
```