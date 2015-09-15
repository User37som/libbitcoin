Create an encrypted private key from an intermediate passphrase token (BIP38).
```sh
$ bx ek-new --help
```
```
Usage: bx ek-new [-hu] [--config VALUE] [--version VALUE] TOKEN [SEED]   

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
                     first 192 bits are used). If not specified the seed 
                     is read from STDIN.  
```
The `--version` option is a [libbitcoin enhancement](https://github.com/libbitcoin/libbitcoin/wiki/Altchain-Encrypted-Private-Keys) not yet specified in [BIP-38](https://github.com/bitcoin/bips/blob/master/bip-0038.mediawiki).

See also [token-new](bx-token-new), [ek-address](bx-ek-address) and [ek-public](bx-ek-public).
### Example 1
lot/sequence
```sh
$ bx ek-new passphrasecpXbDpHuo8F7yuZqR49koDA9uQojPijjjZaxsar7Woo9pfHJbeWF3VMU9EPBqJ baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
6PoJB3hjqER7KJDeo69pfX3ttV5DPaQPEf4pZEwhNYjTjqMdvif5qfE34S
```
### Example 2
```sh
$ bx ek-new passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
6PnUht3dP5Jdcp1B7NGqkEoBw5Ja2wWEeQMDRHqLNrBG4Rqo59eVfMd98B
```
### Example 3
piped commands
```sh
$ bx seed | bx ek-new passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq
```
```
7113f4c2e8f67b61225c9a619cd984b63f28df434bf18217
6PnTXoTt48rHNWvuMBRyW2ttL4zfz31J8TMcsJQVNxmxAgqVMN2mmNezsC
```
### Example 4
invalid seed
```sh
$ bx ek-new passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00d
```
```
The seed is less than 192 bits long.
```
### Example 5
--uncompressed
```sh
$ bx ek-new -u passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
6PfM4jsmgX1veYaiBXqqDe3J8hFtAriohdNGjPfrbt7aQ8H53nijYN6svW
```
### Example 6
--version 111 (testnet)
```sh
$ bx ek-new -v 111 passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
8FEMBzS4QWPwxyzrYJxHwzSrdNzroFiQjkAnpf51xcPPXkTvqGrD8bVq68
```
### Example 7
--version 48 (litecoin), --uncompressed
```sh
$ bx ek-new -u -v 48 passphraseryQXuRZZQ3Jw5rAT7m6MzxkGSSRmysq3Ayj9vuEHEnbVPJSmRQ2xYFKDKjGYrq baadf00dbaadf00dbaadf00dbaadf00dbaadf00dbaadf00d
```
```
7C8LFBdEAqptMNYUNr2cgcP7bppVgsqtz1fXVeSzAPf8VkB29XMKDtF71p
```