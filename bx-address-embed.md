Create a payment address with an embedded record of binary data. 
```sh
$ bx address-embed --help
```
```
Usage: bx address-embed [-h] [--config VALUE] [--version VALUE] [DATA]   

Info: Create a payment address with an embedded record of binary data.   

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired payment address version.                

Arguments (positional):

DATA                 The binary data to encode as Base16. This can be    
                     text or any other data. If not specified the data is
                     read from STDIN.
```
The data is hashed as RIPEMD160 and then embedded in a script of the form: `dup hash160 [ RIPEMD160 ] equalverify checksig`. The script is then serialized, hashed as RIPEMD160, and used with the specified version to create a Bitcoin payment address.

See the [list of Bitcoin address prefixes](https://en.bitcoin.it/wiki/List_of_address_prefixes) for a detailed description of `version`.
### Example 1
```sh
$ bx address-embed "Satoshi Nakamoto"
```
```
168LnUjqoJLie1PW5dTaF2vKUU9Jf6Fe4a
```
### Example 2
piped input
```sh
$ echo Satoshi Nakamoto | bx address-embed
```
```
Satoshi Nakamoto 
168LnUjqoJLie1PW5dTaF2vKUU9Jf6Fe4a
```
### Example 3
--version 111 (testnet)
```sh
$ bx address-embed -v 111 "Satoshi Nakamoto"
```
```
mkeJ5XppcKmyR7s7oCRx4x8eLTk1Xrso8t
```