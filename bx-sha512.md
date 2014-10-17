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