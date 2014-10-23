Assign a script to an existing transaction input.
```sh
$ bx input-set --help
```
```
Usage: bx input-set [-h] [--config VALUE] [--index VALUE]                
SIGNATURE_SCRIPT [TRANSACTION]                                           

Info: Assign a script to an existing transaction input.                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-i [--index]         The ordinal position of the input within the        
                     transaction, defaults to zero.                      

Arguments (positional):

SIGNATURE_SCRIPT     The signature script to assign to the input.        
TRANSACTION          The Base16 transaction. If not specified the        
                     transaction is read from STDIN.
```
### Example 1

For the **preceding step** see [Example 1](bx-input-sign) of the `input-sign` command.

```sh
$ 
```
```
```

The **complete scenario** is detailed in [How to Receive and Spend](How-to-Receive-and-Spend).