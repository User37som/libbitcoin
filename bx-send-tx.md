Broadcast a transaction to the Bitcoin network via an Obelisk server.
```sh
$ bx send-tx --help
```
```
Usage: bx send-tx [-h] [--config VALUE] [TRANSACTION]                    

Info: Broadcast a transaction to the Bitcoin network via an Obelisk      
server.                                                                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

TRANSACTION          The Base16 transaction to send. If not specified the
                     transaction is read from STDIN. 
```
### Example 1
```sh
$ bx send-tx ...
```
```
...
```