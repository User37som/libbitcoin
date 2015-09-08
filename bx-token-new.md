Create an intermediate passphrase token for deferred encrypted key generation (BIP38).
```sh
$ bx token-new --help
```
```
Usage: bx token-new [-h] [--config VALUE] [--lot VALUE] [--sequence      
VALUE] [PASSPHRASE] [SALT]                                               

Info: Create an intermediate passphrase token for deferred encrypted key 
generation (BIP38).                                                      

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-l [--lot]           An arbitrary lot number, limited to 1048575.        
-s [--sequence]      An arbitrary sequence number, limited to 4095.      

Arguments (positional):

PASSPHRASE           The passphrase for locking the token.               
SALT                 The Base16 entropy for the new token. Must be at    
                     least 32 bits in length (only the first 32 bits are 
                     used).
```
### Example 1
```sh
TODO
```