Create a new HD (BIP32) private key from entropy.   
```sh
```
$ bx hd-new --help
```
Usage: bx hd-new [-h] [--config VALUE] [SEED]                            

Info: Create a new HD (BIP32) private key from entropy.                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.

Arguments (positional):

SEED                 The Base16 randomness seed for the new key. Must be 
                     at least 128 bits in length. If not specified the   
                     seed is read from STDIN.  
```
### Example 1
BIP-32 [Test Vector A](github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) master
```
$ bx hd-new 000102030405060708090a0b0c0d0e0f
```
```
xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
### Example 2
```
$ bx hd-new fffcf9f6f3f0edeae7e4e1dedbd8d5d2cfccc9c6c3c0bdbab7b4b1aeaba8a5a29f9c999693908d8a8784817e7b7875726f6c696663605d5a5754514e4b484542
```
```
xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```
### Example 3
short seed error
```sh
$ bx hd-new baadf00dbaadf00d
```
```
The seed is less than 128 bits long.
```