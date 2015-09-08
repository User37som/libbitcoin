Create a payment address derived from an intermediate passphrase   
```sh
$ bx ek-address --help
```
```
Usage: bx ek-address [-hu] [--config VALUE] [--version VALUE] [TOKEN]    
[SEED]                                                                   

Info: 
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
SEED                 The Base16 entropy used to create the corresponding 
                     encrypted private key. Must be at least 192 bits in 
                     length (only the first 192 bits are used).
```
See also [ek-new](bx-ek-new) and [ek-public](bx-ek-public).
### Example 1
```sh
TODO
```