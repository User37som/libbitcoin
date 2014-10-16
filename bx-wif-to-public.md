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
```sh
$ bx wif-to-public 5JuBiWpsjfXNxsWuc39KntBAiAiAP2bHtrMGaYGKCppq4MuVcQL
```
```
0447140d2811498679fe9a0467a75ac7aa581476c102d27377bc0232635af8ad36e87bb04f401be3b770a0f3e2267a6c3b14a3074f6b5ce4419f1fcdc1ca4b1cb6
```
Examples 2 and 3 show that the compression flag is carried in the WIF, independently of the private key and used when the public key is exposed.