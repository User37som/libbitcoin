Derive the HD (BIP32) public key of a HD private key. 
```sh
$ bx hd-to-public --help
```
```
Usage: bx hd-to-public [-h] [--config VALUE] [HD_PRIVATE_KEY]            

Info: Derive the HD (BIP32) public key of a HD private key.              

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

HD_PRIVATE_KEY       The HD private key. If not specified the key is read
                     from STDIN.  
```
### Example 1
