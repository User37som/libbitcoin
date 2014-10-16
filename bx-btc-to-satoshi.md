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
$ bx btc-to-satoshi 42
```
```
4200000000
```
### Example 2
maximum coinage
```sh
$ bx btc-to-satoshi 20999999.9769
```
```
2099999997690000
```
### Example 3
maximum representable in bx ([64 bit unsigned integer](http://en.wikipedia.org/wiki/Wheat_and_chessboard_problem))
```sh
$ bx btc-to-satoshi 184467440737.09551615
```
```
18446744073709551615
```