Validate and decompose a Bitcoin URI into its parts. 
```sh
$ bx uri-decode --help
```
```
Usage: bx uri-decode [-h] [--config VALUE] [--format VALUE] [URI]        

Info: Validate and decompose a Bitcoin URI into its parts.               

Options (named):

-c [--config]        The path to the configuration settings file.        
-f [--format]        The output format. Options are 'info', 'json' and   
                     'xml', defaults to 'info'.                          
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

URI                  The Bitcoin URI to decode. If not specified the URI 
                     is read from STDIN.   
```
### Example 1
```sh
$ bx uri-decode
```
```
```