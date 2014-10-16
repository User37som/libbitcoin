Convert a seed to its Electrum mnemonic.

> This command is currently based on the [Electrum implementation](https://github.com/libbitcoin/libbitcoin-explorer/issues/14).

```sh
$ bx mnemonic-encode --help
```
```
Usage: bx mnemonic-encode [-h] [--config VALUE] [SEED]                   

Info: Convert a seed to its Electrum mnemonic.                           

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SEED                 The Base16 randomness seed. Must be at least 128    
                     bits in length. If not specified the seed is read   
                     from STDIN. WARNING: This implementation is         
                     deprecated in favor of BIP39.
```
### Example 1
128 bit seed
```sh
$ bx mnemonic-encode baadf00dbaadf00dbaadf00dbaadf00d
```
```
eternity blood task eternity blood task eternity blood task eternity blood task
```
### Example 2
short seed error
```sh
$ bx mnemonic-encode baadf00dbaadf00d
```
```
The seed is less than 128 bits long.
```
### Example 3
piped commands
```sh
$ bx seed | bx mnemonic-encode
```
```
3dce4601da9a3d3c31b2af0e4677ca46
sweat gasp monkey grip lesson eternity neck candle physical grown bread belly
```