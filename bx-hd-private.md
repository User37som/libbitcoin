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
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H
```
$ bx hd-private -d xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
```
xprv9uHRZZhk6KAJC1avXpDAp4MDc3sQKNxDiPvvkX8Br5ngLNv1TxvUxt4cV1rGL5hj6KCesnDYUhd7oWgT11eZG7XnxHrnYeSvkzY7d2bhkJ7
```
### Example 2
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H/1
```
$ bx hd-private -i 1 xprv9uHRZZhk6KAJC1avXpDAp4MDc3sQKNxDiPvvkX8Br5ngLNv1TxvUxt4cV1rGL5hj6KCesnDYUhd7oWgT11eZG7XnxHrnYeSvkzY7d2bhkJ7
```
```
xprv9wTYmMFdV23N2TdNG573QoEsfRrWKQgWeibmLntzniatZvR9BmLnvSxqu53Kw1UmYPxLgboyZQaXwTCg8MSY3H2EU4pWcQDnRnrVA1xe8fs
```
### Example 3
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) chain M/0
```
$ bx hd-private xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```
```
xprv9vHkqa6EV4sPZHYqZznhT2NPtPCjKuDKGY38FBWLvgaDx45zo9WQRUT3dKYnjwih2yJD9mkrocEZXo1ex8G81dwSM1fwqWpWkeS3v86pgKt
```
### Example 4
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) Chain m/0/2147483647H
```
$ bx hd-private -d -i 2147483647 xprv9vHkqa6EV4sPZHYqZznhT2NPtPCjKuDKGY38FBWLvgaDx45zo9WQRUT3dKYnjwih2yJD9mkrocEZXo1ex8G81dwSM1fwqWpWkeS3v86pgKt
```
```
xprv9wSp6B7kry3Vj9m1zSnLvN3xH8RdsPP1Mh7fAaR7aRLcQMKTR2vidYEeEg2mUCTAwCd6vnxVrcjfy2kRgVsFawNzmjuHc2YmYRmagcEPdU9
```