Perform a SHA160 (also known as SHA-1) hash of Base16 data.  
```sh
$ bx sha160 --help
```
```
Usage: bx sha160 [-h] [--config VALUE] [BASE16]                          

Info: Perform a SHA160 (also known as SHA-1) hash of Base16 data.        

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 data to hash. If not specified the value 
                     is read from STDIN.
```
### Example 1
```sh
$ bx sha160 900df00d
```
```ec5386a03e88b5ac9328f4eabe5103e601906daa
```