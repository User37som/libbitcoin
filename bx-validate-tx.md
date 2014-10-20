Determine if a transaction is valid for submission to the blockchain.
```sh
$ bx validate-tx --help
```
```
Usage: bx validate-tx [-h] [--config VALUE] [TRANSACTION]                

Info: Determine if a transaction is valid for submission to the          
blockchain. Requires an Obelisk server connection.                       

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
### Example 1
```sh
$ bx validate-tx ...
```
```
...
```