Compose a Bitcoin URI from specified parts. 
```sh
$ bx uri-encode --help
```
```
Usage: bx uri-encode [-h] [--amount VALUE] [--config VALUE] [--label     
VALUE] [--message VALUE] [--request VALUE] [--stealth VALUE]             
[BITCOIN_ADDRESS]                                                        

Info: Compose a Bitcoin URI from specified parts.                        

Options (named):

-a [--amount]        The value of the amount parameter.                  
-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-l [--label]         The value of the label parameter.                   
-m [--message]       The value of the label parameter.                   
-r [--request]       The value of the payment request parameter.         
-s [--stealth]       The stealth address for the address part.           

Arguments (positional):

BITCOIN_ADDRESS      The Bitcoin address for the address part. 
```
### Example 1
```sh
$ bx uri-encode
```
```
```