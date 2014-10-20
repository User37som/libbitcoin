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
                     is read from STDIN.
```
### Example 1
```sh
$ bx bitcoin160 900df00d
```
```
49f180cdaa4c6564f74a0b0321633bbcba4ef9c5
```
Notice that the following commands produce the equivalent result.
```sh
$ bx sha256 900df00d | bx ripemd160
```
```
f0ebe3bd55115e573ba35c2b1b65a923ff64c7a548d0deab73f9314754a9149d
49f180cdaa4c6564f74a0b0321633bbcba4ef9c5
```
### Example 2
piped commands
```sh
$ bx base16-encode "L'homme est libre au moment qu'il veut l'être." | bx bitcoin160
```
```
4c27686f6d6d6520657374206c69627265206175206d6f6d656e7420717527696c2076657574206c27ea7472652e
7cbb98db61cff05c303c121f30754bd649dcb519
```