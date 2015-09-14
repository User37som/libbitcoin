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
See also [ek-new](bx-ek-new).
### Example 1
lot 0, sequence 0 (i.e. defaults when salt is less than 64 bits)
```sh
$ bx token-new "my passphrase" baadf00d
```
```
passphrasecpXbDpHuo8F7yuZqR49koDA9uQojPijjjZaxsar7Woo9pfHJbeWF3VMU9EPBqJ
```
### Example 2
--lot 7 --sequence 42
```sh
$ bx token-new -l 7 -s 42 "my passphrase" baadf00d
```
```
passphrasecpXbDpHuo8FGWy2zdpFXvmsu31YuLU5peBAqzJifHjeaHfePVW45ptrh3NqD3Z
```
### Example 3
invalid salt
```sh
$ bx token-new "my passphrase" baadf0
```
```
The salt is less than 32 bits long.
```
### Example 4
--lot 1048576 (invalid)
```sh
$ bx token-new -l 1048575 "my passphrase" baadf00d
```
```
The lot exceeds the maximum value of 1048575.
```
### Example 5
--sequence 4096 (invalid)
```sh
$ bx token-new -s 4096 "my passphrase" baadf00d
```
```
The sequence exceeds the maximum value of 4095.
```
### Example 6
piped commands, no lot/sequence (default when salt at least 64 bits)
```sh
$ bx seed | bx token-new "my passphrase"
```
```
f6af40a01b79c95fef5e397eca05e27d7a3d1c35b01108db
passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq
```
### Example 7
--lot 7 --sequence 42, piped input
```sh
$ echo f6af40a01b79c95f | bx token-new -l 7 -s 42 "my passphrase"
```
```
f6af40a01b79c95fef5e397eca05e27d7a3d1c35b01108db 
passphraseeJe8PsbqqTpXKHHL5CupNg3hf396MFAHUeFf1k74zFs2pqxM9ARwjKLh4Px1sB
```
### Example 8
demo unused salt bits
```sh
$ bx token-new -l 7 -s 42 "my passphrase" f6af40a01b79c95fef5e397eca05e27d7a3d1c35b01108db 
```
```
f6af40a01b79c95fef5e397eca05e27d7a3d1c35b01108db 
passphraseeJe8PsbqqTpXKHHL5CupNg3hf396MFAHUeFf1k74zFs2pqxM9ARwjKLh4Px1sB
```