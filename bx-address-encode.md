Convert a RIPEMD160 value to a payment address.     
```sh
$ bx address-encode --help
```
```
Usage: bx address-encode [-h] [--config VALUE] [--version VALUE]         
[RIPEMD160]                                                              

Info: Convert a RIPEMD160 value to a payment address.                    

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired payment address version.                

Arguments (positional):

RIPEMD160            The Base16 hash to convert. If not specified the    
                     value is read from STDIN. 
```
See the [list of Bitcoin address prefixes](https://en.bitcoin.it/wiki/List_of_address_prefixes) for a detailed description of `version`.

See also [address-decode](bx-address-decode).
### Example 1
```sh
$ bx address-encode b472a266d0bd89c13706a4132ccfb16f7c3b9fcb
```
```
1HT7xU2Ngenf7D4yocz2SAcnNLW7rK8d4E
```
### Example 2
--version 111 (testnet)
```sh
$ bx address-encode -v 111 b472a266d0bd89c13706a4132ccfb16f7c3b9fcb
```
```
mwy5FX7MVgDutKYbXBxQG5q7EL6pmhHT58
```
### Example 3
piped commands
```sh
$ bx seed | bx ec-new | bx ec-to-public | bx bitcoin160 | bx address-encode
```
```
3ef002f66a2be8301106e39861433e9740f7e058a738738b
6162020b12fdefd90ec772f0da856aa10a34d5e19c4fe1fcedd2eedaf9fcf6fc
03527e99e7e665c95c4354c74ecb59c0e0b6d97568b546eed170789648d13c3dea
1a928dd68a297e6eff178b17c8faa8afc78b7a4a
13RW8k2YdMXP7M4Xc4mcZvGgBEksRmkWQW
```
### Example 4
2 of 4 multisig, --version 196 (testnet pay-to-script-hash)
```sh
$ bx script-to-address -v 196 "2 [ 020ae29f86f404e4b302cfa17ff15d93149af6a54c80a4172d47e41f55f6a78d73 ] [ 03664d528eb80096671ef9011c533ceb5df133238e3690d88f2960c786398b86b1 ] [ 029a449ea4a2155ea10002d704604bb3e8606631d35af20889a74b82b2dab572f6 ] [ 0321602d78046d63256b1730b119b1aca3428039f18fdb73ccf45ad3e148dd9b17 ] 4 checkmultisig"
```
```
2N8uwbECKZJLmfYRErQazYBAWfd8PJ66rAN
```