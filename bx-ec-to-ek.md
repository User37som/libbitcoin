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
See also [ek-to-ec](bx-ek-to-ec).
### Example 1
```sh
$ bx ec-to-ek "my passphrase" c94e9cc74bb32e0bff1138ba6d7f0f986e025a81fc600a3723e7e6faa25d3dd1
```
```
6PYNAp4ckhJBFiRSvimDCT12MpuM4ZsqPV4Cj3cSiUQUhMMKTSe97jqFPr
```
### Example 1
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-ek "my passphrase"
```
```
349e9b1e16620f3af0c8cdd313540c8c4174fc9aa7100f7e
261fc32e9f29c70e3d898aa7db028c81ede0658e8ff8ffab8160073c048ae83f
6PYXCdvtrs4NN1TjUYbGS5Sd2gjsVsDm7GttqERRWvRjWDsrhQfJeEHrg5
```