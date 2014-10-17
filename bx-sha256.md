Perform a SHA256 hash of Base16 data.
```sh
$ bx sha256 --help
```
```
Usage: bx sha256 [-h] [--config VALUE] [BASE16]                          

Info: Perform a SHA256 hash of Base16 data.                              

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 data to hash. If not specified the value 
                     is read from STDIN. 
```
### Example 1
```sh
$ bx sha256 900df00d
```
```
f0ebe3bd55115e573ba35c2b1b65a923ff64c7a548d0deab73f9314754a9149d
```
### Example 2
```sh
$ bx base16-encode abc | bx sha256
```
```
616263
ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f20015ad
```
### Example 3
```sh
$ bx base16-encode abcdbcdecdefdefgefghfghighijhijkijkljklmklmnlmnomnopnopq| bx sha256
```
```
6162636462636465636465666465666765666768666768696768696a68696a6b696a6b6c6a6b6c6d6b6c6d6e6c6d6e6f6d6e6f706e6f7071
248d6a61d20638b8e5c026930c3e6039a33ce45964ff2167f6ecedd419db06c1
```