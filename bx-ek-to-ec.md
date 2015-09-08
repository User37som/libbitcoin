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
EK_PRIVATE_KEY       The encrypted private key to unlock.
```
See also [ec-to-ek](bx-ec-to-ek).
### Example 1
```sh
TODO
```