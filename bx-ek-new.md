Info: Create an encrypted private key from an intermediate passphrase    
token (BIP38).
```sh
$ bx ek-new --help
```
```
Usage: bx ek-new [-hu] [--config VALUE] [--version VALUE] [TOKEN] [SEED] 

Info: Create an encrypted private key from an intermediate passphrase    
token (BIP38).                                                           

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-u [--uncompressed]  Use the uncompressed public key format.             
-v [--version]       The desired payment address version.                

Arguments (positional):

TOKEN                The intermediate passphrase token.                  
SEED                 The Base16 entropy for the new encrypted private    
                     key. Must be at least 192 bits in length (only the  
                     first 192 bits are used).
```
See also [ek-address](bx-ek-address) and [ek-public](bx-ek-public).
### Example 1
```sh
TODO
```