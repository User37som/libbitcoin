Perform a SHA512 hash of Base16 data.
```sh
$ bx sha512 --help
```
```
Usage: bx sha512 [-h] [--config VALUE] [BASE16]                          

Info: Perform a SHA512 hash of Base16 data.                              

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BASE16               The Base16 data to hash. If not specified the value 
                     is read from STDIN.
```
### Example 1
```sh
$ bx sha512 900df00d
```
```
d1f51c57b00d399be4e708bfd1d76d711bbbdda534383df4f06933187bce41fdfdaa6385cfa960f68abcd33ae0573deb39503f73e8e2b7645845671f11855f8e
```
### Example 2
piped commands
```sh
$ bx base16-encode "L'homme est libre au moment qu'il veut l'être." | bx sha512
```
```
4c27686f6d6d6520657374206c69627265206175206d6f6d656e7420717527696c2076657574206c27ea7472652e
c9beafc853a93a29fab2509720c93a516c80a51f1e7eca657d919fb95a130b9dd3f003ef474618e667cd083bd2a3e31bcc17ffd8671a8d07bbda96a2acd7e038
```