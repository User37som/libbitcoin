Convert an Electrum mnemonic to its seed.

> This command is currently based on the [Electrum implementation](https://github.com/libbitcoin/libbitcoin-explorer/issues/14).

```sh
bx mnemonic-decode --help
```
```
Usage: bx mnemonic-decode [-h] [--config VALUE] [WORD]...                

Info: Convert an Electrum mnemonic to its seed. WARNING: mnemonic should 
be generated from a random seed. WARNING: This implementation is         
deprecated in favor of BIP39.                                            

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

WORD                 The set of words from the Electrum word list. If not
                     specified the words are read from STDIN.
```
### Example 1
```sh
$ bx mnemonic-decode eternity blood task eternity blood task eternity blood task eternity blood task
```
```
baadf00dbaadf00dbaadf00dbaadf00d
```
### Example 2
```sh
$ bx mnemonic-decode eternity blood task
```
```
baadf00d
```