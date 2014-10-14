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