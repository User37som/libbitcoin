Extract the EC public key of an encrypted public key (BIP38).  
```sh
$ bx ek-public-to-ec --help
```
```
Usage: bx ek-public-to-ec [-h] [--config VALUE] [PASSPHRASE]             
[EK_PUBLIC_KEY]                                                          

Info: Extract the EC public key of an encrypted public key (BIP38).      

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PASSPHRASE           The passphrase that was used to generate the        
                     encrypted private key.                              
EK_PUBLIC_KEY        The encrypted public key to decrypt.
```
See also [ek-public-to-address](bx-ek-public-to-address).
### Example 1
```sh
TODO
```