Derive the EC public key of an EC private key.
```sh
$ bx ec-to-public --help
```
```
Usage: bx ec-to-public [-hu] [--config VALUE] [EC_PRIVATE_KEY]

Info: Derive the EC public key of an EC private key. Defaults to the    
compressed public key format.

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-u [--uncompressed]  Derive using the uncompressed public key format.    

Arguments (positional):

EC_PRIVATE_KEY       The Base16 EC private key. If not specified the key 
                     is read from STDIN.
```