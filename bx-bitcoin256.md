Perform a SHA256 hash of a SHA256 hash of Base16 data and then reverse the byte order. 
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
                     is read from STDIN.
```
### Example 1
```sh
$ bx bitcoin256 900df00d
```
```
23429b4cc436b2ebd4aa33b904a1e08f195715c34d275e9088ea7b12af3872cd
```
Notice that following commands produce the same result with the exception that the resulting hash [cd7238af...] is in the reverse byte order of the `bitcoin256` command output [...af3872cd]. This is an idiosyncrasy of the reference implementation.
```sh
$ bx sha256 900df00d | bx sha256
```
```
f0ebe3bd55115e573ba35c2b1b65a923ff64c7a548d0deab73f9314754a9149d
cd7238af127bea88905e274dc31557198fe0a104b933aad4ebb236c44c9b4223
```
### Example 2
piped commands
```sh
$ bx base16-encode "Give me control of a nation's money and I care not who makes the laws." | bx bitcoin256
```
```
47697665206d6520636f6e74726f6c206f662061206e6174696f6e2773206d6f6e657920616e6420492063617265206e6f742077686f206d616b657320746865206c6177732e
47057d00d7f51721444daf837b491ed2f97c3ce1f2e68be9bca9818228f65cff
```