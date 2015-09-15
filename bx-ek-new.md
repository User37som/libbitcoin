Create an encrypted private key from an intermediate passphrase token (BIP38).
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
See also [token-new](bx-token-new), [ek-address](bx-ek-address) and [ek-public](bx-ek-public).
### Example 1
lot/sequence token
```sh
$ bx ek-new passphrasecpXbDpHuo8F7yuZqR49koDA9uQojPijjjZaxsar7Woo9pfHJbeWF3VMU9EPBqJ baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
6PoJB3hjqER7KJDeo69pfX3ttV5DPaQPEf4pZEwhNYjTjqMdvif5qfE34S
```
### Example 7
no lot/sequence
```sh
$ bx ek-new passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
6PnUht3dP5Jdcp1B7NGqkEoBw5Ja2wWEeQMDRHqLNrBG4Rqo59eVfMd98B
```
### Example 8
piped commands, no lot/sequence
```sh
$ bx seed | bx ek-new passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq
```
```
7113f4c2e8f67b61225c9a619cd984b63f28df434bf18217
6PnTXoTt48rHNWvuMBRyW2ttL4zfz31J8TMcsJQVNxmxAgqVMN2mmNezsC
```
### Example 9
invalid seed
```sh
$ bx ek-new passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00d
```
```
The seed is less than 192 bits long.
```