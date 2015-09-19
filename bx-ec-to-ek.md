Encrypt an EC private key as an encrypted private key (BIP38).
```sh
$ bx ec-to-ek --help
```
```
Usage: bx ec-to-ek [-hu] [--config VALUE] [--version VALUE] PASSPHRASE   
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
empty passphrase
```sh
$ bx ec-to-ek "" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
```
6PYXCdvttCfzn7bo5NrhXsSE1hrYgw2oLbGQCvSLMZV4qr7FEJK7fJhN4R
```
### Example 3
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-ek "my passphrase"
```
```
349e9b1e16620f3af0c8cdd313540c8c4174fc9aa7100f7e
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
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
--uncompressed
```sh
$ bx ec-to-ek -u "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
```
6PRPDbKfv3A45QPPfEtvcxM4oA6ShVL7t72VP74P1W3JEUHPrZXNy39FKe
```
### Example 6
--version 111 ([TEST](https://github.com/libbitcoin/libbitcoin/wiki/BIP44-Altcoin-Version-Mappings#bip44-altcoin-version-mapping-table) version/WIF column)
```sh
$ bx ec-to-ek -v 239 "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
```
675v6gkbEo9sVFM78zaYucgBFs8NRYeRmstr7RLw7DzrGvhJj7cPE22hBk
```
### Example 7
--version 176 ([LTC](https://github.com/libbitcoin/libbitcoin/wiki/BIP44-Altcoin-Version-Mappings#bip44-altcoin-version-mapping-table) version/WIF column), --uncompressed
```sh
$ bx ec-to-ek -u -v 48 "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
```
9KuZDrNHkhZ4FWCLstF426suoni93kzMwAETwya7F5FzmnJkiPr3FtdDUV
```