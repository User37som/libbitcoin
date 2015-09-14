Recover the EC private key from an encrypted private key (BIP38). 
```sh
$ bx ek-to-ec --help
```
```
Usage: bx ek-to-ec [-h] [--config VALUE] [PASSPHRASE] [EK_PRIVATE_KEY]   

Info: Recover the EC private key from an encrypted private key (BIP38).  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PASSPHRASE           The passphrase that was used to encrypt the         
                     encrypted private key.                              
EK_PRIVATE_KEY       The encrypted private key to decrypt.
```
Altchain support is a [libbitcoin enhancement](https://github.com/libbitcoin/libbitcoin/wiki/Altchain-Encrypted-Private-Keys) not yet specified in [BIP-38](https://github.com/bitcoin/bips/blob/master/bip-0038.mediawiki).

Public key compression and payment address version (i.e. altchain) affect the encrypted private key but have no impact on the value of the underlying elliptic curve private key. These values are carried in the encoding to inform payment address generation.

See also [ec-to-ek](bx-ec-to-ek) and [ek-to-address](bx-ek-to-address).
### Example 1
incorrect passphrase
```sh
$ bx ek-to-ec "i forgot" 6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```
```
The passphrase is incorrect.
```
### Example 2
mainnet
```sh
$ bx ek-to-ec "my passphrase" 6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 3
piped input
```sh
$ echo 6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5 | bx ek-to-ec "my passphrase"
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 4
round trip
```sh
$ bx ec-to-ek "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f | bx ek-to-ec "my passphrase"
```
```
6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 5
testnet, compressed
```sh
$ bx ek-to-ec "my passphrase" 8EzHSxX3sfZp6NjYUdt7fZAPCKByrFDS12PHfdexFLSaSAfM7wM7tw3Hof
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 6
litecoin, uncompressed
```sh
$ bx ek-to-ec "my passphrase" 7BtJaSMBHZJMgKtDp4rNLDjkoCZu2e5av1FYxMwwvdq5AN124paeds82tP
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 7
multiplied
```sh
$ bx ek-to-ec "my passphrase" [TODO]
```
```
[TODO]
```