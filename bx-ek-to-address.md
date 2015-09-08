Extract the payment address of an encrypted private key (BIP38).
```sh
$ bx ek-to-address --help
```
```
Usage: bx ek-to-address [-h] [--config VALUE] [PASSPHRASE]               
[EK_PRIVATE_KEY]                                                         

Info: Extract the payment address of an encrypted private key (BIP38).   

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

PASSPHRASE           The passphrase that was used to generate the        
                     intermediate passphrase token or to lock the        
                     encrypted private key.                              
EK_PRIVATE_KEY       The encrypted private key from which to extract the 
                     payment address.
```
See also [ek-to-ec](bx-ek-to-ec).
### Example 1
```sh
TODO
```