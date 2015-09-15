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
mainnet
```sh
$ bx ek-to-ec "my passphrase" 6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 2
incorrect passphrase
```sh
$ bx ek-to-ec "i forgot" 6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```
```
The passphrase is incorrect.
```
### Example 3
piped input
```sh
$ echo 6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5 | bx ek-to-ec "my passphrase"
```
```
6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5 
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
uncompressed
```sh
$ bx ek-to-ec "my passphrase" 6PRPDbKfv3A45QPPfEtvcxM4oA6ShVL7t72VP74P1W3JEUHPrZXNy39FKe
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 6
testnet
```sh
$ bx ek-to-ec "my passphrase" 8EzHSxX3sfZp6NjYUdt7fZAPCKByrFDS12PHfdexFLSaSAfM7wM7tw3Hof
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 7
litecoin, uncompressed
```sh
$ bx ek-to-ec "my passphrase" 7BtJaSMBHZJMgKtDp4rNLDjkoCZu2e5av1FYxMwwvdq5AN124paeds82tP
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 8
multiplied: lot/sequence
```sh
$ bx ek-to-ec "my passphrase" 6PoJB3hjqER7KJDeo69pfX3ttV5DPaQPEf4pZEwhNYjTjqMdvif5qfE34S
```
```
056115405c7161e62216fcbbf48832c8ed5ef66819a361ec8f6583f12bb2a924
```
### Example 9
multiplied
```sh
$ bx ek-to-ec "my passphrase" 6PnUht3dP5Jdcp1B7NGqkEoBw5Ja2wWEeQMDRHqLNrBG4Rqo59eVfMd98B
```
```
b1c23d8bf9a957349eafd851808ce5555279cc103924ebd96ddaa3b03666ac74
```
### Example 10
multiplied: uncompressed
```sh
$ bx ek-to-ec "my passphrase" 6PfM4jsmgX1veYaiBXqqDe3J8hFtAriohdNGjPfrbt7aQ8H53nijYN6svW
```
```
1MydksvfdWNXM1KnVTS8A78M4b78aJcL1W
```
### Example 11
multiplied: testnet
```sh
$ bx ek-to-ec "my passphrase" 8FEMBzS4QWPwxyzrYJxHwzSrdNzroFiQjkAnpf51xcPPXkTvqGrD8bVq68
```
```
b1c23d8bf9a957349eafd851808ce5555279cc103924ebd96ddaa3b03666ac74
```
### Example 12
multiplied: litecoin, uncompressed
```sh
$ bx ek-to-ec "my passphrase" 7C8LFBdEAqptMNYUNr2cgcP7bppVgsqtz1fXVeSzAPf8VkB29XMKDtF71p
```
```
b1c23d8bf9a957349eafd851808ce5555279cc103924ebd96ddaa3b03666ac74
```