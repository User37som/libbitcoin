Convert satoshi to BTC.
```sh
$ bx satoshi-to-btc --help
```
```
Usage: bx satoshi-to-btc [-h] [--config VALUE] [SATOSHI]                 

Info: Convert satoshi to BTC.                                            

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SATOSHI              The whole number of satoshi to convert. If not      
                     specified the value is read from STDIN.
```
### Example 1
```sh
$ bx satoshi-to-btc 42
```
```
0.00000042
```
### Example 2
maximum coinage
```sh
$ bx satoshi-to-btc 2099999997690000
```
```
20999999.9769
```
### Example 3
maximum representable in bx ([64 bit unsigned integer](http://en.wikipedia.org/wiki/Wheat_and_chessboard_problem))
```sh
$ bx satoshi-to-btc 18446744073709551615
```
```
184467440737.09551615
```
### Example 4
piped commands, round trip
```sh
$ bx satoshi-to-btc 18446744073709551615 | bx btc-to-satoshi
```
```
184467440737.09551615
18446744073709551615
```