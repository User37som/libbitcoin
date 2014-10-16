Derive a child HD (BIP32) private key from another HD private key. 
```sh
$ bx hd-private --help
```
```
Usage: bx hd-private [-dh] [--config VALUE] [--index VALUE]              
[HD_PRIVATE_KEY]                                                         

Info: Derive a child HD (BIP32) private key from another HD private key. 

Options (named):

-c [--config]        The path to the configuration settings file.        
-d [--hard]          Signal to create a hardened key.                    
-h [--help]          Get a description and instructions for this command.
-i [--index]         The HD index, defaults to zero.                     

Arguments (positional):

HD_PRIVATE_KEY       The parent HD private key. If not specified the key 
                     is read from STDIN. 
```
### Example 1
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) master
```
$ bx hd-new 000102030405060708090a0b0c0d0e0f
```
```
xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
### Example 2
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) chain M
```
$ bx hd-new fffcf9f6f3f0edeae7e4e1dedbd8d5d2cfccc9c6c3c0bdbab7b4b1aeaba8a5a29f9c999693908d8a8784817e7b7875726f6c696663605d5a5754514e4b484542
```
```
xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```