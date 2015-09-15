Create a payment address derived from an intermediate passphrase token (BIP38).
```sh
$ bx ek-address --help
```
```
Usage: bx ek-address [-hu] [--config VALUE] [--version VALUE] [TOKEN]    
[SEED]                                                                   

Info: Create a payment address derived from an intermediate passphrase   
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
See also [token-new](bx-token-new), [ek-new](bx-ek-new) and [ek-public](bx-ek-public).
### Example 1
lot/sequence
```sh
$ bx ek-address passphrasecpXbDpHuo8F7yuZqR49koDA9uQojPijjjZaxsar7Woo9pfHJbeWF3VMU9EPBqJ baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
6PoJB3hjqER7KJDeo69pfX3ttV5DPaQPEf4pZEwhNYjTjqMdvif5qfE34S
```
### Example 2
```sh
$ bx ek-address passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
1DeDt7odeJqJvquJ6obEZfH1hfJHMvnURa
```
### Example 3
piped commands
```sh
$ bx seed | bx ek-address passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq
```
```
7113f4c2e8f67b61225c9a619cd984b63f28df434bf18217 
1DS3aqzg5w8bMsyzyutxcrhKoLZGjPnC13
```
### Example 4
invalid seed
```sh
$ bx ek-address passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00d
```
```
The seed is less than 192 bits long.
```
### Example 5
--uncompressed
```sh
$ bx ek-address -u passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
1MydksvfdWNXM1KnVTS8A78M4b78aJcL1W
```
### Example 6
--version 111 (testnet)
```sh
$ bx ek-address -v 111 passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
mtABBAtcTLGZhxNupNZcPaVLZetzHVWgAp
```
### Example 7
--version 48 (litecoin), --uncompressed
```sh
$ bx ek-address -u -v 48 passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
LgCb26EViAcabp1wfbRRS8C7GoUQffafGp
```