Perform a SHA256 hash of a SHA256 hash of Base16 data and then     
reverse the byte order. 
```sh
$ bx bitcoin256 --help
```
```
Usage: bx bitcoin256 [-h] [--config VALUE] [BASE16]                      

Info: Perform a SHA256 hash of a SHA256 hash of Base16 data and then     
reverse the byte order.                                                  

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
### Example 2
piped commands, bitcoin256 equivalent (with byte order reversed)
```sh
$ bx sha256 900df00d | bx sha256
```
```
f0ebe3bd55115e573ba35c2b1b65a923ff64c7a548d0deab73f9314754a9149d
cd7238af127bea88905e274dc31557198fe0a104b933aad4ebb236c44c9b4223
```