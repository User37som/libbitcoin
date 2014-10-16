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
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H
```sh
$ bx hd-public -d xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
```
xprv9uHRZZhk6KAJC1avXpDAp4MDc3sQKNxDiPvvkX8Br5ngLNv1TxvUxt4cV1rGL5hj6KCesnDYUhd7oWgT11eZG7XnxHrnYeSvkzY7d2bhkJ7
```
### Example 2
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H/1
```sh
$ bx hd-public -i 1 xprv9uHRZZhk6KAJC1avXpDAp4MDc3sQKNxDiPvvkX8Br5ngLNv1TxvUxt4cV1rGL5hj6KCesnDYUhd7oWgT11eZG7XnxHrnYeSvkzY7d2bhkJ7
```
```
xprv9wTYmMFdV23N2TdNG573QoEsfRrWKQgWeibmLntzniatZvR9BmLnvSxqu53Kw1UmYPxLgboyZQaXwTCg8MSY3H2EU4pWcQDnRnrVA1xe8fs
```
### Example 3
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) chain M/0
```sh
$ bx hd-public xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```
```
xprv9vHkqa6EV4sPZHYqZznhT2NPtPCjKuDKGY38FBWLvgaDx45zo9WQRUT3dKYnjwih2yJD9mkrocEZXo1ex8G81dwSM1fwqWpWkeS3v86pgKt
```
### Example 4
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) Chain m/0/2147483647H
```sh
$ bx hd-public -d -i 2147483647 xprv9vHkqa6EV4sPZHYqZznhT2NPtPCjKuDKGY38FBWLvgaDx45zo9WQRUT3dKYnjwih2yJD9mkrocEZXo1ex8G81dwSM1fwqWpWkeS3v86pgKt
```
```
xprv9wSp6B7kry3Vj9m1zSnLvN3xH8RdsPP1Mh7fAaR7aRLcQMKTR2vidYEeEg2mUCTAwCd6vnxVrcjfy2kRgVsFawNzmjuHc2YmYRmagcEPdU9
```
### Example 5
piped commands (public key derivation from private key)
```sh
$ bx seed | bx hd-new | bx hd-public
```
```
091974a96a5bfc5b0d4a5ddb3ed987bf
xprv9s21ZrQH143K4R2ZMbGkj7RB7wvDhi9ciTTvoLz92LBxfhpfuebjpzwYW9DVzainPDChhipGuEpyfV76ntw51v95FNBnEhHAgiLsJ9DaR9m
xpub69jBNd8w5JXfxde1m46b1oHPVdnG4RWS46ZDSP5gVNph7AbDqJzbdRbpYsYwTKAec6YSMMZEZNXLDDtNQcvVaYHgdSuZkCnqCaTM4PxXBZ2
```
### Example 6
piped commands (public key derivation from public key)
```sh
$ bx seed | bx hd-new | bx hd-to-public | bx hd-public
```
```
d2c31a9f1a3327992ca7d0127bf5fd41
xprv9s21ZrQH143K2bSFxzjzNx5ujrKfNUrMByypMf8fKf3KxQPmGS1GtULEgKXHkovH8quK4wTFmJrJUKcE1s9AbriMqN8JyRPjmSi7ZKFF7og
xpub661MyMwAqRbcF5Wj52Gzk62eHtA9mwaCZCuRA3YGszaJqCiuoyKXSGeiXbRtR2qNoYS5XYXL7bFuLWG2honBdoq9S3aubW3RJAcwHtx11fJ
xpub69DYj2pS3TSfjRqX67H8SVidbHzdr5Nw52eX8FAZvkBkZr3W3nd6pTnYAqEFXBMnm6XsfVcfVnHu9ainWZp3Csv7trxd74iFzZapj2ECBLs
```