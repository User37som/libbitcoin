Create an encrypted public key from an intermediate passphrase token (BIP38).
```sh
$ bx ek-public --help
```
```
Usage: bx ek-public [-hu] [--config VALUE] [--version VALUE] [TOKEN]     
[SEED]                                                                   

Info: Create an encrypted public key from an intermediate passphrase     
token (BIP38).                                                           

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.  
-u [--uncompressed]  Use the uncompressed public key format, as used to  
                     create the corresponding encrypted private key.     
-v [--version]       The desired payment address version used to create  
                     the corresponding encrypted private key.            

Arguments (positional):

TOKEN                The intermediate passphrase token used to create the
                     corresponding encrypted private key.                
SEED                 The Base16 entropy for the new encrypted public key.
                     Must be at least 192 bits in length (only the first 
                     192 bits are used).
```
See also [ek-address](bx-ek-address) and [ek-new](bx-ek-new).
### Example 1
```sh
TODO
```