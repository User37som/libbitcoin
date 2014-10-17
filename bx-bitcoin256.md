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
$ bx bitcoin256 900df00d
```
```
23429b4cc436b2ebd4aa33b904a1e08f195715c34d275e9088ea7b12af3872cd
```