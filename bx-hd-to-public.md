Derive the HD (BIP32) public key of a HD private key. 
```sh
$ bx hd-to-public --help
```
```
Usage: bx hd-to-public [-h] [--config VALUE] [--version VALUE]           
[HD_PRIVATE_KEY]                                                         

Info: Derive the HD (BIP32) public key of a HD private key.              

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired HD public key version, defaults to      
                     76067358.                                           

Arguments (positional):

HD_PRIVATE_KEY       The HD private key. If not specified the key is read
                     from STDIN. 
```
### Example 1
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m
```sh
$ bx hd-to-public xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
```
xpub661MyMwAqRbcFtXgS5sYJABqqG9YLmC4Q1Rdap9gSE8NqtwybGhePY2gZ29ESFjqJoCu1Rupje8YtGqsefD265TMg7usUDFdp6W1EGMcet8
```
### Example 2
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) Chain m
```sh
$ bx hd-to-public xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```
```
xpub661MyMwAqRbcFW31YEwpkMuc5THy2PSt5bDMsktWQcFF8syAmRUapSCGu8ED9W6oDMSgv6Zz8idoc4a6mr8BDzTJY47LJhkJ8UB7WEGuduB
```
### Example 3
piped commands
```sh
$ bx seed | bx hd-new | bx hd-to-public
```
```
53dc6e013ee4de6c858adb4ef75eb772
xprv9s21ZrQH143K4BXnA5VBs3HYVS9mkTjbXFfDepC5f6yAtU38MYmUUq7www2BjDWqZWR7EXtToXEphCWCxiQ6SwrpwcaUH7uDp2VGD47Hna7
xpub661MyMwAqRbcGfcFG72CEBEH3TzG9vTStUapTCbhDSW9mGNGu65j2dSRoDg3Uy79LHe9wFqFbhjM7UitQu5gAvkPnHtAWRLFzDRTM2t3C43
```
### Example 4
--version 70617039 (testnet)
```sh
$ bx hd-to-public -v 70617039 xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```
```
tpubD6NzVbkrYhZ4XJDrzRvuxHEyQaPd1mwwdDofEJwekX18tAdsqeKfxss79AJzg1431FybXg5rfpTrJF4iAhyR7RubberdzEQXiRmXGADH2eA
```