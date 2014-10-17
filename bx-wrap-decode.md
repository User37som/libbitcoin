Validate the checksum of a Base16 data and recover its version byte
and data.
```sh
$ bx wrap-decode --help
```
```
Usage: bx wrap-decode [-h] [--config VALUE] [--format VALUE] [WRAPPED]   

Info: Validate the checksum of a Base16 data and recover its version byte
and data.                                                                

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'json', 'xml', 'info'
                     or 'native', defaults to native.                    
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

WRAPPED              The Base16 data to unwrap. If not specified the     
                     value is read from STDIN.
```
### Example 1
```sh
$ bx wrap-decode 00031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd0065b09d03c
```
```
wrapper
{
    checksum 1020266843
    payload 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    version 0
}
```