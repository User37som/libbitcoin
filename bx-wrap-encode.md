Add a version byte and checksum to Base16 data.
```sh
$ bx wrap-encode --help
```
```
Usage: bx wrap-encode [-h] [--config VALUE] [--version VALUE] [PAYLOAD]  

Info: Add a version byte and checksum to Base16 data.                    

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired version number.                         

Arguments (positional):

PAYLOAD              The Base16 data to wrap. If not specified the value 
                     is read from STDIN.
```
See also [wrap-decode](bx-wrap-decode).
### Example 1
--version 0
```sh
$ bx wrap-encode 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
00031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd0065b09d03c
```
### Example 2
--version 42
```sh
$ bx wrap-encode -v 42 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
```
```
2a031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006298eebe4
```
### Example 3
Demonstrate `wrap-encode` equivalence to steps 4-8 in *[Technical background of version 1 Bitcoin addresses]((https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses))*.
```sh
$ bx wrap-encode 010966776006953d5567439e5e39f86a0d273bee | bx base58-encode
```
```
00010966776006953d5567439e5e39f86a0d273beed61967f6
16UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM
```
### Example 4
piped input
```sh
$ bx base16-encode "Satoshi Nakamoto" | bx wrap-encode
```
```
5361746f736869204e616b616d6f746f
005361746f736869204e616b616d6f746f5311991f
```