Derive the HD (BIP32) public key of a HD private key. 
```sh
$ bx hd-to-public --help
```
```
Usage: bx hd-to-public [-h] [--config VALUE] [HD_PRIVATE_KEY]            

Info: Derive the HD (BIP32) public key of a HD private key.              

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

HD_PRIVATE_KEY       The HD private key. If not specified the key is read
                     from STDIN.  
```
### Example 1
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m
```
$ bx hd-to-public xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
```
xpub661MyMwAqRbcFtXgS5sYJABqqG9YLmC4Q1Rdap9gSE8NqtwybGhePY2gZ29ESFjqJoCu1Rupje8YtGqsefD265TMg7usUDFdp6W1EGMcet8
```
### Example 2
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) Chain m
```
$ bx hd-to-public xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```
```
xpub661MyMwAqRbcFW31YEwpkMuc5THy2PSt5bDMsktWQcFF8syAmRUapSCGu8ED9W6oDMSgv6Zz8idoc4a6mr8BDzTJY47LJhkJ8UB7WEGuduB
```