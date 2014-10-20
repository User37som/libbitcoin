Broadcast a transaction to the Bitcoin network via a single Bitcoin network node.
```sh
$ Usage: bx send-tx-node [-h] [--config VALUE] [--port VALUE] [--host      
VALUE] [TRANSACTION]                                                     
```
```
Info: Broadcast a transaction to the Bitcoin network via a single Bitcoin
network node.                                                            

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-p [--port]          The IP port of the Bitcoin service on the node.     
                     Defaults to 8333, the standard for mainnet.         
-t [--host]          The IP address or DNS name of the node. Defaults to 
                     localhost.                                          

Arguments (positional):

TRANSACTION          The Base16 transaction to send. If not specified the
                     transaction is read from STDIN.
```
### Example 1
```sh
$ bx send-tx-node ...
```
...
```
