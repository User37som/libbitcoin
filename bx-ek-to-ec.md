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
See also [ec-to-ek](bx-ec-to-ek) and [ek-to-address](bx-ek-to-address).
### Example 1
```sh
$ bx ek-to-ec "my passphrase" 6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```
```
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 2
round trip
```sh
$ bx ec-to-ek "my passphrase" 261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f | bx ek-to-ec "my passphrase"
```
```
6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
```
### Example 3
incorrect passphrase
```sh
$ bx ek-to-ec "i forgot" 6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```
```
The passphrase is incorrect.
```