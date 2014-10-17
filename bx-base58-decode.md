Convert a Base58 value to Base16.
```sh
$ bx base58-decode --help
```
```
Usage: bx base58-decode [-h] [--config VALUE] [BASE58]                   

Info: Convert a Base58 value to Base16.                                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE58               The Base58 value to decode as Base16. If not        
                     specified the value is read from STDIN.
```
# Example 1
```sh
$ bx base58-decode vYxp6yFC7qiVtK1RcGQQt3L6EqTc8YhEDLnSMLqDvp8D
```
```
031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```