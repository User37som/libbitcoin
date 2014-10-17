Convert a Base16 value to Base58.  
```sh
$ bx base58-encode --help
```
```
Usage: bx base58-encode [-h] [--config VALUE] [BASE16]                   

Info: Convert a Base16 value to Base58.                                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 value to encode as Base58. If not        
                     specified the value is read from STDIN.
```
# Example 1
```sh
$ bx base58-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
vYxp6yFC7qiVtK1RcGQQt3L6EqTc8YhEDLnSMLqDvp8D
```
# Example 2
```sh
$ bx base16-encode "Satoshi Nakamoto" | bx base58-encode
```
```
5361746f736869204e616b616d6f746f
BJBRbygJtzBfp4gjJG2iqL
```