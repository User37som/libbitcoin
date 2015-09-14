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

PASSPHRASE           The passphrase for encrypting the token.            
SALT                 The Base16 entropy for the new token. Must be at    
                     least 32 bits in length. Only the first 32 bits are 
                     used unless lot and sequence are zero or unspecified
                     and the salt is at least 64 bits, in which case 64  
                     bits are used and lot and sequence are not used.    
```
### Example 1
```sh
$ bx token-new "my passphrase" baadf00d
```
```
passphrasecpXbDpHuo8FGWjkFCxTEYSaekfi45D88ad5DVReNLhCTbnETGLfYfcrV4vwx3Q
```
### Example 2
invalid salt
```sh
$ bx token-new "my passphrase" baadf0
```
```
The salt is less than 32 bits long.
```
### Example 3
piped commands
```sh
$ bx seed | bx token-new "my passphrase"
```
```
f6af40a01b79c95fef5e397eca05e27d7a3d1c35b01108db
passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq
```