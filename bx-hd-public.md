Derive a child HD (BIP32) public key from another HD public or     
private key.
```sh
$ bx hd-public --help
```
```
Usage: bx hd-public [-dh] [--config VALUE] [--index VALUE]               
[HD_PUBLIC_KEY]                                                          

Info: Derive a child HD (BIP32) public key from another HD public or     
private key.                                                             

Options (named):

-c [--config]        The path to the configuration settings file.        
-d [--hard]          Signal to create a hardened key.                    
-h [--help]          Get a description and instructions for this command.
-i [--index]         The HD index, defaults to zero.                     

Arguments (positional):

HD_PUBLIC_KEY        The parent HD public or private key. If not         
                     specified the key is read from STDIN. 
```
### Example 1
hard option error
```sh
$ bx hd-public -d xpub661MyMwAqRbcFtXgS5sYJABqqG9YLmC4Q1Rdap9gSE8NqtwybGhePY2gZ29ESFjqJoCu1Rupje8YtGqsefD265TMg7usUDFdp6W1EGMcet8
```
```
The hard option requires a private key.
```
### Example 2
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H/1
```sh
$ bx hd-public -i 1 xpub68Gmy5EdvgibQVfPdqkBBCHxA5htiqg55crXYuXoQRKfDBFA1WEjWgP6LHhwBZeNK1VTsfTFUHCdrfp1bgwQ9xv5ski8PX9rL2dZXvgGDnw
```
```
xpub6ASuArnXKPbfEwhqN6e3mwBcDTgzisQN1wXN9BJcM47sSikHjJf3UFHKkNAWbWMiGj7Wf5uMash7SyYq527Hqck2AxYysAA7xmALppuCkwQ
```
### Example 3
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H/1/2H
```sh
$ bx hd-public -d -i 2 xpub6ASuArnXKPbfEwhqN6e3mwBcDTgzisQN1wXN9BJcM47sSikHjJf3UFHKkNAWbWMiGj7Wf5uMash7SyYq527Hqck2AxYysAA7xmALppuCkwQ
```
```
The hard option requires a private key.
```
### Example 4
piped commands (public key derivation from private key)
```sh
$ bx seed | bx hd-new | bx hd-public
```
```
091974a96a5bfc5b0d4a5ddb3ed987bf
xprv9s21ZrQH143K4R2ZMbGkj7RB7wvDhi9ciTTvoLz92LBxfhpfuebjpzwYW9DVzainPDChhipGuEpyfV76ntw51v95FNBnEhHAgiLsJ9DaR9m
xpub69jBNd8w5JXfxde1m46b1oHPVdnG4RWS46ZDSP5gVNph7AbDqJzbdRbpYsYwTKAec6YSMMZEZNXLDDtNQcvVaYHgdSuZkCnqCaTM4PxXBZ2
```
### Example 5
piped commands (public key derivation from public key)
```sh
$ bx seed | bx hd-new | bx hd-to-public | bx hd-public
```
```
9d72c9d7e17468d5f789e841cfa11e19
xprv9s21ZrQH143K3dkWG7DPBN7r6QDrTqvszLBBreXR2PKrG7tPJ21JwJ2rHK5ZSXE3SzoSuzZ5twjJPTYhSCTZgjje2Ueg4TJDpXRikxa9mrk
xpub661MyMwAqRbcG7pyN8kPYW4aeS4LsJejMZ6nf2w2airq8vDXqZKZV6ML8a71xfXYNR3ZktB2oF8smPmprPaXuMZ5wStSfcKpUvjorwKugxu
xpub68W9m7AG6qRBkVgU3bxrk6feqT6efmdba7m2S9s4AYyyK4dypNWReP5rrUkwthCV3xLhhx65xnJ7eg7j4CK7jv4mKtNRGeNuXxZSQQh883V
```