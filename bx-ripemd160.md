Perform a RIPEMD160 hash of Base16 data.
```sh
$ bx ripemd160 --help
```
```
Usage: bx ripemd160 [-h] [--config VALUE] [BASE16]                       

Info: Perform a RIPEMD160 hash of Base16 data.                           

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 data to hash. If not specified the data  
                     is read from STDIN.
```
### Example 1
```sh
$ bx ripemd160 900df00d
```
```
31589998e7e92e769bfd5d453d12fbfa17c86297
```