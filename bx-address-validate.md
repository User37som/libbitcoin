Validate an address. Returns the address if it is valid.
```sh
$ bx address-validate --help
```
```
Usage: bx address-validate [-h] [--config VALUE] [BITCOIN_ADDRESS]

Info: Validate an address. Returns the address if it is valid.

Options (named):

-c [--config]        The path to the configuration settings file.
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

BITCOIN_ADDRESS      The Bitcoin address to validate. If not specified
                     the address is read from STDIN.
```
### Example 1
valid
```sh
$ bx address-validate 3J98t1WpEZ73CNmQviecrnyiWrnqRhWNLy
```
```
3J98t1WpEZ73CNmQviecrnyiWrnqRhWNLy
```
### Example 2
invalid
```sh
$ bx address-validate 0J98t1WpEZ73CNmQviecrnyiWrnqRhWNLy
```
```
The address is not valid.
```
### Example 3
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-public | bx ec-to-address | bx address-validate
```
```
86d8d776681092a71f7ac8a6292526e9
2422475cb9aa52a8383c37917553dc4f48cf4366d18793e664544336b202803c
033e4a533bb68b0cf8cff53632a8d3c5a0c70a7305ab199af97596ea38cd4e4648
16k1u5aUwxZ9wyg7KZbhpJMzqJaJBQPPqR
16k1u5aUwxZ9wyg7KZbhpJMzqJaJBQPPqR
```