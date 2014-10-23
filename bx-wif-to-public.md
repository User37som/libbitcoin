Derive the EC public key from a WIF private key.
```sh
$ bx wif-to-public --help
```
```
Usage: bx wif-to-public [-h] [--config VALUE] [WIF]                      

Info: Derive the EC public key from a WIF private key.                   

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

WIF                  The WIF private key. If not specified the value is  
                     read from STDIN.
```
### Example 1
```sh
$ bx wif-to-public L21LJEeJwK35wby1BeTjwWssrhrgQE2MZrpTm2zbMC677czAHHu3
```
```
0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36
```
### Example 2
[Bitcoin Wiki example](https://en.bitcoin.it/wiki/Wallet_import_format)
```sh
$ bx wif-to-public 5HueCGU8rMjxEXxiPuD5BDku4MkFqeZyd4dZ1jvhTVqvbTLvyTJ
```
04d0de0aaeaefad02b8bdc8a01a1b8b11c696bd3d66a2c5f10780d95b7df42645cd85228a6fb29940e858e7e55842ae2bd115d1ed7cc0e82d934e929c97648cb0a
```
### Example 3
piped commands, compressed
```sh
$ bx ec-to-wif 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8 | bx wif-to-public
```
```
L21LJEeJwK35wby1BeTjwWssrhrgQE2MZrpTm2zbMC677czAHHu3
0247140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36
```
### Example 4
piped commands, uncompressed
```sh
$ bx ec-to-wif -u 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8 | bx wif-to-public
```
```
5JuBiWpsjfXNxsWuc39KntBAiAiAP2bHtrMGaYGKCppq4MuVcQL
0447140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36e87bb04f401be3b770a0f3e2267a6c3b14a3074f6b5ce4419f1fcdc1ca4b1cb6
```
> The piped commands examples show the compression flag carried by the WIF, independently of the private key, and used when the public key is exposed.