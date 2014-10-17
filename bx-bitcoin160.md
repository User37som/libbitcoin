Perform a RIPEMD160 hash of a SHA256 hash of Base16 data.
```sh
$ bx bitcoin160 --help
```
```
Usage: bx bitcoin160 [-h] [--config VALUE] [BASE16]                      

Info: Perform a RIPEMD160 hash of a SHA256 hash of Base16 data.          

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 data to hash. If not specified the data  
                     is value from STDIN.
```
# Example 1
```sh
$ bx bitcoin160 900df00d
```
```
49f180cdaa4c6564f74a0b0321633bbcba4ef9c5
```