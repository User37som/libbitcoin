Encrypt an EC private key as an encrypted private key (BIP38).
```sh
$ bx ec-to-ek --help
```
```
Usage: bx ec-to-ek [-hu] [--config VALUE] [--version VALUE] [PASSPHRASE] 
[EC_PRIVATE_KEY]                                                         

Info: Encrypt an EC private key as an encrypted private key (BIP38).     

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-u [--uncompressed]  Use the uncompressed public key format.             
-v [--version]       The desired payment address version.                

Arguments (positional):

PASSPHRASE           The passphrase for encrypting the private key.      
EC_PRIVATE_KEY       The EC private key to encrypt. If not specified the 
                     key is read from STDIN.
```
Third party-generated encrypted private keys are referred to as [multiplied](https://github.com/bitcoin/bips/blob/master/bip-0038.mediawiki#Encryption_when_EC_multiply_mode_is_used) by BIP-38. To create multiplied encrypted public keys use [token-new](bx-token-new) and [ec-new](bx-ec-new).

The `--version` option is a [libbitcoin enhancement](https://github.com/libbitcoin/libbitcoin/wiki/Altchain-Encrypted-Private-Keys) not yet specified in [BIP-38](https://github.com/bitcoin/bips/blob/master/bip-0038.mediawiki).

See also [ek-to-ec](bx-ek-to-ec).
### Example 1
mainnet
```sh
$ bx ec-to-ek "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
```
6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```
### Example 2
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-ek "my passphrase"
```
```
349e9b1e16620f3af0c8cdd313540c8c4174fc9aa7100f7e
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```
### Example 3
round trip
```sh
$ bx ec-to-ek "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f | bx ek-to-ec "my passphrase"
```
```
6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 4
--uncompressed
```sh
$ bx ec-to-ek -u "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
```
6PRPDbKfv3A45QPPfEtvcxM4oA6ShVL7t72VP74P1W3JEUHPrZXNy39FKe
```
### Example 5
--version 111 (testnet)
```sh
$ bx ec-to-ek -v 111 "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
```
8EzHSxX3sfZp6NjYUdt7fZAPCKByrFDS12PHfdexFLSaSAfM7wM7tw3Hof
```
### Example 6
--version 48 (litecoin), --uncompressed
```sh
$ bx ec-to-ek -u -v 48 "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
```
7BtJaSMBHZJMgKtDp4rNLDjkoCZu2e5av1FYxMwwvdq5AN124paeds82tP
```