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
-f [--format]        The output format. Options are 'info', 'json', and  
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

WRAPPED              The Base16 data to unwrap. If not specified the     
                     value is read from STDIN.
```
See also [wrap-encode](bx-wrap-encode).
### Example 1
version 0
```sh
$ bx wrap-decode 00031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd0065b09d03c
```
```js
wrapper
{
    checksum 1020266843
    payload 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    version 0
}
```
### Example 2
version 42
```sh
$ bx wrap-decode 2a031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006298eebe4
```
```js
wrapper
{
    checksum 3840642601
    payload 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    version 42
}
```
### Example 3
piped input
```sh
$ echo 2a031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006298eebe4 | bx wrap-decode
```
```js
wrapper
{
    checksum 3840642601
    payload 031bab84e687e36514eeaf5a017c30d32c1f59dd4ea6629da7970ca374513dd006
    version 42
}
```