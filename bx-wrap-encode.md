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