Convert BTC to satoshi.
```sh
$ bx btc-to-satoshi --help
```
```
Usage: bx btc-to-satoshi [-h] [--config VALUE] [BTC]                     

Info: Convert BTC to satoshi.                                            

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BTC                  The number of BTC to convert. If not specified the  
                     value is read from STDIN.
```
### Example 1
```sh
$ bx btc-to-satoshi 1
```
```
100000000
```
### Example 2
```sh
$ bx btc-to-satoshi 21000000
```
```
2100000000000000
```