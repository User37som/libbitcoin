Perform a SHA256 hash of a SHA256 hash of Base16 data.   
```sh
$ bx bitcoin256 --help
```
```
Usage: bx bitcoin256 [-h] [--config VALUE] [BASE16]                      

Info: Perform a SHA256 hash of a SHA256 hash of Base16 data.             

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 data to hash. If not specified the data  
                     is value from STDIN.
```
### Example 1
```sh
$ bx bitcoin256 baadf00d
```
```
1ae79d785d7a487ec4cc49a340bd962638a6f55d5452ee547b61e654f6147d70
```