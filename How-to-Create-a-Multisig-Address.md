To receive payment you must first create a multisig payment address. This example shows a "2 of 3" address, however it can be generalized to any "m of n" scenario.

From three random **seeds**, generate three **private keys** and corresponding **public keys**.
```sh
$ bx seed | bx ec-new | bx ec-to-public
```
```
6b3f9712911f3262fe72de340f0cbb8d (seed #1)
9d695afea1c3ab99e11248e4b74e698332b11f5c5c051e6e80da61aa19ae7c89 (private key #1)
02b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b (public key #1)
```
```sh
$ bx seed | bx ec-new | bx ec-to-public
```
```
ca5167e564d813d6011ce02679a2c252 (seed #2)
68ebab45a918444d7e088c49bda76d7df89b9ea6ba5ddeb1aab5945391828b83 (private key #2)
025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c (public key #2)
```
```sh
$ bx seed | bx ec-new | bx ec-to-public
```
```
d4ec97842cf63764ed261ea80f221a69 (seed #3)
d1a7069b6057195545d4d9048887dd22be97f16bf463c201b76f8bb05ed423ee (private key #3)
021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f010 (public key #3)
```
Use the public keys to create the redeem **script** and the corresponding script hash address. The "2" represents the number signatures required to spend money received at the address and the "3" represents the number of possible signatures.
```sh
$ bx script-to-address "2 [ 02b66fcb1064d827094685264aaa90d0126861688932eafbd1d1a4ba149de3308b ] [ 025cab5e31095551582630f168280a38eb3a62b0b3e230b20f8807fc5463ccca3c ] [ 021098babedb3408e9ac2984adcf2a8e4c48e56a785065893f76d0fa0ff507f010 ] 3 checkmultisig"
```
```
3A6oGpJ5MzABAj9PofXKjcpTJCgYrdGBNJ
```
Now you can spend some amount to the address. This is my [spend transaction](https://blockchain.info/tx/f759759bc998ec96879e4ae8c1639e8a186e0d507401eb32e4479de64d340605).