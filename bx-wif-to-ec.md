Convert a WIF private key to an EC private key.  
```sh
$ bx wif-to-ec --help
```
```
Usage: bx wif-to-ec [-h] [--config VALUE] [WIF]                          

Info: Convert a WIF private key to an EC private key.                    

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

WIF                  The value to convert. If not specified the value is 
                     read from STDIN.
```
### Example 1
uncompressed
```sh
$ bx wif-to-ec L21LJEeJwK35wby1BeTjwWssrhrgQE2MZrpTm2zbMC677czAHHu3
```
```
8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8
```
### Example 2
piped commands, compression does not affect private key
```sh
$ bx ec-to-wif -u 8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8 | bx wif-to-ec
```
```
5JuBiWpsjfXNxsWuc39KntBAiAiAP2bHtrMGaYGKCppq4MuVcQL
8ed1d17dabce1fccbbe5e9bf008b318334e5bcc78eb9e7c1ea850b7eb0ddb9c8
```