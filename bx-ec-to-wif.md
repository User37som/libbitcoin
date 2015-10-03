Convert an EC private key to a WIF private key.
```sh
$ bx ec-to-wif --help
```
```
Usage: bx ec-to-wif [-hu] [--config VALUE] [--version VALUE]             
[EC_PRIVATE_KEY]                                                         

Info: Convert an EC private key to a WIF private key. The result         
associates with the compressed public key format by default.             

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-u [--uncompressed]  Associate the result with the uncompressed public   
                     key format.                                         
-v [--version]       The desired WIF version, defaults to 128.           

Arguments (positional):

EC_PRIVATE_KEY       The Base16 EC private key to convert. If not        
                     specified the key is read from STDIN.   
```
See also [wif-to-ec](bx-wif-to-ec).
### Example 1
```sh
$ bx ec-to-wif 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8
```
```
L21LJEeJwK35wby1BeTjwWssrhrgQE2MZrpTm2zbMC677czAHHu3
```
### Example 2
--uncompressed
```sh
$ bx ec-to-wif -u 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8
```
```
5JuBiWpsjfXNxsWuc39KntBAiAiAP2bHtrMGaYGKCppq4MuVcQL
```
### Example 3
[Bitcoin Wiki example](https://en.bitcoin.it/wiki/Wallet_import_format)
```sh
$ bx ec-to-wif -u 0c28fca386c7a227600b2fe50b7cae11ec86d3bf1fbe471be89827e19d72aa1d
```
```
5HueCGU8rMjxEXxiPuD5BDku4MkFqeZyd4dZ1jvhTVqvbTLvyTJ
```
### Example 4
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-wif
```
```
6e3f120eb1b8c51486775550b7a44d84
984826b715209c50673499ac5faa0b84a4d61e9ef62a231a79ea67102909a0f3
L2Kj7UjmWSaJQed5RKLeJk12Ai17CZdmk2svNzi2aUkMTgYC1Tb1
```
### Example 5
--version 239 (testnet)
```sh
$ bx ec-to-wif -v 239 1560496d135730f5a1bb39580abba1fe8ea270768a08c49a66732772b0b811e2
```
```
cNJFgo1driFnPcBdBX8BrJrpxchBWXwXCvNH5SoSkdcF6JXXwHMm
```