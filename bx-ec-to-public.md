Derive the EC public key of an EC private key.
```sh
$ bx ec-to-public --help
```
```
Usage: bx ec-to-public [-hu] [--config VALUE] [EC_PRIVATE_KEY]

Info: Derive the EC public key of an EC private key. Defaults to the    
compressed public key format.

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-u [--uncompressed]  Derive using the uncompressed public key format.    

Arguments (positional):

EC_PRIVATE_KEY       The Base16 EC private key. If not specified the key 
                     is read from STDIN.
```
### Example 1
```sh
$ bx ec-to-public 4c721ccd679b817ea5e86e34f9d46abb1660a63955dde908702214eaab038475
```
```
03ac9e60013853128b42a1324609bac2ccff6a0b4844b6301f1f552e15ee14c7a5
```
### Example 2
--uncompressed
```sh
$ bx ec-to-public -u 4c721ccd679b817ea5e86e34f9d46abb1660a63955dde908702214eaab038475
```
```
04ac9e60013853128b42a1324609bac2ccff6a0b4844b6301f1f552e15ee14c7a56e880343da4e6701e0c2266db10cffbd2b8c81d54ba77766d776c661476d1069
```
### Example 2
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-public
```
```
2deeac24fa1b0678c71f2427400c35ac
1f31b7247933f36dde11610b32d473710aedca81f34d90137370366f5291c966
02daa7db1b30da2a9a457171f5861d98d055b3bb0f31316679766fd1c774519d2a
```