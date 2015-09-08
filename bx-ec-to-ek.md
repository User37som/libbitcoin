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

PASSPHRASE           The passphrase for encryptingthe private key.       
EC_PRIVATE_KEY       The EC private key to encrypt. If not specified the 
                     key is read from STDIN.
```
See also [ek-to-ec](bx-ek-to-ec).
### Example 1
```sh
TODO
```